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

#### Tooling for Protobuf:
- **[Protobuf Decoder (Online)](https://protobuf-decoder.netlify.app/)**: Useful for decoding base64-encoded binary payloads from MQTT without a schema.
- **`tomvd/local-powerstream`**: Contains Java implementations for creating control messages.

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

### 🛡️ Tricking the Device (Local MQTT Redirect)
Using Adguard or Pi-hole, you can redirect the DNS for `mqtt-e.ecoflow.com` to your local machine running a Mosquitto server.
1.  **DNS Rewrite**: Point `mqtt-e.ecoflow.com` to your local IP.
2.  **Certificate**: Create a self-signed certificate for the local broker.
3.  **Observation**: The device will connect to your local broker, allowing you to intercept all telemetry and send commands directly without the EcoFlow cloud.
4.  **Reference**: See the [local-powerstream](https://github.com/tomvd/local-powerstream) repository for a pre-configured docker setup.

### 🔑 Official Local API Access
Believe it or not, EcoFlow support has been known to grant local API access upon request.
*   **Method**: Contact EcoFlow support with your device's **Serial Number** and request "Local API access for Home Automation integration."
*   **Result**: If granted, the device can expose data locally over Wi-Fi, which is much more stable than cloud-based MQTT polling.
*   **Integration**: Primarily used in conjunction with [hassio-ecoflow](https://github.com/vwt12eh8/hassio-ecoflow).

## 5. Bluetooth Low Energy (BLE)
Devices also advertise over BLE.
*   **Service UUIDs**: Proprietary EcoFlow UUIDs.
*   **Data**: Encrypted. Requires initial handshake with the app (which gets keys from the cloud) to effectively decode or control via BLE.
*   **Reverse Engineering**: Check `rabits/ef-ble-reverse` for deep dives into the Android APK's handling of BLE packets.
