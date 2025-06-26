---
layout: post
title: Skibidi Writeup - BCACTF 6.0
description: My writeup for the Rev/Skibidi challenge in BCACTF 6.0
image: "/assets/img/skibidi0.png"

categories:
- Writeups
- BCACTF 6.0

tags:
- Rev
date: 2025-6-23 00:06 -0500
---

# Rev/Skibidi - Colin
*As a True Sigma, I now only write code in the best programming language of all time. See if you can figure out what the flag is.*

## Initial Thoughts
We are given a file entitled `brainrot.skibidi`, which is really just a .txt file. It contains the following:
```skibidi
gyatt gyatt grimaceshake gyatt gyatt gyatt gyatt gyatt skibidi sigma rizz fanumtax skibidi gyatt gyatt
gyatt gyatt ohio sigma ohio gyatt gyatt ohio sigma sigma ohio gyatt grimaceshake gyatt gyatt gyatt
skibidi sigma rizz fanumtax skibidi gyatt gyatt ohio sigma sigma sigma grimaceshake gyatt skibidi sigma
sigma sigma rizz fanumtax skibidi sigma ohio sigma grimaceshake gyatt gyatt gyatt gyatt gyatt skibidi
sigma rizz fanumtax skibidi ohio gyatt grimaceshake sigma sigma skibidi gyatt gyatt gyatt rizz fanumtax
skibidi gyatt gyatt ohio gyatt gyatt gyatt gyatt ohio sigma sigma sigma sigma sigma ohio grimaceshake
gyatt skibidi sigma sigma rizz fanumtax skibidi sigma ohio gyatt grimaceshake gyatt gyatt skibidi sigma
rizz fanumtax skibidi gyatt gyatt ohio gyatt gyatt gyatt gyatt grimaceshake gyatt skibidi sigma sigma
rizz fanumtax skibidi gyatt ohio gyatt grimaceshake gyatt skibidi sigma sigma sigma sigma sigma sigma
rizz fanumtax skibidi sigma ohio gyatt gyatt gyatt gyatt ohio sigma sigma sigma sigma sigma ohio
grimaceshake gyatt skibidi sigma sigma rizz fanumtax skibidi sigma ohio gyatt grimaceshake gyatt gyatt skibidi
sigma rizz fanumtax skibidi gyatt gyatt ohio gyatt gyatt gyatt gyatt grimaceshake gyatt skibidi sigma sigma
rizz fanumtax skibidi gyatt ohio sigma grimaceshake gyatt gyatt skibidi sigma rizz fanumtax skibidi ohio
grimaceshake gyatt gyatt gyatt gyatt gyatt skibidi sigma rizz fanumtax skibidi gyatt gyatt ohio gyatt
gyatt gyatt gyatt gyatt gyatt gyatt gyatt gyatt gyatt gyatt gyatt gyatt gyatt gyatt gyatt
ohio grimaceshake gyatt gyatt gyatt gyatt gyatt skibidi sigma sigma sigma rizz fanumtax skibidi gyatt gyatt
ohio sigma grimaceshake gyatt gyatt gyatt skibidi sigma rizz fanumtax skibidi ohio grimaceshake gyatt gyatt skibidi
sigma rizz fanumtax skibidi gyatt ohio gyatt gyatt gyatt grimaceshake gyatt skibidi sigma sigma rizz fanumtax
skibidi gyatt ohio grimaceshake gyatt gyatt gyatt skibidi sigma rizz fanumtax skibidi sigma sigma ohio sigma
grimaceshake sigma sigma skibidi gyatt gyatt gyatt rizz fanumtax skibidi ohio gyatt gyatt gyatt ohio ohio
gyatt grimaceshake gyatt skibidi sigma sigma rizz fanumtax skibidi gyatt ohio grimaceshake gyatt gyatt gyatt skibidi
sigma rizz fanumtax skibidi sigma sigma ohio sigma grimaceshake gyatt skibidi sigma sigma sigma rizz fanumtax
skibidi ohio grimaceshake gyatt gyatt skibidi sigma rizz fanumtax skibidi gyatt gyatt gyatt gyatt ohio
grimaceshake gyatt skibidi sigma sigma rizz fanumtax skibidi gyatt ohio sigma grimaceshake gyatt gyatt skibidi sigma
rizz fanumtax skibidi sigma ohio sigma sigma sigma sigma ohio gyatt gyatt gyatt gyatt gyatt grimaceshake
gyatt skibidi sigma sigma rizz fanumtax skibidi gyatt ohio grimaceshake gyatt gyatt gyatt gyatt gyatt skibidi
sigma sigma sigma rizz fanumtax skibidi gyatt gyatt ohio sigma grimaceshake gyatt gyatt gyatt skibidi sigma
rizz fanumtax skibidi ohio grimaceshake gyatt gyatt skibidi sigma rizz fanumtax skibidi gyatt ohio gyatt gyatt
gyatt grimaceshake gyatt skibidi sigma sigma rizz fanumtax skibidi gyatt ohio gyatt grimaceshake gyatt skibidi sigma
sigma sigma sigma sigma sigma rizz fanumtax skibidi sigma ohio grimaceshake gyatt skibidi sigma sigma rizz fanumtax
skibidi sigma ohio gyatt grimaceshake gyatt gyatt skibidi sigma rizz fanumtax skibidi gyatt gyatt gyatt gyatt
ohio sigma sigma sigma sigma sigma sigma sigma ohio gyatt gyatt gyatt gyatt gyatt gyatt gyatt
ohio sigma grimaceshake gyatt skibidi sigma sigma rizz fanumtax skibidi ohio grimaceshake gyatt gyatt skibidi sigma
rizz fanumtax skibidi gyatt ohio sigma sigma ohio sigma sigma ohio sigma sigma ohio sigma sigma
grimaceshake gyatt gyatt gyatt skibidi sigma sigma sigma sigma sigma rizz fanumtax skibidi ohio sigma
grimaceshake gyatt gyatt skibidi sigma rizz fanumtax skibidi ohio gyatt grimaceshake gyatt gyatt gyatt skibidi sigma
rizz fanumtax skibidi sigma ohio gyatt gyatt gyatt gyatt gyatt gyatt gyatt ohio grimaceshake gyatt gyatt
gyatt gyatt gyatt skibidi sigma sigma sigma rizz fanumtax skibidi gyatt gyatt ohio sigma grimaceshake gyatt
gyatt gyatt skibidi sigma rizz fanumtax skibidi ohio grimaceshake gyatt gyatt skibidi sigma rizz fanumtax skibidi
gyatt ohio sigma sigma sigma grimaceshake gyatt skibidi sigma sigma rizz fanumtax skibidi sigma ohio gyatt
gyatt gyatt gyatt gyatt gyatt gyatt gyatt gyatt gyatt gyatt gyatt gyatt gyatt gyatt
ohio gyatt grimaceshake gyatt skibidi sigma sigma sigma sigma sigma sigma rizz fanumtax skibidi ohio gyatt
gyatt gyatt ohio ohio skibidi gyatt gyatt grimaceshake gyatt gyatt skibidi sigma sigma sigma rizz fanumtax
skibidi ohio
```

