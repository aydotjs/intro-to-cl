# Introduction to Computational Linguistics

This repo contains materials for *Introduction to Computational Linguistics*–a course given by [Aaron Steven White](http://aaronstevenwhite.io/) at the University of Rochester. 

## About the course

This course covers foundational concepts in computational linguistics. Major focus is placed on the use of formal languages as a tool for understanding natural language as well as on developing students' ability to implement foundational algorithms pertaining to those formal languages. Topics include basic formal language theory, finite state phonological and morphological parsing, and syntactic parsing for context free grammars and mildly context sensitive formalisms.

## Prerequisites

This course relies on concepts covered in an introductory linguistics course and an introductory programming course. With respect to the latter, it specifically assumes that you can competently write scripts that do non-trivial things and can work competently with Python's object-oriented programming facilities but maybe not develop a package on your own.

## About the instructor

Aaron Steven White is an Associate Professor of [Linguistics](http://www.sas.rochester.edu/lin/) and [Computer Science](https://www.cs.rochester.edu/) at the [University of Rochester](https://rochester.edu/), where he directs the [Formal and Computational Semantics lab](http://factslab.io/) (FACTS.lab). [His research](http://aaronstevenwhite.io/research) investigates the relationship between linguistic expressions and conceptual categories that undergird the human ability to convey information about possible past, present, and future configurations of things in the world. 

In addition to being a principal investigator on numerous federally funded grants and contracts, White is the recipient of [a National Science Foundation Faculty Early Career Development (CAREER) award](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2237175). His work has appeared in a variety linguistics, cognitive science, and natural language processing venues, including Semantics & Pragmatics, Glossa, Language Acquisition, Cognitive Science, Cognitive Psychology, Transactions of the Association for Computational Linguistics, and Empirical Methods in Natural Language Processing.

## Installation

The site itself is built using [Quarto](https://quarto.org/). The source files for this site are available on github at [`aaronstevenwhite/intro-to-cl`](https://github.com/aaronstevenwhite/intro-to-cl). You can obtain the files by cloning this repo.

```bash
git clone https://github.com/aaronstevenwhite/intro-to-cl.git
```

All further code on this page assumes that you are inside of this cloned repo.

```bash
cd intro-to-cl
```

### Installing Quarto and extensions

To build this site, you will need to [install Quarto](https://quarto.org/docs/get-started/) as well as its [`include-code-files`](https://github.com/quarto-ext/include-code-files) and [`line-highlight`](https://github.com/shafayetShafee/line-highlight) extensions.

```bash
quarto add quarto-ext/include-code-files
quarto add shafayetShafee/line-highlight
```

These extensions are mainly used for including and highlighting parts of external files.

### Building the Docker container

All pages that have executed code blocks are generated from jupyter notebooks, which were run within a [Docker](https://www.docker.com/) container constructed using the Dockerfile contained in this repo. 

```{.dockerfile include="Dockerfile"}
```

Assuming you have Docker installed, the image can be built using:

```bash
docker build --platform linux/amd64 -t intro-to-cl .
```

A container based on this image can then be constructed using:

```bash
docker run -it --rm -p 8888:8888 -v "${PWD}":/home/jovyan/work intro-to-cl
```

To access jupyter, simply copy the link provided when running this command. It should look something like this (though your access tokens will differ):

```bash
To access the server, open this file in a browser:
    file:///home/jovyan/.local/share/jupyter/runtime/jpserver-8-open.html
Or copy and paste one of these URLs:
    http://4738b6192fb0:8888/lab?token=8fc165776e7e99c98ec19883f750071a187e85a0a9253b81
    http://127.0.0.1:8888/lab?token=8fc165776e7e99c98ec19883f750071a187e85a0a9253b81
```

You can change the port that docker forwards to by changing the first `8888` in the `-p 8888:8888` option–e.g. to redirect port 10000 `-p 10000:8888`. Just remember to correspondingly change the port you attempt to access in your browser: so even though the message above has you accessing port 8888, that's the docker container's port 8888, which forwards to your machine's 10000.

## Acknowledgments

The development of these materials was supported by the University of Rochester and a National Science Foundation grant: *CAREER: Logical Form Induction* ([BCS/IIS-2237175](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2237175)).

## License <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a>

<span xmlns:dct="http://purl.org/dc/terms/" href="http://purl.org/dc/dcmitype/Text" property="dct:title" rel="dct:type">Introduction to Computational Linguistics</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://aaronstevenwhite.io" property="cc:attributionName" rel="cc:attributionURL">Aaron Steven White</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>. Based on a work at <a xmlns:dct="http://purl.org/dc/terms/" href="https://github.com/aaronstevenwhite/representation-learning-course" rel="dct:source">https://github.com/aaronstevenwhite/intro-to-cl</a>.