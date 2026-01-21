# EcoFlow Software Protocols & Communication

This document outlines the software layers used by EcoFlow devices, primarily focusing on the MQTT and Protobuf implementations that allow for monitoring and control.

## 1. Overview
EcoFlow devices generally operate in two modes:
*   **Direct Mode (AP Mode)**: Device creates its own Wi-Fi hotspot (`EcoFlow_XXXX`). Limited functionality.
*   **IoT Mode (Station Mode)**: Device connects to your Wi-Fi and communicates with EcoFlow clouds (`tcp.ecoflow.com`) via MQTT on port **6500**.

## 2. MQTT Protocol
The core communication transport is MQTT.
*   **Host**: `mqtt.ecoflow.com`, `mqtt-a.ecoflow.com`, or directly to device IP (rarely open).
*   **Port**: `1883` (Standard), `8883` (SSL), `6500` (Proprietary/Raw).
*   **Authentication**: Requires `accessKey` and `secretKey` derived from your EcoFlow account credentials.

### Topic Structure
Common topics observed in reverse engineering:
*   **Status Updates**: `/app/device/property/{serial_number}`
*   **Set Commands**: `/app/{user_id}/{serial_number}/thing/property/set`
*   **Get Commands**: `/app/{user_id}/{serial_number}/thing/property/get`

## 3. Data Payload: Google Protobuf
Unlike simple JSON-based MQTT implementations, EcoFlow uses **Google Protocol Buffers (Protobuf)** for the message payload. This makes the data binary and unreadable without the correct `.proto` definition files.

### Decoding the Data
To decode the payloads, you need the schema. Community projects have reverse-engineered these schemas.

#### Key Repositories for Protobuf Definitions:
1.  **`foxthefox/ioBroker.ecoflow-mqtt`**: Contains extensive JavaScript/TypeScript definitions for various device properties.
2.  **`tolwi/hassio-ecoflow-cloud`**: Python-based implementation for Home Assistant, containing logic to parse these binary streams.

### Example Protobuf Concepts
A typical message might contain fields for:
*   `pd`: Power Distribution (USB, AC output, DC output states).
*   `bms`: Battery Management System status (Voltage, Temp, Cycles).
*   `mppt`: Solar input status (Volts, Amps).

## 4. Local Access via Scripting
While official local API access is limited, you can use scripts to bridge the cloud data to your local system.

### Getting Credentials
You can use the `ecoflow-token` script from community repositories to exchange your email/password for the MQTT keys:
```bash
# Conceptual usage
python3 get_token.py --email "user@example.com" --password "secret"
```
*   *Warning*: Credentials expire and need refreshing.

### 📶 Direct Connection Mode (No Cloud)
When you press the IoT button to enter Direct Mode, the EcoFlow creates its own Wi-Fi Access Point (e.g., `EcoFlow_XXXX`).
*   **Mechanism**: Your phone connects to this AP. The EcoFlow runs a local MQTT broker on its own internal IP (usually `192.168.4.1`).
*   **Local Access**: Some developers have successfully connected to this local broker to read data without an internet connection, but the app is required to "activate" the stream.
*   **Safety**: There is no password for the Direct Mode Wi-Fi by default—anyone within range can potentially control the unit if they have the app. Always switch back to IoT Mode (Cloud) for security.

## 5. Bluetooth Low Energy (BLE)
Devices also advertise over BLE.
*   **Service UUIDs**: Proprietary EcoFlow UUIDs.
*   **Data**: Encrypted. Requires initial handshake with the app (which gets keys from the cloud) to effectively decode or control via BLE.
*   **Reverse Engineering**: Check `rabits/ef-ble-reverse` for deep dives into the Android APK's handling of BLE packets.
