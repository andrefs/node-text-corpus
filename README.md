
# text-corpus

Some classes to represent elements in a text corpus. Currently, this
is mainly something to be used in [cetem-publico](https://www.npmjs.com/package/cetem-publico), [tnt-tagger]() and other modules, but hopefully it will be generic enough to be useful in other contexts as well.

## Installation

```bash
$ npm install text-corpus
```

## Classes

### Token
Used to represent the tokens (words) in the corpus.

#### `new Token(word, info)`

* `word` is the word in the original corpus text
* `info` (all these are optional)
    * `tokenId`: an ID for this token
    * `lemma`: the lemmatized version of `word`
    * `pos`: the part-of-speech (POS) tag for `word`
    * `other*: more information about the token

### MultiWordExpression

This class provides a way to group some tokens into multi-word
expressions.

MWEs can have attributes indicating the lemma and the POS tag
for the whole expression.

#### `new MultiWordExpression({lemma, pos}, tokens)`

* `lemma`: the lemma for the multi-word expression
* `pos`: the POS tag for the multi-word expression
* `tokens`: an array of Token objects which make this MWE

### Sentence

Sentences contain a list of tokens (the words in that sentence).
Because some words can form multi-word expressions, inside a
`Sentence` we can find both `Token`s and `MultiWordExpression`s
(which, in turn, have `Token` objects inside).

#### `new Sentence(id, tokens)`

* `id`: an id for the sentence
* `tokens`: an array of tokens and MWEs which form this sentence

### Paragraph
Paragraphs are composed of a sequence of sentences.

#### `new Paragraph(id, sentences)`

* `id`: an id for the paragraph
* `sentences`: an array of sentences which form this paragraph

## Bugs and stuff

Open a [GitHub issue](https://github.com/andrefs/node-text-corpus/issues) or, preferably, send me a pull request.

## License

MIT

