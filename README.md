Building Raspberry Pi ADS-B Airplane Tracking System

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

add blank file titled ssh to root directory

edit  wpa_supplicant.conf with your appropriate SSID and password

```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=US

network={
scan_ssid=1
ssid="ssid"
psk="password"
}
```

let raspi boot up, get IP from router

SSH into console with the default username pi and password `raspberry` and pull any updates to the base OS
```sudo apt-get update && sudo apt-get upgrade```

Change default password and set hostname

```sudo raspi-config```

Reboot raspi
```sudo reboot```

Follow instructions here https://www.flightradar24.com/build-your-own

At time of writing this bash script will install fr24
```sudo bash -c "$(wget -O - https://repo-feed.flightradar24.com/install_fr24_rpi.sh)"```

Install adsbexchange feeder  
At time of writing this bash script will install adsbx feeder
```sudo bash -c "$(wget -nv -O - https://raw.githubusercontent.com/adsbxchange/adsb-exchange/master/install.sh)"```
Install readsb script
```https://github.com/wiedehopf/adsb-scripts/wiki/readsb-script```


To Do
install piaware https://flightaware.com/adsb/piaware/build





