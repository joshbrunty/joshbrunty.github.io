---
layout: article
title: Writing Digital Forensics Reports
tags: reporting report writing DFIR casenotes
author: rms
key: anything
class: success error shadow
article_header:
  type: cover
  image:
    src: 
    
---
## **Prologue**
Each year I get asked a common question by students here at Marshall University (and sometimes in the DFIR community) the following: *"How do I write a DFIR report?"* Year after year I've given the same answer; a list full of outdated links and a verbal "laundry list" of things I've seen work over my 15 years of working in this community. As digital forensic examiners/analysts, it's a given that we must report and present our findings on a very technical discipline in a simplistic manner. I always tell students that everything should be explained to *"make sense to "your 80 old grandmother."* I think most all of us can relate to that funny, yet true symbolism. However, that *grandmother* may be a supervisor, client, attorney, etc. or even to a judge and jury who will read and interpret your report after it has been cross-examined. Are you prepared to explain your findings? When the case goes to trial and you are called upon to testify a year or more in the future will you be able to remember the case based simply from the details you included in your digital forensic report? Better yet, will someone else be able to make sense of (or even validate) my findings if I'm not around to explain them? *What templates do I use? What headings do I include? How do I list figures?* The list can go on and on and on. I'll do my best to address these (and a host of other things) in this article. 

Without wasting any time, let's tackle the first, and most important, question on the list: *"Where do I start?"* For me a good report ALWAYS starts with two important phases: 1) good planning and preparation and 2) casenotes/benchnotes.

## **Planning & Preparation**
Years ago I was working a case that involved a plethora of stolen items: guns, money, and a dog (yes a dog). The detective on the case brought me a phone, laptop, and thumb drive that they had seized as part of the case. Multiple times throughout the course of that case, the detective continued to supply me with *intelligence* which was nothing more than additional keywords and suspect names to search for pertaining the case. This process repeated itself it least 4-5 more times over the course of the next 3 months. Even when drafting the report, the detective was STILL giving me keywords. A process that should have taken weeks took months and hours of fruitless searches. The report took *forever* to draft because of the complexity of the searches and steps performed. At the end of this I was asking myself "What if better planning had been executed?" Later in my career I sought to answer these questions *BEFORE* I began the case rather than after. This better planning, in turn, led to better reports. 

