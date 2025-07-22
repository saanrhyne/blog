---
layout: post
title: Love GranniE Writeup - DownUnderCTF 2025
description: My writeup for the OSINT/Love GranniE challenge in DownUnderCTF 2025
image: "/assets/img/grannie0.jpg"

categories:
- Writeups
- DownUnderCTF 2025

tags:
- OSINT

date: 2025-7-20 00:02 -0500
---

# OSINT/Love GranniE - a_metre
*Hello dear, it's your Grannie E.*

*My lovely nurse took me out today and I found where I used to go see movies! Back in my day movies didn't talk or have sound! How the times have changed. I've added in a photo from back when I used to live there, with help from my nurse.*

*I'm going for a cuppa now, will call later.*

*Love,*

*Grannie E.*

*--------------------------------*

*Given the image from Grannie E, can you find the name of the movie building, and its current day location? I'll need a suburb too.*

*NOTE: Sometimes old records get out of date, you might need to try the street number next door*

*Flag Format: DUCTF{BuildingName_StreetAddress_Suburb} (case insensitive) - include the street number in the address*

## Initial Thoughts
We are given a seemingly old photo of a bridge. All we need to do is find where it is, then find a movie theater next to it. Seems simple enough, right? (Spoiler alert: It was, but I overcomplicated it)

![bridge](/assets/img/grannie1.jpg)

## Methodology
First, I use Google reverse image search. This yields not 1, but 2 exact matches! Rare for an OSINT challenge.

![rev image search](/assets/img/grannie2.png)

It seems this bridge is the Epping Bridge. 

![bridge](/assets/img/grannie3.png) ![bridge](/assets/img/grannie4.png)

Now, because the document quite clearly says "Australian Government" and this is a CTF hosted in Australia, one would assume that the answer is somewhere in Australia.

For some reason, I did not come to this very logical conclusion, and instead assumed it was Epping in the UK.

Searching for "Epping UK movie theater old" on Google yields the historic [Empire Cinema](https://cinematreasures.org/theaters/29481) in Epping, UK.

![the wrong theater](/assets/img/grannie5.png)

After finding this, I was convinced that the flag was DUCTF{EmpireCinema_134HighStreet_Epping}. I tried many variations, but none of them seemed to work.

I opened a ticket, and a very helpful (and patient) moderator helped me realize that this CTF is hosted in Australia, and there is an Epping in Australia. I somehow missed that on the document I found earlier about the Epping bridge. In my defense, it was late at night when I was working on the challenge initially.

Google searching "Epping Australia movie theater old" yields the historic [Epping Kings Theatre](https://cinematreasures.org/theaters/40752) in Epping, Sydney, Australia.

![the right theater](/assets/img/grannie6.png)

This led me to believe the flag was DUCTF{EppingKingsTheatre_46BeecroftRoad_Epping}. However, that wasn't working. I knew (or really hoped) this was the theater, so I checked to see if it had any other names.

On that same Cinema Treasures listing, I found out that the theater used to be called Cambria Theatre.

![another name???](/assets/img/grannie7.png)

## Solution
The flag is `DUCTF{CambriaTheatre_46BeecroftRoad_Epping}`. This was a fairly easy and fun OSINT challenge, and shoutout to the moderators for putting up with my ridiculousness.
