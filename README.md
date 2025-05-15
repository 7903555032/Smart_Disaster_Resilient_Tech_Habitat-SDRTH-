# Smart_Disaster_Resilient_Tech_Habitat-SDRTH-
PHASE-01
🌱 Smart Agriculture Monitor with Arduino UNO & NodeMCU
This project is a Smart Agriculture Monitoring System built using Arduino UNO, NodeMCU (ESP8266), and several sensors. It helps monitor soil moisture, temperature, and humidity, and provides visual and sound alerts using an RGB LED and buzzer.

📦 Components Used
Arduino UNO

NodeMCU ESP8266

Soil Moisture Sensor

DHT11 Temperature & Humidity Sensor

RGB LED (Common Anode)

Buzzer

Push Button

Jumper Wires & Breadboard

🔧 Features
Soil Moisture Monitoring: Alerts when the soil is dry

Temperature & Humidity Display: Real-time readings from DHT11

RGB LED Indicators:

🔴 Red – Soil too dry

🟢 Green – Soil is good

🔵 Blue – Manual alert via button

Buzzer Alert: Sounds when soil is dry or button is pressed

Serial Output: All sensor values printed via Serial Monitor

ESP8266 TX/RX Setup: Communication-ready (for future IoT integration)

📋 Functional Logic
Condition	Buzzer	RGB LED
Soil too dry	ON	Red
Soil moisture is fine	OFF	Green
Button is pressed	Beep	Blue

🛠 Setup Notes
Common Anode RGB LED is used. Color values are inverted in code using 255 - value logic.

Do not connect TX/RX lines between NodeMCU and Arduino while uploading code – disconnect them first to avoid upload errors.

📁 File Contents
smart_agriculture.ino – Main Arduino sketch

README.md – Project overview and setup

🚀 Future Scope
ESP8266 integration for cloud-based IoT monitoring

Data logging on a web server or mobile app
