# ICS 4111: Embedded Systems & IoT
## Semester Project: Deliverable 1
### Flora Farms - Rose Greenhouse Monitoring System

**Group Members:** [Add your group member names here]  
**Date:** [Add submission date]  
**Assigned Flower:** Rose

---

## 1. Environmental Requirements for Rose Growth

After thorough research, our team has identified the following environmental requirements for optimal rose growth in greenhouse conditions:

| Environmental Parameter | Optimal Range | Unit | Notes |
|------------------------|---------------|------|-------|
| **Temperature Range** | 18-24°C (Day) / 15-21°C (Night) | °C | For most rose varieties, the ideal temperature range is around 65-75°F during the day (18-24°C), and 60-70°F overnight (15-21°C) [[2]] |
| **Relative Humidity** | 50-80 | % RH | The optimal greenhouse humidity range is between 50% and 80% of RH, with around 80% RH often cited as optimal for greenhouse cultivation [[14]][[17]] |
| **Soil Type** | Well-draining, loamy soil | - | Roses require well-drained and nutrient-rich soil for optimal growth [[42]] |
| **Soil Moisture Content** | 40-60 | % volumetric water content | Roses grow best in evenly moist soil. Irrigate when the top 2 inches of soil become dry [[36]] |
| **Soil pH Range** | 6.0-7.0 (Optimal: 6.5) | pH | The ideal soil pH for growing roses lies between 6.0 and 7.0 (slightly acidic to neutral), with optimal around 6.5 [[20]][[23]][[24]] |
| **Sunlight Exposure** | 6-8 | hours/day | Roses require at least 6 hours of full sun per day, preferably 6-8 hours of direct sunlight, ideally in the morning [[42]][[44]][[45]] |

### Additional Notes:
- **LPG Monitoring:** Since the greenhouses use LPG heating systems, monitoring for gas leaks (methane, propane, butane) is critical for safety
- **Temperature Integration:** Lower temperatures may lead to reduced flowering, while temperatures above 35°C can cause roses to cease blooming [[8]]
- **Humidity Control:** High humidity (70-90%) during winter conditions can affect stomatal function and plant health [[11]]

---

## 2. Hardware Components List

Our team has identified the following hardware components required to develop the embedded monitoring system for rose greenhouses:

### 2.1 Core Components

| Component | Quantity | Purpose | Specifications |
|-----------|----------|---------|----------------|
| **ESP32S DevKIT WIFI+ BLE Module (30Pin)** | 1-2 | Main microcontroller unit for data processing and WiFi communication | Dual-core 32-bit MCU, 2.4 GHz Wi-Fi, Bluetooth 5 (LE), 3.3V operating voltage [[56]][[57]] |
| **DHT22 (AM2302) Temperature and Humidity Sensor** | 1 | Monitor air temperature and relative humidity in greenhouse | Temperature: -40 to 125°C (±0.5°C), Humidity: 0-100% RH (±2% RH), 3.3-6V DC [[63]][[64]] |
| **MQ-5 LPG Gas Sensor** | 1 | Detect LPG gas leaks (methane, propane, butane) from heating system | Detects LPG, natural gas, coal gas; 200-10000 ppm range; 5V operating voltage [[70]][[76]] |
| **1.3" White IIC 128×64 OLED LCD Display** | 1 | Local display of sensor readings and system status | 128×64 pixel resolution, I2C interface, 3.3-5V operation, SSD1306 driver [[79]][[85]] |
| **5V 1-Channel Low Level Trigger Relay Module** | 1 | Control external devices (heating system, ventilation) based on sensor data | 5V coil voltage, 10A contact rating, active-low trigger, SPDT configuration [[88]][[92]] |

### 2.2 Prototyping Tools and Accessories

