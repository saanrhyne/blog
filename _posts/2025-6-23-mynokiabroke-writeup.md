---
layout: post
title: My Nokia Broke Writeup - BCACTF 6.0
description: My writeup for the Rev/My Nokia Broke challenge in BCACTF 6.0
image: "/assets/img/mynokiabroke0.png"

categories:
- Writeups
- BCACTF 6.0

tags:
- Rev
date: 2025-6-23 00:04 -0500
---

# Rev/My Nokia Broke - Jacob K.
*Hi, I downloaded this MIDlet app on my new Nokia, but it's asking for a password. Does anyone know what the password is?

Note: the flag is all caps, wrapped in bcactf{}, and there are underscores where line breaks are displayed.*

## Initial Thoughts
We are given `MyNokiaBroke.jar`, a bundle of Java files. The description mentions MIDlet, and I initially think about finding an emulator for it. However, I first upload the file into a .jar decompiler

## Methodology
After uploading the file into [Decompiler.com](https://www.decompiler.com/), I see two main files: `AppMIDlet.java`, and `FlagCanvas.java`. I decide to check out the file with flag in the name.

![files in the .jar](/assets/img/mynokiabroke1.png)

The file contains instructions for drawing the flag.

![the file](/assets/img/mynokiabroke2.png)

I convert it to Python using turtle, because I don't feel like downloading Java.

```python
import turtle

screen = turtle.Screen()
screen.bgcolor("white")

pen = turtle.Turtle()
pen.speed(0)
pen.color("red")

def draw_line(x1, y1, x2, y2):
    pen.penup()
    pen.goto(x1 - 100, 200 - y1)
    pen.pendown()
    pen.goto(x2 - 100, 200 - y2)

draw_line(140, 10, 160, 10)
draw_line(110, 130, 110, 170)
draw_line(50, 130, 50, 170)
draw_line(10, 110, 30, 110)
draw_line(105, 50, 120, 10)
draw_line(180, 130, 180, 170)
draw_line(50, 110, 70, 110)
draw_line(20, 70, 20, 110)
draw_line(160, 50, 160, 10)
draw_line(90, 10, 105, 50)
draw_line(50, 10, 70, 10)
draw_line(10, 10, 30, 10)
draw_line(120, 50, 120, 10)
draw_line(150, 130, 150, 170)
draw_line(140, 50, 160, 50)
draw_line(10, 130, 30, 130)
draw_line(90, 170, 110, 170)
draw_line(50, 70, 50, 90)
draw_line(30, 150, 20, 150)
draw_line(30, 150, 30, 170)
draw_line(90, 150, 110, 150)
draw_line(50, 150, 70, 170)
draw_line(20, 10, 20, 50)
draw_line(140, 30, 160, 30)
draw_line(20, 50, 10, 50)
draw_line(70, 90, 70, 110)
draw_line(50, 70, 70, 70)
draw_line(170, 130, 190, 130)
draw_line(50, 25, 50, 50)
draw_line(10, 170, 30, 170)
draw_line(10, 170, 10, 130)
draw_line(90, 130, 110, 130)
draw_line(70, 10, 70, 25)
draw_line(150, 150, 130, 150)
draw_line(50, 25, 70, 25)
draw_line(10, 90, 20, 70)
draw_line(90, 10, 90, 50)
draw_line(130, 130, 130, 150)
draw_line(70, 90, 50, 90)
draw_line(50, 50, 70, 50)

pen.penup()
pen.goto(50 - 100, 200 - 130)
pen.pendown()
pen.goto(70 - 100, 200 - 130)
pen.goto(70 - 100, 200 - 150)
pen.goto(50 - 100, 200 - 150)
pen.goto(50 - 100, 200 - 130)
```

This yields the following drawing, thanks to turtle.

![drawing](/assets/img/mynokiabroke3.png)

## Solution
The flag is `bcactf{J2M3_1S_GRE4T}`. There were probably other ways to solve this challenge involved MIDlet or a Nokia emulator, but I chose the simplest way.
