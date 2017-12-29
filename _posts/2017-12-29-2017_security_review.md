---
layout: post
title:  'Security vs. the Internet: 2017 in Review'
categories: 
  - blog
tags:
  - security
favorite: true
published: false
---

<i class="fa fa-quote-left fa-4x fa-pull-left fa-border" aria-hidden="true"></i> ***Disclaimer:** <font style="font-size:medium" color="#000066">Though I intend to cover all the major security breaches of 2017, it is nearly impossible to  make an exhaustive list of all of them. Even if it is possible, it won't be suitable for a compressed blog post like this. It is very much possible that I might have missed a "must-have" breach because of the 'Internet filter bubble' that we all live in. Please consider bringing it to my notice!</font>*

Security breaches are one of the most recurring columns of most of the news media, because they happen every year, every now and then.  The year 2017 is no exception to that!

<i class="fa fa-clock-o" aria-hidden="true"></i> **A brief recap of 2016**: On the offensive side, attacks like [HEIST][heist], [DROWN][drown], [Sweet32][sweet32] and [Dirty C0W][dirtyc0w] got media attention that they deserved. On the defensive side, Transport Layer Security (TLS) 1.3 [design][tls13_spec] was finalized, which includs the standardization of elliptic curves - Curve25519 and Curve448 ([RFC 7748][rfc7748]) to ensure a high level of practical security. 

However, 2017 is almost over now, and yet TLS 1.3 is not in browsers. There is no doubt about the difficulties of upgrading a security protocol in the Internet; it requires both the servers and clients (browsers in this case) to adopt this changes parallely. While many server vendors have taken the first step to upgrade to TLS 1.3, the browser vendors are still [lagging behind][tls13_due] to enabled it by default. Even though the browser evndors blame the <span data-balloon-length="large" data-balloon="A middlebox or network appliance is a computer networking device that transforms, inspects, filters, or otherwise manipulates traffic for purposes other than packet forwarding. Common examples of middleboxes include firewalls." data-balloon-pos="up">middleboxes<sup><i class="fa fa-wikipedia-w" aria-hidden="true"></i></sup></span>, the real reason is *"<font color="#000066">the original design of TLS 1.3 was incompatible with the way the Internet has evolved over time</font>"* - says Nick Sullivan, the Head of Cryptography - ‎Cloudflare, Inc. 

<i class="fa fa-book" aria-hidden="true"></i> [2016 in review][eff2016], [Nick's blog post][tls13_due] and <span data-balloon="It helps check if your network is compatible with TLS 1.3." data-balloon-pos="up">[middlebox test tool][tls13_test]</span>.

---

# Fast-forward to 2017

While Some of them could expose previously unknown vulnerabilities or intorduce a new bug, many of the rest are just reusing well-known vulnerabilities on a different attack surfaces. Reasons could range from inefficient threat models and anlysis to incorrect implementions while bringing theoretical security to practice. Irrespective of the reasoning, public disclosures of the security breaches help us learn from the mistakes and build more secure systems.

## Research: Vulnerabilities 

- **[SHAttered][SHAttered]** - (Practical) collision of SHA-1 found: We reliy on the cryptographic hash functions in our day-to-day digital lives. For example, those hashes are used for digital signatures or while securely browsing over HTTPS. 

https://arstechnica.com/information-technology/2017/02/watershed-sha1-collision-just-broke-the-webkit-repository-others-may-follow/
http://blogs.collab.net/subversion/subversion-sha1-collision-problem-statement-prevention-remediation-options
https://security.stackexchange.com/a/152176/57069
https://www.cylance.com/en_us/blog/how-sha-1-collisions-can-affect-us-in-real-world-attacks.html


- **[KRACK attack][KRACK] and [DUHK][DUHK]**
- **ROCA**: First origin of RSA public keys [1][key_origin] , [tool][key_origin_tool].Then [ROCA][ROCA] refer to [imapct][ROCA_impact], [ROCA TEST1][ROCA_test1] or [ROCA TEST2][ROCA_test2]  ACM CCS conference, received Real-World Impact Award 

[SHAttered]:https://shattered.io/
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

[heist]: https://www.blackhat.com/docs/us-16/materials/us-16-VanGoethem-HEIST-HTTP-Encrypted-Information-Can-Be-Stolen-Through-TCP-Windows-wp.pdf
[drown]: https://drownattack.com/
[sweet32]: https://sweet32.info/#about
[dirtyc0w]: https://dirtycow.ninja/
[tls13_spec]:https://tlswg.github.io/tls13-spec/draft-ietf-tls-tls13.html
[rfc7748]: https://tools.ietf.org/html/rfc7748
[tls13_due]:https://blog.cloudflare.com/why-tls-1-3-isnt-in-browsers-yet/
[eff2016]:https://www.eff.org/deeplinks/2016/12/what-happened-crypto-2016
[tls13_test]:https://tls13.mitm.watch/