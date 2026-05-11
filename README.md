# Raspberry Pi 4G Camera Streaming System

Experimental Raspberry Pi based remote camera streaming system using LTE connectivity, Cloudflare Tunnel and Flask/OpenCV.

## Project Status

Prototype / Research Project

This repository documents the development process of a low-cost remote camera streaming architecture over 4G/LTE networks using Raspberry Pi.

Some original source files were lost over time, however the hardware setup, network architecture, configuration process and implementation details are preserved in the included technical reports.

---

# Overview

The project focuses on establishing a remote video transmission system over mobile LTE infrastructure.

Main goals:

- Establish 4G internet connectivity on Raspberry Pi
- Stream live camera feed remotely
- Create a low-cost remote monitoring architecture
- Test alternative communication methods without requiring static IP SIM cards
- Explore secure remote access using Cloudflare Tunnel

---

# Features

- Raspberry Pi LTE connectivity
- Remote live camera streaming
- Flask/OpenCV based video serving
- Motion based alternative streaming
- Cloudflare Tunnel integration
- Experimental server-assisted device pairing architecture
- Low-cost remote monitoring approach
- Static IP alternative communication design

---

# Hardware Used

- Raspberry Pi 4 (8GB / 4GB)
- Sixfab 3G/4G LTE Base HAT
- Quectel EC25-EUX mini PCIe LTE modem
- SIM card
- LTE antennas
- USB camera
- SMA connection cables

---

# Software Stack

- Raspberry Pi OS (32-bit Legacy)
- PPP connection scripts
- Motion
- Flask
- OpenCV
- Cloudflare Tunnel

---

# LTE Connection Setup

The project uses a Sixfab LTE Base HAT with a Quectel EC25 LTE modem to establish mobile internet connectivity.

Main setup steps:

1. Install LTE modem onto Sixfab HAT
2. Connect antennas
3. Attach HAT to Raspberry Pi
4. Configure PPP scripts
5. Set carrier APN
6. Establish LTE connection using:

```bash
sudo pon
```

The system was tested using a 32-bit Raspberry Pi OS version due to compatibility issues observed with newer 64-bit releases.

---

# Remote Streaming System

Two streaming approaches were explored:

## 1. Motion Based Streaming

Motion was configured to provide lightweight remote camera streaming.

Configuration included:

- daemon mode
- remote access
- stream access
- camera resolution tuning

---

## 2. Flask + OpenCV Streaming

A Flask based MJPEG streaming server was also tested.

The Raspberry Pi captures frames using OpenCV and serves them over HTTP.

Example architecture:

Camera → Raspberry Pi → Flask Server → Internet → Remote Client

---

# Cloudflare Tunnel Integration

Cloudflare Tunnel was used to expose the local Flask stream securely to the internet without direct port forwarding.

Advantages:

- Secure remote access
- Easier deployment
- No public static IP required
- Cloudflare protected connection

The tunnel forwards traffic to:

```text
http://localhost:5000
```

---

# Alternative Architecture Idea

An additional experimental idea explored the use of a lightweight intermediary server.

Purpose:

- Pair remote devices dynamically
- Eliminate the need for static-IP SIM cards
- Maintain connection information
- Re-establish broken sessions automatically

Possible lightweight server hardware:

- Raspberry Pi Zero
- Small VPS
- Local server with Cloudflare Tunnel

This architecture remains experimental and requires further development.

---

# Known Problems

Current limitations observed during testing:

- FPS instability
- Image quality fluctuations
- LTE latency
- Reconnection reliability
- Hardware/network dependency
- No finalized production-ready implementation yet

---

# Future Improvements

- WebRTC integration
- Better compression methods
- GPU acceleration
- OpenCV based image processing
- Automatic reconnection system
- VPN/Tailscale support
- Lower latency streaming
- Adaptive bitrate control
- Better power optimization

---

# Repository Structure

```text
project/
│
├── README.md
├── docs/
├── images/
├── architecture/
└── future-work.md
```

---

# Documentation

Technical reports and setup screenshots are included inside the `docs/` directory.

Topics covered:

- LTE modem installation
- PPP setup
- APN configuration
- Motion configuration
- Cloudflare Tunnel setup
- Flask/OpenCV streaming
- Experimental network architecture

---

# Disclaimer

This repository is primarily intended for research, experimentation and educational purposes.

The system is not production-ready and still requires significant optimization and further testing.

---

# Author

Hasan Aksoy
