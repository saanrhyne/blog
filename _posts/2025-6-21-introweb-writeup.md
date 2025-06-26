---
layout: post
title: Intro to Web (Part 1) Writeup - GPN CTF 2025
description: My writeup for the web/Intro to Web (Part 1) challenge in GPN CTF 2025
image: "/assets/img/introweb0.png"
topic:
- Writeups
tags:
- web
- gpn ctf 2025
date: 2025-6-21 00:01 -0500
---

# web/Intro to Web (Part 1) - finn, vurlo
*5 vulns, 5 stages - can you find them all?*

## Initial Thoughts
We are given the Vuvublog website. In the website, you can see a lovely [demo](https://www.youtube.com/watch?v=dQw4w9WgXcQ), and, once you log in, you can create notes. When you create a note, it displays the title, content, and a fun image.

<img alt="Screenshot of Vuvublog website" src="/assets/img/introweb1.png" height=220px> <img alt="Screenshot of Vuvublog website" src="/assets/img/introweb2.png" height=220px>
<img alt="Screenshot of Vuvublog website" src="/assets/img/introweb3.png" height=220px> <img alt="Screenshot of Vuvublog website" src="/assets/img/introweb4.png" height=220px>

We are also given the files behind the websites. After a little poking around, we determine that the flag for this first stage is stored in an environmental variable. If we can figure out a way to get the website to leak the .env file, we can get the flag.

<img alt="Screenshot of source code" src="/assets/img/introweb5.png" height=190px> <img alt="Screenshot of source code" src="/assets/img/introweb6.png" height=190px>

## Methodology
After looking through some of the source code, I noticed a hidden form value that is submitted. This determines the image that accompanies the note, and could be exploited to leak another file.

<img alt="Screenshot of website source" src="/assets/img/introweb7.png"> 

If we change that value to `.env`, it could leak the environment variables, including our flag for this stage.

<img alt="Screenshot of website source" src="/assets/img/introweb8.png"> 

I did just that, and submitted the form. This results in a normal note, but the image doesn't load.

<img alt="Screenshot of the broken note" src="/assets/img/introweb9.png"> 

If you right click and `Copy image address`, we get a base64 string:

```
data:image/png;base64, RkxBU0tfQVBQX1NFQ1JFVF9LRVk9MjJlNGVjNGU2MTY3Y2ExMWQ0MjA5YzQw
YzJmOGQ0NjQ3ZmEwYzc1MDdhMTYzN2I1NmRhM2MzZWUzZmY1MjVkYjIwNDc3ODY0OTM0OTFlZmNlMmMwZj
RkMDRhOWQwYzUxN2Y4MQpGTEFHX1NUQUdFXzE9R1BOQ1RGe2p1UzdfbDNBa19BbGxfdGhFX3RoSW5HU30K
```

After stripping away the non-b64 components (`data:image/png;base64,`), putting this into [CyberChef](https://gchq.github.io/CyberChef/) yields our flag.

<img alt="Screenshot of CyberChef" src="/assets/img/introweb10.png"> 


## Solution
The flag is `GPNCTF{juS7_l3Ak_All_thE_thInGS}`. I don't main web, so I was pretty happy that I could solve this with help from some people in the GPN CTF Discord.
