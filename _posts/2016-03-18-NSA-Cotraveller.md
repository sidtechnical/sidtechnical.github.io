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
 

For some reasons, I took special interest to dig deep into vulnerabilities based on SS7 protocol and I have discussed the same in my subsequent publications such as unblocking stolen mobiles using SS7-MAP vulnerabilities or downgrading LTE networks using to enable user tracking. In this post, I will continue what Ashkan has discussed in his article to provide a deeper insight on **How NSA did it**! Mainly, I will discuss the end-to-end mechanism of NSA’s _**Co-traveller**_ surveillance program.
