## Adding the TexDuino RV-3028-C7 RTC to a Raspberry PI

make sure the raspberry pi is updated<br>
sudo apt-get update<br>
sudo apt-get upgrade<br>

enable the I2C bus in the configuration<br>
sudo raspi-config<br> 

install the I2C python library<br>
sudo apt-get install python-smbus i2c-tools<br> 

verify the raspberry pi can communicate with the RV-3028-C7 breakout board<br>
sudo i2cdetect -y 1 

the TexDuino RV-3028-C7 is at address 52

load the RV-3028-C7 RTC driver<br>
sudo nano /boot/config.txt<br> 
Add these lines at the end of the file:<br>
dtoverlay=i2c-rtc,rv3028<br> 
dtparam=i2c_baudrate=400000<br>

sudo reboot 

sudo apt-get -y remove fake-hwclock

To read time:
sudo hwclock -v -r

To write time:
sudo hwclock -w 
