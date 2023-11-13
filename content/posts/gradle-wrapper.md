+++
title = 'Call Gradle Wrapper from nested Directory'
date = 2021-10-29T20:24:48+01:00
+++

The following script will allow you to use `gw` instead of `./gradlew` in any subdirectory. `gw` will go up the directory hierarchy until it finds `gradlew` or a gradle settings file.
<!--more-->

Save this script as `gw`, make it executable and add it to the search path:

```
#!/bin/bash
relative_path='.'
while [[ $(realpath $relative_path) != '/' ]]; do
  if [[ -f "${relative_path}/gradlew" ]]; then
    #echo "Found gradlew at ${relative_path}"
    # Found gradlew, execute it.
    ${relative_path}/gradlew "$@"
    break
  fi
  # Check for Gradle settings files.
  if [[ -f "${relative_path}/settings.gradle" || -f "${relative_path}/settings.kts" || -f "${relative_path}/settings.gradle.kts" ]]; then
    # Found a Gradle settings file, stop searching.
    break
  fi
  # Move up one directory.
  relative_path="${relative_path}/.."
done
```


