writer avrdude 
=======================
sudo avrdude -c linuxgpio -p m328p -U flash:w:file.hex:i 
=============================================
etc/avrdude.conf ----> uncomment l
.... program "linuxgpio"
mosi 64
miso 65
scl    66
rst    67
==================================
sudo avrdude -c linuxgpio -p m328p -e          /// erase chip
-----------------------------------------------------------------
#programmer
#  id    = "linuxgpio";
#  desc  = "Use the Linux sysfs interface to bitbang GPIO lines";
#  type  = "linuxgpio";
#  reset = 67;
#  sck   = 66;
#  mosi  = 64;
#  miso  = 65;
#;
