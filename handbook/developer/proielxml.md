---
layout: handbook
---

# PROIEL XML

A PROIEL XML treebank can contain one or more texts. These are called _sources_. Each source is divided into one or more _divs_, and each div contains one or more _sentences_, which finally contain one or more _tokens_. In this document, the term _object_ is used generically for sources, divs, sentences and tokens.

## Object IDs

| Element    | Attribute      | Type                           | Availability      |
|------------|----------------|--------------------------------|-------------------|
| `source`   | `id`           | String, optional               | PROIEL XML >= 1.0 |
| `div`      | `id`           | Non-negative integer, optional | PROIEL XML >= 2.1 |
| `sentence` | `id`           | Non-negative integer, optional | PROIEL XML >= 1.0 |
| `token`    | `id`           | Non-negative integer, optional | PROIEL XML >= 1.0 |

The `id` attribute on sources uniquely identifies the source within the treebank. This means that two different sources can have the same value for their `id` attribute if they belong to different treebanks or different versions of the same treebank.

The `id` attribute on divs, sentences and tokens uniquely identify the object within the source. This means that two different sentences can have the same value for their `id` attributes if they belong to different sources.

While duplication of IDs is permitted in the PROIEL XML model, it is not encouraged and should be avoided if possible. Duplication may, however, be unavoidable when multiple treebanks from different vendors or multiple versions of the same treebank are combined.

The absence of the `id` attribute from `div` elements before PROIEL XML 2.1 was unintentional.

TODO: Explain relation between ID duplication in PROIEL XML and uniqueness of XML IDs in a single XML document.

## Object order

Objects are ordered in the sequence that they occur in the original text. The only exception (depending on how you look at it) is an empty token. An empty token is a virtual token that represents a node in the dependency graph but lacks an equivalent in the original text. By convention empty tokens that encode _pro_-drop are placed immediately before the head it is a dependent of, while empty verbal tokens and empty coordinating tokens are placed at the end of the sentence. Nothing hinges on this; it is only a convention.

## Sources

Sources are represented by the element `source`.

## Textual metadata

TODO

### Chronological data

Always use the Gregorian calendar and provide only the year, not the day, month or any other commentary.

Give the year as an integer and use `BC` to denote years before year 1. Do not use other designations like `AD` for the epoch starting with year 1:

```
1040
300 BC
```

If the exact year is not known, but it is possible to place the event within a range of years, give the start and end of the range separated by `-`:

```
1040-1045
30 BC-20 BC
10 BC-10
```

If either end-point of the range is an estimate, prefix an the estimated year by `c. ` (for _circa_):

```
c. 1050-c. 1100
c. 10 BC-c. 10
```

If it is not possible to give a range, give an extimated year prefixed by `c. `:

```
c. 1050
c. 100 BC
```

As a shorthand, a century can be given instead of a range or an estimated year:

```
11th c.     (= c. 1201-c. 1300)
1st c.      (= c. 1-c. 100)
1st c. BC   (= c. 200 BC-c. 1 BC)
```

## Languages

| Element    | Attribute      | Type                           | Availability      |
|------------|----------------|--------------------------------|-------------------|
| `source`   | `language`     | Enumeration, required          | PROIEL XML >= 1.0 |

