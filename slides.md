class: center, middle, bgblue
#Code Tech Security Talk

**By Jonathan Jimenez**

Slides are available on the codetech github
---

class: center, middle, inverse
#Citizen Four
---

class: center, middle, inverse
#SSH
---

#Shell (SH)

An operating system's `shell` is a program that gives you an alternative to the `gui` for controlling your computer.

Shells are text based but the good ones have colors and clickable links, as well as support for utf-8

--

For example, if you want to open a browser to google.com you would enter
```bash
	open https://www.google.com //on OSX
	start https://www.google.com //on Windows
	xdg-open https://www.google.com //on Linux
```

--
Popular Shells
- CMD
- SH
- BASH (Bourne Again Shell)
- ZSH
- CSK
- KSK

---
#Let's give it a try:

.orange[Open the program called CMD, and type]
```bash
  echo hello world
```
.orange[hello world]

--
```bash
  ipconfig
```
.orange[you should see information about your internet connection]


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

.orange[this is usefull]
```bash
  telnet rainmaker.wunderground.com
```

--

.orange[this is a fun one]
```bash
  telnet towel.blinkenlights.nl
```
---
#Secure Shell (SSH)

An application level protocal for using Shells securily and remotely

>Wikipedia:

>Secure Shell, or SSH, is a cryptographic (encrypted) network protocol to allow remote login and other network services to operate securely over an insecure network.

>SSH was designed as a replacement for Telnet and for insecure remote shell protocols...

.gray.small[ Note: You can use any application through an ssh tunnel, but that's another talk.]
---

class: center, middle
#...
---

class: center, middle, inverse
#GPG
---

#PGP
>Wikipedia:

>Pretty Good Privacy (PGP) is a data encryption and decryption computer program that provides cryptographic privacy and authentication for data communication. PGP is often used for signing, encrypting, and decrypting texts, e-mails, files, directories, and whole disk partitions and to increase the security of e-mail communications. It was created by Phil Zimmermann in 1991.

>PGP and similar software follow the OpenPGP standard (RFC 4880) for encrypting and decrypting data.
---

#GPG
>Wikipedia:

>GNU Privacy Guard (GnuPG or GPG) is a free software replacement for the Symantec's PGP cryptographic software suite. GnuPG is compliant with RFC 4880, which is the IETF standards track specification of OpenPGP. Modern versions of PGP and Veridis' Filecrypt are interoperable with GnuPG and other OpenPGP-compliant systems.

--

.gray.small[Note: GNU stands for GNU Not Unix, think about that for a second.]
---

#RSA
>RSA is one of the first practical public-key cryptosystems and is widely used for secure data transmission. In such a cryptosystem, the encryption key is public and differs from the decryption key which is kept secret. In RSA, this asymmetry is based on the practical difficulty of factoring the product of two large prime numbers, the factoring problem. RSA is made of the initial letters of the surnames of Ron Rivest, Adi Shamir, and Leonard Adleman, who first publicly described the algorithm in 1977. Clifford Cocks, an English mathematician, had developed an equivalent system in 1973, but it was not declassified until 1997.
---

class: center, middle
#...
---

#Signing Things

(not on the dotted line)

.orange[Let's sign a statement, a signiture verifies that the signer is seeing the same message]
```bash
  gpg --sign statement.txt
```

--

.orange[lets see what we have]
```bash
  cat statement.sig
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
  hexdump -C statement.txt.gpg
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
  gpg --verify statement.txt.gpg
```

--

.orange[And we get:]

```bash
  gpg: Signature made Sat Sep 26 10:35:06 2015 PDT using RSA key ID 3B4AD5EF
  gpg: Good signature from "Jonathan Jimenez <jonathanjimenezromo@gmail.com>" [ultimate]
```

So we can verify that the file was signed by me, but it's hard to work with.

This would ok is we were signing a large file, but it just doesn't make sense for text.

---

.orange[Lets try]
```bash
  rm statement.txt.gpg
  gpg --clearsign statement.txt
  cat statement.txt.asc
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
  gpg --verify statement.txt.acs
```

--

```bash
  gpg: Signature made Sat Sep 26 10:57:14 2015 PDT using RSA key ID 3B4AD5EF
  gpg: Good signature from "Jonathan Jimenez <jonathanjimenezromo@gmail.com>" [ultimate]
  gpg: WARNING: not a detached signature; file 'statement.txt' was NOT verified!
```

---

.orange[But what good is this? Let's try to chang the statement.]
```bash
  nano statement.txt.asc
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
  gpg --verify statement.txt.acs
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

Also has other tools related to loging into services.




