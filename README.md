# ESP32 Negroni Captive Portal

A captive portal that displays a beautiful Negroni cocktail poster when users connect to the ESP32's WiFi network.

## Features

- Creates an open WiFi access point (no password required)
- Automatically redirects users to the Negroni poster page
- Works with Android, iOS, and desktop captive portal detection
- Beautiful responsive design

## Hardware Required

- ESP32 development board
- USB cable for programming

## Software Setup

### Prerequisites

- PlatformIO (already installed)
- USB drivers for your ESP32 board (usually CH340 or CP2102)

### Installation Steps

1. **Open the project in PlatformIO:**
   - Open VS Code or your PlatformIO IDE
   - File → Open Folder → Select the `esp32-captive-portal` folder

2. **Connect your ESP32:**
   - Connect your ESP32 to your computer via USB
   - Make sure the correct COM port is detected

3. **Build and Upload:**
   - Click the PlatformIO "Upload" button (arrow icon)
   - Or use the command: `pio run --target upload`

4. **Monitor Serial Output (optional but recommended):**
   - Click the "Serial Monitor" button
   - Or use: `pio device monitor`
   - You should see: "Captive portal started!"

## Usage

1. **Power on the ESP32** (either via USB or external power)

2. **Connect to WiFi:**
   - Look for WiFi network: `Negroni Portal`
   - Connect to it (no password required)

3. **View the page:**
   - On most devices, a captive portal popup will appear automatically
   - If not, open a web browser and go to any website
   - You'll be redirected to the Negroni poster

## Customization

### Change WiFi Name

Edit `src/main.cpp`, line 9:
```cpp
const char* ssid = "Negroni Portal";  // Change this to your desired name
```

### Change HTML Content

Edit the `index_html` content in `src/main.cpp` starting at line 13.

### Add Password Protection

To add a password to the WiFi, change line 94:
```cpp
WiFi.softAP(ssid, "your-password-here");
```

## Troubleshooting

**Issue: Can't connect to WiFi**
- Make sure ESP32 is powered on
- Check Serial Monitor for "Captive portal started!" message
- Try forgetting the network and reconnecting

**Issue: Captive portal doesn't pop up automatically**
- Try opening a browser and visiting any website
- The ESP32 IP is usually: 192.168.4.1
- You can visit this directly in your browser

**Issue: Upload failed**
- Make sure the correct COM port is selected
- Try pressing the BOOT button on ESP32 during upload
- Check USB cable (some cables are power-only)

**Issue: Fonts not loading**
- The fonts require internet connection on the viewing device
- The ESP32 serves the HTML, but Google Fonts loads from Google's servers
- Make sure the device viewing the page has internet access (can be from cellular data)

## Technical Details

- **WiFi Mode:** Access Point (AP)
- **IP Address:** 192.168.4.1
- **DNS Server:** Redirects all requests to ESP32
- **HTTP Server:** Serves HTML on port 80
- **Memory:** HTML stored in PROGMEM to save RAM

## License

Free to use and modify for personal and commercial projects.
