---
layout: article
title: Validation of Forensic Tools- A Quick Guide for the DFIR Examiner
tags: DFIR validation
author: rms
key: anything
class: success error shadow
article_header:
  type: cover
  image:
    src: /images/validation/validate1.jpg 
    
---

## **Prologue**
Still need to write one up

## **Introduction**
With the field of digital forensics growing at an almost warp-like speed, there are many issues out there that can disrupt and discredit even the most experienced forensic examiner.  One of the issues that continue to be of utmost importance is the validation of the technology and software associated with performing a digital forensic examination.  The science of digital forensics is founded on the principles of repeatable processes and quality evidence.  Knowing how to design and properly maintain a good validation process is a key requirement for any digital forensic examiner.   This post will attempt to outline the issues faced when drafting tool and software validations, the legal standards that should be followed when drafting validations, and a quick overview of what should be included in every validation. 

## **Setting the Standard: 
* Standards and Legal Baselines for Software/Tool Validation**
According to the National Institute of Standards and Technology (NIST), test results must be repeatable and reproducible to be considered admissible as electronic evidence.  Digital forensics test results are repeatable when the same results are obtained using the same methods in the same testing environment.  Digital forensics test results are reproducible when the same when the same test results are obtained using the same method in a different testing environment (different mobile phone, hard drive, and so on).   NIST specifically defines these terms as follows: 

`Repeatability:`{:.success}
refers to obtaining the same results when using the same method on identical test items in the same laboratory by the same operator using the same equipment within short intervals of time. 
`Reproduciblity:`{:.success}
refers to obtaining the same results being obtained when using the same method on identical test items in different laboratories with different operators utilizing different equipment.     

----stop here

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

* [Base64 Alphabets (Gary Kessler)](https://www.garykessler.net/library/base64.html)

* [RFC 4648](https://www.rfc-editor.org/rfc/rfc4648.txt)

* [Online Base64 Decoder](https://www.base64decode.org/)

<!--more-->
