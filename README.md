# kickstart
## Introduction
 This repo will show my kickstart file for centos7 
## features
- support both mbr and gpt format disk which allows you to use this kickstart file on legacy bios and disk larger than 2TB
 
- default 163 repo
 
- default ipv6 off

- only support legacy bios
## How to Use
- download ks.cfg and unzip centos7 iso 

- copy ks.cfg to the directory of your iso unzipped files

- add new label to the isolinux/isolinux.cfg like this:

```
 label custom
 menu label ^Custom CentOS 7 by Jinxiao2010
 kernel vmlinuz
 append initrd=initrd.img inst.stage2=hd:LABEL=CENTOS7 inst.ks=cdrom:/isolinux/ks.cfg
```
  
- generate a new iso file with following command

```
genisoimage -v -cache-inodes -joliet-long -R -J -T -V CENTOS7 -o /tmp/centos7.iso    \
-c isolinux/boot.cat    -bisolinux/isolinux.bin      \
-no-emul-boot -boot-load-size 4 -boot-info-table    \
-eltorito-alt-boot     -b images/efiboot.img       -no-emul-boot .
```

- then boot your machine with this iso file, it will start automatically installation
