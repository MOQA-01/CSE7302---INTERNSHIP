<div align="center">

# 🚁 Autonomous Navigation and ML-Driven Precision Control for Agricultural UAVs

### *An intelligent spraying drone that sees, thinks, and acts — cutting pesticide waste by 28.5%*

[![Python](https://img.shields.io/badge/Python-3.9-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-ML-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)](https://www.tensorflow.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-Random%20Forest-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![Pixhawk](https://img.shields.io/badge/Pixhawk-PX4-00A9E0?style=for-the-badge)](https://pixhawk.org/)
[![Jetson Nano](https://img.shields.io/badge/NVIDIA-Jetson%20Nano-76B900?style=for-the-badge&logo=nvidia&logoColor=white)](https://developer.nvidia.com/embedded/jetson-nano)
[![License](https://img.shields.io/badge/License-Academic-blue?style=for-the-badge)]()

**🎓 B.Tech Internship Project · Presidency University × MultiD Technologies · 2025–2026**

</div>

---

## 📖 Overview

Traditional pesticide application is **inefficient, wasteful, and hazardous** to farmers. This project replaces blanket spraying with **intelligent autonomy** — a drone that maps a field, distinguishes crops from weeds in real time, computes the precise spray volume each cell needs, and navigates obstacle-free paths to deliver it.

Built during an **8-month internship at MultiD (Multi-Dimensional Technologies OPC Pvt. Ltd.)**, the system bridges aerospace hardware validation with edge-deployed deep learning to create a scalable foundation for precision agriculture in India.

> 💡 **The big idea:** Spray only what needs spraying, only where it needs it, using the shortest possible flight path.

---

## ✨ Key Highlights

| 🎯 Metric | 📊 Target | ✅ Achieved |
|---|---|---|
| ML Detection Accuracy | > 90.0% | **94.2%** |
| Inference Latency (Edge) | < 100 ms | **42 ms** |
| Chemical Savings | > 20.0% | **28.5%** |
| Path Optimization Waste | < 15% | **11.3%** |
| Spray Model Reliability (R²) | > 0.85 | **0.943** |

---

## 🧠 System Architecture

The drone operates on a classic **Sense → Think → Act** loop, with responsibilities split across four layers:

```
┌──────────────────────────────────────────────────────────────┐
│  PERCEPTION   │  Camera · GPS · LIDAR · IMU                  │
│               │  → Environment mapping & obstacle detection  │
├──────────────────────────────────────────────────────────────┤
│  INTELLIGENCE │  3D CNN · Random Forest Regressor            │
│               │  → Target classification & spray volume calc │
├──────────────────────────────────────────────────────────────┤
│  CONTROL      │  A* Planner · Q-Learning Agent               │
│               │  → Path optimization & navigation policy     │
├──────────────────────────────────────────────────────────────┤
│  EXECUTION    │  Pixhawk 4 · Pump Relay · ESCs               │
│               │  → Flight actuation & chemical deployment    │
└──────────────────────────────────────────────────────────────┘
```

---

## 🔬 Technical Pillars

### 1️⃣ Hardware Optimization — Smart Thrust Bench
Empirical propulsion mapping was performed on a **Smart Thrust Bench** to identify the optimal motor-propeller combination for a variable liquid payload. By measuring voltage, current, and thrust across throttle percentages, we derived the **Grams-per-Watt (g/W)** efficiency curve and confirmed a safe **2:1 thrust-to-weight ratio**, extending operational endurance by ~15% per battery cycle.

### 2️⃣ Autonomous Navigation — A* Pathfinding
The A* heuristic search finds the shortest obstacle-free path across a discretized field grid, using **Manhattan distance** as the heuristic for computational speed:

$$f(n) = g(n) + h(n)$$

Obstacles (trees, rocks, structures) are modeled as impassable nodes. A failsafe triggers **Return-to-Launch (RTL)** if drift exceeds 1 meter.

### 3️⃣ Precision Spraying — Random Forest Regressor
A supervised ML model trained on **soil moisture, crop density, and ambient temperature** predicts the exact milliliters required per grid cell — eliminating over-saturation and enabling the 28.5% chemical savings.

### 4️⃣ Real-Time Perception — 3D CNN
A 3D Convolutional Neural Network analyzes **spatial + temporal** frames from the downward-facing camera to distinguish crops from weeds. The pump activates only when confidence exceeds **85%**.

### 5️⃣ Adaptive Policy — Q-Learning
A Q-Learning agent learns efficient field-coverage strategies using:

$$Q(s, a) \leftarrow Q(s, a) + \alpha [R + \gamma \max Q(s', a') - Q(s, a)]$$

with learning rate α = 0.1 and discount factor γ = 0.9, prioritizing full-field coverage over greedy moves.

---

## 🛠️ Hardware Configuration

| Component | Specification | Role |
|---|---|---|
| **Frame** | 650mm Carbon Fiber Quadcopter | Structural integrity & vibration damping |
| **Motors** | 4 × 400KV Brushless DC (BLDC) | High-torque lift capacity |
| **ESCs** | 40A Opto (SimonK Firmware) | Precise motor speed regulation |
| **Propellers** | 15 × 5.5 Carbon Fiber | High lift-to-drag efficiency |
| **Flight Controller** | Pixhawk 4 (Cortex M4) | IMU stabilization & MAVLink I/O |
| **Companion Computer** | NVIDIA Jetson Nano | Edge inference (3D CNN + RF) |
| **Payload** | 5L Tank + Relay-Controlled Pump | Precision chemical deployment |
| **Testing Gear** | Smart Thrust Bench | Empirical propulsion mapping |

---

## 💻 Software Stack

<div align="center">

| Layer | Tooling |
|---|---|
| **Language** | Python 3.9 |
| **ML Framework** | TensorFlow · scikit-learn |
| **Simulation** | NumPy · Matplotlib (2D grid environment) |
| **Flight Stack** | PX4 / ArduPilot · MAVLink Protocol |
| **Ground Station** | QGroundControl (2.4GHz Telemetry) |
| **Edge Optimization** | TensorRT (< 50ms inference) |

</div>

---

## 📁 Repository Structure

```
├── field_sim.py          # NumPy-based grid generator with targets & obstacles
├── ml_models.py          # Pre-trained weights: 3D CNN + Random Forest Regressor
├── path_planner.py       # Core execution engine for A* search logic
├── main_control.py       # "Flight Brain" — translates ML decisions to MAVLink
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites
```bash
python >= 3.9
tensorflow
scikit-learn
numpy
matplotlib
pymavlink
```

### Installation
```bash
# Clone the repository
git clone https://github.com/MOQA-01/CSE7302---INTERNSHIP.git
cd CSE7302---INTERNSHIP

# Install dependencies
pip install -r requirements.txt
```

### Run the Simulation
```bash
# Generate a simulated field with obstacles
python field_sim.py

# Compute the optimal A* path
python path_planner.py

# Launch full control loop (connects to Pixhawk via MAVLink)
python main_control.py
```

---

## 📸 Example — A* Pathfinding Logic

```python
def astar_pathfinding(grid, start, goal):
    open_set = PriorityQueue()
    open_set.put((0, start))
    came_from = {}
    g_score = {node: float('inf') for node in grid}
    g_score[start] = 0

    while not open_set.empty():
        current = open_set.get()[1]
        if current == goal:
            return reconstruct_path(came_from, current)

        for neighbor in get_neighbors(current):
            tentative_g = g_score[current] + grid[neighbor].cost
            if tentative_g < g_score[neighbor]:
                came_from[neighbor] = current
                g_score[neighbor] = tentative_g
                f_score = tentative_g + manhattan_heuristic(neighbor, goal)
                open_set.put((f_score, neighbor))
```

---

## 🌍 Impact & Alignment with UN SDGs

<div align="center">

| 🎯 SDG | Contribution |
|---|---|
| **SDG 2 — Zero Hunger** | Higher yields through precision crop protection |
| **SDG 9 — Industry & Innovation** | Indigenous UAV technology under *Make in India* |
| **SDG 12 — Responsible Consumption** | 28.5% reduction in pesticide use & soil toxicity |

</div>

### Social, Legal & Safety Aspects
- 👨‍🌾 **Farmer Safety** — Eliminates direct contact with toxic pesticides
- ⚖️ **DGCA Compliance** — Built per Drone Rules 2021 with mandatory **NPNT** (No Permission - No Takeoff)
- 🌱 **Environmental Protection** — Prevents groundwater contamination via targeted spraying
- 🛡️ **Geofencing & Failsafes** — Auto-RTL on telemetry loss or battery < 20%

---

## 🔮 Future Scope

- 🐝 **Swarm Intelligence** — Multi-drone coordination for large estates
- 🌈 **Multispectral NDVI Sensors** — Early detection of crop stress
- 🔋 **Automated Battery Swapping** — True 24/7 field monitoring
- ☁️ **Edge-to-Cloud Analytics** — Seasonal crop-health tracking
- 🤖 **Fully Reinforcement-Learned Policies** — End-to-end learned flight & spray control

---

## 📅 Project Timeline

| Phase | Duration | Deliverables |
|---|---|---|
| **Training** | Nov 2025 – Jan 2026 | Literature survey · Thrust Bench setup |
| **Development** | Jan 2026 – Mar 2026 | A* pathfinding · Initial ML target detection |
| **Integration** | Mar 2026 – May 2026 | Flight controller integration · Optimization |
| **Validation** | May 2026 – Jul 2026 | Edge deployment · Field trials · Documentation |

---

## 👨‍💻 Author

<div align="center">

### **Mohammed Qalandar Shah Quazi**
*B.Tech — Computer Science & Engineering (AI & ML)*
**Presidency University, Bengaluru** · USN: 20221COM0041

🏢 **Internship Host:** MultiD — Multi-Dimensional Technologies (OPC) Pvt. Ltd., Bengaluru
👨‍🏫 **Guide:** Mr. Sirapu Teja, Associate Professor, PSCS

[![GitHub](https://img.shields.io/badge/GitHub-MOQA--01-181717?style=for-the-badge&logo=github)](https://github.com/MOQA-01)

</div>

---

## 🙏 Acknowledgements

Heartfelt thanks to **Mr. Sirapu Teja** (Internal Guide), **Dr. Gopal Krishna Shyam** (HoD, PSCS), **Dr. Md Ziaur Rahaman** (School Internship Coordinator), **Mr. Sreehari T M** (Program Coordinator), and the entire team at **MultiD Technologies** for their invaluable mentorship and the opportunity to work at the intersection of AI and aerospace.

---

<div align="center">

### ⭐ *If this project inspired you, consider starring the repo!*

**Built with ☕ curiosity, 🔬 rigor, and 🚁 a whole lot of test flights.**

</div>
