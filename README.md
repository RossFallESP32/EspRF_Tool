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

Download the toolkit from the official [EspRFTestTool Package](https://docs.espressif.com/projects/esp-test-tools/en/latest/esp32/_images/esprftesttool_tool.png).  
The package includes both the tools and required test firmware.

---

## ⚙️ Components

### EspRFTestTool
- **COM Port Config** → Select ChipType, COM, BaudRate  
- **Download Config** → Choose `.bin` and flash via UART  
- **RF Test Config** → Select test mode (Wi-Fi, BT, Zigbee, Manual)  
- **Log Window** → Monitor status and results  

![EspRFTestTool Interface](https://docs.espressif.com/projects/esp-test-tools/en/latest/_images/rf_test_tool.png)

---

### DownloadTool
- Flash firmware into Flash or RAM  
- Steps:  
  1. Select ChipType, COM, BaudRate  
  2. Open port → Select `.bin` → Start Load  
  3. After flashing → Close port and reset chip  

![DownloadTool Interface](https://docs.espressif.com/projects/esp-test-tools/en/latest/_images/download_tool.png)

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