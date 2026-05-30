# John the Ripper Basics — Lab Report

## Task 4: Cracking Different Hash Types
<img width="1912" height="883" alt="hash-crack" src="https://github.com/user-attachments/assets/d27e1702-4171-40fc-89ac-201079586882" />

The task gives you four hash files and expects you to identify each type and crack them.
I used hash-identifier on each file before running anything; guessing the format wastes time.

hash1.txt was sha1. hash2.txt cracked to `kangaroo`. hash3.txt was sha256 and came back as
`microphone`. Those three were straightforward.

hash4.txt was whirlpool and that one caught me off guard. I first ran it with `--format=raw-whirlpool`
the same way I did the others and got an error saying the format name didn't exist. Turns out
whirlpool doesn't follow that naming pattern — you just pass `--format=whirlpool` directly.

```bash
john --format=whirlpool --wordlist=/usr/share/wordlists/rockyou.txt hash4.txt
```

Cracked to `colossal`. After the session ended I ran `--show` to confirm:

```bash
john --show --format=whirlpool hash4.txt
```

Output: `?:colossal` — 1 hash cracked, 0 left.

---

## Task 6: Cracking /etc/shadow
<img width="1852" height="832" alt="hash-shadow-crack" src="https://github.com/user-attachments/assets/3e88cf03-c328-4bee-8dd9-ce62001d9e7e" />

This one is closer to something you'd actually encounter. The task gives you a `local_passwd`
and `local_shadow` file and asks you to crack the root password out of it.

On Linux, password hashes sit in `/etc/shadow` but that file alone isn't enough. John needs
the username context from `/etc/passwd` too. The `unshadow` utility handles that by merging both
into one file:

```bash
unshadow local_passwd local_shadow > unshadowed.txt
```

The root hash was sha512crypt so I passed that as the format:

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt --format=sha512crypt unshadowed.txt
```

Took about 2 seconds. Root password was `1234`.

Not surprising, rockyou.txt has that near the top. The point landed though: a weak password
on a root account falls almost instantly. No sophistication needed.
