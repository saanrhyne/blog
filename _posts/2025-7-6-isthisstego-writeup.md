---
layout: post
title: Is This Stego? Writeup - CubeCTF
description: My writeup for the Misc/Is This Stego? challenge in CubeCTF
image: "/assets/img/isthisstego0.png"

categories:
- Writeups
- CubeCTF

tags:
- OSINT

date: 2025-7-6 00:00 -0500
---

# Misc/Is This Stego? - rdj & ski
*Someone was asking us for a stego challenge, hopefully this is what they were looking for.*

*Flag format: cube{LAT,LON} with only two digits after the decimal point.*

*e.g. cube{12.34,-56.78}*


## Initial Thoughts
We are given a photo of sign that says "STGO", a fountain, and a flag. Although the challenge hints to it being stego (steganography), the descripton asks for a latitude and longitude. This means it is most likely an OSINT challenge. The sign is the biggest clue, and I figured I could find it pretty easily.

![image attachment](/assets/img/isthisstego1.png)


## Methodology
I first googled "STGO sign", yielding some results that looked pretty similar to the sign.

![google results](/assets/img/isthisstego2.png)

When I added the keyword "fountain" to the search, I didn't find many helpful results. This was because Google search wanted to autocorrect "stgo" to "santiago".

![google results](/assets/img/isthisstego3.png)

I put "stgo" in quotes, which found a helpful result from the [Iberia Airlines Travel Guide](https://www.iberia.com/hu/destination-guide/santiago-de-chile/).

![google results](/assets/img/isthisstego4.png)

If you scroll through the "How other travellers see it" section, you can find [a photo](https://www.instagram.com/p/DC4sluJP3t-/?img_index=10) taken in the same place as the original photo. However, the specific location was not given.

![instagram](/assets/img/isthisstego5.png)

At this point, I decided to just use Google images. This found lots of random Instagram photos, and after doing a little profile stalking (this is why your Instagram profile should be private!), I found [a photo](https://www.instagram.com/p/C-7z09GOjGJ/) identifying the location as Cerro San Cristobal, Parque Metropolitano.

![instagram](/assets/img/isthisstego6.png)

## Solution

I looked up the coordinates associated with the location, and Google gave (-33.42, -70.63). After trying a few variations, I found one that worked. The flag is `cube{-33.41,-70.62}`.
