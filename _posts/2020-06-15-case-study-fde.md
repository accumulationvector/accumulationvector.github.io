---
layout: post
title:  "Case Studies in FDE Techniques"
author: "accumulation-vector"
---

I got a lot of interesting feedback on my post pertaining to [full disk encryption tripwires](https://accumulationvector.com/2020-05-07/survey-of-enc-tripwire) so I hope in the future I can edit together a step by step tutorial for each topic I brought up. 

One thing that I've found interesting in reading about the topic further is that if you read older manuals on digital forensics they almost universally recommend that the initial person on the scene should turn off the computer.

The idea here is that they want to preserve the chain of custody and squash any trial motions relating to potential tampering with evidence. The only person that should (in the eyes of these older manuals) actually look at the computer is the forensic analyst touching it later on in a lab. 

The practice of shutting down computers when gathering evidence was dominant in these manuals right up until around 2010 when researchers started to react to the growing number of cases hindered by FDE. 

An interesting research question on the topic would be figuring out how much use each practice has across different countries and different local investigatory guidelines. 

One paper I ran into in this vein of thought [The growing impact of full disk encryption on digital forensics](https://serval.unil.ch/resource/serval:BIB_52974E4C51C4.P001/REF.pdf) by Casey et al. describes the idea of the time period brilliantly.

In this paper, they specifically mention succinctly:

>The increasing use of full disk encryption (FDE) can significantly hamper digital investigations, potentially preventing access to all digital evidence in a case. <br><Br>The practice of shutting down an evidential computer is not an acceptable technique when dealing with FDE or even volume encryption because it may result in all data on the device being rendered inaccessible for forensic examination.

They then discuss the potential future of this subject and propose that no-knock warrants become more prevalent. They specifically predict correctly that prosecutors in the future have to prepare search warrants specifically with FDE in mind.

The main reason I highlighted the paper as worth mentioning was not for the dated analysis the authors put forward but for their discussion of several odd cases. The paper mentions several minor cases that I had not encountered or heard of prior to this. 

What is interesting about some of these cases is that they include instances where full disk encryption caused criminal cases to majorly fail in some aspect of their prosecution. I figured a few people might find them interesting as they are rather odd cases that usually don't get mentioned in these sorts of discussions.

A few of the other examples I list below are cases where FDE was thwarted but played a large role in how the investigation played out. Below I quote all the case studies from the paper.

### Case Example 1:
>In the case of Brazilian banker Daniel Dantas, we see how a strong TrueCrypt passphrase has prevented access to encrypted data on hard drives seized from Dantas’s apartment by the Brazilian police (Leyden, 2010).<br><br> To date, neither dictionary-based attacks by the Brazilian National Institute of Criminology (INC) nor attempts by the FBI have succeeded in accessing the encrypted data.

### Case Example 2:
>A suspected terrorist was apprehended with his laptop open and turned on with the TrueCrypt Mount window displayed on screen. Part of the passphrase for a 1 GB TrueCrypt volume had been typed into the TrueCrypt Mount window. The screen contents and partial passphrase were noted by the police before the laptop was seized, imaged and examined.<br><br> The suspect was asked in interview for the full passphrase but he refused until an order was obtained from the High Court requiring him to disclose the passphrase. However, the passphrase he provided did not work.<br><br> In court, the suspect stated that he believed that that was the correct passphrase, but it was months since he had even seen his computer and he may not be remembering correctly. Based on this situation, the judge held that there was no case to answer.

### Case Example 3:
>Albert Gonzalez and his associates, convicted in 2009 for a string of intrusions including TJX Corp and Heartland Payment Systems, widely employed FDE and encrypted containers. <br><br>Because of the expectation that encrypted storage was prevalent, the pre-raid preparations and on-scene search strategies were crafted to maximize the opportunity to gain access to running systems and the data they contained. <br><br>As a result of this careful planning and the ability to gain access to an FDE system at one of the first crime scenes that digital investigators processed during a coordinated series of searches led by the US Secret Service, critical information was exposed that paved the way for the recovery of a much larger trove of evidence – and eventually to successful prosecution of the organization.

### Case Example 4:
>As part of the recent situation involving a US-based Russian spy ring, the Federal Bureau of Investigation (FBI) successfully circumvented full disk encryption utilized by the Russian agents.<br><br> The FBI was able to access and analyze their acquired forensic images of the encrypted devices because during their searches they recovered pieces of paper containing the necessary passphrases. (U.S. v. Anna Chapman and Mikhail Semenko).

### Case Example 5:
>In the Max Ray Butler (Iceman) case, the digital investigators expected to encounter encryption and the on-scene search was planned accordingly to maximize the opportunity to gain access to running systems, whether they were locked or not. <br><br>Gaining access to cryptographic data during the search permitted the subsequent decryption of his FDE systems and an assortment of encrypted containers on external drives.<br><br> This greatly added to initial evidence of the sale of encoding data for several thousand credit cards, leading to Butler’s eventual conviction for the theft of data for nearly 2 million unique payment cards. It also gave investigators access to artifacts from more than a hundred intrusions over several years.

## More Resources

- [An Assessment Model for Cybercrime Investigation Capacity](https://arxiv.org/abs/1307.0076)<br>

- [Cyber Forensics: Representing and Improving the Chain of Custody Using the Semantic web](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.677.4634&rep=rep1&type=pdf)<br>

- [Digital Chain of Custody: State of the Art](https://www.researchgate.net/profile/Yudi_Prayudi/publication/273694917_Digital_Chain_of_Custody_State_of_The_Art/links/5508eb510cf2d7a2812b6945.pdf)<br>

- [B-CoC: A Blockchain-based Chain of Custody for Evidences Management in Digital Forensics](https://arxiv.org/abs/1807.10359)<br>

- [Cybercrime Investigators are Users Too! Understanding the Socio-Technical Challenges Faced by Law Enforcement](https://arxiv.org/abs/1902.06961)<br>

>Casey E, Stellatos G. The impact of full disk encryption on digital forensics. ACM SIGOPS Operating Systems Review April 2008; 42(3)

