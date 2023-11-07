# Installing lab environment
Whole process started with installing Kali Linux (2023.3) to my old laptop. After setting up the laptop in general I installed Virtual Box with instructions found from 
[Kali's own documentation](https://www.kali.org/docs/virtualization/install-virtualbox-host/). Basically in short I ran the following commands.

```
sudo apt update
sudo apt full-upgrade -y
curl -fsSL https://www.virtualbox.org/download/oracle_vbox_2016.asc|sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/oracle_vbox_2016.gpg
curl -fsSL https://www.virtualbox.org/download/oracle_vbox.asc|sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/oracle_vbox.gpg
echo "deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian bullseye contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list
sudo apt update
sudo apt install -y dkms
sudo apt install -y virtualbox virtualbox-ext-pack
```

After setting up VirtualBox I followed [Tero Karvinen's instructions](https://terokarvinen.com/2021/install-debian-on-virtualbox/) to download debian-live-12.2.0-amd64-xfce.iso image from 
https://cdimage.debian.org/debian-cd/current-live/amd64/iso-hybrid/. With the downloaded ISO image I just started setting up Debian VM with pretty much default settings. What happened in the end was that I wasn't able to install the VM,
because my laptop uses different processor architecture and I had find correct ISO image. One handy tip for readers: check your host computer's processor architecture before downloading ISO image. With a bit of browsing I downloaded
debian-12.2.0-i386-DVD-1.iso from https://cdimage.debian.org/debian-cd/12.2.0/i386/iso-dvd/ and was ready to try again. Now with the i386 architecture ISO I was able to proceed with installing Debian onto VM. Because this is lab environment
I used default settings when installing OS. After successful installation and reboot I ran following commands to install latest updates.

```
sudo apt-get update
sudo apt-get -y dist-upgrade
sudo apt-get -y install ufw
sudo ufw enable
```

Now Debian virtual machine is ready to be used in exercise.
