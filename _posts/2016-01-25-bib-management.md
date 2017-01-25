{
	.tex sub, .latex sub, .latex sup {
  text-transform: uppercase;
}

.tex sub, .latex sub {
  vertical-align: -0.5ex;
  margin-left: -0.1667em;
  margin-right: -0.125em;
}

.tex, .latex, .tex sub, .latex sub {
  font-size: 1em;
}

.latex sup {
  font-size: 0.85em;
  vertical-align: 0.15em;
  margin-left: -0.36em;
  margin-right: -0.15em;
}
}


---
layout: post
title: Bibilography management from multiple resources in <span class="latex">L<sup>a</sup>T<sub>e</sub>X</span> using multibib package.
categories: 
  - blog
  - latex, writing
published: true
---

Eventhough <span class="latex">L<sup>a</sup>T<sub>e</sub>X</span> is an amazing typesetting tools, some small tweaks might take more time than one can assume. However, everything is customizable according to our needs; and the credit definitely should go to the community which is actively contributing to the development.

Recently, I ran across the problem of citing from mulitple bibilography sources and split the bibilography/references into different sections. Ideally, if there is just one ```.bib``` source, when you cite it using normal conventions, every citation would appear in one whole section. Initial web searches pointed me at the [multibib package](https://www.ctan.org/pkg/multibib?lang=en) and I thought it is a straighforward approach to just use that package and complie my .tex source.

It turned out to be a really good learning experience for me. After several hours well spent in [Tex - Stack Exchange](http://tex.stackexchange.com/), I realized once again that "Every beautuiful thing in life has a price; So do <span class="latex">L<sup>a</sup>T<sub>e</sub>X</span>". This is why I decided to write this blog post.

## Problem statement

For the sake of understanding what I am trying to achieve, here is the minimalistic problem statement without digging into the obvious background of <span class="latex">L<sup>a</sup>T<sub>e</sub>X</span>. 

* I have multiple bibilography files.
* I want to display the bibilographies in different sections.
* I am using Ubuntu 16.04 (which [limited](https://askubuntu.com/questions/761985/textlive-bibtex-extra-and-biber-conflict) my options to just ```multibib``` in spite of the claim that the bug was fixed.) and TexMaker (which gices errors while comiling when you have multibib. So, as always GUI is not an option for me.)

### Minimal Working Example (MWE)

Once you know how to use multibib, it works like a charm! 

So, let us walk through an example, first by creating a skeleton latex file - say ```document.text``` with the following preamble code in it.

```
\documentclass{article}
\usepackage{multibib}


\begin{document}

\end{document}
```

