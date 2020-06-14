Building Raspberry Pi ADS-B Airplane Tracking System

This guide is to help people set up a raspberrry pi powered ADS-B tracker, this will allow you to track aircraft in your aread. Additionally, it will feed FlightRadar24, ADS-B Exchange and FlightAware. A side benefit is that you will get commercial access to FR24 and FlightAware's sites.  There are prebuilt images available for some of these, but I wanted to be able to feed multiple sites. 

BOM

1 Raspberry Pi 3-b or 4-b 

1 Software defined radio and Antenna

1 MicroSD card at least 16 gb in size

1 USB power supply for raspi

optional raspi case

For my build I used the 

AirNav RadarBox FlightStick - Advanced USB ADS-B Receiver and onelinkmore 1090Mhz Antenna MCX Plug Connector 2.5dbi Gains ADS-B Aerial with Magnet Base RG174 1M+MCX Female to SMA Male Adapter Connector and a 3d printed raspi case. 


Create image for raspberry pi.  

I used SD Card Formatter https://www.sdcard.org/downloads/formatter/ to cleanly format a 8+ Gig microSD card. 

Use Raspberry Pi Imager to copy over the Raspberry Pi Lite image to the micro SD card. 

https://www.raspberrypi.org/downloads/

If you want to do a wireless and headless install you will need to add two files to the root directory of the SD card

add blank file titled ssh to root directory with no file extension. 

create the wpa_supplicant.conf file in the root directory of the sd card with your appropriate SSID and password

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

let raspi boot up, get IP from your wireless router.

SSH into console with the default username pi and password `raspberry` and pull any updates to the base OS
```sudo apt-get update && sudo apt-get upgrade```

You should change the default password as well as your localization information. raspi-config will allow you to do this.  Make sure that you select the correct country, correct keyboard layout and time zone when doing this. 

```sudo raspi-config```

Reboot raspi
```sudo reboot```

To install FR24 on a fresh raspberry pi install use the following script. If this script fails, https://www.flightradar24.com/build-your-own will have additional instructions. 

At time of writing this bash script will install fr24
```sudo bash -c "$(wget -O - https://repo-feed.flightradar24.com/install_fr24_rpi.sh)"```

Install adsbexchange feeder  
At time of writing this bash script will install adsbx feeder
```sudo bash -c "$(wget -nv -O - https://raw.githubusercontent.com/adsbxchange/adsb-exchange/master/install.sh)"```

Install readsb script
```https://github.com/wiedehopf/adsb-scripts/wiki/readsb-script```

At time of writing this script will install readsb
```sudo bash -c "$(wget -q -O - https://raw.githubusercontent.com/wiedehopf/adsb-scripts/master/readsb-install.sh)"
```

Install PiAware. Follow directions at https://flightaware.com/adsb/piaware/install





