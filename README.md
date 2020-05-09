# Toxic Comment Classification
### Description
The threat of abuse and harassment online means that many people stop expressing themselves and give up on seeking different opinions. Platforms struggle to effectively facilitate conversations, leading many communities to limit or completely shut down user comments.

In this competition, we’re challenged to build a multi-headed model that’s capable of detecting different types of of toxicity like threats, obscenity, insults, and identity-based hate better than Perspective’s current models. We’ll be using a dataset of comments from Wikipedia’s talk page edits. Improvements to the current model will hopefully help online discussion become more productive and respectful.

Disclaimer: the dataset for this competition contains text that may be considered profane, vulgar, or offensive.

Contest link: https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge
## Summary of my approach

- This Case study involves classifying a text to one of the 6 classes :- Toxic, Severe_toxic, Obscene, Threat, Insult, Identity_hate.
- I decided to use the Fasttext and twitter word vectors to try and model the vocabulary of the comment.
- I imported the dataset to check for the number of comments under each class checked for any null values. The total number of clean comments are 89% approx.
- I then used some simple regex to clean the train and text data to make the comments as simmilar as possible without changing the meaning of the sentence.
- I also tried to extend the vocabulary by translating the sentences to a different language and translating them back to english. The idea is that this would expose the model to a larger vocabulary. This could not work as google translate api doesn't allow translating beyond a certain limit for free.
- I also tried manual find and replace for words that had the same meaning but different spellings. This was all done in part to clean the test as much as posisible. Problems like these boil down to the quality of the dataset.
- After this, I checked which word vectors account for the maximum amount of vocabulary in the dataset. Fast-text word vectors could only account for a measly 0.64% of the entire vocabulary, whereas twitter word vectors could account for around 48% of the vocabulary. Hence the embedding matrix was created using the twitter word vectors.
- A deep learning model using Convolution layers was built and ROC-AUC score was used as a performance metric. The Kaggle dashboard gave the best value of ROC-AUC score as 98.12 which is a top 50% solution.
