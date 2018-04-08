---
layout: default
---

The PROIEL Treebank is a treebank of ancient Indo-European languages, including Latin and Ancient Greek. It uses a refined version of dependency grammar and is available under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International](https://creativecommons.org/licenses/by-nc-sa/4.0/). On this site you will find our official, versioned releases of the treebank and pointers to further information.

The PROIEL Treebank is one of three treebanks that use the same annotation system, follow the same principles and available under the same license. The PROIEL Treebank covers Ancient Greek and Latin, as well as the translations of the New Testament into Gothic, Classical Armenian and Old Church Slavonic. The [TOROT Treebank](http://torottreebank.github.io/) covers Old Church Slavonic, Old Russian and Middle Russian, while the [ISWOC Treebank](https://iswoc.github.io/) includes texts in Old English, Old French, Portuguese and Spanish. The complete collection currently has 928,185 tokens, all of which has been manually annotated with morphological and syntactic analyses. Parts of the treebank also have information-structure annotation and the New Testament texts include text alignment.

All the PROIEL-family treebanks can be browsed and queried using [INESS Search](http://clarino.uib.no/iness/treebanks). You can watch an introduction to using INESS with PROIEL on [YouTube](https://www.youtube.com/watch?v=Btk5UX-fsOY&feature=youtu.be&t=2240).

You can also try [Syntacticus](http://syntacticus.org), our experimental interface for browsing and searching the PROIEL Treebank and related treebanks. This interface is not yet ready for serious use, but it will be soon!

#### Downloads

Releases are hosted on [GitHub](https://github.com/proiel/proiel-treebank/), where you can also access [previous releases](https://github.com/proiel/proiel-treebank/releases).

<p style="text-align: center">
  <a class="button button-outline" href="https://github.com/proiel/proiel-treebank/releases/latest">
    <span class="icon">
      <i class="fa fa-download"></i>
    </span>
    <span>Download</span>
  </a>
</p>

#### Citation

If you use the treebank, please cite as:

<blockquote>
  <p>
    <tt>
      Dag T. T. Haug and Marius L. Jøhndal. 2008. '<a href="http://www.hf.uio.no/ifikk/english/research/projects/proiel/Activities/proiel/publications/marrakech.pdf">Creating a Parallel Treebank of the Old Indo-European Bible Translations</a>'. In Caroline Sporleder and Kiril Ribarov (eds.).  <em>Proceedings of the Second Workshop on Language Technology for Cultural Heritage Data (LaTeCH 2008) (2008)</em>, pp. 27-34.
    </tt>
  </p>
</blockquote>

See also the following articles for further details:

<blockquote>
  <p>
    <tt>
      Dag T. T. Haug, Marius L. Jøhndal, Hanne M. Eckhoff, Mari Johanne Hertzenberg and Angelika Müth. 2009. '<a href="http://www.atala.org/IMG/pdf/TAL-2009-50-2-01-Haug.pdf">Computational and Linguistic Issues in Designing a Syntactically Annotated Parallel Corpus of Indo-European Languages</a>'. <em>Traitement automatique des langues</em> 50 (2): 17-45.
    </tt>
  </p>

  <p>
    <tt>
      Dag T. T. Haug, Hanne M. Eckhoff, Marek Majer and Eirik Welo. 2009. '<a href="http://booksandjournals.brillonline.com/content/journals/10.1163/156658409x12529372103308">Breaking down and putting back together: analysis and synthesis of New Testament Greek</a>'. <em>Journal of Greek Linguistics</em> 9 (1): 56-92.
    </tt>
  </p>

  <p>
    <tt>
      Hanne Eckhoff, Kristin Bech, Gerlof Bouma, Kristine Eide, Dag Haug, Odd Einar Haugen and Marius Jøhndal. 2017. '<a href="https://link.springer.com/article/10.1007/s10579-017-9388-5">The PROIEL treebank family: a standard for early attestations of Indo-European languages</a>'. <em>Language Resources and Evaluation</em>.
    </tt>
  </p>
</blockquote>

#### Contents

The following texts are currently included in the PROIEL Treebank:

Text                                       | Language
-------------------------------------------|---------------------
The Greek New Testament                    | Ancient Greek
Herodotus, _Histories_                     | Ancient Greek
Sphrantzes, _Chronicles_                   | Ancient Greek
Jerome's Vulgate                           | Latin
Caesar, _The Gallic War_                   | Latin
Cicero, _De officiis_                      | Latin
Cicero, _Letters to Atticus_               | Latin
_Peregrinatio Aetheriae_                   | Latin
Palladius, _Opus agriculturae_             | Latin
The Armenian New Testament                 | Classical Armenian
The Gothic Bible                           | Gothic
Codex Marianus                             | Old Church Slavonic

Please see the data files in the release distribution for complete contributor details and editorial notes.

The treebank was started as part of the research project [Pragmatic Resources in Old Indo-European Languages](http://www.hf.uio.no/ifikk/english/research/projects/proiel/), which was financed by the Norwegian Research Council. It originally comprised the New Testament in Ancient Greek and its translations into Latin, Old Church Slavonic, Gothic and Classical Armenian. The treebank has since been expanded to include ancient Indo-European texts in general and has spawned the [TOROT](http://torottreebank.github.io/) and [ISWOC](https://iswoc.github.io/) treebanks, which are complementary to the PROIEL Treebank.

We are constantly expanding the treebank. The following texts are in the pipeline and will be included in an upcoming release:

<table>
  <tr>
    <th>Text</th>
    <th>Language</th>
  </tr>
  <tr>
    <td>Plautus, opera omnia</td>
    <td>Latin</td>
  </tr>
  <tr>
    <td>Terence, opera omnia</td>
    <td>Latin</td>
  </tr>
</table>

#### Annotation system

The morphosyntactic annotation scheme is described in the document [PROIEL Guidelines for Annotation](http://folk.uio.no/daghaug/syntactic_guidelines.pdf).

Our releases contain the treebank on our own [PROIEL XML format](https://proiel.github.io/handbook/developer/#the-proiel-xml-format). PROIEL XML is the authoritative format for PROIEL-style treebank and the only one that provides access to all the annotation we have, but for ease of use we also include the treebank as CoNLL-X and CoNLL-U files. We have [a command-line utility](https://github.com/proiel/proiel-cli) that can be used to convert PROIEL XML to various other formats (see the [documentation](https://proiel.github.io/handbook/developer/#manipulating-proiel-xml-treebank-files) for examples), including formats used for training taggers. For more complex tasks you can use our libraries for Ruby. See our [developer's pages](http://dev.syntacticus.org) for more information.

<!-- Ready-made conversion of the PROIEL treebank to Universal Dependencies  -->
