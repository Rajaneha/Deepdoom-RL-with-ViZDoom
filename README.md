# 🎮 DeepDoom: RL with ViZDoom


## 🚀 Overview

**DeepDoom** is a reinforcement learning project built on the [ViZDoom](https://github.com/mwydmuch/ViZDoom) platform. It leverages **PPO**, **A2C**, and **DQN** algorithms to train AI agents for combat and survival in various Doom-inspired FPS scenarios.

> Includes: 🧠 Custom Gym-compatible environments, 📈 training visualizations, 🕹️ real-time interaction via Flask web app, and 🎓 curriculum learning strategies.

---

## 🧠 RL Algorithms Implemented

| Algorithm | Type           | Policy Type | Notes |
|----------|----------------|-------------|-------|
| **PPO**  | On-policy      | Stochastic  | Proximal Policy Optimization |
| **A2C**  | On-policy      | Stochastic  | Advantage Actor-Critic |
| **DQN**  | Off-policy     | Deterministic | Deep Q-Network |

---

## 🧪 Scenarios & Challenges

### 🟩 `basic.cfg`: Feasibility Test

A simple test scenario to verify that training works.

- 🎯 Reward: +101 for killing the monster  
- 💣 Penalty: -5 for missed shot  
- ⌛ Step penalty: -1 per step  
- 🎮 Actions: Move Left, Move Right, Shoot  
- ⏳ Timeout: 300 steps

---

### 🟨 `defend_the_center.cfg`: Survival Arena

Player in center with limited ammo, surrounded by respawning melee monsters.

- ☠️ Reward: +1 per kill  
- 😵 Penalty: -1 on death  
- 🎮 Actions: Turn Left, Turn Right, Shoot  

---
### 🟥 `deadly_corridor.cfg`: Navigation Under Fire

Navigate toward a goal while avoiding ranged attacks.

- ➕ Closer to goal: +dX  
- ➖ Moving back: -dX  
- 💀 Death: -100  
- 🎮 Actions: Turn Left, Turn Right, Move Left/Right, Shoot  
- ⏳ Timeout: 4200 steps  
- ⚙️ Difficulty: `doom_skill = 5`  
- 🎓 Curriculum: `s1` → `s5` (200,000 steps total)

---


## 🧪 Training Overview

| Scenario           | Algorithms Used         | Training Steps |
|--------------------|-------------------------|----------------|
| basic.cfg          | PPO, A2C, DQN, Hardcoded PPO | 60,000         |
| defend_the_center  | PPO                     | 100,000        |
| deadly_corridor    | PPO (Curriculum Learning)| 200,000 total  |

**Training was visualized with WandB and evaluated using SB3’s `evaluate_policy()` utility.**

---

## 🌐 Flask Web UI

A simple Flask web interface allows you to:
- Visualize how each model works after the training 
- Interact with agents in real time


## 🛠️ How to Run

1. **Clone the repo**  
   ```bash
   git clone https://github.com/kanis777/DeepDoom.git
   cd DeepDoom
   ```
2. **Install dependencies**

  ```bash
  pip install -r requirements.txt
  ```
3. **Launch Flask App**

  ```bash
  cd main
  python app.py
  ```
4. **Explore Notebooks**

    deep_doom.ipynb contains training logic and visualization.

## 📚 Acknowledgements

**Marek Wydmuch, Michał Kempka & Wojciech Jaśkowski, "ViZDoom Competitions: Playing Doom from Pixels," IEEE Transactions on Games, vol. 11, no. 3, pp. 248-259, 2019 (arXiv:1809.03470)**

```bibtex
@article{Wydmuch2019ViZdoom,
  author  = {Marek Wydmuch and Micha{\l} Kempka and Wojciech Ja\'skowski},
  title   = {{ViZDoom} {C}ompetitions: {P}laying {D}oom from {P}ixels},
  journal = {IEEE Transactions on Games},
  year    = {2019},
  volume  = {11},
  number  = {3},
  pages   = {248--259},
  doi     = {10.1109/TG.2018.2877047},
  note    = {The 2022 IEEE Transactions on Games Outstanding Paper Award}
}
```
