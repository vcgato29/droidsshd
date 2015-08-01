# Initial thoughts #

First of all, you should know I'm a big believer in the whole open source universe and the whole community involved on it. With that in mind, let me please congratulate every single person and organization around the globe helping us all out by making their source code of their own projects available, folks that write/publish articles, hints/tips and howtos, (more) experienced people/developers that help out on forums or mailing lists by posting code examples, answering questions, giving suggestions, etc... Such information has been invaluable for a lot of people (like me) over the years!

Anyways: the absolute majority of the source code on this project was written from scratch (in fact, it should be mentioned that DroidSSHd was actually re-written several times since the beginning). DroidSSHd includes pieces/parts or packages from other authors (and some of that code was even updated/tailored/improved to be used on DroidSSHd), but still, there are pieces of DroidSSHd that were _inspired_ by/from a multitude of different places/sources, such as other open source projects, and/or blog/forum posts, etc... you name it :-)

# Credits and Acknowledgements #

I'd like to congratulate and say thanks to (in no particular order):

  * Mario Izquierdo for writing rsyncdroid
    * main inspiration to write DroidSSHd
    * http://code.google.com/p/rsyncdroid/

  * H3R3T1C for posting tutorial "Creating Simple File Chooser"
    * his FileChooser was slighly improved/modified to be used on DroidSSHd (Preferences, Service and Authentication, Authorized/Public Key)
    * http://www.dreamincode.net/forums/topic/190013-creating-simple-file-chooser/

  * Michael Novak for writing/publishing "NumberPicker Widget for Android"
    * NumberPickerPreference, used on DroidSSHd, is based on his NumberPicker
    * http://www.quietlycoding.com/?p=5
    * https://github.com/novak/numpicker-demo

  * Dave Revell for writing SwiFTP (currently unmaintained)
    * Wifi/Wake locks code inspired on/by SwiFTP
    * http://code.google.com/p/swiftp/

  * Kevin Barry for posting ShellCommand, writing QuickSSHd and patches for Dropbear on Android
    * http://www.droidforums.net/forum/android-app-developers/51382-help-something-easy.html
    * http://teslacoilsw.com/dropbear
    * http://teslacoilsw.com/quicksshd
    * 
  * Zeusbox Studio
    * DroidSSHd icons
    * http://www.iconarchive.com/category/funny/gartoon-icons-by-zeusbox.html
    * http://www.zeusboxstudio.com/

  * Friedrich Schaeuffelhut for writing android-openvpn-installer and android-openvpn-settings
    * code for interacting with Android services and daemons inpired on android-openvpn-settings
    * code for InitialSetup on DroidSSHd inspired by android-openvpn-installer
    * http://code.google.com/p/android-openvpn-settings/
    * http://code.google.com/p/android-openvpn-installer/

  * Harald Mue, Ulfada, Bbuxton and Andrew Robinson for android-wifi-tether
    * their NDK/JNI/native code was invaluable as a 'example that actually _works_' when writing our own stuff for DroidSSHd
    * http://code.google.com/p/android-wifi-tether/

If I forgot to mention your name, please drop me a note and this page will be updated accordingly (and forgive me for leaving you out in the first place - thanks!).

# Other interesting/relevant links #

  * Android Dropbear SSHd
    * former name of this project (DroidSSHd)
    * http://code.google.com/p/android-dropbear-sshd/

  * DroidSSHd GIT repository
    * https://github.com/mestre/droidsshd

  * Dropbear SSH server and client
    * http://matt.ucc.asn.au/dropbear/dropbear.html

# See also #

  * Notes on compiling Dropbear
    * http://code.google.com/p/droidsshd/wiki/BuildingDropbear