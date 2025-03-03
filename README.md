# DOTECH
#define sensorPin A0  // Soil moisture sensor connected to A0
#define pumpPin 8     // Water pump connected to digital pin 8

void setup() {
    pinMode(sensorPin, INPUT);
    pinMode(pumpPin, OUTPUT);
    Serial.begin(9600);
}

void loop() {
    int moisture = analogRead(sensorPin); // Read moisture level
    Serial.print("Moisture Level: ");
    Serial.println(moisture);
    
    if (moisture < 300) {  // Threshold for dry soil
        digitalWrite(pumpPin, HIGH);  // Turn ON water pump
        Serial.println("Watering the plant...");
        delay(5000);  // Water for 5 seconds
    } else {
        digitalWrite(pumpPin, LOW);  // Turn OFF water pump
        Serial.println("Soil is moist. Pump OFF.");
    }
    
    delay(2000);  // Wait before next reading
}