There are dozens of models that describe the digital forensic process and how to approach this planning. A good read that approaches this process head-on is the article written by Mark Pollitt titled [*The key to forensic success: examination planning is a key determinant of efficient and effective digital forensics*](https://doi.org/10.1016/B978-0-12-804526-8.00002-2). In this paper, Mark approaches examination planning through using the [National Institute of Standards and Technology (NIST) SP 800-86](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-86.pdf), which describes the process in four (4) stages, defined as follows:

![Image](/images/reporting/examsteps.jpg)

**Collection:** Data are identified, labeled, recorded, and acquired from all of the possible sources of relevant data, using procedures that preserve the integrity of the
data. Data should be collected in a timely manner to avoid the loss of dynamic data, such as a list of current network connections, and the data collected in cell phones, PDAs, and other battery-powered devices.

**Examination:** The data that are collected should be examined using a combination of automated and manual methods to assess and extract data of particular interest for
the specific situation, while preserving the integrity of the data.

**Analysis:** The results of the examination should be analyzed, using well-documented methods and techniques, to derive useful information that addresses the
questions that were the impetus for the collection and examination.

**Reporting:** The results of the analysis should be reported. Items to be reported may include the following: a description of the actions employed; an explanation of
how tools and procedures were selected; a determination of any other actions that should be performed, such as forensic examination of additional data sources, securing identified vulnerabilities, and improving existing security controls; and recommendations for improvements to policies, guidelines, procedures, tools, and other aspects of the forensic process. 

Clearly the last stage focuses on the *Reporting* phase of the analysis, which is the major focus of this writing. But before we move to this phase I want to stop and discuss the second and last important phase leading to an effective report: drafting good casenotes/benchnotes.

## **Case Notes/Bench Notes**
*"It's easy to use a documentation system before you begin working a case. It's impossible to start one after your case is done..."* Brett Shavers ([DFIR.training](https://dfir.training))

**Case Notes (or Bench Notes)** are the detailed notes or contemporaneous records that an analyst takes when analyzing the case in whatever tool (or method) they are using. For some analysts and labs these are merely simple text files with items that will be a hard reminder of how to list these items in a report. For other analysts (and accredited digital forensics labs) these case notes can be rather detailed: screenshots, full, detailed steps of analysis, etc. I'll admit that early in my career I truly undervalued the importance of case notes and how they led to a better report. Now, with years of experience under my belt, the value of good notes is at the top of my list. I'm sure at this point you are asking *"What should my case notes look like?"* Well that depends on a variety of factors. First and foremost you have to figure out how all of this fits into the operational flow of your laboratory. Furthermore, you want to consider that these case notes should be bringing you to the ultimate goal of producing a better forensic report and not just adding additional burden upon your caseload.

*"Are my case notes discoverable in court?"* 

Well, that answer depends. In all my years I never really had a clear, concrete answer to point to, so to answer this question I took to Twitter (see below) to ask the DFIR community. The responses were interesting... 

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">This might be a somewhat naive question but this question has stumped me for years: “Are forensic bench/case notes discoverable in court?”</p>&mdash; Josh Brunty (@joshbrunty) <a href="https://twitter.com/joshbrunty/status/1335732128705728512?ref_src=twsrc%5Etfw">December 6, 2020</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

As you can see there is a consensus on the the answer: *"Yes."* Long story short, case notes *are* discoverable under the Federal Rules of Evidence. Although there are loopholes in the court such as claiming the notes as attorney work product or just not turning the notes in with the final report altogether. That all said, it's still important to keep detailed case notes not just for court discovery, but to refresh your own memory if, and when you get to drafting the final report.

*What software and/or templates do I use to keep such notes?* 

Good question! I'm providing one of my own Microsoft Word examples *HERE*. There are also paid and open-source applications out there to manage case notes. [Forensic Notes](https://www.forensicnotes.com/) is one such option. Forensic Notes stores all notes, images, and attachments in a timestamped read-only, PDF format to protect the integrity and admissibility of evidence. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/iJ7v7i1_kxE" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

An example Case Notes PDF report can be downloaded [HERE](https://www.forensicnotes.com/wp-content/uploads/2018/12/forensic_notebook_exhibit-1-iphone-6-white.pdf). One of the things I really like & appreciate about Forensic Notes is that it compels DFIR examiners to carefully and contemporaneously take notes in a given investigation. Keep in mind, MOST of the work that DFIR examiners ends up in court and/or legal proceedings in some way, shape or form. Investigators need the ability to document complex investigations and not worry about losing or misplacing critical notes and documents essential for full disclosure if and when such cases reach litigation. 

Now that we've established our casenotes it's now time to move to the actual Foresnic Report. 

## The Forensic Report

The purpose of the Forensic Report is simply to tell the story of what the presence or absence of the digital artifact indicates, regardless, if it is inculpatory or exculpatory in nature. The report may include something similar or a slightly different flavor to the following: *Title Page, Table of Contents, an Overview/Case/Executive Summary, Evidence, Objectives, Steps Taken (forensic acquisition & exam preparation), Relevant Findings (forensic analysis), Conclusion, and Exhibits.*

### Title Page

The Title Page should include case name, date, investigator name and contact information. 

### Table of Contents

The Table of Contents should include each section of the report along with page numbers. If drafting in Microsoft Word a table of contents can be [generated automatically](https://support.microsoft.com/en-us/office/insert-a-table-of-contents-882e8564-0edb-435e-84b5-1d8552ccf0c0). 

### Overview/Case/Executive Summary

This section will vary in length but generally this should be a one-paragraph summary of the entire report. Summaries should be short, sweet, and to-the-point. You will include any relevant information regarding what led to you as the digital forensic examiner/analyst becoming involved with the digital evidence. You may be just receiving the fdigital evidence and someone else conducted the forensic acquisition and this is a good place to document that as this will correlate with your chain of custody information that you immediately started once you came into contact with the digital evidence. Keep in mind, this is an overview and a summary of how the case was initialized and where you as the examiner/analyst became involved.

**Example Case Summary

*On today's date, Detective Marco Marshall contacted the Digital Forensics Laboratory in regards to extracting data from an Android device that had been recovered from a crime scene. Detective Marshall is requesting a forensic examination to see what information by the suspect(s) may have been deleted and is requesting a full forensic examination and report for possible criminal charges.*

### Evidence
This should be a table or listing of evidence containing the descriptive details of the physical evidence items submitted (hard drives, mobile devices, etc). A good evidence listing will include make, model, serial numbers, description, condition, hash values, custodian information, etc.  

**Example Evidence Listing:** 
![Image](/images/reporting/PhysicalEvidenceExample.jpg)

### Objectives
this section outlines spcifically what are you being asked to do. You will include your hypothesis here.  IT is especially important to include if you were asked to perform a targeted investigation.  Also a good idea to include any specific search terms requested.

### Forensic Analyis (Steps Taken)
This is what you did, what you did it with (including make, model, and version of software, tools, etc.). This section is very important, as you must detail your interaction with the digital evidence and the steps taken to preserve and forensically acquire the evidence. Any additional steps that you take (e.g. forensically wiping storage/examination media, utlizing bootloaders in mobile acquisition, etc.) should be notated in this section of your report. Remember, this section of your report is usually where you as the examiner/analyst came into contact with the digital evidence and thoroughly documenting what you have done is very important to the integrity of the digital evidence and your chain of custody.

**Example #1: Mobile Device Forensics Examination**

*1) On today's date I began the forensic acquisition process of the Google Android device. Prior to acquisition of the mobile device, the analyst photographed the device, documenting any identifiers (e.g., make, model, serial #), unique markings, visible damage, etc. while maintaining chain of custody.
*2) After completing the forensic acquisition of the mobile device via the Android Debug Bridge (ADB) the analyst then analyzed the extraction with forensic tools
*3)The analyst used the following tools for forensic analysis, which are licensed to this examiner:

* 1) *Cellebrite Physical Analyzer v.7.13 (build 6600)
* 2) *Magnet Axiom v.4.16
* 3) *Oxygen Forensic Detective v.3.16 (build 3383)
* 4) *Android Logs, Events, And Protobuf Parser-ALEAPP v.1.06

**Example #2: Network Forensics Examination**

* **Analysis #1**- *Initial Inspection: Upon initial download of the file.pcap file onto the desktop of the forensic machine being utilized for investigation, the file was opened using Wireshark v.2.13. Steps were taken to ensure the time and date of packets contained on the file were set to UTC time prior to determining the range of packet captures. The analyst determined the packets to have ranged from 01:51:07 on 07/22/2008 (**Figure 1**) until 06:13:47 on 07/22/2008 (**Figure 2**). The total number of packets contained in the file were then determined by the analyst to be 95,175 packets.

* **Analysis #2**- *Examination of Protocol Hierarchy: The analyst examined the protocol hierarchy for the entire PCAP file using Wireshark (***Figure 3***) *and found 100% of the packets to be Ethernet, with 95.8% having an IPv4 IP address. Further investigation found that 88.1% of the total packets used Transmission Control Protocol (TCP) and that 10.8% attributed to Hypertext Transfer Protocol (HTTP) (**Figure 4**).


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
