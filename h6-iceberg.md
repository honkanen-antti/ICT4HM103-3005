# Article summaries

# TOR

## Installing the browser
Quick google search for TOR provided me link to [TOR project's](https://www.torproject.org/) website where I was able to find download link and signature for the package.

![TOR Project's website](/tor_project.png)
![Downloading packages](/tor_download.png)

After downloading packages I verified signature using TOR project's [support pages](https://support.torproject.org/tbb/how-to-verify-signature/).

![Fetching developer key](/tor_import_signature.png)
![Verify signature](/tor_verify_signature.png)

Now that the package was downloaded and signature was verified, I was able to install the TOR browser using `tar xf tor-browser-linux-x86_64-13.0.6.tar.xz` command. It didn't go as expected, because I got an error about processor architecture which I forgot to take into account.

![Startup error](/tor_start_error.png)

Well, I had to find a package with i686 architecture so googling again. I was able to find correct package easily (searching for "tor browser i686") and followed previous steps to verify the package before starting installing it.

![Start screen](/tor_browser.png)

## Browsing the network
Firstly I went to [Ahmia site](https://ahmia.fi/) to get to onion service ([http://juhanurmihxlp77nkq76byazcldy2hlmovfu2epvl5ankdibsot4csyd.onion/](http://juhanurmihxlp77nkq76byazcldy2hlmovfu2epvl5ankdibsot4csyd.onion/)). Then I tried searching for Finnish newspapers, but that didn't provide results I wanted so I needed to switch to more global newspapers.

I found New York Times's drop service from TOR network (see picture below).

![New York Times](/tor_new_york_times.png)

I also tried to find marketplace, fraud service, forum and well known organization.

![Marketplace](/tor_dark_road.png)
![Fraud](/tor_fraud.png)
![Forum](/tor_forum.png)
![CIA](/tor_org.png)

## Anonymity and TOR

## Threat models
