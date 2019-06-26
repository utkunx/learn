23 may, 2019, attempt 3333.
----------------


--------------------------------
## https://www.ostechnix.com/arch-linux-2016-post-installation/

# before start;
--------------------------------
https://lampjs.wordpress.com/2017/01/19/easy-installing-arch-linux-dual-boot-with-windows-uefi-or-mbr-for-beginners/
https://www.tecmint.com/arch-linux-installation-and-configuration-guide/

## usb burn image on windows settings;

install Rufus utility to make your arch linux bootable usb.
If you want to install arch linux in uefi mode then in rufus select “GPT Partition Scheme for UEFI”.
It is recommended that your windows installation should be also in UEFI mode if you are installing linux in UEFI Mode.
```
rufus settings;
# partition scheme, GPT
# target system UEFI(non CSM)
# write in DD image mode.
```
----------------------------------------
## steps sums;

Set up partitions, pacstrap, chroot, set locales, hostname, root password, user setup, and then it's as simple as setting up packages

| step number | command | description | extrainfo? 
| -------------|:--------:|:----------:|:-----------:|
| 0.0 | setfont latarcyrheb-sun32     | 4k display, HiDPI screen      | To make this setting persistent after installation, create /etc/vconsole.conf with the following content:
```
# /etc/vconsole.conf
FONT=latarcyrheb-sun32
```        |
| partitions   | sda1     | 500 MB     | ntfs        |
| pacstrap     | sda2     | 100 MB     | vfat        |
| chroot       | sda3     | 16 MB      | ?           |
| set locales  | sda4     | 80 GB      | ntfs        |
| hostname     | sda1     | 500 MB     | ntfs        |
| root password| sda2     | 100 MB     | vfat        |
| user setup   | sda3     | 16 MB      | ?           |

| ...          | sda1     | 500 MB     | ntfs        |
| ...          | sda2     | 100 MB     | vfat        |
| ...          | sda3     | 16 MB      | ?           |
| ...          | sda4     | 80 GB      | ntfs        |







| steps        | descirip | command    | >?????????? |
| -------------|:--------:|:----------:|:-----------:|
| hw pre config | sda4     | 80 GB      | ntfs        |
| partitions   | sda1     | 500 MB     | ntfs        |
| pacstrap     | sda2     | 100 MB     | vfat        |
| chroot       | sda3     | 16 MB      | ?           |
| set locales  | sda4     | 80 GB      | ntfs        |
| hostname     | sda1     | 500 MB     | ntfs        |
| root password| sda2     | 100 MB     | vfat        |
| user setup   | sda3     | 16 MB      | ?           |

| ...          | sda1     | 500 MB     | ntfs        |
| ...          | sda2     | 100 MB     | vfat        |
| ...          | sda3     | 16 MB      | ?           |
| ...          | sda4     | 80 GB      | ntfs        |








-on thinkpad p1 basis;
```
setfont latarcyrheb-sun32
wifi-menu
ping -c 3 www.google.com
```
then;;;



1     partitions

lsblk
fdisk -l

we neeed 3 partition
efi system partition (windows efi location, mine is, nvme1n1p1)
swap partition, swap on
root partition
home partition?

we use cfdisk command to create disk layout

cfdisk /dev/nvme0n1p;
#select label type ?
gpt

then create swap;
new partition ; type linux swap
30g

then /root
linux filesystem; 30g

write,quit

check it out 
fdisk -l

# mkfs.fat -F32 /dev/sda1 (we dont need this, windows have aldready done it)
mkfs.ext4 /dev/nvme0n1p1 (for root)
mkfs.ext4 /dev/nvme0n1p3 (for home???)
mkswap /dev/nvme0n1p2 (for swap)

-----------------------------------
mount, install arch linux

mount /dev/nvme0n1p1 /mnt (mount the root to /mnt location)
ls /mnt 
swapon /dev/nvme0n1p2 (activate swap)

increase install speed;;;
nano /etc/pacman.d/mirrorlist
[multilib]
Include = /etc/pacman.d/mirrorlist
write,quit.

installllllll;;;;;
pacstrap /mnt base base-devel  (20 min ???)

generate fstab;
genfstab -U -p /mnt >> /mnt/etc/fstab
cat /mnt/etc/fstab  (inspect it)

in order to configure Arch Linux;;;
arch-chroot /mnt
echo "archbox" > /etc/hostname

