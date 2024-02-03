# Download

The latest OpenWRT firmware images for Netgear R9000 and Netgear XR700

* [OpenWRT Linux v6.1.69 builds for Netgear R9000 and XR700](https://github.com/masmbit/Netgear-R9000-Build/tree/master/bin/01.01.2024)


# Install

- Upgrade
```
If you already have OpenWRT installed on the router, you can flash the sysupgrade files directly from LuCi
for R9000: openwrt-alpine-generic-netgear_r9000-squashfs-sysupgrade
for XR700: openwrt-alpine-generic-netgear_xr700-squashfs-sysupgrade
```

- First time
```
To install OpenWrt on a router for the first time, the following steps are required ...*
-> on Windows
-> on Linux
```


# W I N D O W S

Use [Tftpd64](https://github.com/PJO2/tftpd64) to flash the OpenWRT firmware in windows


#### prepare TFTP
```
a) setup lan adapter to 192.168.1.5
b) open TFTP tool and select client mode
c) server interfaces select 192.168.1.5
d) set host to "192.168.1.1" and port to 69
e) select the firmware under local file
```

#### To put the R9000 into TFTP mode.

```
1. Power off the router

2. Hold down the reset button.

3. Power on the router and keep holding down the reset button.

4. When the router first boots the power led flashes orange and then it will switch to a slow white flash.
   Keep holding down reset button. The slow white flash will change to a faster white flash and then to a second even faster white flash.
   Let it blink 3-4 on the second set of faster white flashes and let go of the reset button and now send the IMG file via TFTP.
   (When the power LED is fast white blinking, the router is in TFTP mode and ready to accept any IMG file)   

5. Push the file onto the router using TFTP64.
     for R9000: "openwrt-alpine-generic-netgear_r9000-squashfs-factory"
     for XR700: "openwrt-alpine-generic-netgear_xr700-squashfs-factory"
   --> "Put" on TFTP

6. Wait a full 5 minutes before touching the router. It should do it's update and reboot by itself. 

7. Keep your browser open and try to load 192.168.1.1
```


# L I N U X


#### Install TFTP Server
```
On Debian and Ubuntu
    apt-get install tftpd-hpa 

Fedora and CentOS
    yum -y install tftp-server 
```
#### Setup your host for sending factory image
```
Connect PC via Ethernet cable to one of the switch ports on the router
Assign IP address 192.168.1.2 to host
Device IP address will be 192.168.1.1 in recovery mode
```
#### Enter recovery mode
```
Power off router
Press and hold reset button at the back
Still hold the button pressed and power on router
Hold the button pressed for 10 seconds
Power LED blinks white every second
Router expects a firmware sent via TFTP
Router responds to pings to address 192.168.1.1
```
#### Send factory image to device
```
Use a TFTP client to send a factory image from your host to device
Only IMG files can be sent via TFTP
command in Linux for R9000: tftp-hpa -v -m binary 192.168.1.1 -c put openwrt-alpine-generic-netgear_r9000-squashfs-factory.img
command in Linux for XR700: tftp-hpa -v -m binary 192.168.1.1 -c put openwrt-alpine-generic-netgear_xr700-squashfs-factory.img
After sending IMG file to router via TFTP wait for router reboot
```

```
```
# Screenshot
![Screenshot of OpenWRT on Netgear R9000](https://github.com/masmbit/Netgear-R9000-Build/blob/master/bin/01.01.2024/Screenshot.jpg)
