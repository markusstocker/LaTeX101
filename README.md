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

The [lecture](lecture/stocker17latex101-lecture.pdf) introduces students to LaTeX by explaining what LaTeX is and what its pros and cons are compared to commonly used word processing software, primarily Microsoft Word. The lecture surveys key elements of a typical scientific article, such as figures and references, and explains how to write them in LaTeX. We discuss BibTeX and reference management, styling scientific articles with journal LaTeX templates, LaTeX support for writing slides and posters, as well as approaches for collaborative writing with LaTeX.

## Hands-on

The hands-on part of the course consists of pratical exercises in writing scientific documents using LaTeX. The course material includes a [default article](article/default-article.pdf) but we encourage students to bring along an article they co-authored. The course assumes that you have installed [TeX Live](https://www.tug.org/texlive/) ([MiKTeX](https://miktex.org/) or [MacTeX](https://www.tug.org/mactex/)), [TeXstudio](http://www.texstudio.org/), [JabRef](http://www.jabref.org/), and [Git](https://git-scm.com/). The hands-on part is structured in four sub parts:

[Hands-on I](#hands-on-i): Basic elements of an article  
[Hands-on II](#hands-on-ii): Advanced elements of an article  
[Hands-on III](#hands-on-iii): Slides and poster  
[Hands-on IV](#hands-on-iv): Collaborative writing  

### Hands-on I

In this first hands-on, we look at the basic elements of an article. We will write our article using the Elsevier `elsarticle` document class. You can download the [elsarticle package](http://www.ctan.org/tex-archive/macros/latex/contrib/elsarticle) to your working directory from the [CTAN Comprehensive TeX Archive Network](http://ctan.org), as [zip archive](http://mirrors.ctan.org/macros/latex/contrib/elsarticle.zip). Unpack the zip archive, change to the `elsarticle` sub directory, and execute the following command

```
latex elsarticle.ins
```

This will create the required [`elsarticle.cls`](article/elsarticle.cls) and [`elsarticle-harv.bst`](article/elsarticle-harv.bst) files. Copy the `elsarticle.cls`, `elsarticle-harv.bst`, and `elsarticle-template-harv.tex` files into your working directory. The latter file serves as the template: rename the template file to something that better reflects your article.

*Hint: If you have problems with this step, follow the links to the `.cls` and `.bst` files and you will be able to download copies.*

You are now ready to start writing your own article. The following description uses our [default article](article/default-article.pdf).

Open the `.tex` file in TeXstudio as well as the default article (PDF). In TeXstudio, select `Build & View` (green double arrow) to build the document. You will see a PDF output on the right hand side in TeXstudio. The aim now is to re-create the default article in LaTeX by writing the `.tex` file.

As you can see in the footnote, we plan to submit the article to the Elsevier [SoftwareX](https://www.journals.elsevier.com/softwarex/) journal. Find the corresponding LaTeX command to specify the journal name and change it to *SoftwareX* (or your favorite journal). Build the document to see the change in PDF.

The default article has a title and three authors. Locate the LaTeX command to specify the title and add the title. At any time you can build the document to check if the change is reflected in the PDF output as intended. The Elsevier template provides documentation how to add author names and corresponding affiliations. Add the authors Kaiser, Doe, and Kaisaniemi with the corresponding affiliations. Look for documentation for the `\ead` command to add email addresses.

*Hint: Make use of the optional labels to link authors to addresses.*

Scientific articles typically include an abstract as well as keywords. It is generally easy to set these in LaTeX and many journal templates provide guidance. Extend your template with abstract and keywords.

*Hint: Make sure to use the command to separate keywords as suggested in the template.*

Build your document and see how you are progressing nicely.

Next, we create the structure of the article, namely sections for Introduction, Case Study, Results, and Acknowledgements. Note that Acknowledgements is not numbered. You can achieve this with the command `\section*` (note the asterisk).

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

In this second hands-on, we look at the remaining more advanced elements of the article, in particular mathematical formulae, tables, figures, citations and references.

In the previous hands-on we have already made use of the inline math mode, `$ ...$`. This is practical for simple and short mathematical expresions. For more complex expressions, we use the `displaymath` environment

```
\begin{displaymath}
...
\end{displaymath}
```

The article includes a mathematical expression in such an environment. Writing such expressions in, LaTeX can be confusing at first, but the result is consistently great. Our expression includes the commands `\lim`, `\to` and `\frac`. Try it out!

*Hint: The template is as follows, \lim_{...} \frac{...}{...}*

Tables are important elements of scientific articles. In LaTeX, they can also be rather confusing at first. Tables live in the `table` environment, which encapsulates the table itself, a caption, typically a label and possibly other commands. For the table itself we use the `tabular` environment. Thus, the basic structure is as follows:

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

For Figure 1 you can use the file [load-performance-plot.pdf](article/load-performance-plot.pdf) and for Figure 2 the file [query-performance-plot.pdf](article/query-performance-plot.pdf). Download these files to your working directory and add them instead of <filename>, respectively. 

An `includegraphics` option you'll often use is `scale`. It accepts a number used as scaling factor. Typically the number will be above zero and below 1. Try, for instance, `scale=0.6`. Also, try to comment the command `\centering` to see the effect.

In Section 3, we refer to Table 1, Figure 1, and Figure 2. Such references are easily set using the `\ref{<label>}` command, whereby <label> refers to the name given in the corresponding `\label{...}`, of tables and figures. The same is true for sections: Try it out in Section 1 that refers to Section 2. Where to you put the section label?

*Hint: The `\label` command follows right after the `\section` command.

References are a crucial element of scientific articles and it is important to know how to handle them in LaTeX. Fortunately, it isn't difficult. Bibliographies are best loaded from external `.bib` files using the `\bibliography{<filename>}` command. The Elsevier template provides instructions. In fact, you can have one bibliography and include the file in all your LaTeX articles: LaTeX will include only those you cite in the particular article.

We provide a [bibliography file](article/bibliography.bib) to include in your working directory. You can include it in your LaTeX article with the following command

```
\bibliography{bibliography}
```

*Hint: The Elsevier template already includes the command. It is however commented. You need to uncomment the `\bibliographystyle` and `\bibliography` commands. Furthermore, you need to comment the `\begin{thebibliography}` environment (including its content).*

In Section 1, we cite a number of articles. Here, we use the following commands `\citet{<key>}` or `\citep{<key>}` whereby <key> corresponds to the unique identification of the citation in your bibliography. Open the `bibliography.bib` file in TeXstudio and search the `lefort12qb` key.

The difference between the `\citet` and `\citep` commands is for textual and parenthetical citations, respectively. In Section 1 you can try them both. These commands accept a comma separated list of keys.

The first paragraph in Section 1 uses a further command, namely `\citeauthor` for the second reference to Wang et al.:  Try it out and see the difference.

The Elsevier template suppresses the section title for the reference list. You can include it by adding the following command just after `\bibliographystyle`

```
\section*{\refname}
```

*Note: Recall the meaning of the asterix.*

Bibliographies should be managed using a tool. As we have seen in the lecture, publishers typically allows you to download BibTeX formatted citations. These can be easily included in your bibliography file using tools, just as JabRef. Try to open the `bibliography.bib` file in JabRef. Can you add a dummy citation and cite it in your article? Does it show up in the reference list?

As a final task for this hands-on, look at the preamble of the Elsevier template. It documents a number of available options to style your article, e.g. double line spacing for review or two-column for the layout of published articles. Try to comment the `\documentclass` commands and test a few options to see the effect. See also the effect of the `\linenumbers` command.

This demonstrates how easily it can be to completely change the layout of your article, using few options in a single command. Changing document class from `elsarticle` to one of another publisher may involve a bit more work in the preamble but little or nothing in the body. This is the beauty of separating content from layout.

### Hands-on III

In this third hands-on, we look at creating slides and a poster for our article.

There exist several document classes for creating slides. Here we will use `beamer`. The `.tex` file for the slides used to present our article at a conference will thus begin with 

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

Now, let's see how easy it is to take content from the article and create slides, including citations, tables, images.

For the Introduction slide, create a list with text citing some papers. You can take this from Section 1 in the article. You will need to do two things. First, include the bibliography in an own frame with title *References*

```
% \tiny
\bibliographystyle{plain} 
\bibliography{bibliography}
```

You will see why you need to uncomment the `\tiny` command. Next, add the following command to the preamble

```
\setbeamertemplate{bibliography item}{\insertbiblabel}
```

This will substitute an icon with a number. Now you are ready to cite work in your bibliography. Instead of using `\citet` and `\citep` as was the case in the article, here we use the `\cite{<key>}` command.

Create another frame and include some chemical formulae and quantities. Remember to include the corresponding packages.

Next, create a slide that includes the table and one that includes a figure. You may not need a caption and label. Try including the table and figure without the corresponding environments. Note that you still want to center these elements on your slides. For the image, it may make sense to increase the scale factor, say to 0.8.

*Hint: After building the document, try to zoom the slide with the image. Note that it does not pixelize as you zoom further. This is because we are including vector graphics.*

Now let's try to create a poster.

As for slides, there are [numerous templates](https://www.latextemplates.com/cat/conference-posters) that support you in writing a poster with LaTeX. Here, we will use the [Jacobs Landscape Poster](https://www.latextemplates.com/template/jacobs-landscape-poster).

First, [download](http://www.latextemplates.com/templates/conference_posters/1/conference_poster_1.zip) the zip archive and unpack it in your working directory. Open `main.tex` in TeXstudio and try to build the document. The template is well documented. Note that the template builds on `beamer`.

Next, try to edit the poster by setting title, author, and institute. You can add multiple authors and affiliations as follows

```
\author{AuthorA\inst{1} \and AuthorB\inst{2}
\institute{\inst{1} InstituteA \and \inst{2} InstituteB}
```

As you can see, the whole poster rests in a single `frame`. There are three main columns. The middle column is twice the size of the other two. The frame thus has the following main structure

```
\begin{frame}

\begin{columns}

\begin{column}{\onecolwid}
...
\end{column}

\begin{column}{\twocolwid}
...
\end{column}

\begin{column}{\onecolwid}
...
\end{column}

\end{columns}

\end{frame}
```

Try to place the content of your article into these columns. You may need to move around blocks in order to fit the poster.

### Hands-on IV

In this fourth hands-on, we look at collaborative writing with LaTeX. Specifically, we use [Overleaf](https://www.overleaf.com/) to edit our default article and test the possibility to work on the article collaboratively. Second, we demonstrate how [Git](https://git-scm.com/) can be used to work collaboratively on LaTeX documents.

For both services you will need to register. Overleaf supports a number of social logins to make sign up easier. I use ORCID. Once signed up/in, you can create new projects or upload your zip archived LaTeX project. Try uploading your LaTeX article.

Similarly to Google Docs, Overleaf allows you to share your document by adding collaborators. You can test this feature by inviting fellow students. Try to collaborate on changing the article. In particular, try to use the `changes` package to track changes you make. For this, you need to add the package to the preamble, add yourself and your collaborators as authors using the following command

```
\definechangesauthor[name={<your name>}, color=<blue,red,green,yellow>]{<your acronym>}
```

and then edit the text using the following commands, depending on your action

```
\deleted{...}
\replaced{...}{...}
\added[id=JD]{...}
```

Note what happens if you add the `final` option to `usepackage` in the preamble, as follows

```
\usepackage[final]{changes}
```

Git is another approach to work collaboratively on documents, including LaTeX articles, slides, posters. To use Git collaboratively, you need to [install Git](https://git-scm.com/downloads) on your computer and choose an online Git repository service. [GitHub](https://github.com/) is arguably the most popular. Unfortunately, GitHub is free only for public projects, meaning that you need a paid plan if you want to manage your LaTeX articles in private repositories. There are alternatives, including some that include private repositories in their free plan. [Bitbucket](https://bitbucket.org) is an example.

The course material is managed in a [GitHub repository](https://github.com/markusstocker/LaTeX101). In order to clone it into your working directory, you don't actually need an account. Try the following command:

```
git clone https://github.com/markusstocker/LaTeX101.git
```

This will clone the repository onto your computer. You obtain copies of all materials.

You can use Git to managed document versions in your local environment. Create a directory called `myarticle` and change the directory. Then execute the following commands

```
git init
touch myarticle.tex # Create a file
git add myarticle.tex
git commit -m "added"
```

This will create a Git repository and track your `.tex` file. Now, open `myarticle.tex` and type, e.g. the following

```
\documentclass{article}

\begin{document}

Hello world

\end{document}
```

You can create a PDF using the command

```
pdflatex myarticle
```

You can check which files changed since your last commit using 

```
git status
```

The file `myarticle.tex` was modified and a number of files are . If you want to track `myarticle.pdf`, use `git add myarticle.pdf` to track it. Then commit the changes with the following command

```
git add myarticle.tex
git commit -m "writing myarticle"
```

Next, make a change to `myarticle.tex` and then commit the change

```
git commit -a -m "a small change"
```

Now, let's assume tomorrow you are unhappy about the small change and you want to reset to the earlier version. With `git log` you can see the history. The following command will reset to the desired version

```
git reset --hard <commit>
```

You will see that the small change was indeed reset.

While this is a good approach to track your changes and make sure you can reset to earlier versions, it does not enable collaboration with others, including with yourself (e.g. on different devices). Furthermore, there is no remote clone of your repository, meaning there is no "backup". For this you need to push your local repository to a service such as GitHub or Bitbucket.

With your GitHub account, create a new repository called `myarticle`. GitHub will instruct you how you can push your existing repository to GitHub, e.g. using `HTTPS`

```
git remote add origin https://github.com/[username]/myarticle.git
git push -u origin master
```

That's it. Your repository is now on GitHub. Load the `https://github.com/[username]/myarticle` URL in your browser. If you happen to remove the `myarticle` directory on your local computer, or you like to work on your article from some other computer, you can simply clone the repository

```
git clone https://github.com/[username]/myarticle.git
```

If a co-author likes to contribute content to your article, they can fork the repository, make their changes, and then create a pull request. This is the mechanism for you to integrate changes and collaborate on your LaTeX article.

## Closing

Final questions and comments.




