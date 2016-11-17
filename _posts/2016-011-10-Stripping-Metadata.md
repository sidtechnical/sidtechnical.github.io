---
layout: post
title: "Stripping and editing the metadata from your PDF files."
categories: 
  - blog
  - projects
published: true
---

#"Threat Intelligence"
##Is that the new name for selling surviellance capabilities?
---




#####Introduction
With the increase of attacks on the Internet and the supporting infrastructure, the efforts to make these systems more secure has also seen a rapid rise. The cyber security industry is shifting towards *"predict and prevent"* methodologies from the *"detect and improve"* approaches. The advancements in the fields of machine learning, artificial intelligence, data mining, and pattern matching has contributed substantially to predict the future attacks based on the previous failures of the system when they were attacked and compromised. Undoubtedly, these technologies have provided new dimensions of protecting the Internet companies's assets, which the classical cryptography failed to address. Indeed, the *"predict and prevent"* methodolgies of securing any Internet companies assests is a must to have weapon to survive in the constant arm race with the evil side of the Internet and the rival  counterparts.

In the context of identifying the root cause of modern security breaches and attacks, we often see the threats from human-made cyber weapons such as  botnets, viruses, malwares as well as ransomwares. However, the biggest cybersecurity threats can also [reside within a company](https://hbr.org/2016/09/the-biggest-cybersecurity-threats-are-inside-your-company) , such as the human beings (employers) themselves. For the same reason, modern techniques of cyber forensics - the process of identifying root cause of cyber crimes, relies on **Threat Intelligence**, as it allows many preventive measures. One of the many definitions of 'threat intelligence' is as follows:
>Threat intelligence is evidence-based knowledge, including context, mechanisms, indicators, implications and actionable advice, about an existing or emerging menace or hazard to assets that can be used to inform decisions regarding the subject's response to that menace or hazard.
> - (*Source*: [Gartner](https://www.gartner.com/doc/2487216/definition-threat-intelligence))

As the name and definition probably suggests, the cybersecurity companies selling threat intelligence products relies on many machine learning techniques to intelligently predict the future occurence of the security breach events. The word *threat intelligence* is not only trending to buzz the list of Internet jargons, it has also made its way be to the most frequently used word everywhere in the sales pitches of the Internet industry. This fancy buzzword may attract more customers (big companies) to adapt the threat intelligence products within thier systems. However, it raises the some extreme privacy concerns from an end-user point of view.

The traditional threat intelligence softwares include honeypots, firewall policies and various pattern recognizition techniques. However, due to the increased demand for addressing insider threats, the modern softwares are very much focused on recording and recognizing the anomalous human behavior. In simpler words, these are nothing but the softwares which could surveil people's computers (mainly desktops) and present insightful analytics in a very fancy manner. Not so surprisingly, some of these companies can be found in the [Surveillance Industry Index (SII)]( https://sii.transparencytoolkit.org) built by [Privacy International](https://privacyinternational.org/) and [Transparency Kit](https://transparencytoolkit.org/).

This article investogates the modus operandi of modern threat intelligence products to highlight the privacy risks associated with it. This is an exploratory analysis based on the live demos, information in the brouchers and websites, and in-person queries that I could made. The section following to this introductory remarks articulates the targetted attributes of the the threat intelligence products. The methods to displaying the attribute-human associations and the insights that they make on perosnal behaviour is described in the next sections. We conclude this article by highlighting the privacy concerns and consequences.

---
#####System Overview
The threat intelligence products (softwares) considered in the context of this article follow similar modus operandi in spite of being built by different companies. These softwares tries to efficiently log the jouney of target components right from their creation till deletion, including all the modifications made in between. Figure 1 below gives an overview of them in a nut shell. 
![System overview of modern threat intelligence softwares](/home/sid/Desktop/Notes/Threat_Intelligence_System_Overview.png)
<p align="center">*Fig 1:* System overview of modern threat intelligence softwares</p>
Description about different components of the system is as follows:
1. Target component: The target component of the system specifically deals with three aspects - **(a) Source** objetct, **(b) Origin** of the source attributes and **(c) Associated** attributes of the source.
	- Source attributes: The source 
	- Associated attributes:
	- Origin attributes:

2. **Monitoring**
3.  
4. **Event**:






---

#####Methods to display
- Social graph of files:
- Screencasting of the desktop:
---
#####Further analytics
1. User behaviour history:
2. Aggregated dashboard:
---
#####Consequences
- Workplace privacy and ethics:
- Service agreements and privacy:
- Surveillance capabilities:
---
#####Conclusion



######References:

[1] [Who's Using Cyberthreat Intelligence and How?](https://www.sans.org/reading-room/whitepapers/analyst/cyberthreat-intelligence-how-35767) - SANS Institute Report
[2] [Threat Intelligence - Beyond the Hype](https://www.alienvault.com/blogs/security-essentials/threat-intelligence-definitions) - Michael Roytman, Alien Vault/Kenna Security.
[3] [Definitive Guide to Cyber Threat Intelligence](https://cryptome.org/2015/09/cti-guide.pdf) - Jon Friedman Mark Bouchard, Jonathan Couch and Matt Hartley


#####Background
I was fortunate to attend the [Blackhat Europe 2016](https://www.blackhat.com/eu-16/) as a speaker. We presented our research on breaking the 4G/LTE backbone protocol called "Diameter", using which an attacker can perform Denial of Service (DoS) either to kick out a specific user or whole bunch of users from cellular network of a specific location. More details about our research can be found either in the [official briefing](https://www.blackhat.com/eu-16/briefings.html#detach-me-not-dos-attacks-against-4g-cellular-users-worldwide-from-your-desk)  of Balckhat Europe or in any of these media reports ([1](https://www.cyberscoop.com/4g-lte-protocols-used-smarthphones-can-hacked-researchers-found/), [2](http://www.darkreading.com/mobile/4g-cellular-networks-at-risk-of-dos-attacks/d/d-id/1327422)).

For those of you who don't know about the Blackhat and its briefings - it is a world renowned computer security conference, where hackers from different places talk their findings. Irrespective of the difficulty to get into the Blackhat conferences and the supercool attacks that are usual presented there, it is often considered as a non-academic conference. For the same reason, hailing from academia and as a newbie to research field, this was my first ever Blackhat talk. With the much associated hype about being a Blackhat Speaker", I was expenting it to be more of a networking event, where infosec professionals from diverse background gather together, discuss their previous researches and future collaboration ideas. I strongly blame  '[Troopers Conference](http://troopers.de/)' - 'family event for hackers' and  such as '[Citizen Lab Summer Institute](https://citizenlab.org/summerinstitute/)' - a very diverse + scholarly event, which are one of the few non-academic (or rather not purely academic) I have attended. Unlike these events, Blackhat turned out more to be a business forum and a very interesting speakers lined up. I could not communicate with the fellow speakers much, and I would definitely blame myself rather than the conference organizers.

There were plenty of companies selling "Cyber Threat Intelligence" products and it sought my interest at first mainly because each one of them had a live demo, a thick brochures and colorful presentations. Of course, non-Latex presentations are so fancy for a person hailing from academia. I thought it is a great opportunity for me learn about industrial advancement of threat intelligence. I was aware of quite many aspects of the topic ranging from honeypots, firewall policies and various pattern recognizition techniques to detect the botnets.

Surprisingly their products were way beyond what I knew about threat intelligence, as it including more on recording and recognizing insider threats. In simpler words, these were the softwares which could surveil people's computers (mainly desktops) and present insightful analytics in a very fancy manner. What surprised me ever more was, I found couple of these companies in the [Surveillance Industry Index (SII)]( https://sii.transparencytoolkit.org/search?utf8=%E2%9C%93&q=nuix) built by [Privacy International](https://privacyinternational.org/) and [Transparency Kit](https://transparencytoolkit.org/). So, I thought of investigating their products further more in order to provide more details on their working mechanism. Indeed this is an exploratory analysis based on the live demos of the threat intelligence products, information in the brouchers and websites, and in-person queries made by me.

