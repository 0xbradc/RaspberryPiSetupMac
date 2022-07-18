# RaspberryPiSetupMac
Easy setup instructions for Mac OSX. This was created due to the surprisingly sparse or convoluted documentation currently available for the setup of Raspberry Pi machines on Mac. 



# Getting Started
1. Purchase a Micro-SD card over 8GB.
2. Download the [Raspberry Pi Imager](https://www.raspberrypi.org/downloads/) to your Mac.
3. Download the [VNC Viewer](https://www.realvnc.com/en/connect/download/viewer/macos/) to your Mac.



# Setting Up the Raspberry Pi
1. Plug the SD card into your computer.

2. Download, install, and run the [Raspberry Pi Imager](https://www.raspberrypi.org/downloads/) into the directory of your choice.

3. Open the application and click `CHOOSE OS`. Select the first option for `Raspberry Pi OS (32-bit)`.

4. Click `CHOOSE STORAGE` and find the SD card that you have set aside for the Raspberry Pi to run on. 

5. Click `WRITE`. This will most likely take several minutes.

6. Within the root directory of the SD card, create an empty text file called `ssh`. This will allow connections to the Raspberry Pi via SSH.

7. Within the root directory of the SD card, create a file called `wpa_supplicant.conf`. Within this file, add the following code:
  ```
  country=US
  ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
  update_config=1

  network={
  scan_ssid=1
  ssid="your_wifi_ssid"
  psk="your_wifi_password"
  } 
  ```
  Be sure to change `your_wifi_ssid` to your connection's SSID (usually the name of the network) as well as `your_wifi_password` to the corresponding WIFI password. Instead of this file, it is possible to connect with an ethernet connection. The internet has some resources on this process.

8. With all file changes saved, you may now eject the SD card. Proceed to insert it into the Raspberry Pi. Also, ensure that your Raspberry Pi is plugged into a power source and within range of the WIFI network you configured earlier.

9. Open a Terminal shell on your OSX. Type the following command:
  ```
  ssh pi@raspberrypi.local
  ```
  
10. There should be a prompt for a password. This is going to be "raspberry" by default. If you are connecting from a different SSH client, the username of the system is "pi" by default.

11. In order to view the GUI for Raspberry Pi, we can use [VNC Viewer](https://www.realvnc.com/en/connect/download/viewer/macos/). Open VNC Viewer and enter "raspberrypi.local" in the top input bar. Click `Connect To` in order to establish the connection.

12. Go through the necessary setup instructions on the Raspberry Pi SSH GUI and begin using your new tool!



# Other Useful Pieces of Information
1. In order to send an entire directory/folder through SSH, perform the following command.
  ```
  scp -r path/to/local/dir pi@raspberrypi.local:/path/to/remote/dir
  ```



# Resources
[Tom's Hardware](https://www.tomshardware.com/reviews/raspberry-pi-headless-setup-how-to,6028.html)

[SSH](https://www.ssh.com/academy/ssh/putty/mac)

[Raspberry Pi Imager](https://www.raspberrypi.org/downloads/)

[VNC Viewer](https://www.realvnc.com/en/connect/download/viewer/macos/)

