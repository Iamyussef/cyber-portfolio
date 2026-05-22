# TryHackMe — Hashing Basics

This room covered the fundamentals of hashing (what it is, how it works, 
and where it's used in the real world.)

Hashing takes input data and produces a fixed-length digest. The same input 
always produces the same hash, but even a tiny change in the input completely 
changes the output. It's a one-way process — you can't reverse a hash to get 
the original data back.

The room covered common algorithms like MD5, SHA-1, SHA-256, and SHA-512, 
each differing in digest length and security strength. MD5 and SHA-1 are 
considered weak by today's standards, while SHA-256 and SHA-512 are still 
widely used.

Hashing is used for password storage, file integrity checks, and digital 
signatures. When stored correctly, passwords are hashed (ideally with a salt) 
rather than being saved in plaintext.

The practical side involved identifying hash types and cracking them using 
Hashcat with a wordlist, which showed how quickly weak or common passwords 
fall regardless of the algorithm protecting them.

The room wrapped up by drawing a clear line between hashing, encoding, and 
encryption — three things that are easy to confuse but serve completely different purposes.
