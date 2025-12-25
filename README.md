# NitroWave
# Smart Soil Monitoring System for Flood Affected Farms

## 🌾 Project Overview

The **Smart Soil Monitoring System** is an innovative agricultural technology solution designed to help farmers recover from flood-damaged farmland by providing instant, cost-effective soil nutrient analysis. This project combines hardware (NPK sensor with Arduino and RS485 communication) and software (interactive web interfaces) to measure soil nutrient levels and deliver actionable fertilizer recommendations.

## 🌊 The Problem

When floods occur, they wash away essential nutrients from agricultural soil, leaving it unsuitable for cultivation. The impact varies by flood severity:

- **Heavy Floods**: Nitrogen levels drop to **85 mg/kg**, requiring urgent intervention costing **₹3,000-4,000 per acre**
- **Moderate Floods**: Nitrogen reduces to **165 mg/kg**, needing **₹2,000-2,500** in fertilizers
- **Light Floods**: Nitrogen at **235 mg/kg**, requiring **₹1,000-1,500** of amendments

### Traditional Lab Testing Issues:
- ❌ **Cost**: ₹2,000-3,000 per test
- ❌ **Time**: Takes several days for results
- ❌ **Accessibility**: Limited availability in rural areas
- ❌ **Scalability**: Expensive for frequent monitoring

## ✅ Our Solution

A portable, affordable NPK soil testing system that provides:
- ✔️ **Results in 30 seconds** (vs. days with lab testing)
- ✔️ **One-time device cost** (reusable thousands of times)
- ✔️ **Actionable recommendations** tailored to flood severity
- ✔️ **Easy-to-use web interface** for farmers
- ✔️ **Complete fertilizer guidance** with cost estimates

## 🔧 Hardware Components

The system uses the following hardware:

```
NPK Soil Sensor
    ↓
Arduino Microcontroller
    ↓
MAX485 RS485 Module (for serial communication)
    ↓
Web Interface (via USB/WiFi)
```

### Key Components:
- **NPK Sensor**: Measures Nitrogen (N), Phosphorus (P), and Potassium (K) in mg/kg
- **Arduino**: Processes sensor data via Modbus RTU protocol
- **MAX485 Module**: Enables RS485 serial communication
- **Baud Rate**: 9600 (configurable)
- **Measurement Range**: N: 0-500 mg/kg, P: 0-200 mg/kg, K: 0-300 mg/kg

## 💻 Software Architecture

### Arduino Code (circuitdiag.html)
```cpp
#include <ModbusMaster.h>
#include <SoftwareSerial.h>

// RS485 control pin
#define MAX485_DE_RE 2

// Software Serial pins
#define RX_PIN 10
#define TX_PIN 11

// Reads NPK values from sensor registers:
// Nitrogen: Register 0x001E
// Phosphorus: Register 0x001F
// Potassium: Register 0x0020
```

### Web Interfaces

The system includes 5 interconnected HTML pages:

#### 1. **index.html** - Main Dashboard
The primary interface featuring:
- **Manual Input Mode**: Enter soil readings manually
- **Auto Simulation Mode**: Test with simulated sensor data
- **Demo Scenarios**: Pre-configured flood situation examples
- **Testing History**: Track all measurements with timestamps
- **Visual Analytics**: Chart nitrogen levels over time
- **Navigation Buttons**: Quick access to circuit diagram and flowchart

#### 2. **circuitdiag.html** - Arduino Code Reference
- Complete Arduino sketch for NPK sensor interfacing
- RS485 Modbus RTU implementation
- Hardware pin configuration
- Serial communication setup

#### 3. **flowchart.html** - System Workflow
- Visual flowchart of development process
- Decision trees for testing and improvements
- Mobile responsiveness verification steps

#### 4. Navigation Panel
White panel with 2 clickable buttons:
- **Arduino Code & Circuit** → Links to circuitdiag.html
- **System Flowchart** → Links to flowchart.html

## 📊 Feature Breakdown

### Manual Input Mode
- Input field for location/field name
- Separate inputs for N, P, K values
- Real-time display with color-coded status
- Level indicator bar (capped at 100% for values exceeding max)
- Nutrient recommendations based on levels
- Save readings to history

### Auto Simulation Mode
- Generates realistic random NPK values
- Simulates actual sensor behavior
- 2-second processing time (like real sensor)
- Save simulated readings to database
- Test without physical hardware

### Demo Scenarios
Four pre-configured flood situations:

1. **Heavy Flood (Severe Damage)**
   - N: 85 mg/kg, P: 22, K: 65
   - Status: Urgent Help Needed
   - Cost: ₹3,000-4,000 per acre

2. **Medium Flood (Moderate Damage)**
   - N: 165 mg/kg, P: 45, K: 125
   - Status: Needs Fertilizer
   - Cost: ₹2,000-2,500 per acre

3. **Light Flood (Minor Damage)**
   - N: 235 mg/kg, P: 68, K: 175
   - Status: Minor Problem
   - Cost: ₹1,000-1,500 per acre

4. **After Recovery (Good Soil)**
   - N: 310 mg/kg, P: 95, K: 210
   - Status: Good Condition
   - No urgent fertilizers needed

### Testing History & Analytics
- Timestamped record of all tests
- Location tracking
- Status color-coding (Low/Moderate/Good/High)
- Delete individual records
- Clear all history option
- Visual bar chart of nitrogen trends

## 🎯 Nutrient Level Interpretation

### Nitrogen (N) Recommendations:

