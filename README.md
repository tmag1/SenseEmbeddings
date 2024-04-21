# Generating Sense Embeddings

The included notebook utilizes code from the following sources:

- [LMMS](https://github.com/danlou/LMMS/tree/master)
- [fullstop-punctuation-multilang-large hugging face model](https://huggingface.co/oliverguhr/fullstop-punctuation-multilang-large)
- [TextGrids and utils](https://github.com/HuthLab/speechmodeltutorial/tree/master) from HuthLab's speech model tutorial

Additionally, vectors were downloaded from [this dataset](https://figshare.com/articles/dataset/LMMS-SP_ALBERT-XXLARGE/21975773?file=38999423) on figshare. Specifically, the file used is 'lmms-sp-wsd.albert-xxlarge-v2.vectors.txt'.

Update notes(04/15):
- I was having trouble running the full script for syntax embeddings but I wrote a function that takes in a sentence and a list of next words and return the most likely word if it is in the list of possibilities
- I started writing code for a siamese model approach, the issue right now is that I have to come up with a way to define syntactic similarity using the dependency and pos tags that will make sure there is a minimum overlap for tag of at least 2. 

Update Notes:

- [This](https://huggingface.co/oliverguhr/fullstop-punctuation-multilang-large) hugging face model seems to be the best solution to inserting punctutation. It seems nltk doesn't have functionality for inserting punctuation. I experimented with different hugging face models and this one has the highest accuracy. [This one](https://huggingface.co/felflare/bert-restore-punctuation) is also pretty good (a little worse than currently used one) but I was having dependency issues when trying to get it to work. You can also use GPT to insert punctuation but I would have to find a solution for ensuring words aren't deleted or added.
- The generate_sense_embedding function now also returns a dictionary that contains non-stop words that don't have sense embeddings and how often they appear in the given text. It also returns a list of sentences so you can review how punctuation was inserted and how the original text was split into sentneces based on the inserted punctuation.
