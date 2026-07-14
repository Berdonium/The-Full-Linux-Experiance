# The-Full-Linux-Experiance
A full description of my linux experiance constantly updating based on what im doing and figuring out.

## Distro Suggestions

✅ = Yes
🟠 = Kinda
❌ = No

| Distros | Just Works | Customizable | Bloated | First Looks |
| ------- | ---------- | ------------ | ------- | ----------- |
| Nobara  |     ✅     |      ❌      |    🟠   |      ✅     |
| Mint    |     ✅     |      ❌      |    ✅   |      🟠     |
| Fedora  |     🟠     |      🟠      |    ✅   |      ✅     |
| Arch    |     ❌     |      ✅      |    ❌   |      ❌     |

## Installation
To start preperation in windows or mac open the partion manager or disk management and create a new partion allocate as much space as you want. Download Ventoy from [here](https://sourceforge.net/projects/ventoy/files/v1.1.16/ventoy-1.1.16-windows.zip/download) and extract it. Now open Ventoy2Disk, select your usb drive and hit the install(remove all media from the drive). Download the .iso file for your distro of choice and choose a Desktop Enviorment(e.g. Plasma). Put that on the drive then try to find the change boot order key for your motherboard or laptop. restart your computer whilst holding that key then once you enter that menu select your usb drive, select the desired os and then the installation starts.

### Nobara / Mint
After booting to the usb select the language time zone etc but pay attension to the select a drive part. MAKE SURE TO CHOOSE THE RIGHT PARTION! you can do this by looking at the partion size and make sure it matches the partion you setup. select that hit install and wait now reboot hit that change boot order key again and click the new option this will open nobara and now it installed.

### Fedora
No tutorial yet.

### Arch
I installed Arch the easy way, you probably should too. Heres how to install it. Along side the iso from the arch website you will also have download the .iso.sig and put that on the ventoy drive. Once you've enter the iso select the first option, then connect wifi or if your connected to ethernet you can skip this step. The easiest way to do this is to run 
```
ip link
```
This will show you your wifi adapter. Its the last one highlighted in blue. Then run 
```
station your-wifi-adapter connect "network-ssid"
```
After you run this it will prompt you for the wifi password, just enter it. Now lets reconfigure your disk. First run 
```
lsblk
```
If anything under the name of nvme0n1 appears that is probably the disk you partioned so find the correct partion (probably the one with the biggest number at the end). Then run 
```
cfdisk /dev/disk-name
```
This will open a TUI that can be used for disk configuration. After running it, hit the free space section and allocate 1 GB. select this new partion and hit change type, change it to EFI. Now hit the write then quit. The final step is to set the partion filesystems. Use the command 
```
mkfs.ext4 /dev/main-linux-partion-name
```
Then 
```
mkfs.fat -F32 /dev/linux-efi-partion-name
```
There, we have finished pationing the drives. Now lets mount it, run 
```
mkdir /mnt/boot
```
Then 
```
mount /dev/main-linux-partion /mnt
```
And 
```
mount /dev/efi-linux-partion /mnt/boot
```
Finally we finished partioning the drive, now lets install arch. Run 
```
pacman -Syu
```
Then 
```
pacman -S archinstall
```
Now finally run 
```
archinstall
```
Skip the part about locales and skip straight to the mirror part, select the country closest to you. For the disk part select mounted partion and type `/mnt` skip the Swap section and go to bootloader, select grub its the best one. Skip uinified kernel images. Skip host name, for root password skip root password but create a user and password. MAKE YOUR SELF A SUPER USER IT IS VERY IMPORTANT. For profile you can choose whatever you want(if your new use kde plasma or gnome). Then select open source drivers because its most likely to work. For audio choose pulse audio. For kernal images select linux and linux lts so if one fails you always have a second. For network select copy iso. For additional pkgs select things from pacman like git, firefox, and code. Finally select your timezone and hit install then yes and wait. After waiting hit reboot and spam the change boot order key and select arch if arch is not there hit any thing that is not windows boot manager. Finally its installed you can now say I Use Arch btw.

### The Distro I Use
Currently i use Arch btw and i LOVE IT. It is now for begginers or people who want it to just work but its amazing for me. Im a kid with tons of free time and nothing important on my pc so if it breaks its ok. I LOVE the customization and the aur. Arch is like building a PC, if something doesnt work there are other components but they mst be compatible. Anyways Arch has so many variables that anything can happen and anything can break. But good for me I love fixing tech problems. Sadly Arch probably is not for you specifically if you need something reliable beacause Arch is for experimenters if not its not for you.

