# GPU hardware 

### Install the Nvidia driver

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
