# Need to be installed 

Install GDB
$ sudo apt install gdb-multiarch

You'll also need:

- make
- libtool
- pkg-config >= 0.23 or pkgconf

OpenOCD uses jimtcl library; build from git can retrieve jimtcl as git
submodule.

Additionally, for building from git:

- autoconf >= 2.69
- automake >= 1.14
- texinfo >= 5.0
```
sudo apt-get update
sudo apt-get install libtool pkg-config
sudo apt-get install pkg-config libjim-dev
```
==========================================================
sudo apt install git libtool pkg-config   
# download git OpenOcg 
git clone https://github.com/openocd-org/openocd.git 

---------------------------------------------------------
edit /tcl/interface/sysfsgpio-raspberrypi.cfg 
```
# Original Orange PI One -- PC04 PD14 TxD1 RxD1
# Need to connect serial interface!!! Two wire for SWCLK SWDIO, two for Serial UART
sysfsgpio jtag_nums 68 110 190 198 

# Each of the SWD lines need a gpio number set: swclk swdio
# Header pin numbers: 23 22
sysfsgpio swd_nums 68 110
```
============================================================
```
cd openocd 
# ./bootstrap 
# ./configure --enable-sysfsgpio 
# make 
# make install
```
```
cd /usr/local/share/openocd/scripts/interface
sudo vim sysfsgpio-raspberrypi.cfg
```
=================================================================
```
### Comunication for RB Pico
```
sudo openocd -f interface/sysfsgpio-raspberrypi.cfg -f target/rb2040.cfg 
```
```
sudo openocd -f interface/sysfsgpio-raspberrypi.cfg -f target/stm32f1x.cfg 
```
### // write flash (takes long time)
```
sudo openocd -f interface/sysfsgpio-raspberrypi.cfg -f target/stm32f1x.cfg -c "program blink.elf verify reset exit"
```
#### New test for STM32L151xE 

```
sudo openocd -f interface/sysfsgpio-raspberrypi.cfg -f target/stm32l1.cfg 
```
```
$ sudo src/openocd -f interface/picoprobe.cfg -f target/rp2040.cfg -s tcl
```
https://catch22eu.github.io/website/baremetal/openocd_sysfs_stm32/ <br/>
https://github.com/raspberrypi/openocd

```

```


