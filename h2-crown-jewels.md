# Article review
We were asked to read and summarize [Lockheed Martin Corporation's white paper](https://lockheedmartin.com/content/dam/lockheed-martin/rms/documents/cyber/LM-White-Paper-Intel-Driven-Defense.pdf) about Adversary Campaigns and Intrusion Kill Chains. Article demostrates Advanced Persistent Threats (APTs) and how they compare to other threats. Normal, more generic threat models take into account known threats and known vulnerabilites, but might lack the aspect of unknown actors, exploits and threats. In the article there were few case examples also how attackers were using the defined Intrusion Kill Chain process. A process which goes as followed: Reconnaissance -> Weaponization -> Delivery -> Exploitation -> Installation -> Command and Control (C2) -> Actions on Objectives. Normal threats are known threats and anti-virus and firewall can prevent most of them due to fact that they are known. APTs on the other hand are different story, because first of all they do targeted attacks and secondly APTs try to use zero-day exploits. Best way to defend is to build countermeasures more quickly than APTs can adapt so it will make costs of attack too much for the attacker as descriped in the article.

Even though threat modeling defined in the article is useful some of the detection measures are a bit obsolete. In modern era detecting reconnaisance via web analytics is hard or even impossible. Or should I say, it happens so much that detecting APT from automated reconnaissance will be hard due to all the noise from web traffic. At least that has been the case with few of my employees when I have talked with the IT about these topics. Gathering data is so easy and detecting APT targeting you is really hard for the same reason, data is scattered all over internet. One can easily check something from company's website, other thing from social media like LinkedIn and with fake profiles on other social media platforms you could get more insights of the company from its employees. IT departments don't have access to all the logs from all the services employees are using. When thinking about social media presence, IT departments cannot even get the logs from the platforms the company is using. So what should we do? My best advice is to follow principles defined in the article so model the threats and previous attacks with the Intrusion Kill Chain model and build such a counter measures that most of APTs don't want to waste money on attacking you.

# Threat model from XYZ Org
XYZ Org is an imaginary organization that provides learning platform for schools. Company's greatest asset is the material and exercises created to the learning platform. To protect customer data, company is storing internal operative data in other systems and not on the learning platform. Learning platform only has data related to learning.

So what can go wrong? As mentioned, the material and exercises are company's biggest assets thus they should not leak outside the learning platform. Bad actors are likely interested in stealing that data and selling it to other vendors or blackmail company to not lose the data. To follow with the attack tree, goal is to get the data out of the learning platform. Bad actors then need to get access to learning platform somehow. Buying the product is not impossible, but highly unlikely. Instead attackers could for example use malware or scan for open ports/unpatched vulnerabilites to gain access to servers hosting the platform which is possible. Now that attackers have access to servers hosting the platforms they could destroy the data (no benefit so impossible), use ransomware (possible), leak the data (possible), steal the data and sell it to others (not likely, but possible). Out of these possible options using ransomware and blackmail money from the company is the most likely situation and it might also be the most expensive one.

To reduce attack surface, first of all the learning platform must be developed in a secure way. Taking backups from the data is a no-brainer even though it might not work against ransomware (especially if backups are also encrypted). Limiting open ports on servers, installing latest updates and keeping passwords/keys secure and rotating them enough frequently are also preventive actions that must be implemented. This limits attack surface even though we cannot reduce it entirely. Reducing attack surface is crucial, but also end-users must be kept on mind so that learning platform is usable for end-users.

# Analysis of Rackspace Ransomware Attack
I decided to analyze [Rackspace Ransomware Attack](https://purplesec.us/security-insights/rackspace-ransomware-attack/) which happened on December 2nd 2022. Even though official statement has not been issued security researchers have figured out a possible source for the attack. Most likely entrypoint has been Exchange Cluster which was running version containing [ProxyNotShell vulnerability](https://doublepulsar.com/proxynotshell-the-story-of-the-claimed-zero-day-in-microsoft-exchange-5c63d963a9e9). During reconnaissance attackers probably saw this opportunity and started weaponizing this vulnerability with the exploitation to encrypt Rackspace's servers (objective). With exploitation available attackers were able to use the known vulnerability to deliver exploitation and install it to server environment and start encrypting servers. In the table below you can see Cyber Kill Chain framework's way of descriping the attack.

|Phase|Indicator|
|-----|---------|
|Reconnaissance|Scanning vulnerable Exchange Cluster builds|
|Weaponization|Exploitation and patch available already|
|Delivery|Unpatched vulnerability (likely) used to access servers|
|Exploitation|CVE-2022-41040 and CVE-2022-41082|
|Installation|Since official statement is missing we are not sure how ransomware was installed.|
|C2|Since official statement is missing we are not sure how command and control activities were performed.|
|Action on Objectives|Encrypt servers aka perform ransomware attack|

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

# References
[Trust to Blockchain 2023 autumn](https://terokarvinen.com/2023/trust-to-blockchain/)
