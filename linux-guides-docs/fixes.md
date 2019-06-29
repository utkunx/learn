
# Fix “Unable to locate package” error in Kali Linux

* A
  * .This error is basically due to entries in the sources.list file.
  * .Open /etc/apt/ using following command:
  * cd /etc/apt/
  * .Open the sources.list file using:
  * sudo nano sources.list
  * .Now paste the following code at the last line of the file:
  * deb http://http.kali.org/kali kali-rolling main contrib non-free
  * For source package access, uncomment the following line
  * deb-src http://http.kali.org/kali kali-rolling main contrib non-free
  * deb http://http.kali.org/kali sana main non-free contrib
  * deb http://security.kali.org/kali-security sana/updates main contrib non-free
  * For source package access, uncomment the following line
  * deb-src http://http.kali.org/kali sana main non-free contrib
  * deb-src http://security.kali.org/kali-security sana/updates main contrib non-free
  * deb http://old.kali.org/kali moto main non-free contrib
  * For source package access, uncomment the following line
  * deb-src http://old.kali.org/kali moto main non-free contrib
  * .Write and quit the file using CTRL+O and CTRL+X
  * .Now just run:
  * sudo apt-get update

# How to delete GRUB files from a Boot EFI partition in Windows 10

* A
  * windows 10, usb install disk
  * fix, command promont
    * `diskpart`
      * `list disk`
      * `select disk 0`
      * only volume with fat32, 100 mb
      * `select vol 2`
      * `assign letter=N:`
      * `exit`
    * The final task involves changing into the Boot EFI folder, 
listing its contents to identify what subfolder the GRUB files would be.
      * `cd /d N:`
      * `dir`
      * `dir EFI`
      * `cd EFI`
      * `dir`
      * `rmdir /S kali?-or-other-linux`
      * `Y (yes)`
      * `dir`
      * result should;
        * Boot
        * Microsoft

# How to fix “chown: invalid group:” if the user does not exist on the running system?

* A
  * I want to fix permissions on another disk with chown. Set the permissions to a user which does not exist on the system which is currently running.
  * Use the numerical UID/GID instead of the user/group name.
    * You can find the UID/GID on the system the disk belongs to by using
    * `id some_username`
    * `ls -ln some_file`
    * where some_file is a file that belongs to user you are looking for

* so basiccly ;
    * `sudo chown -R $USER:$USER .` does not WORK.
    * `sudo chown -R 1001:1001 .` does work

# intel microcode

Processor Model | Stepping | Identifier(Stepping F-MO-S/PI) | Version (Old->New)| Products |
|----|-----|-----|-----|-----|
| CFL-H/S/E3 | U0 | 6-9e-a/22 | 000000aa->000000b4 | Core Gen8 Desktop, Mobile, Xeon E |

* if a processor signature is 0x000906eb, it means
Family=0x006, Model=0x9e and Stepping=0xb

  * to 0x000906ea
    * signature | family | model | stepping
      ----|-----|-----|-----|-----
      0x000906eb | 0x006 | 0x9e | 0xb
      0x000906ea | 0x006 | 0x9e | 0xa ?

# How to give new UUID to a partition on disk procedure ? 

   * `e2fsck -f /dev/nvme1n1p7` first run it check filesystem (mantetory for tune2fs to work)
   * `tune2fs -U $(uuidgen) /dev/nvme1n1p7` then run it give new UUID to that partition...
     * `blkid` list all partitions labels and UUID's
	 * `/dev/nvme0n1: PTUUID="c3901cef-7db3-6843-a8e2-1166aa043855" PTTYPE="gpt"`
     * `fstab(5)` fstab filesystem mount points manager
	 * `/etc/fstab` where the the file stored.
---

| `commands`  | extra param  | into |
| :------------ |:---------------:| -----:|
| `e2fsck`      | -f /dev/nvme1n1p7 | it must be runned to `tune2fs` work later... |
| `tune2fs`      | -U $(uuidgen) /dev/nvme1n1p7        |   $12 |
| zebra stripes | are neat        |    $1 |

# print boot logs

* `journalctl -b`
