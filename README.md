# LiteHouse

**LiteHouse** is a smart home lighting control system designed as a graduation project in 2025 at **Gymnázium Šumperk**. The project enables real-time control of WiFi-enabled devices such as **WLED**, **Tasmota**, and **OpenBeken** using a modern web interface and MQTT communication protocol.

---

## 🧠 Project Description

The system is split into a frontend and backend that communicate over REST API and MQTT. Users can:

- Control individual devices
- Adjust color and brightness
- Toggle power
- Create and save scenes
- Apply scenes dynamically
- Use the system on mobile and desktop with responsive UI

This project demonstrates practical use of MQTT protocols, Flask backend, and dynamic web control for embedded systems.

---

## ✨ Features

- Real-time control of WLED, Tasmota, and OpenBeken devices
- Per-device control for power, RGB color, and brightness
- Scene saving and applying (with persistent JSON storage)
- Mobile-friendly interface with touch and haptic support
- Automatic recognition of device types from settings
- Modular architecture for easy device extension
- Full control via local network without cloud dependency

---

## 🛠️ Technologies Used

- **Python 3**
- **Flask** (REST API backend)
- **paho-mqtt** (MQTT communication)
- **HTML/CSS/JS** frontend
- **iro.js** (color picker)
- **Tasmota / WLED / OpenBeken** devices
- **Raspberry Pi** (recommended for deployment)

---

## 🗂️ File Structure

```
LiteHouse/
│
├── backend/
│   ├── app.py               # Flask API server
│   ├── main.py              # Scene control and MQTT logic
│   ├── mqtt_handler.py      # Device-specific MQTT command mapping
│   ├── settings.json        # Configuration of devices and MQTT broker
│   ├── scenes.json          # Scene storage (power, color, brightness)
│   └── requirements.txt         # Python dependencies
│
├── frontend/
│   ├── index.html           # Main UI
│   ├── script.js            # UI logic, API calls
│   ├── styles.css           # UI styles
│   └── iro.min.js           # Color picker library
└──
```

---

## ⚙️ Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/fsolardev/litehouse.git
cd litehouse/backend
```

### 2. Set Up Virtual Environment (Optional but recommended)

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### 3. Configure Devices and MQTT Broker

Edit the `settings.json` file:

```json
{
  "mqtt": {
    "broker": "192.168.x.x",
    "port": 1883,
    "username": "your_mqtt_user",
    "password": "your_mqtt_password"
  },
  "devices": [
    {
      "id": "wled_device",
      "name": "WLED Desk",
      "type": "WLED",
      "topic": "wled_device"
    }
  ]
}
```
ChatGPT will always help you with the configuration of your devices ;)

### 4. Run the Backend Server

```bash
python app.py
```

It will run on: `http://<raspberry-pi-ip>:5000`

### 5. Open the Web Interface

In your browser open the url `frontend/` folder and open `index.html` in a browser (Chrome recommended).  
For mobile, deploy via `nginx` or similar local HTTP server if needed.

---

## 🚦 Scene Control Logic

- Scene data (power, color, brightness) is saved in `scenes.json`
- Scenes can be applied without reloading the page
- When applying a scene:
  - If device is **OFF**, only a power command is sent
  - If device is **ON**, all properties are applied

---

## ⚠️ Limitations

- Only supports RGB lights with MQTT-based protocols
- Currently designed for local network use only
- No login/authentication layer
- Layout for only 3 devices at once

---

## 📚 Educational Value

This project demonstrates integration of:

- IoT principles and MQTT
- Frontend-to-backend communication via REST
- JSON-based persistence
- Hardware integration with WLED / Tasmota
- Modular software architecture in Python

---

## 🏫 Author & Acknowledgements

Created by a student (me) of **Gymnázium Šumperk** in 2025 as a **maturitní projekt** (graduation project).  
Thanks to open-source contributors of WLED, Tasmota, and others for inspiration and technical references.
