# 🌱 Smart Irrigation System using Arduino (Wokwi Simulation)

This project automatically controls a water pump based on soil moisture levels to save water efficiently.  
The system was simulated using [Wokwi](https://wokwi.com), and programmed using Arduino IDE (C++).

---

## 🧩 Components Used
- Arduino Uno  
- Soil Moisture Sensor  
- LED (Pump indicator)  
- Jumper Wires  
- Breadboard  
- (Simulated on Wokwi)

---

## ⚙️ Working Principle
- The soil moisture sensor detects the water level in the soil.  
- If the moisture is **below a set threshold**, the **pump (LED)** turns **ON**.  
- When moisture is **sufficient**, the **pump turns OFF**.  

---

## 💻 Arduino Code

```cpp
// Smart Irrigation System

int sensorPin = A0;
int pumpPin = 13;
int sensorValue = 0;

void setup() {
  pinMode(pumpPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  sensorValue = analogRead(sensorPin);
  int moisture = map(sensorValue, 1023, 0, 0, 100); // Convert reading to %
  
  Serial.print("Soil Moisture: ");
  Serial.print(moisture);
  Serial.println("%");

  if (moisture < 30) {
    digitalWrite(pumpPin, HIGH);
    Serial.println("Pump ON 💧");
  } else {
    digitalWrite(pumpPin, LOW);
    Serial.println("Pump OFF");
  }

  delay(1000);
}

 Conclusion:

> The Smart Irrigation System reduces manual effort and ensures optimal water usage by automatically controlling irrigation based on soil moisture. This prototype can be further extended using IoT for remote monitoring.




---

 Future Scope / Enhancements (optional but impressive)

> Add an IoT dashboard using Blynk / Firebase

Live moisture monitoring on a mobile app

SMS alert when soil is dry


# Smart Irrigation System using IoT

## ⭐ Project Overview
This project automatically controls the water pump based on soil moisture levels. When the soil becomes dry, the pump turns ON, and when the soil becomes wet, the pump turns OFF. This helps save water and reduces manual monitoring.
