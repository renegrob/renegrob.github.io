+++
title = 'How to see HTTP headers and raw output during debugging with cURL'
date = 2022-07-19T20:27:04+01:00
draft = true
+++
When debugging, it is often helpful to see the returned HTTP headers and the raw output of a curl request. This can be done using the following command:
```
curl -X GET -is -o /dev/stdout https://myhost
```
If you need information about the connection establishment and TLS handshake, you can add the -v flag to the command:
```
curl -X GET -isv -o /dev/stdout https://myhost
```