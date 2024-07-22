# Robot-Walking-Motion-Control-with-Servo-Motors
This project demonstrates how to control servo motors to create a walking motion for a bipedal robot. The aim is to simulate a simple walking gait using Arduino and servo motors. Each leg of the robot consists of three servo motors controlling the hip, knee, and ankle joints. By precisely controlling the angles of these servos, we can simulate the walking motion.

### Components

- Arduino board (e.g., Arduino Uno)
- Servo motors (6x)
- Connecting wires
- Power supply for the servos
- Breadboard (optional)
- Robot chassis with leg mounts

### Wiring

Connect the servo motors to the Arduino board as follows:
- Hip Left Servo to Pin 9
- Hip Right Servo to Pin 10
- Knee Left Servo to Pin 11
- Knee Right Servo to Pin 12
- Ankle Left Servo to Pin 13
- Ankle Right Servo to Pin 14

### Arduino Code

The following Arduino code demonstrates how to control the servo motors to create a walking motion. The `Servo` library is used to simplify the control of the servo motors.

```cpp
#include <Servo.h>

// Define the servo motors
Servo hipLeft;
Servo hipRight;
Servo kneeLeft;
Servo kneeRight;
Servo ankleLeft;
Servo ankleRight;

// Pin definitions for the servos
const int hipLeftPin = 9;
const int hipRightPin = 10;
const int kneeLeftPin = 11;
const int kneeRightPin = 12;
const int ankleLeftPin = 13;
const int ankleRightPin = 14;

void setup() {
  // Attach the servos to the specified pins
  hipLeft.attach(hipLeftPin);
  hipRight.attach(hipRightPin);
  kneeLeft.attach(kneeLeftPin);
  kneeRight.attach(kneeRightPin);
  ankleLeft.attach(ankleLeftPin);
  ankleRight.attach(ankleRightPin);

  // Initialize servos to their starting positions
  hipLeft.write(90);
  hipRight.write(90);
  kneeLeft.write(90);
  kneeRight.write(90);
  ankleLeft.write(90);
  ankleRight.write(90);

  delay(1000);  // Wait for servos to reach the starting position
}

void loop() {
  walkStep();
}

void setAngle(Servo servo, int angle) {
  servo.write(angle);
  delay(500);
}

void walkStep() {
  // Lift the right leg
  setAngle(hipRight, 120);
  setAngle(kneeRight, 150);
  setAngle(ankleRight, 90);

  // Place the right leg
  setAngle(hipRight, 90);
  setAngle(kneeRight, 90);
  setAngle(ankleRight, 90);

  // Lift the left leg
  setAngle(hipLeft, 120);
  setAngle(kneeLeft, 150);
  setAngle(ankleLeft, 90);

  // Place the left leg
  setAngle(hipLeft, 90);
  setAngle(kneeLeft, 90);
  setAngle(ankleLeft, 90);
}
