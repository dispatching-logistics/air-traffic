# air-traffic
Raspberry Pi 3 Stratux Plane Finder Client

###Start with a Raspberry Pi Stratux Kit with antennas.

[Vilros Raspberry Pi Dual Channel Aviation Traffic Receiver Kit](https://amzn.to/2kAITFz)

* Set it up outside, protected from the elements.
* A small container can house everything.
* Use an extension cord for power and have the antennas outside the container.
* [Add-on Antennas](https://amzn.to/2GRAQkO)


####SSH to it
```ssh pi@IP.ADDRESS.HERE``` password ```raspberry```

Change WiFi Settings
-
```sudo nano /etc/network/interfaces```

```
auto lo
 
iface lo inet loopback
iface eth0 inet dhcp
 
allow-hotplug wlan0
 
iface wlan0 inet static
      wpa-ssid "WIFINETWORKNAME"
      wpa-psk "WIFIPASSWORD"
      address 192.168.0.31
      netmask 255.255.255.0
      gateway 192.168.0.1

```
```sudo reboot``` to save and apply settings.

Setup Plane Finder Client
-
```
wget http://client.planefinder.net/pfclient_3.7.40_armhf.deb
 
sudo dpkg -i pfclient_3.7.40_armhf.deb
 
sudo reboot
```

Other Commands
-
Find the port to use
```sudo netstat -pant```

check disk usage
```
df

cd /var/log/stratux && sudo rm -rf *
sudo truncate -s 0 /var/log/*.*
```

```
sudo apt-get update && sudo apt-get -y install ntp

sudo /etc/init.d/ntp stop && sudo ntpd -q -g && sudo /etc/init.d/ntp start

sudo nano /etc/init.d/dothetimething
sudo chmod 755 /etc/init.d/dothetimething
sudo update-rc.d dothetimething defaults
```
