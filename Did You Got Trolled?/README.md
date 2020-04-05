# Did we Got Trolled?

> web

Author: [whitex](https://instagram.com/najeh_halawani)

##Description

An army of hackers has stolen the flag from our rabbits. 
Security experts have failed to capture the flag and some have even gone mad. 
Please…GIMME THE FLAG!! 

## Writeup

One of the first thing we should test on new website... is to see if there's a robots.txt, and indeed:

```
Disallow: /deep.php
```

open it and we'll found: 

```
deep.php/page=debug.html
```
If we look at the url we will see that it is including a file, most likely we are facing an LFI, but we do not know the location of the flag, so we go with the next logical step, look at the code of the page and surprise !:

```
<!-- Creds in /home/ubuntu/key2.txt -->
```
we have already located the path of key2.txt, we edit the url to open this file and we should get this

```
key2=flag0x085927
```

Ok, but we need to locate key1, seeing the amount of comments that there are on the web referring to key we started to read all the code that we could find on the web, first html, and then css ... and look at what we found in one of them:

``` url: ip:port/css/clean-blog.css
	* key1= gimme0x038792
```
we already have both keys! we only need to enter them in the form and we get the flag 

```d33p{h3r3_1s_y0ur_7r0ll_fl4g}```
