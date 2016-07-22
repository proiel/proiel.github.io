---
layout: handbook
---

<div class="notification is-danger">
  <button class="delete"></button>
  As of July 2016, this document is an evolving draft. All information here is correct and up to date, but very incomplete.
</div>

# Valency

Valency is presented in terms of argument frames, which are generated automatically from the morphosyntactic annotation.

Generating an argument frame for a specific instance of a predicate in a treebank minimally requires the following three steps.

  1. All dependents of the predicate are filtered by relation. Dependents whose relation do not indicate argumenthood are discarded from further consideration. In this filtering process, `obj`, `obl`, `xobj`, `comp` and `narg` count as arguments, while `sub`, `ag`, `adv`, `xadv`, `aux`, `apos`, `atr`, `part` and `expl` do not. Among the unspecific relations, `arg`, which always indicates an argument, counts as an argument; `adnom`, `nonsub` and `per`, which may or may not actually indicate arguments, do not count; and `rel`, which never indicates an argument, does not count.

  2. Certain morphological feature values are extracted from each dependent. These are feature values that tend to play a role in argument selection regardless of language. For nominal dependents (nouns, adjectives, pronouns and numerals), the value of the `case` feature is extracted. For verbal dependents (verbs), the value of the `mood` feature is extracted. For other dependents, no feature value is extracted.

  Note that the `case` and `mood` features can have values that express unspecific or uncertain analyses. Such values will percolate into the final argument frame. Recall also that the `mood` feature in PROIEL treebanks covers both the mood of finite verbs and the classification of various forms of non-finite verbal forms.

  3. An argument frame is constructed by pairing the relation and the morphological feature values of each dependent, and then sorting these pairs. The pairs are sorted by increasing obliqueness.

  Relations are sorted using the obliqueness hierarchy
  ```
  obj < xobj < arg < obl < comp < narg
  ```
  Pairs with morphological feature values are more oblique than pairs without, but no specific order is defined for pairs with the same relation but different morphological feature values.

Two additional steps are often necessary:

* function words

* coordination

Both overt coordination and asyndetic coordination count
