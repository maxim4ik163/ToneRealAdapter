# ToneReal Guitar Adapter
DIY Rocksmith guitar adapter based on CMedia CM6327A  USB Single-Chip Audio Solution for Mono Microphone. VID/PID/product and manufacture strings of this chip can be configured by EEPROM, that allows to use it as original cable on PlayStation, Xbox and PC.

Datasheet for this chip doesn't contain schematics, so I used PCB from various USB-microphones based on CM6327A as reference (Blue snowball ice, Trust Buzz, Bird UM-1 DEXP BK-20 etc).
To check my schematics made by photos of PCBs, i bought DEXP BK-20 with PCB YFT261764 and checked all the traces.

Project contains 3 version of PCB:
 - ToneReal_Adapter_v1.1 - small version (closer to original RGA cable).
 - ToneReal_Adapter_v1.0 - bigger version, uses ECAP (closer to reference boards).
 - ToneReal_Adapter_DIY - one layer PCB for homemade.

Both versions has footprints for USB Type-A male connector to mount adapter directly to device or Type-B female connector for use with cable. Also boards have holes for zipties, if you want to solder guitar cable directly to PCB and not use 6.35 jack.

### Disclaimer
> I did not assemble this circuit board because during the development  I tested this concept on a board from a USB microphone. And because of the need for a long wait for chip from Aliexpress and the production of PCB, I purchased the original cable :) 
But this allowed me to compare them with each other: they are identical in sound and delays.

## Assembly
1. Assemble the desired version according to the BOM (or get PCB from mic with CM6327A).
2. Program the EEPROM with the attached dump (as exemple using CH341A).
3. If everything is done correctly, the VID/PID of the device should change to 12BA 00FF.
4. Plug and enjoy :)
