# NVIDIA Docker on ppc64le

## Compilation
This repository gives basic support for nvidia-docker on ppc64le.

Please note that in current, nvidia-docker and nvidia-docker-plugin tool compilation are ported to ppc64le only. Nvidia docker images building has not been ported yet. You need to port your dockerfile to ppc64le by yourself.

To build deb packages, please follow these steps:
```sh
# Build golang 1.6.3 image. golang 1.5 on ppc64le has a "relocation truncated" bug to build nvidia-docker.
make build-golang

# Build deb package for nvidia-docker and nvidia-docker-plugin
make deb
```
After compilation, following the printed message to find the deb package.

## Installation
```sh
# Install nvidia-docker package
dpkg -i nvidia-docker-<release>.deb

# One-time setup
sudo nvidia-docker volume setup
```

# NVIDIA Docker

This repository includes utilities to build and run NVIDIA Docker images.

![nvidia-gpu-docker](https://cloud.githubusercontent.com/assets/3028125/12213714/5b208976-b632-11e5-8406-38d379ec46aa.png)

> Example of how CUDA integrates with Docker

# Documentation

The full documentation is available on the [repository wiki](https://github.com/NVIDIA/nvidia-docker/wiki).  
A good place to start is to understand [why NVIDIA Docker](https://github.com/NVIDIA/nvidia-docker/wiki/Why%20NVIDIA%20Docker) is needed in the first place.

# Quick start

Assuming the NVIDIA drivers and Docker are properly installed (see [installation](https://github.com/NVIDIA/nvidia-docker/wiki/Installation)), there are two ways to install NVIDIA Docker:

### Plugin install (Recommended)

##### _Ubuntu distributions_
```sh
# Install nvidia-docker and nvidia-docker-plugin
wget -P /tmp https://github.com/NVIDIA/nvidia-docker/releases/download/v1.0.0-rc/nvidia-docker_1.0.0.rc-1_amd64.deb
sudo dpkg -i /tmp/nvidia-docker_1.0.0.rc-1_amd64.deb && rm /tmp/nvidia-docker*.deb

# Test nvidia-smi
nvidia-docker run --rm nvidia/cuda nvidia-smi
```

##### _Other distributions_
```sh
# Install nvidia-docker and nvidia-docker-plugin
wget -P /tmp https://github.com/NVIDIA/nvidia-docker/releases/download/v1.0.0-rc/nvidia-docker_1.0.0.rc_amd64.tar.xz
sudo tar --strip-components=1 -C /usr/bin -xvf /tmp/nvidia-docker_1.0.0.rc_amd64.tar.xz && rm /tmp/nvidia-docker*.tar.xz

# Run nvidia-docker-plugin
sudo -b nohup nvidia-docker-plugin > /tmp/nvidia-docker.log

# Test nvidia-smi
nvidia-docker run --rm nvidia/cuda nvidia-smi
```

### Standalone install
```sh
# Install nvidia-docker and nvidia-docker-plugin
wget -P /tmp https://github.com/NVIDIA/nvidia-docker/releases/download/v1.0.0-rc/nvidia-docker_1.0.0.rc_amd64.tar.xz
sudo tar --strip-components=1 -C /usr/bin -xvf /tmp/nvidia-docker_1.0.0.rc_amd64.tar.xz && rm /tmp/nvidia-docker*.tar.xz

# One-time setup
sudo nvidia-docker volume setup

# Test nvidia-smi
nvidia-docker run --rm nvidia/cuda nvidia-smi
```

# Issues and Contributing

**A signed copy of the [Contributor License Agreement](https://raw.githubusercontent.com/NVIDIA/nvidia-docker/master/CLA) needs to be provided to digits@nvidia.com before any change can be accepted.**

* Please let us know by [filing a new issue](https://github.com/NVIDIA/nvidia-docker/issues/new)
* You can contribute by opening a [pull request](https://help.github.com/articles/using-pull-requests/)
