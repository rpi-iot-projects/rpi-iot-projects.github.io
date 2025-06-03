---
title: "Smart Lock System"
excerpt: "A secure and robust IoT-based smart lock system using STM32U585-IOT02 board with secure authentication and remote control capabilities."
header:
  image: /assets/images/projects/smart-lock-banner.jpg
  teaser: /assets/images/projects/smart-lock-teaser.jpg
sidebar:
  - title: "Team"
    image: /assets/images/projects/team2-logo.jpg
    image_alt: "Team 2 logo"
    text: "Team 2"
  - title: "Responsibilities"
    text: "IoT Security, Hardware Integration, Mobile App Development"
gallery:
  - url: /assets/images/projects/smart-lock-1.jpg
    image_path: /assets/images/projects/smart-lock-1-th.jpg
    alt: "Smart Lock Prototype"
  - url: /assets/images/projects/smart-lock-2.jpg
    image_path: /assets/images/projects/smart-lock-2-th.jpg
    alt: "Mobile App Interface"
  - url: /assets/images/projects/smart-lock-3.jpg
    image_path: /assets/images/projects/smart-lock-3-th.jpg
    alt: "System Architecture Diagram"
---

# Smart Lock System

A secure IoT-based smart lock system with STM32U585-IOT02 board.

## Components

### App
Simple Python code for the application:
- User authentication and authorization
- Remote lock control interface
- Event logging and notifications

### Controller
Firmware for the STM32U585-IOT02 board:
- Developed using templates from the [ST STM32U5 repo](https://github.com/STMicroelectronics/STM32CubeU5)
- Hardware-level security implementation
- Secure communication protocol

## Key Features

- **Secure Authentication**: Multi-factor authentication for enhanced security
- **Remote Access**: Control your lock from anywhere using the mobile app
- **Access Logs**: Comprehensive logging of all lock/unlock events
- **Battery Monitoring**: Low battery alerts to prevent lockouts

{% include gallery caption="Smart Lock System Images" %}

## GitHub Repository

[View on GitHub](https://github.com/rpi-iot-projects/Team-2-Smart-Lock-System)
