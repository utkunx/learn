How to delete GRUB files from a Boot EFI partition in Windows 10.md


# windows 10, usb install disk
# fix, command promont
------------------------------
Step 1
------------------------------
diskpart
list disk

select disk 0

#only volume with fat32, 100 mb

select vol 2
assign letter=N:

exit
------------------------------
Step 2
------------------------------
#The final task involves changing into the Boot EFI folder, 
listing its contents to identify what subfolder the GRUB files would be.

cd /d N:

dir

dir EFI

cd EFI

dir

rmdir /S kali?-or-other-linux 
Y (yes)

dir
#result should, 

Boot  
Microsoft
------------------------------------------
