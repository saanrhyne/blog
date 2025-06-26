---
layout: post
title: Plain Sight Writeup - BCACTF 6.0
description: My writeup for the Foren/Plain Sight challenge in BCACTF 6.0
image: "/assets/img/plainsight0.png"

categories:
- Writeups
- BCACTF 6.0

tags:
- Foren
date: 2025-6-23 00:05 -0500
---

# Foren/Plain Sight - Lam To
*Can you help find my flag? I tried asking around but all I found was this poem.*

## Initial Thoughts
We are given `hiding_in_plain_sight.pdf`, which contains a lovely poem:

<img src="/assets/img/plainsight1.png" height=200px> <img src="/assets/img/plainsight2.png" height=200px> <img src="/assets/img/plainsight3.png" height=200px>

My first thought was, like the [Dessert Time](/posts/desserttime-writeup/) challenge, to check for hidden text. Unfortunately, I found none.

## Methodology
I then decided to check for hidden images in the PDF using [I Love PDF](https://www.ilovepdf.com/pdf_to_jpg).

![button](/assets/img/plainsight4.png)

This yielded the file `img4.jpg`, which contains our flag.

![flag](/assets/img/plainsight5.jpg)


## Solution
The flag is `bcactf{Now_y0U_s3e_mE}`. This challenge was pretty easy for me thanks to one of the forensics questions in [DPRK](https://sakouk.me/cyberpatriot) - if you know, you know.
