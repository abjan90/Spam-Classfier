The codes and the Solution to the exercises from the book hands On machine learning

1. Stemming bhaneko chahi different word which gives off same meaning lai chahi process garnu bhanda aghi same banauney. So , for eg => if we have word DO , DOING , DOES this have same meaning but if we don't use stemming the model will differentiate each word as different. So we use a natural language processing model called nltk and stem it.

2. We will also need a way to replace URLs with the word "URL". SO we use urlextract library.

3. The first transformer email_to_word_count converts the email object into word count and which can be used for the further processing.

4. In the second Transformer the fit method will build the vocabulary of common words and transform method will use the vocabulary to convert word counts into the vectors.

5. LogisticRegression model is used and Precision => 95.70% is acheived with recall => 93.68%.

