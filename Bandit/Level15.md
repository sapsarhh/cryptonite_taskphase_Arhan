# Level 15
In this level I had to change my port to 30001 but with a catch, which was that an openssl encryption had to be used this time.
basically openssl encryption of course ensures more security and is a process of converting the text to an an encrypted text which has to be deciphered in order to get access over.
so firstly I had to of course apply some hit and trial and guess how the openssl command would be used.
my first guess was this which did nothing and gave me an error---->nc localhost 30001 openssl
so then I had to research how to encrypt a connection using ssl which landed me with the following result, reference------> https://serverfault.com/questions/476068/can-netcat-talk-to-an-encrypted-port and also https://serverfault.com/questions/102032/connecting-to-https-with-netcat-nc
~~~
bash
bandit14@bandit:~$ openssl s_client localhost:30001
CONNECTED(00000003)
Can't use SSL_get_servername
depth=0 CN = SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = SnakeOil
verify return:1
---
Certificate chain
 0 s:CN = SnakeOil
   i:CN = SnakeOil
   a:PKEY: rsaEncryption, 4096 (bit); sigalg: RSA-SHA256
   v:NotBefore: Jun 10 03:59:50 2024 GMT; NotAfter: Jun  8 03:59:50 2034 GMT
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIFBzCCAu+gAwIBAgIUBLz7DBxA0IfojaL/WaJzE6Sbz7cwDQYJKoZIhvcNAQEL
BQAwEzERMA8GA1UEAwwIU25ha2VPaWwwHhcNMjQwNjEwMDM1OTUwWhcNMzQwNjA4
MDM1OTUwWjATMREwDwYDVQQDDAhTbmFrZU9pbDCCAiIwDQYJKoZIhvcNAQEBBQAD
ggIPADCCAgoCggIBANI+P5QXm9Bj21FIPsQqbqZRb5XmSZZJYaam7EIJ16Fxedf+
jXAv4d/FVqiEM4BuSNsNMeBMx2Gq0lAfN33h+RMTjRoMb8yBsZsC063MLfXCk4p+
09gtGP7BS6Iy5XdmfY/fPHvA3JDEScdlDDmd6Lsbdwhv93Q8M6POVO9sv4HuS4t/
jEjr+NhE+Bjr/wDbyg7GL71BP1WPZpQnRE4OzoSrt5+bZVLvODWUFwinB0fLaGRk
GmI0r5EUOUd7HpYyoIQbiNlePGfPpHRKnmdXTTEZEoxeWWAaM1VhPGqfrB/Pnca+
vAJX7iBOb3kHinmfVOScsG/YAUR94wSELeY+UlEWJaELVUntrJ5HeRDiTChiVQ++
wnnjNbepaW6shopybUF3XXfhIb4NvwLWpvoKFXVtcVjlOujF0snVvpE+MRT0wacy
tHtjZs7Ao7GYxDz6H8AdBLKJW67uQon37a4MI260ADFMS+2vEAbNSFP+f6ii5mrB
18cY64ZaF6oU8bjGK7BArDx56bRc3WFyuBIGWAFHEuB948BcshXY7baf5jjzPmgz
mq1zdRthQB31MOM2ii6vuTkheAvKfFf+llH4M9SnES4NSF2hj9NnHga9V08wfhYc
x0W6qu+S8HUdVF+V23yTvUNgz4Q+UoGs4sHSDEsIBFqNvInnpUmtNgcR2L5PAgMB
AAGjUzBRMB0GA1UdDgQWBBTPo8kfze4P9EgxNuyk7+xDGFtAYzAfBgNVHSMEGDAW
gBTPo8kfze4P9EgxNuyk7+xDGFtAYzAPBgNVHRMBAf8EBTADAQH/MA0GCSqGSIb3
DQEBCwUAA4ICAQAKHomtmcGqyiLnhziLe97Mq2+Sul5QgYVwfx/KYOXxv2T8ZmcR
Ae9XFhZT4jsAOUDK1OXx9aZgDGJHJLNEVTe9zWv1ONFfNxEBxQgP7hhmDBWdtj6d
taqEW/Jp06X+08BtnYK9NZsvDg2YRcvOHConeMjwvEL7tQK0m+GVyQfLYg6jnrhx
egH+abucTKxabFcWSE+Vk0uJYMqcbXvB4WNKz9vj4V5Hn7/DN4xIjFko+nREw6Oa
/AUFjNnO/FPjap+d68H1LdzMH3PSs+yjGid+6Zx9FCnt9qZydW13Miqg3nDnODXw
+Z682mQFjVlGPCA5ZOQbyMKY4tNazG2n8qy2famQT3+jF8Lb6a4NGbnpeWnLMkIu
jWLWIkA9MlbdNXuajiPNVyYIK9gdoBzbfaKwoOfSsLxEqlf8rio1GGcEV5Hlz5S2
txwI0xdW9MWeGWoiLbZSbRJH4TIBFFtoBG0LoEJi0C+UPwS8CDngJB4TyrZqEld3
rH87W+Et1t/Nepoc/Eoaux9PFp5VPXP+qwQGmhir/hv7OsgBhrkYuhkjxZ8+1uk7
tUWC/XM0mpLoxsq6vVl3AJaJe1ivdA9xLytsuG4iv02Juc593HXYR8yOpow0Eq2T
U5EyeuFg5RXYwAPi7ykw1PW7zAPL4MlonEVz+QXOSx6eyhimp1VZC11SCg==
-----END CERTIFICATE-----
subject=CN = SnakeOil
issuer=CN = SnakeOil
---
No client certificate CA names sent
Peer signing digest: SHA256
Peer signature type: RSA-PSS
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 2103 bytes and written 373 bytes
Verification error: self-signed certificate
---
New, TLSv1.3, Cipher is TLS_AES_256_GCM_SHA384
Server public key is 4096 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 18 (self-signed certificate)
---
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: DB0801475EBE102B1C904DBD7D42B9AD155A716429894DF9B8122057AD51E447
    Session-ID-ctx:
    Resumption PSK: DEA8147C7871B3E751E1DECCB1400E4FDC48C409795F3B3EE1ED12992EE7F69FB2880AB5DDC51646D1F674C20B8FED68
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - c0 c6 3d 9e 22 a9 6f a8-d6 08 ea 57 e8 ec 3e f7   ..=.".o....W..>.
    0010 - 84 88 8e ba 0a a8 a6 6e-01 bb 89 d7 de c1 70 48   .......n......pH
    0020 - 19 4b 30 10 32 66 90 01-ab 23 4e a7 19 d4 49 44   .K0.2f...#N...ID
    0030 - 57 34 97 e8 a2 e7 54 e7-90 89 bb 78 fc d5 d7 23   W4....T....x...#
    0040 - 7d a0 f0 22 d4 aa 62 d8-6f 00 0d 74 91 ac c8 e9   }.."..b.o..t....
    0050 - 07 bd cc 62 ac cf f0 1b-77 46 27 ba f8 32 81 28   ...b....wF'..2.(
    0060 - f4 74 7e 1f 32 61 51 5c-4e 09 c3 e2 d2 3f 9e ae   .t~.2aQ\N....?..
    0070 - 0a 24 a2 90 06 eb 80 cb-30 11 ad 4e 20 ee eb 32   .$......0..N ..2
    0080 - cb f7 bf 5f ee 57 8e 26-35 c8 06 20 6c f5 53 da   ..._.W.&5.. l.S.
    0090 - 3f 0d f0 6e e1 5d d3 98-b1 b7 b4 d2 0a 29 0c 99   ?..n.].......)..
    00a0 - f7 58 6a f9 4a 3b a8 0f-5f 28 d1 6a a1 a2 a5 96   .Xj.J;.._(.j....
    00b0 - d8 d5 fe 85 25 76 0b 7d-1b a2 8b 6b cb 78 a0 1a   ....%v.}...k.x..
    00c0 - 78 a0 07 c9 fc aa 1d 13-1f 4a fe b5 e6 6b 21 48   x........J...k!H
    00d0 - 28 fc b2 0f 13 cd 5a 52-3c cd df 44 e8 85 9b 35   (.....ZR<..D...5

    Start Time: 1729278769
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: DC03262418A68094D8F369189EB8C1E7FD9ED70DB3E5CC435F8112328A7FCA31
    Session-ID-ctx:
    Resumption PSK: BF7F93B2261FA57BEE5FD35406AF1369C2F7177EC7A8252844AE59122DF753873280E78E4D2D4967DCC5E534875A182C
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - c0 c6 3d 9e 22 a9 6f a8-d6 08 ea 57 e8 ec 3e f7   ..=.".o....W..>.
    0010 - a4 96 36 7b 7d f2 44 40-c2 9e a9 f3 6c 10 d6 29   ..6{}.D@....l..)
    0020 - d9 13 6d 09 53 06 a1 bd-56 fa 66 97 80 31 83 04   ..m.S...V.f..1..
    0030 - b3 7e b0 90 e5 da 3e a2-11 e2 b9 3e 73 a5 bf 7b   .~....>....>s..{
    0040 - df 12 63 6f d4 21 bb ea-0d 76 a5 e7 3e 0a 2f db   ..co.!...v..>./.
    0050 - a8 9e b4 24 22 e9 b3 85-c0 73 ef 48 82 4d 9e 68   ...$"....s.H.M.h
    0060 - 51 71 d6 45 81 43 11 c3-05 d3 b9 d7 85 c5 b1 b7   Qq.E.C..........
    0070 - 83 2e e4 b4 a2 bc 0e 50-c0 e2 4a 3d 1e da 4c b4   .......P..J=..L.
    0080 - 58 b6 d7 fb dc c9 1e eb-23 4c 6d 01 f6 0c f6 d7   X.......#Lm.....
    0090 - da e1 36 03 57 b9 0d 83-01 3e 1c 25 1f 7f 22 80   ..6.W....>.%..".
    00a0 - 1a 4b ff 3c 34 6d 00 15-28 47 f9 0d 5a 20 0d 03   .K.<4m..(G..Z ..
    00b0 - e5 c2 a8 5a 0c 6e 86 fe-7e d0 d3 71 60 47 a4 b3   ...Z.n..~..q`G..
    00c0 - c6 94 36 54 21 5a 9c 50-fb 61 8c f0 c4 44 45 44   ..6T!Z.P.a...DED
    00d0 - 91 8d 83 06 cd aa 40 cc-86 72 31 70 e0 6a eb 63   ......@..r1p.j.c

    Start Time: 1729278769
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
Correct!
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

closed
~~~
used the above command and then tried with the password which I obtained from the previous level and got the password.
