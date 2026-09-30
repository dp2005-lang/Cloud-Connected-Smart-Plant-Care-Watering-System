# Cloud-Connected-Smart-Plant-Care-Watering-System
🌿 **Smart Plant Care &amp; Watering System** is a cloud-connected IoT dashboard that monitors soil moisture, temperature, humidity, and light while automating plant watering. Built with Python, Flask, SQLite, HTML, CSS, JavaScript, and Chart.js, it includes alerts, analytics, virtual sensors, watering history, and real-time monitoring.
# 🌿 Smart Plant Care & Watering System

A **cloud-connected smart plant monitoring and automated watering system** built with Python, Flask, SQLite, HTML, CSS, JavaScript, and Chart.js.

The project simulates an IoT-based plant-care environment where virtual sensors continuously collect plant data, a Flask REST API processes the information, and an interactive web dashboard provides real-time monitoring, automation, alerts, analytics, and watering controls.

---

## 📌 Overview

The **Smart Plant Care & Watering System** is designed to demonstrate how IoT concepts, backend APIs, databases, automation logic, and web dashboards can work together in a smart-agriculture application.

The system uses **virtual IoT sensors**, so no physical hardware is required. Simulated devices continuously generate readings such as:

* 🌱 Soil moisture
* 🌡️ Temperature
* 💧 Humidity
* ☀️ Light level
* 🪣 Water tank level
* ⚙️ Pump status

The automation engine evaluates sensor readings and determines when watering should occur based on configurable plant requirements and safety conditions.

---

## ✨ Key Features

### 🌱 Real-Time Plant Monitoring

Monitor multiple virtual plants from a centralized dashboard.

Each plant provides information about:

* Current soil moisture
* Temperature
* Humidity
* Light level
* Plant type
* Location
* Device status
* Moisture threshold
* Watering status

### 💧 Automated Watering

The automation engine can automatically activate watering when soil moisture falls below the configured threshold.

Safety controls include:

* Moisture threshold
* Water tank minimum level
* Pump cooldown period
* Maximum automatic watering duration
* Target moisture margin
* Pump flow-rate calculation

### 🖐️ Manual Watering

Users can manually trigger watering directly from the dashboard.

The system records watering events and provides information about the watering duration and moisture before and after watering.

### 🚨 Smart Alerts

The application generates alerts for important conditions such as:

* Low soil moisture
* High temperature
* Low water tank level
* Device/offline conditions
* Other system events

Alerts can be acknowledged through the dashboard.

### 📡 Virtual IoT Devices

The project includes a virtual sensor simulator that behaves like connected IoT hardware.

The simulator continuously sends sensor data to the Flask REST API, allowing the complete system to be tested without physical sensors.

### 📊 Interactive Dashboard

The web dashboard provides:

* Plant fleet overview
* Individual plant monitoring
* Soil moisture charts
* Water usage visualization
* Temperature and humidity charts
* Light-level monitoring
* Plant analytics
* Recent alerts
* Watering history
* Live event logs
* Device management
* Manual controls
* Virtual plant registration

### 🗄️ SQLite Database

The system uses SQLite to store application data including:

* Users
* Devices
* Sensor readings
* Watering events
* Alerts

### 🔐 API Authentication

The REST API uses generated API credentials and a demo user token to control access to protected endpoints.

### ☁️ Google Colab Support

The complete project is designed to run from **a single Google Colab cell**.

Running the cell:

1. Starts the Flask backend.
2. Initializes the SQLite database.
3. Starts virtual IoT sensor threads.
4. Starts the monitoring system.
5. Runs API self-tests.
6. Launches the interactive dashboard.
7. Provides an accessible dashboard window through the Colab runtime.

---

# 🏗️ System Architecture

