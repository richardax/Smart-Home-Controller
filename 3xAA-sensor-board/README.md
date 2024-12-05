Examples codes are available in FW folder

Note, in order to save power:
- OTA can be used, but you need to prevent sleep and wait for it to wake ni order to use OTA
- Autoprogramming has been disabled, you have to press BOOT while connecting the USB cable, or keep BOOT pressed while shortly pressing and releasing Reset.

To simplify the process, the API code has been preinstalled. It is a bit less work to get going, but will consume more power.
MQTT will update faster and more reliably, i.e. saving battery, but you will have to install an MQTT broker to use it.

Setup:
- Power up the device by inserting 3xAA batteries or by connecting a USB cable
- The awake LED will turn on and the status LED will blink (meaning not connected)
- Connect to the AP (WiFi) "rdnx-aa"
- Enter 192.168.4.1 in a browser and choose your network

In Home Assistant:
- Settings / Integrations / ESPHome
- The device should be discovered, press Configure
- It will ask if you want to add it, press Submit
- Select an area if you want to, press finish
- The device is now added, but will have no entries yet

- Go to ESPHome add-on (not the integration)
- The device will be discovered, press Adopt
- You will be asked to rename it if you want, press Adopt
- Configuration created, you can press install here, or make some changes if you want to (note that once you install, the device will sleep most of the time and you will need to take some extra steps to install via OTA, or use USB)
- To check the code and make changes:
  - Press skip, not install
  - Press close
  - Find the device you just added, press edit
  - Here you can edit the code if you want to
  - If you want to be able to disable sleep in order to use OTA and change sleep duration, follow the instructions to setup a helper
  - If you do not want to set up the helper, you can set the permanent sleep duration in substitution: initial_sleep_duration
  - Note that if you do not set up the helper to prevent sleep, you will still be able to use OTA for the first installation, but for future updates, you will have to use a USB cable
  - When you are done with the code, press Install, press Wirelessly
- When the install is completed, press the reset button, the Awake LED will come on, the Status LED will blink until connected and then both LEDs will turn off
- Go back to Homeassistant / Setting Integrations / ESPHome
- Your device will be here and should have all entities updated
- If you setup the helper to prevent sleep, you can turn it on and sleep will be prevented next time it wakes up and you can use OTA or change sleep duration


To use MQTT instead of API (note that you don't need the sleep prevention helper with MQTT, but you will need a MQTT broker installed)

- Power up the device by inserting 3xAA batteries or by connecting a USB cable
- The awake LED will turn on and the status LED will blink (meaning not connected)
- Connect to the AP (WiFi) "rdnx-aa"
- Enter 192.168.4.1 in a browser and choose your network 

In Home Assistant:
- Go to ESPHome add-on (not the integration)
- The device will be discovered, press Adopt
- You will be asked to rename it if you want, press Adopt
- Configuration created, press skip, not install
- Press close
- Find the device you just added, press edit
- Remove all but the name substitution
- Copy and paste the MQTT code from this repository
- Replace the name with what the device name was
- Keep your credentials (MQTT broker, user, password, and SSID and password) in "Secrets" and it should work as is, or you will have to enter your credentials on the code.

If you accidently delete the device of for some other reason want to start from scratch with a new device and code, follow these instructions:

In Home Assistant:
- Go to ESPHome (add-on, not integration)
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
