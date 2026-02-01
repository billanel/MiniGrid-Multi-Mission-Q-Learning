# MiniGrid Multi-Mission Q-Learning

A reinforcement learning project using Q-Learning to train an agent to navigate MiniGrid environments with multiple color-coded missions.

## 🎯 Overview

This project trains an agent to solve 4 different missions in the same 8x8 MiniGrid environment:
- 🔴 **Red**: Navigate to the red door
- 🟢 **Green**: Navigate to the green door
- 🔵 **Blue**: Navigate to the blue door
- 🟡 **Yellow**: Navigate to the yellow door

The agent learns to distinguish between different missions and find the optimal path for each one.

## 🚀 Installation

### Prerequisites
- Python 3.8+
- pip

### Setup

1. **Clone the repository**
```bash
git clone https://github.com/your-username/minigrid-qlearning.git
cd minigrid-qlearning
```

2. **Create a virtual environment (recommended)**
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

## 📝 Usage

### Training with logs
```bash
python src/train_4missions_perfect.py
```

This will:
- Train the agent for 8000 episodes
- Display statistics every 500 episodes
- Save training results

### Real-time visualization
```bash
python src/realtime.py
```

Shows the agent in action navigating the environment with delays for better visualization.

## 📊 Configuration

Training parameters are located at the top of each script:

```python
# Environment
ENV_ID = "MiniGrid-GoToDoor-8x8-v0"
TRAIN_SEEDS = [3657, 8182, 9656, 10255]  # 4 seeds for 4 missions

# Hyperparameters
ALPHA = 0.1        # Learning rate
GAMMA = 0.99       # Discount factor
EPS_START = 1.0    # Initial exploration
EPS_END = 0.05     # Final exploration
EPS_DECAY = 0.9992 # Exploration decay

# Training
EPISODES = 8000
MAX_STEPS = 100
```

## 🧠 Architecture

### Main files

- `src/train_4missions_perfect.py` - Complete training script with logging
- `src/realtime.py` - Real-time visualization of the agent
- `src/config.py` - Centralized configuration (optional)

### Algorithm

**Q-Learning**: Off-policy reinforcement learning
- State = (position_x, position_y, direction, mission_id)
- Actions = [left, right, forward, done]
- Reward = +1 for success, -1 for unnecessary steps

## 📈 Expected Results

After training:
- The agent should learn all 4 different paths
- Convergence to near-optimal solutions after ~4000 episodes
- Average resolution time: ~10-15 steps per mission

## 🔧 Development

### Adding new missions

Modify the `get_goal_id()` function:
```python
def get_goal_id(mission: str) -> int:
    m = mission.lower()
    if "red" in m: return 0
    if "green" in m: return 1
    if "blue" in m: return 2
    if "yellow" in m: return 3
    # Add here
    if "purple" in m: return 4
    return -1
```

### Improving hyperparameters

Experiment with:
- `ALPHA`: Higher = faster learning but more unstable
- `GAMMA`: Closer to 1 = consider long-term future
- `EPS_DECAY`: Closer to 1 = slower exploration decay

## 🐛 Troubleshooting

**Problem**: Agent is not learning
- Solution: Increase `EPISODES` or decrease `EPS_DECAY`

**Problem**: MiniGrid import error
- Solution: `pip install minigrid --upgrade`

## 📚 References

- [Gymnasium Documentation](https://gymnasium.farama.org/)
- [MiniGrid Repository](https://github.com/Farama-Foundation/Minigrid)
- [Q-Learning Theory](https://en.wikipedia.org/wiki/Q-learning)

## 📄 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for more details.

## 👤 Author

[Your name/username]

## 🤝 Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## ⭐ If you like this project

Feel free to star it on GitHub!
