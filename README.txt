# linuxGuide

sudo apt-get install vlc              mp4 player

https://apps.ubuntu.com/cat/applications/audacious/       mp3 Audacious

netBeans   recomended JDK7
after dawnload
For Linux platforms, the installer file has the .sh extension. For these platforms, you need to make the installer files executable by using the following command: chmod +x <installer-file-name>. Type ./<installer-file-name> to run the installer.

sudo apt-get update
sudo apt-get upgrade    -update

netbeans freezing moduls
This is the answer
http://askubuntu.com/questions/689291/netbeans-8-0-2-freezing-at-startup-on-ubuntu-15-10-64bit/691652#691652
To make it work with OpenJDK 8, edit /etc/java-8-openjdk/accessibility.properties and comment out the line "assistive_technologies=org.GNOME.Accessibility.AtkWrapper", as suggested here: https://bugs.launchpad.net/ubuntu/+source/openjdk-8/+bug/1510009.
In my case
sudo pico /etc/java-7-openjdk/accessibility.properties


In case user doesn't have the permission to delete the folder:
Add sudo at the beginning of the command :
sudo rm -rf folderName


How to remove Ubuntu
on an installation media CD. Click "Repair your computer" 

Open the Command Prompt, then type bootrec /fixmbr into the Command Prompt.


