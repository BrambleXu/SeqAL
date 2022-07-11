# Tutorial 4: Prepare Data Pool

This tutorial shows how to prepare data pool.

## Load CoNLL Format


We can use the `ColumnDataset` class to load CoNLL format. 

```python
from seqal.datasets import ColumnDataset

columns = {0: "text"}
pool_file = "./datasets/conll/train_pool.txt"
data_pool = ColumnDataset(pool_file, columns)
unlabeled_sentences = data_pool.sentences
```

We can get sentences from data_pool by calling `sentences` property.

```python
print(data_pool.sentences[0])
```

This prints:

```
Sentence: "Taleban said its shipment of ammunition from Albania was evidence of Russian military support for Rabbani 's government ."   [− Tokens: 19  − Token-Labels: "Taleban <B-MISC> said its shipment of ammunition from Albania <B-LOC> was evidence of Russian <B-MISC> military support for Rabbani <B-PER> 's government ."]
```

## Load Plain Text

We can use `load_plain_text` to read the unlabeled dataset. This will create a list of `Sentence` objects.

```python
from seqal.utils import load_plain_text

file_path = "./datasets/conll/train_pool.txt"
unlabeled_sentences = load_plain_text(file_path)
```

## Non-spaced Language

As we mentioned in [TUTORIAL_2_Prepare_Corpus](TUTORIAL_2_Prepare_Corpus.md), we have to provide the tokenized data for non-spaced language.


An example with CoNLL format:

```
東京
は
都市
です
```
