# Ultrasonic Sensor Distance Measurement

This repository provides an example code to measure distance using an ultrasonic sensor connected to an Arduino. The sensor uses a trigger pin to send an ultrasonic pulse and an echo pin to receive the reflected pulse. The distance is calculated based on the time it takes for the pulse to return.

## Features
- Measures distance using an ultrasonic sensor
- Outputs distance in centimeters
- Easy-to-understand and customizable code

## Requirements
- Arduino board
- Ultrasonic sensor (e.g., HC-SR04)
- Jumper wires
- Breadboard (optional)

## Code Explanation
Here is the Arduino code used in this project:

```cpp
int trig = 2;   // Trigger pin
int echo = 3;   // Echo pin
float timeduration, distance;

void setup()
{
  Serial.begin(9600);
  pinMode(trig, OUTPUT);
  pinMode(echo, INPUT);
}

void loop()
{
  digitalWrite(trig, LOW);
  delayMicroseconds(2);
  digitalWrite(trig, HIGH);
  delayMicroseconds(10);
  digitalWrite(trig, LOW);
  timeduration = pulseIn(echo, HIGH);   // Measures the duration of the pulse
  distance = 0.034 * timeduration / 2;  // Calculates distance in cm
  Serial.print("Distance in cm : ");
  Serial.println(distance);
  delay(100);
}
```

## How to Use
1. **Connect the Components**:
   - Connect the trigger pin of the ultrasonic sensor to digital pin 2 on the Arduino.
   - Connect the echo pin of the ultrasonic sensor to digital pin 3 on the Arduino.
   - Connect VCC and GND of the sensor to the 5V and GND pins of the Arduino.

2. **Upload the Code**:
   - Open the Arduino IDE.
   - Copy and paste the code into the IDE.
   - Connect your Arduino board to your computer.
   - Upload the code to the Arduino board.

3. **View the Output**:
   - Open the Serial Monitor in the Arduino IDE.
   - Set the baud rate to 9600.
   - Observe the distance readings in centimeters.

## Notes
- Ensure the sensor is placed in a location where it can emit and receive ultrasonic pulses without obstructions.
- The echo pin must be connected to a pin capable of PWM.
- The distance calculation uses the speed of sound in air (~343 m/s or 0.034 cm/µs).

## Applications
- Obstacle detection
- Proximity sensing
- Distance measurement in robotics projects

## Troubleshooting
- If the distance readings are inaccurate, ensure proper wiring and connections.
- Double-check the sensor's orientation and ensure it faces the target object.

## License
This project is open-source and available under the MIT License.
