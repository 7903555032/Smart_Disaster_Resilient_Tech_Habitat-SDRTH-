# Smart_Disaster_Resilient_Tech_Habitat-SDRTH-
#include <DHT.h>

#define DHTPIN 2
#define DHTTYPE DHT11
DHT dht(DHTPIN, DHTTYPE);

const int buttonPin = 7;
const int buzzerPin = 8;
const int redPin = 5;     // PWM
const int greenPin = 6;   // PWM
const int bluePin = 3;    // PWM
const int soilMoisturePin = A0;

const int dryThreshold = 600;

void setup() {
  Serial.begin(9600);
  dht.begin();

  pinMode(buttonPin, INPUT_PULLUP);
  pinMode(buzzerPin, OUTPUT);

  pinMode(redPin, OUTPUT);
  pinMode(greenPin, OUTPUT);
  pinMode(bluePin, OUTPUT);

  setColor(0, 0, 0);
}

void loop() {
  int soilMoisture = analogRead(soilMoisturePin);
  float temp = dht.readTemperature();
  float hum = dht.readHumidity();

  Serial.print("Soil Moisture: ");
  Serial.println(soilMoisture);

  Serial.print("Temperature: ");
  Serial.print(temp);
  Serial.println(" °C");

  Serial.print("Humidity: ");
  Serial.print(hum);
  Serial.println(" %");

  Serial.println("---------------------------");

  // Soil moisture check
  if (soilMoisture > dryThreshold) {
    digitalWrite(buzzerPin, HIGH);
    setColor(255, 0, 0); // Red
  } else {
    digitalWrite(buzzerPin, LOW);
    setColor(0, 255, 0); // Green
  }

  // Button check (active LOW)
  if (digitalRead(buttonPin) == LOW) {
    digitalWrite(buzzerPin, HIGH);
    setColor(0, 0, 255); // Blue
    delay(300);
    digitalWrite(buzzerPin, LOW);
  }

  delay(2000);
}

void setColor(int r, int g, int b) {
  // For common anode, invert values
  analogWrite(redPin, 255 - r);
  analogWrite(greenPin, 255 - g);
  analogWrite(bluePin, 255 - b);
}
