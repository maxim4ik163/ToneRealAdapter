# ToneReal Guitar Adapter
## RU
Самодельный гитарный адаптер для игры в Rocksmith на базе CMedia CM6327A, которая имеет возможность конфигурации VID/PID через EEPROM, что позволяет использовать её как оригинальный кабель на PlayStation, Xbox и ПК.

[Даташит](https://github.com/maxim4ik163/ToneRealAdapter/blob/main/Datasheets/CM6327A.pdf) на этот чип не содержит принципиальной схемы, поэтому пришлось воссоздовать её по [фотографиям](https://github.com/maxim4ik163/ToneRealAdapter/tree/main/Reference_PCB's) плат от различных USB-микрофонов на базе CM6327A (Blue snowball ice, Trust Buzz, Bird UM-1, DEXP BK-20 и т.д.).
Для того чтобы быть уверенным в принципиальной схеме я купил DEXP BK-20 с типовой платой YFT261764 на базе CM6327A.

Проект содержит 3 версии платы:
  - ToneReal_Adapter_v1.1 - уменьшенная версия с керамическими конденсаторами (ближе к оригинальному кабелю RGA).
  ![v1.1](https://raw.githubusercontent.com/maxim4ik163/ToneRealAdapter/main/Pics/v1.1_TOP.PNG)

  - ToneReal_Adapter_v1.0 - увеличенная версия, с электролитическими SMD конденсаторами (реплика платы YFT261764).
  ![v1.1](https://raw.githubusercontent.com/maxim4ik163/ToneRealAdapter/main/Pics/v1.0_TOP.PNG)

  - ToneReal_Adapter_DIY - однослойная плата для изготовления методом ЛУТ.
  ![v1.1](https://raw.githubusercontent.com/maxim4ik163/ToneRealAdapter/main/Pics/DIY_TOP.PNG)

  В версиях 1.0 и 1.1 предусмотрены посадочные места для разъема USB type-A для подключения адаптера непосредственно в устройство или гнездового разъема type-B для использования с кабелем. Также на платах есть отверстия для стяжек, если вы захотите припаять гитарный кабель напрямую к плате, а не использовать джек 6.35.

## Сборка
1. Соберите желаемую версию в соответствии с BOM (или используйте готовую плату от микрофона на базе CM6327A).
2. Запрограммируйте EEPROM с прикрепленным [дампом](https://github.com/maxim4ik163/ToneRealAdapter/blob/main/EEPROM/DUMP%20RGA.bin) (например, используя программатор CH341A).
3. Если все сделано правильно, VID/PID устройства должен [измениться](https://github.com/maxim4ik163/ToneRealAdapter/blob/main/Pics/VID_PID.png) на 12BA 00FF.
4. Собирайте Олимпийский в Rocksmith :)

## Тесты
  - PlayStation 5 с PS4 Rocksmith 2014 Remastered (*примечание: версия для PS4 имеет проблему с задержкой вывода звука на PS5 через HDMI как и с оригинальным кабелем. Используйте беспроводную гарнитуру Pulse 3D или Dualsense для вывода звука*) - [ссылка](https://github.com/maxim4ik163/ToneRealAdapter/blob/main/Test_videos/PS5_test.MOV)
  - XBOX360 с Rocksmith 2014 - [ссылка](https://github.com/maxim4ik163/ToneRealAdapter/blob/main/Test_videos/XBOX360_test.MOV)
  - ПК с Rocksmith 2014 Remastered - [ссылка](https://github.com/maxim4ik163/ToneRealAdapter/blob/main/Test_videos/PC_test.MOV)

### Дисклеймер
> Из-за необходимости долгого ожидания CM6327A с Алиэкспресс, производства печатной платы и отсутсвия скидок на Rocksmith в PSN я не выдержал и купил с рук оригинальный кабель с игрой :) Зато это позволило мне сравнить оригинальный кабель и самодельный друг с другом: они идентичны по звучанию и задержкам. Так что в правильности схемы я уверен на 99.9%.

## En
DIY Rocksmith guitar adapter based on CMedia CM6327A  USB Single-Chip Audio Solution for Mono Microphone. VID/PID/product and manufacture strings of this chip can be configured by EEPROM, that allows to use it as original cable on PlayStation, Xbox and PC.

[Datasheet](https://github.com/maxim4ik163/ToneRealAdapter/blob/main/Datasheets/CM6327A.pdf) for this chip doesn't contain schematics, so I used PCB from various USB-microphones based on CM6327A as [reference](https://github.com/maxim4ik163/ToneRealAdapter/tree/main/Reference_PCB's) (Blue snowball ice, Trust Buzz, Bird UM-1 DEXP BK-20 etc).
To check my schematics made by photos of PCBs, i bought DEXP BK-20 with PCB YFT261764 and checked all the traces.

Project contains 3 version of PCB:
 - ToneReal_Adapter_v1.1 - small version (closer to original RGA cable).
 ![v1.1](https://raw.githubusercontent.com/maxim4ik163/ToneRealAdapter/main/Pics/v1.1_TOP.PNG)
 - ToneReal_Adapter_v1.0 - bigger version, uses ECAP (closer to reference boards).
 ![v1.1](https://raw.githubusercontent.com/maxim4ik163/ToneRealAdapter/main/Pics/v1.0_TOP.PNG)
 - ToneReal_Adapter_DIY - one layer PCB for homemade.
 ![v1.1](https://raw.githubusercontent.com/maxim4ik163/ToneRealAdapter/main/Pics/DIY_TOP.PNG)

 Versions 1.0 and 1.1 has footprints for USB Type-A male connector to mount adapter directly to device or Type-B female connector for use with cable. Also boards have holes for zipties, if you want to solder guitar cable directly to PCB and not use 6.35 jack.

## Assembly
1. Assemble the desired version according to the BOM (or get PCB from mic with CM6327A).
2. Program the EEPROM with the attached [dump](https://github.com/maxim4ik163/ToneRealAdapter/blob/main/EEPROM/DUMP%20RGA.bin) (as exemple using CH341A).
3. If everything is done correctly, the VID/PID of the device should [change](https://github.com/maxim4ik163/ToneRealAdapter/blob/main/Pics/VID_PID.png) to 12BA 00FF.
4. Plug and enjoy :)

## Tests
 -  PlayStation 5 with PS4 Rocksmith 2014 Remastered (*note: PS4 version has output delay issue on PS5 via HDMI with original/ToneReal cable. Use Pulse 3D Wireless Headset or Dualsense for audio output*)  - [link](https://github.com/maxim4ik163/ToneRealAdapter/blob/main/Test_videos/PS5_test.MOV)
 -  XBOX360 with Rocksmith 2014 - [link](https://github.com/maxim4ik163/ToneRealAdapter/blob/main/Test_videos/XBOX360_test.MOV)
 -  PC with Rocksmith 2014 Remastered - [link](https://github.com/maxim4ik163/ToneRealAdapter/blob/main/Test_videos/PC_test.MOV)

### Disclaimer
> I did not assemble this circuit board because during the development  I tested this concept on a board from a USB microphone. And because of the need for a long wait for chip from Aliexpress, production of PCB and PSN game discount I purchased the original cable with game :) 
But this allowed me to compare them with each other: they are identical in sound and delays. So I am 99.9% sure that the circuit is correct.

