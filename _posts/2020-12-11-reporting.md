---
layout: article
title: Report-Writing for Digital Forensics
tags: reporting reports DFIR
author: rms
key: anything
class: success error shadow
article_header:
  type: cover
  image:
    src: /images/base64/base64.gif 
    
---

## **Prologue**
Each year I get asked a common question by students here at Marshall University (and sometimes in the DFIR community) the following: *"How do I write a DFIR report?"* Year after year I've given the same answer; a list full of outdated links and a verbal "laundry list" of things I've seen work over my 15 years of working in this community. As digital forensic examiners/analysts, it's a given that we must report and present our findings on a very technical discipline in a simplistic manner. I always tell students that everything should be explained to *"make sense to "your 80 old grandmother."* I think most all of us can relate to that funny, yet true symbolism. However, that *grandmother* may be a supervisor, client, attorney, etc. or even to a judge and jury who will read and interpret your report after it has been cross-examined. Are you prepared to explain your findings? When the case goes to trial and you are called upon to testify a year or more in the future will you be able to remember the case based simply from the details you included in your digital forensic report? Better yet, will someone else be able to make sense of (or even validate) my findings if I'm not around to explain them? *What templates do I use? What headings do I include? How do I list figures?* The list can go on and on and on. I'll do my best to address these (and a host of other things) in this article. 

Without wasting any time, let's tackle the first, and most important, question on the list: *"Where do I start?"* For me this starts with good case notes (or bench notes)...

## **Case Notes/Bench Notes**

**Case Notes (or Bench Notes)** are the detailed notes or contemporaneous records that an analyst takes when analyzing the case in whatever tool (or method) they are using. For some analysts and labs these are merely simple text files with items that will be a hard reminder of how to list these items in a report. For other analysts (and accredited digital forensics labs) these case notes can be rather detailed: screenshots, full, detailed steps of analysis, etc. I'll admit that early in my career I truly undervalued the importance of case notes and how they led to a better report. Now, with years of experience under my belt, the value of good notes is at the top of my list. I'm sure at this point you are asking *"What should my case notes look like?"* Well that depends on a variety of factors. First and foremost you have to figure out how all of this fits into the operational flow of your laboratory. Furthermore, you want to consider that these case notes should be bringing you to the ultimate goal of producing a better forensic report and not just adding additional burden upon your caseload.

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">This might be a somewhat naive question but this question has stumped me for years: “Are forensic bench/case notes discoverable in court?”</p>&mdash; Josh Brunty (@joshbrunty) <a href="https://twitter.com/joshbrunty/status/1335732128705728512?ref_src=twsrc%5Etfw">December 6, 2020</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>



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

* [Base64 Alphabets (Gary Kessler)](https://www.garykessler.net/library/base64.html)

* [RFC 4648](https://www.rfc-editor.org/rfc/rfc4648.txt)

* [Online Base64 Decoder](https://www.base64decode.org/)

<!--more-->
