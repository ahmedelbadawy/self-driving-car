# Self-Driving Car

A remote-controlled and self-driving car built on **Arduino** and **ESP32**, with an onboard camera that uses **OpenCV lane detection** to drive autonomously. The car is controlled through a **Progressive Web App (PWA)** over WiFi, and supports two modes: **manual** (drive it yourself from the app) and **self-driving** (the car follows the lane on its own using rule-based steering).

## Features

- **Two driving modes** — switch between manual and self-driving directly from the app.
- **Progressive Web App control** — drive and monitor the car from any device with a browser, no install required.
- **OpenCV lane detection** — an onboard camera detects lane lines and steers the car via rule-based control in self-driving mode.
- **WiFi connectivity** — the ESP32 connects the car to the app server wirelessly.

## Architecture

```
[ Camera ] --> [ OpenCV lane detection ] --> rule-based steering
                                                    |
[ PWA (HTML/CSS/JS) ] <--WiFi--> [ Node.js server ] <--> [ ESP32 ] <--> [ Arduino + motors ]
```

- **Arduino** — drives the motors and low-level car hardware.
- **ESP32** — handles WiFi connectivity and relays commands between the server and the Arduino.
- **Node.js server** — bridges the web app and the car, passing control commands and mode selection.
- **Progressive Web App (HTML, CSS, JS)** — the user interface for controlling the car and switching modes.
- **OpenCV lane detection** — processes the camera feed to detect lane lines and compute steering commands in self-driving mode.

## Tech Stack

| Layer            | Technology              |
|------------------|-------------------------|
| Hardware         | Arduino, ESP32, camera  |
| Connectivity     | WiFi (ESP32)            |
| Server           | Node.js                 |
| Front end        | HTML, CSS, JS (PWA)     |
| Lane detection   | Python, OpenCV          |

## Getting Started

### Prerequisites
- Node.js installed
- Arduino IDE (to flash the Arduino and ESP32)
- Python with the vision dependencies installed

### Setup
1. Clone the repository:
   ```bash
   git clone https://github.com/ahmedelbadawy/self-driving-car.git
   cd self-driving-car
   ```
2. Flash the firmware to the Arduino and ESP32 using the Arduino IDE.
3. Install and start the server:
   ```bash
   npm install
   npm start
   ```
4. Connect your device to the same WiFi network as the ESP32, then open the app in your browser.

## Usage
- Choose **Manual** mode to drive the car yourself, or **Self-Driving** mode to let the car follow the lane on its own using OpenCV lane detection.

