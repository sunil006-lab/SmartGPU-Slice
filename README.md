# SmartGPU-Slice
AI-Driven GPU Slicing with Kubernetes DRA
# SmartGPU-Slice: AI-Driven GPU Slicing with Kubernetes DRA

## 🧠 Overview
SmartGPU-Slice is a Python-based proof-of-concept that showcases how Kubernetes Dynamic Resource Allocation (DRA) can be used to optimize GPU usage through slicing. It simulates AI workloads and demonstrates intelligent, SLA-aware scheduling across fractional GPU resources.

## 🚀 Key Features
- Dynamic GPU slice allocation using Kubernetes DRA
- AI-driven workload placement and SLA enforcement
- Integration with MIG/MPS for GPU partitioning
- Real-time metrics collection and visualization
- Modular Python architecture for extensibility

## 📦 Architecture
+----------------------------+
|  Source Cloud (Azure/GCP) |
+----------------------------+
              ↓
+----------------------------+
|   SmartGPU-Slice Frontend |
+----------------------------+
              ↓
+----------------------------+
| Kubernetes Cluster with DRA|
+----------------------------+
              ↓
+----------------------------------------+
| AI Workload Simulator + Scheduler      |
+----------------------------------------+
              ↓
+----------------------------------------+
| GPU Slice Allocation + Monitoring      |
+----------------------------------------+


## 🛠️ Modules
| Module                  | Description                                      |
|-----------------------  |--------------------------------------------------|
| `slice_requester.py`    | Creates GPU slice claims via Kubernetes API      |
| `workload_simulator.py` | Runs AI inference tasks using PyTorch/TensorFlow |
| `scheduler_agent.py`    | Decides slice allocation based on SLA, latency   |
| `metrics_collector.py`  | Collects Prometheus metrics for slice usage      |
| `slice_visualizer.py`   | Streamlit dashboard for real-time visualization  |

## 📋 Prerequisites
- Kubernetes 1.27+ with DRA enabled
- NVIDIA GPU with MIG or MPS support
- Python 3.9+
- Helm, kubectl, Prometheus, Grafana
- PyTorch or TensorFlow (for workload simulation)

## ⚙️ Installation
```bash
git clone https://github.com/your-org/smartgpu-slice.git
cd smartgpu-slice
pip install -r requirements.txt

🚦 Usage
1. 	Deploy DRA driver and GPU slice plugin
2. 	Run  to create slice claims
3. 	Launch  to simulate AI tasks
4. 	Monitor slice usage via  and Grafana
5. 	Visualize workload placement with

📈 Sample Workloads
• 	ResNet image classification
• 	LLM prompt inference (e.g., GPT-2)
• 	Multi-tenant SLA simulation
📄 Whitepaper
See  for a detailed technical overview, results, and future roadmap.

🧪 Future Enhancements
- OptiFlow integration for SDN-aware routing
- Multi-cloud GPU orchestration
- SLA prediction using reinforcement learning
🤝 Contributors
- Sunil (Architect, Cloud Transformation & Strategy)
- [Your Team Members]
📜 License
Apache 2.0