Installing Java with apt-get is easy. First, update the package index:
sudo apt-get update
Then, check if Java is not already installed:
java -version
If it returns "The program java can be found in the following packages", Java hasn't been installed yet, so execute the following command:
sudo apt-get install default-jre
This will install the Java Runtime Environment (JRE). If you instead need the Java Development Kit (JDK), which is usually needed to compile Java applications (for example Apache Ant, Apache Maven, Eclipse and IntelliJ IDEA execute the following command:
sudo apt-get install default-jdk

To install OpenJDK 7, execute the following command:
sudo apt-get install openjdk-7-jre 
This will install the Java Runtime Environment (JRE). If you instead need the Java Development Kit (JDK), execute the following command:
sudo apt-get install openjdk-7-jdk




flashPlayer after download
Agendo con i privilegi di super utente, copiare il file libflashplayer.so nella sottocartella plugins della cartella di installazione di Firefox. Ad esempio, se Firefox è installato in /usr/lib/mozilla, utilizzare il comando sudo cp libflashplayer.so /usr/lib/mozilla/plugins ed inserire la password di super utente quando richiesto. 


Before you try out the article, open up terminal and key in 
----> acpi_listen 
and then press your fn+up and fn+down key combinations to check whether your brightness keys are actually getting registered by Ubuntu or not.
ok. that's good. this means, the keys are getting registered. now can you give the output of 
----> ls /sys/class/backlight/
it says "acer-wmi intel_backlight"
You do have intel drivers controlling your brightness. now open terminal and paste 
----> lspci | grep -i vga and provide the output
now paste 
----> sudo gedit /usr/share/X11/xorg.conf.d/20-intel.conf 
in the terminal. this would open geditor. Copy the following to the file and save and exit, logout and log in back again. you may ignore any error messages that appears in the terminal. 
----> Section "Device" Identifier "card0" Driver "intel" Option "Backlight" "intel_backlight" BusID "PCI:0:02:0" EndSection


Run the following command in a terminal:
----> xinput list
You will get an output that looks like this:
----> 
⎡ Virtual core pointer                          id=2    [master pointer  (3)]
⎜   ↳ Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
⎜   ↳ SynPS/2 Synaptics TouchPad                id=12   [slave  pointer  (2)]
⎣ Virtual core keyboard                         id=3    [master keyboard (2)]
    ↳ Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    ↳ Power Button                              id=6    [slave  keyboard (3)]
    ↳ Video Bus                                 id=7    [slave  keyboard (3)]
    ↳ Power Button                              id=8    [slave  keyboard (3)]
    ↳ Sleep Button                              id=9    [slave  keyboard (3)]
    ↳ Laptop_Integrated_Webcam_1.3M             id=10   [slave  keyboard (3)]
    ↳ AT Translated Set 2 keyboard              id=11   [slave  keyboard (3)]
    ↳ Dell WMI hotkeys                          id=13   [slave  keyboard (3)]
<---- 
It displays all the input devices connected. Note that they all have an id. Since 12 is the id for my touchpad, running the following command will disable it.
----> xinput set-prop 12 "Device Enabled" 0



For using by command-line:
You can make executable file (let by command 
----> gedit myfp
)as follows:
----> #!/bin/bash
----> [Your commands Here]
Give it execution permission by 
----> chmod +x myfp 
and put this file in location: /usr/local/bin
Now you can easily execute [Your commands Here] by running command 
----> mypf 
in Terminal.
For using by GUI (as a Launcher):
You can create a desktop file (let by command 
----> gedit mypf.desktop
) as follows:
----> 
[Desktop Entry]
Name=My Firefox
Comment=My Profile
Exec=[your command here]
Type=Application
Icon=[path/to/icon-file]
<----
where [Desktop Entry] remains constant and [your command here] is may be 
----> firefox -p 
or directly 
----> mypf 
if available. [path/to/icon-file] is path to icon file.
Give it execution permission by 
----> chmod +x mypf.desktop 
and put in location /usr/share/applications.
You can also create symbolic link to your desktop by 
----> ln -s /usr/share/applications/mypf.desktop  ~/Desktop 
and launch from Desktop easily.
Additional Info: It can be run at startup by putting Desktop file in $HOME/.config/autostart.



Opera
The best and easiest way to install Opera is by just downloading the deb-package from Opera's website. When you install the package, it will add their repository, automatically configured for updates.
When you have downloaded the file, you can install it by double clicking on the file to open Ubuntu software center. If you don't want to add the repository, you can install the package by opening a terminal in the directory where you have downloaded Opera, and run this command:
----> sudo dpkg -i <opera-package-name>
When you do this, you will be asked if you want to add their repository or not.
You can read more about this here: http://deb.opera.com/manual.html
Portable version
You can convert the deb package with this script: https://gist.github.com/ruario/8416e36372f1a976a713
Plugins
Flash
Install this package to get flash:
----> sudo apt-get install pepperflashplugin-nonfree
Java
Java is not supported currently, as they only provide a NPAPI plugin (which are not supported on both Opera and Chrome on Linux).
Get H.264 working
Updated 2015-09-19:
Right now it's a bit complicated to get support for H.264. You can read why here: https://forums.opera.com/discussion/comment/15223803#Comment_15223803
To get support for H.264, you have to run the following commands in a terminal:
----> sudo apt-get install chromium-codecs-ffmpeg-extra
----> sudo ln -s /usr/lib/chromium-browser/libs/libffmpeg.so /usr/lib/x86_64-linux-gnu/opera/lib_extra/libffmpeg.so.'x'
x = the Opera version. For example: libffmpeg.so.32
Note! Each time you update Opera to a new major version, you have to make a new symlink where you change the last number to the right one.
Then restart Opera.




Please note that wireless was working fine all this time, its just the missing icon.
Next install following two packages: indicator-applet and indicator-network.
---->  sudo apt-get install indicator-applet indicator-network 




netbeans JDK
First, you have to install a JDK, because you said in your comments:
---->      There is only one alternative in link group java (providing /usr/bin/java): /usr/lib/jvm/java-8-oracle/jre/bin/java 
---->      Nothing to configure.
so
---->  sudo add-apt-repository ppa:webupd8team/java
---->  sudo apt-get update
---->  sudo apt-get install oracle-java8-installer
---->  sudo apt-get install oracle-java8-set-default
Now you have to configure Netbeans to use this JDK or run Netbeans with
---->  netbeans --jdkhome /usr/lib/jvm/java-8-oracle
or, make sure that you are in the directory which the NetBeans folder is in
---->  gedit netbeans-<versionNumber>/etc/netbeans.conf
And then locate variable called ---->  netbeans_jdkhome <----
---->  netbeans_jdkhome="/home/<username>/jdk1.8.0_40"


Install Redis from the Ubuntu repositories:
---->  apt-get install redis-server
All Redis configuration options can be specified in the redis.conf file located at 
---->  /etc/redis/redis.conf. 
You may wish to make a copy of this file before editing it, to retain default values in case of a problem down the line:
---->  cp /etc/redis/redis.conf /etc/redis/redis.conf.default
After applying these configuration changes, restart Redis:
---->  service redis-server restart


eclipse frizz
I had something the same with 16.04 and Eclipse Mars. 
I thought it had frozen but in fact it was running very, very slowly. 
The problem is the version of GTK+ 3, shipped with 16.04. Fortunately the solution is very easy. 
Open a terminal and then type 
---->  export SWT_GTK3=0
---->  then start Eclipse from the terminal. 
If that works, then a more persistent fix is to put the 2 lines in italics below into eclipse.ini
---->  --launcher.GTK_version
---->  2
before the line:
--launcher.appendVmargs



eclipse menu panel
Open your eclipse.desktop file:
---->  sudo -H gedit /usr/share/applications/eclipse.desktop
(If you can't find it in this path, try in ~/.local/share/applications/eclipse.desktop. Otherwise, you could have to find yours using locate command).
Replace the Exec= line with this:
---->  Exec=env UBUNTU_MENUPROXY= eclipse
Where "eclipse" is the path to your eclipse executable. In this case it's just "eclipse" since there's a symlink in /usr/bin folder.


How to Install MySql Workbench on Ubuntu
apt-get update commands downloads the package lists from the repositories and “updates” them to get information on the newest versions of packages and their dependencies so that you’ll install the latest version of software packages.
---->  sudo apt-get update
---->  sudo apt-get install mysql-workbench
Now installation is complete to start this application, typing following command on terminal.
---->  mysql-workbench &


MySql Workbench on Ubuntu
error, access denied, when launched as local(no sudo)
To simply fix this issue, change the owner of the folder to the desired user using this command in terminal:
---->  sudo chown -R <user>:<group> .mysql
what this command does? i will explain each one of them
---->  sudo 
stands for "switch user and do" which is actually changing the user to root internally for this operation
---->  chown 
stands for "change owner" and it does what actually it means, of course for this command to work properly on a folder. the owner of the folder has to run it, in this case was root so sudo was necessary
---->  -R 
this parameter is actually from chown and it applies the same command recursively to all sub folders/files
---->  <user>:<group> 
this is just the desired owner and group we would like to assign to folder/file and its a mandatory parameter from chown. Also you have to enter the source of the folder/file next to this parameter
you can check more options for chown using man chown
actual case
---->  sudo chown -R roman:roman /home/roman/.mysql/workbench/sql_workspaces
---->  sudo chown -R roman:roman /home/roman/.mysql/workbench/cache
---->  sudo chown -R roman:roman /home/roman/.mysql/workbench/sql_history
or perhaps?
---->  sudo chown -R roman:roman /home/roman/.mysql/workbench



Install MySQL
---->  sudo apt-get update
---->  sudo apt-get upgrade
---->  sudo apt-get install mysql-server
MySQL will bind to localhost (127.0.0.1) by default.
To log in to MySQL as the root user:
---->  mysql -u root -p


The -S switch makes sudo read the password from STDIN. This means you can do
---->  echo mypassword | sudo -S command
to pass the password to sudo



GIT
in project's folder press
---->   Ctrl+H
find
---->   .gitignor
and set it to
---->  # Specifies intentionally untracked files to ignore when using Git
---->  # http://git-scm.com/docs/gitignore
---->  
---->  target



Shell
On the newer versions, on 
---->  nautilus (Files)
go to 
---->  Edit > preferences > Behaviour tab > 
and change the settings for 
---->  executable text file.



/*
*
*	FAO
*
*/

//Very large log files, what should I do?
Simply delete these files and then reboot?
No. Empty them but do not use rm because it could end up crashing something while 
you are typing the touch command to recreate it.
Shortest method:

---% cd /var/log
---% sudo su
---% > lastlog
---% > wtmp
---% > dpkg.log 
---% > kern.log
---% > syslog
---% exit

BEFORE YOU DO THAT. Do a tail {logfile} and check if there is a reason for them to be so big. 
Unless this system is several years old there should be no reason for this and fixing the problem 
is better than letting this go on.

And to prevent it to become that big in the future: setup logrotate. 
It is pretty straightforward and will compress the logfile when 
it becomes bigger then a size you set it to.


//gitCommit
---% git add <file-name, try through TAB>
---% git commit -a <*all*> -m "<commit message>"


//gitPull
---% git pull -f <*forse*> <repository>


//git change branch
---% git checkout -b <*new branch*> <branch name>
or
---% git checkout <branch name>


//Slow shutdown on Ubuntu


//How can I adjust the mouse scroll speed?
---% $ xinput set-prop <devnum> "Evdev Scrolling Distance" 8 1 1 # for smooth scroll
---% $ xinput set-prop <devnum> "Evdev Scrolling Distance" -8 1 1 # for smooth 'natural' scroll
Add this to your .profile file in home/user to apply on login
To get the <devnum>=9 run 
---% xinput list

