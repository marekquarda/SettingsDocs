```
sudo vim /usr/local/share/openocd/scripts/interface/sysfsgpio-raspberrypi.cfg
```
## interface/sysfsgpio-raspberrypi.cfg

```
adapter driver sysfsgpio
# Header pin numbers: 16 12 40 38
# Pins PC4 PD14 PG7 PG6 
sysfsgpio jtag_nums 68 110 199 198 

# Header pin numbers: 16 12
sysfsgpio swd_nums 68 110

transport select swd

# Header pin PC07
sysfsgpio srst_num 71
reset_config srst_only srst_nogate connect_assert_srst
```
