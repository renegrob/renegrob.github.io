---
title: 'Show headers and content of HTTP request in console with cURL'
layout: post
tags: []
category: bash
---

During debugging, I often want to see the returned http headers and the raw output. 
```
curl -X GET -is -o /dev/stdout https://myhost
```
If you need information about the connection establishment / TLS handshake, just add `-v`.
