Fix “Unable to locate package” error in Kali Linux.md

.This error is basically due to entries in the sources.list file.
.Open /etc/apt/ using following command:

cd /etc/apt/

.Open the sources.list file using:

sudo nano sources.list

.Now paste the following code at the last line of the file:

deb http://http.kali.org/kali kali-rolling main contrib non-free
# For source package access, uncomment the following line
# deb-src http://http.kali.org/kali kali-rolling main contrib non-free
deb http://http.kali.org/kali sana main non-free contrib
deb http://security.kali.org/kali-security sana/updates main contrib non-free
# For source package access, uncomment the following line
# deb-src http://http.kali.org/kali sana main non-free contrib
# deb-src http://security.kali.org/kali-security sana/updates main contrib non-free
deb http://old.kali.org/kali moto main non-free contrib
# For source package access, uncomment the following line
# deb-src http://old.kali.org/kali moto main non-free contrib

.Write and quit the file using CTRL+O and CTRL+X

.Now just run:

sudo apt-get update
