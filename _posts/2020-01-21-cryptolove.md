---
title: "CryptoLove"
date: "2020-01-21"
layout: single
tags:
- Automation
categories:
- Projects
---

# CryptoLove
Basically it is a script that identifies the hash and gets a list of words
and tries to encrypt those words with all combinations of words to get the
same hash code and it tries padding with each word so about half million
combinations for each word, it is determined by the length of the hash

**Example**:

So when you try to crack "d1282e62a3dd7c145c9192d5c146ff68"
with the given wordlist.txt
```
Omar
Mohamed
Test
Hello
123456
```
the script tests "Omar" to 2500 free words with padding just to see if it
works alone then it tries "Mohamed" to 2500 free words with padding to see
if it works alone then it tries combination of "OmarMohamed" to 2500 free
words with padding, then it tries smallcase and Capital case so it would
take long time to crack but we care about the final.

```python
ow = open("wordlist.txt")
hash = "d1282e62a3dd7c145c9192d5c146ff68"
lines = []
for i in ow.readlines():
    lines.append(i)
for i in range(0,len(lines) - 1):
    one_comb = lines[i]
    two_comb = lines[i] + lines[i+1]
    for z in range(0, 2500):
        one_comb = one_comb + "\x00" # PADDING
        hashz = md5_encrypt(one_comb)
        if hashz == hash:
            print("Found")
```
thats the idea not the offical script
Finally it gets, "d1282e62a3dd7c145c9192d5c146ff68" == "OmarTest " (with one space)
