+++
title = 'Call Gradle Wrapper from nested Directory'
date = 2021-10-29T20:24:48+01:00
draft = true
+++

Save this script as `gw`, make it executable and put it to the search path:

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
