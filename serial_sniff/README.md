This program sniff the communication between an iDevice and a Serial
accessory.

This is intended to run on an Arduino but other AVR boards can be used.

 - **RX1** should be connected to **Data1** pin of the iDevice's lightning port.
 - **TX1** should be connected to **Data2** pin of the iDevice's lightning port.
 - **RX2** should be connected to **Data2** pin of the accessory's lightning connector.
 - **TX2** should be connected to **Data1** pin of the accessory's lightning connector.

**The code is not written with the Arduino IDE. Here are instructions
for compiling and uploading the code:**

 - For Arduino Uno:
```
avr-gcc -DF_CPU=16000000UL -mmcu=atmega328p -Os -o serial_sniff.o serial_sniff.c
avr-objcopy -O ihex -R .eeprom serial_sniff.o serial_sniff.hex
avrdude -V -F -c arduino -p m328p -b 115200 -P /dev/ttyACM0 -U flash:w:serial_sniff.hex
```

 - For Arduino Mega:
```
avr-gcc -DF_CPU=16000000UL -mmcu=atmega2560 -Os -o serial_sniff.o serial_sniff.c
avr-objcopy -O ihex -R .eeprom serial_sniff.o serial_sniff.hex
avrdude -V -F -c stk500v2 -p m2560 -b 115200 -P /dev/ttyACM0 -U flash:w:serial_sniff.hex
```
