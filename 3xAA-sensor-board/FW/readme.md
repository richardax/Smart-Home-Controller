A couple of example codes that can be used.

Note, in order to save power:
- OTA is not enabled in ESPHome, you will have to use USB
- Autoprogramming has been disabled, you have to press BOOT while connecting the USB cable, or keep BOOT pressed while shortly pressing and releasing Reset.

The API version should work as is together with Home Assistant if you have your WiFi credentials in secret.yaml

In Home Assistant:
- Go to ESPHome
- New device
- Continue (not "OPEN ESPHOME WEB")
- Create a name, press NEXT
- Choose ESP32-S2 with recommended settings checked
- Skip the install
- Edit the device that was just created
- 
