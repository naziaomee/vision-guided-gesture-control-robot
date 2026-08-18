# 🤖 Vision-Guided Gesture-Controlled Robotic Vehicle with Object Manipulation

<p align="center">
  <img src="images/robot.jpg" alt="Vision-Guided Gesture-Controlled Robotic Vehicle" width="700"/>
</p>

<p align="center">
  <b>A low-cost robotic vehicle controlled through hand gestures with real-time video streaming and object manipulation.</b>
</p>

---

## 📌 Overview

This project presents a **vision-guided, gesture-controlled robotic vehicle** designed to provide intuitive remote control and object manipulation.

The system combines:

* 🖐️ Hand gesture-based navigation
* 📡 Wireless communication
* 📷 Real-time video streaming
* 🤖 4WD robotic vehicle movement
* 🦾 Servo-controlled object manipulation
* 📟 Real-time OLED status monitoring

The operator wears a glove equipped with an **ADXL345 accelerometer** and joystick. Hand movements are translated into directional commands and transmitted wirelessly to the robotic vehicle using **ESP32** microcontrollers.

An **ESP32-CAM** provides live visual feedback, while a servo-driven gripper allows the robot to pick up, hold, and release objects.

---

## ✨ Features

| Feature                | Description                                             |
| ---------------------- | ------------------------------------------------------- |
| 🖐️ Gesture Control    | Control robot movement using hand tilting               |
| 🚗 4WD Navigation      | Forward, backward, left, right and stop                 |
| 📡 Wireless Control    | ESP32-based Wi-Fi communication                         |
| 📷 Live Video          | Real-time video feed using ESP32-CAM                    |
| 🦾 Object Manipulation | Servo-controlled robotic gripper                        |
| 🎮 Joystick Control    | Manual gripper positioning                              |
| 📟 OLED Display        | Displays gesture, sensor and system information         |
| 💰 Low Cost            | Built using affordable and readily available components |

---

## 🏗️ System Architecture

The system is divided into three major computing units:

```text
                 ┌─────────────────────┐
                 │   Gesture Glove     │
                 │                     │
                 │ ESP32               │
                 │ ADXL345             │
                 │ Joystick            │
                 │ OLED                │
                 └──────────┬──────────┘
                            │
                         Wi-Fi / UDP
                            │
                            ▼
                 ┌─────────────────────┐
                 │   Vehicle Control   │
                 │                     │
                 │ ESP32               │
                 │ L298N Motor Driver  │
                 │ 4WD Motors          │
                 │ Servo + Gripper     │
                 └─────────────────────┘
                            │
                            │
                 ┌──────────▼──────────┐
                 │     ESP32-CAM       │
                 │                     │
                 │ Live Video Stream   │
                 └──────────┬──────────┘
                            │
                           HTTP
                            │
                            ▼
                    ┌───────────────┐
                    │ Web Browser   │
                    │ Live View     │
                    └───────────────┘
```

The project uses a decentralized architecture consisting of a **gesture controller, vehicle controller, and independent vision unit**.

---

## 🔄 How It Works

```text
Hand Movement
      ↓
ADXL345 Accelerometer
      ↓
Gesture Classification
      ↓
ESP32 Glove Controller
      ↓
Wi-Fi / UDP Communication
      ↓
Vehicle ESP32
      ↓
Command Processing
      ↓
L298N Motor Driver
      ↓
4WD Robot Movement
```

For object manipulation:

```text
Joystick
   ↓
ESP32 Glove
   ↓
Wireless Command
   ↓
Vehicle ESP32
   ↓
Servo Motor
   ↓
Robotic Gripper
   ↓
Pick / Hold / Release Object
```

At the same time, the **ESP32-CAM continuously provides a live video stream** so the operator can observe the robot's environment remotely.

---

## 🧰 Hardware Components

* ESP32 Development Kit × 2
* ESP32-CAM
* ADXL345 3-Axis Accelerometer
* L298N H-Bridge Motor Driver
* 4WD Robotic Chassis
* 4 × DC Motors
* Servo Motor
* Robotic Gripper
* 0.96" I2C OLED Display
* Analog Joystick
* LiPo Battery
* 5V USB Power Bank
* Breadboard
* Jumper Wires

The complete hardware specification and component purposes are documented in the project report.

---

## 💻 Software & Technologies

* **C++**
* **Arduino IDE**
* **ESP32**
* **ESP32-CAM**
* **Wi-Fi**
* **UDP**
* **HTTP / MJPEG Streaming**
* **Adafruit ADXL345 Library**
* **Adafruit SSD1306 Library**
* **Adafruit GFX Library**
* **Servo Library**

