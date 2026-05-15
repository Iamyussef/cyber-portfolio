# TryHackMe — Public Key Cryptography Basics

Finished this room as part of the Cyber Security 101 path.

This room covers asymmetric cryptography from both the theory and practical side.

Worked through:

* RSA
* Diffie-Hellman
* SSH keys
* GPG/PGP

For RSA, I manually calculated values like `n` and `ϕ(n)` from raw prime numbers instead of relying on tools, which helped me understand what’s actually happening behind the encryption process.

Diffie-Hellman was probably the most interesting section. The idea that two people can agree on a shared secret over a public channel — without ever sending the secret itself — still feels almost like a magic trick even after doing the math.

The SSH task was straightforward: inspected a private key file and identified the encryption algorithm directly from the header. Since I already use SSH keys regularly, that part connected quickly.

The GPG lab was the most hands-on section. Had to import a private key into GPG’s keyring and decrypt an encrypted message.

```bash
gpg --import tryhackme.key
gpg --decrypt message.gpg
```

One important thing I learned:
just because a private key file exists on disk doesn’t mean GPG automatically recognizes it — you must import it into the keyring first. Small detail, but exactly the kind of thing that can trip you up in a real-world situation.

Also learned that passphrase-protected private keys can be attacked using `gpg2john` + John the Ripper, very similar to cracking protected SSH keys.

Overall, a solid room. Everything here connects directly to real-world tools and workflows I’m already using.
