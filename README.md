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


# NVIDIA CUDA Installation (For Ubuntu 18.04)

## Install
Remove existing installations if exist.

>sudo apt --purge remove "cublas*" "cuda*"

>sudo apt --purge remove "nvidia*"


Use installation instructions from [Installation Instructions](https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=deblocal) for local .deb installation.


## Configure 

To configure CUDA envrionments for all users ([Reference](https://www.pugetsystems.com/labs/hpc/How-to-install-CUDA-9-2-on-Ubuntu-18-04-1184))

Create and edit a file 

> gedit /etc/profile.d/cuda.sh

Add following content 

> export PATH=$PATH:/usr/local/cuda/bin

> export CUDADIR=/usr/local/cuda

Create and edit a file 

>gedit /etc/ld.so.conf.d/cuda.conf

Add the following content

> /usr/local/cuda/lib64

Run config
> sudo ldconfig

## Test

CUDA samples can be executed for testing ([Reference](https://www.pugetsystems.com/labs/hpc/How-to-install-CUDA-9-2-on-Ubuntu-18-04-1184))

>mkdir cuda-testing

>cp -a /usr/local/cuda/samples  cuda-testing/

>cd cuda-testing/samples

>make -j4
