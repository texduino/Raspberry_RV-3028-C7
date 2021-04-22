## Adding the TexDuino RV-3028-C7 RTC to a Raspberry PI

make sure the raspberry pi is updated
sudo apt-get update
sudo apt-get upgrade

enable the I2C bus in the configuration
sudo raspi-config 

install the I2C python library
sudoapt-get install python-smbus i2c-tools 

verify the raspberry pi can communicate with the RV-3028-C7 breakout board
sudo i2cdetect -y 1 

the TexDuino RV-3028-C7 is at address 52

load the RV-3028-C7 RTC driver
sudo nano /boot/config.txt 
Add a line with:
dtoverlay=i2c-rtc,rv3028 

sudo reboot 

sudo apt-get -y remove fake-hwclock

To read time:
sudo hwclock -v -r

To write time:
sudo hwclock -w 