nano /etc/locale.gen
en_US.UTF-8 UTF-8 (remove #)
en_US ISO-8859-1  (remove #)
write,quit.

locale-gen
echo LANG=en_US.UTF-8 > /etc/locale.conf
export LANG=en_US.UTF-8

ls /usr/share/zoneinfo/
ln -s /usr/share/zoneinfo/Europe/Bucharest /etc/localtime

hwclock --systohc --utc
----------------------
nano /etc/pacman.conf
multilib un comment it;;;;;

Yaourt package tool
add to bottom 
[archlinuxfr]
SigLevel = Never
Server = http://repo.archlinux.fr/$arch
write, quit...

pacman -Syu (synchronize and update database mirrors )

passwd
useradd -mg users -G wheel,storage,power -s /bin/bash your_new_user
passwd your_new_user
chage -d 0 your_new_user

-------------
22. After the newly user has been added you need to install the sudo package 
and update the wheel group line from /etc/sudoers file in order to grant root
privileges to the newly added user.

pacman -S sudo
visudo

Add this line to /etc/sudoers file:
%wheel ALL=(ALL) ALL

------------------
last step;;;;;
install bootloader

pacman -S grub efibootmgr dosfstools os-prober mtools
mkdir /boot/EFI
mount /dev/nvme1n1p1 /boot/EFI  (efi location)
grub-install --target=x86_64-efi  --bootloader-id=grub_uefi --recheck

25. Finally, create the GRUB configuration file by issuing the following command.
grub-mkconfig -o /boot/grub/grub.cfg

Congratulations! Arch Linux is now installed and configured for your box. 
exit
umount -a
telinit 6

Set up partitions, pacstrap, chroot, set locales, hostname, root password, user setup, and then it's as simple as setting up packages

1     partitions
2     pacstrap
3     chroot
4     set locales
5     hostname
6     root password
7     user setup

----------------------------------------
1     partitions
----------------------------------------
(root,swap,home)
First thing is to identify your existing disk partitions
lsblk

(To create a disk, type)
fdisk /dev/sda  
(Type “n” for a new partition)
n 
(Type in “p” for a primary partition)
p
(partition number ?)
1
(last sector+ ?)
+10G

(this created new partisions for /(root))
(create 2 more...(swap,home))
(Create two more partitions similarly for home and swap, and press ‘w‘ to save the changes and exit.)

------------------------------------
creating filesystem,,,
(root,swap,home)

(root, mkfs, sda1)
(swap, mkswap, sda2)
(home, mkfs, sda3)

mkfs.ext4 /dev/sda1
mkfs.ext4 /dev/sda3

mkswap /dev/sda2
swapon /dev/sda2

mount partitions,,,
(mount, root and home)

mount /dev/sda1 /mnt
mkdir /mnt/home
mount /dev/sda3 /mnt/home

install,,,

let’s install the base package
pacstrap /mnt base base-devel

,Configuring the system

genfstab -U /mnt >> /mnt/etc/fstab
arch-chroot /mnt
exit

,Setting Timezone

ln -sf /usr/share/<zoneinfo>/<Region>/<City> /etc/localtime
ls /usr/share/zoneinfo
hwclock --systohc --utc

,Setting up Locale

Now generate the locale config in /etc directory file using the commands below:
locale-gen
echo LANG=en_GB.UTF-8 > /etc/locale.conf
export LANG=en_GB.UTF-8

Installing bootloader, setting up hostname and root password,,,

Create a /etc/hostname file and add a matching entry to host.

127.0.1.1 myhostname.localdomain myhostname

To install a bootloader use below commands :
pacman -S grub
grub-install /dev/sda
grub-mkconfig -o /boot/grub/grub.cfg

To create root password, type
passwd

Once done, update your system. Chances are that you already have an updated system 
since you have downloaded the latest ISO file.

pacman -Syu
Congratulations! You have successfully installed a minimal command line Arch Linux.

In the next step, we will see how to set up a desktop environment or Graphical User Interface for the Arch Linux

Install a desktop environment (GNOME in this case),
Before you can install a desktop environment, you will need to configure the network first.!!!!!!!!!111

ip link
ping -c 3 www.google.com
wifi-menu

vi /etc/systemd/network/enp0s3.network
[Match]
name=en*
[Network]
DHCP=yes
Save and exit. 

Restart your systemd network for the changes to reflect.
systemctl restart systemd-networkd
systemctl enable systemd-networkd

And then add the below two entries in /etc/resolv.conf file.
nameserver 8.8.8.8
nameserver 8.8.4.4

Next step is to install X environment.
Type the below command to install the Xorg as display server.
pacman -S xorg xorg-server

gnome contains the base GNOME desktop. gnome-extra contains GNOME applications, 
archive manager, disk manager, text editors and more.

pacman -S gnome gnome-extra

The last step includes enabling the display manager GDM for Arch.
systemctl start gdm.service
systemctl enable gdm.service

Restart your system and you can see the GNOME login screen. !!!!!!!!!!!!!!





#INSTALL ARCH

pacstrap -i /mnt base

# GENERATE MOUNT CONFIGURATION FILE

genfstab -U -p /mnt >> /mnt/etc/fstab
nano /mnt/etc/fstab

# SWITCHING FROM USB TO ARCH ROOT ON YOUR SYSTEM

arch-chroot /mnt /bin/bash

# BOOT LOADER CONFIGURATION

pacman -S grub efibootmgr

ount /dev/sda1 /boot (Mount the efi file system partition, for example it is /dev/sda2)

# Install Grub

grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=GRUB

pacman -S os-prober
mkdir /mnt/windows10
mount /dev/sda2 /mnt/windows10
grub-mkconfig -o /boot/grub/grub.cfg