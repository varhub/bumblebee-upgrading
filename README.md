bumblebee-upgrading
===================

Bumblebee requires to specify exact version of nvidia driver at 
`/etc/bumblebee/bumblebee.conf`:

```
## Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia-352
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-352:/usr/lib32/nvidia-352:/usr/lib/nvidia-352/vdpau
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-352/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia
```

In order to simplify this process, here you are *bumblebee-update-driver*, 
which will set last version of nvidia driver. You can also specify a fixed 
version:
`./bumblebee-update-driver [nvidia-352]`


State: beta
Master: https://github.com/varhub/bumblebee-upgrading.git



# Throubleshooting

## nvidia-xxx nvidia-current
Bumblebee brings upgrade compatibility through *nvidia-current*. If you need 
newer driver, you should change `bumblebee.conf` file or tweak `bumblebee-update-driver`.

## Failed to open VDPAU backend libvdpau_nvidia.so
Ensure that LibraryPath (bumblebee.conf) includes `/usr/lib/nvidia-xxx/vdpau`.
Otherwise just make a symlink `/usr/lib/nvidia-xxx$ sudo ln -s vdpau/libvdpau_nvidia.so`
