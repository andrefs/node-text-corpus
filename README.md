
# cetem-publico

Some classes to represent elements in a text corpus. Currently, this
is mainly something to be used in [cetem-publico](https://www.npmjs.com/package/cetem-publico), [tnt-tagger]() and other modules, but hopefully it will be generic enough to be useful in other contexts as well.

## Installation

```bash
$ npm install text-corpus
```

## Classes

### Token
Used to represent the tokens in the original corpus file. In the
format used by CETEMPublico, each token is in an individual line.

#### `new Token(word, info)`

* `word` is the word in the original corpus text
* `info` (all these are optional)
    * `lineNum`: the line number for this token in the original corpus
      file
    * `tokenId`: an ID for this token
    * `section`: the ID of the section the token is in
    * `week`:
    * `lemma`: the lemmatized version of `word`
    * `pos`: the part-of-speech (POS) tag for `word`
    * `other*: an object with all the extra information found in
      CETEMPublico for this token

### MultiWordExpression

CETEMPublico annotates some mult-word expressions using `<mwe>` tags.
Inside each tag, the tokens which compose the expression, one in each
line. MWEs can have attributes indicating the lemma and the POS tag
for the whole expression.

#### `new MultiWordExpression({lemma, pos}, tokens)`

* `lemma`: the lemma for the multi-word expression
* `pos`: the POS tag for the multi-word expression
* `tokens`: an array of Token objects which make this MWE

### Sentence

In CETEMPublico, a sentence is represented using a `<s>` tag.
Sentences contain a list of tokens (the words in that sentence).
Because some words can form multi-word expressions, inside a
`Sentence` we can find both `Token`s and `MultiWordExpression`s
(which, in turn, have `Token` objects inside).

#### `new Sentence(id, tokens)`

* `id`: an id for the sentence
* `tokens`: an array of tokens and MWEs which form this sentence

### Paragraph
A paragraph, represented in CETEMPublico using the tag `<p>`.
Paragraphs are composed of a sequence of sentences.

#### `new Paragraph(id, sentences)`

* `id`: an id for the paragraph
* `sentences`: an array of sentences which form this paragraph

## Bugs and stuff

Open a [GitHub issue](https://github.com/andrefs/node-text-corpus/issues) or, preferably, send me a pull request.

## License

MIT

