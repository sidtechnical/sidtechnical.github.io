---
layout: post
title: Tinkering with Firefox browsing history for analysis
categories:
- blog
- analysis
published: false
---

Modern browsers such as Firefox, Google Chrome, Opera and Internet Explorer stores the browsing history to provide a user-friendly browsing experience. By default, these browsers store the history of all the previously visited websites, cached copy of the websites, form filling history, cookie information and also bookmarks. Depending on the operating system and the browser, these information will be stored in a specific location, in an sqlite database. For example, in Ubuntu (or most of the Debian based systems) the Firefox related data is stored in 




 Some of us rant about this default nature of the browsers, as it compels users to manually opt-out of browsing history storing mechanisms and the privacy concerns assosiated with it. Browser history - specifically the website information and cached copy has its own advantage in terms of usability:

1. Automatic completion/suggestion of previously visited URLs.
2. Locally cached copies of the previously visited websited to boost up the browsing speed, which is very helpful when the Internet connection is very slow. 

Since, browisng history provides a rich source of metadata of our daily interactions with the Internet world, it is indeed an interesting thing to analyze. 



