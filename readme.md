Smoothieware for the MKS SBASE 1.3 for the Anycubic Kossel. Flash the official Smoothieware firmware to the board first, then upload my config to the board.
Flash the included TFT firmware to the touchscreen (if you have it) and use my config to make it talk to the board.


SBASE:

config - this is the main config file

config-override - overrides settings used for autolevel. You probably don't need this

delta.grid - specific autolevel grid information generated for my machine. You really don't need this.

TFT:
mkstft28.bin - Makerbase's firmware for the TFT32 screen (seems like 28 -32 are identical in terms of firmware)

mks_config - my config for the TFT screen

mks_pic - picture resource files to be used with the 


My wiring:

Pretty standard. 

Heater1 is the hotend

Heater2 is the hotend cooling fan (turns on at 50c)

Fan0 is the layer fan

Thermistor1 is the bed

Thermistor2 is the hotend

Z-prope is wired to Z- endstop


Don't forget to change the microstepping jumper from 1/16 to 1/32 (or halve the steps/mm in the config files).

Thoughts:

I'm not entirely sure about the stepper current. My settings are relatively low, but the drivers do heat up quite a bit. May need additional cooling, especially with the board mounted under the bed.

Wired networking seems to crash the board during prints. Use a raspberry pi with Octoprint instead, it's much faster and better.

Autolevel with the display: untested, and still need to add something to manually set the Z0 position as specified in the Smoothieware documentation.

The board uses DRV8825 stepper drivers which may emit pulses that are too short, causing artifacts/print abberations. Look into the TL-smoother or "drv8825 diode hack" for more info (it's a 13$ upgrade).


Useful links:

Smoothieware firmware:
http://smoothieware.org/flashing-smoothie-firmware

Firmware/config for the TFt screen:
https://github.com/makerbase-mks/MKS-TFT

MKS Smoothieware guide:
http://www.instructables.com/id/Configuring-MKS-Sbase-V12-32-bit-Controller-Basics/

As always, use at your own risk.