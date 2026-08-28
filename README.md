# EspRF_Tool
The EspRFTestTool toolkit is an RF test tool provided by Espressif. It contains EspRFTestTool, DownloadTool, and PowerLimitTool.

# EspRFTestTool
The EspRFTestTool toolkit is an RF test tool provided by Espressif. It contains EspRFTestTool, DownloadTool, and PowerLimitTool.
# EspRFTestTool Toolkit (ESP32)

EspRFTestTool is a set of utilities from **Espressif** designed for RF testing of ESP32 devices.  
It includes three main tools:

- **EspRFTestTool** → Main interface for RF testing  
- **DownloadTool** → Flash test firmware to the device  
- **PowerLimitTool** → Generate `phy_init_data` files to enforce TX power limits  

---

## 📦 Installation

Download the toolkit from the official [EspRFTestTool Package](https://dl.espressif.com/RF/EspRFTestTool_v5.2_Manual.zip).  
The package includes both the tools and required test firmware.

---

## ⚙️ Components

### EspRFTestTool
- **COM Port Config** → Select ChipType, COM, BaudRate  
- **Download Config** → Choose `.bin` and flash via UART  
- **RF Test Config** → Select test mode (Wi-Fi, BT, Zigbee, Manual)  
- **Log Window** → Monitor status and results  

![EspRFTestTool](https://github.com/RossFallESP32/EspRF_Tool/blob/main/img/esprftesttool_tool_1.png)
![EspRFTestTool Interface](https://docs.espressif.com/projects/esp-test-tools/en/latest/esp32/development_stage/rf_test_guide/rf_test_guide.html#esprftesttool)

---
### COM Port Configuration Area

![COM Port Configuration Area](https://github.com/RossFallESP32/EspRF_Tool/blob/main/img/esprftesttool_com_2.png)

- ChipType: Select the chip;

- COM: Select the serial port number;

- BaudRate: Select the baud rate;

- Open: Open the serial port;

- Close: Close the serial port.

  After configuring the serial port, you can perform quick flashing and RF tests.

  ---

  ### Download Configuration Area

  ![Download Configuration Area](https://github.com/RossFallESP32/EspRF_Tool/blob/main/img/esprftesttool_download_3.png)

  Generally, the DownloadTool is used to download the firmware required for RF tests. However, for some simple firmware, such as non-signaling test firmware and adaptivity test firmware, EspRFTestTool can be used for quick flashing.

- Pull down the Boot pin and re-power the chip to enter download mode;

- By default, flashing is conducted through UART;

- Select flash to download to the flash;

- Click Select Bin to select the bin file to be flashed;

- Click Load Bin to start flashing;

- After flashing is completed, pull up the Boot pin and re-power the chip to enter operation mode.

  ---

  ### RF Test Configuration Area

  ![RF Test Configuration Area](https://github.com/RossFallESP32/EspRF_Tool/blob/main/img/esprftesttool_rftest_4.png)

  After flashing the firmware, you can perform the corresponding RF tests:

- Wi-Fi Test: Used for Wi-Fi Non-Signaling Test;

- BT Test: Used for Bluetooth and Bluetooth LE Non-Signaling Test;

- Wi-Fi Adaptivity: Used for Wi-Fi Adaptivity Test;

- Zigbee Test: Used for 802.15.4 Non-Signaling Test;

- Manual: Used to enter serial port commands.

  For specific parameter configuration, please refer to the corresponding RF test document.

  ---

  ### Log Window

  The Log window is used to display the status of the tool. To view the log printed via the chip serial port, please use a general serial port assistant, such as SerialPortUtility.
![SerialPortUtility Interface](http://alithon.com/downloads)



### DownloadTool
- Flash firmware into Flash or RAM  
- Steps:  
  1. Select ChipType, COM, BaudRate  
  2. Open port → Select `.bin` → Start Load  
  3. After flashing → Close port and reset chip  

![DownloadTool Interface](https://docs.espressif.com/projects/esp-test-tools/en/latest/_images/download_tool.png)

Click "Tool" in the toolbar and select "DownloadTool" to enter the DownloadTool interface.



![DownloadTool](https://github.com/RossFallESP32/EspRF_Tool/blob/main/img/downloadtool_main_5.png)

Follow the steps below to flash the firmware:

- Set the <span style="color:red">red Chip Type red text</span>, <font color="red">COM Port red</font>, and "Baud Rate</font>. Then, click Open to <font color="red">open</font> the serial port;

- Select <font color="red">flash</font> to download to the flash;

- Select the firmware and flash it to the specified address;

- Check whether the chip has entered download mode. If yes, click <font color="red">Start Load</font> to start flashing.
- 
- After flashing is completed, the <font color="red">SUCC</font> sign shows up;

- After flashing is completed, click <font color="red">Close</font> to close the serial port.

![DownloadTool Selection](https://github.com/RossFallESP32/EspRF_Tool/blob/main/img/downloadtool_select_6.png)

---

### PowerLimitTool
- Adjust **Wi-Fi TX Power** to comply with country regulations  
- Supports FCC, CE, SRRC, NCC, KCC, MIC, IC  
- Generate `phy_init_bin` for single or multiple countries  

![PowerLimitTool Interface](https://docs.espressif.com/projects/esp-test-tools/en/latest/_images/power_limit_tool.png)

---

## 📡 RF Test Modes
- **Wi-Fi Test** → Non-Signaling  
- **BT Test** → Bluetooth/LE DTM  
- **Wi-Fi Adaptivity** → Adaptivity testing  
- **Zigbee Test** → 802.15.4 Non-Signaling  
- **Manual** → Send UART commands directly  

---

## 📊 Typical ESP32 TX Power (dBm)

| **Rate**       | **Power** |
|----------------|-----------|
| 11b 1 Mbps     | 19.5 |
| 11b 11 Mbps    | 19.5 |
| 11g 6 Mbps     | 18 |
| 11g 54 Mbps    | 14 |
| 11n-20 MCS0    | 18 |
| 11n-20 MCS7    | 13 |
| 11n-40 MCS0    | 18 |
| 11n-40 MCS7    | 13 |

---

## ✅ Summary
- EspRFTestTool is used for **RF performance testing of ESP32**  
- Works via **test firmware + UART**, without modifying production code  
- Ideal for **certification, QA, and TX power tuning**  

---

## 🔄 Workflow Diagram

```mermaid
flowchart TD
    A[Connect DUT via UART] --> B[Flash test firmware with DownloadTool]
    B --> C[Open EspRFTestTool]
    C --> D[Select RF Test Mode]
    D --> E[Run tests and monitor logs]
    E --> F[Adjust TX Power with PowerLimitTool if needed]
---

This README.md is now **GitHub‑ready** with code formatting, tables, images, and even a **Mermaid diagram** for workflow visualization.  

Would you like me to also add a **“Quick Start” section with example UART commands** so developers can run tests immediately without digging into the docs?
