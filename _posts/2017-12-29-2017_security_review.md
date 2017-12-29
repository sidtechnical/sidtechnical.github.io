---
layout: post
title:  'Security vs. the Internet: 2017 in Review'
categories: 
  - blog
tags:
  - security
favorite: true
published: true
---

<i class="fa fa-quote-left fa-4x fa-pull-left fa-border" aria-hidden="true"></i> ***Disclaimer:** <font style="font-size:medium" color="#000066">Though I intend to cover all the major security breaches of 2017, it is nearly impossible to  make an exhaustive list of all of them. Even if it is possible, it won't be suitable for a compressed blog post like this. It is very much possible that I might have missed a "must-have" breach because of the 'Internet filter bubble' that we all live in. Please consider bringing it to my notice!</font>*

<i class="fa fa-clock-o" aria-hidden="true"></i> **A brief recap of 2016**: On the offensive side, attacks like [HEIST][heist], [DROWN][drown], [Sweet32][sweet32] and [Dirty C0W][dirtyc0w] got media attention that they deserved. On the defensive side, Transport Layer Security (TLS) 1.3 [design][tls13_spec] was finalized, which includs the standardization of elliptic curves - Curve25519 and Curve448 ([RFC 7748][rfc7748]) to ensure a high level of practical security. 

However, 2017 is almost over now, and yet TLS 1.3 is not in browsers. There is no doubt about the difficulties of upgrading a security protocol in the Internet; it requires both the servers and clients (browsers in this case) to adopt this changes parallely. While many server vendors have taken the first step to upgrade to TLS 1.3, the browser vendors are still [lagging behind][tls13_due] to enabled it by default. Even though the browser evndors blame the <span data-balloon-length="large" data-balloon="A middlebox or network appliance is a computer networking device that transforms, inspects, filters, or otherwise manipulates traffic for purposes other than packet forwarding. Common examples of middleboxes include firewalls." data-balloon-pos="up">middleboxes<sup><i class="fa fa-wikipedia-w" aria-hidden="true"></i></sup></span>, the real reason is *"<font color="#000066">the original design of TLS 1.3 was incompatible with the way the Internet has evolved over time</font>"* - says Nick Sullivan, the Head of Cryptography - ‎Cloudflare, Inc. 

