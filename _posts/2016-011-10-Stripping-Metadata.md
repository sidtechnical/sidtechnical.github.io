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




###Introduction
With the increase of attacks on the Internet and the supporting infrastructure, the efforts to make these systems more secure has also seen a rapid rise. The cyber security industry is shifting towards *"predict and prevent"* methodologies from the traditional *"detect and improve"* approaches, as they aim to provide fail-safe security solutions. The advancements in the fields of machine learning, artificial intelligence, data mining, and pattern matching had contributed substantially to predict the future attacks based on the previous failures of the system when they were attacked and compromised. Undoubtedly, these technologies have provided new dimensions of protecting the Internet companies' assets, which the classical cryptography failed to address. Indeed, the *"predict and prevent"* methodologies of securing any Internet companies assets is a must to have a weapon to survive in the constant arms race with the evil side of the Internet and the rival counterparts.

In the context of identifying the root cause of recent security breaches and attacks, we often see the threats from human-made cyber weapons such as botnets, viruses, malware as well as ransomware. However, the biggest cybersecurity threats can also [reside within a company](https://hbr.org/2016/09/the-biggest-cybersecurity-threats-are-inside-your-company), such as the human beings (employers) themselves. For the same reason, modern techniques of cyber forensics - the process of identifying the root cause of cyber crimes, relies on **Threat Intelligence**, as it allows many preventive measures. One of the many definitions of 'threat intelligence' is as follows:
>Threat intelligence is evidence-based knowledge, including context, mechanisms, indicators, implications and actionable advice, about an existing or emerging menace or hazard to assets that can be used to inform decisions regarding the subject's response to that menace or hazard.
> - (*Source*: [Gartner](https://www.gartner.com/doc/2487216/definition-threat-intelligence))

As the name and definition probably suggest, the cybersecurity companies selling threat intelligence products relies on many machine learning techniques to intelligently predict the future occurrence of the security breach events. The word *threat intelligence* is not only trending to buzz the list of Internet jargons, but it has also made its way be to the most frequently used word everywhere in the sales pitches of the Internet industry. This fancy buzzword may attract more customers (large enterprises) to adapt the threat intelligence products within their systems. However, it raises some extreme privacy concerns from an end-user point of view.

The traditional threat intelligence software includes honeypots, firewall policies, and various pattern recognition techniques. However, due to the increased demand for addressing insider threats, the modern software are very much focused on recording and recognizing the anomalous human behavior. In simpler words, these are nothing but the software which could surveil people's computers (mainly desktops) and present insightful analytics in a very fancy manner. Not so surprisingly, some of these companies can be found in the [Surveillance Industry Index (SII)]( https://sii.transparencytoolkit.org) built by [Privacy International](https://privacyinternational.org/) and [Transparency Kit](https://transparencytoolkit.org/).

This article investigates the modus operandi of Modern Threat Intelligence Software (MTIS) to highlight the privacy risks associated with it. This is an exploratory analysis based on the live demos, information in the brochures and websites, and in-person queries that I could make. The section following to this introductory remarks articulates the targetted attributes of the threat intelligence products. The methods to displaying the attribute-human associations and the insights that they make on personal behavior are described in the next sections. We conclude this article by highlighting the privacy concerns and consequences.

---
###System Overview
The MTIS considered in the context of this article follow similar modus operandi in spite of being built by different companies. These software tries to efficiently log the journey of target components right from their creation till deletion, including all the modifications made in between. Figure 1 below gives an overview of them in a nutshell. 

Think of MTIS as a piece of piece of software working in client-server mode. The client consists of a a background daemon process  covertly running on your computing device which will be installed by your employer. This client communicates with a remote server which runs several analytics on the data presented to it. The server contains an admin dashboard, which is explained in detail in the later sections.
<div class="center">
![System overview of modern threat intelligence softwares](/home/sid/Desktop/Notes/Threat_Intelligence_System_Overview.png)
*Fig 1:* System overview of modern threat intelligence software </div>
Description about different components of the system is as follows:

1. **Target component**: The target component of the system specifically deals with three aspects - *(a) Source* object, *(b) Origin* of the source attributes and *(c) Associated* attributes of the source. The target objects are primarily based on metadata and file attributes.
    *  ***Source object***: The MTIS mainly target the files on the hard disks as the source objects. The e-mails in the inbox are also considered either as a source or as an associated attributes.
    *  ***Associated attributes***: Associated attributes for files contain the audit log of information such as creation/last modification timestamp, version history of file modification, creator of the file, list of people with access to the file (such as access control list) and directory hierarchy of the files. It is important to note that, no operating system keeps track of version history by default. 
    The associated attributes for the mails simply comprise of email metadata from the headers - to, from, subject and timestamp, along with other information such as its first/last seen, attachments, whole mail chain (reply/forwards) until the creator of the mail.
    *  ***Origin attributes***: Origin attributes contain the origin of the files or emails, again as an addendum of aforementioned associated attributes. These attributes audit whether a file was downloaded from an email, website or copied from a folder/trashbin.
2. **Monitoring**: The monitoring component is a background process which monitors and records all the ongoing activities of a user's device around the clock. The data captured by this component is displayed as described in the next section.
3. **Security Policies**: Security policies could include activities such as copy/modification of specific files, general norms of computer usage (such as using VPN and login mechanisms) and acceptable range of events (e.g. number of usual email trends). Based on the initial policies set by the company, the MTIS tries to learn the usual behavior of sepcific users and general trend of all the employees. 
4. **Event**: Even though the MTIS logs every activities of the users, if anyone strongly violates the security policies, it immediately reports the admin. Depending the action set for the violation, the account can be detained or subjected to further actions. In simpler words, event is triggered when somebody violates the security policies.






---

###Methods of display
By the flamboyant look and feel of the MTIS,  it is evident that the emphasis is definitely on graphically appealing User Interfaces (UI) and interactive data visualization methods. The interactivity not only makes it easy to understand the underlying complex relationship between the files and the users, but also it helps to seek useful insights on user behaviors. The admin panel, which has access to the dashboard represents the monitored interactions of the users with target components in the following two ways:

* **Social graph of files**:  Based on the file access control lists and audit of the file logs, the MTIS build an interactive social graph. It is more or less similar to the demo of one of the popular javascript libraries represented [here](http://arborjs.org/). The admin can start by clicking on the target component which was detected to be suspicious/malicious, and the software allows him to navigate and explore the origin attributes, associated attributes, sub-events, and a list of users who have access to it. The details also include the timestamp associated in a reverse chronological order.

* **Screencasting of the desktop:**: The MTIS has the capability to record literally EVERYTHING that is happening on a user's machine. So, the admin from the dashboard can see the live or recorded screencast of the user's desktop as it is taking place. It includes how the user copied/modified the files, opened the mailbox, composed an email and opened a browser to surf a specific website. The admin can play, pause, rewind and forward the screencasting as if they are watching a movie on "How to evade someone's privacy."  The screen capture of this sort adds an overhead of storage limitations. So MTIS efficiently captures the screencast in the form of compressed GIFs and uploads to the server periodically. Uploading the captures and related information to a remote server not only allows the save the hard disk space, but also it restricts the users themselves to see the what has been captured about them.

---
###Further analytics
Besides providing an interactive interface to primarily perform the forensic analysis of root cause of malicious/suspicious users and to monitor every tiny detail of their activities, the MTIS also provide further analytical features to the administrators. These software aggregate every users' behavioral history based on the monitoring history and violations of internal policies (which is unknown to users)  to quantify the risk associated with every user. The dashboard provides the analytics in the following formats:

* **User behaviour history**: The MTIS learns the general limit across all the users under their radar regarding the average number of emails that they send (which in turn does some time-series analysis probably), average number of files they create, modify, copy or delete on a daily basis, usage of encryption and VPN software, etc. The user behavioral history contains the location of their computer access which provides a map of their travel (previously traveled locations and the current location). It also includes the IP address, MAC  address, and ISP details, along with the type of device that they are using (mobile, tablet or desktop). If the user is beyond any of the prior limit or any anomaly is found in his behavior, the MTIS tags them as a *target* or *suspicious insider*, to assign a risk score for them. 


* **Aggregated dashboard**: The dashboard provides a comprehensive overview of all the users and an aggregated insight of their behaviors. Based on the risk as mentioned earlier score, the dashboard categorizes the users mainly as *Notable Users*, *Users in Watchlist* and *Account lockouts*, where the former being the least threat actors and the latter is the detained accounts per day due to anomaly beyond the certian threshold. It provides the insight by grouping the users based on specific behavior to detail the Most Visited locations, Top travelers, Most risky mailbox, etc.

---
###Consequences of such intelligence:
Under certain circumstances, the MTIS might be able to investigate the actual cause of anomalous user behaviors. For example, it logs the **failed login attempts**, and potentially this could be due to malware from a compromised device or bots mimicking a legitimate user using stolen credentials. However, from the privacy point of view, getting all your activities surveilled and allowing someone to access that without any particular reason is indeed no different than any mass surveillance programs. For any legitimate employee, usage of such software is a privacy nightmare on the following grounds:

* **Workplace privacy**: Imagine you work for a company which uses the MTIS to defend their system against the insider threats. It means, none of your activities using a computing device about that company is no more private. *Does your employers care about workplace privacy if they use such corporate surveillance mechanisms?* Ethically it is wrong, as everyone has their personal space whether or not they are in their workplace. Specifically, this is a significant threat to personal privacy with the increased trend of Bring Your Device (BYOD) work culture, where there is a very little bifurcation between work life and personal life, as everything will be done through the same device. 
* **Service agreements and ethics**: In addition to the workplace privacy, the usage of MTIS makes service agreements and ethics of an employer debatable. When a person is employed by a company, how much is is obliged to be surveilled? How does reading every mail and monitoring every bit of his activity justified? Is it done with the employee's consent, at least with the long and confusing service agreements with sophisticated corporate law jargons? What about the ethics of such companies?

The above two points highlight the consequences of using MTIS in corporate environments. Now, think what if this software are sold to nation state agencies and police intelligence agencies (e.g., NSA, GHCQ, FBI). Isn't it an even bigger threat to the whole civil society of the world?

* **Surveillance capabilities**: We have already witnessed security companies selling surveillance and censorship products to government agencies, such as [here](https://www.theguardian.com/technology/2015/jul/06/hacking-team-hacked-firm-sold-spying-tools-to-repressive-regimes-documents-claim) and [here](https://citizenlab.org/2016/09/tender-confirmed-rights-risk-verifying-netsweeper-bahrain/). The technologies used by these companies make it easier to seek more insight on user behaviors, monitor their activities on a constant basis and thus, create a business opportunity to sell these systems of surveillance to goverments at a premium price. It not only reduces the development effort of the government spying agencies, but it also allows them to scale these niche software into their surveillance needs. No wonder the companies building the MTIS are found in the surveillance index as we mentioned earlier. 

---
###Conclusion
This article provides a high-level overview of the modus operandi of Modern Threat Intelligent Softwares (MTIS). Due to its capabilities to capture every activities of a user, it induces threats to personal privacy. Furthermore, it leads us think about the consequences of these softwares being sold to nation state actors, therey being utilized by surveillance programs.

The collected brochures are submitted to Surveillance Industry Index (SII) database. The next phase of the investogation is planned to include reverse engineering the softwares or finding evidences of these softwares being used in mass or corporate surveillance programs. If anyone is interested, contact me (use GPG encryption and feel free to introduce yourself breifly) for more details. 

---

<p align="center">THE END</p>

---


