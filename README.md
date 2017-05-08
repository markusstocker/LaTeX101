# Introduction to writing with LaTeX

These materials were prepared for the [MARUM](http://www.marum.de) Basic Skills and Methods Course on writing with [LaTeX](http://www.latex-project.org/). The course was first held on May 12, 2017, and is structured in two parts: the first part consists of an introductory lecture and the second of a series of hands-on sessions. The schedule is as follows:

10.00 - 11.30 [Lecture](#lecture)  
11.30 - 12.30 Lunch  
12.30 - 13.15 [Hands-on I](#hands-on-i)  
13.15 - 13.30 Break  
13.30 - 14.15 [Hands-on II](#hands-on-ii)  
14.15 - 14.45 Coffee break  
14.45 - 15.30 [Hands-on III](#hands-on-iii)  
15.30 - 15.45 Break  
15.45 - 16.30 [Hands-on IV](#hands-on-iv)  
16.30 - 17.00 [Closing](#closing)

## Lecture

The [lecture](materials/lecture/stocker17latex101-lecture.pdf) introduces students to LaTeX by explaining what LaTeX is and what its pros and cons are compared to commonly used word processing software. The lecture surveys key elements of a typical scientific manuscript, such as figures and references, and explains how to write them in LaTeX. We will present BibTeX and reference management, styling scientific manuscripts with journal LaTeX templates, LaTeX support for writing slides and posters, as well as present approaches for collaborative writing of LaTeX documents.

## Hands-on

For the hands-on part of the course, we will write a scientific manuscript using LaTeX. The course provides a [default manuscript](materials/manuscript/default-manuscript.pdf) but we encourage students to bring along a manuscript they co-authored. The course assumes that you have installed [TeX Live](https://www.tug.org/texlive/) ([MiKTeX](https://miktex.org/) or [MacTeX](https://www.tug.org/mactex/)), [TeXstudio](http://www.texstudio.org/), and [Git](https://git-scm.com/). The hands-on part is structured in four sub parts:

[Hands-on I](#hands-on-i)  
[Hands-on II](#hands-on-ii)  
[Hands-on III](#hands-on-iii)  
[Hands-on IV](#hands-on-iv)  

### Hands-on I

We will write our manuscript using the elsarticle document class. You can [download](http://www.ctan.org/tex-archive/macros/latex/contrib/elsarticle) the elsarticle package to your working directory from the CTAN Comprehensive TeX Archive Network, as [zip archive](http://mirrors.ctan.org/macros/latex/contrib/elsarticle.zip). Specifically, you'll need the [elsarticle_template_harv_tex](http://mirrors.ctan.org/macros/latex/contrib/elsarticle/elsarticle-template-harv.tex) template.

Unpack the zip archive, change to the `elsarticle` sub directory, and execute the following command

```
latex elsarticle.ins
```

This will create the required [`elsarticle.cls`](materials/manuscript/elsarticle.cls) and [`elsarticle-harv.bst`](materials/manuscript/elsarticle-harv.bst) files. 

Hint: If you have problems with this step, follow the links to the cls and bst files and you will get copies.

Now copy the `elsarticle.cls`, `elsarticle-harv.bst`, and `elsarticle-template-harv.tex` files into your working directory. 



### Hands-on II

### Hands-on III

### Hands-on IV


