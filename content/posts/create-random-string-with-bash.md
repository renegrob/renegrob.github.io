+++
title = 'How to create a random String with Bash'
date = 2020-04-17T19:52:26+01:00
+++
With this approach you can create nearly every random text or number.

```
tr -dc '0-9A-Za-z' < /dev/random | head -c10
```

### Explanation:

`tr -dc` deletes all characters except those specified in the argument. This means that we waste a lot of bytes, but for occasional manual use, this is usually acceptable.  
`| head -c10` prints the first 10 characters of the output of the previous command.
