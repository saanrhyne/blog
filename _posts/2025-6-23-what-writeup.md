---
layout: post
title: What? Writeup - BCACTF 6.0
description: My writeup for the Web/What? challenge in BCACTF 6.0
image: "/assets/img/what0.png"

categories:
- Writeups
- BCACTF 6.0

tags:
- Web
date: 2025-6-23 00:07 -0500
---

# Web/What? - Thomas Raskin
*Surmount the insurmountable. [http://challs.bcactf.com:47861](http://challs.bcactf.com:47861)*

## Initial Thoughts
We are given a website that asks you to input two strings, and then compares their hashes. We are also given a `what.php`, a script that determines the conditions you must meet to get the flag.

![image of website](/assets/img/what1.png)

## Methodology
This is the full php script:

```php
<?php
    if ($_SERVER['REQUEST_METHOD'] === 'POST') {
        $str1 = $_POST['string1'] ?? '';
        $str2 = $_POST['string2'] ?? '';

        $hash1 = md5($str1);
        $hash2 = md5($str2);

        if ($str1 == $str2 || strlen($str1) > 100 || strlen($str2) > 100 ||
            strlen($str1) < 5 || strlen($str2) < 5) {
            echo "No\n";
            exit;
        } else if ($hash1 == $hash2) {
            echo file_get_contents("flag.txt");
            exit;
        }
    }
?>
```

Let's break it down further:
```php
if ($str1 == $str2 || strlen($str1) > 100 || strlen($str2) > 100 ||
            strlen($str1) < 5 || strlen($str2) < 5) {
            echo "No\n";
            exit;
```

If string 1 and string 2 are equal, or either of them are longer than 100 characters or shorter than 5 characters, it won't return the flag.

```php
} else if ($hash1 == $hash2) {
            echo file_get_contents("flag.txt");
            exit;
```

If the MD5 hash of string 1 is equal to the hash of string 2, then it will print the flag.

Two strings who have the same hash but are different are known as hash collisions. On the [MD5 Wikipedia Page](https://en.wikipedia.org/wiki/MD5#Collision_vulnerabilities), the following hash collision is listed:

![hash collision](/assets/img/what2.png)

However, this collision won't work, as both the strings are longer than 100 characters.

On [Twitter](https://x.com/realhashbreaker/status/1770161965006008570), I find this MD5 hash collision:

![hash collision 2](/assets/img/what3.png)

Submitting those two hashes into the form passes all checks, and gets us our flag.

## Solution
The flag is `bcactf{wh0_kn0ws_4nym0r3_11fab08d769a}`. This challenge explored a very interesting phenomenon. It was cool to learn about hash collisions.
