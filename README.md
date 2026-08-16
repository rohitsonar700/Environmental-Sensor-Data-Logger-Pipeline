# Environmental Sensor Data-Logger Pipeline

An STM32-based embedded data-logging pipeline that reads real-time ambient temperature and humidity metrics from an HTU21DF sensor over I2C and streams formatted CSV telemetry over USART for TinyML and Edge AI model development.

---

## 📸 Hardware Setup & Connections
<img width="625" height="351" alt="Picture" src="https://github.com/user-attachments/assets/b8e4da09-8b88-4d47-af11-b20c8c2c0b41" />
<img width="564" height="317" alt="Picture2" src="https://github.com/user-attachments/assets/1de4de4d-afc4-473c-9bdd-7155607608c2" />

*Figure : STM32 Nucleo board connected to HTU21DF environmental sensor.*

---

## 📌 Key Features
* **I2C Communication**: Interfaced HTU21DF digital environmental sensor using STM32 HAL I2C driver.
* **Real-Time Telemetry**: Streams raw and calibrated sensor metrics over USART/UART to a host PC.
* **CSV Format Generation**: Formats data frames directly on-chip into a standard `.csv` structure for direct AI dataset creation.
* **TinyML Ready**: Designed specifically to collect labeled environmental datasets for NanoEdge AI Studio / Edge AI pipelines.

---

## 🛠️ Hardware & Software
* **Microcontroller**: STM32 Nucleo Board (e.g., NUCLEO-F411RE)
* **Sensor**: HTU21DF Digital Humidity & Temperature Sensor
* **Protocols**: I2C (Sensor communication), USART (PC Data streaming)
* **IDE**: STM32CubeIDE
* **Language**: Embedded C

---

## 🔌 Hardware Pinout
| HTU21DF Sensor | STM32 Board Pin | Function |
| :--- | :--- | :--- |
| **VCC** | 3.3V | Power Supply |
| **GND** | GND | Ground |
| **SDA** | PB9 / I2C1_SDA | Data Line |
| **SCL** | PB8 / I2C1_SCL | Clock Line |

---

## ⚙️ System Data Flow
1. **Sensor Initialization**: STM32 initializes I2C peripheral and checks HTU21DF status.
2. **Data Polling**: STM32 periodically queries temperature and relative humidity registers over I2C.
3. **Data Processing**: Converts raw values into physical parameters using datasheet formulas in C.
4. **CSV Streaming**: Constructs formatted CSV strings (`Timestamp, Temperature_C, Humidity_Pct`) and transmits them over USART to serial logging software.

---

## 📊 Sample Telemetry Stream Output
```csv
Timestamp_ms,Temperature_C,Humidity_Pct
1000,24.52,55.30
2000,24.55,55.28
3000,24.60,55.35