| Level | Status | Action | Cost |
|-------|--------|--------|------|
| < 150 mg/kg | LOW | Urgent: Urea 50-60 kg/acre, DAP 30 kg/acre | ₹2,500-3,000 |
| 150-250 mg/kg | MODERATE | Urea 30-40 kg/acre + compost | ₹1,500-2,000 |
| 250-350 mg/kg | GOOD | Maintain current practices | No action needed |
| > 350 mg/kg | HIGH | Stop nitrogen fertilizers, risk of water pollution | Reduce by 50% |

## 📱 User Interface Features

### Responsive Design
- **Desktop**: Full 2-column layout
- **Tablet**: Single column, optimized spacing
- **Mobile**: Touch-friendly buttons, readable text, hidden columns

### Visual Elements
- Color-coded status indicators (Red/Orange/Yellow/Green)
- Gradient backgrounds for emphasis
- Smooth animations and transitions
- Interactive hover effects
- Real-time value updates

### Data Management
- LocalStorage support for persistent data
- Export-ready history table
- Timestamped records with IST (India Standard Time)
- Sortable data display

## 🚀 How to Use

### 1. Main Dashboard (index.html)
```
Open in browser → Select testing mode → Enter/simulate data → View recommendations → Save to history
```

### 2. Manual Testing
- Fill in field location
- Enter N, P, K values (0-500, 0-200, 0-300 respectively)
- Click "Update Readings" for live preview
- Click "Save to History" to record
- View recommendations based on values

### 3. Simulation Mode
- Click "Auto Simulation Mode"
- Click "Start Simulation"
- System generates realistic NPK values
- Click "Save This Reading" to record

### 4. Demo Scenarios
- Click "Demo Scenarios"
- Select one of 4 pre-configured situations
- View recommended actions
- Save scenario results to history

## 💡 Benefits for Farmers

1. **Speed**: Results in 30 seconds vs. 3-7 days for lab testing
2. **Cost**: One-time device investment vs. ₹2,000+ per test
3. **Accessibility**: Works offline, no internet required for testing
4. **Accuracy**: Direct sensor measurement of actual soil
5. **Actionable**: Immediate fertilizer recommendations with costs
6. **Scalability**: Test unlimited fields with one device
7. **Data Tracking**: Historical records for soil health monitoring

## 📈 Cost Comparison

| Method | Cost Per Test | Turnaround | Accessibility |
|--------|---------------|-----------|---------------|
| Lab Testing | ₹2,000-3,000 | 3-7 days | Limited |
| This System | One-time device cost | 30 seconds | Anytime, anywhere |

## 🔌 Hardware Connection Diagram

```
NPK Sensor
    ├─ VCC → Arduino 5V
    ├─ GND → Arduino GND
    ├─ RX → MAX485 DI (Pin R0)
    └─ TX → MAX485 RO (Pin R1)

MAX485 Module
    ├─ DI → Software Serial TX (Pin 11)
    ├─ RO → Software Serial RX (Pin 10)
    ├─ DE/RE → GPIO Pin 2
    ├─ VCC → Arduino 5V
    ├─ GND → Arduino GND
    └─ A/B → NPK Sensor A/B

Arduino
    ├─ Pin 10 → RX (Software Serial)
    ├─ Pin 11 → TX (Software Serial)
    ├─ Pin 2 → DE/RE Control
    ├─ 5V & GND → Power
    └─ USB → Computer/Web Interface
```

## 📋 File Structure

```
NitroWave-main/
├── index.html          (Main dashboard - testing interface)
├── circuitdiag.html    (Arduino code & circuit reference)
├── flowchart.html      (System development flowchart)
├── README.md           (This file)
└── LICENSE
```

## 🛠️ Technical Specifications

- **Sensor Protocol**: Modbus RTU over RS485
- **Communication**: Serial (9600 baud)
- **Response Time**: ~30 seconds per complete test
- **Measurement Accuracy**: ±5% (typical)
- **Temperature Range**: 0-50°C (operational)
- **Web Technology**: HTML5, CSS3, Vanilla JavaScript
- **Data Storage**: Browser LocalStorage
- **Compatibility**: All modern browsers (Chrome, Firefox, Safari, Edge)

## 📝 Installation & Setup

### Hardware Setup
1. Connect NPK sensor to MAX485 module (follow connection diagram)
2. Connect MAX485 to Arduino as shown
3. Upload Arduino sketch (from circuitdiag.html) to Arduino board
4. Connect Arduino to computer via USB

### Software Setup
1. Save all HTML files in same directory
2. Open `index.html` in web browser
3. System ready for testing

## 🎓 Educational Value

This project demonstrates:
- IoT sensor integration
- Serial communication protocols (RS485/Modbus)
- Embedded systems programming (Arduino)
- Web application development
- Data visualization
- Real-world problem solving
- Agricultural technology

## 🌱 Environmental Impact

- Reduces fertilizer waste through precision application
- Prevents water pollution from excess nitrogen
- Enables sustainable agriculture recovery
- Helps restore flood-affected farmland faster
- Reduces chemical runoff into water bodies

## 👨‍🌾 Target Users

- **Small & Medium Farmers**: Affected by floods
- **Agricultural Consultants**: Need quick soil analysis
- **Agricultural Colleges**: Educational tool for students
- **Government Agencies**: Flood recovery programs
- **NGOs**: Rural development projects

## 📞 Support & Documentation

- **Arduino Code**: See circuitdiag.html for complete implementation
- **System Flow**: See flowchart.html for workflow visualization
- **User Manual**: Built-in help in web interface (recommendations section)

## 📄 License

See LICENSE file for details.

## 🙏 Acknowledgments

This system was designed to address the critical need for quick, affordable soil testing solutions for farmers recovering from natural disasters like floods. It combines affordable hardware with intuitive software to democratize agricultural soil testing.

---

**Version**: 1.0  
**Last Updated**: December 2025  
**Status**: Fully Functional