| Component | Quantity | Purpose |
|-----------|----------|---------|
| **Breadboard (830-point or similar)** | 1-2 | Prototype circuit connections without soldering |
| **Jumper Wires (Male-to-Male, Male-to-Female, Female-to-Female)** | 20-30 | Connect components on breadboard and to ESP32 |
| **Resistors (10kΩ)** | 5-10 | Pull-up resistors for I2C lines and DHT22 data line |
| **Resistors (220Ω, 330Ω)** | 5 | Current limiting for LEDs and other components |
| **USB Cable (Micro-USB or USB-C)** | 1 | Power supply and programming interface for ESP32 |
| **5V Power Supply / Battery** | 1 | Power source for the system (compatible with 12V 100Ah greenhouse battery via regulator) |
| **Voltage Regulator (5V/3.3V)** | 1-2 | Step down 12V battery to 5V and 3.3V for components |
| **Capacitors (100nF, 10µF)** | 5-10 | Power supply decoupling and filtering |
| **Multimeter** | 1 | Test voltages, continuity, and troubleshoot circuits |
| **Wire Stripper/Cutter** | 1 | Prepare wires for connections |

### 2.3 Additional Sensors (Optional for Enhanced Monitoring)

| Component | Quantity | Purpose |
|-----------|----------|---------|
| **Soil Moisture Sensor (Capacitive type)** | 1-2 | Monitor soil moisture content for irrigation control |
| **Soil pH Sensor** | 1 | Monitor soil pH levels |
| **Light Intensity Sensor (BH1750 or similar)** | 1 | Measure sunlight exposure in greenhouse |
| **Water Flow Sensor** | 1 | Monitor irrigation water usage from river stream |

---

## 3. Component Datasheets

Our team has retrieved the following datasheets and technical documentation for all major components:

### 3.1 ESP32S DevKIT WIFI+ BLE Module