Language tags contain an [ISO-639-3](http://www.sil.org/iso639-3/) language tag.
All tags defined in the most recent version of the ISO-639-3 standard are
valid. See SIL's [ISO-639-3 code table](http://www.sil.org/iso639-3/codes.asp)
for a list.

## Annotation status

| Element    | Attribute      | Type                           | Availability      |
|------------|----------------|--------------------------------|-------------------|
| `sentence` | `status`       | Enumeration, optional          | PROIEL XML >= 1.0 |
| `sentence` | `annotated_by` | String, optional               | PROIEL XML >= 2.1 |
| `sentence` | `reviewed_by`  | String, optional               | PROIEL XML >= 2.1 |
| `sentence` | `annotated_at` | Time stamp, optional           | PROIEL XML >= 2.1 |
| `sentence` | `reviewed_at`  | Time stamp, optional           | PROIEL XML >= 2.1 |

TODO: `status`

The `status` attribute must be one of `unannotated`, `annotated` and `reviewed`. If absent, it should be understood as having the value `unannotated`.

TODO: `annotated_by`, `reviewed_by`
TODO: `annotated_at`, `reviewed_at`

## Lemma, part of speech and morphology

| Element    | Attribute        | Type                           | Availability      |
|------------|------------------|--------------------------------|-------------------|
| `token`    | `lemma`          | String, optional               | PROIEL XML >= 1.0 |
| `token`    | `part-of-speech` | String, optional               | PROIEL XML >= 1.0 |
| `token`    | `morphology`     | String, optional               | PROIEL XML >= 1.0 |

The `lemma` attribute contains the lemma associated with the token, i.e. the dictionary form of the token.

When it is necessary to distinguish between multiple lemmas with the same textual form, the PROIEL XML convention is use the associated part of speech to distinguish them.

If there are multiple lemmas with the same textual form and the same part of speech, the convention is to append `#` and a positive, non-zero integer:

```xml
<token lemma="quod#1" part-of-speech="Df">...</token>
<token lemma="quod#2" part-of-speech="Df">...</token>
```

Lemma uniqueness is therefore determined by the pair (`lemma`, `part-of-speech`).

It is a good idea to number lemmas consecutively but nothing in the model assumes that this is the case.

TODO: `part-of-speech`

Parts of speech are defined in the annotation schema included in a PROIEL XML file. For ease of reference, the table below gives the default parts of speech for a PROIEL XML 2.1 treebank:

Tag  | Part of speech
-----|-----------------------------
`A-` | adjective
`C-` | conjunction
`Df` | adverb
`Dq` | relative adverb
`Du` | interrogative adverb
`F-` | foreign word
`G-` | subjunction
`I-` | interjection
`Ma` | cardinal numeral
`Mo` | ordinal numeral
`N-` | infinitive marker
`Nb` | common noun
`Ne` | proper noun
`Pc` | reciprocal pronoun
`Pd` | demonstrative pronoun
`Pi` | interrogative pronoun
`Pk` | personal reflexive pronoun
`Pp` | personal pronoun
`Pr` | relative pronoun
`Ps` | possessive pronoun
`Pt` | possessive reflexive pronoun
`Px` | indefinite pronoun
`Py` | quantifier
`R-` | preposition
`S-` | article
`V-` | verb
`X-` | unassigned

TODO: `morphology`

## Dependency relations

TODO

Dependency relations are defined in the annotation schema included in a PROIEL XML file. For ease of reference, the table below gives the default dependency relations for a PROIEL XML 2.1 treebank:

Tag       | Dependency relation                         | Primary relation | Secondary relation
----------|---------------------------------------------|------------------|-------------------
`adnom`   | adnominal                                   | Yes              | Yes
`adv`     | adverbial                                   | Yes              | Yes
`ag`      | agens                                       | Yes              | Yes
`apos`    | apposition                                  | Yes              | Yes
`arg`     | argument (object or oblique)                | Yes              | Yes
`atr`     | attribute                                   | Yes              | Yes
`aux`     | auxiliary                                   | Yes              | Yes
`comp`    | complement                                  | Yes              | Yes
`expl`    | expletive                                   | Yes              | Yes
`narg`    | adnominal argument                          | Yes              | Yes
`nonsub`  | non-subject (object, oblique or adverbial)  | Yes              | Yes
`obj`     | object                                      | Yes              | Yes
`obl`     | oblique                                     | Yes              | Yes
`parpred` | parenthetical predication                   | Yes              | Yes
`part`    | partitive                                   | Yes              | Yes
`per`     | peripheral (oblique or adverbial)           | Yes              | Yes
`pid`     | predicate identity                          | No               | Yes
`pred`    | predicate                                   | Yes              | Yes
`rel`     | apposition or attribute                     | Yes              | Yes
`sub`     | subject                                     | Yes              | Yes
`voc`     | vocative                                    | Yes              | Yes
`xadv`    | open adverbial complement                   | Yes              | Yes
`xobj`    | open objective complement                   | Yes              | Yes
`xsub`    | external subject                            | No               | Yes

## Information structure

TODO

Information statuses are defined in the annotation schema included in a PROIEL XML file. For ease of reference, the table below gives the default information statuses for a PROIEL XML 2.1 treebank:

Tag                  | Information status
---------------------|---------------------------
`acc_gen`            | acc-gen
`acc_inf`            | acc-inf
`acc_sit`            | acc-sit
`info_unannotatable` | unannotatable
`kind`               | kind
`new`                | new
`no_info_status`     | annotatable (undecided)
`non_spec_inf`       | inferred from non-specific
`non_spec_old`       | non-specific old
`non_spec`           | non-specific
`old_inact`          | old-inact
`old`                | old
`quant`              | quantifier restriction

## Alignments

| Element    | Attribute      | Type                           | Availability      |
|------------|----------------|--------------------------------|-------------------|
| `source`   | `alignment-id` | String, optional               | PROIEL XML >= 2.1 |
| `div`      | `alignment-id` | Non-negative integer, optional | PROIEL XML >= 2.1 |
| `sentence` | `alignment-id` | Non-negative integer, optional | PROIEL XML >= 2.1 |
| `token`    | `alignment-id` | Non-negative integer, optional | PROIEL XML >= 2.1 |

The PROIEL model supports alignments between sources, between divs in different sources, between sentences in different sources and between tokens in different sources.

Alignments between objects are one-to-many; many-to-many alignments are not supported. As an illustration, this means that the model can express alignments between the Latin translation of the New Testament and the Ancient Greek original, between the Old Church Slavonic translation and the Ancient Greek original, and so on, but it cannot at the same time express alignments between the Latin and Old Church Slavonic translations.

Given this restriction, alignments are encoded in PROIEL XML on an abbreviated form. Objects whose alignment is defined have the attribute `alignment-id` with the ID of the aligned object. As the IDs of divs, sentences and tokens are unique only within each source (see section [Object IDs](#object-ids)), the `alignment-id` on `div`, `sentence` and `token` elements must be interpreted in relation to the `alignment-id` on the `source` element.

In the example below, `text1` is aligned to `text2`. The alignment of token `12345678` in `text1` should be understood to be with token `12345678` in `text2`. Similarly, sentence `123` is aligned with sentence `456` in `text2`, and div `12` with div `10000` in `text2`:

```xml
<source id="text1" alignment-id="text2">
  ...
  <div id="12" alignment-id="10000">
    ...
    <sentence id="123" alignment-id="456">
      ...
      <token id="12345678" alignment-id="12345678"/>
      ...
    </sentence>
    ...
  </div>
  ...
</source>
```

This means that if the source element lacks an `alignment-id` attribute, but one of its descendant `div`, `sentence` or `token` elements has an `alignment-id` attribute, the PROIEL XML file is inconsistent. This constraint can be verified using the `proiel validate` command.

## References to external data

| Element    | Attribute      | Type                           | Availability      |
|------------|----------------|--------------------------------|-------------------|
| `sentence` | `foreign-ids`  | String, optional               | PROIEL XML >= 1.0 |
| `token`    | `foreign-ids`  | String, optional               | PROIEL XML >= 1.0 |
| `lemma`    | `foreign-ids`  | String, optional               | PROIEL XML >= 1.0 |

The attribute `foreign_ids` is intended for storing user-defined references to external data of any kind. No particular format is required but the convention is to use a comma-separated list of key=value pairs, such as

```xml
<token ... foreign_ids="source_segment_id=T567,witness=CA">
```

## Textual values

All text should be encoded using UTF-8 and we recommend ensuring that it uses Unicode Normalization form C. (Since PROIEL XML uses XML, it is possible to use a different encoding if you specify this in the XML prologue but there is really no good reason to do this, so we say that you should not do it!)

### Representing whitespace

Whitespace in textual values is not considered significant. If a text
value contains whitespace that should be significant, as in, for example,
poetry and drama, the following Unicode characters should be used:

  1. For a line break, use [`U+2028 (LINE
     SEPARATOR)`](https://codepoints.net/U+2028)
  2. For a paragraph break, use [`U+2029 (PARAGRAPH
     SEPARATOR)`](https://codepoints.net/U+2029)
  3. For an indented line (in poetry, after a line break), use TODO
  4. For a caesura (in poetry, within a line), use TODO

### Character codes with special interpretation

| Code point | Character name        | Function in PROIEL XML      | Recommended HTML translation |
|------------|-----------------------|-----------------------------|------------------------------|
| U+2028     | LINE SEPARATOR        | End of line in poetry/drama      | `<br>`   |
| U+2029     | PARAGRAPH SEPARATOR   | End of paragraph in poetry/drama | `<p>`    |
| U+F000     | PRIVATE USE CODEPOINT | Start of italics                 | `<i>`    |
| U+F001     | PRIVATE USE CODEPOINT | Start of subscript               | `<sub>`  |
| U+F002     | PRIVATE USE CODEPOINT | Start of superscript             | `<sup>`  |
| U+F003     | PRIVATE USE CODEPOINT | Start of bold face               | `<b>`    |
| U+F100     | PRIVATE USE CODEPOINT | End of italics                   | `</i>`   |
| U+F101     | PRIVATE USE CODEPOINT | End of subscript                 | `</sub>` |
| U+F102     | PRIVATE USE CODEPOINT | End of superscript               | `</sup>` |
| U+F103     | PRIVATE USE CODEPOINT | End of bold face                 | `</b>`   |

### Rendering as HTML

The principles for rendering textual values as HTML are as follows:

  1. Concatenate all textual values columns in their implicit
     order, including any relevant metadata like citations if required.
  2. Map each code point in the table above to their recommended HTML translation.
  3. Replace any sequence of whitespace with a single `U+0020 (SPACE)`
     character.
  4. Remove any whitespace from the beginning and end of the string.

## Schema versions

Version |
--------|
[PROIEL XML 2.1](https://raw.githubusercontent.com/proiel/proiel/master/lib/proiel/proiel_xml/proiel-2.1/proiel-2.1.xsd) |
[PROIEL XML 2.0/2.0.1](https://raw.githubusercontent.com/proiel/proiel/master/lib/proiel/proiel_xml/proiel-2.0/proiel-2.0.xsd) |
[PROIEL XML 1.0](https://raw.githubusercontent.com/proiel/proiel/master/lib/proiel/proiel_xml/proiel-1.0/proiel-1.0.xsd) |

### PROIEL XML 1.0

This was the first version of PROIEL XML intended for public consumption. This version is now obsolete.

### PROIEL XML 2.0/2.0.1

This version replaces the TEI header of version 1.0 with a sequence of pre-defined metadata elements.

### PROIEL XML 2.1

This version adds the following new attributes:

  - an optional `id` attribute on `div` elements
  - an optional `alignment-id` attribute on `source`, `div`, `sentence` and `token` elements
  - optional `annotated-by`, `annotated-at`, `reviewed-by` and `reviewed-at` attributes on `sentence` elements

Any valid PROIEL XML 2.0 treebank is also a valid PROIEL XML 2.1 treebank.

### PROIEL XML 3.0 (**unreleased**)

This version adds support for dictionaries. These are defined per language using the `dictionary` element. 

This version also adds the following new elements:

  - optional `note` elements under `source`, `div`, `sentence`, `token` and `lemma`
  - optional `tag` elements under `token` and `lemma`

Any valid PROIEL XML 2.1 treebank is also a valid PROIEL XML 3.0 treebank.

