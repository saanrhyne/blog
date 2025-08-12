---
layout: post
title: Plain Sight Writeup - BCACTF 6.0
description: My writeup for the Forensics/Plain Sight challenge in BCACTF 6.0
image: "/assets/img/plainsight0.png"

categories:
- Writeups
- BCACTF 6.0

tags:
- Forensics
date: 2025-6-23 00:05 -0500
---

# Foren/Plain Sight - Lam To
*Can you help find my flag? I tried asking around but all I found was this poem.*

## Initial Thoughts
We are given `hiding_in_plain_sight.pdf`, which contains a lovely poem: *Hiding in Plain Sight by Denise Riley*

```
I try to find you, yet you are not here.
I’ve studied absence, fought to fill it in –
courage comes easier with a grasp of why.
A secret’s camouflaged when unconcealed.
I chose to not see/saw the thing too near?
Absence turns thicker, muscled by its strain.
A moon in daylight, whitest blue on blue,
surprises briefly, to appear surreal
until it slips to rights. I couldn’t spot
the obvious – obviam, in the way; plain
sight goes blind through chasing clarity.
I looked for you, so couldn’t see you gone.
I sensed your not-there in its burning life.
I listened out to feel its silence beat.
It does not speak with any human mouth.
```

My first thought was, like the [Dessert Time](/posts/desserttime-writeup/) challenge, to check for hidden text. Unfortunately, I found none.

## Methodology
I then decided to check for hidden images in the PDF using [I Love PDF](https://www.ilovepdf.com/pdf_to_jpg).

![button](/assets/img/plainsight4.png)

This yielded the file `img4.jpg`, which contains our flag.

![flag](/assets/img/plainsight5.jpg)


## Solution
The flag is `bcactf{Now_y0U_s3e_mE}`. This challenge was pretty easy for me thanks to one of the forensics questions in [DPRK](https://sakouk.me/cyberpatriot) - if you know, you know.
