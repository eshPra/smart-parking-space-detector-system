# Smart Parking Space Detector System

A smart solution for real-time parking space detection and monitoring, designed for easy deployment on a Raspberry Pi 3. This project leverages computer vision and IoT to identify available parking spots, providing live updates to users via a web dashboard or mobile device.

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [System Architecture](#system-architecture)
- [Hardware Requirements](#hardware-requirements)
- [Software Requirements](#software-requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Deployment on Raspberry Pi 3](#deployment-on-raspberry-pi-3)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

The Smart Parking Space Detector System uses a camera and computer vision algorithms to automatically detect available parking slots in a parking lot. The system is optimized for the Raspberry Pi 3, making it a cost-effective and portable solution for smart parking management.

---

## Features

- **Real-time Parking Detection:** Detects and updates the status of each parking slot.
- **Web Dashboard:** Visual display of parking occupancy status.
- **Mobile Friendly:** Responsive dashboard for mobile device viewing.
- **Lightweight & Portable:** Designed for easy deployment on Raspberry Pi 3.
- **Customizable Slot Layout:** Configure according to your parking lot.
- **Notification Support:** Optional alerts for available/free slots.
- **Open Source:** Community contributions are welcome.

---

## System Architecture

```
+------------------+      +-------------------+
| Raspberry Pi 3   | ---> | Web Dashboard/API |
| + Camera Module  |      +-------------------+
| + CV Algorithms  |                 |
+------------------+                 v
                           +---------------------+
                           | User Devices        |
                           | (PC / Mobile Phone) |
                           +---------------------+
```

---

## Hardware Requirements

- **Raspberry Pi 3 (Model B or B+)**
- **Raspberry Pi Camera Module** (or USB webcam)
- **MicroSD Card** (16GB recommended)
- **Power Supply for Pi**
- **WiFi Dongle** (if not using Pi 3's onboard WiFi)
- **Optional:** External LEDs or displays for local slot indication

---

## Software Requirements

- **OS:** Raspberry Pi OS (Raspbian) or compatible Linux
- **Python 3.x**
- **OpenCV** for image processing
- **Flask** (or Django/FastAPI) for web dashboard/API
- **NumPy**
- **Requests**
- **Other Python dependencies:** See [`requirements.txt`](requirements.txt)

---

## Installation

### 1. Prepare the Raspberry Pi

- Flash Raspberry Pi OS onto your microSD card.
- Boot your Pi and connect to a network.
- Enable the camera interface via `raspi-config` if using the Pi camera.

### 2. Clone the Repository

```bash
git clone https://github.com/eshPra/smart-parking-space-detector-system.git
cd smart-parking-space-detector-system
```

### 3. Install Dependencies

```bash
sudo apt update
sudo apt install python3-opencv python3-pip
pip3 install -r requirements.txt
```

### 4. Configure the System

Edit `config.json` or the relevant configuration file to set the number and location of parking slots, camera parameters, and server settings.

---

## Usage

### 1. Start the Detection Service

```bash
python3 detect_parking.py
```
(or the main application file, e.g., `app.py`)

### 2. Access the Dashboard

Open a browser and go to `http://<raspberry-pi-ip>:<port>/` to view the status dashboard.

---

## Configuration

- **Slot Setup:** Define coordinates for each parking spot in the configuration file.
- **Camera Settings:** Adjust resolution and frame rate as needed.
- **Notification Settings:** Enable/disable and customize notifications.

Refer to the commented sections in `config.json` for further customization.

---

## Deployment on Raspberry Pi 3

1. **Connect and position the camera** to cover all required parking spots.
2. **Configure WiFi/Ethernet** for network access.
3. **Run the detection script** on boot by adding it to `rc.local` or as a systemd service:
    ```bash
    sudo nano /etc/rc.local
    # Add before 'exit 0':
    python3 /home/pi/smart-parking-space-detector-system/detect_parking.py &
    ```
4. **Access the dashboard** from any device on the same network.
5. **Optional:** Set up port forwarding or a VPN for remote monitoring.

---

## Troubleshooting

- **Camera Not Detected:** Check connection and enable the camera in `raspi-config`.
- **Web Dashboard Not Loading:** Ensure the Flask server is running and the port is open.
- **Detection Inaccurate:** Adjust camera angle, lighting, or retrain detection regions.
- **Performance Issues:** Lower camera resolution or frame rate.

---

## Contributing

Pull requests are welcome! Please fork the repository, create a feature branch, and submit your PR. Open issues for feature requests or bug reports.

---

## License

This project is licensed under the MIT License. See [`LICENSE`](LICENSE) for details.

---

## Authors & Credits

- [eshPra](https://github.com/eshPra) and contributors.

---

## Acknowledgements

- OpenCV community
- Raspberry Pi Foundation
- Flask project

---

Feel free to customize this README for your specific setup or needs!
