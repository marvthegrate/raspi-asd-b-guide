Building ASD-B raspi 

BOM
1 Raspberry Pi 3-b or 4-b 
1 Software defined radio and Antenna
1 MicroSD card at least 8 gb in size
1 USB power supply for raspi
optional raspi case
For my build I used the 
AirNav RadarBox FlightStick - Advanced USB ADS-B Receiver and onelinkmore 1090Mhz Antenna MCX Plug Connector 2.5dbi Gains ADS-B Aerial with Magnet Base RG174 1M+MCX Female to SMA Male Adapter Connector and a 3d printed raspi case. 


Image raspi with Noobs 
https://www.raspberrypi.org/downloads/noobs/
Download zip file, expand, copy to SD card.  Delete unused images from /os/ directory
Add silentinstall to recovery.cmdline file
add ssh file
edit wpa supplicant file with needed features /etc/wpa_supplicant/wpa_supplicant.conf

ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=US

network={
scan_ssid=1
ssid="ssid"
psk="password"
}


let boot up, get IP from router

SSH into console and "sudo apt-get update && sudo apt-get upgrade" 
Change password with "passwd" 
Reboot

Follow instructions here https://www.flightradar24.com/build-your-own

Install tar1090 https://github.com/wiedehopf/tar1090

install piaware https://flightaware.com/adsb/piaware/build
