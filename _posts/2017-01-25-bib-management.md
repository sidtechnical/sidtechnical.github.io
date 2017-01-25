---
layout: post
title:  Bibliography management from multiple resources using multibib.
categories: 
  - blog
  - latex, writing
published: true
---

Eventhough LaTeX is an amazing typesetting tools, some small tweaks might take more time than one can assume. However, everything is customizable according to our needs; and the credit definitely should go to the community which is actively contributing to the development.

Recently, I ran across the problem of citing from mulitple bibliography sources and split the bibliography/references into different sections. Ideally, if there is just one ```.bib``` source, when you cite it using normal conventions, every citation would appear in one whole section. Initial web searches pointed me at the [multibib package](https://www.ctan.org/pkg/multibib?lang=en) and I thought it is a straighforward approach to just use that package and complie my .tex source.

It turned out to be a really good learning experience for me. After several hours well spent in [Tex - Stack Exchange](http://tex.stackexchange.com/), I realized once again that "Every beautuiful thing in life has a price; So do LaTeX". This is why I decided to write this blog post.

## Problem statement

For the sake of understanding what I am trying to achieve, here is the minimalistic problem statement without digging into the obvious background of LaTeX. 

* I have multiple bibliography files.
* I want to display the bibilographies in different sections.
* I am using Ubuntu 16.04 (which [limited](https://askubuntu.com/questions/761985/textlive-bibtex-extra-and-biber-conflict) my options to just ```multibib``` in spite of the claim that the bug was fixed.) and TexMaker (which gices errors while comiling when you have multibib. So, as always GUI is not an option for me.)

### Minimal Working Example (MWE)

Once you know how to use multibib, it works like a charm! 

So, let us walk through an example, first by creating a skeleton latex file - say ```document.text``` with the following preamble code in it.

```
\documentclass{article}
\usepackage{multibib}
\usepackage{lipsum} %package to generate dummy text.


\begin{document}
\lipsum[1] %generating dummy text

\end{document}
```
The output pdf (document.pdf) when I run ```pdflatex document.tex```, it looks like this.
---
![Bare minimal PDF without citation]({{site.baseurl}}/assets/images/bare_minimal_pdf.png)
---

Now, I have four bibliography files as follows:

* [bibliography.bib](https://raw.githubusercontent.com/sidtechnical/sidtechnical.github.io/master/assets/files/bibliography.bib) which I intend to use it as the genric bibiliography file. It means, I can just cite the content within this file strightaway using ```\cite{<xxx>}``` and it appears in the end of the output PDF.
* [security.bib](https://raw.githubusercontent.com/sidtechnical/sidtechnical.github.io/master/assets/files/security.bib), [privacy.bib](https://raw.githubusercontent.com/sidtechnical/sidtechnical.github.io/master/assets/files/privacy.bib) and [encryption.bib](https://raw.githubusercontent.com/sidtechnical/sidtechnical.github.io/master/assets/files/encryption.bib) which I intend to cite them in different section so that the citations from these files are displayed right after the section, rather than appearin in the end of the PDF document.

Suppose, I want to have the bibliography in alpha style by default, i can define it by adding the following line in the preamble *i.e.* before the occurence of ```\begin{document}```

```
\bibliographystyle{alpha}
```



