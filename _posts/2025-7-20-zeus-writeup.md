---
layout: post
title: Zeus - DownUnderCTF 2025
description: My writeup for the Beginner/Zeus challenge in DownUnderCTF 2025
image: "/assets/img/zeus0.png"

categories:
- Writeups
- DownUnderCTF 2025

tags:
- Rev

date: 2025-7-20 00:04 -0500
---

# Beginner/Zeus - jzt
*To Zeus Maimaktes, Zeus who comes when the north wind blows, we offer our praise, we make you welcome!*

## Initial Thoughts
We are given an ELF binary. The first step, as with any rev challenge, is to decompile it.

## Methodology
After putting the binary into Binja, we find the main logic of it.

![binja](/assets/img/zeus1.png)

When you run the binary, you have to add a `-invocation` with a value equal to var_10 for it to print the flag.

Scrolling up in the binary finds the full value of var_10.

![binja](/assets/img/zeus2.png)

Now it's time to run the binary using my trusty Kali VM.

![running the binary](/assets/img/zeus3.png)

## Solution
The flag is `DUCTF{king_of_the_olympian_gods_and_god_of_the_sky}`.
