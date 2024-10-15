Here are the connection details for the provided Arduino code, which controls motors, flame sensors, and a servo for a soda-acid fire extinguisher.

### Connections

#### 1. **Motor Driver Connections**
Assuming you're using an H-Bridge motor driver (like the **L298N**), here’s how to connect the motors:

- **Motor Driver Pins:**
  - **Motor 1 (Left Motor)**:
    - **Output A**: Connect to **Motor 1** (Positive terminal)
    - **Output B**: Connect to **Motor 1** (Negative terminal)
  - **Motor 2 (Right Motor)**:
    - **Output C**: Connect to **Motor 2** (Positive terminal)
    - **Output D**: Connect to **Motor 2** (Negative terminal)

- **Control Pins from Arduino to Motor Driver**:
  - **Motor Driver IN1 (Pin 3)** → Connect to **motorPin1** (Arduino Pin 3)
  - **Motor Driver IN2 (Pin 4)** → Connect to **motorPin2** (Arduino Pin 4)
  - **Motor Driver IN3 (Pin 5)** → Connect to **motorPin3** (Arduino Pin 5)
  - **Motor Driver IN4 (Pin 6)** → Connect to **motorPin4** (Arduino Pin 6)

- **Enable Pins (for PWM Control)**:
  - **ENA** (for Motor 1) → Connect to **enableA** (Arduino Pin 9)
  - **ENB** (for Motor 2) → Connect to **enableB** (Arduino Pin 10)

#### 2. **Servo Connections**
- **Servo Motor**:
  - **Servo Control Pin** → Connect to **servoPin** (Arduino Pin 7)
  - **Power and Ground**:
    - Connect the **VCC** of the servo to the **5V pin** on the Arduino.
    - Connect the **GND** of the servo to the **GND pin** on the Arduino.

#### 3. **Flame Sensors Connections**
You’ll need to connect the four flame sensors as follows:
- **Front Flame Sensor** → Connect to **sensorFront** (Arduino Pin A0)
- **Back Flame Sensor** → Connect to **sensorBack** (Arduino Pin A1)
- **Left Flame Sensor** → Connect to **sensorLeft** (Arduino Pin A2)
- **Right Flame Sensor** → Connect to **sensorRight** (Arduino Pin A3)

Each flame sensor typically has three pins: **VCC**, **GND**, and **Analog Output**. Connect them as follows:
- **VCC** of all sensors → Connect to the **5V pin** on the Arduino.
- **GND** of all sensors → Connect to the **GND pin** on the Arduino.
- **Analog Output** of each sensor → Connect to the respective analog pins as mentioned above.

#### 4. **Relay Connection (Optional)**
If you decide to use a relay to control the extinguisher:
- **Relay Control Pin** → Connect to **relayPin** (Arduino Pin 2)
- **Power and Ground for Relay**:
  - Connect the **VCC** of the relay to the **5V pin** on the Arduino.
  - Connect the **GND** of the relay to the **GND pin** on the Arduino.

### Power Supply
- **Motor Driver Power**: Connect the motor driver's power supply (typically 12V) to its power input (VCC) and connect its ground (GND) to the common ground shared with the Arduino.
- **Arduino Power**: You can power the Arduino via USB or by connecting a battery to the **Vin pin** or the barrel jack.

### Summary of Connections
Here’s a concise list of the connections:
- **Motors**: Connected to the motor driver, which is controlled by Arduino pins 3, 4, 5, 6, 9, and 10.
- **Servo**: Connected to pin 7.
- **Flame Sensors**: Connected to analog pins A0, A1, A2, and A3.
- **Relay**: Connected to pin 2 (optional).
- **Common Ground**: Ensure all grounds are connected together.

