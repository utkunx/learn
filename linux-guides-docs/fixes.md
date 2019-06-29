
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
