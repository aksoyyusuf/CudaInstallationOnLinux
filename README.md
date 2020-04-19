# Ubuntu Installations
Essential Ubuntu installations such as drivers, packages, programs etc. for future self.


# NVIDIA Driver Installation

## Standart Drivers

Detect recommended drivers

>ubuntu-drivers devices

Install all recommended drivers

>sudo ubuntu-drivers autoinstall

Or, install desired driver version only

>sudo apt install nvidia-440

Reboot and you're done

>reboot

## Beta Drivers

Add `ppa:graphics-drivers/ppa`repository

>sudo add-apt-repository ppa:graphics-drivers/ppa

>sudo apt update

Detect recommended drivers 

>ubuntu-drivers devices

Install all recommended drivers

>sudo ubuntu-drivers autoinstall

Or, install desired driver version only

>sudo apt install nvidia-440

Reboot and you're done

>reboot