```text
                ┌─────────────────────────┐
                │   Virtual IoT Sensors   │
                │                         │
                │ Moisture • Temp • Humidity
                │ Light • Tank • Pump     │
                └────────────┬────────────┘
                             │
                             │ HTTP / JSON
                             ▼
                ┌─────────────────────────┐
                │      Flask REST API     │
                │                         │
                │ Authentication          │
                │ Validation              │
                │ Device Management       │
                │ Sensor Data             │
                └────────────┬────────────┘
                             │
                ┌────────────┴────────────┐
                ▼                         ▼
       ┌─────────────────┐       ┌─────────────────┐
       │  SQLite Database│       │ Automation Engine│
       │                 │       │                 │
       │ Users           │       │ Moisture Check  │
       │ Devices         │       │ Watering Logic  │
       │ Sensor Readings │       │ Safety Rules    │
       │ Watering Events │       │ Pump Control    │
       │ Alerts          │       └─────────────────┘
       └─────────────────┘
                │
                ▼
       ┌─────────────────────────┐
       │    Web Dashboard        │
       │                         │
       │ Charts • Alerts         │
       │ Analytics • Controls    │
       │ Plant Monitoring        │
       └─────────────────────────┘
```

---

# 🛠️ Technology Stack

| Technology       | Purpose                                      |
| ---------------- | -------------------------------------------- |
| **Python**       | Backend, simulation and automation           |
| **Flask**        | REST API and web server                      |
| **SQLite**       | Local database                               |
| **HTML5**        | Dashboard structure                          |
| **CSS3**         | Responsive dashboard styling                 |
| **JavaScript**   | Dashboard interactions and API communication |
| **Chart.js**     | Data visualization                           |
| **Requests**     | HTTP communication                           |
| **Google Colab** | Development and execution environment        |

---

# 🌿 Default Virtual Plants

The system initializes a sample fleet containing:

| Device      | Plant        | Type      | Location       |
| ----------- | ------------ | --------- | -------------- |
| `PLANT-001` | Tomato Plant | TOMATO    | Greenhouse A   |
| `PLANT-002` | Aloe Vera    | SUCCULENT | Living Room    |
| `PLANT-003` | Basil        | HERB      | Kitchen Window |

The application also supports registering additional virtual plants through the dashboard.

---

# 🌡️ Plant Profiles

The application includes configurable moisture profiles for:

* **SUCCULENT** — 20%
* **TOMATO** — 40%
* **HERB** — 35%
* **INDOOR** — 30%

These values are used by the watering automation system to determine when a plant requires additional water.

---

# ⚙️ Automation & Safety

The watering system incorporates multiple safeguards before activating the virtual pump.

### Moisture Threshold

Watering can be triggered when the measured soil moisture drops below the configured threshold.

### Tank Protection

The system prevents watering when the tank level falls below the configured minimum.

### Pump Cooldown

A cooldown period prevents repeated watering actions from occurring too frequently.

### Maximum Pump Duration

Automatic watering is limited by a maximum pump runtime.

### Offline Protection

The monitoring system detects devices that stop sending sensor data and can generate an offline alert.

### Temperature Monitoring

High-temperature conditions can also trigger system alerts.

---

# 📡 REST API

The backend exposes REST endpoints for device management, sensor data, watering, alerts, analytics, and simulation.

### Sensor Data

```text
POST /api/sensors/data
```

Receives sensor readings from virtual devices.

### Devices

```text
GET  /api/devices
GET  /api/devices/<did>
```

Retrieves device information and current status.

### Sensor History

```text
GET /api/devices/<did>/latest
GET /api/devices/<did>/history
```

Retrieves the latest reading and historical sensor data.

### Configuration

```text
GET /api/devices/<did>/threshold
PUT /api/devices/<did>/threshold

PUT /api/devices/<did>/settings
```

Allows device watering settings and thresholds to be managed.

### Watering

```text
POST /api/devices/<did>/water
POST /api/devices/<did>/refill
GET  /api/devices/<did>/watering-history
```

Provides manual watering, tank refill, and watering history functionality.

### Analytics

```text
GET /api/devices/<did>/analytics
```

Provides plant-level analytics.

### Alerts

```text
GET  /api/alerts
PUT  /api/alerts/<aid>/acknowledge
```

Retrieves and manages system alerts.

### Logs

