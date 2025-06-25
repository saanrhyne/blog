---
layout: post
title: Sky Writeup - SmileyCTF 2025
description: My writeup for the misc/sky challenge in SmileyCTF 2025
image: "/assets/img/sky0.png"
category:
- Writeups
tags:
- misc
- smileyctf 2025
date: 2025-6-15 00:02 -0500
---

# misc/sky - smashmaster
*look at the sky, what do you see? a bird? a plane? no, its a challenge about the sky! (autocomplete wrote everything after the first 4 words)*


## Initial Thoughts
We are given a photo of a palm tree, a bit of a building, and some sail shades. The palm tree and sail shades indicated it was somewhere warm and sunny, probably Florida or California. The architecture and coloring of the
building in the right looked a bit more like a Californian villa to me. My first thought was just reverse image search.

<img src="/assets/img/sky1.png" alt="Image Attachment for the Challenge" style="width:300px;"/>


## Methodology
After running it through lots of reverse image searchers, and even finding someone who [posted the photo on r/guessthecity](https://www.reddit.com/r/guessthecity/comments/1lb0vva/guess_this_city/) and hoped to have someone
do the work for them, I found [Picarta](https://picarta.ai/). It analyzed the image, and gave me, among other results, La Jolla, with a GPS location around: 32.8•••••,-117.2•••••. The website hid the full GPS details behind
a signup-wall, and maybe we could've solved the challenge faster if I'd made an account, but who knows.

Anyways, I decided to research La Jolla, San Diego, California. The sail shades still stood out to me as a clue that would help a lot. I searched for sail shades in La Jolla and, after scrolling through images, I found
[studio.MK Design](https://www.studiomkdesign.com/tensile-structures), which had constructed shade sails (not sail shades, as I thought they were called) at the Westfield UTC in none other than La Jolla, CA. This coincided
with another team member saying "I think it's in Westfield UTC mall." He said he found it via Google image search, so kudos to him.

I googled "Westfield UTC Mall Lat Long" and tried a few different results in the coordinate input server, and 32.871274, -117.210659 worked, getting us our 3rd solve of the competition.

![Screenshot of Inputting Coordinates into Checker](/assets/img/sky2.png)

## Solution

The flag is `.;,;.{g00gl3_ai_th1nks_th3s3_pr0duc3_r3n3w3bl3_3n3rgy_1ma0}`. This was the third challenge we solved, and was a team effort. OSINT challenges are lots of fun, especially when you have to use logic and you can't just find the image on Instagram somwhere.
