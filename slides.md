class: center, middle, bgblue
#SSH and Networking

**By Jonathan Jimenez**

Slides are available on the codetech github
???
Slides are at `github.com/codetech` then click `ssh-networking-presentation` scroll down and click where it says `click me`
---

#Topics
This presentation will lightly cover:
- The shell and telnet
- Public Key Cryptography
- Somthing else

And in detail
- How to set up ssh to connect using a public key
- Something else
---

class: center, middle
#Citizen Four
???
At this point we play a short clip from the citezen four movie talking about keys, and somebody uses rsync
---

class: center, middle, inverse
#RSA
---

class: center, middle
![something](1.png)
???
```
  +-------+                                  +-------+
  |       |+--------+                        |       |
  | Alice || Secret |--------------------->  |  Bob  |
  |       |+--------+                        |       |
  +-------+                                  +-------+
```
---
class: center, middle
![something](2.png)
???
```
  +-------+                                  +-------+
  |       |                        +--------+|       |
  | Alice |                        | Secret ||  Bob  |
  |       |                        +--------+|       |
  +-------+                                  +-------+
```
---
class: center, middle
![something](3.png)
???
```
  +-----------------+
  |  Secure System  |
  |                 |
  +-----------------+------------------------------------+
  |                                                      |
  | +-------+                                  +-------+ |
  | |       |+--------+                        |       | |
  | | Alice || Secret |--------------------->  |  Bob  | |
  | |       |+--------+                        |       | |
  | +-------+                                  +-------+ |
  |                                                      |
  +------------------------------------------------------+
```
---
class: center, middle
![something](4.png)
???
```
  +-----------------+
  |  Secure System  |
  |                 |
  +-----------------+------------------------------------+
  |                                                      |
  | +-------+                                  +-------+ |
  | |       |                        +--------+|       | |
  | | Alice |                        | Secret ||  Bob  | |
  | |       |                        +--------+|       | |
  | +-------+                                  +-------+ |
  |                                                      |
  +------------------------------------------------------+
```
---
class: center, middle
![something](5.png)
???
```
  +-----------------+                  +-----------------+
  |  Secure System  |                  |  Secure System  |
  |                 |                  |                 |
  +-----------------+----+         +---+-----------------+
  |                      |         |                     |
  | +-------+            |         |           +-------+ |
  | |       |+--------+  |         |           |       | |
  | | Alice || Secret |--+---------+-------->  |  Bob  | |
  | |       |+--------+  |         |           |       | |
  | +-------+            |         |           +-------+ |
  |                      |         |                     |
  +----------------------+         +---------------------+
```
---
class: center, middle
![something](6.png)
???
```
  +-----------------+                  +-----------------+
  |  Secure System  |                  |  Secure System  |
  |                 |                  |                 |
  +-----------------+----+         +---+-----------------+
  | +-------+            |         |           +-------+ |
  | |       |            |         | +--------+|       | |
  | | Alice |            |         | | Secret ||  Bob  | |
  | |       |            |         | +--------+|       | |
  | +-------+            |         |           +-------+ |
  |                      |         |                     |
  +----------------------+         +---------------------+
```
---
class: center, middle
![something](7.png)
???
```
  +-----------------+                  +-----------------+
  |  Secure System  |                  |  Secure System  |
  |                 |                  |                 |
  +-----------------+----+         +---+-----------------+
  | +-------+            |         |           +-------+ |
  | |       |            |         | +--------+|       | |
  | | Alice |            |         | | Secret ||  Bob  | |
  | |       |            |         | +--------+|       | |
  | +-------+            |         |           +-------+ |
  |                      |         |                     |
  +----------------------+         +---------------------+

  +----------------------+         +---------------------+
  | +-------+            |         |           +-------+ |
  | |       |            |         | +--------+|       | |
  | | Alice |            |         | | Secret ||  Bob  | |
  | |       |            |         | +--------+|       | |
  | +-------+            |         |           +-------+ |
  |                      |         |                     |
  +----------------------+         +---------------------+
```
---
class: center, middle
![something](8.png)
???
```
  +----------------------+         +---------------------+
  |                      |         |                     |
  | +-------+            |  +----+ |           +-------+ |
  | |       |+--------+  |  |    | |           |       | |
  | | Alice || Secret |--+--+Eve +-+-------->  |  Bob  | |
  | |       |+--------+  |  |    | |           |       | |
  | +-------+            |  +----+ |           +-------+ |
  |                      |         |                     |
  +----------------------+         +---------------------+
```
---
class: center, middle
![something](9.png)
???
```
  +----------------------+         +---------------------+
  | +-------+            |         |           +-------+ |
  | |       |            |         | +--------+|       | |
  | | Alice |            |         | | Secret ||  Bob  | |
  | |       |            |         | +--------+|       | |
  | +-------+            |         |           +-------+ |
  |                      |         |                     |
  +----------------------+         +---------------------+

  +----+
  |    |+--------+
  |Eve || Secret |
  |    |+--------+
  +----+
```
---
class: center, middle
![something](10.png)
???
```
  +------------------------------------------------------+
  |                                                      |
  | +-------+                 +-------+                  |
  | |       |+--------+       |       |       +--------+ |
  | | Alice || Secret |-------|Crypt  |-----> | Frperg | |
  | |       |+--------+       |       |       +--------+ |
  | +-------+                 +-------+                  |
  |                                                      |
  +------------------------------------------------------+
```
---
class: center, middle
![something](11.png)
???
```
  +------------------------------------------------------+
  |                                                      |
  | +-------+                 +-------+                  |
  | |       |+--------+       |       |       +--------+ |
  | | Alice || Secret |-------|Crypt  |-----> | Frperg | |
  | |       |+--------+       |       |       +--------+ |
  | +-------+                 +-------+                  |
  |                                                      |
  +------------------------------------------------------+

  +----------------------+         +---------------------+
  |                      |         |                     |
  | +-------+            |         |           +-------+ |
  | |       |+--------+  |         |           |       | |
  | | Alice || Frperg |--+---------+-------->  |  Bob  | |
  | |       |+--------+  |         |           |       | |
  | +-------+            |         |           +-------+ |
  |                      |         |                     |
  +----------------------+         +---------------------+
```
---
class: center, middle
![something](12.png)
???
```
  +------------------------------------------------------+
  |                                                      |
  | +-------+                 +-------+                  |
  | |       |+--------+       |       |       +--------+ |
  | | Alice || Secret |-------|Crypt  |-----> | Frperg | |
  | |       |+--------+       |       |       +--------+ |
  | +-------+                 +-------+                  |
  |                                                      |
  +------------------------------------------------------+

  +----------------------+         +---------------------+
  | +-------+            |         |           +-------+ |
  | |       |            |         | +--------+|       | |
  | | Alice |            |         | | Frperg ||  Bob  | |
  | |       |            |         | +--------+|       | |
  | +-------+            |         |           +-------+ |
  |                      |         |                     |
  +----------------------+         +---------------------+
```
---
class: center, middle
![something](13.png)
???
```
  +------------------------------------------------------+
  |                                                      |
  | +-------+                 +-------+                  |
  | |       |+--------+       |       |       +--------+ |
  | | Alice || Secret |-------|Crypt  |-----> | Frperg | |
  | |       |+--------+       |       |       +--------+ |
  | +-------+                 +-------+                  |
  |                                                      |
  +------------------------------------------------------+

  +----------------------+         +---------------------+
  | +-------+            |         |           +-------+ |
  | |       |            |         | +--------+|       | |
  | | Alice |            |         | | Frperg ||  Bob  | |
  | |       |            |         | +--------+|       | |
  | +-------+            |         |           +-------+ |
  |                      |         |                     |
  +----------------------+         +---------------------+

  +------------------------------------------------------+
  |                                                      |
  |                  +-------+                 +-------+ |
  | +--------+       |       |       +--------+|       | |
  | | Secret | <-----|Crypt  |-------| Frperg ||  Bob  | |
  | +--------+       |       |       +--------+|       | |
  |                  +-------+                 +-------+ |
  |                                                      |
  +------------------------------------------------------+
```
---
class: center, middle
![something](14.png)
???
```
  +----------------------+         +---------------------+
  |                      |         |                     |
  | +-------+            |         |           +-------+ |
  | |       |+--------+  |         |           |       | |
  | | Alice || PassWd |--+---------+-------->  |  Bob  | |
  | |       |+--------+  |         |           |       | |
  | +-------+            |         |           +-------+ |
  |                      |         |                     |
  +----------------------+         +---------------------+
```
---
class: center, middle
![something](15.png)
???
```
  +----------------------+         +---------------------+
  | +-------+            |         |           +-------+ |
  | |       |            |         | +--------+|       | |
  | | Alice |            |         | | PassWd ||  Bob  | |
  | |       |            |         | +--------+|       | |
  | +-------+            |         |           +-------+ |
  |                      |         |                     |
  +----------------------+         +---------------------+
```
---
class: center, middle
![something](16.png)
???
```
  +----------------------+         +---------------------+
  |                      |         |                     |
  | +-------+            |  +----+ |           +-------+ |
  | |       |+--------+  |  |    | |           |       | |
  | | Alice || PassWd |--+--+Eve +-+-------->  |  Bob  | |
  | |       |+--------+  |  |    | |           |       | |
  | +-------+            |  +----+ |           +-------+ |
  |                      |         |                     |
  +----------------------+         +---------------------+
```
---
class: center, middle
![something](17.png)
???
```
  +----------------------+         +---------------------+
  | +-------+            |         |           +-------+ |
  | |       |            |         | +--------+|       | |
  | | Alice |            |         | | PassWd ||  Bob  | |
  | |       |            |         | +--------+|       | |
  | +-------+            |         |           +-------+ |
  |                      |         |                     |
  +----------------------+         +---------------------+

  +----+
  |    |+--------+
  |Eve || PassWd |
  |    |+--------+
  +----+
```
---
class: center, middle
![something](18.png)
???
```
  +------------------------------------------------------+
  |                                                      |
  | +-------+                 +-------+                  |
  | |       |+--------+       |       |       +--------+ |
  | | Alice || PassWd |-------|Crypt  |-----> | CnffJq | |
  | |       |+--------+       |       |       +--------+ |
  | +-------+                 +-------+                  |
  |                                                      |
  +------------------------------------------------------+
```
---
class: center, middle
![something](19.png)
???
```
+------------------------------------------------------+
|                                                      |
| +-------+                 +-------+                  |
| |       |+--------+       |       |       +--------+ |
| | Alice || PassWd |-------|Crypt  |-----> | CnffJq | |
| |       |+--------+       |       |       +--------+ |
| +-------+                 +-------+                  |
|                                                      |
+------------------------------------------------------+

+----------------------+         +---------------------+
|                      |         |                     |
| +-------+            |         |           +-------+ |
| |       |+--------+  |         |           |       | |
| | Alice || CnffJq |--+---------+-------->  |  Bob  | |
| |       |+--------+  |         |           |       | |
| +-------+            |         |           +-------+ |
|                      |         |                     |
+----------------------+         +---------------------+
```
---
class: center, middle
![something](20.png)
???
```
  +------------------------------------------------------+
  |                                                      |
  | +-------+                 +-------+                  |
  | |       |+--------+       |       |       +--------+ |
  | | Alice || PassWd |-------|Crypt  |-----> | CnffJq | |
  | |       |+--------+       |       |       +--------+ |
  | +-------+                 +-------+                  |
  |                                                      |
  +------------------------------------------------------+

  +----------------------+         +---------------------+
  | +-------+            |         |           +-------+ |
  | |       |            |         | +--------+|       | |
  | | Alice |            |         | | CnffJq ||  Bob  | |
  | |       |            |         | +--------+|       | |
  | +-------+            |         |           +-------+ |
  |                      |         |                     |
  +----------------------+         +---------------------+
```
---

