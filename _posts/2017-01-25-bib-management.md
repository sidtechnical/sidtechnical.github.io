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

and I can cite anything by defining the bibliography file by adding the line ```\bibliography{<_name_of_the_bib_file>.bib}``` and citing a specific item in that bib file by the code \cite{name_of_the_handle}. As I mentioned earlier, I will be using bibiliography.bib as the default and I will cite both the items in by adding the following lines to my document.tex file.


```python
\documentclass{article}
\usepackage{multibib}
\usepackage{lipsum} %package to generate dummy text.

\bibliographystyle{alpha}%default style for generic bibliography.

\begin{document}
\lipsum[1] %generating dummy text
Let us \cite{casti1994complexification} and \cite{schloss2009introducing} from the generic bibilogrpahy. 

\bibliography{bibliography.bib}
\end{document}
```

The output pdf has to be compiled by running ```pdflatex document.tex```, followed by ```bibtex document.aux``` and again running ```pdflatex document.tex``` twice. The output pdf looks like follows:
P.S: This can be done in TexMaker just by pressing **F1** (shortcut for "Quick Build")),

![Genric citation]({{site.baseurl}}/assets/images/generic_citation_pdf.png)

Until now, everything is straighforward. Now, we will have to add new bibliographies and code to allow us to cite it from those files in the following format:

```python
\newcites{<_bib_handle>}{<Name for the reference section>}
```
Since we have three other files, and to easily recognize them, I will add the following lines of code to the preamble of the tex file.

```python
\newcites{sec}{Citations related to security}
\newcites{priv}{Citations related to privacy}
\newcites{enc}{Citations related to encryption}

```

Now, if we want to cite from the security.bib file, we have to cite it as follows:

```python
\documentclass{article}
\usepackage{multibib}
\usepackage{lipsum} %package to generate dummy text.

\bibliographystyle{alpha} %default style for generic bibliography.

\newcites{sec}{Citations related to security}
\newcites{priv}{Citations related to privacy}
\newcites{enc}{Citations related to encryption}



\begin{document}
\lipsum[1] %generating dummy text
Let us \cite{casti1994complexification} and \cite{schloss2009introducing} from the generic bibilogrpahy. 

\section{Content about security}
I am citing \citesec{kandukuri2009cloud} from the security.bib file.
\bibliographystylesec{alpha} % remember to add the bibliography style
\bibliographysec{security.bib} and mention the bib file.

\bibliography{bibliography.bib}
\end{document}
```
Now comes thre twist! Unlike the bare minimal example, we cannot simply compile from TexMaker. Instead we have to compile all the ``` .aux``` file manually from the command line. The order of compiling is as follows:

```bash
pdflatex document.tex %no change from the generic citation example
bibtex document.aux  %no change from the generic citation example
% Since we added the command for security.bib as \newcites{sec}{Citations related to security}, 
% it creates an auxilliary file by the name sec.aux, which has to be manually compiled with bibtex.

bibtex sec.aux 

pdflatex document.tex
pdflatex document.tex

The output pdf looks like below:

![citation sectionwise]({{site.baseurl}}/assets/images/section_wise_citation_pdf.png)


Also, to add all the citations from a bibliography file without citing them can be displayed in the list of bibliography section using ```\noite{*}``` in which it loads everything from our generic ```bibliography.bib``` file. To do the same from other bibliography files, we have to use nocitepriv{*} and nociteenc{*}.

So, the final code in document.tex will look like this:

```python
\documentclass{article}
\usepackage{multibib}
\usepackage{lipsum} %package to generate dummy text.

\bibliographystyle{alpha} %default style for generic bibliography.

\newcites{sec}{Citations related to security}
\newcites{priv}{Citations related to privacy}
\newcites{enc}{Citations related to encryption}



\begin{document}
\lipsum[1] %generating dummy text
Let us \cite{casti1994complexification} and \cite{schloss2009introducing} from the generic bibilogrpahy. 

\section{Content about security}
I am citing \citesec{kandukuri2009cloud} from the security.bib file.
\bibliographystylesec{alpha} % remember to add the bibliography style
\bibliographysec{security.bib} and mention the bib file.

\section{Content about privacy}
\nocitepriv{*}
\bibliographystylepriv{alpha}
\bibliographypriv{privacy.bib}
%
\section{Content about encryption}
\nociteenc{*}
\bibliographystyleenc{alpha}
\bibliographyenc{encryption.bib}


\bibliography{bibliography.bib}
\end{document}
```

This has to be compiled in the terminal as follows:

``` bash

pdflatex document.tex

% The mandatory additional step is to compile every aux file using bibtex seperately, which TexMaker fails to do 
% by default in spite of proper settings.

bibtex document.aux
bibtex sec.aux
bibtex priv.aux
bibtex enc.aux

pdflatex document.tex
pdflatex document.tex


```
The final PDF output is here.



