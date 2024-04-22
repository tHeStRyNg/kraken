### Kraken - 



#### Instalation 

##### Add the Nvidia Repo and key to access the Nvidia Drivers
```
bash -c 'echo "deb http://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64 /" > /etc/apt/sources.list.d/cuda.list'

apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/3bf863cc.pub

apt update
```


##### Install the required drivers and tooling

```
sudo apt install -y cuda-12-0 cuda-runtime-12-0 cuda-drivers # cuda-drivers-525 libnvidia-gl-525 nvidia-driver-525 libnvidia-extra-525 hashcat
```

##### Reboot 
(optional)

```
reboot now
```

##### check that the Nvidia driver is working correctly

```
nvidia-smi
```

#### Benchmark Hashcat to check everything is installed correctly

```
hashcat -m 1000 --force -b
