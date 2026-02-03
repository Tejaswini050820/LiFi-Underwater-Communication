 Underwater Li-Fi Communication System

 Major Project Phase 2 | Bachelor of Engineering in Computer Science

This repository contains the implementation of a **Visible Light Communication (VLC)** system—popularly known as **Li-Fi**—engineered for underwater data transmission. Traditional RF (Radio Frequency) communication fails in underwater environments due to high conductivity and signal absorption; this project utilizes the high-bandwidth, low-latency properties of light to bridge that gap.

---

 🚀 System Overview

The system establishes a secure simplex communication link between a transmitter (ESP32) and a receiver (ESP32/PC). Data is encoded, encrypted, and then pulsed through a high-intensity LED. The receiver captures these pulses via an LDR/Photodiode and decrypts the message in real-time.

🔒 Security & Reliability Features

SHA-256 Dynamic Encryption: Every byte sent is XOR-encrypted using a key generated from a SHA-256 hash of a rolling counter.
Sliding Window Synchronization: The receiver utilizes a Window Size of 5 to handle potential packet loss, ensuring the transmitter and receiver stay in sync even if a signal is missed.
Binary Mapping: Efficient data handling using a CSV-based lookup table (`data.csv`) for predefined command sentences.

---

🛠️ Technical Architecture

 Hardware Components

Microcontroller: ESP32 (Dual-core, integrated ADC and UART).
Transmitter: High-Intensity White LED + Transistor Driver Circuit.
Receiver: LDR (Light Dependent Resistor) / Photodiode Module.
Medium: Underwater environment (simulated or tank-tested).

 Software Stack

Firmware: Developed in C using the ESP-IDF framework.
 `transmit.c`: Handles precision timing for bit modulation ( bit duration).
 `receive.c`: Implements ADC sampling and threshold-based signal detection.


Application: Python 3.x for the end-user interface.
 `receiver.py`: Manages serial communication, cryptographic decryption, and CSV data mapping.



---

 📂 Project Structure

 `transmit.c` – Source code for the LED modulation logic.
 `receive.c` – Source code for the sensor data acquisition and framing.
 `receiver.py` – Python script for decryption and message display.
 `data.csv` – Mapping of 8-bit binary values to human-readable sentences.
 `tx_counter.txt` / `rx_counter.txt` – Persistent storage for the synchronization counters.

---

 📖 How to Use

1. Hardware Wiring: Connect LED to GPIO 14.
 Connect LDR/Sensor to GPIO 34.


2. Flash Firmware: Use VS Code with the ESP-IDF extension to build and flash the `.c` files to your respective ESP32 boards.
3. Run Receiver: Ensure the ESP32 is connected to your PC via USB.
```bash
python receiver.py

```


4. Monitor: The Python terminal will display the "Encrypted Byte" received via light and the corresponding "Decrypted Message."



