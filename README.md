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

