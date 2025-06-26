---
layout: post
title: Dessert Time Writeup - BCACTF 6.0
description: My writeup for the Misc/Dessert Time challenge in BCACTF 6.0
image: "/assets/img/desserttime0.png"

categories:
- Writeups
- BCACTF 6.0

tags:
- Misc
date: 2025-6-23 00:00 -0500
---

# Misc/Dessert Time - Juna Lee and Puhalenthi
*I'm a very good planner, but my robotics competition really fried my brain! I remember eating something for the past few weeks but I just can't seem to remember what. Can you please help me? Here's my schedule for reference*

## Initial Thoughts
We are given the link to a spreadsheet entitled [schedule](https://docs.google.com/spreadsheets/d/152qYlpG-FRBdHEfemX1_zD6dX1y1BO2JVmlxRRTYhDM/edit?usp=sharing). It has columns for each time and date from 3/6 to 4/23, and each column contains a number and a color. It seems to be tracking some sort of consumption.

![Image of the spreadsheet](/assets/img/desserttime1.png)

## Methodology
There are no discernable patterns in the data, and it seems quite arbitrary. When I click on a seemingly empty cell, I notice that it contains a number 1. This hints to me that some data could be obscured in white text.

![Image of the hidden number](/assets/img/desserttime2.png)

I make a copy of the schedule so I can manipulate it further. I select all the text with `Ctrl+A `, and change it all to black. This reveals previously hidden letters in the spreadsheet.

![Image of the hidden letters](/assets/img/desserttime3.png)


Just like the hint says (`I remember eating it early in the morning, but sometimes I would snack on it in the evening too.`), these letters appear in the early morning and in the evening. To get the flag, I deleted all columns and rows without letters, and then put those letters together going from top to bottom and left to right.

![Image of the letters that make up the flag](/assets/img/desserttime4.png)

## Solution

The flag is `bcactf{Apple_pieS_Are_yuMMy}`. I liked the use of conditional formatting in this challenge, and I liked how the challenge creators used it to hide ones in the "blank" columns and use that as a bit of a clue.
