# Starbie — Half Life (Week 1)

> **A motion-controlled digital desk pet powered by the Seeed XIAO ESP32-C3.**  
> Built by **Tejas** ([@tejuas98](https://github.com/tejuas98)) for **[Hack Club Half Life](https://halflife.hackclub.com/)** (Week 1: PCB Design).

![Starbie render](GuidePics/Starbie%20Render.png)

---

## 🌟 What is Starbie?

Starbie is a desktop digital pet with motion interactivity. Instead of only pressing buttons, you physically tilt and shake the board to play with your pet, navigate the 4-way radial menu, and monitor environmental conditions!

### Hardware Architecture:
- **Microcontroller:** Seeed Studio XIAO ESP32-C3 (RISC-V, USB-C, 2.4GHz Wi-Fi/BLE)
- **Display:** 0.96" 128x64 Monochrome OLED Display (I2C, Address `0x3C`)
- **Motion Sensor:** MPU6050 6-Axis Accelerometer & Gyroscope (I2C, Address `0x68`)
- **Environment Sensor:** DHT11 Temperature & Relative Humidity Sensor (GPIO 3)
- **Input Controls:** 2x Tactile Pushbuttons (GPIO 4 and GPIO 5)
- **Power:** 5V / 3.3V via USB-C on the XIAO module

---

## 📂 Repository Structure

```text
├── BOM.csv                      # Complete Bill of Materials with supplier links (~$15 total)
├── Firmware/
│   ├── Starbie/
│   │   └── Starbie.ino         # Complete Arduino firmware (all-in-one beginner friendly)
│   ├── simulator.html          # In-browser 3D interactive hardware simulator
│   └── README.md
├── PCB/
│   ├── Starbie.kicad_sch       # KiCad schematic
│   ├── Starbie.kicad_pcb       # KiCad PCB board layout
│   └── production/
│       └── Starbie Gerbers V1.0.zip  # Ready-to-order fabrication Gerbers for JLCPCB
├── GuidePics/                  # Screenshots and render assets
└── Week 1 Guide.md             # Complete step-by-step PCB and firmware guide
```

---

## 🛠️ Bill of Materials (BOM)

| Item | Qty | Approx Cost | Notes |
| :--- | :---: | :---: | :--- |
| **Seeed XIAO ESP32-C3** | 1 | $5.00 | Microcontroller brain |
| **0.96" I2C OLED Display (128x64)** | 1 | $2.50 | SSD1306 driver |
| **MPU6050 Accelerometer/Gyro** | 1 | $2.29 | Detects tilt, shake, and movement |
| **DHT11 Sensor** | 1 | $3.33 | Measures temperature and humidity |
| **Tactile Buttons / MX Switches** | 2 | $0.36 | Menu navigation & stats toggling |
| **10kΩ Resistor** | 1 | $0.10 | Pull-up resistor for DHT11 data line |
| **Total Cost** | | **~$13.58** | *Well within the Half Life $30 Tier 1 budget!* |

---

## 🎮 How Starbie Works

- **Button 1 (Menu):** Press to bring up the 4-way radial menu. Tilt the board to guide the cursor into a sector:
  - **TOP:** `NAP` (Starbie sleeps and emits Zs)
  - **RIGHT:** `PLAY` (Starbie runs fast laps)
  - **BOTTOM:** `FEED` (Fullness restore & happy jump)
  - **LEFT:** `PET` (Emits floating heart icons)
  - Press Button 1 again to confirm the action!
- **Button 2 (Stats Overlay):** Press to toggle the live HUD showing Joy, Energy, Fullness, and live room Temperature & Humidity readings.
- **Physical Shake:** Give Starbie a friendly shake to boost Joy!

---

## 💻 Web Simulator

Before physical assembly, you can test the entire firmware logic directly in your browser. Open [`Firmware/simulator.html`](Firmware/simulator.html) to interact with the 3D board, test tilt physics, and simulate button presses.

---

## 🚀 Building & Flashing

Follow the complete step-by-step guide in [Week 1 Guide.md](Week%201%20Guide.md) for:
1. Installing KiCad and viewing/editing the schematic & board.
2. Generating and inspecting Gerber fabrication outputs.
3. Setting up Arduino IDE with the ESP32 board package and Adafruit libraries.
4. Customizing the 32x32 sprite pixel art and flashing to the board.
