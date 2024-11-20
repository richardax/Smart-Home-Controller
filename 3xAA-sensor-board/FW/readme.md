A couple of example codes that can be used.

Note, in order to save power:
- OTA is not enabled in ESPHome, you will have to use USB
- Autoprogramming has been disabled, you have to press BOOT while connecting the USB cable, or keep BOOT pressed while shortly pressing and releasing Reset.

The API code is installed by default and should work as is together with Home Assistant
If you have your WiFi credentials in secret.yaml it should show up when connected, otherwise AP will be enabled, connecto to the WiFi "RNX-AA xxxxxx", enter 192.168.4.1 in a browser and choose your network.

During setup, awake LED will be turned on and the status LED will blink (meaning not connected). Note that it will timeout, so make sure it is blinking when you look for it in Home Assistant. You can restart the procedure by pressing reset button.

To add it in HA follow instruction below "For API".

To simplify the process, the API code has been preinstalled. It is a bit less work to get going, but will consume more power.
MQTT will update faster and more reliably, i.e. saving battery, but you will have to install an MQTT broker to use it.

To chage the code, do this:

In Home Assistant:
- Go to ESPHome
- New device
- Continue (not "OPEN ESPHOME WEB")
- Create a name, press NEXT
- Choose ESP32-S2 with recommended settings checked
- Skip the install
- Edit the device that was just created
- Paste the API or MQTT code from this repository
- Press Install
- Choose "Plug into this computer"
- Wait to prepare download
- Press "Download project" and choose "Factory format" (your browser may block the file and you may have to press "keep" or something)
- Option 1:
  - "Open ESPHome Web"
  - While keeping the boot button pressed, plug in the board to USB
  - Press Connect
  - Choose the COM port (if no COM port shows up, you may have to install drivers. Also make sure you dont have any terminal running that is connected to the COM port)
  - Press INSTALL
  - Select the file you just downloaded and press INSTALL
  - Wait until installed, press close
- Option 2, this will give you a little bit more information in case you need it:
  - Go to https://adafruit.github.io/Adafruit_WebSerial_ESPTool/
  - While keeping the boot button pressed, plug in the board to USB
  - Press Connect
  - Choose the COM port
  - Select the file just downloaded in the top "Choose a file"
  - Press Program
  - Wait until installed, disconnect
- Press Reset button on the board

For API code:
- Home Assistant, Settings
- Devices & Services
- ESPHome
- The new device should have been discovered, or press "Add device", press configure, done.

For MQTT code:
- Home Assistant, ESPHome, press "Secrets" in the upper right corner. Keep your MQTT credentials (broker, user and password) here and it should work as is.
- Home Assistant, Settings
- Devices & Services
- MQTT
- The new device should be here


