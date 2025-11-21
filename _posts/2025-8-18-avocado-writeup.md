---
layout: post
title: Just Some Avocado Writeup - scriptCTF 2025
description: My writeup for the "Just Some Avocado" forensics challenge in scriptCTF 2025
image: "/assets/img/avocado/thumbnail.jpg"

categories:
- Writeups
- scriptCTF 2025

tags:
- Forensics
date: 2025-8-18 00:00 -0500
---

# Just Some Avocado (302pts)

*just an innocent little avocado!*

[avocado.jpg](/blog/assets/attachments/avocado.jpg)

## Initial Thoughts
We are given an image file, `avocado.jpg`. Because it is a forensics challenge, the first thing to check is stegonography.

![The provided file, "avocado.jpg", which depicts a cartoonish avocado with a light blue background.](/assets/attachments/avocado.jpg)

## Methodology

I uploaded the image into Aperi'solve, and foremost found a zip file.

![A screenshot of foremost on Aperi'solve, which says "foundat=justsomezip.zipUT"](/assets/img/avocado/1.png)

Unfortunately, the zip file requires a password.

![A screenshot of 7-zip, which says "0% Extracting C:\Users\saanv\Downloads\avocado.jpg" and "Enter password:"](/assets/img/avocado/2.png)

Using [zip-password-finder](https://github.com/agourlay/zip-password-finder) and [rockyou](https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt), we find the password `impassive3428`.

![A screenshot of a Kali Linux terminal, showing the process of finding the zip password](/assets/img/avocado/3.png)

Unzipping the file shows `staticnoise.wav` and `justsomezip.zip`.

![A screenshot of 7-zip, showing the files found from unzipping avocado.jpg: justsomezip.zip and staticnoise.wav](/assets/img/avocado/4.png)

Unfortunately, `justsomezip.zip` is password protected. However, it does seem to contain the flag.

![A screenshot of a Kali Linux terminal, showing how the password for justsomezip.zip could not be cracked using rockyou.txt](/assets/img/avocado/5.png)

This means that `staticnoise.wav` must have the password hidden somehow. The audio is, just as it says, static noise. This means that it's probably not morse code or garbled text in the audio file itself.

The next thing to check is spectograms. Sometimes audio files have hidden pictures/text "drawn" on the wavelengths that are revealed when you view the spectogram.

I upload staticnoise.wav into [Audacity](https://www.audacityteam.org/) and switch it to spectogram view.

![A screenshot of Audacity, showing a hidden stenographic message](/assets/img/avocado/6.png)

This reveals a hidden message of `d41v3ron`. Using that as the password for `justsomezip.zip` works.

![A screenshot of 7-zip, showing the file found from unzipping justsomezip.zip: flag.txt](/assets/img/avocado/7.png)

Finally, we find `flag.txt`.

## Solution

The flag is `scriptCTF{1_l0ve_d41_v3r0n}`. This was a relatively simple forensics challenge that combined numerous basic techniques, and  I had fun.
