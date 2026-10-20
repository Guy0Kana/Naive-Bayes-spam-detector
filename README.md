# Naïve Bayes Spam Email Detector

Spam classifier built with a bag-of-words model and Multinomial Naïve Bayes.

## Dataset
[Spam filter dataset (Kaggle)](https://www.kaggle.com/datasets/karthickveerakumar/spam-filter): 5,728 emails, ~76% ham / 24% spam.
Download `emails.csv` and place it in `data/`.

## Method
1. Remove duplicates (33 rows)
2. Clean text: lowercase, strip punctuation, remove stop words, Porter stemming
3. Stratified 80/20 train/test split
4. `CountVectorizer` (top 5000 words), fit on training data only
5. `MultinomialNB`

## Results (test set, 1139 emails)
| Class | Precision | Recall | F1 |
|---|---|---|---|
| ham | 1.00 | 0.98 | 0.99 |
| spam | 0.95 | 0.99 | 0.97 |

Accuracy: 98.60%. Only 2 spam emails missed; 14 legitimate emails wrongly flagged.

## Run it
pip install -r requirements.txt
jupyter notebook naivebayes-spamdetector.ipynb

## Limitations
- The dataset looks Enron-era, so the model may not generalize to modern spam.
- Bag-of-words ignores word order and context.
