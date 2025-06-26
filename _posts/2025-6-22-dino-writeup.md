---
layout: post
title: DiNo. 1 Writeup - IERAE CTF 2025
description: My writeup for the Misc/DiNo. 1 challenge in IERAE CTF 2025
image: "/assets/img/dino0.png"

categories:
- Writeups
- IERAE CTF 2025

tags:
- Misc
date: 2025-6-22 00:01 -0500
---

# Misc/DiNo. 1 - IERAE
*No Internet*

## Initial Thoughts
We are given a variant of the Chrome Dino Game with bears and wagging fingers. We're told that if we beat 5000 points, we will recieve the flag. I did solve the challenge with my expert dino game skills, but I also wanted to see if I could solve it in a more technical way.

![Screenshot of the Game](/assets/img/dino1.png)

## Methodology
I inspected the source code and noticed that, like the instructions said, the flag would be printed if your score was greater than the clearscore (5000).

![Screenshot of the Game](/assets/img/dino2.png) ![Screenshot of the Game](/assets/img/dino3.png)

I used Chrome's developer console to change the value of our score with `score = 5001;`, and then trigger the game ending with `gameOver()`. This showed the flag over top of the previous Game Over loss message, which is why it looks a little glitchy.

![Screenshot of the Game](/assets/img/dino4.png) ![Screenshot of the Game](/assets/img/dino5.png)

## Solution
The flag is `IERAE{In_f4ct,th3_4uth0r's_h1gh_sc0r3_1s_4b0ut_5000}`. I like that this challenge had 2 ways to solve it, and both were pretty fun.
