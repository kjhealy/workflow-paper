---
title: The Plain Person's Guide to Plain Text Social Science
author:
- name: Kieran Healy
  affiliation: Duke University
  email: kjhealy@soc.duke.edu
date: February 2016
thanks: "This is an updated and expanded version of 'Choosing Your Workflow Applications' (2013). The main difference is an increased emphasis on Rmarkdown and `knitr` rather than Org-mode."
abstract: "As a beginning graduate student in the social sciences, what sort of software should you use to do your work? More importantly, what principles should guide your choices? This article offers some answers. The short version is: write using a good text editor (there are several to choose from); analyze quantitative data with R or Stata; minimize errors by storing your work in a simple format (plain text is best) and documenting it properly. Keep your projects in a version control system. Back everything up regularly and automatically. Don't get bogged down by gadgets, utilities or other accoutrements: they are there to help you do your work, but often waste your time by tempting you to tweak, update and generally futz with them. To help you get started, I briefly discuss the Emacs Starter Kit for the Social Sciences, a drop-in set of useful defaults designed to help you get started using Emacs (a powerful, free text-editor) for data analysis and writing. I also point to several alternatives."
crossrefYaml: "./pandoc-crossref-settings.yaml"
...


## Introduction

You can do productive, maintainable and reproducible work with all kinds of different software set-ups. This is the main reason I don't go around encouraging everyone to convert to the applications I use. (My rule is that I don't try to persuade anyone to switch if I can't commit to offering them technical support during and after their move.) So this discussion is not geared toward convincing you there is One True Way to organize things. I do think, however, that if you're in the early phase of your career as a graduate student in, say, Sociology, or Economics, or Political Science, you should give some thought to how you're going to organize and manage your work.[^1] This is so for two reasons. First, the transition to graduate school is a good time to make changes. Early on, there's less inertia and cost associated with switching things around than there will be later. Second, in the social sciences, text and data management skills are usually not taught to students explicitly. This means that you may end up adopting the practices of your advisor or mentor, continue to use what you are taught in your methods classes, or just copy whatever your peers are doing. Following these paths may lead you to an arrangement that you will be happy with. But maybe not. It's worth looking at the options.

Two remarks at the outset. First, because this discussion is aimed at beginning students, some readers may find much with which they are already familiar. Even so, some sections may still be of interest, as I have tried to keep the software references quite current. Second, although in what follows I advocate you take a look at several applications in particular, it's not really about the gadgets or utilities. The Zen of Organization is Not to be Found in Fancy Software. Nor shall the true path of Getting Things Done be revealed to you through the purchase of a nice [Moleskine Notebook](http://www.moleskineus.com/). Instead, it lies within---unfortunately.


## What's the Problem?

The problem is that doing scholarly work is intrinsically a mess. There's the annoying business of getting ideas and writing them down, of course, but also everything before, during, and around it: data analysis and all that comes with it, and the tedious but unavoidable machinery of scholarly papers---especially citations and references. There is a lot of keep track of, a lot to get right, and a lot to draw together at the time of writing. Academic papers are by no means the only form of writing subject to constraints of this sort. Consider [this sensible discussion](http://www.leancrew.com/all-this/2013/12/a-free-distraction/) by Dr Drang, a consulting engineer:

> I don’t write fiction, but I can imagine that a lot of fiction writing can be done without any reference materials whatsoever. Similarly, a lot of editorials and opinion pieces are remarkably fact-free; these also can spring directly from the writer’s head. But the type of writing I typically do—mostly for work, but also here—is loaded with facts. I am constantly referring to photographs, drawings, experimental test results, calculations, reports written by others, textbooks, journal articles, and so on. These are not distractions; they are essential to the writing process.
> 
> And it’s not just reference material. Quite often I need to make my own graphs and drawings to include in a report. Because the text and the graphics are all part of a coherent whole, I need to go back and forth between the two; the words inform the pictures and the pictures inform the words. This is not the Platonic ideal of a clean writing environment—a cup of coffee on an empty desk in a white room—that you see in videos for distraction-free editors.
>
> Some of the popularity of these editors is part of the backlash against multitasking, but people are confusing themselves with their computers. When I’m writing a report, that is my single task, and I bring to bear whatever tools are necessary to complete it. That my computer is multitasking by running many programs simultaneously isn’t a source of confusion or distraction, it’s the natural and efficient way for me to get my one task done.

A lot of academic writing is just like this. It is difficult to manage. It's even worse when you have collaborators and other contributors. So, what to do?

## The Office Model and the Engineering Model 

Let me make a crude distinction. There are "Office Type" solutions to this problem, and there are "Engineering Type" solutions. Don't get hung up on the distinction or the labels. Office solutions tend towards a cluster of tools where something like Microsoft Word is at the center of your work. A Word file or set of files is the most "real" thing in your project. Changes to your work are tracked inside that file or files. Citation and reference managers plug into them. The outputs of data analyses---tables, figures---get dropped into them or kept alongside them. The master document may be passed around from person to person or edited and updated in turn. The final output is exported from it, perhaps to PDF or to HTML, but maybe most often the final output just *is* the `.docx` file, cleaned up and with the track changes feature turned off.

In the Engineering model, meanwhile, plain text files are at the center of your work. The most "real" thing in your project will either be those files or, more likely, the Git repository that controls the project. Changes are tracked outside the files. Data analysis is managed in code that produces outputs in (ideally) a known and reproducible manner. Citation and reference management will likely also be done in plain text, as with a BibTeX `.bib` file. Final outputs are assembled from the plain text and turned to `.tex`, `.html`, or `.pdf` using some kind of typesetting or conversion tool. Very often, because of some unavoidable facts about the world, the final output of this kind of solution is also a `.docx` file.

