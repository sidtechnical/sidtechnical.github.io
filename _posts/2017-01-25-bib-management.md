---
layout: post
title:  Bibliography management from multiple resources in LaTeX using multibib package.
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

\begin{document}

\end{document}
```

Now, I have four bibliography files as follows:

* ```bibliography.bib``` which I intend to use it as the genric bibiliography file. It means, I can just cite the content within this file strightaway using ```\cite{<xxx>}``` and it appears in the end of the output PDF.
* security.bib, privacy.bib and encryption.bib which I intend to cite them in different section so that the citations from these files are displayed right after the section, rather than appearin in the end of the PDF document.

Contents of these .bib files are as follows:

``` 
%bibliography.bib

@article{schloss2009introducing,
  title={Introducing mothur: open-source, platform-independent, community-supported software for describing and comparing microbial communities},
  author={Schloss, Patrick D and Westcott, Sarah L and Ryabin, Thomas and Hall, Justine R and Hartmann, Martin and Hollister, Emily B and Lesniewski, Ryan A and Oakley, Brian B and Parks, Donovan H and Robinson, Courtney J and others},
  journal={Applied and environmental microbiology},
  volume={75},
  number={23},
  pages={7537--7541},
  year={2009},
  publisher={Am Soc Microbiol}
}

@article{casti1994complexification,
  title={Complexification explaining a paradoxical world through the science of surprise},
  author={Casti, John L},
  year={1994}
}


```

``` 
%security.bib

@inproceedings{kandukuri2009cloud,
  title={Cloud security issues},
  author={Kandukuri, Balachandra Reddy and Rakshit, Atanu and others},
  booktitle={Services Computing, 2009. SCC'09. IEEE International Conference on},
  pages={517--520},
  year={2009},
  organization={IEEE}
}

@inproceedings{sabahi2011cloud,
  title={Cloud computing security threats and responses},
  author={Sabahi, Farzad},
  booktitle={Communication Software and Networks (ICCSN), 2011 IEEE 3rd International Conference on},
  pages={245--249},
  year={2011},
  organization={IEEE}
}

```

``` 
%privacy.bib

@article{westin1968privacy,
  title={Privacy and freedom},
  author={Westin, Alan F},
  journal={Washington and Lee Law Review},
  volume={25},
  number={1},
  pages={166},
  year={1968}
}


@inproceedings{agrawal2000privacy,
  title={Privacy-preserving data mining},
  author={Agrawal, Rakesh and Srikant, Ramakrishnan},
  booktitle={ACM Sigmod Record},
  volume={29},
  number={2},
  pages={439--450},
  year={2000},
  organization={ACM}
}

```

``` 
%encryption.bib

@inproceedings{boneh2001identity,
  title={Identity-based encryption from the Weil pairing},
  author={Boneh, Dan and Franklin, Matt},
  booktitle={Annual International Cryptology Conference},
  pages={213--229},
  year={2001},
  organization={Springer}
}


@article{needham1978using,
  title={Using encryption for authentication in large networks of computers},
  author={Needham, Roger M and Schroeder, Michael D},
  journal={Communications of the ACM},
  volume={21},
  number={12},
  pages={993--999},
  year={1978},
  publisher={ACM}
}


```

