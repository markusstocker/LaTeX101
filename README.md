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

For the hands-on part of the course, we will write a scientific manuscript using LaTeX. The course provides a [default manuscript](materials/manuscript/default-manuscript.pdf) but we encourage students to bring along a manuscript they co-authored. The course assumes that you have installed [TeX Live](https://www.tug.org/texlive/) ([MiKTeX](https://miktex.org/) or [MacTeX](https://www.tug.org/mactex/)), [TeXstudio](http://www.texstudio.org/), [JabRef](http://www.jabref.org/), and [Git](https://git-scm.com/). The hands-on part is structured in four sub parts:

[Hands-on I](#hands-on-i): Basic elements of a manuscript  
[Hands-on II](#hands-on-ii): Advanced elements of a manucript  
[Hands-on III](#hands-on-iii): Slides and poster  
[Hands-on IV](#hands-on-iv): Collaborative writing  

### Hands-on I

In this first hands-on, we will look at the basic elements of a manuscript. We will write our manuscript using the elsarticle document class. You can download the [elsarticle package](http://www.ctan.org/tex-archive/macros/latex/contrib/elsarticle) to your working directory from the [CTAN Comprehensive TeX Archive Network](http://ctan.org), as [zip archive](http://mirrors.ctan.org/macros/latex/contrib/elsarticle.zip). Unpack the zip archive, change to the `elsarticle` sub directory, and execute the following command

```
latex elsarticle.ins
```

This will create the required [`elsarticle.cls`](materials/manuscript/elsarticle.cls) and [`elsarticle-harv.bst`](materials/manuscript/elsarticle-harv.bst) files. Copy the `elsarticle.cls`, `elsarticle-harv.bst`, and `elsarticle-template-harv.tex` files into your working directory. The latter file serves as the template: rename the template file to something that better reflects your manuscript.

*Hint: If you have problems with this step, follow the links to the `.cls` and `.bst` files and you will be able to download copies.*

You are now ready to start writing your own manuscript. The following description uses our [default manuscript](materials/manuscript/default-manuscript.pdf).

Open the `.tex` file in TeXshop as well as the default manuscript (PDF). In TeXshop, select `Build & View` (green double arrow) to build the document. You will see a PDF output on the right hand side in TeXshop. The aim now is to re-create the default manuscript in LaTeX by writing the `.tex` file.

As you can see in the footnote, we plan to submit the manuscript to the Elsevier [SoftwareX](https://www.journals.elsevier.com/softwarex/) journal. Find the corresponding LaTeX command to specify the journal name and change it to *SoftwareX* (or your favorite journal). Build the document to see the change in PDF.

The default manuscript has a title and three authors. Locate the LaTeX command to specify the title and add the title. At any time you can build the document to check if the change is reflected in the PDF output as intended. The Elsevier template provides documentation how to add author names and corresponding affiliations. Add the authors Kaiser, Doe, and Kaisaniemi with the corresponding affiliations. Look for documentation for the `\ead` command to add email addresses.

*Hint: Make use of the optional labels to link authors to addresses.*

Scientific manuscripts typically include an abstract as well as keywords. It is generally easy to set these in LaTeX and many journal templates provide guidance. Extend your template with abstract and keywords.

*Hint: Make sure to use the command to separate keywords as suggested in the template.*

Build your document and see how you are progressing nicely.

Next, we create the structure of the manuscript, namely sections for Introduction, Case Study, Results, and Acknowledgements. Note that Acknowledgements is not numbered. You can achieve this with the command `\section*` (note the asterisk).

We can now start filling the sections. Let's start with introduction. It is just a few lines but includes variations for how to cite published literature, quoted text, and a reference to Section 2. We will look at the citations in the next hands-on session. Thus, for now just copy the text as it stands, e.g. "Wang et al. (2014)". However, let's get the quotes right as well as the reference to Section 2. Build your document to check if things look good.

Section 2 introduces some chemical molecules, footnotes, quantities and units, and mathematical notation. You'll need to include the packages `mhchem` and `siunitx` in the preamble of your LaTeX document by adding the following `\usepackage` commands:

```
\usepackage[version=3]{mhchem}
\usepackage{siunitx}
```

Recall that chemical molecules are written using the `\ce{...}` command. Thus, CO2 is written `\ce{CO2}`. Try the same for methane and water (vapour).

Next we have a footnote. It can be easily set following the period at the end of the corresponding sentence using hte `\footnote{...}` command. Note that the URL in the footnote is active. This can be achieved with the `\url{...}` command, which requires the command `\usepackage{url}` in the preamble.

For quantities with value and unit, we have seen the command `\SI{<value>}{<unit>}`. Try it out for 10 Hz. Rather than writing `Hz`, what could be the command for the unit Hertz? What may be the command for the unit minute?

The `siunitx` package also supports writing numbers using the `\num{...}` command. Note how the command formats the number `1604500` with spaces.

Next, the text speaks of a matrix of 18000 rows and 40 columns. We use the inline math mode to `$ ... $` to write this in LaTeX, using the `\times` command. Can you spot the difference if you use the `\num{...}` command for format, e.g., the number of rows?

Finally, we have two units. We can use the `siunitx` package and `\si{<unit>}` command. Micro mole per mole is `\si{\micro\mol\per\mol}`. What could be the command for milli?

Section 3 refers to a table, two figures, and mathematical formulae. We will look into those in the next hands-on. To conclude this hands-on, we highlight two commands used to format text, namely `\emph{...}` and `\texttt{...}`. Use them to emphasize the words `load` and `query` and to print in true type the words `FILTER` and `ORDER BY`, respectively.

### Hands-on II

In this second hands-on, we will look at the remaining more advanced elements of the manuscript, in particular mathematical formulae, tables, figures, citations and references.

In the previous hands-on we have already made use of the inline math mode, `$ ...$`. This is practical for simple and short mathematical expresions. For more complex expressions, we use the `displaymath` environment

```
\begin{displaymath}
...
\end{displaymath}
```

The manuscript includes a mathematical expression in such an environment. Writing such expressions in, LaTeX can be confusing at first, but the result is consistently great. Our expression includes the commands `\lim`, `\to` and `\frac`. Try it out!

*Hint: The template is as follows, \lim_{...} \frac{...}{...}*

Tables are important elements of scientific manuscripts. In LaTeX, they can also be rather confusing at first. Tables live in the `table` environment, which encapsulates the table itself, a caption, typically a label and possibly other commands. For the table itself we use the `tabular` environment. Thus, the basic structure is as follows:

```
\begin{table}
  \caption{...}
  \begin{tabular}{<column definition>}
  ...
  \end{tabular}
  \label{...}
\end{table}
```

Tables are typically centered, and this can be easily achieved with the `\centering` command within the `table` environment. As table captions are typically written above the table, the `\caption` command comes before the `tabular` environment.

Our table has four columns. Columns are defined in <column definition> by determining if column text is left/right aligned or centered and whether the columns are separated by a line (this is admittedly not the full story but it serves the purpose here). In our table, text alignment in the four columns is centered, right, right, right. Furthermore, we have lines separating each column. This is codified with the following sequence for <column definition>

```
|c|r|r|r|
```

whereby `c` stands for centered, `r` stands for right and the `|` sets lines between columns.

In the `\tabular` environment, we can now start writing the table. First, we have a line. Use the `\hline` command. Then we have a header with column names. Columns are separated by `&` and rows are ended by `\\` (newline). Try writing the table. Can you guess what happens if you change the <column definition> to `|crrr|`?

Figures are placed not unlike tables and are less complicated. Unless generated by LaTeX, they are loaded from files (image files as well as PDF). The images are thus included into LaTeX documents and remain distinct files. To include images, you need to first load the `graphicx` package in the preamble:

```
\usepackage{graphicx}
```

Figures live in the `figure` environment, are generally centered, have a caption and label - just like tables. The actual image is included using the `\includegraphics` command. The basic structure is thus as follows:

```
\begin{figure}
  \centering
  \includegraphics[<options>]{<filename>}
  \caption{...}
  \label{...}
\end{figure}
```

For Figure 1 you can use the file [load-performance-plot.pdf](materials/manuscript/load-performance-plot.pdf) and for Figure 2 the file [query-performance-plot.pdf](materials/manuscript/query-performance-plot.pdf). Download these files to your working directory and add them instead of <filename>, respectively. 

An `includegraphics` option you'll often use is `scale`. It accepts a number used as scaling factor. Typically the number will be above zero and below 1. Try, for instance, `scale=0.6`. Also, try to comment the command `\centering` to see the effect.

In Section 3, we refer to Table 1, Figure 1, and Figure 2. Such references are easily set using the `\ref{<label>}` command, whereby <label> refers to the name given in the corresponding `\label{...}`, of tables and figures. The same is true for sections: Try it out in Section 1 that refers to Section 2. Where to you put the section label?

*Hint: The `\label` command follows right after the `\section` command.

References are a crucial element of scientific manuscripts and it is important to know how to handle them in LaTeX. Fortunately, it isn't difficult. Bibliographies are best loaded from external `.bib` files using the `\bibliography{<filename>}` command. The Elsevier template provides instructions. In fact, you can have one bibliography and include the file in all your LaTeX manuscripts: LaTeX will include only those you cite in the particular manuscript.

We provide a [bibliography file](materials/manuscript/bibliography.bib) to include in your working directory. You can include it in your LaTeX manuscript with the following command

```
\bibliography{bibliography}
```

*Hint: The Elsevier template already includes the command. It is however commented. You need to uncomment the `\bibliographystyle` and `\bibliography` commands. Furthermore, you need to comment the `\begin{thebibliography}` environment (including its content).*

In Section 1, we cite a number of articles. Here, we use the following commands `\citet{<key>}` or `\citep{<key>}` whereby <key> corresponds to the unique identification of the citation in your bibliography. Open the `bibliography.bib` file in TeXshop and search the `lefort12qb` key.

The difference between the `\citet` and `\citep` commands is for textual and parenthetical citations, respectively. In Section 1 you can try them both. These commands accept a comma separated list of keys.

The first paragraph in Section 1 uses a further command, namely `\citeauthor` for the second reference to Wang et al.:  Try it out and see the difference.

The Elsevier template suppresses the section title for the reference list. You can include it by adding the following command just after `\bibliographystyle`

```
\section*{\refname}
```

*Note: Recall the meaning of the asterix.*

Bibliographies should be managed using a tool. As we have seen in the lecture, publishers typically allows you to download BibTeX formatted citations. These can be easily included in your bibliography file using tools, just as JabRef. Try to open the `bibliography.bib` file in JabRef. Can you add a dummy citation and cite it in your manuscript? Does it show up in the reference list?

As a final task for this hands-on, look at the preamble of the Elsevier template. It documents a number of available options to style your article, e.g. double line spacing for review or two-column for the layout of published articles. Try to comment the `\documentclass` commands and test a few options to see the effect. See also the effect of the `\linenumbers` command.

This demonstrates how easily it can be to completely change the layout of your manuscript, using few options in a single command. Changing document class from `elsarticle` to one of another publisher may involve a bit more work in the preamble but little or nothing in the body. This is the beauty of separating content from layout.

### Hands-on III

In this third hands-on, we will look at creating slides and a poster for our manuscript.

There exist several document classes for creating slides. Here we will use `beamer`. The `.tex` file for the slides used to present our manuscript at a conference will thus begin with 

```
\documentclass{beamer}
```

There are several theme, color and font schemes available. Take a moment to [browser through the gallery](http://deic.uab.es/~iblanes/beamer_gallery/). You can load theme, color and font using the following commands in the preamble:

```
\usetheme{...}
\usecolortheme{...}
\usefonttheme{...}
```

Presentations generally have a title, author, and date. Similarly to articles, you can set these in the preamble with the following commands:

```
\title{}
\author{}
\date{}
```

You can add several author names. Try to underline the presenting author. 

*Bonus: How can you add affiliation and email. Try to search for an answer on Google.*

For the date you can either write one out or try the command `\today`. The basics are now configured and you are ready to start with drafting your slides. A set of slides is just a document. Unsurprisingly, we thus start with

```
\begin{document}
```

Remember to end the document. The first slide should be a title slide with author and date as configured in the preamble. You can instruct LaTeX to create a title slide with the following command

```
\maketitle
```

Each following slide rests in a `frame` environment. The basic pattern of commands is as follows:

```
\begin{frame}
  \frametitle{Introduction}

  \begin{itemize}
  \item
  \end{itemize}

\end{frame}
```

Now, let's see how easy it is to take content from the manuscript and create slides, including citations, tables, images.

For the Introduction slide, create a list with text citing some papers. You can take this from Section 1 in the manuscript. You will need to do two things. First, include the bibliography in an own frame with title *References*

```
% \tiny
\bibliographystyle{plain} 
\bibliography{bibliography}
```

You will see why you need to uncomment the `\tiny` command. Next, add the following command to the preamble

```
\setbeamertemplate{bibliography item}{\insertbiblabel}
```

This will substitute an icon with a number. Now you are ready to cite work in your bibliography. Instead of using `\citet` and `\citep` as was the case in the manuscript, here we use the `\cite{<key>}` command.

Create another frame and include some chemical formulae and quantities. Remember to include the corresponding packages.

Next, create a slide that includes the table and one that includes a figure. You may not need a caption and label. Try including the table and figure without the corresponding environments. Note that you still want to center these elements on your slides. For the image, it may make sense to increase the scale factor, say to 0.8.

*Hint: After building the document, try to zoom the slide with the image. Note that it does not pixelize as you zoom further. This is because we are including vector graphics.*


### Hands-on IV


