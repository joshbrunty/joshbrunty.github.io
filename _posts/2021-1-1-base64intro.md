---
layout: article
title: Base64- A Forensic Introduction
tags: Base64 DFIR encoding decoding cyberchef
author: rms
key: anything
class: success error shadow
article_header:
  type: cover
  image:
    src: /images/base64/base64.gif 
    
---

## **Prologue**
Although a digital forensic examiner may encounter many different encoding schemes in their daily casework, one of the most popular is that of Base64. Base64 is often applied to data being transported from one system to another, and is a popular encoding format because it ensures that a device (and it's associated oeprating system) at the opposite end can properly interpret the data being transmitted. In many cases we find messages stored by 3rd party applications, data BLOBs within SQLite databases, and even login usernames/passwords utilizing Base64! So it goes without saying that digital forensic examiners, especially those tasked with investigating mobile devices, know how the basic foundations of Base64. Most forensic software and/or analytical programs support the decoding of Base64 in addition to various other encoding schemes. In the event that a program doesn't support Base64 decoding, there are many web-based applications available to choose (we'll discuss those at the end of this post).

## **Introduction**

**Base64** is a group of binary-to-text encoding schemes that represent binary data (more specifically a sequence of 8-bit bytes) in an ASCII string format by translating it into a radix-64 representation. The term Base64 originates from a specific MIME content transfer encoding. Each non-final Base64 digit represents exactly 6 bits of data. Three 8-bit bytes (i.e., a  total of 24 bits) can therefore be represented by four 6-bit Base64 digits.

Characters of the Base64 alphabet can be grouped into four groups:

* **Uppercase letters** (indices 0-25): *ABCDEFGHIJKLMNOPQRSTUVWXYZ*

* **Lowercase letters** (indices 26-51): *abcdefghijklmnopqrstuvwxyz*

* **Digits** (indices 52-61): *0123456789* 

* **Special Symbols** (indices 62-63): *+/*

I have grouped all of the above indices into the following table below:

![Image](/images/base64/base64table.png)

It is  very important to note that the Base64 letters are **case sensitive**. This means that, for example, when decoding the values *QQ==*, *Qq==*, *qq==*,  and *qQ==* four different results are obtained.

Decoding Base64 by hand is not a common practice as most (if not all) digital & mobile forensics tools decode Base64 automatically, in addition to online decoding resources available. However, understanding the structure of how BASE64 encodes data is a critical component of digital forensics. Many applications (especially messaging applications) utilize this encoding scheme. 

## **Methodology**
Decoding Base64 is a tedious, but straightforward process. To accomplish this we will follow this 4 step process:

{:.success}
**Step #1: Convert the ASCII to Binary**  

* **HER** (decimal 72, 69, 82) becomes: 01001000 01000101 01010010

* **HERD** (decimal 72, 69, 82, 68) becomes: 01001000 01000101 01010010 01000100 

* **HERDU** (decimal 72, 69, 82, 68, 85) becomes: 01001000 01000101 01010010 01000100 01010101 

{:.success}
**Step #2: Next, your bits must be divisible by 6, so re-section each binary into 6-bit increments, and, if not divisible by 6, pad the end with zeros until it is:**

* **HER** becomes: 010010 000100 010101 010010

* **HERD** becomes: 010010 000100 010101 010010 010001 00*0000*

* **HERDU** becomes: 010010 000100 010101 010010 010001 000101 0101*00*

{:.success}
**Step #3 Now, convert your 6-bit words you just created into decimal (utilizing this handy chart below):**

![Image](/images/base64/6bitconversionchart.PNG)

`NOTE:`{:.success}
The first two bits in each word will be zeros. Therefore, "H" converts to 010010, which then equals 18.

* **HER** becomes: 18 4 21 18 

* **HERD** becomes: 18 4 21 18 17 0

* **HERDU** becomes: 18 4 21 18 17 5 17

{:.success}
**Step #4 Finally, utilize the BASE64 chart above to covert the index value to the appropriate ASCII character. This BASE64 table remains constant, which means that other systems are able to properly decode the data.**

![Image](/images/base64/BASE64converted.PNG)

`NOTE:`{:.success}
*HER* is 3 units in length and thus doesn't require padding, whereas *HERD* totals 4 units, so it requires a padding of 2 (2 equal signs "==") to make the length of 6, which is now divisible by 3. The pad character (=) does not have a binary representation in Base64; it is inserted into the Base64 text as a placeholder to maintain 24-bit alignment.

## **Conclusion** 

To perform this automatically I'd recommend utilizing the builtin decoding mechanisms of your forensic tools. Tools like Cellebrite & Magnet Axiom have robust data coversion capabilities, but there might be a case where you are using a standalone script or utility that doesn't have such a mechanism. One such program I highy recommend using is [CyberChef](https://gchq.github.io/CyberChef/#recipe=To_Base64('A-Za-z0-9%2B/%3D')&input=SEVSRA). CyberChef handles both Base64 encoding/decoding (among a host of other decoding types commonly encountered by digital forensics examiners). 

## **Additional Links**

* [CyberChef](https://gchq.github.io/CyberChef/)

* [BASE64- A Visual Explanation](https://www.lucidchart.com/techblog/2017/10/23/base64-encoding-a-visual-explanation/)

* [BASE64 Visual Encoder](https://codepen.io/lewistg/pen/MEQbmB)

* [Base64 Alphabets (Gary Kessler)](https://www.garykessler.net/library/base64.html)

* [RFC 4648](https://www.rfc-editor.org/rfc/rfc4648.txt)

* [Online Base64 Decoder](https://www.base64decode.org/)

* [Custom base64 alphabet encoder/decoder](https://www.matteomalvica.com/blog/2019/01/21/custom-base64-alphabet-encoder/decoder/)

<!--more-->
