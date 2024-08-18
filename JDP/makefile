SERIALPORT = /dev/tty.usbmodem 14301
SOURCEFILE = message.c i2c.c SSD1306.c

begin:	main.hex

main.hex: main.elf
	rm -f main.hex
	avr-objcopy -j .text -j .data -O ihex main.elf main.hex
	avr-size --format=avr --mcu=atmega328p main.elf

main.elf: $(SOURCEFILE)
	avr-gcc -Wall -Os -DF_CPU=16000000 -mmcu=atmega328p -o main.elf $(SOURCEFILE) 

flash:	begin
	avrdude -c arduino -b 115200 -P $(SERIALPORT) -p atmega328p -U flash:w:main.hex:i