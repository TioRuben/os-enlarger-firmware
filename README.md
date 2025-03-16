# Open Source Enlarger Firmware

This firmware implements a Bluetooth Low Energy (BLE) GATT server that allows remote control of an RGBW LED. The LED outputs are driven using the LEDC peripheral, enabling brightness control for red, green, blue, and white channels. This is intended to be used with the "Darkroom enlarger controller" project in [https://v0.dev/chat/darkroom-enlarger-control-bVdr1Vk1Gyb](https://v0.dev/chat/darkroom-enlarger-control-bVdr1Vk1Gyb)

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

## Usage
- Once flashed and running, the firmware advertises as "OS ENLARGER 📷".
- Connect using [https://v0-darkroom-enlarger-controller.vercel.app/](https://v0-darkroom-enlarger-controller.vercel.app/) or any BLE scanning tool or mobile app.
- Write a 4-byte RGBW value to the characteristic to update the LED colors.

## License
This project is released under the Unlicense OR CC0-1.0.