class: center, middle
![something](21.png)
???
```
  +------------------------------------------------------+
  |                                                      |
  | +-------+                 +-------+                  |
  | |       |+--------+       |       |       +--------+ |
  | | Alice || PassWd |-------|Crypt  |-----> | CnffJq | |
  | |       |+--------+       |       |       +--------+ |
  | +-------+                 +-------+                  |
  |                                                      |
  +------------------------------------------------------+

  +----------------------+         +---------------------+
  | +-------+            |         |           +-------+ |
  | |       |            |         | +--------+|       | |
  | | Alice |            |         | | CnffJq ||  Bob  | |
  | |       |            |         | +--------+|       | |
  | +-------+            |         |           +-------+ |
  |                      |         |                     |
  +----------------------+         +---------------------+

  +------------------------------------------------------+
  |                                                      |
  |                  +-------+                 +-------+ |
  | +--------+       |       |       +--------+|       | |
  | | PassWd | <-----|Crypt  |-------| CnffJq ||  Bob  | |
  | +--------+       |       |       +--------+|       | |
  |                  +-------+                 +-------+ |
  |                                                      |
  +------------------------------------------------------+
```
---
#RSA

- **Cryptosystem** - Other encryption methods are built on top of RSA

--

- **Asymetrical** - You don't use the same key to encrypt and decrypt.

