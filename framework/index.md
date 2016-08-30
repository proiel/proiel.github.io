---
layout: default
---

The _PROIEL treebanking framework_ consists of an [annotation
scheme](http://folk.uio.no/daghaug/syntactic_guidelines.pdf), an XML-based
[interchange
format](../handbook/developer/proielxml)
and a set of tools for creating and manipulating treebanks.

The three main tools of the framework are

1. [PROIEL Annotator](https://github.com/mlj/proiel-webapp), a web-based tool for creating and annotating PROIEL treebanks,
2. [PROIEL Reader](http://proiel.johndal.com), a web-based treebank browser, and
3. [PROIEL Library](https://github.com/proiel/proiel), a Ruby-based library for manipulating PROIEL treebanks, whose most frequently used functionality is exposed by a [command-line interface](https://github.com/proiel/proiel-cli).

If you want to use an existing PROIEL treebank that you have obtained, you will only need to install the PROIEL Library.

If you want to create a new PROIEL treebank and set up your own infrastructure
for this, you will need both PROIEL Annotator and PROIEL Reader. You should start
by reading the installation instructions in the [PROIEL Reader
wiki](https://github.com/mlj/proiel-webapp/wiki).

The PROIEL treebanking framework is currently used by the following treebanking projects:

* [The Tromsø Old Russian and OCS Treebank (TOROT)](http://torottreebank.github.io/)
* [The PROIEL Treebank](http://proiel.github.io/)
* [Information Structure and Word Order Change in Germanic and Romance Languages (ISWOC)](http://iswoc.github.io/)
* [Menotec](http://foni.uio.no:3000)
