---
layout: handbook
published: true
---

<div class="notification is-danger">
  <button class="delete"></button>
  As of July 2016, this document is an evolving draft. All information here is correct and up to date, but very incomplete.
</div>

# Valency

Valency is presented in terms of argument frames, which are generated automatically from the morphosyntactic annotation.

Generating an argument frame for a specific instance of a predicate in a treebank minimally requires the following three steps.

First, all dependents of the predicate are filtered by relation. Dependents whose relation do not indicate argumenthood are discarded from further consideration. In this filtering process, `obj`, `obl`, `xobj`, `comp` and `narg` count as arguments, while `sub`, `ag`, `adv`, `xadv`, `aux`,<sup id="a1">[1](#f1)</sup> `apos`, `atr`, `part` and `expl` do not. Among the unspecific relations, `arg`, which always indicates an argument, counts as an argument; `adnom`, `nonsub` and `per`, which may or may not actually indicate arguments, do not count; and `rel`, which never indicates an argument, does not count.

Second, certain morphological feature values are extracted from each dependent. These are feature values that tend to play a role in argument selection regardless of language. For nominal dependents (nouns, adjectives, pronouns and numerals), the value of the `case` feature is extracted. For verbal dependents (verbs), the value of the `mood` feature is extracted. For other dependents, no feature value is extracted.

Note that the `case` and `mood` features can have values that express unspecific or uncertain analyses. Such values will percolate into the final argument frame. Recall also that the `mood` feature in PROIEL treebanks covers both the mood of finite verbs and the classification of various forms of non-finite verbal forms.

Finally, an argument frame is constructed by pairing the relation and the morphological feature values of each dependent, and then sorting these pairs. The pairs are sorted by increasing obliqueness.

Relations are sorted using the obliqueness hierarchy
```
obj < xobj < arg < obl < comp < narg
```
Pairs with morphological feature values are considered to be more oblique than pairs without, but no specific order is defined for pairs with the same relation but different morphological feature values.

Additional steps are necessary in a number of circumstances:

* **Coordination**: When a dependent is headed by a coordinator, whether asyndetic or an overt conjunction, the relevant valency information is found among the coordinated dependents. The following procedure deals with coordination: First, all dependents are hoisted to the same level so that they depend directly on the predicate whose valency frame is to be computed. Hoisting applies recursively as there is no ban on embedding coordinators within coordinators. Second, the relation and morphological features of the hoisted dependents are folded. If the result is a unique relation and unique morphological features, these are treated as representative of the entire coordination. If the features are not unique, they are ignored.

* **Function words**: For subjunctions and prepositions the relevant morphological features are those of the dependent of the function word. We also include the lemma of the function word. The dependent of the function word may be a coordination, which has to be resolved as above. Additionally, as there is no ban on multiple dependents of a single function word without any coordination, the relations and features of all dependents of the function word have to be folded and tested for uniqueness.

* **Adverbs**: For adverbs in argument position we include the lemma of the adverb.

<b id="f1">1</b> Although dependents with the relation `aux` do not count as arguments, the valency algorithm includes a subset of them for some languages. For Slavic languages, where reflexives can play an important role in verbal valency frames, `aux` dependents that are reflexive are included in valency frames. [↩](#a1)
