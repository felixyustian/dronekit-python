# DroneKit-Python



This repository contains the **DroneKit-Python** library, which allows developers to create Python applications that run on an onboard companion computer (like a Raspberry Pi) and communicate with an ArduPilot flight controller using the MAVLink protocol.

## 🚁 Overview

DroneKit-Python enables you to:
* **Connect** to a vehicle via UDP, TCP, or Serial (Telemetry Radio).
* **Get and Set** vehicle state (Mode, Armed status, Battery, GPS, Attitude).
* **Control** movement (Velocity, Position, Waypoints).
* **Manage** autonomous missions.

It is widely used for research, academic projects (like KRTI/KRBAI), and custom drone applications.

## 🛠️ Technology Stack

* **Language:** Python 2.7 / 3.x
* **Protocol:** MAVLink (via `pymavlink`)
* **Supported Firmwares:** ArduCopter, ArduPlane, ArduRover

## 📋 Prerequisites

* A drone or simulator (SITL) running ArduPilot.
* Python is installed on your ground station or companion computer.
* A connection link (USB, Telemetry Radio, or WiFi).

## 🔧 Installation

To install this library from the source code in this repository:

1.  **Clone the Repository**
    ```bash
    git clone [https://github.com/felixyustian/dronekit-python.git](https://github.com/felixyustian/dronekit-python.git)
    cd dronekit-python
    ```

2.  **Install Dependencies**
    ```bash
    pip install pymavlink
    ```

3.  **Install DroneKit**
    ```bash
    python setup.py install
    ```

## 🚀 Quick Start Example

Here is a simple script to connect to a drone, print its heartbeat status, and arm the motors.

Create a file named `hello_drone.py`:

```python
from dronekit import connect, VehicleMode
import time

# Connect to the Vehicle
# Use '/dev/ttyUSB0' for Linux serial, or '127.0.0.1:14550' for SITL
print("Connecting to vehicle...")
vehicle = connect('127.0.0.1:14550', wait_ready=True)

# Get some vehicle attributes (state)
print(f"Get some vehicle attribute values:")
print(f" GPS: {vehicle.gps_0}")
print(f" Battery: {vehicle.battery}")
print(f" Last Heartbeat: {vehicle.last_heartbeat}")
print(f" Is Armable?: {vehicle.is_armable}")
print(f" System status: {vehicle.system_status.state}")
print(f" Mode: {vehicle.mode.name}")

# Close vehicle object before exiting script:
vehicle.close()
print("Completed")
```

Run the script:
```bash
python hello_drone.py
```

## 📚 Documentation & Resources
Official Documentation: https://dronekit-python.readthedocs.io/

ArduPilot Dev Docs: https://ardupilot.org/dev/

MAVLink Guide: https://mavlink.io/en/

## 📄 License
This project is open-source and typically distributed under the Apache 2.0 License.
