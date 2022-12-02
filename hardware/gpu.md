# GPU hardware 

## Table of contents 

## Install the Nvidia driver

Using graphics-drivers PPA repository allows us to install bleeding edge Nvidia 
beta drivers at the risk of an unstable system. To proceed first add the ppa:graphics-drivers/ppa repository into your system: 

```
sudo add-apt-repository ppa:graphics-drivers/ppa
```

Select a driver and install it via `apt` : 

```
sudo apt install nvidia-driver-510
```

Reboot

```sudo reboot```

### Check the installation 

```nvidia-smi```

## Install cuda 
- Follow the [pre-installation steps](https://developer.nvidia.com/cuda-downloads?target_os=Linux)
- Follow the [installation](https://developer.nvidia.com/cuda-downloads?target_os=Linux)
```
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/cuda-keyring_1.0-1_all.deb
sudo dpkg -i cuda-keyring_1.0-1_all.deb
sudo apt-get update
sudo apt-get -y install cuda
```
Complementary : [Quick start guide](https://docs.nvidia.com/cuda/cuda-quick-start-guide/index.html#ubuntu-x86_64-deb)
```
sudo reboot
export PATH=/usr/local/cuda-11.8/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda-11.8/lib64\
                         ${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
```
- Check the installation 
```nvcc --version```
