# SmartGPU-Slice (Memory segmentation/Allocation)
AI-Driven GPU Slicing with Kubernetes DRA
# SmartGPU-Slice: AI-Driven GPU Slicing with Kubernetes DRA

##  Overview
SmartGPU-Slice is a Python-based proof-of-concept that showcases how Kubernetes Dynamic Resource Allocation (DRA) can be used to optimize GPU usage through slicing. It simulates AI workloads and demonstrates intelligent, SLA-aware scheduling across fractional GPU resources.

##  Key Features
- Dynamic GPU slice allocation using Kubernetes DRA
- AI-driven workload placement and SLA enforcement
- Integration with MIG/MPS for GPU partitioning
- Real-time metrics collection and visualization
- Modular Python architecture for extensibility

##  Architecture-1
```text
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
```

## 📦 Architecture -2
+-------------------------------------------------------------+
|                      User Interface (Frontend)              |
|  - Cloud Selection (Source/Destination)                     |
|  - Workload Type & SLA Input                                |
+----------------------------+--------------------------------+
                             ↓
+----------------------------+--------------------------------+
|                 Python Orchestration Layer                  |
|  - slice_requester.py      → Creates GPU slice claims       |
|  - workload_simulator.py   → Runs AI inference tasks        |
|  - scheduler_agent.py      → SLA-aware slice allocation     |
|  - metrics_collector.py    → Monitors GPU usage             |
+----------------------------+--------------------------------+
                             ↓
+----------------------------+--------------------------------+
|               Kubernetes Cluster with DRA Enabled           |
|  - DRA Controller & Device Plugin                           |
|  - GPU Slicing via MIG/MPS                                  |
|  - ResourceClaimTemplates for fractional GPU allocation     |
+----------------------------+--------------------------------+
                             ↓
+----------------------------+--------------------------------+
|              GPU Hardware Layer (NVIDIA MIG/MPS)            |
|  - Physical GPU (e.g., A100, L40S)                          |
|  - Sliced into logical partitions (e.g., MIG instances)     |
+----------------------------+--------------------------------+
                             ↓
+----------------------------+--------------------------------+
|               Monitoring & Visualization Stack              |
|  - Prometheus + Grafana                                     |
|  - Optional Streamlit dashboard (slice_visualizer.py)       |
+-------------------------------------------------------------+

##  Modules
| Module                  | Description                                      |
|-----------------------  |--------------------------------------------------|
| `slice_requester.py`    | Creates GPU slice claims via Kubernetes API      |
| `workload_simulator.py` | Runs AI inference tasks using PyTorch/TensorFlow |
| `scheduler_agent.py`    | Decides slice allocation based on SLA, latency   |
| `metrics_collector.py`  | Collects Prometheus metrics for slice usage      |
| `slice_visualizer.py`   | Streamlit dashboard for real-time visualization  |

## Core Python dependencies
kubernetes==26.1.0           # For interacting with Kubernetes API
requests==2.31.0             # For HTTP calls and API integration
PyYAML==6.0.1                # For parsing Kubernetes manifests

# AI Workload Simulation
torch==2.1.0                 # PyTorch for model inference
torchvision==0.16.0          # Image models and transforms
tensorflow==2.14.0           # Optional: TensorFlow support

# Metrics and Monitoring
prometheus-client==0.19.0    # For exposing custom metrics
psutil==5.9.6                # For system resource tracking

# Visualization (Optional)
streamlit==1.29.0            # For real-time dashboard
matplotlib==3.8.0            # For plotting slice usage

# Scheduler Intelligence
scikit-learn==1.3.2          # For SLA prediction and workload classification
numpy==1.26.0                # Core numerical operations
pandas==2.1.1                # Data handling and SLA logs

# Logging and Utilities
loguru==0.7.2                # Elegant logging
tqdm==4.66.1                 # Progress bars for workload simulation


##  Prerequisites
- Kubernetes 1.27+ with DRA enabled
- NVIDIA GPU with MIG or MPS support
- Python 3.9+
- Helm, kubectl, Prometheus, Grafana
- PyTorch or TensorFlow (for workload simulation)

##  Installation
```bash
git clone https://github.com/your-org/smartgpu-slice.git
cd smartgpu-slice
pip install -r requirements.txt

## Usage
1. 	Deploy DRA driver and GPU slice plugin
2. 	Run  to create slice claims
3. 	Launch  to simulate AI tasks
4. 	Monitor slice usage via  and Grafana
5. 	Visualize workload placement with

## Sample Workloads
• 	ResNet image classification
• 	LLM prompt inference (e.g., GPT-2)
• 	Multi-tenant SLA simulation
## Whitepaper
See  for a detailed technical overview, results, and future roadmap.

## Future Enhancements
- OptiFlow integration for SDN-aware routing
- Multi-cloud GPU orchestration
- SLA prediction using reinforcement learning
 Contributors
- Sunil (Architect, Cloud Transformation & Strategy)
- [Your Team Members]
## License
Apache 2.0

