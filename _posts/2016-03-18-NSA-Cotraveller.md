---
layout: post
title: "Surveillance - How NSA did it using signalling protocols?"
categories: 
  - blog
  - projects
published: true
---


Most of us have read Washington Post’s coverage of National Security issues, in particular the investigative articles on Snowden files. Several people have done research based on the [files revealed by Snowden](https://cryptome.org/2013/11/snowden-tally.htm) mainly to contribute to investigative journalism series(e.g. “What They Know” series by Wall Street Journal). Out of such abundant information and interpretations available on the Internet, [Ashkan Soltani](https://twitter.com/ashk4n)’s series on the [analysis of backend systems used by NSA during mass surveillance](http://ashkansoltani.org/work/washpost/) sought my interest for the following two reasons: 
1. It is a well narrated series both in terms of technical depth and impact on the end-users (civilians).
2. The backend systems extensively utilized a protocol called “Siganlling System No. 7” - which has been the area of my interest since my [master’s thesis](https://aaltodoc.aalto.fi/handle/123456789/19044).



For some reasons, I took special interest to dig deep into vulnerabilities based on SS7 protocol and I have discussed the same in my subsequent publications such as [unblocking stolen mobiles using SS7-MAP vulnerabilities](http://sidtechnical.github.io/2016/03/16/eeexplore.ieee.org/xpls/abs_all.jsp?arnumber=7345408) or downgrading LTE networks using to enable user tracking. In this post, I will continue what Ashkan has discussed in his article to provide a deeper insight on **How NSA did it**! Mainly, I will discuss the end-to-end mechanism of NSA’s _**Co-traveller**_ surveillance program.

NSA exploited the loopholes in _Radio Access Network (RAN)_ of mobile telephony target specific people to intercept there conversation. Remember [Angela Merkel's calls being trapped](https://www.washingtonpost.com/news/the-switch/wp/2013/10/24/the-switchboard-angela-merkel-reportedly-livid-over-alleged-nsa-surveillance/)!! RAN is the communication channel between your mobile phones to the _cell towers_ or _base stations_, and NSA planted fake base stations which are popularly known as **IMSI catchers** to conduct such targeted interception of mobile communication. However, this method is not effective enough to scale to perform mass surveillance as installing the IMSI catchers everywhere in the world is practically an infeasible idea. That too when NSA could simply exploit the backend of telecommunication called _core network_ using one of the signalling protocol called **Signalling System No. 7 (SS7)**. Relying on such protocols provided NSA with easy remote access to mobile users's data which indeed made mass surveillance an easier task.

The NSA exploited the core network and signalling sytems worldwide to track locations of civilians in the name of a program called _Co-travellers_. Through this program NSA collected 5 billion user records per day to find and develop more suspected targets! Co-traveller was indeed a sophisticated end-to-end surveillance system to collect and analyze data from signalling systems. The figure below depicts the overall architecture:
![NSA Co-traveller surveillance architecture]({{site.baseurl}}/_posts/NSA_Fascia_Cotraveller.png)





