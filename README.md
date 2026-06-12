# Burmese Language Corpus

> A monolingual Burmese (Myanmar) text corpus for low-resource NLP.

A collection of plain-text Burmese sentences derived from the CC100 dataset, intended as raw training data for language modeling, tokenization, and other Burmese NLP tasks where labeled or monolingual data is scarce.

![Language: Burmese](https://img.shields.io/badge/language-Burmese-blue)
![Format: TXT](https://img.shields.io/badge/format-plain%20text-lightgrey)
![Encoding: UTF-8](https://img.shields.io/badge/encoding-UTF--8-green)
![License: Apache 2.0](https://img.shields.io/badge/license-Apache%202.0-orange)

## Contents

The corpus lives under `corpus/`, split across 13 plain-text shards. Each shard holds roughly 150,000 sentences.

```
corpus/
    |--- bm_corpus_1.txt
    |--- bm_corpus_2.txt
    |--- ...
    |--- bm_corpus_13.txt
```

## Data Format

- Plain-text (`.txt`), UTF-8 encoded.
- One Burmese sentence per line.
- No labels, headers, or metadata — raw monolingual text only.

Example lines:

```
လင်းတငှက်တို့သည်
လူသေကောင်ပုပ်ကိုရှာကြသည်။
```

## Usage

Read a shard line by line in Python:

```python
with open("corpus/bm_corpus_1.txt", encoding="utf-8") as f:
    sentences = [line.strip() for line in f if line.strip()]

print(len(sentences), sentences[0])
```

Stream all shards together:

```python
import glob

for path in sorted(glob.glob("corpus/bm_corpus_*.txt")):
    with open(path, encoding="utf-8") as f:
        for line in f:
            line = line.strip()
            if line:
                ...  # process sentence
```

## Source / Provenance

Derived from CC100 (Burmese): https://huggingface.co/datasets/cc100

> This corpus is an attempt to recreate the dataset used for training XLM-R. This corpus comprises monolingual data for 100+ languages, constructed from the January–December 2018 Commoncrawl snapshots using the CC-Net repository. No claims of intellectual property are made on the preparation of the corpus.

## License

Released under the [Apache License 2.0](LICENSE).
