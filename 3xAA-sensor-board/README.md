Examples codes are available in FW folder

Note, in order to save power:
- OTA can be used, but you need to prevent sleep and wait for it to wake ni order to use OTA
- Autoprogramming has been disabled, you have to press BOOT while connecting the USB cable, or keep BOOT pressed while shortly pressing and releasing Reset.

The API code is installed by default and should work as is together with Home Assistant
At the first start AP will be enabled, connecto to the WiFi "Device name xxxxxx", enter 192.168.4.1 in a browser and choose your network. Note that you only have one minute to set it up. The device will time out and go back to sleep if not connected within a minute. You can wake it up by pressing the reset button. More details below in these instructions.

During setup, awake LED will be turned on and the status LED will blink (meaning not connected). Note that it will timeout, so make sure it is blinking when you look for it in Home Assistant. You can restart the procedure by pressing reset button.

To add it in HA follow instruction below "For API".

To simplify the process, the API code has been preinstalled. It is a bit less work to get going, but will consume more power.
MQTT will update faster and more reliably, i.e. saving battery, but you will have to install an MQTT broker to use it.

To change the code, do this:

In Home Assistant:
- Go to ESPHome
- New device
- Continue (not "OPEN ESPHOME WEB")
- Create a name, press NEXT
- Choose ESP32-S2 with recommended settings checked
- Skip the install
- Edit the device that was just created
- Delete everything except the name and friendly name
- Paste the API or MQTT code from this repository. Note: Keep your credentials (MQTT broker, user, password, and SSID and password) in "Secrets" and it should work as is, or you will have to enter your credentials on the code.
- Replace the name and friendly name in "substitutions:" with what you named your device
- Note the "name_add_mac_suffix: true" in the code
  - If you have several devices named the same, keep this true and the last three bytes of the MAC will be added at the end of the name
  - If you only have on device or manually name them differently, you can change this to false and the device will get the name you gave it
- Press Install
- Choose "Plug into this computer"
- Wait to prepare download
- Press "Download project" and choose "Factory format" (your browser may block the file and you may have to press "keep" or something)
- Option 1:
  - "Open ESPHome Web"
  - While keeping the boot button pressed, plug in the board to USB
  - Press Connect
  - Choose the COM port (if no COM port shows up, you may have to install drivers. Also make sure you dont have any other terminal running that is connected to the COM port)
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

Now you will have ONLY 1 MINUTE to set it up! It will time out and go back to sleep after one minute. To wake it and restart the process you can push the reset button and you have another minute.

On your phone or computer
- Open your wifi settings
- Connect to the wifi with the device name
- You may or may not have to do some of these steps manually
  - Open web browser and go to 198.168.4.1
  - If it does not connect, try turn of mobile data and retry
- Select the network you want to connect to and type in password, press connect

By now it will probably time out and go to sleep, so before next step, press reset.

For API code:
- Home Assistant, Settings
- Devices & Services
- ESPHome
- The new device should have been discovered, or press "Add device", press configure, done.

For MQTT code:
- Home Assistant, Settings
- Devices & Services
- MQTT
- The new device should be here

