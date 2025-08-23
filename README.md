
# 🌱 Soil Testing Equipment (IoT with ESP8266 + ThingSpeak)

This project uses an **ESP8266 (NodeMCU)** to measure soil parameters such as **pH, moisture, temperature, and gas levels**. The collected data is uploaded to **ThingSpeak**, where it can be visualized in real time.

---

## 📌 Features
- Reads values from multiple sensors:
  - **pH Sensor** (analog)
  - **Soil Moisture Sensor**
  - **Temperature Sensor** (analog/digital pin used as demo)
  - **Gas Sensor** (MQ-series or similar)
- Sends live sensor data to **ThingSpeak Cloud**
- Serial Monitor debugging
- Simple and modular Arduino code

---

## 🛠️ Hardware Requirements
- **ESP8266 NodeMCU / ESP-12E**
- **pH Sensor** (analog output)
- **Soil Moisture Sensor**
- **Temperature Sensor** (LM35, DHT11/DHT22, or other)
- **Gas Sensor** (MQ135 / MQ2 etc.)
- Jumper wires, Breadboard, USB cable

---

## 🔌 Pin Connections
| Sensor            | ESP8266 Pin |
|-------------------|-------------|
| pH Sensor (AOUT)  | A0          |
| Moisture Sensor   | D1 (GPIO5)  |
| Temperature Sensor| D2 (GPIO4)  |
| Gas Sensor        | D3 (GPIO0)  |

⚠️ Note: ESP8266 has only **one ADC pin (A0)**, so only **one true analog sensor** can be connected.  
In this example, multiple sensors are shown for demonstration. To use multiple analog sensors, you may need an **external ADC module (e.g., ADS1115)**.

---

## 💻 Arduino Setup
1. Install **Arduino IDE**
2. Add **ESP8266 Boards** (Board Manager URL: `http://arduino.esp8266.com/stable/package_esp8266com_index.json`)
3. Install libraries via Library Manager:
   - `ESP8266WiFi`
   - `ThingSpeak`
4. Open `SoilMonitor.ino` and update:
   ```cpp
   const char* ssid = "Your_SSID";
   const char* password = "Your_PASSWORD";
   unsigned long myChannelNumber = 123456;   // Replace with your ThingSpeak channel
   const char* myWriteAPIKey = "YOUR_API_KEY";
