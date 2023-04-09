# ToneReal Guitar Adapter
DIY Rocksmith guitar adapter based on CMedia CM6327A  USB Single-Chip Audio Solution for Mono Microphone. VID/PID/product and manufacture strings of this chip can be configured by EEPROM, that allows to use it as original cable on PlayStation, Xbox and PC.

Datasheet for this chip doesn't contain schematics, so I used PCB from various USB-microphones based on CM6327A as [reference](https://github.com/maxim4ik163/ToneRealAdapter/tree/main/Reference_PCB's) (Blue snowball ice, Trust Buzz, Bird UM-1 DEXP BK-20 etc).
To check my schematics made by photos of PCBs, i bought DEXP BK-20 with PCB YFT261764 and checked all the traces.

Project contains 3 version of PCB:
 - ToneReal_Adapter_v1.1 - small version (closer to original RGA cable).
 ![v1.1](https://raw.githubusercontent.com/maxim4ik163/ToneRealAdapter/main/Pics/v1.1_TOP.PNG)
 - ToneReal_Adapter_v1.0 - bigger version, uses ECAP (closer to reference boards).
 ![v1.1](https://raw.githubusercontent.com/maxim4ik163/ToneRealAdapter/main/Pics/v1.0_TOP.PNG)
 - ToneReal_Adapter_DIY - one layer PCB for homemade.
 ![v1.1](https://raw.githubusercontent.com/maxim4ik163/ToneRealAdapter/main/Pics/DIY_TOP.PNG)

 Versions 1.0 and 1.1 has footprints for USB Type-A male connector to mount adapter directly to device or Type-B female connector for use with cable. Also boards have holes for zipties, if you want to solder guitar cable directly to PCB and not use 6.35 jack.

### Disclaimer
> I did not assemble this circuit board because during the development  I tested this concept on a board from a USB microphone. And because of the need for a long wait for chip from Aliexpress and the production of PCB, I purchased the original cable :) 
But this allowed me to compare them with each other: they are identical in sound and delays.

## Assembly
1. Assemble the desired version according to the BOM (or get PCB from mic with CM6327A).
2. Program the EEPROM with the attached [dump](https://github.com/maxim4ik163/ToneRealAdapter/blob/main/EEPROM/DUMP%20RGA.bin) (as exemple using CH341A).
3. If everything is done correctly, the VID/PID of the device should [change](https://github.com/maxim4ik163/ToneRealAdapter/blob/main/Pics/VID_PID.png) to 12BA 00FF.
4. Plug and enjoy :)

## Tests
 -  PlayStation 5 with PS4 Rocksmith 2014 Remastered (*note: PS4 version has output delay issue on PS5 via HDMI with original/ToneReal cable. Use Pulse 3D Wireless Headset or Dualsense for audio output*)  - [link](https://github.com/maxim4ik163/ToneRealAdapter/blob/main/Pics/PS5_test.MOV)
 -  XBOX360 with Rocksmith 2014 - [link](https://github.com/maxim4ik163/ToneRealAdapter/blob/main/Pics/XBOX360_test.MOV)
 -  PC with Rocksmith 2014 Remastered - [link](https://github.com/maxim4ik163/ToneRealAdapter/blob/main/Pics/PC_test.MOV)

