# Configure AvrDude in Orange PI

writer avrdude 

```
$ sudo avrdude -c linuxgpio -p m328p -U flash:w:file.hex:i 
```
Edit Avr configure file
```
$ vim etc/avrdude.conf 
```
----> uncomment 
```
.... program "linuxgpio"
mosi 64
miso 65
scl    66
rst    67
```
Erase chip (example)
```
sudo avrdude -c linuxgpio -p m328p -e          /// erase chip
```
Erase chip (AT90S8535)
```
sudo avrdude -c linuxgpio -p 8535 -e          /// erase chip
```

Other configuration
```
#programmer
#  id    = "linuxgpio";
#  desc  = "Use the Linux sysfs interface to bitbang GPIO lines";
#  type  = "linuxgpio";
#  reset = 67;
#  sck   = 66;
#  mosi  = 64;
#  miso  = 65;
#;
```
