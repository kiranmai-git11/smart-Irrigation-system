
#define SENSOR A0
#define LED 8

void setup() {
  pinMode(SENSOR, INPUT);
  pinMode(LED, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int moisture = analogRead(SENSOR);
  int moisturePercent = map(moisture, 0, 1023, 0, 100);

  Serial.print("Soil Moisture: ");
  Serial.print(moisturePercent);
  Serial.println("%");

  if (moisture < 400) {  // dry soil
    digitalWrite(LED, HIGH);
    Serial.println("Pump ON");
  } else {
    digitalWrite(LED, LOW);
    Serial.println("Pump OFF");
  }

  delay(1000);
}
