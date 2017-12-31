---
layout: post
title:  'Security recap: 2017 in Review'
categories: 
  - blog
tags:
  - security
favorite: true
published: true
---

<!-- <i class="fa fa-quote-left fa-4x fa-pull-left fa-border" aria-hidden="true"></i> ***Disclaimer:** <font style="font-size:medium" color="#000066">Though I intend to cover all the major security breaches of 2017, it is nearly impossible to  make an exhaustive list of all of them. Even if it is possible, it won't be suitable for a compressed blog post like this. It is very much possible that I might have missed a "must-have" breach because of the 'Internet filter bubble' that we all live in. Please consider bringing it to my notice!</font>* -->

<i class="fa fa-clock-o" aria-hidden="true"></i> **A brief recap of 2016**: On the offensive side, attacks like [HEIST][heist], [DROWN][drown], [Sweet32][sweet32] and [Dirty C0W][dirtyc0w] got media attention that they deserved. On the defensive side, Transport Layer Security (TLS) 1.3 [design][tls13_spec] was finalized, which includs the standardization of elliptic curves - Curve25519 and Curve448 ([RFC 7748][rfc7748]) to ensure a high level of practical security. 

However, 2017 is almost over now, and yet TLS 1.3 is not in browsers. There is no doubt about the difficulties of upgrading a security protocol in the Internet; it requires both the servers and clients (browsers in this case) to adopt this changes at the same time. While many server vendors have taken the first step to upgrade to TLS 1.3, the browser vendors are still [lagging behind][tls13_due] to enabled it by default. Even though the browser vendors blame the <span data-balloon-length="large" data-balloon="A middlebox or network appliance is a computer networking device that transforms, inspects, filters, or otherwise manipulates traffic for purposes other than packet forwarding. Common examples of middleboxes include firewalls." data-balloon-pos="up">middleboxes<sup><i class="fa fa-wikipedia-w" aria-hidden="true"></i></sup></span>, the real reason is *"<font color="#000066">the original design of TLS 1.3 was incompatible with the way the Internet has evolved over time</font>"* - says Nick Sullivan, the Head of Cryptography - ‎Cloudflare, Inc. 

