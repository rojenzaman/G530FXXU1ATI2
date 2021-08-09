## SM-G530FQ - Bloatware Removed [STOCK ROM]

<img alt="Samsung Galaxy Grand Prime" src="grandprime.png" height="230" />

 - See removed files: [bloatware-list.txt](bloatware-list.txt).

 - If you want to download the original stock rom visit the wayback archive: [TUR-G530FXXS1ARK2-20210203212229.zip](https://web.archive.org/web/20210809141245/https://ftp.rojenz.de/fortunalte/TUR-G530FXXS1ARK2-20210203212229.zip).

### INSTALL

Just flash these files with [heimdall](https://github.com/Benjamin-Dobell/Heimdall) on bootloader mode:

```bash
heimdall flash --BOOT boot.img --RECOVERY recovery.img --SYSTEM system.img.ext4
```

Specify the `--RECOVERY recovery_twrp-3.5.2.img` to install TWRP.


### EDIT ROM:

#### Unpack

Convert android sparse image to ext4 image as using [simg2img](https://github.com/anestisb/android-simg2img):

```bash
simg2img system.img.ext4 system.img
```

Mount to `system/` directory:


```bash
mount system.img system/
```

Then edit files:

```bash
cd system/
```


#### Repack

Convert ext4 image to android sparse image as using [img2simg](https://github.com/anestisb/android-simg2img):

```bash
img2simg system.img system.img.ext4
```

OR:

```bash
dd if=/dev/zero of=system-new.img status=progress bs=1M count=1024
mount system-new.img system-new/
rsync -avz system/ system-new/
umount system-new/
```

```bash
img2simg system-new.img system.img.ext4	
```
