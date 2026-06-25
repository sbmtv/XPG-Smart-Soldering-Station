# XPG-Smart-Soldering-Station
XPG Smart C470/C245/C210/T12 Soldering Station
![图片描述](https://github.com/sbmtv/XPG-Smart-Soldering-Station/blob/main/img/%E4%B8%BB%E6%9D%BF%E9%80%8F%E6%98%8E%E5%9B%BE.png)
![图片描述](https://github.com/sbmtv/XPG-Smart-Soldering-Station/blob/main/%E7%99%BD.png)
![图片描述](https://github.com/sbmtv/XPG-Smart-Soldering-Station/blob/main/%E6%B7%B1%E7%81%B0.png)
![图片描述](https://github.com/sbmtv/XPG-Smart-Soldering-Station/blob/main/%E8%93%9D.png)
![图片描述](https://github.com/sbmtv/XPG-Smart-Soldering-Station/blob/main/%E9%BB%91.png)
![图片描述](https://github.com/sbmtv/XPG-Smart-Soldering-Station/blob/main/%E7%82%AB%E5%BD%A9.png)
# XPG Smart Soldering Station User Manual

---

## Table of Contents

1. [Product Overview](#1-product-overview)
2. [Getting Started](#2-getting-started)
3. [Main Screen Operation](#3-main-screen-operation)
4. [Settings Screen](#4-settings-screen)
5. [System Settings](#5-system-settings)
6. [Other Settings](#6-other-settings)
7. [WiFi Settings](#7-wifi-settings)
8. [Temperature Calibration](#8-temperature-calibration)
9. [Sleep & Screensaver](#9-sleep--screensaver)
10. [Safety Protection](#10-safety-protection)
11. [Remote Control (Web API)](#11-remote-control-web-api)
12. [Firmware Upgrade (Factory Mode)](#12-firmware-upgrade-factory-mode)
13. [Factory Reset](#13-factory-reset)
14. [Troubleshooting](#14-troubleshooting)

---

## 1. Product Overview

The XPG Smart Soldering Station is a high-performance intelligent soldering tool based on the ESP32-S3, featuring a 3.5-inch color touchscreen, support for multiple heater cartridge models, PID precision temperature control, multiple safety protections, and WiFi remote control.

**Supported Heater Cartridge Models**: T12, C245, C210, C470 (auto-detection supported)

**Key Features**:
- PID intelligent temperature control — fast heating, stable holding
- 3.5-inch color touchscreen with 4 color themes
- Bilingual interface (Chinese / English)
- WiFi connectivity for remote monitoring and control via phone/PC
- Multiple safety protections (overcurrent, over-temperature, under-voltage, tip-change protection)
- Smart sleep and auto-shutdown
- Buzzer audio feedback

---

## 2. Getting Started

### 2.1 Power On

1. Connect the power supply (supports 12–48V DC; choose the appropriate voltage for your heater cartridge)
2. Install the heater cartridge (the device auto-detects the model)
3. The startup screen appears after power-on

### 2.2 First-Time Setup

On first boot, the following initial setup is required:

1. **Touchscreen Calibration**: Tap the crosshairs that appear at the four corners of the screen in sequence, then tap the center to confirm
2. **Language Selection**: A language dialog pops up — choose "中文" (Chinese) or "English"

### 2.3 Basic Operation Flow

1. Tap the **Heat** button on the main screen to turn on heating
2. Set the target temperature using the slider or +/- buttons
3. Wait for the temperature to be reached — the buzzer will sound
4. Begin soldering
5. When finished, tap the **Heat** button to turn off, or place the iron on the stand to enter sleep mode automatically

---

## 3. Main Screen Operation

The main screen is the most frequently used interface, providing temperature display, heating control, and parameter adjustment.

### 3.1 Heating On/Off

- Tap the **Heat button** at the bottom left to toggle heating on/off
- The button highlights when heating is on, and returns to normal style when off
- When heating is on, the PID controller automatically heats the tip to the set temperature

### 3.2 Temperature Setting

Three ways to set the target temperature (range 0–500°C):

| Method | Operation | Description |
|--------|-----------|-------------|
| Slider | Drag the temperature slider on the right panel | Continuous adjustment, real-time update |
| +/- Buttons | Tap/long-press the [-] [+] buttons | Short press: ±10°C per tap; long press: continuous adjustment |
| Presets | Tap P1/P2/P3/P4 buttons | One-touch switch to preset temperature |

### 3.3 Real-Time Information Display

The main screen shows the following real-time information:

- **Current Temperature**: Large font display with PWM arc indicator
- **Set Temperature**: Target temperature value
- **Tip Type**: Currently detected heater cartridge model
- **Cold Junction Temperature**: Ambient temperature at the handle
- **Supply Voltage**: Current input voltage
- **Operating Current**: Current heating current
- **Heating Power**: Current output power
- **Operating Status**: Current state (Normal/Sleep/Standby/Protection, etc.)

### 3.4 Temperature Reached Notification

- When the heating reaches the target temperature, the buzzer plays a notification sound
- If the temperature drops more than 10°C and then reaches the target again, the notification will sound again

---

## 4. Settings Screen

Tap the **Settings** button at the bottom of the main screen to enter the settings screen.

### 4.1 Heater Cartridge Type

- Tap the tip type button at the top left to cycle through: **T12 → C245 → C210 → C470 → Auto Detect**
- When "Auto Detect" is selected, the device automatically identifies the cartridge model via the ID pin
- Switching the tip type also switches the corresponding calibration data and PID parameters

### 4.2 Sleep Temperature

- Tap/long-press [-] [+] buttons to adjust the sleep hold temperature
- Range: 0–300°C, step 10°C
- Default: 200°C

### 4.3 Sleep Timeout

- Tap/long-press [-] [+] buttons to adjust the idle time before entering sleep
- Range: 1–30 minutes
- Default: 3 minutes

### 4.4 Preset Temperatures

- 4 preset temperature groups (P1–P4), each with [-] [+] buttons
- Each tap: ±10°C, range 0–500°C
- Defaults: 300°C / 350°C / 400°C / 420°C

### 4.5 Navigation Buttons

| Button | Function |
|--------|----------|
| Calibrate | Enter temperature calibration screen |
| System | Enter system settings screen |
| Other | Enter other settings screen |
| WiFi | Enter WiFi settings screen |
| Save | Save all settings and return to main screen |
| Back | Return to main screen without saving |

---

## 5. System Settings

### 5.1 PID Parameter Adjustment

PID parameters affect the response speed and stability of temperature control. Normally no adjustment is needed.

| Parameter | Range | Default | Description |
|-----------|-------|---------|-------------|
| Kp (Proportional) | 1.0–50.0 | 20.0 | Response speed — higher values give faster response but may cause oscillation |
| Ki (Integral) | 1.0–50.0 | 20.0 | Steady-state error elimination — higher values eliminate error faster but may cause overshoot |
| Kd (Derivative) | 1.0–50.0 | 20.0 | Overshoot suppression — higher values suppress overshoot more but are more sensitive to noise |

> **Tip**: If temperature holding is unstable or overshoot is severe, try reducing Ki and slightly increasing Kd. For professional tuning, use the step test feature via the Web API.

### 5.2 Protection Thresholds

| Protection | Range | Default | Description |
|------------|-------|---------|-------------|
| Under-voltage | 6.0–30.0V | 6.0V | Heating turns off when supply voltage drops below this value |
| Overcurrent | 0–20.0A | 10.0A | Heating turns off when peak current exceeds this value; 0 = disabled |

### 5.3 Other Options

| Option | Operation | Description |
|--------|-----------|-------------|
| Language | Tap the "Language" button | Cycle: 中文 / English |
| Sleep Mode | Tap the "Sleep Mode" button | Cycle: Stand Sleep / Vibration Sleep |
| Boot Logo | Toggle switch | Enable/disable boot logo display |
| Page Animation | Toggle switch | Enable/disable page transition animations |

### 5.4 Factory Reset

- Drag the "Factory Reset" slider to 100% to trigger
- Releasing before 100% causes the slider to spring back (prevents accidental operation)
- Once triggered, all settings are restored to defaults and the device restarts automatically

---

## 6. Other Settings

### 6.1 Background Color Theme

- Tap the color button at the top right to cycle through 4 themes:

| Theme | Description |
|-------|-------------|
| White | Bright and clean, suitable for well-lit environments |
| Blue | Dark blue background, classic style |
| Black | Pure black background, darkroom friendly |
| Dark Gray | Dark gray background, soft on the eyes |

### 6.2 Backlight Brightness

- Drag the slider to adjust screen brightness
- Range: 1 (dimmest) – 10 (brightest)

### 6.3 Buzzer Volume

- Drag the slider to adjust buzzer volume
- Range: 0 (silent) – 10 (maximum)

### 6.4 Auto-Shutdown Time

- Drag the slider to set the time after sleep before auto-shutdown
- Range: 0–120 minutes, 0 = never shut down
- Default: 30 minutes

### 6.5 Screensaver Mode

| Mode | Description |
|------|-------------|
| Show Clock | Black background with large time and date display, backlight at minimum |
| Screen Off | Pure black screen with backlight off, lowest power consumption |

### 6.6 Power Output Mode

| Mode | Description |
|------|-------------|
| Auto | Automatically calculates maximum power based on tip type and supply voltage |
| Manual | User-defined PWM duty cycle (1–97%) |
| Max | Fixed 97% duty cycle, no power limit |

**Auto Mode Power Reference Table**:

| Cartridge | Low Voltage | High Voltage |
|-----------|-------------|--------------|
| T12 | 97% (all voltages) | 97% |
| C245 | <19V → 97% | 24V → 50% |
| C210 | <13V → 60% | 24V → 25% |
| C470 | <40V → 97% | 48V → 50% |

> **Note**: Power is automatically reduced at higher voltages to prevent cartridge overload. To use full power, select "Max" mode, but ensure your power supply and cartridge can handle it.

---

## 7. WiFi Settings

### 7.1 Scan & Connect

1. Tap the **Scan** button to search for nearby WiFi hotspots
2. The list shows each hotspot's name, signal strength, and encryption status
3. Tap the hotspot you want to connect to:
   - **Open network**: Connects directly
   - **Secured network**: A password input dialog with virtual keyboard appears; enter the password and connect

### 7.2 Forget Network

- Tap the **Forget** button to disconnect from the current WiFi and clear saved credentials
- You will need to re-enter the password next time

### 7.3 Connection Status

The screen displays real-time WiFi connection status:
- Not Connected / Connecting / Connected / Connection Failed
- IP address is shown when connected

> **Tip**: Once WiFi is connected, you can access the device's IP address from a phone or computer browser for remote control.

---

## 8. Temperature Calibration

Temperature calibration corrects the heater cartridge's temperature reading deviation, ensuring the displayed temperature matches the actual temperature.

> **Note**: Calibration requires an external reference thermometer. Incorrect calibration data can cause abnormal temperature control — please operate with care.

### 8.1 Calibration Steps

1. Enter the Settings screen and tap the **Calibrate** button
2. Prepare a reliable external thermometer
3. Select the temperature point to calibrate (100/200/300/400/500/600°C)
4. Heat the iron to the corresponding temperature and wait for it to stabilize
5. Tap the temperature point button to read the current ADC value
6. Use the [-] [+] buttons to fine-tune the ADC value until the displayed temperature matches the external thermometer reading
7. Repeat steps 3–6 for all calibration points needed
8. Tap **Save** to save the calibration data

### 8.2 Voltage Calibration

- Use the [-] [+] buttons to adjust the voltage calibration coefficient
- The screen displays the current voltage reading in real time; adjust by comparing with a multimeter
- Range: 2–400

### 8.3 Room Temperature Calibration (Cold Junction Offset)

- Use the [-] [+] buttons to adjust the cold junction temperature offset
- The screen displays the cold junction temperature reading in real time; adjust by comparing with the actual room temperature
- Range: -100 to 100 (unit: 0.1°C)

---

## 9. Sleep & Screensaver

### 9.1 Sleep Mode

The device supports two sleep trigger methods:

| Mode | Trigger | Wake Up |
|------|---------|---------|
| Stand Sleep | Place the iron on the stand | Remove the iron from the stand |
| Vibration Sleep | No vibration for the set timeout | Pick up or touch the iron |

During sleep, the tip is maintained at the sleep hold temperature (default 200°C), saving energy while allowing quick return to working temperature.

### 9.2 Auto-Shutdown & Screensaver

- After sleeping for the set auto-shutdown time, the device enters screensaver mode
- Heating is completely off in screensaver mode

| Screensaver Mode | Display | Exit Method |
|-----------------|---------|-------------|
| Show Clock | Black background with large time + date | Touch the screen |
| Screen Off | Pure black screen | Touch the screen |

> **Note**: After exiting the screensaver, the device enters normal working mode, but heating is off by default and must be manually enabled.

---

## 10. Safety Protection

The device has built-in multiple safety protection mechanisms to ensure safe operation.

### 10.1 Overcurrent Protection

| Item | Description |
|------|-------------|
| Trigger Condition | Peak current exceeds the set threshold (default 10A) |
| Trigger Behavior | Heating immediately turns off; status bar shows red "Overcurrent" warning |
| Recovery | Device restart required |

### 10.2 Over-Temperature Protection

| Item | Description |
|------|-------------|
| Trigger Condition | Tip temperature exceeds 550°C |
| Trigger Behavior | Heating immediately turns off; buzzer alarm; status bar shows red "Over-Temp" warning |
| Recovery | Automatically recovers when temperature drops below 540°C |

### 10.3 Under-Voltage Protection

| Item | Description |
|------|-------------|
| Trigger Condition | Supply voltage drops below the set threshold (default 6.0V) |
| Trigger Behavior | Heating turns off; buzzer alarm; status bar shows red "Under-Voltage" warning; voltage display turns red |
| Recovery | Automatically clears when voltage recovers |

### 10.4 Tip-Change Protection

| Item | Description |
|------|-------------|
| Trigger Condition | Heater cartridge removal/insertion detected |
| Trigger Behavior | Heating turns off; buzzer notification; status bar shows orange "Tip Change" warning; 5-second wait |
| Recovery | Automatically recovers after 5 seconds |

---

## 11. Remote Control (Web API)

Once the device is connected to WiFi, you can remotely monitor and control it via a phone or computer browser.

### 11.1 Access Method

1. Ensure the device is connected to WiFi (WiFi signal icon visible at the top left of the main screen)
2. Check the device's IP address in Settings → WiFi
3. Enter the IP address in a browser on a phone/computer on the same local network

### 11.2 Remote Control Features

| Feature | Description |
|---------|-------------|
| Real-time Status Monitoring | View current temperature, set temperature, voltage, current, power, etc. |
| Remote Temperature Setting | Adjust target temperature via web page |
| Remote Heating On/Off | Turn heating on/off via web page |
| Modify Settings | Adjust all device parameters (PID, protection thresholds, sleep settings, etc.) |
| WiFi Management | Scan and connect to WiFi networks |
| Firmware Upgrade | Upload new firmware for OTA upgrade |
| Factory Reset | Remotely restore factory settings |

### 11.3 WebSocket Real-Time Push

Once a browser is connected, the device pushes real-time status data every 100ms for dynamic monitoring.

---

## 12. Firmware Upgrade (Factory Mode)

Factory mode is used for firmware upgrades and WiFi pre-configuration.

### 12.1 Entering Factory Mode

| Method | Operation |
|--------|-----------|
| Main program OTA upgrade | Device enters automatically (no manual action needed) |
| No valid firmware | Device enters automatically (no manual action needed) |

### 12.2 Factory Mode Operation

After entering Factory mode, the screen displays the OTA upgrade guide:

1. **Connect to WiFi Hotspot**: Use a phone or computer to search and connect to WiFi:
   - SSID: `XPG.ME`
   - Password: `12345678`

2. **Open Browser**: Visit `http://192.168.4.1`

3. **Upload Firmware**:
   - Click the file selection button and choose a .bin firmware file
   - Click the "Upload Firmware" button
   - Wait for the progress bar to complete
   - The device automatically restarts with the new firmware

4. **Configure Home WiFi** (optional):
   - In the WiFi Configuration section of the same page
   - Enter your home WiFi SSID and password
   - Click "Save & Reboot"
   - After restart, the main program automatically connects to your home WiFi

---

## 13. Factory Reset

Three ways to perform a factory reset:

| Method | Operation | Description |
|--------|-----------|-------------|
| System Settings screen | Drag the "Factory Reset" slider to 100% | Must drag all the way to prevent accidental operation |
| Web API | Access the device web page and click Factory Reset | Remote operation |
| Hardware button | Long-press the BOOT button for 3 seconds | BOOT button on the device |

After factory reset:
- All user settings are restored to defaults
- Calibration data is restored to defaults
- Custom boot logo is deleted
- The device restarts automatically

---

## 14. Troubleshooting

| Problem | Possible Cause | Solution |
|---------|---------------|----------|
| Displays 25°C at startup instead of residual heat | ADC warmup not complete | Wait a few seconds for it to update to actual temperature |
| Temperature cannot reach set value | Power mode limitation / insufficient supply voltage | Check power mode settings; verify supply voltage |
| Severe temperature overshoot | Improper PID parameters | Try reducing Ki and slightly increasing Kd |
| Shows "Under-Voltage" | Supply voltage too low | Check power connection and voltage |
| Shows "Overcurrent" | Abnormal current | Check if cartridge is short-circuited; restart the device |
| Shows "Over-Temp" | Temperature exceeds 550°C | Wait for temperature to drop below 540°C for auto-recovery |
| Shows "Tip Change" | Heater cartridge change detected | Wait 5 seconds for auto-recovery |
| WiFi cannot connect | Wrong password / weak signal | Re-enter password; move closer to router |
| Touchscreen inaccurate | Touchscreen not calibrated | Re-calibrate the touchscreen in system settings |
| Cannot enter Factory mode | Firmware boots normally | Factory mode is only entered automatically during OTA or when no valid firmware exists |
| Heating is on but temperature doesn't rise | Cartridge not installed or damaged | Check cartridge connection |
| Buzzer doesn't sound | Volume set to 0 | Increase buzzer volume in Other Settings |

---

## Technical Specifications

| Item | Specification |
|------|--------------|
| Controller | ESP32-S3 dual-core 240MHz |
| Display | 3.5-inch ILI9488 color touchscreen, 320×480 resolution |
| Supported Cartridges | T12 / C245 / C210 / C470 |
| Temperature Range | 0–500°C |
| Temperature Control | PID intelligent control |
| Supply Voltage | 12–48V DC (select based on cartridge model) |
| WiFi | 802.11 b/g/n |
| Interface | Touchscreen + Web API |
| Safety Protections | Overcurrent / Over-temperature / Under-voltage / Tip-change |
| Languages | Chinese / English |

