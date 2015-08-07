---
layout: default
---

The _PROIEL treebanking framework_ consists of an annotation scheme, an XML-based interchange format and a set of tools for creating and manipulating treebanks.

The two main tools of the framework are 

1. `proiel-cli`, a library for manipulating existing PROIEL treebanks using the XML-based interchange format, and
2. [`proiel-webapp`](https://github.com/mlj/proiel-webapp), a web-based tool for creating and annotating PROIEL treebanks

If you want to use an existing PROIEL treebank that you have obtained, you will only need `proiel-cli`.

If you want to create a new PROIEL treebank and set up your own infrastructure for this, you will also need [`proiel-webapp`](https://github.com/mlj/proiel-webapp). See the [`proiel-webapp` wiki](https://github.com/mlj/proiel-webapp/wiki) for installation instructions and advice on which version to use.

We also provide a number of _experimental_ tools which are still under development:

* `proiel-query`, a query tool using the TigerQuery formalism
* [`proiel-api`](https://github.com/mlj/proiel-api), a JSON API for building applications on top of proiel-webapp instances
* `proiel-lint`, a validation tool
* `proiel-viewer`, a read-only front end for existing treebanks

The PROIEL treebanking framework is currently used by the following treebanking projects:

* [The Tromsø Old Russian and OCS Treebank (TOROT)](https://nestor.uit.no/)
* [The PROIEL Treebank](http://proiel.github.io)
* [Information Structure and Word Order Change in Germanic and Romance Languages (ISWOC)](http://foni.uio.no:3000)
* [Menotec](http://foni.uio.no:3000)