# Article summaries
Summary from [Schneier 2015: Applied Cryptography: Chapter 2](https://learning.oreilly.com/library/view/applied-cryptography-protocols/9781119096726/10_chap02.html#chap02-sec005):
- Public key encryption allows everyone to encrypt messages, but only the private key holder can decrypt the messages. Using public key cryptography solves key-management problem, when symmetric cryptography requires both parties to use same key.
- "Trent has to be completely secure. If his database of secret keys ever got out or if someone managed to modify his programming, everyone's signatures would be completely useless. False documents purported to be signed years ago could appear."
- Digital signature often include timestamps to verify when message was signed. This approach is to eliminate reusing signing and crooked signing (signing -> leaking private key on purpose -> lying that someone used your key to sign).
- Theoretically signing messages can be compromised, but requires some party to not check the signatures. You should check the message for comprehensibility before sending a receipt to avoid this security problem.
- Computers don't create actual random numbers, but pseudo-random numbers. This is a bit of an issue with cryptography, but something that can be managed.

Summary from [Rosenbaum 2019: Grokking Bitcoin: Chapter 2](https://learning.oreilly.com/library/view/grokking-bitcoin/9781617294648/OEBPS/Text/kindle_split_011.html#ch02lev1sec1):
- In the book Lisa is acting as a Bitcoin by being the trusted partner to keep account balance for everyone.
- On the background Bitcoin (and blockchains) use hashing. More specifically cryptographic hash functions which take any digital input data (pre-image) and produce a fixed-length output out of them (hash).
- Bitcoin also uses signatures to authorize payments for example. By signing the request it is verified that request is coming from trusted source (aka you are who you claim to be).
- Rosenbaum's and Schneier's book share to same concer of keeping the private keys private. As far as private keys are not leaked and they stay secure, the system using them stays secure. When someone leaks a private key, then that compromised key can be used to do harm.

Summary from [Karvinen 2023: PGP - Send Encrypted and Signed Message - gpg](https://terokarvinen.com/2023/pgp-encrypt-sign-verify/):
- Tero's instructions for setting up the lab environment is once again state of the art.
- His example cases are fun to read, for example the reference to famous Nokia ringtone [Säkkijärven Polkka](https://www.youtube.com/watch?v=jvFMtMAxGSw) was hilarious.
- With these instructions it was easy to setup my own environment and try out this myself.

# Pubkey today
Today I have used SSH access to development server and to version control (GitHub). To setup SSH connection I have created SSH keys and added the public key to GitHub/development server. See [connecting to GitHub witth SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh) for more detailed instructions.

# Messaging
Lab environment running, please try again later...
```
Send an encrypted and signed message using PGP, then verify and decrypt it. (You can use folders to simulate users, or use two computers or two different OS users. Don't use Tero as a name of any party, unless that's your given name.)
```

# Other tool
Lab environment running, please try again later...
```
Encrypt a message using a tool other than PGP. Explain how different parties use different keys at different stages of operation. Evaluate the security of the tool you've chosen.
```

# Eve and Mallory
Both parties have built trust relationship so both parties trust each other. By building this trust relationship and sharing the public keys in some secure way, messaging parties prevent Eve and Mallory acting. Eve can listen the conversation, but all she
can hear is encrypted data which is really hard to decrypt without the private keys. Same also applies to Mallory, because for him to be able to modify messages, he should be able to decrypt messages first.

Now Mallory could try to be sneaky and use his own public and private keys when messaging with either party. Mallory could record first party's message and at some later time, send that message to second party, claiming that it came from him (Mallory).
Second party thinks that it is a legitimate message from Mallory, so decrypting the message with own private key and then tries to verify Mallory's signature by decrypting it with Mallory's public key. Result will be pure gibberish,
but if the second party goes on with the protocol and sends Mallory a receipt, Mallory decrypt the message with his private key, encrypt it with second party's public key, decrypt it again with his private key, and encrypt it with first party's public key and voilà! Mallory has the content.

# Password management
Password managers free people from the need to remember all the passwords. They just need to remember the master password to unlock others. Unfortunately by default users are lazy and quite a few people use the same password everywhere, hence that's the security risk and that is what attackers do. When attackers find username-password combination in clear-text, they try to use it to multiple services.

# Refer to sources
Done

# References
[Trust to Blockchain 2023 autumn](https://terokarvinen.com/2023/trust-to-blockchain/)
