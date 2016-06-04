---
layout: handbook
---

# PROIEL XML

## Object IDs

| Element    | Attribute      | Type                           | Availability      |
|------------|----------------|--------------------------------|-------------------|
| `source`   | `id`           | String, optional               |                   |
| `div`      | `id`           | Non-negative integer, optional | PROIEL XML >= 2.1 |
| `sentence` | `id`           | Non-negative integer, optional |                   |
| `token`    | `id`           | Non-negative integer, optional |                   |

The `id` attribute on sources uniquely identifies the source within the treebank. This means that two different sources can have the same value for their `id` attribute if they belong to different treebanks or different versions of the same treebank.

The `id` attribute on divs, sentences and tokens uniquely identify the object within the source. This means that two different sentences can have the same value for their `id` attributes if they belong to different sources.

While duplication of IDs is permitted in the PROIEL XML model, it is not encouraged and should be avoided if possible. Duplication may, however, be unavoidable when multiple treebanks from different vendors or multiple versions of the same treebank are combined.

The absence of the `id` attribute from `div` elements before PROIEL XML 2.1 was unintentional.

TODO: Explain relation between ID duplication in PROIEL XML and uniqueness of XML IDs in a single XML document.

## Annotation status

| Element    | Attribute      | Type                           | Availability      |
|------------|----------------|--------------------------------|-------------------|
| `sentence` | `status`       | Enumeration, optional          |                   |
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
| `token`    | `lemma`          | String, optional               |                   |
| `token`    | `part-of-speech` | String, optional               |                   |
| `token`    | `morphology`     | String, optional               |                   |

The `lemma` attribute contains the lemma associated with the token, i.e. the dictionary form of the token.

When it is necessary to distinguish between multiple lemmas with the same textual form, the PROIEL XML convention is use the associated part of speech to distinguish them.

If there are multiple lemmas with the same textual form and the same part of speech, the convention is to append `#` and a positive, non-zero integer:

```xml
<token lemma="quod#1" part-of-speech="Df">...</token>
<token lemma="quod#2" part-of-speech="Df">...</token>
```

Lemma uniqueness is therefore determined by the pair (`lemma`, `part-of-speech`).

TODO: `part-of-speech`
TODO: `morphology`

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

