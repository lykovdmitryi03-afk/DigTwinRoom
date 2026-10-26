
# MQTT Contract

## Broker

Development broker: Mosquitto

Base topic: `room/`

## Sensor Topics

| Topic | Unit | Value |
|-------|------|-------|
| room/sensors/temperature | C | number |
| room/sensors/humidity | % | number |
| room/sensors/light | raw | number |
| room/sensors/noise | boolean | 0 or 1 |
| room/sensors/co2 | ppm | number |
| room/sensors/motion | boolean | 0 or 1 |

Light values are initially raw ADC measurements.
Noise represents a threshold event, not decibels.
CO2 data is initially simulated.

## Sensor Message

```json
{
  "device_id": "esp32-room-01",
  "sensor": "temperature",
  "value": 23.5,
  "unit": "C",
  "timestamp": "2026-10-26T12:00:00Z"
}
```

## Lamp Command

Topic: `room/actuators/lamp/set`

```json
{
  "device_id": "esp32-room-01",
  "state": true
}
```

## Lamp State

Topic: `room/actuators/lamp/state`

```json
{
  "device_id": "esp32-room-01",
  "state": true,
  "timestamp": "2026-10-26T12:00:01Z"
}
```

## Rules

- JSON messages use UTF-8 encoding.
- Timestamps use ISO 8601 in UTC.
- Sensor messages must contain all required fields.
- Unknown sensor names are rejected.
- Sensor values must match their declared units.
- The subscriber listens to `room/sensors/+`.
- Lamp commands must not be stored as sensor readings.
- The simulator and ESP32 use the same message contract.
- MQTT QoS 1 is used for sensor and command messages.
- Lamp state messages are retained.
- Lamp commands are not retained.
- The broker is restricted to the development network.

