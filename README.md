# Project S.M.A.L.L. (Synchronized Monitoring & Autonomous Localized-response Layer)

An autonomous multi-agent disaster management swarm system utilizing 4 aerial drones and 5 ground tracking units to safely coordinate real-time hazardous area mapping with hot-swappable hardware architecture.

## ⚖️ License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details (Approved OSI License).

## 🚀 Setup & Installation

### Prerequisites
- Python 3.10+
- Arduino IDE (with ESP32 board manager installed)
- Raspberry Pi OS (for central edge node deployment)

### Edge Server Setup (Raspberry Pi)
1. Clone the public repository:
   ```bash
   git clone https://github.com
   cd Project-SMALL/server
   ```
2. Install Required Packages:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the Dashboard Local Flask Hub:
   ```bash
   python app.py
   ```

### Swarm Node Firmware Deployment (ESP32 Agents)
1. Navigate to the `/firmware` directory.
2. Open `agent_mesh.ino` in your Arduino IDE.
3. Verify and compile the flash program using the ESP32 Dev Module board configuration.
4. Upload firmware to your respective ground and aerial agents via serial connection.

---

## 🧠 AI Architecture & Hackathon Stack Integration

### 1. Swarm Mission Context Optimization via NVIDIA Llama-3.1-Nemotron-70B
During multi-agent tracking, processing extensive unstructured environmental text feeds and raw telemetry updates directly on the hardware is highly compute-prohibitive. Project S.M.A.L.L. implements the open-source **NVIDIA Llama-3.1-Nemotron-70B** model to analyze real-time text descriptions from local sensor nodes. Nemotron acts as an on-demand edge-coordination oracle, transforming sparse environmental readings into structured situational reports. It evaluates complex hazard variables, optimizes the swarm's localized micro-agent pathing matrices, and prioritizes search patterns safely before human operators toggle manual control parameters.

### 2. High-Throughput Token Generation via Token Factory
To support highly fluid, live interactions within the centralized dashboard, telemetry streaming requires lightning-fast inference turnarounds. We integrated Nebius's **Token Factory** API infrastructure to power our Nemotron pipelines. The high token-per-second throughput offered by Token Factory allowed the master pathfinding controller to continuously stream and structure mission logs at absolute peak speeds. This radically accelerated our debugging workflow, enabling rapid testing of coordinate spatial vectors under highly tight development constraints without encountering severe rate limits or execution lag.

### 3. Distributed Infrastructure via Nebius AI Services
The compute-heavy text parsing engine is offloaded from the localized Raspberry Pi hardware tier by utilizing high-performance cloud compute instances managed on the **Nebius AI Platform**. By processing incoming text streams inside optimized container spaces hosted via Nebius Services, Project S.M.A.L.L. maintains a low-latency, secure data bridge between physical ad-hoc ESP32 networks and state-of-the-art open-source physical AI pipelines.