```text
GET /api/logs
```

Provides application event logs.

### Simulation

```text
POST /api/sim/<did>/<action>
```

Supports virtual plant simulation actions such as environmental changes and device-state simulation.

---

# 🚀 Running in Google Colab

The project is packaged as a **single-cell Google Colab application**.

### Step 1 — Open the Notebook

Open:

`Smart_Plant_Care_Dashboard_Colab.ipynb`

### Step 2 — Run the Cell

Execute the single Python cell.

The program automatically:

```text
Install/verify dependencies
        ↓
Initialize SQLite
        ↓
Create demo user
        ↓
Create virtual plant fleet
        ↓
Start Flask API
        ↓
Start virtual IoT sensors
        ↓
Start monitoring thread
        ↓
Run API self-tests
        ↓
Launch dashboard
```

### Step 3 — Open the Dashboard

The notebook provides an embedded dashboard preview and a separate dashboard window through the Colab runtime.

---

# 🖥️ Dashboard

The dashboard provides a centralized control center for the entire system.

### Dashboard Sections

**Plant Fleet**

Displays all connected virtual plants and their current health.

**System Overview**

Shows:

* Total plants
* Water tank level
* Pump status
* Active alerts

**Quick Actions**

Provides controls for:

* Registering a new plant
* Manual watering
* Simulating dry soil
* Simulating heat conditions

**Analytics**

Visualizes sensor and watering data through interactive charts.

**Alerts**

Displays current system warnings and allows alerts to be acknowledged.

**Watering History**

Provides a record of previous automatic and manual watering events.

**Live Event Log**

Displays recent system activity.

---

# 🧪 Built-In Testing

The program performs quick API self-tests after startup.

The tests cover areas including:

* API authentication
* Request validation
* Unknown device handling
* User token authentication
* Device count
* Invalid threshold handling

This helps verify that the backend is functioning correctly before using the dashboard.

---

# 📂 Project Structure

The primary one-cell project can be distributed as:

```text
Smart_Plant_Care_Dashboard_Colab/
│
├── Smart_Plant_Care_Dashboard_Colab.ipynb
├── Smart_Plant_Care_Dashboard_Colab.py
└── README.md
```

The application database is created automatically at runtime.

---

# 🔄 Application Workflow

```text
Virtual Sensor
      ↓
Sensor Reading
      ↓
Flask REST API
      ↓
SQLite Database
      ↓
Automation Engine
      ↓
Watering / Alert Decision
      ↓
Database Update
      ↓
Live Dashboard
      ↓
Charts + Alerts + Analytics
```

---

# 🎯 Project Objectives

The project demonstrates practical implementation of:

* IoT system simulation
* REST API development
* Sensor data processing
* Automated decision-making
* Database management
* Real-time monitoring
* Web dashboard development
* Alert management
* Device health monitoring
* Google Colab deployment
* Full-stack Python application development

---

# 🔮 Future Scope

Potential future improvements include:

* 🔌 Integration with real soil-moisture sensors
* 💧 Physical water pumps and relay modules
* 📡 ESP32/ESP8266 integration
* ☁️ Cloud database integration
* 🔐 Production-grade authentication
* 📱 Mobile application
* 🔔 Push notifications
* 🌦️ Weather API integration
* 🤖 Machine-learning-based watering prediction
* 📈 Advanced plant-health analytics
* 👥 Multi-user management
* 🌐 Cloud deployment
* 📊 Historical reporting and exports

---

# ⚠️ Important Note

This project uses **virtual IoT sensors and a simulated watering system**. It is intended for demonstration, learning, development, and testing purposes and does not require physical plant-care hardware.

---

# 👨‍💻 Project

**Smart Plant Care & Watering System**

A practical demonstration of how IoT simulation, automation, backend services, databases, and interactive dashboards can be combined into a complete smart-plant monitoring solution.

---



---

## 📜 License

Add your preferred license here, such as **MIT License**, before publishing the repository publicly.

---

⭐ If you found this project useful or interesting, consider giving the repository a star!
