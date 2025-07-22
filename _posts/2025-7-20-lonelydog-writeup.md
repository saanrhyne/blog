---
layout: post
title: Our Lonely Dog Writeup - DownUnderCTF 2025
description: My writeup for the Beginner/Our Lonely Dog challenge in DownUnderCTF 2025
image: "/assets/img/lonelydog0.png"

categories:
- Writeups
- DownUnderCTF 2025

tags:
- Misc

date: 2025-7-20 00:01 -0500
---

# Beginner/Our Lonely Dog - Crem
*e-dog has been alone in the downunderctf.com email server for so long, please yeet him an email of some of your pets to keep him company, he might even share his favourite toy with you.*

*He has a knack for hiding things one layer deeper than you would expect.*

## Initial Thoughts
We first need to find our what the correct contact email for E-Dog is. I use the [Verifalia](https://verifalia.com/validate-email) email address validator to check a few variations, and find that `e-dog@downunderctf.com` works.

![validate fail](/assets/img/lonelydog1.png) ![validate check](/assets/img/lonelydog2.png)

Now that we have the email, it's time to send some.

## Methodology
I send an email with an attachment entitled "dog.png". Within 1 minute, I get a response.

![email](/assets/img/lonelydog3.png)

Unfortunately, we don't get the flag. I try sending another email, incorporating the word bone and an attachment entitled "bone.png".

![email](/assets/img/lonelydog4.png)

Unfortunately, this email (and some other variations) get the same response.

![email](/assets/img/lonelydog6.png)

Because the challenge description mentioned "layers" I thought about the OSI model and was wondering if we needed to use a different transport layer protocol. I opened a ticket to see if that was on the right track, and I was told I was overthinking the challenge.

I decided to poke around in Gmail a bit more, and I noticed you could "Show original".

![menu items](/assets/img/lonelydog7.png)

After scrolling through lots of authentication signatures and random information, there was a field entitled "X-FLAG" that contained the flag.

![flag](/assets/img/lonelydog8.png)

## Solution
The flag is `DUCTF{g00d-luCk-G3tT1nG-ThR0uGh-Al1s-Th3-eM41Ls}`. I didn't know that you could view a lot more information about an email like that, and props to the organizers for keeping with the email inbox theme.