<i class="fa fa-book" aria-hidden="true"></i> [2016 in review][eff2016], [Nick's blog post][tls13_due] and <span data-balloon="It helps check if your network is compatible with TLS 1.3." data-balloon-pos="up">[middlebox test tool][tls13_test]</span>.

---

# Fast-forward to 2017

Security breaches are one of the most recurring columns of most of the news media, because they happen every year, every now and then.  The year 2017 is no exception to that!

While some of them could expose previously unknown vulnerabilities or intorduce a new bug, many of the rest are just reusing well-known vulnerabilities on a different attack surfaces. Reasons could range from inefficient threat models and anlysis to incorrect implementions while bringing theoretical security to practice. Irrespective of the reasoning, public disclosures of the security breaches help us learn from the mistakes and build more secure systems.

## Research: New vulnerabilities 

**1. [SHAttered][SHAttered] - (Practical) collision of SHA-1:** <span data-balloon="a mathematical one-way function which converts (represents) any arbitary size of data into a fixed-size bit string" data-balloon-pos="up">Cryptographic hashes</span> form one of the backbones of modern information security, because many authentication (e.g. digital signatures or message authentication codes) rely on it. These hashes must ensure <span data-balloon="deterministic, fast one-way only (while finding the hash), infeasiable to reverse" data-balloon-pos="up">several properties</span>, out of which **collision-resistance** is one of the most fragile points.
In theory, the only way to find a collision is by <span data-balloon="exhaustively list every possible message space (data), followed by finding a matching hash" data-balloon-pos="up">brute-force</span>, however, this has been tampered every time the computer architecture gets improvised, or when a clever way of reducing the complexity is discovered. Ever since, the theoretical collisions were found for SHA-1 ([2005][2005_shattered], [2011][2011_shattered]), it has been deprecated. However, being one of the major hash algorithms, it is still used in many legacy systems including up to [10% of credit card payment systems][SHA1_creditcard]. 

In Feb 2017, researcher from Google and CWI Amsterdam together found the **first ever practical collision** (based on the previous [theoretical work][2011_shattered]) using highly efficient GPUs. Given the fact that the cost of such collision (75-150K USD), it is out of reach for individual hackers, unless they are part of nation-state hacking regimes. However, this breakthrough attack has affected real word applications such as code repositories (e.g. [webkit][sha1_webkit], [svn][SHA1_svn]) and [payment systems][sha1_payment].

<i class="fa fa-book" aria-hidden="true"></i> [SHAttered][SHAttered], their [paper][SHAttered_paper], and possibly [this <i class="fa fa-stack-overflow" aria-hidden="true"> discussion</i>][SHAttered_SO].

---

**2. [KRACK][KRACK] - Pit in the WiFi:** In spite of the fact that WPA2 has been [formally analyzed for its security][WPA2_formal] already in 2005, this flaw came as a surprise to the security community to become one of the most discussed attack disclosures of 2017. Since it is a flaw within the WiFi protocol (WPA2: IEEE 802.11i), it would potentially affects any device that uses WiFi. WPA2 encrypts the messages (WiFi frames) using a <span data-balloon="A type of encryption where each bit of the data is encrypted (using XOR) one at a time with the corresponding bit of randomly generated keystream." data-balloon-pos="up">stream cipher</span> (generally with AES-CCM), which offers security only if the keys, specifically the initialization vectors are never re-used. Initialization vector in WPA2 is constructed using a `packet number` counter, which starts from "**zero**" (when a device tries to connect to a WiFi access point). And it increments every now and then upto its maximum limit is reached, at which the rekeying should start again. This approach as it is has no defect, because, the `packet number` counter is automatic and can never be reset.

However, there is a small caveat! The aforementioned key used for encryption is derived by a **four way handshake** negotiation between the WiFi access point and the client device. KRACK attack exploits this handshake mechanism, specifically by blocking the third message of the handshake. When an attacker blocks this message (to be sent to the client), the access point falls back to its initial point, where the `packet number` counter resets to "**zero**", thereby causing the re-use of the stream cipher's keystream i.e. **K**ey **R**einstallation **A**tta**ck** (KRACK). At this point, the attacker tricks the client to connect to his malicious network and gains man-in-the-middle position between the access point and the benign client. Since the encryption provided by WiFi is broken, the attacker can decrypt all the WiFi frames and intercept all the traffic generated from the client. If the Internet traffic (via browsers) is secured using HTTPs, the man-in-the-middle position of the attacker gives him an opportunity to  **strip the 's'** from HTTPs using tools like [*`sslstrip`*] [SSLStrip].

<i class="fa fa-book" aria-hidden="true"></i> [KRACK Attack][KRACK], their [paper][KRACK_paper], and [this blog post][MG_Blog] by Matthew Green.

---

**3. [ROCA][ROCA] - Destruction of crypto by the coppersmiths**: The gist of public key cryptography e.g. RSA is that a pair of keys are generated - a public key and a matching private key. While the private key is neaver revealed to anyone, the public key can be distributed everywhere without fear of any compromise on security of the communication. Anyone can encrypt a message using this public key, however, it can only be decrypted by the private key by it's owner. What if the public key reveals some information about the private key? As one can guess, it could be disasterous!

In 2016, &Scaron;venda and Nemec et.al observed an interesting statistical properties extracted from a large number of public keys, in which the **bits of an RSA public key could leak information about design and implementation choices** such as the prime generation algorithm (refer [The Million-Key Question][key_origin] and the [tool][key_origin_tool]). Based on that, they extended their investigation just to realise in 2017 that a remote attacker can compute an RSA private key from the value of a public key based on an improvised variant of <span data-balloon-length="large" data-balloon="Coppersmith's attack describes a class of cryptographic attacks on the public-key cryptosystem RSA based on the Coppersmith method. Particular applications of the Coppersmith method for attacking RSA include cases when the public exponent e is small or when partial knowledge of the secret key is available." data-balloon-pos="up">**coppersmith's attack**<sup><i class="fa fa-wikipedia-w" aria-hidden="true"></i></sup></span>. More specifically, they discovered that the prime numbers generated by the library (RSALib) of a major manufacturer of cryptographic hardware (Infineon Technologies) significantly lacks entropy. Due to this, when these primes numbers are used to generate RSA public-private key pair, **just based on the public key, the matching private key can be derived**. 


Once the private key is derives, it can be misused to impersonate its legitimate owner, decrypt sensitive messages or forge digital signatures. This creates a huge mess where the flawed library is used for mass production, for example, [Estonian electronic ID (eID) cards][ROCA_impact]. 
<!-- $$p = k * M + (65537^a\ mod\ M)$$ -->

<i class="fa fa-book" aria-hidden="true"></i> [ROCA Attack][ROCA], their [paper][ROCA_paper], and tools (by [keychest][ROCA_test1] and [cryptosense][ROCA_test2]) to test the RSA keys.

<i class="fa fa-gift fa-4x fa-pull-left fa-border" aria-hidden="true"></i> Another attack called [DUHK][DUHK] is worth reading. **DUHK (Don't Use Hard-coded Keys)** is a vulnerability that affects devices using ANSI X9.31, a deprecated Random Number Generator (RNG) in conjunction with a hard-coded keys in VPNs that uses specific versions [FortiOS][FortiOS].


---


## Nation-state got pwned

**1. Wikileaks [CIA Vault 7][vault7]:** Wikileaks published a trove of more than 8,761 documents that are claimed to be from the US Central Intelligence Agency (CIA), which is possibly the largest intelligence publication in history. These leaked documents provide details about activities and capabilities of CIA regarding malwares targetted for phones(iPhone, Android) and smart TVs, operating systems (Windows, OSx, Linux) on PCs and routers, and <span data-balloon-length="large" data-balloon="A software vulnerability that is unknown to those who would be interested in mitigating the vulnerability (including the vendor of the target software). Until the vulnerability is mitigated, hackers can exploit it to adversely affect computer programs, data or a network." data-balloon-pos="up">zero-day<sup><i class="fa fa-wikipedia-w" aria-hidden="true"></i></sup></span> bugs for iOS and Android. Furthermore, these leaks reveal a framework (dubbed by Wikileaks as **Marble**) which allegedly assists the CIA to write customised malware that disguises their authorship, making it difficult for forensic investigators and anti-virus companies from attributing these malwares to the CIA. In addition to that it uncovers the techniques used by CIA to gain **persistant access** on Apple devices. 

<i class="fa fa-book" aria-hidden="true"></i> [Vault7][vault7] dump, Wired [series][wired_v7], Guardian [article][Gaurdian_v7], and [**Vault8**][vault8] - the source code + analysis of Vault7.

---

**2. [ShadowBrokers][shad_bro] -Bro(ker)s behind the shadow:** An anonymous hacking group, self-named as ShadowBrokers came into existance in [2016][Shad_bro_16] by announcing an auction of what it claimed as ["cyber weapons made by the NSA"][Shad_bro_16_2]. 


They continued in 2017 as well with their public embarrassing of the NSA by mocking its intelligence-gathering capabilities. They have exposed major vulnerabilities in Cisco routers, Microsoft Windows (e.g. e-mail client bugs and privilege escalation exploits) and other major firewall products. Furthermore, they allegedly gave the authors of the **WannaCry ransomware** the exploit they needed to infect a large number of computers. Similar to that of the CIA's tools exposed in Vault7, the leaks from shadowbrokers include executables used by the NSA to bypass for antivirus programs, disguise techniques and other zero-days.From August 2016 to April 2017, ShadowBrokers have leaked different arsenals with humurous names - _Equation Group Cyber Weapons Auction - Invitation_, _TrickOrTreat_, _Black Friday / Cyber Monday Sale_, _Don't Forget Your Base_ and _Lost in Translation_.


<i class="fa fa-book" aria-hidden="true"></i> [Blog post][shad_bro_tek] by [Tek](https://twitter.com/tenacioustek) which covers a wide range of pointers, [article][shad_bro] by TechCrunch. 


---

**3. [Macron hack][macron_hack] - The email macaroni:** It has happened in the past (e.g. [John Podesta][podesta_hack], [Hillary Clinton][HC_hack], [Democratic National Committee][DNC_hack] or [Erdogan][Erdogan_hack]), and it happened in 2017 too! In 2017, this unfortunate glory was credited to Emmanuel Macron, the then French presidential candidate. The 9GB worth of email dump just 48 hours before France's election, first over <span data-balloon="A site (pastebin.com) where one can anonymously store plain text." data-balloon-pos="up">PasteBin</span>containing links to torrent files, followed by an [archive on Wikileaks][macron_hack].

Whether or not Wikileaks dumping emails on public domains [passes Public Interest Test][zeynep_16], they probably [put women in danger, for no reason][zeynep_17]. On the positive side, they lead to some nice visualization projects to learn about the [networks][viz_email] or the [metadata][viz_metadata].

<i class="fa fa-book" aria-hidden="true"></i> [Wikileaks dump][macron_hack] and [article][macron_hack_wired] by Wired.

<i class="fa fa-gift fa-4x fa-pull-left fa-border" aria-hidden="true"></i> Citizen Lab's report called [**Tainted Leaks** - Disinformation and Phishing With a Russian Nexus][tainted_links] on an extensive phishing and disinformation campaign. This research uncovers Russian-led large phishing operation, with over 200 unique targets spanning 39 countries.


---

## Corporates got hit

**1. [Cloudbleed][cb_incident] - Leak in the memory:** Cloudfare, Inc.<span data-balloon-length="large" data-balloon="A U.S. company that provides a content delivery network, DDoS mitigation, Internet security services and distributed domain name server services, sitting between the visitor and the Cloudflare user's hosting provider, acting as a reverse proxy for websites." data-balloon-pos="up"><sup><i class="fa fa-wikipedia-w" aria-hidden="true"></i></sup></span> provides different kinds of service to companies like Uber, OK Cupid, and Fitbit, who transport sensitive user information (including Personally Identifiable Information) via Cloudfare. In Feb 2017, *Tavis Ormandy* - a security researcher from Project Zero team, noticed a serious issue in Cloudfare's proxy servers which was spilling sensitive data belonging to arbitary users of companies (including Uber, Ok Cupid and Fitbit) in spite the data being protected by HTTPS.


Cloudfare parses the HTML pages of their clients and modify specific HTML tags **on the fly**. For example, to rewrite `http://` links of a HTML page to `https://`, or obfuscate email addresses for privacy reasons. Earlier, these parsing task was done using an open source software called [Regal][regal], and in conjunction with that, an year before this bug was reported, Cloudfare started using another parser called cf-html. Both cf-html and Ragel parsers were implemented in such a way that one of them would parse and modify **buffers** (blocks of memory) containing specific HTML tags before passing it on to the other parser. Due to an implementation error by Cloudfare while writing the Regal code, a well-known security vulnerability called <span data-balloon-length="large" data-balloon="Anomaly where a program, while writing data to a buffer, overruns the buffer's boundary and overwrites adjacent memory locations." data-balloon-pos="up">**buffer overflow**<sup><i class="fa fa-wikipedia-w" aria-hidden="true"></i></sup></span> would spill information of arbitary users when webpages had **a particular combination of HTML tags**. While frankly admitting this [incident][cb_incident] and reacting quickly to minimize the [impact][cb_impact], "_Only a very small portion of web traffic was affected by this bug_" - says John Graham-Cumming, the CTO of Cloudflare.

<i class="fa fa-book" aria-hidden="true"></i> The [bug report][cd_bug_report] by Tavis, Cloudfare's [incident response][cb_incident] and the [article][cloudbleed] by The Register.

---


**2. [Equifax][eq_announcement] - the SSN spiller:** Credit card giant Equifax faced a massive data breach in September 2017 where sensitive information such as names, birthdates, addresses, driver’s license numbers, as well as Social Security Numbers 143 million consumers were exposed to the hackers. Due to its sensitivity [the company][eq_sec] as well the [FTC][equifax_FTC] tried to take measures to identify and lessen the harm. However, seems like it was too late. 

This blunder was due to [failure of Equifax to patch][struts_response] an earlier reported exploit in an open source software called **Apache Struts**. While the [exploit is almost 9 years old][equifax_qz], a security patch was released by Apache in March 2017. This exploit allowed the hackers to [misuse][struts_bug] the **file upload** functionality to **remotely execute malicious codes on the server**.

<i class="fa fa-book" aria-hidden="true"></i> [Announcement][eq_announcement] by Equifax, their [online tool][eq_sec] and Apache's [reponse][struts_response].

---

**3. [Cellebrite hack][cb1] - (bad) Hackers got hacked:** In January 2017, a hacker [reported][cb1] Mother Board with 900GB worth of data related to Cellebrite, which included Android, Blackberry and iOS [cracking tools][cb2]. Cellebrite is one of the most popular mobile phone hacking companies, known for their flagship product called **Universal Forensic Extraction Device (UFED)** which can extract data (e.g. SMS messages, emails) from mobile phones. As a surveillance tech company, Cellebrite offers service to wide range of organizations including [law enforcement agencies][mb_police], [repressed regimes][mb_regime] (of Russia, the United Arab Emirates, and Turkey) as well as the [banks][mb_bank].

<i class="fa fa-book" aria-hidden="true"></i>  [**Phone Crackers**][mb_series] series by *Joseph Cox*, Motherboard .

<i class="fa fa-gift fa-3x fa-pull-left fa-border" aria-hidden="true"></i> Another disaster where [**198 million voters got exposed**][voters_exposed] from a [misconfigured storage server][server_misconf]. Interestingly, they shed some light on [**(big)data-driven election campaigns**][bdd_campaign].



---

<!--  - Others such as Virgin America, Deloitte, as usual Yahoo, Verifone -->

## Malwares (To-do)
<!--  - [Value of security hygine][msr_security_hygine]-->

 - WannaCry
 - Petya/NotPetya/Nyetya/Goldeneye
 - BadRabbit 
 
<!--  [msr_security_hygine]: https://blogs.technet.microsoft.com/mmpc/2017/09/06/ransomware-1h-2017-review-global-outbreaks-reinforce-the-value-of-security-hygiene/ -->

---

## <i class="fa fa-bookmark" aria-hidden="true"></i> Recommended reading

 - [The Biggest Cybersecurity Disasters of 2017 So Far][wired_2017] - **Wired**
 - [2017's biggest hacks, leaks, and data breaches][ZDNet_2017] - **ZDNet**
 - [Nation-State Hacking: 2017 in Review][EFF_2017] and [other articles][EFF_Series_2017] from the same series - **EFF**

<!-- Referenes -->
<!---2016 recap -->

[heist]: https://www.blackhat.com/docs/us-16/materials/us-16-VanGoethem-HEIST-HTTP-Encrypted-Information-Can-Be-Stolen-Through-TCP-Windows-wp.pdf
[drown]: https://drownattack.com/
[sweet32]: https://sweet32.info/#about
[dirtyc0w]: https://dirtycow.ninja/
[tls13_spec]:https://tlswg.github.io/tls13-spec/draft-ietf-tls-tls13.html
[rfc7748]: https://tools.ietf.org/html/rfc7748
[tls13_due]:https://blog.cloudflare.com/why-tls-1-3-isnt-in-browsers-yet/
[eff2016]:https://www.eff.org/deeplinks/2016/12/what-happened-crypto-2016
[tls13_test]:https://tls13.mitm.watch/

<!---SHAttered -->

[SHAttered]:https://shattered.io/
[2005_shattered]:https://link.springer.com/chapter/10.1007%2F11535218_2
[2011_shattered]:https://link.springer.com/chapter/10.1007%2F978-3-642-38348-9_15
[SHA1_creditcard]: https://threatpost.com/sha-1-end-times-have-arrived/123061/
[SHA1_svn]: http://blogs.collab.net/subversion/subversion-sha1-collision-problem-statement-prevention-remediation-options
[sha1_webkit]: https://arstechnica.com/information-technology/2017/02/watershed-sha1-collision-just-broke-the-webkit-repository-others-may-follow/
[sha1_payment]: https://blog.pcisecuritystandards.org/how-the-sha-1-collision-impacts-security-of-payments
[SHAttered_paper]:https://shattered.io/static/shattered.pdf
[SHAttered_SO]: https://security.stackexchange.com/a/152176/57069

<!---Krack -->

[KRACK]: https://www.krackattacks.com/
[KRACK_paper]:https://papers.mathyvanhoef.com/ccs2017.pdf
[WPA2_formal]:https://www.andrew.cmu.edu/user/danupam/hsddm-ccs05.pdf
[SSLStrip]: https://github.com/moxie0/sslstrip
[MG_Blog]: https://blog.cryptographyengineering.com/2017/10/16/falling-through-the-kracks/


<!---ROCA -->

[ROCA]:https://crocs.fi.muni.cz/public/papers/rsa_ccs17
[ROCA_paper]: https://crocs.fi.muni.cz/_media/public/papers/nemec_roca_ccs17_preprint.pdf

[key_origin]:[https://www.usenix.org/node/197198]
[key_origin_tool]: https://www.fi.muni.cz/~xsekan/

[ROCA_test1]: https://keychest.net/roca
[ROCA_test2]:https://keytester.cryptosense.com
[ROCA_impact]:https://arstechnica.com/information-technology/2017/10/crypto-failure-cripples-millions-of-high-security-keys-750k-estonian-ids/

[DUHK]: https://duhkattack.com/
[FortiOS]:https://www.fortinet.com/products/fortigate/fortios.html.


<!-- Recommended reading -->

[wired_2017]:https://www.wired.com/story/2017-biggest-hacks-so-far/
[ZDNet_2017]:http://www.zdnet.com/pictures/biggest-hacks-leaks-and-data-breaches-2017/
[EFF_2017]: https://www.eff.org/deeplinks/2017/12/2017-year-nation-state-hacking
[EFF_Series_2017]:https://www.eff.org/deeplinks/2017/12/year-review-security-education-roundup

<!-- Vault 7 -->

[vault7]:https://wikileaks.org/ciav7p1/
[wired_v7]:https://www.wired.com/tag/vault-7/
[vault8]: https://wikileaks.org/vault8/
[Gaurdian_v7]: https://www.theguardian.com/technology/2017/mar/08/wikileaks-vault-7-cia-documents-hacked-what-you-need-to-know


<!-- Macron Hacked -->

[HC_hack]: https://wikileaks.org/clinton-emails/
[podesta_hack]: https://wikileaks.org/podesta-emails/
[DNC_hack]:https://wikileaks.org/dnc-emails/
[Erdogan_hack]: https://wikileaks.org/akp-emails/
[macron_hack]: https://wikileaks.org/macron-emails/

[zeynep_16]:https://www.npr.org/2016/10/22/498954190/wikileaks-dump-method-destroys-privacy-sociologist-says-not-all-leaked-pass-publ
[zeynep_17]:https://www.huffingtonpost.com/zeynep-tufekci/wikileaks-erdogan-emails_b_11158792.html

[macron_hack_wired]: https://www.wired.com/2017/05/macron-email-hack-french-election/

[viz_email]: https://clinton.media.mit.edu/
[viz_metadata]:https://labs.rs/en/metadata/


[tainted_links]: https://citizenlab.ca/2017/05/tainted-leaks-disinformation-phish/


<!-- ShadowBrokers -->

[Shad_bro_16]:https://www.theguardian.com/technology/2016/aug/16/shadow-brokers-hack-auction-nsa-malware-equation-group
[Shad_bro_16_2]:https://techcrunch.com/2016/08/19/snowden-docs-link-nsa-to-equation-group-hackers/

[shad_bro]: https://techcrunch.com/2017/04/08/shadow-brokers-be-back/
[shad_bro_tek]: https://www.randhome.io/blog/2017/04/14/shadowbrokers-easter-gift/

[voters_exposed]:[https://www.wired.com/story/voter-records-exposed-database/]
[server_misconf]:https://www.upguard.com/breaches/the-rnc-files
[bdd_campaign]: http://adage.com/article/campaign-trail/trump-camp-s-inexperience-set-stage-rnc-data-win/307105/


<!-- Cloudbleed -->

[cb_incident]: https://blog.cloudflare.com/incident-report-on-memory-leak-caused-by-cloudflare-parser-bug/
[cb_impact]: https://blog.cloudflare.com/quantifying-the-impact-of-cloudbleed/
[regal]: https://www.colm.net/open-source/ragel/
[cloudbleed]: https://www.theregister.co.uk/2017/02/24/cloudbleed_buffer_overflow_bug_spaffs_personal_data/
[cd_bug_report]: https://bugs.chromium.org/p/project-zero/issues/detail?id=1139

<!-- Equifax hack -->

[eq_announcement]: https://investor.equifax.com/news-and-events/news/2017/09-07-2017-213000628
[equifax_qz]:https://qz.com/1073221/the-hackers-who-broke-into-equifax-exploited-a-nine-year-old-security-flaw/
[equifax_FTC]: https://www.consumer.ftc.gov/blog/2017/09/equifax-data-breach-what-do
[eq_sec]:https://www.equifaxsecurity2017.com/
[struts_response]: https://blogs.apache.org/foundation/entry/media-alert-the-apache-software
[struts_bug]: http://blog.talosintelligence.com/2017/03/apache-0-day-exploited.html

<!-- cellebrite -->

[cb1]: https://motherboard.vice.com/en_us/article/3daywj/hacker-steals-900-gb-of-cellebrite-data 
[cb2]:https://motherboard.vice.com/en_us/article/5355ga/hacker-dumps-ios-cracking-tools-allegedly-stolen-from-cellebrite
[mb_series]:[https://motherboard.vice.com/en_us/topic/phone-crackers]
[mb_bank]: https://motherboard.vice.com/en_us/article/ezp9kp/banks-use-cellebrite-phone-cracking-tech-too
[mb_regime]: https://motherboard.vice.com/en_us/article/aekqjj/cellebrite-sold-phone-hacking-tech-to-repressive-regimes-data-suggests
[mb_police]: https://motherboard.vice.com/en_us/article/aekqkj/us-state-police-have-spent-millions-on-israeli-phone-cracking-tech-cellebrite



