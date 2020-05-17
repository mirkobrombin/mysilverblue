# System

## RPMFusion
In Silverblue procedure is a little bit different compared to Fedora Workstation and should be done via rpm-ostree:
```bash
sudo rpm-ostree install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

## NVIDIA
Package installations (RPM Layers) should be done with rpm-ostree`.
```bash
sudo rpm-ostree install akmod-nvidia xorg-x11-drv-nvidia
```
after installation we are going to blacklist nouveau and enable modeset to nvidia:
```bash
sudo rpm-ostree kargs --append=rd.driver.blacklist=nouveau --append=modprobe.blacklist=nouveau --append=nvidia-drm.modeset=1
```

### CUDA (optional)
```bash
sudo rpm-ostree install akmod-nvidia xorg-x11-drv-nvidia-cuda
```

### NVENC/NVDEC (optional)
```bash
sudo rpm-ostree install xorg-x11-drv-nvidia-cuda-libs
```
