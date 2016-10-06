---
layout: default
---

The PROIEL Treebank is a treebank of ancient Indo-European languages, including Latin and Ancient Greek. It uses a refined version of dependency grammar and is available under a [Creative Commons Attribution-NonCommercial-ShareAlike 3.0 License](http://creativecommons.org/licenses/by-nc-sa/3.0/us/). On this site you will find our official, versioned releases of the treebank and pointers to further information.

The PROIEL Treebank is one of three treebanks that use the same annotation system, follow the same principles and available under the same license. The PROIEL Treebank covers Ancient Greek and Latin, as well as the translations of the New Testament into Gothic, Armenian and Old Church Slavonic. The [TOROT Treebank](http://torottreebank.github.io/) covers Old Church Slavonic, Old Russian and Middle Russian, while the [ISWOC Treebank](https://iswoc.github.io/) includes texts in Old English, Old French, Portuguese and Spanish. The complete collection currently has 928,037 tokens, all of which has been manually annotated with morphological and syntactic analyses. Parts of the treebank also have information-structure annotation and the New Testament texts include text alignment.

## Downloads

Releases are hosted on [GitHub](https://github.com/proiel/proiel-treebank/), where you can also access [previous releases](https://github.com/proiel/proiel-treebank/releases).

<p style="text-align: center">
  <a class="button gray" href="https://github.com/proiel/proiel-treebank/releases/latest"><i class="icon-download-alt"></i> Download current version</a>
</p>

If you use the treebank, please cite as:
<div class="citation">
  Dag T. T. Haug and Marius L. Jøhndal. 2008. '<a href="http://www.hf.uio.no/ifikk/english/research/projects/proiel/Activities/proiel/publications/marrakech.pdf">Creating a Parallel Treebank of the Old Indo-European Bible Translations</a>'. In Caroline Sporleder and Kiril Ribarov (eds.).  <em>Proceedings of the Second Workshop on Language Technology for Cultural Heritage Data (LaTeCH 2008) (2008)</em>, pp. 27-34.
</div>

See also the following articles for further details:

<div class="citation">
  Dag T. T. Haug, Marius L. Jøhndal, Hanne M. Eckhoff, Mari Johanne Hertzenberg and Angelika Müth. 2009. '<a href="http://www.atala.org/IMG/pdf/TAL-2009-50-2-01-Haug.pdf">Computational and Linguistic Issues in Designing a Syntactically Annotated Parallel Corpus of Indo-European Languages</a>'. <em>Traitement automatique des langues</em> 50 (2): 17-45.
</div>

<div class="citation">
  Dag T. T. Haug, Hanne M. Eckhoff, Marek Majer and Eirik Welo. 2009. '<a href="http://booksandjournals.brillonline.com/content/journals/10.1163/156658409x12529372103308">Breaking down and putting back together: analysis and synthesis of New Testament Greek</a>'. <em>Journal of Greek Linguistics</em> 9 (1): 56-92.
</div>

## Contents

The following texts are currently included in the PROIEL Treebank:

<table>
  <tr>
    <th>Text</th>
    <th>Language</th>
  </tr>
  <tr>
    <td>The Greek New Testament</td>
    <td>Ancient Greek</td>
  </tr>
  <tr>
    <td>Herodotus, <i>Histories</i></td>
    <td>Ancient Greek</td>
  </tr>
  <tr>
    <td>Sphrantzes, <i>Chronicles</i></td>
    <td>Ancient Greek</td>
  </tr>
  <tr>
    <td>Jerome's Vulgate</td>
    <td>Latin</td>
  </tr>
  <tr>
    <td>Caesar, <i>The Gallic War</i></td>
    <td>Latin</td>
  </tr>
  <tr>
    <td>Cicero, <i>Letters to Atticus</i></td>
    <td>Latin</td>
  </tr>
  <tr>
    <td><i>Peregrinatio Aetheriae</i></td>
    <td>Latin</td>
  </tr>
  <tr>
    <td>The Armenian New Testament</td>
    <td>Classical Armenian</td>
  </tr>
  <tr>
    <td>The Gothic Bible</td>
    <td>Gothic</td>
  </tr>
  <tr>
    <td>Codex Marianus</td>
    <td>Old Church Slavonic</td>
  </tr>
</table>

Please see the data files in the release distribution for complete contributor details and editorial notes.

The treebank was started as part of the research project [Pragmatic Resources in Old Indo-European Languages](http://www.hf.uio.no/ifikk/english/research/projects/proiel/), which was financed by the Norwegian Research Council. It originally comprised the New Testament in Ancient Greek and its translations into Latin, Old Church Slavonic, Gothic and Armenian. The treebank has since been expanded to include ancient Indo-European texts in general and has spawned the [TOROT](http://torottreebank.github.io/) and [ISWOC](https://iswoc.github.io/) treebanks, which are complementary to the PROIEL Treebank.

We are constantly expanding the treebank. The following texts are in the pipeline and will be included in an upcoming release:

<table>
  <tr>
    <th>Text</th>
    <th>Language</th>
  </tr>
  <tr>
    <td>Cicero, <i>De officiis</i></td>
    <td>Latin</td>
  </tr>
  <tr>
    <td>Palladius, <i>Opus agriculturae</i></td>
    <td>Latin</td>
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

## Annotation system

The morphosyntactic annotation scheme is described in the document [PROIEL Guidelines for Annotation](http://folk.uio.no/daghaug/syntactic_guidelines.pdf).

## Development

Our releases contain the treebank on our own [PROIEL XML format](http://proiel.github.io/handbook/developer/proielxml.html). PROIEL XML is the authoritative format for PROIEL-style treebank and the only one that provides access to all the annotation we have, but for ease of use we also include the treebank as CoNLL-X and CoNLL-U files. We have [a command-line utility](https://github.com/proiel/proiel-cli) that can be used to convert PROIEL XML to various other formats (see the [documentation](http://proiel.github.io/handbook/developer/cli.html) for examples), including formats used for training taggers. For more complex tasks we have a [Ruby library](https://github.com/proiel/proiel), which is quite well [documented](http://www.rubydoc.info/gems/proiel).

<!-- Ready-made conversion of the PROIEL treebank to Universal Dependencies  -->

<hr>

<footer class="footer">
  <div class="container">
    <div class="center">
      <p>
        This website is maintained by <a href="http://johndal.com/">Marius L Jøhndal</a>. The content of this website is licensed <a href="http://creativecommons.org/licenses/by-nc-sa/4.0/">CC BY-NC-SA 4.0</a>.

      </p>

      <div id="social">
        <iframe class="github-btn" src="https://ghbtns.com/github-btn.html?user=proiel&repo=proiel-treebank&type=star&count=true" allowtransparency="true" frameborder="0" scrolling="0" width="105px" height="20px"></iframe>
      </div>
    </div>
  </div>
</footer>
