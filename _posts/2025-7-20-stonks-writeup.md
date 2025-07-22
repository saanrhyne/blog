---
layout: post
title: Stonks Writeup - DownUnderCTF 2025
description: My writeup for the Beginner/Stonks challenge in DownUnderCTF 2025
image: "/assets/img/stonks0.png"

categories:
- Writeups
- DownUnderCTF 2025

tags:
- Web

date: 2025-7-20 00:00 -0500
---

# Beginner/Stonks - MC Fat Monke
*Times were wild before the email apocalypse. There were even sites giving out free money that also supported currency conversions!*

*WARNING: This challenge contains flashing colours! To disable add ?boring=true to the end of the URL when you visit the site.*

*AU: https://beginner-stonks-a0c8e158ea33.2025.ductf.net*

*US: https://beginner-stonks-a0c8e158ea33.2025-us.ductf.net*

## Initial Thoughts
We are given a website that has images, text, and buttons flying everywhere. We are also given a file called stonks.zip, which I assume to be the source code.

![website](/assets/img/stonks1.png)

There is a login now button, and I append "?boring=true" to the URL so I can actually see the challenge.

![website](/assets/img/stonks2.png)

## Methodology
The first thing I do with any web challenge is attempt to login with the credentials admin:admin. When I do that, the challenge seems to already be solved on that account.

![website](/assets/img/stonks3.png)

For context, logging in with any other account starts with a balance of 50 AUD.

![website](/assets/img/stonks4.png)

When I click "Check if you are rich", it gives me the flag.

![website](/assets/img/stonks5.png)

## Solution
The flag is `DUCTF{r3u5iNg_d3R_S35510N5_4_St000o0oONKsS5!}`. This unintended solve shows the danger of using one instance for all teams and not having unique instances.
