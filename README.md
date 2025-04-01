# Nim AI: Reinforcement Learning for Optimal Gameplay

## Overview
This project implements an AI that learns to play the game of **Nim** using **reinforcement learning**. The AI trains itself through thousands of self-play games, gradually improving its strategy by updating Q-values based on rewards.

## Game Rules
Nim is a strategy game where players take turns removing objects from piles. The player forced to take the last object loses.

## AI Approach
The AI learns using **Q-learning**, an algorithm that assigns numerical values (Q-values) to state-action pairs based on experience. Over time, the AI optimizes its decision-making process, choosing moves that maximize its chances of winning.

## Implementation Details
The AI is implemented in `nim.py` and follows these steps:
1. **Training Phase**: The AI plays **10,000 self-play games**, updating its knowledge with each move.
2. **State Representation**: Each game state is represented as a tuple of integers, indicating the number of objects in each pile.
3. **Actions**: An action consists of a tuple `(pile, objects)`, representing the removal of a specific number of objects from a pile.
4. **Q-Learning Formula**:
   \[ Q(s, a) \leftarrow Q(s, a) + \alpha (R + \gamma \max Q(s', a') - Q(s, a)) \]
   - `alpha` (learning rate) controls how much new knowledge affects old knowledge.
   - `gamma` (discount factor) influences the importance of future rewards.
   - `R` is the immediate reward.

## Files and Functions
- **`nim.py`**
  - `get_q_value(state, action)`: Retrieves the Q-value for a given state-action pair.
  - `update_q_value(state, action, old_q, reward, future_rewards)`: Updates Q-values using the learning formula.
  - `best_future_reward(state)`: Returns the best possible future reward for a given state.
  - `choose_action(state, epsilon=False)`: Selects the best action based on Q-values or follows an epsilon-greedy strategy.
- **`train.py`**: Trains the AI by simulating thousands of games.
- **`play.py`**: Allows a human to play against the trained AI.

## Running the Project
### Train the AI
```sh
python play.py
```
### Example Output
```
Playing training game 1
Playing training game 2
...
Playing training game 10000
Done training

Piles:
Pile 0: 1
Pile 1: 3
Pile 2: 5
Pile 3: 7

AI's Turn
AI chose to take 1 from pile 2.
```

## Conclusion
This project demonstrates how **reinforcement learning** can be used to develop an optimal strategy for **Nim**. Through self-play and Q-learning, the AI continuously refines its decision-making, ultimately becoming a formidable opponent.

## License
This project is part of an Harvard's CS80 AI coursework assignment exploring Machine Learning.
