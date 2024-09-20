# Hot or Cold Custom Env RL
 

This repository contains a custom environment for the classic "Hot or Cold" game, designed for use in reinforcement learning (RL) experiments. The agent is placed in a 100x100 grid, with the goal of reaching a randomly placed target by moving in one of eight possible directions (up, down, left, right, and diagonal). Rewards are given based on the distance to the target and whether the agent successfully reaches it.

## Table of Contents

- [Features](#features)
- [Libraries Used](#libraries-used)
- [Reward Mechanism](#reward-mechanism)
- [Test Function](#test-function)
- [Example Usage](#example-usage)
- [Customization](#customization)

## Features
- **Grid Size:** 100x100 grid for agent navigation.
- **Actions:** 8 possible actions (4 cardinal directions + 4 diagonals).
- **Reward Function:** The agent receives a reward based on proximity to the target and a large reward upon reaching the target.
- **Termination:** The episode ends either when the agent reaches the target or after a predefined number of steps (time out).

## Libraries Used

This project utilizes several libraries to facilitate the development of the `Hot_or_Cold_Env` environment:

1. **gym**
   - **Purpose:** The `gym` library is used to create and manage the environment. It provides a standard interface for reinforcement learning environments, making it easier to implement, test, and evaluate various algorithms.

2. **numpy**
   - **Purpose:** The `numpy` library is used for numerical operations. It provides support for multi-dimensional arrays and matrices, along with a collection of mathematical functions to operate on these arrays, which is essential for calculating distances and managing states in the environment.

3. **random**
   - **Purpose:** The `random` library is utilized to introduce randomness into the environment, such as initializing the agent's and target's positions randomly within the grid.

4. **os**
   - **Purpose:** The `os` library can be used for interacting with the operating system, although it may not be necessary in the current version of the project. It can be helpful for file management and environment configurations in more complex scenarios.


## Reward Mechanism
The reward mechanism in the Hot or Cold environment operates as follows:

1. **Base Penalty for Steps:**
   - The agent receives a small negative reward of `-0.1` for each step taken. This penalty encourages the agent to find the target quickly rather than taking unnecessary steps.

2. **Distance-Based Rewards:**
   - The distance to the target is calculated using the Euclidean distance formula. As the agent moves closer to the target, it can earn additional rewards:
     - If the agent gets closer to the target compared to the previous step, it receives a positive reward of `+1`.
     - If the agent moves further away from the target, it incurs a penalty of `-0.5`. This mechanism helps the agent learn to minimize the distance to the target effectively.

3. **Target Reached:**
   - If the agent successfully reaches the target, it receives a significant positive reward of `+100`, which serves as a strong incentive for achieving the goal.

4. **Episode Termination:**
   - The episode ends when the agent reaches the target or when the maximum number of steps (time limit) is reached. In the latter case, no additional rewards are given.

### Test Function

The test function works as follows:

1. **Initialization:** An instance of the `Hot_or_Cold_Env` class is created, and the environment is reset to obtain the initial state and target position.

2. **Action Selection:** The agent randomly selects an action from the available action space.

3. **State Update:** The action is applied to the environment, which returns the new state, reward, done flag, and additional info.

4. **Reward Tracking:** The total reward is accumulated over the steps taken.

5. **Output:** For each step, the function prints:
   - The action taken
   - The new state of the agent
   - The reward received
   - The total reward so far
   - The distance to the target

6. **Completion Check:** If the agent reaches the target or the time runs out, the function indicates that the episode is complete and exits the loop.

### Example Usage

To run the test, simply call the `test_hot_or_cold_env()` function:
```python
test_hot_or_cold_env()
```

## Customization

- **Grid Size:** Adjust the grid dimensions by modifying the `observation_space` in the environment class.
  
- **Action Space:** Change the available actions by updating the `self.action_space` in the `Hot_or_Cold_Env` class.
  
- **Reward Function:** Customize the reward system by modifying the logic within the `step()` method.