**Datasheet Links:**
- [ESP32 DevKitC Official Documentation - Espressif](https://docs.espressif.com/projects/esp-dev-kits/en/latest/esp32/esp32-devkitc/index.html) [[51]]
- [ESP32 Datasheet PDF - SparkFun](https://cdn.sparkfun.com/datasheets/IoT/esp32_datasheet_en.pdf) [[53]]
- [ESP-32S Datasheet - Electronics Source](https://www.es.co.th/Schemetic/PDF/ESP32.PDF) [[49]]

**Key Specifications:**
- Operating Voltage: 2.7V - 3.6V (typical 3.3V)
- Power Supply (USB): 5V DC
- Operating Current: Minimum 500mA
- Wi-Fi: 2.4 GHz up to 150 Mb/s
- Bluetooth: BLE 4.0 and legacy Bluetooth
- GPIO Pins: 30+ programmable pins
- ADC: 12-bit SAR ADC up to 18 channels
- Flash: 4MB (typical)

### 3.2 DHT22 (AM2302) Temperature and Humidity Sensor

**Datasheet Links:**
- [DHT22 Datasheet PDF - SparkFun](https://cdn.sparkfun.com/assets/f/7/d/9/c/DHT22.pdf) [[61]]
- [AM2302/DHT22 User Manual PDF](https://cdn-reichelt.de/documents/datenblatt/B300/ST1173.pdf) [[62]]
- [Digital Humidity and Temperature Sensor AM2302 PDF - Adafruit](https://cdn-shop.adafruit.com/datasheets/Digital+humidity+and+temperature+sensor+AM2302.pdf) [[66]]

**Key Specifications:**
- Power Supply: 3.3V - 6V DC
- Operating Current: 2.5mA (max)
- Temperature Range: -40°C to 125°C
- Temperature Accuracy: ±0.5°C
- Humidity Range: 0-100% RH
- Humidity Accuracy: ±2% RH
- Output: Digital signal (single-bus interface)
- Sampling Rate: 0.5 Hz (once every 2 seconds)

### 3.3 MQ-5 LPG Gas Sensor

**Datasheet Links:**
- [MQ-5 Technical Data PDF - Seeed Studio](https://files.seeedstudio.com/wiki/Grove-Gas_Sensor-MQ5/res/MQ-5.pdf) [[72]]
- [MQ-5 Flammable Gas Sensor PDF - Winsen](https://www.winsen-sensor.com/d/files/MQ-5.pdf) [[76]]
- [MQ-5 Datasheet - WinSEN Electronics](https://www.alldatasheet.com/datasheet-pdf/pdf/1304543/WINSEN/MQ-5.html) [[69]]

**Key Specifications:**
- Operating Voltage: DC 5V
- Operating Current: 150mA (typical)
- Heating Consumption: < 800mW
- Detection Range: 200-10000 ppm
- Sensitive Gases: LPG, natural gas, town gas (methane, propane, butane)
- Operating Temperature: -10°C to 50°C
- Output: Analog voltage (0-5V)
- Response Time: < 10 seconds
- Recovery Time: < 30 seconds

### 3.4 1.3" White IIC 128×64 OLED LCD Display

**Datasheet Links:**
- [1.3inch IIC OLED Module User Manual PDF](https://cdn.awsli.com.br/945/945993/arquivos/1.3inch_IIC_OLED_Module_MC130GX&MC130VX_User_Manual_EN.pdf) [[78]]
- [1.3inch IIC OLED Module - LCD Wiki](https://www.lcdwiki.com/1.3inch_IIC_OLED_Module_SKU:MC130VX) [[85]]
- [OLED 128x64 1.3" I2C PDF - Universal Solder](https://universal-solder.ca/downloads/canaduino_oled_1.3_i2c.pdf) [[81]]

**Key Specifications:**
- Display Size: 1.3 inch diagonal
- Resolution: 128×64 pixels
- Display Color: White on black (or blue on black)
- Interface: I2C (2-wire: SDA, SCL)
- Driver IC: SSD1306 or SH1106
- Operating Voltage: 3.3V - 5V DC
- Power Consumption: < 40mW
- Operating Temperature: -40°C to +80°C
- I2C Address: 0x3C (typical)

### 3.5 5V 1-Channel Low Level Trigger Relay Module

**Datasheet Links:**
- [1 Channel 5V Relay Module PDF - Handson Technology](https://handsontec.com/dataspecs/relay/1Ch-relay.pdf) [[88]]
- [5V Relay Module Datasheet PDF - DigiKey](https://mm.digikey.com/Volume0/opasdata/d220001/medias/docus/5773/TS0010D%20DATASHEET.pdf) [[94]]
- [Relay Module Datasheet PDF - BerryBase](https://www.berrybase.de/en/product-datasheet/019234a41f1b7116b417eac37a61e879/create) [[87]]

**Key Specifications:**
- Coil Voltage: 5V DC
- Coil Current: 15-20mA (trigger current), ~70mA (active)
- Supply Voltage: 3.75V - 6V DC
- Contact Configuration: SPDT (Single Pole Double Throw)
- Contact Rating: 10A at 250VAC / 10A at 30VDC
- Trigger Signal: Low level trigger (active-low)
- Quiescent Current: 2mA
- Optical Isolation: Yes (protects microcontroller)
- Terminals: NO (Normally Open), NC (Normally Closed), COM (Common)

---

## 4. Schematic Diagrams

Our team has developed three different schematic architectures based on the specified components. Each design serves different monitoring and control scenarios for the rose greenhouse.

### 4.1 Architecture A: Single ESP32S with All Sensors

**Description:**  
This architecture uses a single ESP32S microcontroller connected to the MQ-5 gas sensor, DHT22 temperature/humidity sensor, and 1.3" OLED display. This is the simplest and most cost-effective design suitable for basic monitoring applications.

**Circuit Diagram:**

*[Refer to Figure 1 - Single ESP32S Architecture]*

**Connections:**

| Component | Pin | ESP32S Pin | Additional Components |
|-----------|-----|------------|----------------------|
| **MQ-5 Gas Sensor** | VCC | 5V | - |
| | GND | GND | - |
| | AOUT (Analog Output) | GPIO 34 (ADC1_CH6) | - |
| | H (Heater) | 5V | - |
| **DHT22 Sensor** | VCC | 3.3V | - |
| | GND | GND | - |
| | DATA | GPIO 4 | 10kΩ pull-up resistor to 3.3V |
| **OLED Display** | VCC | 3.3V | - |
| | GND | GND | - |
| | SCL | GPIO 22 | 10kΩ pull-up resistor to 3.3V |
| | SDA | GPIO 21 | 10kΩ pull-up resistor to 3.3V |

**Advantages:**
- Simple wiring and programming
- Cost-effective (single microcontroller)
- Lower power consumption
- Easy to prototype and debug

**Disadvantages:**
- Single point of failure
- Limited GPIO availability for expansion
- All processing on one chip

---

### 4.2 Architecture B: Dual ESP32S with UART Communication

**Description:**  
This architecture uses two ESP32S microcontrollers communicating via UART serial communication. ESP32S_1 handles the MQ-5 gas sensor, while ESP32S_2 manages the DHT22 sensor. This design provides distributed processing and modularity.

**Circuit Diagram:**

*[Refer to Figure 2 - Dual ESP32S UART Communication Architecture]*

**Connections:**

**ESP32S_1 (Gas Monitoring Node):**
| Component | Pin | ESP32S_1 Pin | Additional Components |
|-----------|-----|--------------|----------------------|
| **MQ-5 Gas Sensor** | VCC | 5V | - |
| | GND | GND | - |
| | AOUT | GPIO 34 (ADC1_CH6) | - |
| **UART Communication** | TX | GPIO 1 → ESP32S_2 RX | - |
| | RX | GPIO 3 ← ESP32S_2 TX | - |
| | GND | GND (Common) | - |

**ESP32S_2 (Climate Monitoring Node):**
| Component | Pin | ESP32S_2 Pin | Additional Components |
|-----------|-----|--------------|----------------------|
| **DHT22 Sensor** | VCC | 3.3V | - |
| | GND | GND | - |
| | DATA | GPIO 4 | 10kΩ pull-up resistor to 3.3V |
| **UART Communication** | TX | GPIO 1 → ESP32S_1 RX | - |
| | RX | GPIO 3 ← ESP32S_1 TX | - |
| | GND | GND (Common) | - |

**UART Communication Protocol:**
- Baud Rate: 115200 bps (typical)
- Data Bits: 8
- Stop Bits: 1
- Parity: None
- Flow Control: None

**Advantages:**
- Distributed processing load
- Modular design - easier to maintain individual nodes
- Redundancy - if one node fails, the other may continue operating
- Scalability - additional nodes can be added

**Disadvantages:**
- Higher cost (two microcontrollers)
- More complex programming (inter-processor communication)
- Higher power consumption
- Requires synchronization between nodes

---

### 4.3 Architecture C: Relay-Controlled Dual ESP32S System

**Description:**  
This advanced architecture uses a relay module to control power to the second ESP32S based on DHT22 sensor readings from the first ESP32S. This design enables power management and conditional activation of the gas monitoring system, which can help conserve energy in the solar-powered greenhouse.

**Circuit Diagram:**

*[Refer to Figure 3 - Relay-Controlled Dual ESP32S Architecture]*

**Connections:**

**ESP32S_1 (Primary Controller - Climate Monitoring):**
| Component | Pin | ESP32S_1 Pin | Additional Components |
|-----------|-----|--------------|----------------------|
| **DHT22 Sensor** | VCC | 5V | - |
| | GND | GND | - |
| | DATA | GPIO 4 | 10kΩ pull-up resistor |
| **Relay Control** | GPIO 4 | Relay Module IN | - |

**5V 1-Channel Relay Module:**
| Pin | Connection | Purpose |
|-----|------------|---------|
| VCC | 5V | Relay coil power |
| GND | GND | Common ground |
| IN | ESP32S_1 GPIO 4 | Control signal (active-low) |
| COM | 5V (via diode) | Common terminal |
| NO | ESP32S_2 EN (GPIO 5) | Normally open - enables ESP32S_2 when activated |
| NC | - | Not connected |
| **Protection Diode** | 1N4007 across relay coil | Prevents back EMF damage |

**ESP32S_2 (Secondary Controller - Gas Monitoring):**
| Component | Pin | ESP32S_2 Pin | Additional Components |
|-----------|-----|--------------|----------------------|
| **Enable Pin** | EN | GPIO 5 (controlled by relay) | Activated when relay closes |
| **MQ-5 Gas Sensor** | VCC | 5V (always powered) | - |
| | GND | GND | - |
| | AOUT | GPIO 34 (ADC1_CH6) | - |
| | H (Heater) | 5V | - |

**Control Logic:**
- When temperature/humidity exceeds thresholds, ESP32S_1 sets GPIO 4 LOW
- This activates the relay (active-low trigger)
- Relay closes NO contact, enabling ESP32S_2 via GPIO 5
- ESP32S_2 wakes up and begins gas monitoring
- When conditions normalize, ESP32S_1 sets GPIO 4 HIGH
- Relay deactivates, ESP32S_2 enters low-power mode

**Advantages:**
- Energy efficient - gas monitoring only active when needed
- Extends battery life in solar-powered system
- Intelligent power management
- Reduces unnecessary MQ-5 heater power consumption

**Disadvantages:**
- Most complex design
- Continuous gas monitoring not possible
- Requires careful threshold tuning
- Additional relay component adds cost and potential failure point

---

## 5. Power Supply Considerations

Given that the Flora Farms greenhouses are solar-powered with 200W solar panels and a 12V 100Ah battery setup, our embedded system must be compatible with this power infrastructure.

### Power Requirements Calculation:

| Component | Voltage | Current (Typical) | Power |
|-----------|---------|-------------------|-------|
| ESP32S (active) | 3.3V | 80mA | 264mW |
| ESP32S (deep sleep) | 3.3V | 10µA | 33µW |
| DHT22 (measuring) | 3.3V | 2.5mA | 8.25mW |
| MQ-5 (with heater) | 5V | 150mA | 750mW |
| OLED Display | 3.3V | 12mA | 39.6mW |
| Relay Module (active) | 5V | 70mA | 350mW |

**Total System Power (Architecture A - All active):** ~1.4W  
**Daily Energy Consumption (24h operation):** ~33.6 Wh/day

This is well within the capacity of the 12V 100Ah battery (1200 Wh capacity) and can be easily sustained by the 200W solar panels.

### Voltage Regulation:
To step down from 12V battery to required voltages:
- **12V → 5V:** Use LM7805 or buck converter (more efficient)
- **5V → 3.3V:** Use AMS1117-3.3 or buck converter
- **Recommendation:** Use DC-DC buck converters for higher efficiency (85-95%) compared to linear regulators

---

## 6. Team Collaboration Evidence

### Group Meeting Minutes

**Meeting 1:** [Date]  
**Attendees:** [List all members]  
**Topics Discussed:**
- Initial research on rose growing requirements
- Component selection and specifications
- Task distribution among team members

**Meeting 2:** [Date]  
**Attendees:** [List all members]  
**Topics Discussed:**
- Review of datasheets and component compatibility
- Schematic diagram design discussions
- Power supply calculations

**Meeting 3:** [Date]  
**Attendees:** [List all members]  
**Topics Discussed:**
- Final review of all three architectures
- Documentation compilation
- Submission preparation

### Task Distribution

| Team Member | Responsibilities |
|-------------|------------------|
| [Member 1] | Research on rose environmental requirements, temperature and humidity monitoring |
| [Member 2] | Component datasheet collection, MQ-5 gas sensor research |
| [Member 3] | Schematic diagram design (Architecture A and B), power calculations |
| [Member 4] | Schematic diagram design (Architecture C), documentation formatting |
| [All Members] | Group discussions, design reviews, final document review |

### Group Photo
*[Insert group photo here from lab session or team meeting]*

---

## 7. References

1. DryGair. "How to Grow Roses – Rose Greenhouse Guide." https://drygair.com/blog/rose-greenhouse/ [[2]]
2. Ludwig's Roses. "Conditions that suit roses." https://www.ludwigsroses.co.za [[4]]
3. New Mexico State University. "Growing Roses." https://pubs.nmsu.edu/_h/H165/ [[8]]
4. Rose Society of NSW. "Soil Improvement and the importance of pH." https://nsw.rose.org.au [[20]]
5. The Spruce. "Preparing Garden Soil for Growing Roses." https://www.thespruce.com/soil-for-roses-1403048 [[23]]
6. Smithsonian Gardens. "Tips for Growing Healthy Roses." https://gardens.si.edu/learn/blog/tips-for-growing-healthy-roses/ [[42]]
7. Espressif Systems. "ESP32-DevKitC Documentation." https://docs.espressif.com [[51]]
8. SparkFun. "ESP32 Datasheet." https://cdn.sparkfun.com/datasheets/IoT/esp32_datasheet_en.pdf [[53]]
9. Adafruit. "DHT22/AM2302 Sensor Datasheet." https://cdn-shop.adafruit.com/datasheets/Digital+humidity+and+temperature+sensor+AM2302.pdf [[66]]
10. Seeed Studio. "MQ-5 Gas Sensor Technical Data." https://files.seeedstudio.com/wiki/Grove-Gas_Sensor-MQ5/res/MQ-5.pdf [[72]]
11. Winsen Electronics. "MQ-5 Flammable Gas Sensor." https://www.winsen-sensor.com/d/files/MQ-5.pdf [[76]]
12. LCD Wiki. "1.3inch IIC OLED Module." https://www.lcdwiki.com/1.3inch_IIC_OLED_Module_SKU:MC130VX [[85]]
13. Handson Technology. "1 Channel 5V Relay Module." https://handsontec.com/dataspecs/relay/1Ch-relay.pdf [[88]]

---

## 8. Conclusion

Our team has successfully completed Deliverable 1 for the Flora Farms rose greenhouse monitoring project. We have:

1. ✅ Researched and documented the environmental requirements for rose growth, including temperature (18-24°C day, 15-21°C night), humidity (50-80% RH), soil pH (6.0-7.0), soil moisture (40-60%), and sunlight exposure (6-8 hours/day)

2. ✅ Identified all necessary hardware components including the ESP32S microcontroller, DHT22 sensor, MQ-5 gas sensor, OLED display, and relay module, along with prototyping tools

3. ✅ Retrieved and documented datasheets for all major components with direct links to technical documentation

4. ✅ Developed three distinct schematic architectures:
   - Architecture A: Single ESP32S with all sensors (simple, cost-effective)
   - Architecture B: Dual ESP32S with UART communication (modular, distributed)
   - Architecture C: Relay-controlled dual ESP32S (energy-efficient, intelligent)

5. ✅ Calculated power requirements and confirmed compatibility with the greenhouse's 200W solar panel and 12V 100Ah battery system

The next steps for our project will involve prototyping the chosen architecture (likely Architecture A for initial testing), developing the firmware for sensor data acquisition, and implementing WiFi connectivity for cloud communication.

---

**Document Prepared By:** [Your Name/Team Lead]  
**Reviewed By:** [All Team Members]  
**Submission Date:** [Date]

---

*This document is part of the ICS 4111: Embedded Systems & IoT semester project for Strathmore University.*
