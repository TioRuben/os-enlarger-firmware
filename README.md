# Open Source Photography Enlarger head Firmware

This firmware implements a Bluetooth Low Energy (BLE) GATT server that allows remote control of an RGBW LED. The LED outputs are driven using the LEDC peripheral, enabling brightness control for red, green, blue, and white channels. This is intended to be used with the "Darkroom enlarger controller" project in [https://v0.dev/chat/darkroom-enlarger-control-bVdr1Vk1Gyb](https://v0.dev/chat/darkroom-enlarger-control-bVdr1Vk1Gyb)

## Usage
- Once flashed and running, the firmware advertises as "OS ENLARGER 📷".
- Connect using [https://v0-darkroom-enlarger-controller.vercel.app/](https://v0-darkroom-enlarger-controller.vercel.app/) or any BLE scanning tool or mobile app.
- You can click on "focus" button to turn on/off RGBW to full brightness. Use the settings on the web app to choose the desired color mix and exposure time. Click on "Expose" to begin exposure.
- Or Write a 4-byte RGBW value to the characteristic 0xFF01 on service 0x00FF to update the LED colors.

## Features
- **BLE GATT Service:** Exposes a characteristic that accepts 4-byte RGBW values.
- **Dynamic LED Control:** Updates LED colors in real time upon receiving new values.
- **Advertising:** Uses raw advertising data to broadcast the device name.
- **LED PWM Control:** Configured using ESP-IDF's LEDC driver for smooth brightness control.

## Hardware Requirements
- ESP32 module (or compatible) with built-in BLE and LEDC support.
- External LED or LED array connected to the appropriate GPIOs.

## Build and Flash Instructions
1. Set up the ESP-IDF development environment.
2. Clone this repository:
   ```
   git clone https://github.com/TioRuben/os-enlarger.git
   ```
3. Configure your project:
   ```
   idf.py menuconfig
   ```
4. Build and flash the firmware to your device:
   ```
   idf.py build flash monitor
   ```

## License
This project is released under MIT license.

## AI
This project has been entirely developed with Copilot and OpenAI o3-mini model, starting with the ESP-IDF GATTS Server example.