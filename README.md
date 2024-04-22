### Kraken

![image](https://github.com/tHeStRyNg/kraken/assets/118682909/14178ce2-4f7a-4c0a-8cce-eef300915a71)

#### Instalation 

##### Check if HW is present

```
root@kraken:~# lspci | grep -i nv
06:00.0 3D controller: NVIDIA Corporation GA100 [A100 PCIe 80GB] (rev a1)
```

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

![image](https://github.com/tHeStRyNg/kraken/assets/118682909/bb4961e7-3219-472d-8a48-c82e3fb1d6e4)

#### Benchmark Hashcat to check everything is installed correctly

```
root@kraken:~# hashcat -I
hashcat (v6.2.5) starting in backend information mode

CUDA Info:
==========

CUDA.Version.: 12.0

Backend Device ID #1 (Alias: #2)
  Name...........: GRID A100D-1-10C MIG 1g.9gb
  Processor(s)...: 14
  Clock..........: 1410
  Memory.Total...: 10235 MB
  Memory.Free....: 8735 MB
  PCI.Addr.BDFe..: 0000:06:00.0

OpenCL Info:
============

OpenCL Platform ID #1
  Vendor..: NVIDIA Corporation
  Name....: NVIDIA CUDA
  Version.: OpenCL 3.0 CUDA 12.0.151

  Backend Device ID #2 (Alias: #1)
    Type...........: GPU
    Vendor.ID......: 32
    Vendor.........: NVIDIA Corporation
    Name...........: GRID A100D-1-10C MIG 1g.9gb
    Version........: OpenCL 3.0 CUDA
    Processor(s)...: 14
    Clock..........: 1410
    Memory.Total...: 10235 MB (limited to 2558 MB allocatable in one block)
    Memory.Free....: 8704 MB
    OpenCL.Version.: OpenCL C 1.2
    Driver.Version.: 525.125.06
    PCI.Addr.BDF...: 06:00.0

OpenCL Platform ID #2
  Vendor..: The pocl project
  Name....: Portable Computing Language
  Version.: OpenCL 2.0 pocl 1.8  Linux, None+Asserts, RELOC, LLVM 11.1.0, SLEEF, DISTRO, POCL_DEBUG

  Backend Device ID #3
    Type...........: CPU
    Vendor.ID......: 128
    Vendor.........: GenuineIntel
    Name...........: pthread-Intel Xeon Processor (Cascadelake)
    Version........: OpenCL 1.2 pocl HSTR: pthread-x86_64-pc-linux-gnu-cascadelake
    Processor(s)...: 2
    Clock..........: 2992
    Memory.Total...: 12927 MB (limited to 2048 MB allocatable in one block)
    Memory.Free....: 6431 MB
    OpenCL.Version.: OpenCL C 1.2 pocl
    Driver.Version.: 1.8

```

Then we benchmark

```
hashcat -m 1000 --force -b
```




