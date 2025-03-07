#include <Wire.h>
#include <Adafruit_SHT31.h>

// Create an instance of the SHT31 sensor
Adafruit_SHT31 sht31 = Adafruit_SHT31();

void setup() {
  // Start serial communication
  Serial.begin(115200);
  
  // Initialize I2C communication with ESP32-CAM (SDA: GPIO21, SCL: GPIO22)
  Wire.begin(14, 15);  // You can also change the pins if required
  
  // Initialize the SHT30 sensor
  if (!sht31.begin(0x44)) {  // Default I2C address for SHT30 is 0x44
    Serial.println("Couldn't find SHT30 sensor!");
    while (1);  // Hang if the sensor isn't detected
  }
  Serial.println("SHT30 Sensor initialized.");
}

void loop() {
  // Read temperature and humidity from the sensor
  float temperature = sht31.readTemperature();
  float humidity = sht31.readHumidity();
  
  // Check if readings are valid (not NaN)
  if (!isnan(temperature) && !isnan(humidity)) {
    // Print temperature and humidity values to the Serial Monitor
    Serial.print("Temperature: ");
    Serial.print(temperature);
    Serial.print(" °C");
    Serial.print("\tHumidity: ");
    Serial.print(humidity);
    Serial.println(" %");
  } else {
    Serial.println("Failed to read from sensor!");
  }

  // Delay for 2 seconds before reading again
  delay(2000);
}
