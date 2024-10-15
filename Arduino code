#include <Servo.h>

// Motor pin definitions
#define motorPin1 3
#define motorPin2 4
#define motorPin3 5
#define motorPin4 6
#define enableA 9
#define enableB 10

// Servo pin
#define servoPin 7

// Flame sensor pin definitions (4 directions)
#define sensorFront A0
#define sensorBack A1
#define sensorLeft A2
#define sensorRight A3

// Relay pin to trigger the extinguisher (if used for future enhancements)
#define relayPin 2

Servo extinguisherServo;  // Create servo object to control the soda-acid bottle

void setup() {
  // Set motor pins as outputs
  pinMode(motorPin1, OUTPUT);
  pinMode(motorPin2, OUTPUT);
  pinMode(motorPin3, OUTPUT);
  pinMode(motorPin4, OUTPUT);
  pinMode(enableA, OUTPUT);
  pinMode(enableB, OUTPUT);

  // Set relay pin as output (optional for relay control)
  pinMode(relayPin, OUTPUT);
  digitalWrite(relayPin, LOW);  // Keep relay off initially

  // Flame sensor setup
  pinMode(sensorFront, INPUT);
  pinMode(sensorBack, INPUT);
  pinMode(sensorLeft, INPUT);
  pinMode(sensorRight, INPUT);

  // Attach servo motor to servoPin
  extinguisherServo.attach(servoPin);

  // Set initial motor speeds
  analogWrite(enableA, 200);  // Left motor speed
  analogWrite(enableB, 200);  // Right motor speed

  Serial.begin(9600); // For debugging
}

void loop() {
  // Read all flame sensor values
  int frontVal = analogRead(sensorFront);
  int backVal = analogRead(sensorBack);
  int leftVal = analogRead(sensorLeft);
  int rightVal = analogRead(sensorRight);

  // Find the direction with the highest flame sensor reading
  int maxVal = max(frontVal, max(backVal, max(leftVal, rightVal)));

  // Determine movement direction based on max sensor value
  if (maxVal == frontVal) {
    Serial.println("Moving forward towards fire!");
    moveForward();
  } else if (maxVal == backVal) {
    Serial.println("Moving backward towards fire!");
    moveBackward();
  } else if (maxVal == leftVal) {
    Serial.println("Turning left towards fire!");
    turnLeft();
  } else if (maxVal == rightVal) {
    Serial.println("Turning right towards fire!");
    turnRight();
  }

  // If any sensor detects high flame intensity, stop and extinguish fire
  if (maxVal > 500) {  // Adjust threshold for fire detection
    stopMotors();
    activateExtinguisher();  // Trigger the extinguisher
  }

  delay(100);  // Short delay for stability
}

// Function to move the car forward
void moveForward() {
  digitalWrite(motorPin1, HIGH);
  digitalWrite(motorPin2, LOW);
  digitalWrite(motorPin3, HIGH);
  digitalWrite(motorPin4, LOW);
}

// Function to move the car backward
void moveBackward() {
  digitalWrite(motorPin1, LOW);
  digitalWrite(motorPin2, HIGH);
  digitalWrite(motorPin3, LOW);
  digitalWrite(motorPin4, HIGH);
}

// Function to turn left
void turnLeft() {
  analogWrite(enableA, 100);  // Slow down left motor
  analogWrite(enableB, 200);  // Right motor full speed
}

// Function to turn right
void turnRight() {
  analogWrite(enableA, 200);  // Left motor full speed
  analogWrite(enableB, 100);  // Slow down right motor
}

// Function to stop the motors
void stopMotors() {
  digitalWrite(motorPin1, LOW);
  digitalWrite(motorPin2, LOW);
  digitalWrite(motorPin3, LOW);
  digitalWrite(motorPin4, LOW);
}

// Function to activate the soda-acid extinguisher using the servo motor
void activateExtinguisher() {
  // Rotate the servo to trigger the extinguisher (spin the bottle)
  Serial.println("Activating extinguisher!");
  extinguisherServo.write(90);  // Rotate servo to 90 degrees to spin the bottle
  delay(2000);  // Wait for 2 seconds (time for spraying)
  extinguisherServo.write(0);  // Return servo to initial position
}
