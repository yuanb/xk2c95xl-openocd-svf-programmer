
# XK2C95XL-openocd-porgrammer
Instructions to use openocd as 'pldKit XK2C95XL XILINX CPLD Kit' programmer (FT232R)

[XK2C95XL XILINX CPLD Kit](http://pldkit.com/xk2c95xl)

## What you need
Ubuntu 20.04 running in as a Virtual Machine

## Build openocd
### Tutorials
[JTAG On the Cheap with the FTDI FT232R](https://jacobncalvert.com/2020/02/04/jtag-on-the-cheap-with-the-ftdi-ft232r/)  
[Compiling OpenOCD from Source on Ubuntu 16.04](https://hackaday.io/page/4991-compiling-openocd-from-source-on-ubuntu-1604)  

### Install required packages
```
sudo apt update
sudo apt upgrade
sudo apt-get install libtool pkg-config texinfo libusb-dev libusb-1.0.0-dev libftdi-dev autoconf make git
```
### Clone code, enable ft232r support, build and install it

```
git clone https://github.com/ntfreak/openocd.git
cd openocd/
git submodule init
git submodule update
./bootstrap
./configure --enable-ft232r --disable-dependency-tracking
make
sudo make install
cd contrib
sudo cp 60-openocd.rules /etc/udev/rules.d/
```
