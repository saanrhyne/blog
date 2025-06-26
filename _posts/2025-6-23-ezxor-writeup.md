---
layout: post
title: Ez-XOR Writeup - BCACTF 6.0
description: My writeup for the Crypto/Ez-XOR challenge in BCACTF 6.0
image: "/assets/img/ezxor0.png"

categories:
- Writeups
- BCACTF 6.0

tags:
- Crypto
date: 2025-6-23 00:00 -0500
---

# Crypto/Ez-XOR - Colin
*Please be very ORZ and do some XORing.*

## Initial Thoughts
We are given `encoded_flag.txt`, which contains the following:
```
ICEjITYkOREpKyArBisRNyQkHRArODguJxAvJx0RKyUvIx0OIywmch0DNzAjJS0sHQAjMC0sHRcyJTAjJicmPw==
```

## Methodology
This looks like a Base64 string, but when I use [CyberChef](https://gchq.github.io/CyberChef/) to translate it, we get the following, which isn't exactly a flag.

![Photo of cyberchef](/assets/img/ezxor1.png)

The challenge is literally called Ez-XOR, so I assume it has something to do with XOR. I tried XOR bruteforce and then decoding it with magic, but that wasn't working.

![Photo of cyberchef](/assets/img/ezxor2.png)

I then had the idea to decode from base64 first, and then XOR it. By base64 decoding the string, and then XORing it with a key of 42, I found the flag.

![Photo of the flag](/assets/img/ezxor3.png)

## Solution
The flag is `bcactf{SkibiDiSuff_RizzleRme_Sigma_Land0_Auragon_Baron_Upgraded}`. This was definitely an easy crypto challenge, but it was good for a non-crypto main like me.
