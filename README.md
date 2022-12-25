# text-classification-indonesian-health-influencers
This repository contains a text classification with 3 attributes, there are sentiment, agreement, and emotion with a state-of-the-art model based on Indonesian BERT transformers from indobenchmark. 
The results show that the classification model, IndoBERT by IndoNLU is the best model used for the calculation of the influence score with an accuracy score of 84%-96%, an average precision of 84%-97%, and recall of 83%-97% for all labels.

#Dataset
The dataset is extracted and collected from Twitter with Twitter API and tweepy library from 7 health influencer in Indonesia in January and February 2022. The dataset is consists of indonesian, english, and mix of those two languages. The train data is all tweets and replies from January 2022 that labelled manually (gold-label) and the test data is all tweets and replies from February 2022.

#Attributes definition
1. Sentiment
- Defines the tweet and reply sentiment
- Consists of three labels there are positive, negative, and neutral
2. Agreement
- Defines if the reply is agree with the tweet. Consists of three labels there are agree, neutral, and disagree
- The agreement indoBERT model has different approach with other attributes, because there is two inputs (tweet and reply) so I utilized the segment_ids for tokenization
3. Emotion
- Defines the tweet and reply emotion
- Consists of 7 labels there are anger, disgust, fear, joy, sadness, surprise, and neutral

The attributes and labels are based on research by Sailunaz and Alhajj, R (2019) "Emotion and sentiment analysis from Twitter text" in Journal of Computational Science, 36, 101003. https://doi.org/10.1016/j.jocs.2019.05.009

#Model Training Parameter
- Batch size: 32
- Optimizer: AdamW
- Learning Rate: 2e-5
- Epsilon: 1e-8

Model training for the emotion attributes will be carried out in stages because the number of neutral labels dominates. 
- The first training is for the binary emotion category, which contains neutral and emotion labels. 
- The second training for both tweets and replies labeled emotion then will be classified into five labels, namely anger, disgust, joy, fear, and sadness.
