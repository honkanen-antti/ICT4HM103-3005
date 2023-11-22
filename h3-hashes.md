# Article summaries
Schneier's book (2015) [Applied Cryptography](https://learning.oreilly.com/library/view/applied-cryptography-protocols/9781119096726/10_chap02.html#chap02-sec003) gave great first look to how hashing and public key encryption works. Below is a really short summary of the subchapters 2.3 and 2.4:
- Many functions look and smell like one-way functions, but having evindence on them is really hard. Theory is present, but having practical evidence is not yet provided. That is why it is expected (or pretended) that one-way functions do exist.
- For public key encryption we cannot use traditional one-way function, but we need some sort of trapdoor to decrypt the message. By trapdoor in this case we actually mean instructions how to solve the original message.
- Calculcating hashes gives us a way to check that for example file/package hasn't changed on the way (we download a version we were supposed to download). In theory multiple inputs might produce same hash, but that is pretty unlikely situation hence we can trust pretty safely on checking the hash.

Tero Karvinen's [Command Line Basics Revisited](https://terokarvinen.com/2020/command-line-basics-revisited/) was pretty neat instructions for newbies to interact with terminal. I wish I had stumbled to these instructions when I was learning to use Linux almost 20 years ago.

I actually started with cracking the hashed and stumbled to Tero Karvinen's [Cracking Passwords with Hashcat](https://terokarvinen.com/2022/cracking-passwords-with-hashcat/) article. Tero's instructions are clear and I was easily able to find the correct option I was looking for hashcat (the output `-o` option).

# Billion dollar busywork (task A)
Adding `v` for example gives hash that starts with 0. So running `echo -n 'vTero'|sha256sum` gives `0ed33bb80f14525269119f8e3d5d1325cbbf2a3ff36242479c3ed45c58d0ff6e`.

# Comparing hashed (task B)
I created file `demo.txt` and added `Hello World` as its content. By running `sha256sum demo.txt` I got `d2a84f4b8b650937ec8f73cd8be2c74add5a911ba64df27458ed8229da804a26` as its has and when I added `s` to the end (file content 'Hello Worlds') I got `7c8008fad75cf050d84ea0bcf9376ec2c91d44cdba7868a611fcb54b0a012793` as its hash. By just adding one character to the file, changed the hash significantly making it impossible to guess what has changed without "cracking" the hash.

# Cracking the hash (task C)
First I tried to figure out the correct hash algorithm with `hashid -m 21232f297a57a5a743894a0e4a801fc3`. That gave me the following results:
```
[+] MD2 
[+] MD5 [Hashcat Mode: 0]
[+] MD4 [Hashcat Mode: 900]
[+] Double MD5 [Hashcat Mode: 2600]
[+] LM [Hashcat Mode: 3000]
[+] RIPEMD-128 
[+] Haval-128 
[+] Tiger-128 
[+] Skein-256(128) 
[+] Skein-512(128) 
[+] Lotus Notes/Domino 5 [Hashcat Mode: 8600]
[+] Skype [Hashcat Mode: 23]
[+] Snefru-128 
[+] NTLM [Hashcat Mode: 1000]
[+] Domain Cached Credentials [Hashcat Mode: 1100]
[+] Domain Cached Credentials 2 [Hashcat Mode: 2100]
[+] DNSSEC(NSEC3) [Hashcat Mode: 830
```
With that list I went on to try to crack the hash. First try with MD5 `hashcat -m 0 21232f297a57a5a743894a0e4a801fc3` didn't work and I tried MD4, double MD5 and NTLM. Since non of those modes worked I decided to download rockyou.txt from the web and include that.

Now with the rockyou.txt I went on to try again, this time with defining attack mode also. Running `hashcat -a 0 -m 0 21232f297a57a5a743894a0e4a801fc3 rockyou.txt` gave me the answer of `admin`. Since I didn't output the solution to some file I ran the command again with `--show` flag which printed the hash and its clear text nicely to terminal.

# Cracking the NTLM hash (task D)
By just following previous principles with already given hash mode, it was easy to run `hashcat -a 0 -m 1000 f2477a144dff4f216ab81f2ac3e3207d rockyou.txt`. With show command printed result is `monkey`.

# Craking the unknown (task E)
Firstly I tried to figure out what could be the hash mode. Running `hashid -m $2y$18$axMtQ4N8j/NQVItQJed9uORfsUK667RAWfycwFMtDBD6zAo1Se2eu` directly didn't give anything, because of Linux using $ sign as environment variables. After passing the hash in escaped mode (with single quotes `hashid -m '$2y$18$axMtQ4N8j/NQVItQJed9uORfsUK667RAWfycwFMtDBD6zAo1Se2eu'`) I got some responses.
```
Analyzing '$2y$18$axMtQ4N8j/NQVItQJed9uORfsUK667RAWfycwFMtDBD6zAo1Se2eu'
[+] Blowfish(OpenBSD) [Hashcat Mode: 3200]
[+] Woltlab Burning Board 4.x 
[+] bcrypt [Hashcat Mode: 3200]
```

Now with the few options I went on to try to crack the hash with mode 3200 and rockyou.txt: `hashcat -a 0 -m 3200 '$2y$18$axMtQ4N8j/NQVItQJed9uORfsUK667RAWfycwFMtDBD6zAo1Se2eu' rockyou.txt`. After waiting for a while I got the hash cracked and the answer was `12345`.

# References
[Trust to Blockchain 2023 autumn](https://terokarvinen.com/2023/trust-to-blockchain/)
