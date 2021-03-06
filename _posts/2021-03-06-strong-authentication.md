## Strong Authentication, Two Factor Authentication, Multi-Factor Authentication - What is it all about?

### The Classic Two Factor Authentication

The classic Two Factor Authentication defines that you need to use two of the possible factors to identify a user:
1. Something you know, e.g. a password or a pin code
2. Something you own, e.g. a device or a secret
3. Something you are, e.g. fingerprint, iris, face, voice, typing or mouse-move characteristics
4. Where you are, GPS or network location

Please note, that none of them uniquely identifies a user. They must be combined to increase the certainty that a returning user is the same person as during the last session. 
The term Multi-Factor Authentication is used to emphasis that more than two facors a are used to identify the user.

### Out of Band Authentication

Two Factor Authentication is often confused with Out of Band Authentication. While Two Factor Authentication can be combined with Out of Band Authentication, these are completely independent techniques. 
Out of Band Authentication tries to mitigate a potentially compromised connection between the user and the server by using a different connection. However in practise it is hard to verify that a different connection is used which is also safer. E.g. mobile text messages (SMS) use a poor encryption while modern mobile apps usually communicate over the same wirless LAN that is used by the desktop computer. And if you use the web-site on the smartphone then you need a second device to do an Out of Band Authentication.

### Why I prefer the term Strong Authentication

Two Factor Authentication somehow implies that the factors have a certain strength but doesn't define it. If your first factor is the password "123456" and your second factor is the country where you are, the authentication is still be weak.
You don't necessary need multiple factors securely identify a returning user. Service users / technical users cannot use classic Two Factor Authentication but if the use a securely stored private-key or even a hardware security module (HSM) or similar device, their authentication is technically much stronger and safer, although it only uses a single authentication factor. From that point-of-view it doesn't make sense to require Two Factor Authentication but Strong Authentication - no matter how it is achieved.

### How can the server verify these things?

A computer cannot distinguish between something you know, something you own and something you are. All these attributes are repsresented as data.

#### Ways to verify Authentication Data

##### Shared Secret
The easiest way to verify a shared secret is to store it and compare it with the received secret, however, these secrects could be stolen by a hacker and he could use them to login and if the user used the same secret for another account the hacker might gain access to that one too. The safest way to verify the secrets is to safe their cryptographic hash-code that uses an individual salt. The salt is needed to increase the entropy in order to mitigate brute-force attacks (unless the secret contains enough entropy and is pure random). Shared Secrets are prone to replay attacks. They can be mitigated by protecting the communication channel and periodically  renew the secret.

##### Public-Key

##### Range / Anomalie Checks

### How are Authentication Factors checked?

#### Something you know


#### Something you own

#### Something you are

#### Where you are


this is usually a private-key or a symmetric-key but it could also be any other shared secret that has enough entropy that you can't remember it and it's nearly impossible to enter it manually.


### Attacks

#### Replay Attack

#### Social Engineering Attack

##### Phishing Attack

#### Interception Attack

##### Man-in-the-middle Attack

##### Man-in-the-browser Attack

#### Bruteforce Attack

##### Offline Bruteforce Attack
##### Online Bruteforce Attack

### Securely Storing Secrets