<i class="fa fa-book" aria-hidden="true"></i> [2016 in review][eff2016], [Nick's blog post][tls13_due] and <span data-balloon="It helps check if your network is compatible with TLS 1.3." data-balloon-pos="up">[middlebox test tool][tls13_test]</span>.

---

# Fast-forward to 2017

Security breaches are one of the most recurring columns of most of the news media, because they happen every year, every now and then.  The year 2017 is no exception to that!

While some of them could expose previously unknown vulnerabilities or intorduce a new bug, many of the rest are just reusing well-known vulnerabilities on a different attack surfaces. Reasons could range from inefficient threat models and anlysis to incorrect implementions while bringing theoretical security to practice. Irrespective of the reasoning, public disclosures of the security breaches help us learn from the mistakes and build more secure systems.

## Research: Vulnerabilities 

**1. [SHAttered][SHAttered] - (Practical) collision of SHA-1:** <span data-balloon="a mathematical one-way function which converts (represents) any arbitary size of data into a fixed-size bit string" data-balloon-pos="up">Cryptographic hashes</span> form one of the backbones of modern information security, because many authentication (e.g. digital signatures or message authentication codes) rely on it. These hashes must ensure <span data-balloon="deterministic, fast one-way only (while finding the hash), infeasiable to reverse" data-balloon-pos="up">several properties</span>, out of which **collision-resistance** is one of the most fragile points.
In theory, the only way to find a collision is by <span data-balloon="exhaustively list every possible message space (data), followed by finding a matching hash" data-balloon-pos="up">brute-force</span>, however, thishas been tampered every time the computer architecture gets improvised, or when a clever way of reducing the complexity is discovered. Ever since, the theoretical collisions were found for SHA-1 ([2005][2005_shattered], [2011][2011_shattered]), it has been depricated. However, being one of the major hashing algorithms, it is still used in many legacy systems including up to [10% of credit card payment systems][SHA1_creditcard]. 

In Feb 2017, researcher from Google and CWI Amsterdam together found the **first ever practical collision** (based on the previous [theoretical work][2011_shattered]) using highly efficient GPUs. Given the fact that the cost of such collision (75-150K USD), it is out of reach for individual hackers, unless they are part of nation-state hacking regimes. However, this breakthrough attack has affected real word applications such as code repositories (e.g. [webkit][sha1_webkit], [svn][SHA1_svn]) and [payment systems][sha1_payment].

<i class="fa fa-book" aria-hidden="true"> [SHAttered][SHAttered], their [paper][SHAttered_paper], and possibly [this <i class="fa fa-stack-overflow" aria-hidden="true"> discussion</i>][SHAttered_SO].

---


**2. [KRACK attack][KRACK] **

**3. ROCA**: First origin of RSA public keys [1][key_origin] , [tool][key_origin_tool].Then [ROCA][ROCA] refer to [imapct][ROCA_impact], [ROCA TEST1][ROCA_test1] or [ROCA TEST2][ROCA_test2]  ACM CCS conference, received Real-World Impact Award 



[DUHK][DUHK]

[KRACK]: https://www.krackattacks.com/
[DUHK]: https://duhkattack.com/
[key_origin]:[https://www.usenix.org/node/197198]
[key_origin_tool]: https://www.fi.muni.cz/~xsekan/
[ROCA]:https://crocs.fi.muni.cz/public/papers/rsa_ccs17
[ROCA_test1]: https://keychest.net/roca
[ROCA_test2]:https://keytester.cryptosense.com
[ROCA_impact]:https://arstechnica.com/information-technology/2017/10/crypto-failure-cripples-millions-of-high-security-keys-750k-estonian-ids/

## Malwares
 - [Value of security hygine][msr_security_hygine]
 - WannaCry
 - Petya/NotPetya/Nyetya/Goldeneye
 - BadRabbit

 [msr_security_hygine]: https://blogs.technet.microsoft.com/mmpc/2017/09/06/ransomware-1h-2017-review-global-outbreaks-reinforce-the-value-of-security-hygiene/

## Related to governments
- Wikileaks [CIA Vault 7][vault7]
- [Shadow Brokers][shad_bro] series (wikipedia), [Etienne][shad_bro_tek]
- Macron Campaign Hack
- Votes got exposed https://www.wired.com/story/voter-records-exposed-database/

[vault7]:https://wikileaks.org/ciav7p1/
[shad_bro]: https://techcrunch.com/2017/04/08/shadow-brokers-be-back/
[shad_bro_tek]: https://www.randhome.io/blog/2017/04/14/shadowbrokers-easter-gift/
[macron_hack]: https://www.wired.com/2017/05/macron-email-hack-french-election/

## Related to corporates
 - [Cloudbleed][cloudbleed], [incedent report][cb_incident], [impact][cb_impact]
 - [Equifax][equifax]
 - [celebrite1][cellebrite 1] and [celebrite2][cellebrite 2]
 - Others such as Virgin America, Deloitte, as usual Yahoo, Verifone


[cloudbleed]: https://www.theregister.co.uk/2017/02/24/cloudbleed_buffer_overflow_bug_spaffs_personal_data/
[cb_incident]: https://blog.cloudflare.com/incident-report-on-memory-leak-caused-by-cloudflare-parser-bug/
[cb_impact]: https://blog.cloudflare.com/quantifying-the-impact-of-cloudbleed/
[equifax]: https://www.consumer.ftc.gov/blog/2017/09/equifax-data-breach-what-do
[cellebrite 1]: https://motherboard.vice.com/en_us/article/3daywj/hacker-steals-900-gb-of-cellebrite-data 
[cellebrite 2]:https://motherboard.vice.com/en_us/article/5355ga/hacker-dumps-ios-cracking-tools-allegedly-stolen-from-cellebrite


## Read more
- https://www.wired.com/story/2017-biggest-hacks-so-far/
- http://www.zdnet.com/pictures/biggest-hacks-leaks-and-data-breaches-2017/
- https://www.eff.org/deeplinks/2017/12/2017-year-nation-state-hacking


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