# MediaPi+

# Setting up the IR with a clean install of OPENELEC

(These instructions were carried out using a Macbook)
# Pre-requisites

a) You have a micro SD card with OPENELEC installed. For instructions on how to install OPENELEC on a Raspberry Pi please visit the
   Openelec wiki
   
b) You have installed your Raspberry Pi 2 Model B or Raspberry PI B+ and have connected the IR leads to the appropriate GPIO pins (see
   the MEDIAPI+ manual for more information).
   
c) You have downloaded and unzipped the config and mapping files.

d) You have an FTP client installed on your machine. For Windows try WINSCP

e) Setting up your own install of OPENELEC to work with the MEDIAPI+ remote

f) Connect the MEDIAPI+ to a monitor or TV (see manual for details)

g) Connect the MEDIAPI+ to your home network (this guide assumes you are connecting via ethernet directly to your router.

h) Plug in the power and switch on the MEDIAPI+


When OPENELEC first starts it will go through the start up wizard. Ensure that you enable SSH when prompted to choose remote methods of access.
Editing the config file

Open a cmd prompt
Connect via SSH to your MEDIAPI+ by typing:
```
ssh 192.168.1.92 -l root
```

Note: Change the ip address to the relevant address for the MEDIAPI+ on your network.

When prompted enter the password (by default it is openelec).
Make sure you can edit the config file by typing:
  
```mount -o remount,rw /flash```

Open the file for editing with nano:

```nano /flash/config.txt```

Add the following lines to the end of the file:
```
dtoverlay=lirc-rpi
device_tree_overlay=lirc-rpi
```

Then close and save the file by typing CTRL+X then press y (to save your changes) when prompted and hit enter.
Now reset the write permissions by typing:
```
mount -o remount,ro /flash
```
Copying the keymapping files

Start up your ftp client and connect to the MEDIAPI+
```
copy lircd.conf to /storage/.config
copy Lircmap.xml to /storage/.kodi/userdata
```
Note: the .config and .kodi folders are hidden. You may need to enable viewing of hidden folders in your FTP client (please refer to the application help for your specific tool).

Now reboot OPENELEC and your IR and media remote should be working.
