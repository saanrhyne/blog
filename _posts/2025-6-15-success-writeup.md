---
layout: post
title: Success Writeup - SmileyCTF 2025
description: My writeup for the Rev/Success challenge in SmileyCTF 2025
image: "/assets/img/success0.png"
comments: true

categories:
- Writeups
- SmileyCTF 2025
tags:
- Rev

date: 2025-6-15 00:00 -0500
---

# Rev/Success - Flocto
*avoid it at all costs*

## Initial Thoughts
We are given a script in .hs, which I learned meant Haskell Script. According to [FileFormat.com](https://docs.fileformat.com/programming/hs/), Haskell is an advanced purely-functional open-source programming language. I did a bit of research, and some ChatGPT-ing to understand the syntax, because who likes reading docs? (spoiler alert: nobody). It seemed to be essentially a logic challenge, you just needed to figure out which values fit the long list of instructions.

![Screenshot of the Initial Script](/assets/img/success1.png)

This is what the start of the script looked like.

![Second Screenshot of the Initial Script](/assets/img/success2.png)

This is what the end of the script looked like.

## Methodology
I converted the script into python code. My idea was to have the script generate random ASCII characters for each part of the flag that we didn't know already, and then check that against the rules. If a rule was matched, I would make that character permanently in that spot, and remove that rule. This seems a bit random, but there was some logic (albeit convoluted) behind it, and it did end up working. I knew it the flag was 39 characters and the format was .;,;.{flag}, so I knew the characters at indices 0-5 and 38. I commented out any rules that didn't involve one of those characters, so that any matches would be verified. I ran the script repeatedly until I got ".;,;.{ipaeine_if_i_made_it_cogpiled!! }".

This obviously wasn't right, so I would comment out some lines that hardcoded characters and re-run the script to see if there was any other matches. This process was made a lot easier because the flag was simple English words and not random characters or words that had letters swapped out for numbers and symbols. Eventually, I got the flag (see below). This probably wasn't the fastest way to solve this challenge, but it worked!

## Script
Here's my script in more detail:

```
import random
from operator import or_, and_, xor

passed = False
chars = []

def format_char(i):
    c = chars[i]
    return f"chars[{i}]={c}('{chr(c)}')"
```
Setting up imports and random stuff

```
def run():
    global passed, chars  # Fix scope issues

    chars = [".", ";", ",", ";", ".", "{"]
    chars = [ord(c) for c in chars]

    while len(chars) != 38:
        if random.randint(1, 2) == 1:
            chars.append(random.randint(97, 122))
        else:
            chars.append(random.randint(48, 57))

    chars[7] = ord("e")
    chars[8] = ord("q")
    chars[10] = ord("i")
    chars[12] = ord("e")
    chars[20] = ord("a")
    chars[31] = ord("i")
    chars[32] = ord("l")
    chars[33] = ord("e")
    chars.append(ord("}"))
```
Creating the chars list and hardcoding the known indices that I got from running the script previously.

```
    if chars[11] * chars[7] == 11990:
        print(f"Check 8 passed: {format_char(11)}, {format_char(7)}")
        passed = True
    if chars[2] + chars[36] == 77:
        print(f"Check 13 passed: {format_char(2)}, {format_char(36)}")
        passed = True
    if chars[7] * chars[15] == 11118:
        print(f"Check 25 passed: {format_char(7)}, {format_char(15)}")
        passed = True

    # if chars[12] * chars[9] == 10403:
    #     print(f"Check 34 passed: {format_char(12)}, {format_char(9)}")

    if xor(chars[25], chars[27]) == 23:
        print(f"Check 35 passed: {format_char(25)}, {format_char(27)}")
        passed = True
    if chars[28] * chars[38] == 13875:
        print(f"Check 49 passed: {format_char(28)}, {format_char(38)}")
        passed = True
    if (chars[27] + chars[26]) + 96 == 290:
        print(f"Check 51 passed: {format_char(27)}, {format_char(26)}")
        passed = True

    # if chars[19] * chars[16] == 10355:
    #     print(f"Check 54 passed: {format_char(19)}, {format_char(16)}")
    # if chars[19] * chars[23] == 10355:
    #     print(f"Check 57 passed: {format_char(19)}, {format_char(23)}")
```
The checks that were commented out involved two indices that I didn't have either of, so if they passed it would be random and probably incorrect. For simplicity, I commented them out until I got one of the characters involved in the check.

```
    if passed == True:
        print(''.join(chr(c) for c in chars))

while passed == False:
    run()
```
This had the script run until a check was passed, and then I was able to figure out the characters that I could add to the hardcoded list, uncomment and delete some checks, and continue on. The whole process (once I had the script written) only took about 20 minutes.

That isn't all of my script (I removed a lot of the checks for brevity, you get the point), and it was changed and had lines deleted or commented out a lot during this process, so I don't have a "final" or "full" version. There was some vibe-coding involved for the format_char function and some of the more repetitive tasks that I was too lazy to do (ie. putting print("Check # passed") after each if statement), but the logic and actual execution was all me.

## Solution
The flag is `.;,;.{imagine_if_i_made_it_compiled!!!}`. This was the first challenge I solved (excluding sanity check) , and I was quite happy with myself, especially considering I didn't expect to solve any challenges during this CTF.
