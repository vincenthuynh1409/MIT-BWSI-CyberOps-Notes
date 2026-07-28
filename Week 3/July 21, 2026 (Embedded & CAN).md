# July 21, 2026 (Embedded & CAN)

<u>Embedded Systems:</u>
- Specialized computers built into larger devices.
- Examples: cars, medical devices, routers, ATMs, IoT devices, industrial systems.
- Components: **MCU/CPU, sensors, actuators, firmware, RTOS**.
- Security is important because compromised systems can affect the **physical world**, not just data.

 <u>Automotive Embedded Systems:</u>
- Modern cars contain many **ECUs (Electronic Control Units)** that control:
	- Engine
	- Brakes
	- Steering
	- Airbags
	- Infotainment
	- Doors and windows

> ECUs communicate using networks such as **CAN, LIN, FlexRay, and Automotive Ethernet**.


<u>CAN Bus:</u>
- **CAN (Controller Area Network)** is a message-based communication protocol widely used in vehicles.

```
        CAN Bus
       /   |   \
   Engine Brakes Dashboard
     ECU    ECU     ECU
```

<u>Important Characteristics:</u>
- ECUs share a common communication bus.
- Messages contain a **CAN ID** and data.
- CAN IDs determine message priority.
- **Lower CAN ID = Higher priority**.
- Traditional CAN does **not inherently authenticate the sender**.


<u>CAN Bus Security Vulnerabilities:</u>
- **Lack of Authentication**
	- CAN does not inherently verify who sent a message.
	- Can enable **spoofing** and **message injection**.
- **Lack of Encryption**
	- Traditional CAN traffic is generally unencrypted.
	- Attackers with network access may monitor and analyze traffic.
- **Message Injection**
	- Unauthorized messages can potentially be sent onto the bus.
- **Spoofing**
	- An attacker may send fake messages that appear legitimate.
- **Replay Attacks**
	- Previously captured messages can potentially be retransmitted.
- **Denial of Service (DoS)**
	- Excessive or high-priority traffic can disrupt legitimate communication.
-  **Weak Segmentation**
	- If networks are poorly separated, compromising one system may provide a path toward more critical systems.


<u>Automotive Attack Surface:</u>
- Potential entry points include:
	- **Bluetooth**
	- **Wi-Fi**
	- **USB**
	- **Cellular/telematics**
	- **Keyless systems**
	- **Diagnostic interfaces**
	- **Infotainment systems**

**A simplified attack path:**

```
External Entry Point
        ↓
Compromise System
        ↓
Reach Internal Network
        ↓
Attempt Access to CAN
```

<u>Security Defenses:</u>
- **Network Segmentation** = Separates critical and non-critical systems.
- **Secure Gateways** = Filter and control communication between networks.
- **CAN IDS** = Detects abnormal message IDs, frequencies, or patterns.
- **Message Authentication** = Helps verify that messages are legitimate.
- **Secure Boot** = Ensures only trusted firmware runs.
- **Signed Firmware** = Prevents unauthorized software from being installed.
- **Secure OTA Updates** = Allows vehicles to receive authenticated and verified updates.

