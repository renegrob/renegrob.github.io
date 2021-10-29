---
title: 'How to create a random String with Bash'
layout: post
tags: []
category: bash
---
With this approach you can create nearly every random text or number.

```
tr -dc '0-9A-Za-z' < /dev/random | head -c10
```

Explanation:

After "tr -dc" you specify all the characters that will not be dropped - yes, we waste a lot of random bytes, but for sporadic manual calls it is usually okay. And "head -c10" means we take the first 10 characters.
