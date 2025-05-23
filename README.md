# PyroPatrol

PyroPatrol is an Arduino-based system for automated fire detection and response. It leverages analog fire/heat sensors, a servo motor, and multiple digital outputs to provide real-time monitoring and active intervention in case of fire hazards. This project is ideal for educational, prototyping, and safety automation applications.

## Features

- **Multi-Point Fire Detection:** Continuously monitors three analog fire/heat sensors for rapid and reliable detection.
- **Automated Response Mechanism:** Activates a servo motor to perform a sweeping action, simulating a scanning or extinguishing process.
- **Multi-Device Output Control:** Manages up to five digital output devices (e.g., alarms, LEDs, relays) for alerting or activating external systems.
- **Serial Data Logging:** Outputs sensor readings and system status to the Serial Monitor for diagnostics and data collection.
- **Customizable Logic:** Easily adjust thresholds, pin assignments, and response logic to suit your specific requirements.

## Hardware Requirements

- Arduino Uno (or compatible board)
- 3 Analog fire/heat sensors (connected to A0, A1, A2)
- Servo motor (signal wire to pin 11)
- 5 Digital output devices (LEDs, buzzers, relays, etc. on pins 2, 3, 4, 5, 6)
- Jumper wires and breadboard
- Common 5V power supply and ground

## Software Requirements

- Arduino IDE
- Servo library (bundled with Arduino IDE)

## Setup Instructions

1. **Hardware Setup:**

   - Connect the analog outputs of the three fire/heat sensors to Arduino pins A0, A1, and A2.
   - Connect the servo motor's signal wire to digital pin 11; connect its power and ground to 5V and GND.
   - Attach output devices (such as LEDs, buzzers, or relays) to digital pins 2, 3, 4, 5, and 6, using appropriate resistors or driver circuits as needed.
   - Ensure all components share a common ground with the Arduino.

2. **Software Setup:**

   - Open `Pyropatrol.ino` in the Arduino IDE.
   - Select the correct board and port under the Tools menu.
   - Upload the sketch to your Arduino board.

3. **Operation:**
   - Open the Serial Monitor at 9600 baud to observe real-time sensor readings and system status.
   - The system will automatically detect fire/heat and activate the servo and output devices according to the programmed logic.

## Circuit Diagram

### Textual Schematic

```
[Arduino Uno] |-- A0 <---[Fire/Heat Sensor 1]
              |-- A1 <---[Fire/Heat Sensor 2]
              |-- A2 <---[Fire/Heat Sensor 3]
              |-- D11 -->[Servo Motor Signal]
              |-- D2 -->[Output Device 1 (Relay)]
              |-- D3 -->[Output Device 2]
              |-- D4 -->[Output Device 3]
              |-- D5 -->[Output Device 4]
              |-- D6 -->[Output Device 5]
              |-- 5V ----+---[Sensors VCC]
              |          +---[Servo VCC]
              |          +---[Output Devices VCC]
              |-- GND----+---[Sensors GND]
                         +---[Servo GND]
                         +---[Output Devices GND]
```

**Wiring Notes:**

- Connect each sensor's analog output to A0, A1, and A2.
- The servo's signal wire goes to D11; power and ground to 5V and GND.
- Each output device (LED, buzzer, relay, etc.) connects its signal pin to D2–D6, with appropriate resistors if needed.
- All components must share a common ground with the Arduino.

For a graphical diagram, refer to the [Fritzing project file](#) (add if available) or use the above schematic as a guide.

## Detailed Explanation

PyroPatrol is designed to automate fire detection and response using an Arduino Uno. Three analog fire/heat sensors continuously monitor the environment. When any sensor detects a value above a set threshold (indicating fire or heat), the Arduino triggers a servo motor to sweep between 60° and 120°, simulating a scanning or extinguishing action. Simultaneously, up to five digital output devices (such as alarms, LEDs, or relays) are activated to alert users or trigger further actions (like activating a fire suppression system).

Sensor readings and system status are output to the Serial Monitor for real-time monitoring and debugging. The system is modular and can be customized for different sensor types, thresholds, and output devices.

### Circuit Explanation

- **Sensors:** Each fire/heat sensor outputs an analog voltage proportional to the detected heat or flame. These outputs are connected to analog pins A0, A1, and A2 on the Arduino. The sensors' VCC and GND are connected to the Arduino's 5V and GND rails.
- **Servo Motor:** The servo's signal wire connects to digital pin 11. Its power (VCC) and ground (GND) are connected to the Arduino's 5V and GND. The servo is activated to sweep between 60° and 120° when fire is detected, simulating a scanning or extinguishing action.
- **Output Devices:** Up to five digital output devices (such as LEDs, buzzers, or relays) are connected to digital pins 2 through 6. Each device's signal/control pin connects to the respective Arduino pin, with VCC and GND connected to the power rails. Use current-limiting resistors for LEDs and appropriate driver circuits for relays or high-power devices.
- **Power and Ground:** All components must share a common ground with the Arduino to ensure reliable operation and signal integrity.

> **Tip:** For a visual schematic, you can use tools like Fritzing or Tinkercad Circuits. If available, add a link to your Fritzing project file here.

## Customization

- **Sensor Thresholds:** Adjust the threshold values in the code to match your specific sensors and environmental conditions.
- **Output Devices:** Modify pin assignments and logic to control different types or numbers of output devices.
- **Expansion:** Integrate additional sensors (e.g., smoke, gas) or actuators (e.g., water pumps) as needed for your application.

## Code Overview

- The main logic resides in `Pyropatrol.ino`.
- The Arduino continuously reads values from the three analog sensors.
- If any sensor reading exceeds the defined threshold, the servo motor sweeps between 60° and 120° for a set number of cycles.
- Digital output devices are activated (set HIGH) when fire/heat is detected and deactivated (set LOW) otherwise.
- All sensor readings and system actions are reported via the Serial Monitor for monitoring and debugging.

## Detailed System Operation

1. **Monitoring:** The Arduino polls all three analog sensors in a loop.
2. **Detection:** If any sensor detects a value above the fire/heat threshold, the system enters response mode.
3. **Response:**
   - The servo motor performs a sweeping motion, which can be used to direct a camera, nozzle, or simply indicate scanning.
   - All connected output devices are activated to alert users or trigger further safety mechanisms.
4. **Reset:** When all sensor readings return below the threshold, the servo and outputs return to their idle state.
5. **Logging:** All events and sensor values are sent to the Serial Monitor for review.

## License

This project is provided for educational and prototyping purposes. Please review and comply with local safety regulations before deploying in real-world scenarios.

---

**Author(s):**

- Paramesh Kumar Selvaraj
- Purusothaman Rajan
- Tharun Murugavel
