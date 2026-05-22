# Hashing Basics — Task 6

The goal was simple: crack two hashes using Hashcat.

**hash3.txt** was a sha512crypt hash (`-m 1800`). Threw rockyou at it and got **spaceman**.

**hash4.txt** was NTLM (`-m 1000`), hash value `b6b0d451bbf6fed658659a9e7e5598fe`. Same wordlist, came back as **funforyou**.

Both cracked without much trouble, which honestly says more about the passwords than the algorithms.\
<img width="1907" height="841" alt="hash" src="https://github.com/user-attachments/assets/efa678f9-a805-48a9-8bf7-bcc19d765c82" />
