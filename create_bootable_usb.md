To make a bootable USB drive using macOS, perform the following actions:

1) Find the USB drive:
```
diskutil list
```
2) Unmount the USB drive:
```
diskutil unmountDisk /dev/disknumber
```
3) Create bootable media:
```
sudo dd if=/path/to/image.iso of=/dev/rdisknumber bs=1m
```
