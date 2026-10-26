
<div align="center">

# Digitálne dvojča inteligentnej miestnosti
### Digital Twin · Internet of Things

**A real-time digital representation of a physical smart room.**

An academic IoT project combining embedded systems,
real-time communication, data processing and 3D visualization.

![Status](https://img.shields.io/badge/status-in_development-orange)
![ESP32](https://img.shields.io/badge/hardware-ESP32-blue)
![Python](https://img.shields.io/badge/backend-Python-blue)
![Three.js](https://img.shields.io/badge/3D-Three.js-black)
![License](https://img.shields.io/badge/license-MIT-green)

</div>

---

## Overview

Smart Room Digital Twin is a university project focused
on developing a virtual representation of a real room.

The system is designed to collect environmental data
using an ESP32 microcontroller and IoT sensors, transmit
it through MQTT, store it in PostgreSQL and visualize
the results in an interactive Three.js environment.

The digital twin will also support bidirectional
communication, allowing users to control selected
physical devices through the web interface.

## Planned Features

- Real-time temperature and humidity monitoring
- Ambient light monitoring
- Sound threshold detection
- PIR motion detection
- Interactive 3D room visualization
- Historical sensor data
- Live updates using WebSockets
- Remote LED control
- Simulated CO2 readings
- ESP32 integration

## System Architecture

```text
    Physical Sensors
          |
          v
         ESP32
          |
       Wi-Fi/MQTT
          |
          v
     MQTT Broker
          |
          v
    Python Subscriber
          |
          v
      PostgreSQL
          |
          v
       FastAPI
          |
     REST / WebSocket
          |
          v
     Three.js Web App
          |
          v
      Digital Twin
```

Commands travel in the opposite direction:

```text
Web App -> FastAPI -> MQTT -> ESP32 -> LED
```

## Technology Stack

| Layer | Technology |
|-------|------------|
| Microcontroller | ESP32 |
| Firmware | C++ / Arduino |
| Messaging | MQTT / Mosquitto |
| Backend | Python / FastAPI |
| Database | PostgreSQL |
| Infrastructure | Docker Compose |
| Frontend | JavaScript / Three.js |
| 3D Modeling | Blender |
| Communication | REST / WebSocket |

## Hardware

| Component | Purpose |
|-----------|---------|
| ESP32 | Main microcontroller |
| DHT11 | Temperature and humidity |
| Photoresistor | Ambient light |
| LM393 microphone module | Sound threshold detection |
| HC-SR501 | Motion detection |
| Red LED | Physical output indicator |
| 330 Ohm resistor | LED current limiting |

CO2 measurements will initially be simulated.

## Repository Structure

```text
firmware/  ESP32 firmware
server/    Python backend and simulator
web/       Three.js web application
model/     Blender project and GLB assets
docs/      Architecture and technical documentation
```

## Development Roadmap

- [ ] Repository and MQTT contract
- [ ] Docker infrastructure
- [ ] PostgreSQL schema
- [ ] MQTT subscriber
- [ ] Sensor simulator
- [ ] FastAPI and WebSocket
- [ ] Blender room model
- [ ] Three.js interface
- [ ] Physical ESP32 integration
- [ ] Final testing and demonstration

## Project Team

**Yevhenii Yevsikov**
- 3D modeling and visualization
- Frontend development
- ESP32 firmware and hardware integration

**Dmytro Lykov**
- Backend development
- Database design
- MQTT infrastructure
- Sensor simulation

Architecture, integration and documentation
are shared responsibilities.

## Academic Context

Ekonomická univerzita v Bratislave

Faculty of Economic Informatics

Course: Internet vecí

Academic Year: 2026/2027

## Documentation

- [System Architecture](docs/architecture.md)
- [MQTT Contract](docs/mqtt-contract.md)
- [Hardware Wiring](docs/wiring.md)

## Project Status

Currently in development.

## License

Distributed under the MIT License.
