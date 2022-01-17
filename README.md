# CUDA Installations
CUDA installation on Ubuntu


# NVIDIA Driver Installation

## Standart Drivers

Detect recommended drivers
```sh
$ ubuntu-drivers devices
```

Install all recommended drivers

```sh
$ sudo ubuntu-drivers autoinstall
```

Or, install desired driver version only

```sh
$ sudo apt install nvidia-440
```

Reboot and you're done
```sh
$ reboot
```

## Beta Drivers

Add ppa repository

```sh
$ sudo add-apt-repository ppa:graphics-drivers/ppa
$ sudo apt update
```

Detect recommended drivers 
```sh
$ ubuntu-drivers devices
```

Install all recommended drivers
```sh
$ sudo ubuntu-drivers autoinstall
```

Or, install desired driver version only
```sh
$ sudo apt install nvidia-440
```

Reboot and you're done
```sh
$ reboot
```

# NVIDIA CUDA Installation (For Ubuntu 18.04)

## Install
Verify if gcc is installed.
```sh
$ gcc --version
```
Install gcc only
```sh
$ sudo apt install gcc
```

Or, install essential packages that includes gcc and additional libraries
```sh
$ sudo apt install build-essential
```

Remove existing installations if exist.

**Option 1**

```sh
$ sudo apt --purge remove "cublas*" "cuda*"
$ sudo apt --purge remove "nvidia*"
```
**Option 2**

```sh
$ sudo /usr/local/cuda-10.2/bin/cuda-uninstaller
$ sudo /usr/bin/nvidia-uninstall
```

Use installation instructions from [Installation Instructions](https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=deblocal) for local .deb installation.


## Configure 

To configure CUDA envrionments for all users ([Reference](https://www.pugetsystems.com/labs/hpc/How-to-install-CUDA-9-2-on-Ubuntu-18-04-1184))

Create and edit a file 
```sh
$ gedit /etc/profile.d/cuda.sh
```

Add following content 
```sh
export PATH=$PATH:/usr/local/cuda/bin
export CUDADIR=/usr/local/cuda
```

Create and edit a file 
```sh
$ gedit /etc/ld.so.conf.d/cuda.conf
```

Add the following content
```sh
/usr/local/cuda/lib64
```

Run config
```sh
$ sudo ldconfig
```

## Test

Check nvcc version. NVCC is proprietary CUDA Compiler.

```sh
$ nvcc --version
```

CUDA samples can be executed for testing ([Reference](https://www.pugetsystems.com/labs/hpc/How-to-install-CUDA-9-2-on-Ubuntu-18-04-1184))

```sh
$ mkdir cuda-testing
$ cp -a /usr/local/cuda/samples  cuda-testing/
$ cd cuda-testing/samples
$ make -j4
```

Run a sample 

```sh
$ cd cuda-testing/samples/bin/x86_64/linux/release
$ ./vectorAdd
```
