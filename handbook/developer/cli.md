---
layout: handbook
---

The general format is `proiel` followed by a command, any options and one or more filenames:

```shell
proiel info -V caes-gal.xml cic-att.xml
```

Most commands also require sub-commands:

```shell
proiel convert conll -V caes-gal.xml
```

The filename arguments are the treebank files to process. All commands accept plain PROIEL XML files or gzipped PROIEL XML files:

```shell
proiel convert conll caes-gal.xml
proiel convert conll caes-gal.xml.gz
```

## Validating

PROIEL XML can be validated using

```
proiel validate input.xml
```

This will peek at the file to determine the version of PROIEL XML to use, validate it using the appropriate XML schema  and then run a number of integrity checks, which verify that cross-references between objects are valid and that the annotation is consistent with the annotation schema.

If you only want to validate the file using the XML schema, you can use a tool like `xmllint`

```
xmllint --nonet --noout --path path_to_schema_files --schema path_to_schema_files/proiel.xsd input.xml
```

## Converting to CoNLL-X

Conversion to [CoNLL-X](http://ilk.uvt.nl/conll/#dataformat) is done using
```
proiel convert conll-x input.xml > output.conll
```

Official releases of the PROIEL treebank include the CoNLL-X format and can be downloaded from the [PROIEL treebank](http://proiel.github.io/).

## Converting to CoNLL-U

Conversion to [CoNLL-U](http://universaldependencies.org/docs/format.html) can be done using
```
proiel convert conll-u input.xml > output.conllu
```
Note that the conversion is experimental and the output is likely to evolve as the Universal Dependencies project matures.

Curated versions of the PROIEL treebank on CoNLL-U format can be downloaded from the [Universal Dependencies](http://universaldependencies.org/) project.

## Merging treebank files

Several treebank files can be merged into one treebank file by using `proiel convert proielxml` with multiple input files:

```shell
proiel convert proielxml caes-gal.xml cic-att.xml
```

The result will be a PROIEL XML file with multiple `source` elements:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<proiel export-time="2014-12-19T12:44:28+01:00" schema-version="2.0">
  <annotation>
     ...
  </annotation>
  <source id="caes-gal" language="lat">
     ...
  </source>
  <source id="cic-att" language="lat">
     ...
  </source>
</proiel>
```

The treebanks to be merged must all use the same schema version and the same tagset.

## Removing information from treebank files

Information can be removed from treebank files by using `proiel convert proielxml` with options like `--remove-information-structure`. Use `proiel convert proielxml --help` for a full list.

## Searching for text

Simple tearches can be performed using `proiel grep` followed by a regular expression. This will serahc the text (which is the `form` attribute on tokens and any `presentation_before`
and `presentation_after` attributes on tokens, sentences and divs) and return any text that matches the regular expression, as in this example:

```
$ proiel grep 'pel' caes-gal.xml
Caes. Gal. 1.1.1 (ID = 52548) Gallia est omnis divisa in partes tres, quarum unam incolunt Belgae, aliam Aquitani, tertiam qui ipsorum lingua Celtae, nostra Galli appellantur.
Caes. Gal. 1.3.3 (ID = 52570) In eo itinere persuadet Castico, Catamantaloedis filio, Sequano, cuius pater regnum in Sequanis multos annos obtinuerat et a senatu populi Romani amicus appellatus erat, ut regnum in civitate sua occuparet, quod pater ante habuerit;
...
$ proiel grep '^pel' caes-gal.xml
Caes. Gal. 3.13.6 (ID = 53210) pelles pro velis alutaeque tenuiter confectae, sive propter inopiam lini atque eius usus inscientiam, sive eo, quod est magis veri simile, quod tantas tempestates Oceani tantosque impetus ventorum sustineri ac tanta onera navium regi velis non satis commode posse arbitrabantur.
```

The regular expression is applied to one sentence at a time so the anchors `^` and `$` refer to the beginning and end of the sentence.

To apply a regular expression to each individual token instead, use the `--level token` option:

```
$ proiel grep 'pel' --level token caes-gal.xml
Caes. Gal. 1.1.1 (ID = 680740) appellantur.
Caes. Gal. 1.3.3 (ID = 681128) appellatus
Caes. Gal. 1.12.4 (ID = 682300) appellabatur
...
$ proiel grep '^pel' --level token caes-gal.xml
Caes. Gal. 1.31.11 (ID = 685232) pellerentur
Caes. Gal. 2.33.2 (ID = 693103) pellibus
Caes. Gal. 3.13.6 (ID = 852327) pelles
...
```

Matching is by default case sensitive. Use the `-i` option for case-insensitive matching:

```
$ proiel grep 'Gal' --level token caes-gal.xml
Caes. Gal. 1.1.1 (ID = 680720) Gallia
Caes. Gal. 1.1.1 (ID = 680739) Galli
Caes. Gal. 1.1.2 (ID = 680749) Gallos
...
$ proiel grep 'Gal' --level token -i caes-gal.xml
...
Caes. Gal. 1.17.4 (ID = 761727) Gallia
Caes. Gal. 1.18.3 (ID = 683173) vectigalia
Caes. Gal. 1.19.3 (ID = 756644) Galliae
...
```

