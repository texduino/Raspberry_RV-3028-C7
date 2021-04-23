## Connecting the TexDuino RV-3028-C7 RTC to a Raspberry PI

Connect the TexDuino RV-3028-C7 breakout board to the Raspberry Pi:

<img src="/images/Connection Pinout - TexDuino RV-3028-C7 to Raspberry Pi.png"
	alt = "connecting the RTC"
/>

make sure the raspberry pi is updated:<br>
sudo apt-get update<br>
sudo apt-get upgrade<br>

Verify I2C is enabled

Edit the file /boot/config.txt  and add this line:<br>
dtoverlay=rv3028-rtc<br>

<img src="/images/editConfig.png"
	alt = "edit config file"
/>
<img src="/images/editConfigdt.png"
	alt = "nano edit config file"
/>
<br>


restart: sudo reboot<br>

Edit the file /lib/udev/hwclock-set and comment out the lines:<br>
if [ -e /run/systemd/system ] ; then
    exit 0
fi

and this line<br>
  /sbin/hwclock  --rtc=$dev --systz  --badyear
  
and this line<br>
  /sbin/hwclcok --rtc=$dev --systz

<img src="/images/edithwClock.png"
	alt = "edit hw clock file"
/><br>
<img src="/images/edithwClockCO1.png"
	alt = "nano edit hw clock file"
/><br>
<img src="/images/edithwClockCO2.png"
	alt = "nano edit config file"
/><br>


restart: sudo reboot<br>

To set the time:<br>
sudo hwclock -s

To write time:<br>
sudo hwclock -w 

To read time:<br>
sudo hwclock -r