This distinction is meant to capture a tendency in organization, not a rigid divide---still less a sort of personality. Obviously it is possible organize things on the Office model. (Indeed, it's the dominant way.) Applications like [Scrivener](http://www.literatureandlatte.com), meanwhile, combine elements of the two approaches. Scrivener embraces the "bittyness" of large writing projects in an effective way, and can spit out clean copy in a variety of formats. Scrivener is built for people writing lengthy fiction (or qualitative non-fiction) rather than anything with quantitative data analysis, so I have never used it extensively. Microsoft Word, meanwhile, still rules large swathes of the Humanities and the Social Sciences, and the production process of many publishers. So even if you prefer plain text for other reasons---especially in connection with project management and data analysis---the routine need or obligation to provide a Word document to someone is one of the main reasons to want to be able to easily convert things. HTML is a great lingua franca.

I'm more or less stuck in the Engineering model. But I also co-author with people who use the Office model. In those cases, it is easier for me to use their software than for them to use mine. We tend to collaborate using Google Docs or some other service that allows for simultaneously editing the master copy of a document. It's not ideal, but it is better than not collaborating. There is little to be gained from plain-text dogmatism in a `.docx` world.

When I write things by myself, or co-author with someone I can imperiously boss around, I want to do everything in plain text. In the past---e.g. for my dissertation, and my [book](http://www.amazon.com/Last-Best-Gifts-Altruism-Market/dp/0226322378)---I wrote everything in LaTeX. This led to me making some [custom LaTeX templates and style files](https://github.com/kjhealy/latex-custom-kjh) meant to produce good-looking PDFs. I try to write in Markdown rather than `.tex` format when I can, because in principle it is simpler and more easily convertible to many different kinds of output. I discuss these and more tools below.

## Two Revolutions in Computing

When talking to undergraduates or graduate students on this topic, and when teaching classes that use these tools, I increasingly run into the problem that it's hard to get started without backing up a bit first in order to talk about how the computer they are using works.

I think reason for this is the rise of the flat-screen, touch-based model of computing, most obviously on phones and then very secondarily on things like Apple's iPad or Microsoft's Surface tablet. Now, most people who need to write long documents (like papers or dissertations) or work in an involved way with data do not use a tablet as their primary device. But it does seem clear that some kind of touch-screen interaction is the future of computing for most people. Indeed, once you consider phones properly you realize it's the _present_ of computing for most people. While it is not strictly impossible, it remains very difficult to do your academic, social-science work on a device of this sort. This is likely to be the case for some time. The tools we have are not designed up for them.

That's not surprising. But I think there is an underappreciated tension here. Two ongoing computing revolutions are tending to pull in opposite directions. On one side, the mobile, cloud-centered, touch-screen, phone-or-tablet model has brought powerful computing to more people than ever before. This revolution is the one everyone is talking about, because it is happening on a huge scale and is where all the money is. In practice it puts single-purpose applications in the foreground and hides from the user both the workings of the operating system and (especially) the structure of the file system where items are stored and moved around.

On the other side, open-source tools for plain-text coding, data analysis, and writing are also better and more accessible than they have ever been. This has happened on a smaller scale than the first revolution, of course. But still, these tools really have revolutionized the availability and practice of data analysis and scientific computing generally. They continue to do so, too, as people work to make them better at everything from slurping up data on the web to presenting it there. These tools mostly work by gluing together separate, specialized widgets into a reproducible workflow. They are "bitty" or granular because the process of data analysis is that way as well. They do much less to hide the operating system layer---instead they often directly mesh with it---and they also presuppose a working knowledge of the file system underpinning the organization of the things the researcher is using or creating, from data files to code to figures and final papers.

The tension is that, increasingly, people who come in to the world of social science wanting to work with data tend to have little or no prior experience with text-based, command-line, file-system-dependent tools. In many cases, they do not have much experience multi-tasking in a windowing environment, either, at least in the sense of making applications work together in the service of a single goal.[^multit] To be clear, this is not something to blame users for, and neither is it something to complain about in misguided nostalgia for the command line. Rather, it is an aspect of how computer use is changing at a very large scale. The coding and data analysis tools we have are powerful and for the most part meant to allow research products to be opened up and inspected. But the way they work clearly runs against the current of everyday, end-use computing, which increasingly hides many implementation details and focuses on single-purpose tasks. Again, specialized tools are necessarily specialized. The net result for the social sciences in the short to medium term, I think, is that we will have a suite of powerful tools that enable an amazing variety of scientific activity, developed in the open and mostly available for free. But it will get harder to teach people how to use them. Organizations like [Data Carpentry](http://www.datacarpentry.org) have begun to address this challenge in a very positive way. I think we'll need a lot more in that vein in the future.

[^multit]: As opposed to multi-tasking in the less-interesting sense of trying to pay attention to a number of discrete tasks (writing, email, calendar, web-browsing), each controlled by a separate application.



## What Sort of Computer Should You Use?

The earliest choice you will face is buying your computer and deciding what operating system to run on it. The leading candidates are Microsoft Windows, Apple's Mac OS X, and some distribution of Linux. Each of these platforms has gone some of the way---in some cases a long way---toward remedying the defects stereotypically associated with it.

I would characterize the present state of things this way. Windows dominates the market in terms of sheer numbers. Many of its long-standing security, design, and usability problems have been ameliorated in recent years. Mac OS X runs only on computers made by Apple (the existence of "hackintoshes" notwithstanding). In the past, it was harder to make direct comparisons between Apple machines and Windows PCs, but this is no longer the case. In general, the more similarly kitted-out a PC is to an Apple machine, the more the price difference between the two goes away.[^2] However, Apple does not compete at all price-points in the market, so it will always be possible to configure a cheaper PC (with fewer features) than one Apple sells. For the same reason, it is also easier to find a PC configuration precisely tailored to some particular set of needs or preferences (e.g., with a better display but without some other feature or other) than may be available from Apple.

Because Apple now runs Intel-based hardware, installing and running Windows is easy, and even catered to by Mac OS's Boot Camp utility. Beyond installing OS X and Windows side-by-side, third-party virtualization software is available that allows you to run Windows or Linux as virtual machines within OS X. Thus, Apple hardware is the only setup where you can easily try out each of the main desktop operating systems.

Linux is stable, secure, and free. User-oriented distributions such as [Ubuntu](http://www.ubuntu.com/) are much better-integrated and well-organized than in the past. The user environment is friendlier now. Installing, upgrading and updating software---a key point of frustration and time-wasting in older Linux distributions---is also much better than it used to be, as Linux's package-management systems have matured. It remains true that Linux users are much more likely to be forced at some point to learn more than they might want to about the guts of their operating system.


## Just Make Sure You Know What You Did

For any kind of formal data analysis that leads to a scholarly paper, however you do it, there are some basic principles to adhere to. Perhaps the most important thing is to do your work in a way that leaves a coherent record of your actions. Instead of doing a bit of statistical work and then just keeping the resulting table of results or graphic that you produced, for instance, write down what you did as a documented piece of code. Rather than figuring out but not recording a solution to a problem you might have again, write down the answer as an explicit procedure. Instead of copying out some archival material without much context, file the source properly, or at least a precise reference to it.

Why should you bother to do any of this? Because when you inevitably return to your table or figure or quotation nine months down the line, your future self will have been saved hours spent wondering what it was you thought you were doing and where you got that result from.

A second principle is that a document, file or folder should always be able to tell you what it is. Beyond making your work reproducible, you will also need some method for organizing and documenting your draft papers, code, field notes, datasets, output files or whatever it is you're working with. In a world of easily searchable files, this may mean little more than keeping your work in plain text and giving it a descriptive name. It should generally *not* mean investing time creating some elaborate classification scheme or catalog that becomes an end in itself to maintain.

A third principle is that repetitive and error-prone processes should be automated if possible. (Software developers call this "DRY", or [Don't Repeat Yourself.](http://en.wikipedia.org/wiki/Don't_repeat_yourself)) This makes it easier to check for and correct mistakes. Rather than copying and pasting code over and over to do basically the same thing to different parts of your data, write a general function that can be called whenever it's needed. Instead of retyping and reformatting the bibliography for each of your papers as you send it out to a journal, use software that can manage this for you automatically.

There are many ways of implementing these principles. You could use Microsoft Word, Endnote and SPSS. Or Textpad and Stata. Or a pile of legal pads, a calculator, a pair of scissors and a box of file folders. Still, software applications are not all created equal, and some make it easier than others to do the Right Thing. For instance, it is *possible* to produce well-structured, easily-maintainable documents using Microsoft Word. But you have to use its styling and outlining features strictly and responsibly, and most people don't bother. You can maintain reproducible analyses in SPSS, but the application isn't set up to do this automatically or efficiently, nor does its design encourage good habits. So, it is probably a good idea to invest some time learning about the alternatives. Many of them are free to use or try out, and you are at a point in your career where you can afford to play with different setups without too much trouble.

The dissertation, book, or articles you write will generally consist of the main text, the results of data analysis (perhaps presented in tables or figures) and the scholarly apparatus of notes and references. Thus, as you put a paper or an entire dissertation together you will want to be able to easily *edit text*, *analyze data* and *minimize error*. In the next section I describe some applications and tools designed to let you do this easily. They fit together well (by design) and are all freely available for Windows, Linux and Mac OS X. They are not perfect, by any means---in fact, some of them can be awkward to learn. But graduate-level research and writing can also be awkward to learn. Specialized tasks need specialized tools and, unfortunately, although they are very good at what they do, these tools don't always go out of their way to be friendly.

### Edit Text

If you are going to be doing quantitative analysis of any kind then you should write using a good text editor. The same can be said, I'd argue, for working with any highly structured document subject to a lot of revision, such as a scholarly paper. Text editors are different from word processors. Unlike applications such as Microsoft Word, text editors generally don't make a big effort to make what you write look like as though it is being written on a printed page.[^3] Instead, they focus on working with text efficiently and assisting you with visualizing the logical structure of what you're writing. If you are writing code to do some statistical analysis, for instance, then at a minimum a good editor will highlight keywords and operators in a way that makes the code more readable. Typically, it will also passively signal to you when you've done something wrong syntactically (such as forget a closing brace or semicolon or quotation mark), and [automagically](http://en.wiktionary.org/wiki/automagical) indent or tidy up your code as you write it. If you are writing a scholarly paper or a dissertation, a good text editor can make it easier to maintain control over the structure of your document, and help ensure that cross-references and other paraphernalia are correct. Just as the actual numbers are crunched by your stats program---not your text editor---the typesetting of your paper is handled by a specialized application, too. Perhaps more importantly, a text editor *manipulates plain text* as opposed to binary file formats like `.doc` or `.pdf`, and plain text is the easiest format to manage, control, back up, and come back to later with some other application.

Emacs is a text editor, in the same way the blue whale is a mammal. Emacs is very powerful, and can become almost a complete working environment in itself, should you so wish. (I don't really recommend it.) Combining Emacs with some other applications and add-ons (described below) allows you to manage writing and data-analysis effectively. The [Emacs Homepage](http://www.gnu.org/software/emacs/) has links to Windows and Linux versions. The two most easily available versions on the Mac are [GNU Emacs](http://emacsformacosx.com/) itself and [Aquamacs](http://aquamacs.org/). The former is the \`\`purest'' version of Emacs and does not implement many Mac conventions out of the box. The latter makes an effort to integrate Emacs with the Mac OS. I prefer GNU Emacs. For Windows users who would like to use Emacs, the developers maintain an [extensive FAQ](http://www.gnu.org/software/emacs/windows/faq.html) including information on where to download a copy and how to install it.

While very powerful and flexible, Emacs can be annoying. Indeed, to many people encountering it for the first time---especially those used to standard applications on Windows or Mac OS---its conventions seem bizarre and byzantine. As applications go, Emacs is quite ancient. The first version was written by Richard Stallman in the 1970s. Because it evolved in a much earlier era of computing (before the development of decent graphical displays, for instance, and window managers, and possibly also fire), it doesn't share many of the conventions of modern applications. Like most powerful text editors, Emacs offers many opportunities to waste your time learning its particular conventions, tweaking its settings, and generally customizing it. There are several good alternatives on each major platform, and I discuss some of them below.

Given that, you may be wondering why I mention it at all. Partly because it's the editor I used. Partly because it is available on every platform you're likely to use. And partly becuase it is very, *very* good at doing what I want it to do. In a modern computing environment there are many good reasons to use something like RStudio, or TextMate, or Sublime Text instead of Emacs (I return to these alternatives below), and you will do fine if you prefer those instead. A recent, good case for Emacs comes from [rekado](http://elephly.net/posts/2016-02-14-ilovefs-emacs.html), who writes:

> Just like a browser is used by many as a platform for running applications operating on some HTML document, Emacs is a platform for anything that can “reasonably” (this is up for interpretation) be mapped to buffers of text. Applications in browsers are written in JavaScript, applications in Emacs are written in EmacsLisp (also called “elisp”). ... A text buffer in Emacs could hold the trail of a shell session (`shell-mode`), an email (`message-mode`), a TODO list (`org-mode`), a directory listing (`dired`), a text file on disk, a chat session (`ERC`), a web page (`eww`), the output produced by an external command, etc. Just like a modern web browser represents an environment in which a programming language can be used to manipulate and interact with HTML documents, Emacs is an environment for text buffers with a language that can be used to manipulate and interact with text buffers. If you have used your web browser (or have observed someone use their web browser) to play games, listen to music, watch videos, read and compose email, edit text (e.g. by contributing to the Wikipedia), chat with friends (or chat about foes), read documentation, installed an extension—well, then the notion of a generic tool as a platform should not be a foreign concept to you. Emacs can be understood as such a generic tool providing a text interface (one of which may be a file editor).


### Analyze Data and Present Results

You will probably be doing some---perhaps a great deal---of quantitative data analysis. R is an environment for statistical computing. It's exceptionally well-supported, continually improving, and has a very active expert-user community who have produced many add-on packages. R has the ability to produce sophisticated and high-quality statistical graphics. The documentation that comes with the software is complete, if somewhat terse, but there are a large number of excellent reference and teaching texts that illustrate its use. These include @dalgaard02introdstatisr, @venables02moderappliedstatissplus, @maindonald03dataanalygraphusingr, @fox02rspluscompanappliedregres, @frank01regresmodelstrat, and @gelmanhill07:dataanalysis. Although it is a command-line tool at its core, it has a good graphical interface as well. You can download it from [The R Project Homepage](http://www.r-project.org/).

R can be used directly within Emacs by way of a package called ESS (for "Emacs Speaks Statistics"). As shown in @fig:ess, it allows you to work with your code in one Emacs frame and a live R session in another right beside it. Because everything is inside Emacs, it is easy to do things like send a chunk of your code over to R using a keystroke. This is a very efficient way of doing interactive data analysis while building up code you can use again in future.

![An R session running inside Emacs using ESS. The R code file is on the
left, and R itself is running on the right. You write in the left-hand
pane and use a keyboard shortcut to send bits of code over to the
right-hand pane, where they are executed by
R.](figures/ess-r-emacs.png){#fig:ess}

You'll present your results in papers, but also in talks where you will likely use some kind of presentation software. Microsoft's PowerPoint is the most common application, but there are better ones. If you wish, you can use LaTeX, too, creating slides with the [Beamer document class](http://latex-beamer.sourceforge.net/) and displaying them as full-screen PDFs. Or you can do the same thing in Rmarkdown (more on that momentarily), and make either PDF or nice HTML-based presentations. The latter can be viewed easily in web browsers. Alternatively, on Mac OS X Apple's [Keynote](http://www.apple.com/iwork/keynote/) is very good.[^4]

### Minimize Error

We have already seen how the right set of tools can save you time by automatically highlighting the syntax of your code, ensuring everything you cite ends up in your bibliography, picking out mistakes in your markup, and providing templates for commonly-used methods or functions. Your time is saved twice over: you don't repeat yourself, and you make fewer errors you'd otherwise have to fix. When it comes to managing ongoing projects, minimizing error means addressing two related problems. The first is to find ways to further reduce the opportunity for errors to creep in without you noticing. This is especially important when it comes to coding and analyzing data. The second is to find a way to figure out, retrospectively, what it was you did to generate a particular result. These problems are obviously related, in that it's easy to make a retrospective assessment of well-documented and error-free work. As a practical matter, we want a convenient way to document work as we go, so that we can retrace our steps in order to reproduce our results. We'll also want to be able to smoothly recover from disaster when it befalls us.

Errors in data analysis often well up out of the gap that typically exists between the procedure used to produce a figure or table in a paper and the subsequent use of that output later. In the ordinary way of doing things, you have the code for your data analysis in one file, the output it produced in another, and the text of your paper in a third file. You do the analysis, collect the output and copy the relevant results into your paper, often manually reformatting them on the way. Each of these transitions introduces the opportunity for error. In particular, it is easy for a table of results to get detached from the sequence of steps that produced it. Almost everyone who has written a quantitative paper has been confronted with the problem of reading an old draft containing results or figures that need to be revisited or reproduced (as a result of peer-review, say) but which lack any information about the circumstances of their creation. Academic papers take a long time to get through the cycle of writing, review, revision, and publication, even when you're working hard the whole time. It is not uncommon to have to return to something you did two years previously in order to answer some question or other from a reviewer. You do not want to have to do everything over from scratch in order to get the right answer. I am not exaggerating when I say that, whatever the challenges of replicating the results of someone else's quantitative analysis, after a fairly short period of time authors themselves find it hard to replicate their *own* work. Computer Science people have a term of art for the inevitable process of decay that overtakes a project simply in virtue of its being left alone on the hard drive for six months or more: bit--rot.

### Reproducible Programming with RMarkdown and `knitr` ###

A first step toward closing this gap is to use [RMarkdown](http://rmarkdown.rstudio.com) and [knitr](http://yihui.name/knitr/) when doing quantitative analysis in R. [Markdown](http://en.wikipedia.org/wiki/Markdown) is a way of writing plain text that includes information about the formatting of your document. RMarkdown is a way to incorporate R code into this process. This approach is designed to integrate the plain-text documentation or writeup of a data analysis and its execution. You write the text of your paper (or, more often, your report documenting a data analysis) as normal. Whenever you want to run a model, produce a table or display a figure, rather than paste in the results of your work from elsewhere, you write down the R code that will produce the output you want. These \`\`chunks'' of code are distinguished from the regular text by a special delimiter at their beginning and end.

When you're ready, you `knit` the document. That is, you feed it to R, which processes the code chunks, and produces a finished version where the code chunks have been replaced by their output. This is now a nice markdown file that you can then turn into a PDF or HTML document. Conversely, if you just want to extract the code you've written from the surrounding text, then you "tangle" the file, which results in an `.R` file. It's pretty straightforward in practice.

The strength of this approach is that is makes it much easier to document your work properly. There is just one file for both the data analysis and the writeup. The output of the analysis is created on the fly, and the code to do it is embedded in the paper. If you need to do multiple but identical (or very similar) analyses of different bits of data, RMarkdown and `knitr` can make generating consistent and reliable reports much easier.

RMarkdown is one of several "literate programming" formats. The idea goes back to Donald Knuth, the pioneering theorist of computer science who developed the TeX typesetting system in his spare time. Although his focus was on documenting computer programs, in retrospect, Knuth anticipated many of the main ideas---and developed the initial tools---for reproducible scientific analysis.

[Org-mode](http://orgmode.org/) is an Emacs mode originally designed to make it easier to take notes, make outlines and manage to-do lists. Very much in the spirit of Emacs itself, its users have extended it so that it is capable of all kinds of other things, too, such as calendar management, time-tracking, and so on. One very powerful extension to org-mode is [Org-Babel](http://orgmode.org/worg/org-contrib/babel/), which is a generalized literate-programming framework for org-mode documents. It works like Rmarkdown, except that instead of writing your papers, reports, or documentation in Markdown and your code in R, you write text in Org-mode's own markup syntax and your code in any one of a large number of supported languages. Org-mode has very powerful export capabilities, so it can convert `.org` files to LaTeX, HTML, and many other formats quite easily. Examples of it in use can be seen at the [Org-babel website](http://orgmode.org/worg/org-contrib/babel/intro.html).

@fig:example-figure-r, for instance, could be generated on the fly from source-code blocks included in the `.Rmd` source for this article.

![Tea and Buscuits](figures/example-figure-1.pdf){#fig:example-figure-r}

Sometimes we will want to only show the results produced by the code---in this case, @fig:example-figure-r. But at other times we will want to display the code as well, as in @lst:r-example. 

```{#lst:r-example .r caption="R code snippet."}

library(ggplot2)
tea <- rnorm(100)
biscuits <- tea + rnorm(100,0,1.3)
qplot(tea, biscuits) + geom_smooth(method="lm") + 
scale_x_continuous(name="Tea") + 
scale_y_continuous(name="Biscuits") + theme_bw() 

```

`knitr` and RMarkdown make it easy to produce HTML output, too. This
makes for easy portability, conversion, and quick previewing while
editing.


### Use Revision Control

The task of documenting your work at the level of particular pieces of code or edits to paragraphs in individual files can become more involved over time, as projects grow and change. This can pose a challenge to the Literate Programming model. Besides, what if you are not doing statistical analysis at all, but still want to keep track of your work as it develops? The best thing to do is to institute some kind of version control system to keep a complete record of changes to a file, a folder, or a project. This can be used in conjunction with or independently of a documentation method like Sweave. A good version control system allows you to easily "rewind the tape" to earlier incarnations of your notes, drafts, papers and code, and lets you keep track of what's current without having to keep directories full of files with confusingly similar names like `Paper-1.txt`, `Paper-2.txt`, `Paper-conferenceversion.txt`, and so on.

In the social sciences and humanities, you are most likely to have come across the idea of version control by way of the \`\`Track Changes'' feature in Microsoft Word, which lets you see the edits you and your collaborators have made to a document. Think of true version control as a way to keep track of whole projects (not just individual documents) in a much better-organized, comprehensive, and transparent fashion. Modern version control systems such as [Subversion](http://subversion.tigris.org/), [Mercurial](http://www.selenic.com/mercurial/) and [Git](http://git.or.cz/) can, if needed, manage very large projects with many branches spread across multiple users. Git has become the *de facto* standard, and [GitHub](http://github.com) is a place where software developers and social scientists make their work available, and where you can contribute to ongoing projects or make public your own.

Modern version control requires getting used to some new concepts related to tracking your files, and learning how your version control system implements these concepts. Because of their power, these tools might seem like overkill for individual users. (Again, though, many people find Word's \`\`Track Changes'' feature indispensable once they begin using it.) But version control systems can be used quite straightforwardly in a basic fashion, and they increasingly come with front ends that can be easily integrated with your text editor.[^6] Moreover, you can meet these systems half way. [Dropbox](https://www.getdropbox.com/), for example, allows you to share files between different computers you own, or with collaborators or general public. But it also automatically version-controls the contents of these folders.

Revision control has significant benefits. A tool like Git combines the virtues of "track changes" with those of backups. Every repository is a complete, self-contained, cryptographically signed copy of the project with a full record of every recorded step in its development by all of its participants. This puts you in the habit of recording (or \`\`committing'') changes to a file or project as you work on it, and (briefly) documenting those changes as you go. It allows you to easily test out alternative lines of development by branching a project. It allows collaborators to work on a project at the same time without sending endless versions of the "master" copy back and forth via email, and it provides powerful tools that allow you to automatically merge or (when necessary) manually compare changes that you or others have made. Perhaps most importantly, it lets you revisit any stage of a project's development at will and reconstruct what it was you were doing. This can be tremendously useful whether you are writing code for a quantitative analysis, managing field notes, or writing a paper. While you will probably not need to control everything in this way (though some people do), I *strongly* suggest you consider managing at least the core set of text files that make up your project (e.g., the code that does the analysis and generates your tables and figures; the dataset itself; your notes and working papers, the chapters of your dissertation, etc). As time goes by you will generate a complete, annotated record of your actions that is also a backup of your project at every stage of its development. Services such as [GitHub](http://www.github.com) allow you to store public or (for a fee) private project repositories and so can be a way to back up work offsite as well as a platform for collaboration and documentation of your work.

### You don't need backups until you really, really need them

Regardless of whether you choose to use a formal revision control system, you should nevertheless have *some* kind of systematic method for keeping track of versions of your files. The task of backing up and synchronizing your files is related to the question of version control. Apple's Time Machine software, for example, backs up and versions your files, allowing you to step back to particular instances of the file you want. Other GUI-based file synchronization tools, such as [Dropbox](http://www.getdropbox.com) and [SugarSync](http://www.sugarsync.com/), are available across various platforms.

Even if you have no need for a synchronization application, you will still need to back up your work regularly. Because you are lazy and prone to magical thinking, you will not do this responsibly by yourself. This is why the most useful backup systems are the ones that require a minimum amount of work to set up and, once organized, back up everything automatically to an external (or remote) hard disk without you having to remember to do anything. On Macs, Apple's Time Machine software is built in to the operating system and makes backups very easy. On Linux, you can use [rsync](http://www.howtogeek.com/135533/how-to-use-rsync-to-backup-your-data-on-linux/) for backups. It is also worth looking into a secure, peer-to-peer, or offsite backup service like [Crashplan](http://www.crashplan.com/), or [Backblaze](http://www.backblaze.com/). Offsite backup means that in the event (unlikely, but not unheard of) that your computer *and* your local backups are stolen or destroyed, you will still have copies of your files.[^7] As Jamie Zawinski [has remarked](http://jwz.livejournal.com/801607.html), when it comes to losing your data \`\`The universe tends toward maximum irony. Don't push it.''

## Pulling it all Together

### What I want to do

I write sociology papers. Those papers cite books and articles. They often incorporate tables and figures created in [R](http://www.r-project.org). What I want to do is quickly turn a markdown file containing things like that into a properly formatted scholarly paper, without giving up any of the typographical quality or necessary scholarly apparatus (on the output side) or the convenience and convertibilty of markdown (on the input side). Most directly, I want to easily produce good-looking output from the same source in both HTML and PDF formats. And I want to do that with an absolute minimum of---ideally, *no*---post-processing of the output beyond that basic conversion step.

For transforming a mixture of R code and text into a markdown file, where the code chunks are replaced by their output, the tool of choice is Yihui Xie's [knitr](http://yihui.name/knitr/). For converting markdown to HTML and PDF, the best thing available is John MacFarlane's superb [Pandoc](http://johnmacfarlane.net/pandoc/). Pandoc can convert plain text in several markup formats into many output formats. Now, managing citations and references---including internal references, such as Figure, Table, and Equation numbering---has long been the Achilles heel of workflows built around "lightweight" markup formats like markdown. It was one of the places where LaTeX really worked much better, especially in conjunction with the editing facilities of something like [AucTeX](https://www.gnu.org/software/auctex/) and [RefTeX](http://www.gnu.org/software/auctex/reftex.html). Markdown is not designed to manage the machinery of academic papers or scholarly books. That isn't what it was made to do. This fact long kept me from being able to use it as extensively as I'd like. But thanks to John's (and other contibutors') continuing and stellar work on `pandoc`, the balance has begun to shift. There are still limitations to what markdown and`pandoc`can conveniently do. But being able to produce good HTML, LaTeX, and PDF in one step from the same source is a very attractive prospect.

![A plain-text document toolchain.](figures/workflow-wide.pdf){#fig:workflow-diagram}

### How I almost do it 

The document flow I want is shown in Figure @fig:workflow-diagram. I promise it is less insane than it appears. Describing this all at once will probably make it sound a little crazy. But, at bottom, there are just two separable pieces: `knitr` converts `.Rmd` files to `.md` files, and `pandoc` converts `.md` files to HTML, `.tex`, and PDFs. In both cases we use a few switches, templates and configuration files to do that nicely. You may have some or all of these tools installed anyway, and use them separately for different things. The thing is just to connect them a little. I assume you have you have a standard set of unix command-line tools available (e.g. Apple's developer tools), along with R, knitr, pandoc, and a TeX distribution. Note that the default set-ups for `knitr` and `pandoc`---the two key pieces of the process---will do most of what we want with no further tweaking. What I'm showing you here are just the relevant options to use and switches to set for these tools, together with some templates and document samples showing how nice-looking output can be produced in practice.

I write everything in Emacs, but as I hope is clear by now, that doesn't matter. Use whatever text editor you like and just learn the hell out of it. The [custom LaTeX style files](https://github.com/kjhealy/latex-custom-kjh) were originally put together to let me write nice-looking `.tex` files directly, but now they just do their work in the background. Pandoc will use them when it converts things to PDF. The heavy lifting is done by the [org-preamble-pdflatex.sty](https://github.com/kjhealy/latex-custom-kjh/tree/master/needs-org-mode) and [memoir-article-styles](https://github.com/kjhealy/latex-custom-kjh/tree/master/needs-memoir) files. If you install these files where LaTeX can find them---i.e., if you can compile a LaTeX document [based on this example](https://github.com/kjhealy/latex-custom-kjh/blob/master/templates/basic/article.tex)---then you are good to go. My [BibTeX master file](https://github.com/kjhealy/socbibs) is also available, but you will probably want to use your own, changing references to it in the templates as appropriate. Second, we have the custom pandoc stuff. [Here is the repository for that](https://github.com/kjhealy/pandoc-templates). Much of the material there is designed to go in the `~/.pandoc/` directory, which is where pandoc expects to find its configuration files.

Inside the pandoc-templates repository there's a [folder with some examples](https://github.com/kjhealy/pandoc-templates/tree/master/examples) of how these pieces go together. Let's start with a straightforward markdown file---no R code yet, so nothing above the `article.md` line in the picture above. The start of the sample `article-markdown.md` file is shown in @lst:yamlheader.

```{#lst:yamlheader .yaml caption="The top of a markdown file, showing the document metadata,"}
---
title: "A Pandoc Markdown Article Starter"
author:
- name: Kieran Healy
  affiliation: Duke University
  email: kjhealy@soc.duke.edu
- name: Joe Bloggs
  affiliation: University of North Carolina, Chapel Hill
  email: joebloggs@unc.edu
date: January 2014
abstract: "Lorem ipsum dolor sit amet"
bibliography: <!-- \bibliography{/Users/kjhealy/Documents/bibs/socbib-pandoc.bib} -->
...

# Introduction
Lorem ipsum dolor sit amet, consectetur adipisicing elit, 
sed do eiusmod tempor incididunt ut labore et dolore magna 
aliqua [@fourcade13classsituat]. Notice that citation.

# Theory
Lorem ipsum dolor sit amet, consectetur adipisicing 
elit, sed do eiusmod tempor incididunt ut labore et 
dolore magna aliqua [@fourcade13classsituat].

```

The bit at the top is YAML metadata, which pandoc understands. The HTML and latex templates [in the pandoc-templates repository](https://github.com/kjhealy/pandoc-templates/tree/master/templates) are set up to use this metadata properly. Pandoc will take care of the citations directly. There is more than one way to have pandoc manage citations, but here we just use the most self-contained route. (The `bibliography` line is not needed by pandoc at all: it is a hack to allow RefTeX to easily insert citations in the document while editing in Emacs.)

Simple documents can be contained in a single `.md` file. Documents including data analysis start life as `.Rmd` files which are then knitted into `.md` files and converted to PDF or HTML. I use a [Makefile](http://kbroman.org/minimal_make/) to control this process. Make is a command-line tool that manages the production of a file (the _target_) that has a number of _prerequisites_. In this case, the PDF or HTML file is the target, and the various figures and data tables are the prerequisites---if the code that produces them changes, the final document will change too. `Make` starts from the final document and works backwards along the chain of prerequisites, re-compiling or re-creating them as needed. It's a powerful tool. The [Makefile](https://github.com/kjhealy/pandoc-templates/blob/master/examples/Makefile) in the examples directory will convert any markdown files in the working directory to HTML, .tex, and PDF output. Just type `make` at the terminal to have it do everyhing, or e.g. `make html` to just produce the HTML file but not a PDF. If things go as they should, the HTML output from the example will look like Figure @fig:pandoc-html.

![HTML Output sample](figures/pandoc-template-html-output-sample.png){#fig:pandoc-html}

The PDF output, meanwhile, [can be viewed here](http://kieranhealy.org/files/misc/article-markdown.pdf). Both look quite nice. The relevant sections of the Makefile show the pandoc commands that generate the output files from the markdown input. The Makefile section for producing PDF output is shown in @lst:makefile.

```{#lst:makefile .bash caption="A piece of a Makefile"}

pandoc -r markdown+simple_tables+table_captions+yaml_metadata_block -s -S \ 
--latex-engine=pdflatex --template=$(PREFIX)/templates/latex.template \ 
--filter pandoc-citeproc \
--csl=$(PREFIX)/csl/$(CSL).csl --bibliography=$(BIB)

```

This contains some variables that are set at the top of the Makefile. The backslashes are there to indicate that the `pandoc` command is actually a single line of text, not several lines separated by the `<return>` key. On my computer, the command as actually executed is shown in @lst:makeoutput.


```{#lst:makeoutput .bash caption="What the Makefile executes"}

pandoc -r markdown+simple_tables+table_captions+yaml_metadata_block -s -S \ 
--latex-engine=pdflatex --template=/Users/kjhealy/.pandoc/templates/latex.template \ 
--filter pandoc-citeproc --csl=/Users/kjhealy/.pandoc/csl/apsr.csl \
--bibliography=/Users/kjhealy/Documents/bibs/socbib-pandoc.bib

```

Again, the backslashes are just for convenience. Your version would vary depending on the location of the templates and bibliography files. This is what you would run from the command line if you wanted to take a markdown file and use pdflatex to turn it in to a PDF, using the [APSR](https://www.apsanet.org/utils/journal.cfm?Journal=APSR) reference style, my latex template, and a `.bib` file called `socbib-pandoc.bib`.

The examples directory [also includes](https://github.com/kjhealy/pandoc-templates/blob/master/examples/article-knitr.Rmd) a sample `.Rmd` file. The code chunks in the file provide examples of how to generate tables and figures in the document. In particular they show some useful options that can be passed to knitr. [Consult the `knitr` project page](http://yihui.name/knitr/) for extensive documentation and many more examples. To produce output from the `article-knitr.Rmd` file, launch R in the working directory, load knitr, and process the file. You will also need the `ascii`, `memisc`, and `ggplot2` libraries to be available.

If things are working properly, then a markdown file called `article-knitr.md` will be produced, together with some graphics in the `figures/` subfolder and some working files in the `cache/` folder. We set things up in the `.Rmd` file so that `knitr` produces both PNG and PDF versions of whatever figures are generated by R. That prepares the way for easy conversion to HTML and LaTeX. Once the `article-knitr.md` file is produced, HTML, .tex, and PDF versions of it can be produced as before, by typing `make` at the command line. You can also run the pandoc commands manually, of course, or run pandoc from inside R via knitr's `pandoc()` helper function, or set your editor up to run `make` for you as needed, if it can do that.

### Using Marked

In everyday use, I find Brett Terpstra's application [Marked](http://marked2app.com) to be a very useful way of previewing text while writing. Marked shows you your Markdown files as HTML, updating the preview on the fly whenever changes are saved in the Markdown file. It can render ordinary Markdown by default, but it also supports `pandoc` as a custom processor. This means it can manage the various extra bells and whistles of scholarly formatting discussed so far. Essentially, you tell Marked run a `pandoc` command similar or identical the one shown above to generate its HTML previews. You do this in the "Advanced" tab of Marked's preferences. The "Path" field in the preferences dialog contains the full path to `pandoc`, and the "Args" field contains all the relevant command switches---in my case, the same as in the Makefile above.

When editing your markdown file in your favorite text editor, you point Marked at the file and get a live preview. You can add the [CSS files in the pandoc-templates repository](https://github.com/kjhealy/pandoc-templates/blob/master/marked/kultiad-serif.css) to the list of Custom CSS files Marked knows about, via the "Style" tab in the Preferences window. That way, Marked's preview will look the same as the HTML file that's produced.

The upshot of all of this is powerful editing using Emacs, [ESS](http://ess.r-project.org), R, and other tools; flexible conversion using pandoc; quick and easy previewing via HTML and Marked; and high-quality PDF typesetting at the same time (or whenever needed)---all generated directly from plain text and including almost all of what most of the scholarly papers I write need to include. While this may seem quite complex when laid out in this way, from my point of view the result is very straightforward. I just live in my text editor, the various scripts and settings do their work quietly, as they should, and I get the formatted output I want.


### An Emacs Starter Kit for the Social Sciences

A step-by-step guide to downloading and installing every piece of software I've mentioned so far is beyond the scope of this discussion. But let's say you take the plunge and download Emacs, a TeX distribution, R, and maybe even Git. Now what? If you're going to work in Emacs, there are a variety of tweaks and add-ons that are very helpful but not set by default. To make things a little easier, I maintain an [Emacs Starter Kit for the Social Sciences](http://kjhealy.github.com/emacs-starter-kit/). It's designed to smooth out Emacs' rough edges by giving you a drop-in collection of default settings, as well as automatically installing some important add-on packages. It will, I hope, help you skirt the abyss of Setting Things Up Forever.

## Do I Have to Use this Stuff?

### Pros and Cons

Writing documents in Markdown or RMarkdown using Emacs, R, and (behind the scenes) LaTeX and HTML has four main advantages. First, these formats and applications are all free. You can try them out without much in the way of monetary expense. (Your time may be a different matter, but although you don't believe me, you have more of that now than you will later.) Second, they are all open-source projects and are all available for Mac OS X, Linux and Windows. Portability is important, as is the long-term viability of the platform you choose to work with. If you change your computing system, your work can move with you easily. Third, they deliberately implement \`\`best practices'' in their default configurations. Writing documents in LaTeX encourages you to produce papers with a clear structure, and the output itself is of very high quality aesthetically. Similarly, by default R implements modern statistical methods in a way that discourages you from thinking about statistics in terms of canned solutions to standard problems. It also produces figures that accord with accepted standards of efficient and effective information design. And fourth, the applications are closely integrated. Everything (including version control systems) can work inside Emacs, and all of them talk to or can take advantage of the others.

None of these tools is perfect. They are powerful, but they can be tedious to learn. However, you don't have to start out using all of them at once, or learn everything about them right away---the only thing you *really* need to start doing immediately is keeping good backups. There are a number of ways to try them out in whole or in part. You could try writing something in Markdown first, using any text editor. You could begin using R with [RStudio](http://rstudio.com), which also makes writing in RMarkdown very easy.[^8] Revision control is more beneficial when implemented at the beginning of projects, and best of all when committing changes to a project becomes a habit of work. But it can be added at any time.

You are not condemned to use these applications forever, either. RMarkdown and (especially) Markdown or Org-mode documents can be converted into many other formats. Your text files are editable in any other text editor and on any other computer. Statistical code is by nature much less portable, but the openness of R means that it is not likely to become obsolete or inaccessible any time soon.

A disadvantage of these particular applications is that I'm in a minority with respect to other people in my field. This is less and less true in the case of R. Writing papers in RMarkdown or Markdown is less common. Most people use Microsoft Word to write papers, and if you're collaborating with people (people you can't boss around, I mean) this can be an issue. Similarly, journals and presses in my field often want Word files both at the point of submission and after acceptance, though again there are important exceptions. Converting files to a format Word understands can be tedious, but is now much easier than it used to be, thanks to `pandoc`.

### Alternatives Might Be Better

There are many other applications you might put at the center of your workflow, depending on need, personal preference, willingness to pay some money, or desire to work on a specific platform. For text editing, especially, there is a plethora of choices. On the Mac, quality editors include [BBEdit](http://www.barebones.com/products/bbedit/index.shtml) (beloved of many web developers, but with relatively little support for R beyond syntax highlighting), and [TextMate](http://macromates.com/) (shown in Figure @fig:tm). TextMate has strong support for LaTeX and good (meaning, ESS-like) support for R. Because it is a modern application written specifically for the Mac it can take advantage of features of OS X that Emacs cannot, and is much better integrated with the rest of the operating system. It also has good support for many of the ancillary applications discussed above, such as version control systems. After a delay somewhat reminiscent of the wait for the second coming of Jesus Christ, [TextMate 2](https://github.com/textmate/textmate) was released as an open-source project late in 2012, and now appears to be under active development again. On Linux, the standard alternative to Emacs is [vi](http://www.eng.hawaii.edu/Tutor/vi.html) or [Vim](http://www.vim.org/), but there are many others. For Windows there is [Textpad](http://www.textpad.com/), [WinEdt](http://www.winedt.com/), [UltraEdit](http://www.ultraedit.com/), and [NotePad++](http://notepad-plus.sourceforge.net/uk/site.htm) amongst many others. Most of these applications have strong support for LaTeX and some also have good support for statistics programming.

![An earlier version of this document being edited in
TextMate.](figures/textmate.png){#fig:tm}

[Sublime Text 3](http://www.sublimetext.com/) is a cross-platform text editor under active development, and with an increasingly large user base. Sublime Text is fast, fluid, and contains a powerful plugin system based on the [Python](http://python.org) programming language. Uniquely amongst alternatives to Emacs and ESS, includes a well-developed [REPL](http://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) that allows R to be run easily inside the editor.[^9] Sublime Text costs \$70.

Finally, for a different approach to working with R, you should consider [RStudio](http://www.rstudio.com). A screenshot is shown in Figure @fig:rstudio. Although it appears quite late in this discussion, it might well be your first choice. I use it when teaching. It is not a text editor but rather an "IDE", an integrated development environment---like a fully-windowed version of ESS, where figures and other output is automatically produced and displayed, and data and script files are managed via various windows and menus. It is available for Mac OS X, Windows, and Linux. It intergrates nicely with R's help files. It understands `knitr` and Git. It has full support for Rmarkdown and generates HTML, PDF, and other formats for you very easily. It also makes it easy to automatically publish workbooks online via its [RPubs platform](https://rpubs.com). It is the easiest way by far to get into using R, and provides a straightforward way to manage many of the tools already discussed here.

![RStudio running on Windows.](figures/rstudio.png){#fig:rstudio}

For statistical analysis in the social sciences, the main alternative to R is [Stata](http://www.stata.com/). Stata is not free, but like R it is versatile, powerful, extensible and available for all the main computing platforms. It has a large body of user-contributed software. In recent versions its graphics capabilities have improved a great deal. ESS can run Stata inside Emacs in the same way as it can do for R. Other editors can also be made to work with Stata: Jeremy Freese provides an [UltraEdit syntax highlighting file for Stata](http://www.jeremyfreese.com/#other%20research). There is a [Stata mode](http://www.winedt.org/Config/modes/Stata.php) for WinEdt. Friedrich Huebler has a [guide for integrating Stata with programming editors](http://mysite.verizon.net/huebler/2005/20050310_Stata_editor.html). Gabriel Rossman's blog [Code and Culture](http://codeandculture.wordpress.com/tag/stata/) has many examples of using Stata in the day-to-day business of analyzing sociological data.

Amongst social scientists, revision control is perhaps the least widely-used of the tools I have discussed. But I am convinced that it is the most important one over the long term. While tools like Git take a little getting used to both conceptually and in practice, the services they provide are extremely useful. It is already quite easy to use version control in conjunction with some of the text editors discussed above: Emacs and TextMate both have support for various DVCSs. There are full-featured clients like [Tower](https://www.git-tower.com) that allow you to administer git without having to use the command line. Taking a longer view, version control is likely to become more widely available through intermediary services or even as part of the basic functionality of operating systems.

## A Broader Perspective

It would be nice if all you needed to do your work was a box software of software tricks and shortcuts. But of course it's a bit more complicated than that. In order to get to the point where you can write a paper, you need to be organized enough to have read the right literature, maybe collected some data, and most importantly asked an interesting question in the first place. No amount of software is going to solve those problems for you. Too much concern with the details of your setup hinders your work. Indeed---and I speak from experience here---this concern is itself a kind self-imposed distraction that placates work-related anxiety in the short term while storing up more of it for later.[^10] On the hardware side, there's the absurd productivity counterpart to the hedonic treadmill, where for some reason it's hard to get through the to-do list even though the cafe you're at contains more computing power than was available to the Pentagon in 1965. On the software side, the besetting vice of productivity-enhancing software is the tendency to waste a lot of your time installing, updating, and generally obsessing about your productivity-enhancing software.[^11] Even more generally, efficient workflow habits are themselves just a means to the end of completing the projects you are really interested in, of making the things you want to make, of finding the answers to the questions that brought you to graduate school. The process of idea generation and project management can be run well, too, and perhaps even the business of choosing what the projects should be in the first place. But this is not the place---and I am not the person---to be giving advice about that.

All of which is just to reiterate that it's the principles of workflow management that are important. The software is just a means to an end. One of the [smartest, most productive people I've ever known](http://en.wikipedia.org/wiki/David_Kellogg_Lewis) spent half of his career writing on a typewriter and the other half on an [IBM Displaywriter](http://www-03.ibm.com/ibm/history/exhibits/pc/pc_8.html). His backup solution for having hopelessly outdated hardware was to keep a spare Displaywriter in a nearby closet, in case the first one broke. It never did.

[^1]: This may also be true if you are about to move from being a
    graduate student to starting as a faculty member, though perhaps the
    rationale is less compelling given the costs.

[^2]: Comparisons should still take account of remaining differences in
    hardware design quality, and of course the OS itself.
    I use Mac OS X these days, and I recommend you do, too. The
    discussion here reflects that preference to some extent. But the
    other options are also viable alternatives, and most of the tools I
    discuss are available on all three platforms. So I will not spend
    any more time trying to convince you one way or the other.

[^3]: For further argument about the advantages of text-editors over
    word processors see Allin Cottrell's polemic, \`\`[Word Processors:
    Stupid and Inefficient](http://www.ecn.wfu.edu/~cottrell/wp.html).''


[^4]: The actual business of *giving* talks based on your work is beyond
    the scope of this discussion. Suffice to say that there is plenty of
    good advice available via Google, and you should pay attention to
    it.

[^6]: Emacs comes with support for a variety of VCS systems built in.
    There's also a very good add-on package,
    [Magit](http://philjackson.github.com/magit/), devoted specifically
    to Git.

[^7]: I know of someone whose office building was hit by a tornado. She
    returned to find her files and computer sitting in a foot of water.
    You never know.

[^8]: If you already know Emacs, you should certainly try R using ESS
    instead of the R GUI, though.



[^9]: TextMate also has some support for this way of working, but it is
    conceived and accomplished a little differently.

[^10]: See [Merlin Mann](http://inboxzero.com/), amongst others, for
    more on this point.

[^11]: Mike Hall's brilliant "[Org-Mode in your Pocket is a GNU-Shaped
    Devil](http://mph.puddingbowl.org/2010/02/org-mode-in-your-pocket-is-a-gnu-shaped-devil/)"
    makes this point very well.

