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

Install required packages: this is LSTM part setup 

```
sudo apt update
sudo apt install -y git python3 python3-pip python3-venv mininet sumo sumo-tools
sudo apt install -y sumo-gui
python3 -m venv sdn_lstm_env
source sdn_lstm_env/bin/activate
pip install --upgrade pip

pip install \
  tensorflow \
  pandas \
  numpy \
  scikit-learn \
  matplotlib \
  seaborn \
  scapy \
  keras

```
## After having setup for LSTM open a new terminal and install/ setup ryu and mininet 
```
# Update and install Python 3.10
sudo apt update
sudo apt install -y software-properties-common
sudo add-apt-repository -y ppa:deadsnakes/ppa
sudo apt update
sudo apt install -y python3.10 python3.10-venv python3.10-dev python3.10-distutils

# Set python3.10 as default (optional, skip if you want to use system python)
# sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.10 1

# Create and activate a virtual environment for Ryu
python3.10 -m venv ryu_env
source ryu_env/bin/activate

# Upgrade pip and install Ryu dependencies
pip install --upgrade pip
pip install msgpack-python eventlet greenlet netaddr oslo.config tinyrpc webob

# Clone Ryu and install it
git clone https://github.com/osrg/ryu.git
cd ryu
pip install .
```

```
# Test Ryu installation
ryu-manager --version
# should show the version 
```
```
cd ..
```

## to activate and decactivate the env 
```
#activate ryu
source ryu_env/bin/activate
```
```
#activate lstm
source sdn_lstm_env/bin/activate
```
```
deactivate
```

## Install mininet 

```
sudo apt install -y git make gcc python3-pip openvswitch-switch openvswitch-common \
    openvswitch-test openvswitch-pki openvswitch-ipsec net-tools iputils-ping \
    iproute2 ethtool socat xterm

# Clone Mininet repo
git clone https://github.com/mininet/mininet.git
cd mininet

# Install Mininet using the install script (only core)
sudo util/install.sh -n3
```

```

# Test Mininet installation
sudo mn --test pingall

```
```
cd ..
```

## Clone repo
```
git clone https://github.com/your-username/sdn-lstm-vehicular.git
cd sdn-lstm-vehicular
```





