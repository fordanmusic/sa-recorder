# sa-recorder
Sound Activated Recorder on RPI

# setup passwordless ssh
1. Get Raspberry Pi Imager (https://www.raspberrypi.org/downloads/)
1. Image SD card (pref 32GB) with Raspberry Pi OS Litefrom PC or laptop
1. Create "wpa_supplicant.conf" in image root (`touch /media/YOURNAME/boot/wpa_supplicant.conf`)
  - Write contents under \# wpa_supplicant to this file (see below)
  - Adjust ISO 3166 alpha-2 country code, network name and network password (`nano /media/YOURNAME/boot/wpa_supplicant.conf`)
1. Create “ssh” (empty) file in image root (`touch /media/YOURNAME/boot/ssh`)
1. Insert SD card & power Pi
  - Wait ~2 min for Pi to boot up
1. Find IP allocated to Pi (see DHCP table in router; try 192.168.1.1 to interface with router)
1. Write contents under \# ssh config to ~/.ssh/config (see below)
  - Adjust IP accordingly
  - You can choose another name as host
1. Generate an ssh key if you have none (`ssh-keygen -t rsa -b 4096`; passphrase not necessary)
1. Copy the public key to Pi via `ssh-copy-id muzmachine`
  - default password is 'raspberry'
1. Log in to Pi via `ssh muzmachine`
1. Disable password login via `sudo nano /etc/ssh/sshd_config`
  - Change to 'no' the following (uncomment lines if necessary):
    - ChallengeResponseAuthentication no
    - PasswordAuthentication no
    - UsePAM no

# extra security steps
1. Change Pi's default password via `sudo raspi-config`
  - You can also change:
    - Network name of Pi
    - Locale & Timezone
    - Update Pi
1. 
1. You can add a user via `sudo adduser alice`
  - If you do, also change user in ~/.ssh/config
    
    
# wpa_supplicant.conf

```
country=US
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="NETWORK-NAME"
    psk="NETWORK-PASSWORD"
}
```

# ssh config

```
host muzmachine
        hostname 192.168.1.10
        user pi
```

# sources

https://desertbot.io/blog/headless-raspberry-pi-3-bplus-ssh-wifi-setup
https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md
https://www.raspberrypi.org/documentation/configuration/security.md
https://www.ssh.com/ssh/keygen/
