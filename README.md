# ignore the ap_nodes , sumo and lstm_model folders for some reasons these are not deleting !!!


# SDN-LSTM Based Network Congestion Reduction for Autonomous Vehicles

This project integrates **Software Defined Networking (SDN)** with **Long Short-Term Memory (LSTM)** neural networks to proactively reduce network congestion in vehicular networks. It predicts traffic patterns at Access Points (APs) using machine learning and reroutes data flows using SDN to the least congested AP.

##  Project Components

### 1. SDN Controller (Ryu-based)
- Receives real-time LSTM predictions over UDP.
- Dynamically reroutes traffic between APs based on predicted congestion.
- Installs and deletes OpenFlow rules accordingly.

### 2. Machine Learning Predictor (LSTM)
- Trained LSTM models to predict:
  - Average latency
  - Bandwidth usage
  - Packet rate
  - Speed, acceleration, and active nodes
- Sends prediction batches every 5 seconds to the Ryu controller.

### 3. Simulation Environment
- **Mininet**: Emulates network topology with switches as APs and hosts as vehicles.
- **SUMO**: Simulates vehicle movement and generates mobility data.
- **Python Scripts**: Extract vehicle and network data for training LSTM models.

---

##  Installation

Follow the steps below to set up the SDN-LSTM Congestion Reduction project on a Ubuntu-based system.

### 1. System Dependencies

Install required packages:

```
sudo apt update
sudo apt install -y git python3 python3-pip python3-venv mininet sumo sumo-tools
sudo apt install -y sumo-gui
python3 -m venv sdn_lstm_env
source sdn_lstm_env/bin/activate
pip install --upgrade pip

pip install \
  ryu \
  tensorflow \
  pandas \
  numpy \
  scikit-learn \
  matplotlib \
  seaborn \
  scapy \
  keras

```

##Clone repo
```
git clone https://github.com/your-username/sdn-lstm-vehicular.git
cd sdn-lstm-vehicular
```