--

- Developed in 1973 by Ron **R**ivest, Adi **S**hamir, and Leonard **A**dleman

--

- Based on difficulty of factoring large numbers
---

class: center, middle, inverse
#SSH
???
The namesake of this presntation
---

#Shell (SH)

An operating system's `shell` is a program that gives you an alternative to the `gui` for controlling your computer.

Shells are text based but the good ones have .yellow[c].blue[o].orange[l].pink[o].cyan[r].green[s] and clickable [links](https://site), as well as support for utf-8

--

For example, if you want to open a browser to google.com you would enter

`$ open https://www.google.com` on OSX

`$ start https://www.google.com` on Windows

`$ xdg-open https://www.google.com` on Linux

???
all three options look a the `https://` to see what to do with it

dont type `$` it just means this is a shell command
--

Popular Shells
- CMD
- SH
- BASH (Bourne Again Shell)
- ZSH
- CSK
- terminal

---
#Let's give it a try:

Open CMD, or whatever shell you preffer
```bash
  $ echo hello world
```
--
```bash
  hello world
```
--
`$ ipconfig` On Windows

`$ ifconfig` On Unix

.orange[you should see information about your internet connection]
???
`ipconfig` is what tv shows think hacking is about

---
#Telnet

But what if I'm far away from my computer,
--
 in another country,
--
 all the way in another room!?

--
>Wikipedia:

>Telnet is a session layer protocol used on the Internet or local area networks to provide a bidirectional interactive text-oriented communication facility using a virtual terminal connection.

--

Things to know, it's (really) simple, but  also (really) insecure.

--

.orange[this is useful]
```bash
  $ telnet rainmaker.wunderground.com
```
???
putty implements the telnet protocol
--

.orange[this is a fun one]
```bash
  $ telnet towel.blinkenlights.nl
```
---
#Secure Shell (SSH)

An application level protocol for using Shells securely and remotely

>Wikipedia:

>[...] SSH, is a [...] network protocol to allow remote login and other network services to operate securely over an insecure network.

>SSH was designed as a replacement for Telnet and for insecure remote shell protocols...

.gray.small[ Note: You can use any application through an ssh tunnel, but that's another talk.]
---

#SSH
Let's connect to a server via ssh

server name is `codetech.jonjmz.com`

username is `coder#`

password is `coder#`

where `#` stands for any number from 1 to 100

--

```bash
  $ ssh coder1@codetech.jonjmz.com
```

--

.orange[and the response is]
```bash
  coder1@codetech.jonjmz.com's password:
```
.orange[so we enter]
```bash
  coder1
```
---

.orange[We should see a welcome message]
```bash
     ___          _        _____          _       __  __
    / __\___   __| | ___  /__   \___  ___| |__   / _\/ _\  /\  /\
   / /  / _ \ / _` |/ _ \   / /\/ _ \/ __| '_ \  \ \ \ \  / /_/ /
  / /__| (_) | (_| |  __/  / / |  __/ (__| | | | _\ \_\ \/ __  /
  \____/\___/ \__,_|\___|  \/   \___|\___|_| |_| \__/\__/\/ /_/

   _____          _   _               __
  /__   \___  ___| |_(_)_ __   __ _  / _\ ___ _ ____   _____ _ __
    / /\/ _ \/ __| __| | '_ \ / _` | \ \ / _ \ '__\ \ / / _ \ '__|
   / / |  __/\__ \ |_| | | | | (_| | _\ \  __/ |   \ V /  __/ |
   \/   \___||___/\__|_|_| |_|\__, | \__/\___|_|    \_/ \___|_|
                              |___/
                Please don't do anything bad.
```

--

.orange[lets see where we are]
```bash
  $ pwd
```

.orange[and we get]
```bash
  $ /home/coder1
```
---

.orange[What do we have available to us?]
```bash
  $ ls -la
```
```bash
  total 8
  drwxr-xr-x   2 coder1 coders 4096 Oct  2 07:09 .
  drwxr-xr-x 104 root   root   4096 Oct  2 07:09 ..
```

--

But what we want is to connect using a public key.
---



First we need to generate out RSA key

```bash
  $ ssh-keygen
```
--

```bash
  Generating public/private rsa key pair.
  Enter file in which to save the key (.ssh/id_rsa): credential
  Enter passphrase (empty for no passphrase):
  Enter same passphrase again:
  Your identification has been saved in credential.
  Your public key has been saved in credential.pub.
  The key fingerprint is:
  SHA256:8JXa6V6xsiThJRSsBvucQeFXn7JbOoWqcVRNtz85Obs lintycompiler@Heliophere
  The key's randomart image is:
  +---[RSA 2048]----+
  |      .o. . . .  |
  |    ... .o = o . |
  |     +o.o = + .  |
  |    . += = =   .o|
  |     + oS * +  *.|
  |      +o * = o  =|
  |      . = B o  . |
  |       + + =    .|
  |      .   o    E |
  +----[SHA256]-----+
```
---

Let's see what we've done.

`$ dir` On windows

`$ ls -l` On Unix

--

```bash
  drwxr-xr-x   4 lintycompiler  staff   136 Jul 18 11:21 Applications
  drwxr-xr-x@  5 lintycompiler  staff   170 Sep 27 10:25 Applications (Parallels)
  drwx------+ 17 lintycompiler  staff   578 Sep 30 14:13 Desktop
  drwxr-xr-x   6 lintycompiler  staff   204 Sep 11 12:01 Dev
  drwx------+ 13 lintycompiler  staff   442 Sep 19 14:05 Documents
  drwx------+ 10 lintycompiler  staff   340 Sep 30 15:44 Downloads
  drwx------@ 59 lintycompiler  staff  2006 Sep 22 14:25 Library
  drwx------+  9 lintycompiler  staff   306 Jul 19 09:49 Movies
  drwx------+  4 lintycompiler  staff   136 Jun 13 22:49 Music
  drwx------+  8 lintycompiler  staff   272 Jul 19 09:46 Pictures
  drwxr-xr-x+  5 lintycompiler  staff   170 Jun 13 17:19 Public
  drwxr-xr-x   4 lintycompiler  staff   136 Jun 30 16:54 Scripts
  -rw-------   1 lintycompiler  staff  1679 Oct  1 15:30 credential
  -rw-r--r--   1 lintycompiler  staff   406 Oct  1 15:30 credential.pub
  -rw-r--r--   1 lintycompiler  staff   760 Sep 30 21:20 file
  drwxr-xr-x   6 lintycompiler  staff   204 Jun 22 19:32 go
```

---

`$ type credential` On Windows

`$ cat credential` On Unix

--

```bash
  -----BEGIN RSA PRIVATE KEY-----
  MIIEpQIBAAKCAQEA6DkVcWsFzvhgNswh7bJXdMdg+iM0U90Q4skRnErdK50/1MXm
  je+TEUj9bwFzDDI/mt0lJ/u7DLT/pQiY9hZ19MIBRLIKrO72gCX41SuIdn2/gyfG
  bNHYNfejNAOjEO/K6RVH2JLTXGkSCbMvjVPjwXgSWh7d3IlAWr9k2a9SfgI8Kp3V
  /FhvNJZMAe7sNoOAt7/b5cTTHcNB+Tv/y3ExTpORCuhuLX+5RMAIICDp/arQExCA
  AkxCnTOtZr4Hfh/FTzq5iIqtippoHcZyJZdzqmIFPDymd+61g7xz2rrmNLCcbQ1C
  ycAjG4bT6oOzecGuqO1TXTHEA8xmEk4IC5mzZQIDAQABAoIBAQDKdHntV5DI0GGR
  ZIZv5Hu6o9g4O1jzhFekYAeqatpHm+B6b86BD8z31NqeXHUgvO4W5ZXvNdftTB9U
  khpI8WwE5t6UNWR5QBxHvNMjhcCDDT5Z6eNkG86TvkHapxETQvt0Gcl5VwhOGIxR
  SJa8b9awZS4aw65JBp/Effg+kEsq7r7BsM4PecGLL7PWOXgSh4NVxkXVL5FnQ6/u
  VHB44VRJdlxD1xRzF/kP744R6LQiyXHvshjgKxA9Z1fh4URljJ46icrAQGbUzPrQ
  wMmZgE1evIuOmn1hI9S6vfl4o/dOg6AnbxdR234ttCWlOKggv8v6G5vzGKntEy7m
  eYY31B5BAoGBAPPS3XISRcgKitfhWACZGubyuXDAH0oTKaY1ED9K17XtYAyh+3aZ
  UrAqKgpciATGFCdmfNp9djzrbI9rX4Qxp2X5beBtuaF+CW2IyJMJHo7+9Se9d2/4
  IGP/ycEjWqy4riC/JvIh/NKhd4Rnjtfdj7x+V6cnwCdeNlyVj3KdI6lvAoGBAPPR
  6S6mAV8YVQKwewqH1QoLz3P8L7ivB+es7JmECFNB5bWdPkvpJJfxnPQ5EIQ+H33D
  bWXrw2GiC0Twbniog4n1Mx++pZJxINwNhRn+PzmNoUuPFpjygJTouufO1Fw+BZJa
  4zzvzCHELOcpo9ySVpfwDYJG1+zE2vKlpBLhZz5rAoGBAPELZ+1b7yzCb1zY5H1C
  33uuPnIfHU/H/gbYssU/ol2y3J/gi49GKJ8MMB+qNrYxdL827Pu7yOaU//ARgI5Z
  4FpJ6rxS/Y+P4JYvAcuK2nEX0RmGj8tcC/mQaM7NutjCgzLQhxodS6qYAmYdUvRJ
  j84TQWh5PdgtpaSGHxh6DUV1AoGBANr4yH0WpeCrz51MthQtDY2qMbQu5wTsXSMa
  UJtG0ttDMXQ8NjiiuDSlz5oerdC2oj2mh9ejN6O1jn1pmS1P2mLKDhISfEzawPIg
  Skuf5VRg+F0NsvPFxuj1YvbQ8DOvl/1rFu4hRqmEr/cjlICCBLcL5nX7/ewsl56Y
  WJSETt7lAoGAA4pHMbJSXlCLgUGP2ANIwqBnKhD5ACcg/pLabTaUMekFFhUGMsej
  A5UQEs6fPNsPfxFf96CtlCN2u3RkB71rjwvIeJg5JbAEwgmB8dgPbtiWph9ecMuC
  rAUb6Nz7SPnr8Xpeb600lFGn0hC4vTkTsROXGoMkAReevdje7tIb1rI=
  -----END RSA PRIVATE KEY-----
```
---

#Uploading Key
Now we need to get out **public** key onto the server

.small[.gray[Remember the private key should never be sent out]]

--

We will use scp, specificly winscp, this should be installed already. Open it now.
???
- The rest should be done in the gui.
- We need to make a folder called .ssh
- Copy over the public key
- Rename it to **authorized_keys**
---

#Logging In
Now we can log into the server using our key
```bash
  $ ssh coder1@codetech.jonjmz.com -i credential
```

--
So now we know how to set up ssh to use a public/private key pair as credentials.

At this point you would deactivate password loggins by edditing `/etc/ssh/ssh_config`
---

class: center, middle, inverse
#GPG
---

#PGP
>Wikipedia:

>Pretty Good Privacy (PGP) is a data encryption and decryption computer program that provides cryptographic privacy and authentication for data communication.
---

#GPG
>Wikipedia:

>GNU Privacy Guard (GnuPG or GPG) is a free software replacement for the Symantec's PGP cryptographic software suite.

--

.gray.small[Note: GNU stands for GNU Not Unix, think about that for a second.]
---

#Signing Things

(not on the dotted line)

.orange[Let's sign a statement, a signiture verifies that the signer is seeing the same message]
```bash
  $ gpg --sign statement.txt
```

--

.orange[let's see what we have]
```bash
  $ cat statement.sig
```

--

.orange[Output:]
```bash
statement.txtV�JExecute order 66
V�J
	���e;J�ﴩ�B7J��2a�d�?
^,��s�g�d��΃["O��,�����>�ux��>�xͰ�i�����]�
                                           �zʛF�

�4��W�Ѕ�_�րó�-�3B�Ҭ襚%�Ԥ�Kq���\x�e��y���4��3��VqN{v~-�h��T�6m<'͈��n�í��Nυ�2��)9��@���y�;3��t��N���<�YEIFƸ���U�2�^)QާD?(�U&�W���'9r�E4���%
```

---

.orange[That's no good, it looks like Binary]
```bash
  $ hexdump -C statement.txt.gpg
```

--

.orange[Output]
```
  00000000  a3 01 01 54 01 ab fe 90  0d 03 00 08 01 ac 85 94  |...T............|
  00000010  65 3b 4a d5 ef 01 ac 24  62 0d 73 74 61 74 65 6d  |e;J....$b.statem|
  00000020  65 6e 74 2e 74 78 74 56  06 d7 4a 45 78 65 63 75  |ent.txtV..JExecu|
  00000030  74 65 20 6f 72 64 65 72  20 36 36 0a 89 01 1c 04  |te order 66.....|
  00000040  00 01 08 00 06 05 02 56  06 d7 4a 00 0a 09 10 ac  |.......V..J.....|
  00000050  85 94 65 3b 4a d5 ef b4  a9 07 ff 42 0f 37 4a e0  |..e;J......B.7J.|
  00000060  e6 32 61 b5 64 07 b8 3f  0a df 3f 0d 5e 2c b0 99  |.2a.d..?..?.^,..|
  00000070  73 98 67 01 d3 64 fb d2  ce 83 5b c2 90 22 4f 9e  |s.g..d....[.."O.|
  00000080  03 b1 2c dd 0e d3 e7 a3  c3 fb 3e a9 75 1a 78 8a  |..,.......>.u.x.|
  00000090  e9 3e b5 78 cd b0 ea 69  bc af 85 d2 c0 9f 5d f4  |.>.x...i......].|
  000000a0  87 0b 88 d6 a0 01 7a ca  9b 46 e6 0a 08 0c ed 83  |......z..F......|
  000000b0  34 f4 f4 57 eb d0 85 cf  5f 87 d6 80 c3 b3 9a 1e  |4..W...._.......|
  000000c0  2d f3 33 42 97 d2 ac e8  a5 9a 25 e3 b2 d4 a4 89  |-.3B......%.....|
  000000d0  4b 71 c4 13 f4 11 f7 84  5c 78 f1 65 98 94 79 05  |Kq......\x.e..y.|
  000000e0  06 88 c5 ed 34 97 aa cc  8c 33 1e 82 80 56 71 4e  |....4....3...VqN|
  000000f0  07 17 7b 76 7e 2d 9a 68  a2 c4 54 b5 36 6d 3c 27  |..{v~-.h..T.6m<'|
  00000100  cd 88 1a bd b9 6e f7 c3  ad aa db 4e cf 85 0e af  |.....n.....N....|
  00000110  7f 32 94 74 08 cd 29 39  f4 f4 40 b1 e9 c5 79 b5  |.2.t..)9..@...y.|
  00000120  3b 33 e7 d8 12 74 f5 c2  4e 94 9e e7 b7 3c b8 10  |;3...t..N....<..|
  00000130  59 02 45 49 46 c6 b8 8e  d7 cd 55 e0 12 32 07 e5  |Y.EIF.....U..2..|
  00000140  5e 29 51 de a7 44 3f 28  fb 55 26 ec 57 9a 88 d2  |^)Q..D?(.U&.W...|
  00000150  1f 27 39 72 c9 45 34 c3  cb f7 04                 |.'9r.E4....|
  0000015b
```

---

.orange[That's easier to read, but lets see if it's any good]
```bash
  $ gpg --verify statement.txt.gpg
```

--

.orange[And we get:]

```bash
  gpg: Signature made Sat Sep 26 10:35:06 2015 PDT using RSA key ID 3B4AD5EF
  gpg: Good signature from "Jonathan Jimenez <jonathanjimenezromo@gmail.com>" [ultimate]
```

So we can verify that the file was signed by me, but it's hard to work with.

This would be ok if we were signing a large file, but it just doesn't make sense for text.

---

.orange[Let's try]
```bash
  $ rm statement.txt.gpg
  $ gpg --clearsign statement.txt
  $ cat statement.txt.asc
```

--

```bash
  -----BEGIN PGP SIGNED MESSAGE-----
  Hash: SHA256

  Execute order 66
  -----BEGIN PGP SIGNATURE-----
  Version: GnuPG v2

  iQEcBAEBCAAGBQJWBtx6AAoJEKyFlGU7StXvR4MH/iv88zOoGrt75tcZcHoUMcih
  1sX2iD6gvg5/CgeOnLVnkkp03insdS/EiFqzfOJ7GVvOtTpXN3qz/XsyYuFKStg1
  YeIYsq679GgfYBiip8lJzUi3/BxYQ2d8f4KbkKDN+JTFUVWdD7C2BDs4h4liuL6O
  y8PzCKRJC0ihx1QhV1YHbjd0OclIi9ILyhmrSrZpjyRgWQGTMyTDYqAz6vzMYpIw
  UD939L1+QaP2JbcLrUq20WROoYqQMr7mDA3Anj7PccBySi4LYlgcjZFfpT1qznBc
  FPwFJGCq91NQjOyJJOuUr6lwuEV/qF35pyCH39PHP8/AO3QN4iZ9SrSNUJ+Q6Ic=
  =gbX2
  -----END PGP SIGNATURE-----
```

--

```bash
  $ gpg --verify statement.txt.acs
```

--

```bash
  gpg: Signature made Sat Sep 26 10:57:14 2015 PDT using RSA key ID 3B4AD5EF
  gpg: Good signature from "Jonathan Jimenez <jonathanjimenezromo@gmail.com>" [ultimate]
  gpg: WARNING: not a detached signature; file 'statement.txt' was NOT verified!
```

---

.orange[But what good is this? Let's try to change the statement.]
```bash
  $ nano statement.txt.asc
```

--

.orange[I changed it to:]
```bash
  -----BEGIN PGP SIGNED MESSAGE-----
  Hash: SHA256

  Execute order 69
  -----BEGIN PGP SIGNATURE-----
  Version: GnuPG v2

  iQEcBAEBCAAGBQJWBtx6AAoJEKyFlGU7StXvR4MH/iv88zOoGrt75tcZcHoUMcih
  1sX2iD6gvg5/CgeOnLVnkkp03insdS/EiFqzfOJ7GVvOtTpXN3qz/XsyYuFKStg1
  YeIYsq679GgfYBiip8lJzUi3/BxYQ2d8f4KbkKDN+JTFUVWdD7C2BDs4h4liuL6O
  y8PzCKRJC0ihx1QhV1YHbjd0OclIi9ILyhmrSrZpjyRgWQGTMyTDYqAz6vzMYpIw
  UD939L1+QaP2JbcLrUq20WROoYqQMr7mDA3Anj7PccBySi4LYlgcjZFfpT1qznBc
  FPwFJGCq91NQjOyJJOuUr6lwuEV/qF35pyCH39PHP8/AO3QN4iZ9SrSNUJ+Q6Ic=
  =gbX2
  -----END PGP SIGNATURE-----
```

--

```bash
  $ gpg --verify statement.txt.acs
```

--

```bash
  gpg: Signature made Sat Sep 26 10:57:14 2015 PDT using RSA key ID 3B4AD5EF
  gpg: BAD signature from "Jonathan Jimenez <jonathanjimenezromo@gmail.com>" [ultimate]
```
---

#Uploading our keys

We will use

`hkp://pool.sks-keyservers.net`

--

other options

`https://pgp.mit.edu`

`hkp://certserver.pgp.com`

--

But in cases like this using the most popular one is best

--

After uploading, you can go to [sks-keyservers.net/i/](https://sks-keyservers.net/i/) and search peoples IDs

--

Notice your keys will be distributed to servers around the world shortly after.


---

class: center, middle, bggreen
#0xac8594653b4ad5ef
`Jonathan Jimenez <jonathanjimenezromo@gmail.com>`

---
#Yubikey

USB/NFC device to store gpg key

Also has other tools related to logging into services.




