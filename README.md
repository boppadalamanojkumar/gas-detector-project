const int gasSensorPin = A0;
const int threshold = 300;
const int alertPin = 13;

void setup() {
  Serial.begin(9600);
  pinMode(alertPin, OUTPUT);
  Serial.println("Gas sensor initializing...");
  delay(2000);
}

void loop() {
  int sensorValue = analogRead(gasSensorPin);

  Serial.print("Gas Level: ");
  Serial.println(sensorValue);

  if (sensorValue > threshold) {
    digitalWrite(alertPin, HIGH);
    Serial.println(" Gas Leak Detected!");
  } else {
    digitalWrite(alertPin, LOW);
  }

  delay(1000);
}
