# RL Grid World Navigator

<div align="center">

![RL](https://img.shields.io/badge/Reinforcement%20Learning-Q--Learning%20%26%20SARSA-7c3aed?style=for-the-badge&logo=openai&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-Canvas%20%2B%20JS-e34f26?style=for-the-badge&logo=html5&logoColor=white)
![Status](https://img.shields.io/badge/Status-Live-00e676?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

## [**Live Demo -- Click to Open the App**](https://manu-krishnan005.github.io/rl-gridworld/)

*An intelligent RL agent that learns to navigate a maze in real time -- right in your browser.*

</div>

---

## About

This project is an **interactive Reinforcement Learning dashboard** built as part of an AI/ML assignment. It demonstrates an intelligent agent learning to navigate a **Grid World maze** using:

- **Q-Learning** (off-policy Temporal Difference algorithm)
- **SARSA** (on-policy Temporal Difference algorithm)
- **epsilon-Greedy Exploration** with epsilon decay over episodes

The agent starts with zero knowledge and progressively learns the optimal path from **Start to Goal** through trial, error, and reward signals -- all visualized live in the browser.

> No Python, no libraries, no server needed. Pure **HTML5 + Canvas + Vanilla JavaScript**.

---

## Live Demo

**https://manu-krishnan005.github.io/rl-gridworld/**

| View | Description |
|------|-------------|
| **Agent View** | Watch the cyan glowing agent navigate the maze in real time |
| **Q-Heatmap** | Color-coded cells showing learned Q-values (cold to hot) |
| **Policy View** | Arrows showing the agent's best action at every cell |
| **Learning Curve** | Live chart of reward per episode + 20-episode moving average |

---

## Features

### Algorithms

| Algorithm | Type | Description |
|-----------|------|-------------|
| **Q-Learning** | Off-policy | Learns optimal Q*(s,a) using greedy max over next state |
| **SARSA** | On-policy | Uses actual next action taken -- safer, more conservative paths |

### Maze Environments

| Maze | Size | Difficulty |
|------|------|------------|
| Simple | 8 x 8 | Beginner |
| Medium | 12 x 12 | Intermediate |
| Hard | 16 x 16 | Advanced |
| Custom Spiral | 12 x 12 | Challenging layout |

### Controls

- **Hyperparameter sliders** -- Learning Rate (alpha), Discount Factor (gamma), Epsilon, Decay Rate
- **Speed modes** -- Slow, Normal, Fast, **Turbo** (trains 50 episodes per tick instantly)
- **Demo Best** -- Runs the fully-learned greedy policy with no exploration
- **Export CSV** -- Download the full Q-table as a spreadsheet
- **Keyboard shortcuts** -- `Space` = Train/Pause, `R` = Reset, `D` = Demo

---

## RL Concepts Demonstrated

### Bellman Update Equation (Q-Learning)

```
Q(s, a) <- Q(s, a) + alpha * [ r + gamma * max Q(s', a') - Q(s, a) ]
```

- `alpha` = learning rate (how fast to update)
- `gamma` = discount factor (how much to value future rewards)
- `r` = immediate reward received
- `max Q(s', a')` = best possible future value (bootstrapping)

### SARSA Update

```
Q(s, a) <- Q(s, a) + alpha * [ r + gamma * Q(s', a') - Q(s, a) ]
```

Where `a'` is the *actual* action taken in `s'` (on-policy), not the greedy max.

### Epsilon-Greedy Exploration Policy

```
pi(a | s) = random action       if rand() < epsilon   (explore)
            argmax_a Q(s, a)    otherwise              (exploit)

epsilon <- epsilon * decay_rate   (applied after each episode)
```

### Reward Structure

| Event | Reward |
|-------|--------|
| Reach Goal | +100 |
| Step on Trap | -10 |
| Hit a Wall | -5 |
| Normal Step | -0.5 |

The step penalty encourages the agent to find **short, efficient paths**.

---

## How to Use

### Option 1 -- Live (Recommended, No Setup)

Open: **https://manu-krishnan005.github.io/rl-gridworld/**

### Option 2 -- Run Locally

```bash
git clone https://github.com/Manu-krishnan005/rl-gridworld.git
cd rl-gridworld
# Open index.html in any modern browser (Chrome, Edge, Firefox)
```

On Windows just double-click `index.html`.

### Recommended Demo Workflow

1. Select a maze (start with **Medium 12x12**)
2. Click **Start Training** or press `Space`
3. Switch to **Turbo** speed -- watch 500+ episodes train in seconds
4. Click **Q-Heat** tab -- see the learned Q-value landscape emerge
5. Click **Policy** tab -- see arrows pointing toward the goal
6. Click **Demo Best** -- watch the agent navigate the optimal path!

---

## Project Structure

```
rl-gridworld/
|
+-- index.html    # Complete self-contained app (HTML + CSS + JS, ~50KB)
+-- README.md     # This file
```

---

## Technical Details

```
State Space    : (row, col) pairs -> rows x cols discrete states
Action Space   : {Up, Down, Left, Right} -> 4 discrete actions
Q-Table        : Q[states x actions] initialized to 0, Float64
Policy         : epsilon-greedy with multiplicative epsilon decay
Update Rule    : Temporal Difference TD(0)
Convergence    : Tracked via episode reward + moving average chart
Rendering      : HTML5 Canvas API (60fps animation loop)
```

---

## Screenshots

**Agent View** -- The glowing cyan dot is the agent learning in real time. Yellow cell = goal, red shading = walls, orange = traps.

**Q-Value Heatmap** -- Cool blue = low value states, teal/cyan = high value states. A bright path forms from start to goal as learning progresses.

**Policy Arrows** -- After training, each cell shows an arrow indicating the agent's best learned action. Arrows form coherent routes toward the goal.

**Learning Curve** -- The reward graph climbs steeply early on then plateaus near optimal. The moving average (colored line) smooths out the noise.

---

## References

- Sutton, R. S., & Barto, A. G. (2018). *Reinforcement Learning: An Introduction* (2nd ed.). MIT Press.
- Watkins, C. J. C. H., & Dayan, P. (1992). Q-learning. *Machine Learning*, 8(3-4), 279-292.
- Rummery, G. A., & Niranjan, M. (1994). On-line Q-learning using connectionist systems (SARSA origin paper).

---

## Author

**Manu Krishnan** -- Reinforcement Learning Assignment Submission

[![GitHub](https://img.shields.io/badge/GitHub-Manu--krishnan005-181717?style=flat-square&logo=github)](https://github.com/Manu-krishnan005)

---

<div align="center">
  Built with pure HTML5, Canvas API & Vanilla JavaScript &nbsp;|&nbsp; No frameworks &nbsp;|&nbsp; No dependencies
</div>
