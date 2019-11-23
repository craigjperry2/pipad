# Pi Companion

A portable linux companion for my iPad Pro.

## Getting Started

Burn the latest raspbian lite image onto an SD Card. Balena etcher is a
reasonable tool on windows for this.

Create an empty file called `ssh` in the boot dir of the new SD.

Create a file called `wpa-supplicant.conf` in the boot dir of the new SD with
the WiFi connection details. It's possible to configure multiple networks to
try in order. Something like:

    ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
    update_config=1
    country=GB

    network={
      priority=30
      ssid="Phone"
      psk="???"
      key_mgmt=WPA-PSK
      id_str="phone"
    }

    network={
      priority=50
      ssid=“Home"
      psk="???"
      key_mgmt=WPA-PSK
      id_str="home"
    }

Boot the device, then reboot the device for all initial setup to take effect.

Run the following commands:

    sudo apt update && sudo apt upgrade
    sudo apt install ansible

Now run the following command to bootstrap the instance:

    sudo ansible-playbook pi-companion.yml

