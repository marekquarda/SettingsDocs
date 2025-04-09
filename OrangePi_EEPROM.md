https://www.laskakit.cz/user/related_files/winbond-elec-w25q64fv.pdf

# Modify Orange PI
Set overlays=spi-spidev in **/boot/orangepiEnv.txt**, set
param_spidev_spi_bus=0, where 0 represents spi0
```
overlays=spi-spidev
param_spidev_spi_bus=0
```
