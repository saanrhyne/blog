---
layout: post
title: Rev Rev Rev Writeup - IERAE CTF 2025
description: My writeup for the Rev/Rev Rev Rev challenge in IERAE CTF 2025
image: "/assets/img/dino0.png"

categories:
- Writeups
- IERAE CTF 2025

tags:
- Rev
date: 2025-6-22 00:01 -0500
---

# Misc/Rev Rev Rev - Rama
*Reverse it.*

## Initial Thoughts
We are given two files: `chal.py`, a script that encrypts the flag, and `output.txt`, the encrypted flag.

![Photo of chal.py](/assets/img/revrevrev1.png)

The contents of `chal.py`.

```
[-246, -131, -204, -199, -159, -203, -201, -207, -199, -159, -204, -158, -155, -205, -211,
-206, -201, -206, -205, -211, -158, -159, -207, -202, -211, -199, -206, -155, -206, -211,
-204, -200, -200, -200, -203, -208, -159, -199, -133, -187, -191, -174, -187, -183]
```
The contents of `output.txt`.

## Methodology
For this challenge, all we have to do is reverse the chal.py script. First, let's figure out what each line does.

```python
flag = open('flag.txt', 'r').read()
```
This line opens the flag and stores it in the flag variable.

```python
x = [ord(c) for c in flag]
```
This converts each character to its corresponding Unicode point value.

```python
x.reverse()
```
This reverses the order of the list of point values.

```python
y = [i^0xff for i in x]
```
This XORs each point value with 0xff, or 255 in decimal.

```python
z = [~i for i in y]
```
This applies the NOT operator to each value, flipping the bits of each integer.

```python
open('output.txt', 'w').write(str(z))
```
This writes the result to output.txt, which we are given.

All we have to do is write a script that does the opposite of each of these lines in the opposite order.



## Script

```python
enc = [-246, -131, -204, -199, -159, -203, -201, -207, -199, -159, -204, -158, -155, -205, -211,
      -206, -201, -206, -205, -211, -158, -159, -207, -202, -211, -199, -206, -155, -206, -211,
      -204, -200, -200, -200, -203, -208, -159, -199, -133, -187, -191, -174, -187, -183]
z = [~i for i in enc]
y = [i^0xff for i in z]
y.reverse()
x = [chr(c) for c in y]
print(''.join(x))
```
This is my full solution script


```python
enc = [-246, -131, -204, -199, -159, -203, -201, -207, -199, -159, -204, -158, -155, -205, -211,
      -206, -201, -206, -205, -211, -158, -159, -207, -202, -211, -199, -206, -155, -206, -211,
      -204, -200, -200, -200, -203, -208, -159, -199, -133, -187, -191, -174, -187, -183]
```
This reverses `open('output.txt', 'w').write(str(z))` by storing the contents of output.txt in a variable.

```python
z = [~i for i in enc]
```
This reverses `z = [~i for i in y]`, as the bitwise NOT operator is involutive, meaning applying it twice reverts to the original value.

```python
y = [i^0xff for i in z]
```
This reverses `y = [i^0xff for i in x]`, as the XOR operator, just like the bitwise NOT operator, is involutive.

```python
y.reverse()
```
This reverses `x.reverse()`, as reversing a list twice reverts it to the original. (Yet another involutive step!)

```python
x = [chr(c) for c in y]
```
This reverses `x = [ord(c) for c in flag]`, as chr(c) converts each item in the list from its Unicode point value to its character representation.

```python
print(''.join(x))
```
Finally, we join the list together, getting our flag.

## Solution
The flag is `IERAE{9a058884-2e29-61ab-3272-3eb4a9175a94}`. This was a pretty simple and fun rev challenge.
