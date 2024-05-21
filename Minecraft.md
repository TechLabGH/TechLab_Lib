Raspberry PI Minecraft server setup (May 24)

# A. Installing the Latest Version of Java to the Raspberry Pi

In this section, we will show you how to install the latest version of Java on your Raspberry Pi.

Unfortunately, the Raspberry Pi’s package repository often contains an out-of-date version of Java. While this isn’t an issue for some software, some rely on newer versions, such as the Minecraft server.

Luckily, we can get newer builds of Java for our Raspberry Pi by adding a third-party repository. This repository is managed by Azul (https://www.azul.com/) and offers builds of newer versions of Java for ARM64 systems like our Raspberry Pi.

The caveat is that these steps must work on a Raspberry Pi 3 or later and a 64-bit operating system.

Preparing your Raspberry Pi for Java
### 1. Before we can add the Azul repository and download the latest version of Java to our Raspberry Pi, we must ensure we have an updated base to work off of.

You can update the package list cache and upgrade any out-of-date packages using the following two commands.
```
sudo apt update
sudo apt upgrade
```
### 2. Your next step is to install the packages we require to set up the Azul repository.
```
sudo apt install curl gnupg ca-certificates
```
Adding the Azul Repository to your Pi
### 3. Using the following command, we will download and save the Azul GPG key to our Raspberry Pi.

We need this key to verify the packages we are downloading are authentic.
```
curl -s https://repos.azul.com/azul-repo.key | sudo gpg --dearmor -o /usr/share/keyrings/azul.gpg
```
### 4. With the GPG key now saved to our system, our next step is to add the Azul repository to our list of sources.

Adding this repository will give us access to the latest versions of Java on our Raspberry Pi,
```
echo "deb [signed-by=/usr/share/keyrings/azul.gpg] https://repos.azul.com/zulu/deb stable main" | sudo tee /etc/apt/sources.list.d/zulu.list
```
### 5. For our system to realize that it can install the new packages, you will want to use the following command to update the package list cache.
```
sudo apt update
```
Installing the Latest LTS Version of Java on your Raspberry Pi
### 6. With the Azul repository now added to our Raspberry Pi, we can install OpenJDK 21 by using the following command.

At the time of publishing, OpenJDK 21 was the current long-term support release. You can install newer versions if you like, as Azul typically has builds for the latest release.
```
sudo apt install zulu21-jdk-headless
```
### 7. You can verify the version of Java you just installed by running the following command within the terminal.
```
java --version
```
Below you can see that we now have OpenJDK 21 (Java 21) running on our Raspberry Pi using the builds from Azul.
```
openjdk 21.0.3 2024-04-16 LTS
OpenJDK Runtime Environment Zulu21.34+19-CA (build 21.0.3+9-LTS)
OpenJDK 64-Bit Server VM Zulu21.34+19-CA (build 21.0.3+9-LTS, mixed mode, sharing)
```

# B. Installing Java to the Raspberry Pi from the Debian Repository
This section will show you how to install Java on your Raspberry Pi using the standard repository.

It’s important to note that this method comes with a limitation. You will be using the version of Java that was initially shipped with your distribution, such as OpenJDK 17 with Raspberry Pi OS Bookworm.

### 1. Before we go ahead and install Java, we need first to ensure that everything is up to date.

To update all existing packages, go ahead, and run the following two commands.
```
sudo apt update
sudo apt upgrade
```
The update process can take some time if you have a slow network connection, or there is a lot of packages to update.

### 2. Once the update process has completed, we can proceed to install the latest available version of Java to our Raspberry Pi by running the following command.

We are using the package default-jdk as this will always point to the latest available version of the JDK for Raspberry Pi OS.

For example, on Bookworm, this command will install Java 17 to our Pi.
```
sudo apt install default-jdk
```
### 3. Now that we have installed Java, let us quickly run it to make sure everything is working.

To test that it has been installed correctly, run the following command on the Raspberry Pi.
```
java -version
```
All this command does is get the Java Runtime to print out its version.
```
openjdk version "11.0.5" 2019-10-15
OpenJDK Runtime Environment (build 11.0.5+10-post-Raspbian-1deb10u1)
OpenJDK Server VM (build 11.0.5+10-post-Raspbian-1deb10u1, mixed mode)
```

# C. Setting up the Raspberry Pi Minecraft Server
### 1. First, update operating system packages to the latest version by entering the following commands.
```
sudo apt update
sudo apt upgrade
```
### 2. Now, we will need to make a couple of changes in the config tool. Let’s bring the tool up by entering the following line.
```
sudo raspi-config
```
If you need more information regarding the raspi-config tool, please check out our guide.

### 3. Also, it is unlikely you want to boot into the desktop, so ensure the boot option is set to the CLI (Command Line Interface). This change will help give the server as much processing power as possible.

To change the boot option, select 1 System Options, and select Boot / Auto Login.

Select Console or Console Autologin.

### 4. Finally, enable SSH so we can access the Pi remotely if required, unless you already have it enabled.

To enable SSH, go to Interface Options. Next, Select I1 SSH. Lastly, answer <YES> to enable the SSH server.

### 5. Now go to <Finish> on the main screen and answer <YES> to the reboot question.

6. We will now want the IP address of our Pi for when we try to connect to our server. To get the Raspberry Pi IP address, enter the hostname command.
```
sudo hostname -I
```
To ensure the IP doesn’t change, you should set up setup a static IP address on the Raspberry Pi and your router.

### 7. Next, we need to make sure that Git is installed. Otherwise, we will not be able to build the server.

Enter the following command to install the Git software.
```
sudo apt install git
```
### 8. By default, Java (17) should already be available on Raspberry Pi OS (Bookworm). However, if you wish to use the latest version of the Minecraft server, you will need to use a newer version than what is available.

To install a version of Java compatible with Minecraft 1.20.6 + (Java 21 or 22), please follow our installing Java guide.

### 9. Now, we will need the Minecraft server file, which we will create using a builder tool that Spigot supplies.

To get the tools, enter the following commands.
```
mkdir ~/minecraft
cd ~/minecraft
wget https://hub.spigotmc.org/jenkins/job/BuildTools/lastSuccessfulBuild/artifact/target/BuildTools.jar
```
### 10. Now we will want to run the build tools file, so it creates our Spigot server. It will take about 15 minutes to finish.

Change --rev latest at the end of the command to get a different version. Don’t forget to change latest in the command to the version number you wish to download. For example, **--rev 1.20.6 will download version 1.20.6**.
```
java -Xmx1024M -jar BuildTools.jar --rev latest
```
Important: If you have a Raspberry Pi B+, B, or any variation before the Raspberry Pi 2, the build tools will likely fail. You will need to generate the spigot.jar on a more powerful computer instead.

### 11. To ensure the Spigot server successfully downloaded and saved, simply type ls. You should see ***spigot-1.20.6.jar***. The filename may be different depending on the version you downloaded.
```
ls
```
Make sure you remain in the ~/minecraft folder as we want all the server files to be created in here. If you start the server in a different folder, it will create the files there.

### 12. Now we are ready to launch the server. To do this, enter the following command. You may need to change the version number depending on what version you’re using e.g. spigot-1.20.4.jar.

**Raspberry Pi 1**
```
java -Xms256M -Xmx496M -jar ~/minecraft/spigot-1.20.6.jar nogui
```

**Raspberry Pi 2, 3, 4, or 5**
```
java -Xms512M -Xmx1008M -jar ~/minecraft/spigot-1.20.6.jar nogui
```
With the 2GB and 4GB variants of the Raspberry Pi 4 or 5, you can increase the Xmx value even higher.

The server will stop straight away as we will need to agree to the Eula. You can do this by opening the Eula by typing the following command.
```
nano eula.txt
```
### 13. In here, change false to TRUE. Once done, save and exit by pressing CTRL + X, then Y.

### 14. Now relaunch the server. It will take a while to create a map, so give it about three to five minutes. If you ever reboot again, it will only take thirty seconds to load if the map has already been created.

### 15. The server should be running and accessible over the local network.

### 16. You might want to mod your user now so that you can use all the server commands when you log in. If we have it auto-boot on startup, accessing the server backend is slightly more difficult.

To mod your user, simply run the following command when the server has launched (Replacing username with your username).
```
op username
```
### 17. The Minecraft server on the Raspberry Pi will now be up and running fine, but you may want to do some optimizations to the server to make it run even better.

Raspberry Pi Minecraft Server

# D.Connecting to the Minecraft Server
If you are on a local network, it should be pretty easy to connect to the Minecraft server running on the Raspberry Pi. To test it out, follow the steps below.

### 1. Load the Minecraft Java client on a computer within the same local network as the Pi. Ensure the version of the client matches the version of the server.

### 2. Go to multiplayer, and your server might appear in the local list. If it doesn’t, simply go to direct connect and enter the IP address we got earlier on the Pi using the hostname command.
```
hostname -I
```
### 3. If you want to allow access to the Minecraft server via the internet, you will need to set up port forwarding.

Assuming you want to learn how to do this, head over to my guide on setting up Raspberry Pi port forwarding. You will need to port forward the port 25565 (unless you change it in the server properties) to the IP of your Pi.

# E. Configuring the Server
Here are a few tips for configuring the server and getting it up and running.

## Optimizing the Minecraft Server
To get the most out of our Minecraft server on the Raspberry Pi, you can install a plugin to help optimize the performance.

There are many plugins that can help with performance or extend the server’s functionality. Simply use the wget command to download them to the Pi. Below is an example.
```
cd ~/minecraft/plugins
wget -O example.jar <example_plugin_url>
```
## Editing the Minecraft Properties
You will probably want to know how to edit the server properties. This ability to edit is very important for optimizing the server and customizing it to how you want the server to be.

If you want more information for each of the server settings, you can find a good page on all the server properties here.

To enter the server properties, enter the following line.
```
sudo nano ~/minecraft/server.properties
```
Now, we will want to change a few settings to help optimize the performance of the server.

You can change these and other settings to whatever you like however you want, but keep in mind the Pi can’t handle too much processing.
```
view-distance=04
max-player=5
```
## Boot on Startup
To have the server start on boot, we will need to do a few extra steps.

### 1. We will need to create a service for the Minecraft server so let’s start writing the service file by entering the command below.
```
sudo nano /lib/systemd/system/minecraftserver.service
```
### 2. In this file you will need to enter the following text.

This file defines the service, so the service manager knows how and what to run. Don’t forget to update the spigot version number whenever you upgrade.

Update <USER> with the username you plan on using to run the server. You can see the username of your user by entering the whoami command into the terminal.
```
[Unit]
Description=Minecraft Spigot Server

[Service]
User=<USER>
Group=<USER>
Restart=on-abort
WorkingDirectory=/home/<USER>/minecraft/
ExecStart=/usr/bin/java -Xms512M -Xmx1008M -jar /home/<USER>/minecraft/spigot-1.20.4.jar nogui

[Install]
WantedBy=multi-user.target
```
Once done, save the file by pressing CTRL + X then Y followed by ENTER.

### 3. Now, we will need to enable the service. You can enable the service by running the command below.
```
sudo systemctl enable minecraftserver.service
```
### 4. You should now be able to start the Minecraft server by simply using the following command.
```
sudo systemctl start minecraftserver.service
```
### 5. Using a similar command, you can check on the status of the service. Checking the status is great for debugging.
```
sudo systemctl status minecraftserver.service
```
### 5. You can stop the server by using the following command.
```
sudo systemctl stop minecraftserver.service
```
Your server should now start on boot. You can test it by restarting the Raspberry Pi. It will take a few minutes to startup.
```
sudo reboot
```
If you want to get access to the server on the command line, then you will need to shut down the server and load it using the normal command.

# F.Installing Webmin

Add a new apt repository

The first way to install Webmin is to add a new repository.
It could be a bit more complicated upfront, but I think that it’s the best solution.
This way you can manage updates in the same way as any other software (graphically or with apt upgrade).

I know, there are a few commands to copy & paste for this solution, but once Webmin installed, you won’t have to use a terminal anymore.

So, here is how to do this:

Open the apt sources.list file:
```
sudo nano /etc/apt/sources.list
```
Add this line at the end:
```
deb https://download.webmin.com/download/repository sarge contrib
```
Yes, Sarge is an old Debian version, but the repository is updated regularly.
It should look like this after the edition:

Then you need to install the GPG key corresponding to this repository:
```
wget http://www.webmin.com/jcameron-key.asc
sudo apt-key add jcameron-key.asc
```
Finally, install Webmin:
```
sudo apt update
sudo apt install webmin
```
