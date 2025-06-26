---
layout: post
title: MiniDSP Writeup - GPN CTF 2025
description: My writeup for the rev/MiniDSP challenge in GPN CTF 2025
image: "/assets/img/minidsp0.png"

tags:
- writeup
- rev
- gpn ctf 2025
date: 2025-6-21 00:00 -0500
---

# rev/MiniDSP - s1nn105
*I found this compiler, I compiled this code, now I am confused. I hope you are as well. Note that the code might be broken.*

## Initial Thoughts
We are given an ELF binary entitled "FUUUNNN_SURLEY". My first thought was to put it into a compiler and poke around.

## Methodology
I uploaded it into [Binary Ninja](https://binary.ninja/), which is what I use for a lot of these challenges because its easy to install and use (IDA license key setup is confusing and Ghidra looks scary), and scrolled through. At the very bottom, there was the flag.

![Binary Ninja Screenshot of the Flag](/assets/img/minidsp1.png)

## Solution
The flag is `GPNCTF{yOu_reaLlY_KNow_yOur_iN5TRument5_Now_PR_iT_TO_GHIDR4}`. This was a pretty simple challenge, and I wish I had more time to explore the rev challenges. I was doing 3 other CTFs at the same time as this one, so it was a bit hectic.
