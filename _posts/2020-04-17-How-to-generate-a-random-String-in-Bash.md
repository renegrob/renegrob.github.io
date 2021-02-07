---
layout: post
title:  "How to create a random String with Bash"
date:   2020-04-18 15:00:00 +0100
categories: bash
---
With this approach you can create nearly every random text or number.

```shell
tr -dc '0-9A-Za-z' < /dev/random | head -c10
``` 

Explanation:

After "tr -dc" you specify all the characters that will not be dropped - yes, we waste a lot of random bytes, but for sporadic manual calls it is usually okay. And "head -c10" means we take the first 10 characters.
