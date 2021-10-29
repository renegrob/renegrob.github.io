---
title: 'Call Gradle Wrapper from nested Directory'
layout: post
tags: [gradle]
category: bash
---

Save this script as "gw", make it executable and put it to the search path: 

```
#!/bin/bash
relative_path='.'
while [[ $(realpath $relative_path) != '/' ]]; do
  #echo $(realpath $relative_path)
  if [[ -f "${relative_path}/gradlew" ]]; then
    #echo "Found gradlew at ${relative_path}"
    ${relative_path}/gradlew "$@"
    break
  fi
  if [[ -f "${relative_path}/settings.gradle" || -f "${relative_path}/settings.kts" || -f "${relative_path}/settings.gradle.kts" ]]; then
    break
  fi
  relative_path="${relative_path}/.."
done
```

This will allow you to use `gw` instead of `./gradlew` in any subdirectory. `gw` will search up until it finds `gradlew` or a gradle settings file.