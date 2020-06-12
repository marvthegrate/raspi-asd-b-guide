Building ASD-B raspi 

Image raspi with Noobs (delete un needed images from OS folder) 
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
