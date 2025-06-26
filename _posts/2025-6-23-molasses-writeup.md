---
layout: post
title: Molasses Writeup - BCACTF 6.0
description: My writeup for the Misc/Molasses challenge in BCACTF 6.0
image: "/assets/img/molasses0.png"

categories:
- Writeups
- BCACTF 6.0

tags:
- Misc
date: 2025-6-23 00:03 -0500
---

# Misc/Molasses - Thomas Raskin
*This GIF shows the flag letter-by-letter but it's really slow and I don't want to wait all day. Maybe there's a faster way to get the flag?*

## Initial Thoughts
We are given a GIF that is super slow. My first thought is to just find a website where we can speed it up.

## Methodology
I upload the GIF into [Ezgif.com](https://ezgif.com/), and then use the 'frames' feature to view each frame of the GIF. Each frame takes 655.34 seconds, and there are 38 frames. It would take over 415 minutes to view the whole flag! I transcribe the flag, and replace the hyphens with underscores per the hint.

![image of the flag](/assets/img/molasses1.png)


## Solution
The flag is `bcactf{is_it_gif_or_gif_a51fd7ace416}`. For the record, it's GIF with a g sound. JIF is a peanut butter brand. GIF stands for Graphics Interface Format, not Jraphics Interface Format. Here is the sped up GIF if you would like to see it:

![sped up GIF](/assets/img/molasses2.gif)