I assumed it was an esoteric programming language, or, a joke programming language not designed for actual use.

## Methodology
After some research, I found the Gen Alpha Brainrot esoteric language on [Esolang Wiki](https://esolangs.org/wiki/Gen_Alpha_Brainrot). This showed that the language was just a variant of "brainflakes" (I will not use the "correct" name of this language, you can find it yourself).

![screenshot](/assets/img/skibidi1.png)

I used Google Docs and the Find and Replace feature (not the most 'techy' solution, but it worked) to convert it into brainflakes.

![screenshot](/assets/img/skibidi2.png)

After doing that, I had:

```brainflakes
 - - [ - - - - - > + < ] > - - - - . + . - - . + + . - [ - - - > + < ] > - - . + + + [ - > + + + <
] > + . + [ - - - - - > + < ] > . - [ + + > - - - < ] > - - . - - - - . + + + + + . [ - > + + < ]
> + . - [ - - > + < ] > - - . - - - - [ - > + + < ] > - . - [ - > + + + + + + < ] > + . - - - - .
+ + + + + . [ - > + + < ] > + . - [ - - > + < ] > - - . - - - - [ - > + + < ] > - . + [ - - > + <
] > . [ - - - - - > + < ] > - - . - - - - - - - - - - - - - - - . [ - - - - - > + + + < ] > - - .
+ [ - - - > + < ] > . [ - - > + < ] > - . - - - [ - > + + < ] > - . [ - - - > + < ] > + + . + [ +
+ > - - - < ] > . - - - . . - [ - > + + < ] > - . [ - - - > + < ] > + + . + [ - > + + + < ] > . [
- - > + < ] > - - - - . [ - > + + < ] > - . + [ - - > + < ] > + . + + + + . - - - - - [ - > + + <
] > - . [ - - - - - > + + + < ] > - - . + [ - - - > + < ] > . [ - - > + < ] > - . - - - [ - > + +
< ] > - . - [ - > + + + + + + < ] > + . [ - > + + < ] > + . - [ - - > + < ] > - - - - . + + + + +
+ + . - - - - - - - . + [ - > + + < ] > . [ - - > + < ] > - . + + . + + . + + . + + [ - - - > + +
+ + + < ] > . + [ - - > + < ] > . - [ - - - > + < ] > + . - - - - - - - . [ - - - - - > + + + < ]
> - - . + [ - - - > + < ] > . [ - - > + < ] > - . + + + [ - > + + < ] > + . - - - - - - - - - - -
- - - . - [ - > + + + + + + < ] > . - - - . . > - - [ - - > + + + < ] > . 
```

I found an online brainflakes compiler on [tutorialsPoint](https://www.tutorialspoint.com/compilers/online-brainfk-compiler.htm), and used that to get the flag.

![screenshot](/assets/img/skibidi3.png)

## Solution
The flag is `bcactf{516m4_516m4_0n_7h3_w411_wh0_15_7h3_5k181d1357_0f_7h3m_411}`. This challenge was an interesting exploration of esoteric programming languages, and I liked it overall.
