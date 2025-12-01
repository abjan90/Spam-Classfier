The codes and the Solution to the exercises from the book hands On machine learning

1. Stemming for Semantic Normalization
Stemming reduces words to their root form to ensure semantic equivalence. For example, "do," "doing," and "does" share the same meaning but would be treated as distinct features without normalization. I implemented the NLTK Porter Stemmer to consolidate these variations, reducing feature dimensionality while preserving semantic information.
2. URL Normalization
Spam emails frequently contain numerous URLs that add noise to the feature space. Using the urlextract library, all URLs are identified and replaced with a standardized "URL" token. This approach captures the presence of hyperlinks without overwhelming the model with unique URL variations.
3. Custom Transformer: email_to_word_count
The first transformer in the pipeline converts raw email objects into structured word count dictionaries. This component handles:

Multipart MIME email parsing
HTML-to-text conversion using BeautifulSoup
Text normalization (lowercasing, URL replacement, number tokenization)
Word stemming via NLTK Porter Stemmer
Generation of Counter objects for efficient word frequency tracking

4. Custom Transformer: word_count_to_vector
The second transformer converts word count dictionaries into numerical feature vectors:

fit() method: Builds a vocabulary of the 1,000 most common words across the training corpus, implementing frequency capping (max count of 10 per word per email) to prevent spam repetition from dominating features
transform() method: Converts word counts to sparse matrix representation using scipy's Compressed Sparse Row (CSR) format, mapping each word to its vocabulary index for efficient computation

5. Model Performance
A Logistic Regression classifier (liblinear solver) was trained on the transformed features, achieving:

Precision: 95.74% - Minimizes false positives (legitimate emails marked as spam)
Recall: 94.74% - Effectively captures the majority of spam emails

These metrics demonstrate the effectiveness of custom feature engineering in text classification tasks.