The software environment and libraries are based on the project's documented implementation.

---

## 🖐️ Gesture Mapping

| Hand Gesture     | Robot Action     |
| ---------------- | ---------------- |
| Tilt Forward     | ⬆️ Move Forward  |
| Tilt Backward    | ⬇️ Move Backward |
| Tilt Left        | ⬅️ Turn Left     |
| Tilt Right       | ➡️ Turn Right    |
| Neutral Position | ⏹️ Stop          |

A dead-zone is used around the neutral position to reduce unwanted movement caused by small hand vibrations.

---

## 📷 Project Showcase

### Robot Prototype

![Robot Prototype](images/robot.jpg)

### Gesture Control Glove

![Gesture Control Glove](images/glove.jpg)

### System Architecture

![System Architecture](images/system.jpg)

### Project Exhibition

![Project Showcase](images/showcase.jpg)

The completed system was demonstrated at **Inter-University ROBO EXPO 3.0**, where the team demonstrated the glove controller, wireless robot movement, live video transmission, and object manipulation.

> **Tip:** Replace `robot.jpg`, `glove.jpg`, `system.jpg`, and `showcase.jpg` with the actual filenames of the images you upload to your repository.

---

## 📊 Performance

The prototype was experimentally evaluated for gesture recognition, control latency, video streaming, and object manipulation.

### Gesture Recognition

The system achieved an average gesture classification accuracy of:

**96.6%**

The individual directional recognition rates were between **95% and 98%**.

### Control Latency

The measured average end-to-end control-loop latency was:

**17.9 ± 3.3 ms**

This includes sensor processing, UDP communication, and actuator execution.

### Video Streaming

The ESP32-CAM streamed video at:

* **14.2 FPS** at 0–5 m
* **10.1–12.4 FPS** at 5–15 m

using a 640×480 VGA stream.

---

## 🧪 Testing

The system was tested in multiple stages:

### Unit Testing

* ADXL345 gesture detection
* Joystick-to-servo response
* Motor movement
* ESP32-CAM video streaming
* OLED display

### Integration Testing

* Glove → Wi-Fi → Vehicle
* Servo and vehicle synchronization
* Camera view

### Object Manipulation Testing

* Pick
* Hold
* Release
* Grip stability
* Repeatability

### Safety Testing

* Battery and wiring heating
* Wireless signal stability

Each test was repeated multiple times to evaluate system consistency.

---

## 🚀 Applications

The system can potentially be adapted for:

* 🔥 Hazardous environment inspection
* 🚨 Search and rescue
* 🏗️ Remote construction-site inspection
* 🌱 Environmental monitoring
* 🔎 Remote visual inspection
* 🧪 Educational robotics
* 🏭 Industrial prototype development

The project's motivation is particularly focused on reducing human exposure to dangerous or inaccessible environments.

---

## 🔮 Future Improvements

Potential improvements include:

* 🧠 AI-based object detection
* 🚧 Automatic obstacle avoidance
* 🔋 Improved battery life
* 📡 Better communication in weak-signal environments
* 🎥 Improved video quality and frame rate
* 🤖 Semi-autonomous navigation
* 🦾 More precise robotic manipulation
* 🗺️ Mapping and navigation capabilities

These improvements are also consistent with feedback received during the project showcase, including recommendations for better battery life, obstacle avoidance, and communication reliability.

---

## 👩‍💻 Team

**Vision-Guided Gesture-Controlled Robotic Vehicle with Object Manipulation**

| Member                 |
| ---------------------- | 
| Nazia Rahman           | 
| Sajid Shahan Rahman    |
| Tanisha Taranoon Hridy | 

**Supervisor:**
Dr. Nazmun Nahid
Assistant Professor
Department of Computer Science & Engineering
University of Asia Pacific

---

## 📚 Documentation

For detailed system architecture, methodology, hardware specifications, testing procedures, mathematical models, and experimental results, see the complete project report.

---

## 📄 Course Information

**Course:** Robotics Laboratory
**Course Code:** CSE 438
**Institution:** University of Asia Pacific
**Year:** 2026

---

## ⭐ Project Highlights

> **Gesture Control + Wireless Communication + Live Vision + Robotic Manipulation**

A single low-cost platform integrating multiple robotic technologies for intuitive remote operation.

---

## 📜 License

This project was developed as an academic robotics project.

If you use or modify this project, please provide appropriate credit to the original team.

