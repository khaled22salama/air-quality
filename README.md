
# IoT Air Quality Monitor with NodeMCU

This project demonstrates how to use an ESP32 NodeMCU board to measure air quality using an MQ-135 gas sensor and publish the data to AskSensors over MQTT. The device connects to a Wi-Fi network, reads the sensor data, and sends it to the AskSensors platform at regular intervals.

## Components Used

- ESP32 NodeMCU
- MQ-135 Air Quality Sensor
- Wi-Fi network
- AskSensors MQTT API

## Getting Started

### Prerequisites

To get started with this project, ensure you have the following:

- [Arduino IDE](https://www.arduino.cc/en/software)
- [AskSensors Account](https://asksensors.com) for MQTT credentials
- ESP32 board library installed in the Arduino IDE

### Circuit Diagram

1. Connect the MQ-135 sensor to the ESP32 NodeMCU.
2. Connect the VCC pin of the MQ-135 to 3.3V on the NodeMCU.
3. Connect the GND pin of the MQ-135 to GND on the NodeMCU.
4. Connect the analog output pin (A0) of the MQ-135 to the A0 pin of the NodeMCU.

### Installation

1. Clone the repository or download the project files.

```bash
git clone https://github.com/khaled22salama/air-quality.git
cd iot-air-quality-monitor
```

2. Open the `iot-air-quality-monitor.ino` file in the Arduino IDE.

3. Install the required libraries:

- [WiFi.h](https://github.com/espressif/arduino-esp32/tree/master/libraries/WiFi)
- [PubSubClient](https://github.com/knolleary/pubsubclient)

You can install these libraries via the Arduino IDE Library Manager.

4. Replace the following placeholders in the code with your specific credentials:

```cpp
const char* ssid = "Your_SSID";           // Your Wi-Fi SSID
const char* password = "Your_PASSWORD";   // Your Wi-Fi Password
const char* username = "Your_Username";   // Your AskSensors username
const char* pubTopic = "publish/Your_Username/Your_API_Key";  // Your AskSensors MQTT topic
```

### Uploading the Code

1. Select the correct board and port from the `Tools` menu in the Arduino IDE.
2. Click on the "Upload" button to upload the code to your ESP32 board.

## How It Works

1. The ESP32 connects to the specified Wi-Fi network using the provided SSID and password.
2. It reads the air quality data from the MQ-135 sensor.
3. The sensor data is published to the AskSensors platform over MQTT.
4. The script periodically sends data at intervals defined by the `writeInterval` variable (default is 25 seconds).

## Code Explanation

- **WiFi Setup:** Connects the ESP32 to a Wi-Fi network.
- **MQTT Configuration:** Establishes an MQTT connection with the AskSensors server.
- **Sensor Data Reading:** Continuously reads the air quality data from the MQ-135 sensor.
- **Data Publishing:** Publishes the sensor data to AskSensors using MQTT at regular intervals.

### Key Configuration Parameters

- `MQ135_THRESHOLD_1`: Threshold for fresh air.
- `writeInterval`: Data publishing interval in milliseconds (default is 25,000 ms).

## Usage

Once the code is successfully uploaded, the ESP32 board will start sending air quality data to the AskSensors platform. You can monitor the data in real-time through your AskSensors dashboard.

## Troubleshooting

- **WiFi Connection Failure:** Verify your Wi-Fi credentials and ensure the network is available.
- **MQTT Connection Failure:** Ensure your AskSensors MQTT username and topic are correctly configured.
- **Incorrect Data:** Check the sensor connections and ensure the MQ-135 is calibrated properly.


## Acknowledgments

- Thanks to [AskSensors](https://asksensors.com) for their MQTT API.
- Inspired by various IoT air quality monitoring projects.

