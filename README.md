
# Abstractive Dialogue Summarization


Astract summary extraction from text dialogue between multiple people in both The arabic and english language




## Dataset
SAMSum Corpus[1] is a dataset with over 16k abstractive dialogue summaries.\
Translated it to Arabic.\
Processing included:
- seperate each speaker with ( | )
- replace abbreviations
- remove special character and emojis
etc \
splitting the data to 16k train, 800 test and 800 validation \
English tokens consisted of 500 for dialogue and 84 for summary whereas the Arabic tokens where at 700 for dialogue and 128 for summary


## Train
### T5
T5 is an encoder-decoder model and converts all NLP problems into a text-to-text format. it is trained on different task. \
we used the t5-base for, which is available on pytorch, on the english data and limited the summary length to 150.
- epochs: 3
- batch-size: 4
- optimizer: AdamW

### mT5
mT5 is a multilingual variant of T5. \
the tokenizer contains 250k tokens for 101 languages, we only took 12k that concerns the arabic language to reduce the redundant size.
- epochs: 1
- batch-size: 1
- optimizer: AdamW

## Results
| Model  | Data | R-1 | R-2 | R-3 |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| DynamicConv + GPT-2 emb. [1]   | English  | 45.41  | 20.65  | 41.45  |
| T5  | English  | 45.43  | 21.61  | 42.15  |
| mT5  | Arabic  | 29.03  | 8.4  | 27.97  |


## References

 - [1] Gliwa, Bogdan, Iwona Mochol, Maciej Biesek, and Aleksander Wawer. "Samsum corpus:A human-annotated dialogue dataset for abstractive summarization." arXiv preprint arXiv:1911.12237 (2019).
