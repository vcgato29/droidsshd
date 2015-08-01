# Introduction #

While Cyanogen Mod and many other alternative Android ROMs do provide Dropbear binaries, there are many that don't (and I believe it's safe to assume most of the non-rooted/stock images running Android devices out there don't include any kind of SSH support). Therefore, we must provide one of our own... and most likely, it would be probably a good idea to have a portable/static binary.

DISCLAIMER: there are many ways of building/compiling dropbear binaries... what you see on this page is just one of them - if you use any part of the information below, do it at your own risk - **you've been warned!** :-)

# Details #

Here's a few relevant links I came across while searching for how to build it and/or alternatives. So first, a few acknowlegdements:

  * Matt Johnston (author of Dropbear)
    * Dropbear homepage - http://matt.ucc.asn.au/dropbear/dropbear.html
  * CyanogenMod
    * GIT repository - https://github.com/CyanogenMod/android_external_dropbear
    * Dropbear setup instructions - http://wiki.cyanogenmod.com/index.php?title=Howto:_Connect_to_Device_with_SSH
  * Kevin Barry (author of QuickSSHd)
    * Patches and build instructions - http://teslacoilsw.com/dropbear
    * QuickSSHd - http://teslacoilsw.com/quicksshd
    * GIT repository - https://github.com/barryk/android_external_dropbear
  * Jakob Blomer
    * Android experiments, hints, tips and ideas - http://jblomer.web.cern.ch/jblomer/android.htm
    * Patch for Android - http://jblomer.web.cern.ch/jblomer/dropbear0.52-android.patch
  * Danang Wijanarko
    * Blog post with patch and build/setup tips - http://www.bekatul.info/content/sshd-your-android-device
  * Roy Cormier
    * Blog post with patch and build hints - http://roycormier.net/2010/11/02/cross-compiling-dropbear-sshd-for-android/
  * Sourcery ARM EABI Toolkit
    * Download link - http://www.codesourcery.com/gnu_toolchains/arm/download.html

Based on the information I was able to gather, I ended up cooking a solution that involves the last four links above. With that in mind, keep reading to learn how it was built/compiled/done.


## Step 1 ##
Download and deploy the appropriate version of the Sourcery ARM EABI toolkit to your platform. This includes downloading the toolkit, unpacking/deploying and updating your PATH to include the binaries (I've installed on /opt/sourcery, so I've add /opt/sourcery/bin to my PATH)
http://www.codesourcery.com/gnu_toolchains/arm/download.html


## Step 2 ##
Get the source code for Dropbear version 0.52 and unpack it on your computer
http://matt.ucc.asn.au/dropbear/

## Step 3 ##
Download Jakob Blomer's patch from http://jblomer.web.cern.ch/jblomer/dropbear0.52-android.patch and apply it with:
```
cd /path/to/your/dropbear/source
patch < /path/to/downloaded/patch/dropbear0.52-android.patch 
```

## Step 4 ##
Get droidsshd.patch from http://code.google.com/p/droidsshd/downloads/list and apply
```
patch < /path/to/droidssh/patch/droidsshd.patch
```

## Step 5 ##
configure your build
```
./configure --host=arm-none-linux-gnueabi \
--disable-zlib \
--disable-largefile \
--disable-loginfunc \
--disable-shadow \
--disable-utmp \
--disable-utmpx \
--disable-wtmp \
--disable-wtmpx \
--disable-pututline \
--disable-pututxline \
--disable-lastlog \
CC=arm-none-linux-gnueabi-gcc
```
## Step 6 ##
Compile it

```
export STATIC=1 MULTI=1 CC=arm-none-linux-gnueabi-gcc SCPPROGRESS=0 PROGRAMS="dropbear dropbearkey scp dbclient"
make strip
```

## Finally ##

If all goes well, you should end up with a static version of dropbearmulti compiled for ARM:
```
$ ls -1sh dropbearmulti
784K dropbearmulti
$ file dropbearmulti 
dropbearmulti: ELF 32-bit LSB executable, ARM, version 1 (SYSV), statically linked, for GNU/Linux 2.6.16, stripped
$
```