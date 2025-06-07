# Twitter Sentiment Analysis

## Project Overview

The main objective of this project is to perform sentiment analysis on Twitter data related to Narendra Modi. By analyzing tweets, we aim to understand public opinion and identify sentiment trends surrounding him.

## Data Description and Preprocessing

**Dataset:** The dataset used is the "Twitter Sentiment Dataset" available on Kaggle, contributed by *S. Shahane.* It contains tweet text (`clean_text`) and a sentiment category (`category`). The data set can be found at https://www.kaggle.com/datasets/milobele/sentiment140-dataset-1600000-tweets?utm_source=chatgpt.com

**Preprocessing Steps:**

1.  **Handling Missing Values:** Rows with missing `clean_text` or `category` were removed.
2.  **Filtering Categories:** Data was filtered to include only positive (1) and negative (-1) sentiments.
3.  **Mapping Sentiment:** Categories were mapped to a binary `sentiment` column (1 for positive, 0 for negative).
4.  **Text Cleaning:** A custom function `clean_text` was applied to:
    *   Remove URLs, mentions, and special characters.
    *   Convert text to lowercase.
    *   Tokenize and lemmatize words.
    *   Remove stop words.
    *   Join cleaned words into a string (`clean` column).

## Exploratory Data Analysis (EDA)

EDA was conducted to understand the dataset characteristics:

*   **Class Distribution:** Visualized the balance of positive and negative tweets.
*   **Tweet Length Distribution:** Analyzed the length of tweets.
*   **Word Clouds:** Visualized the most frequent words in positive and negative tweets.
*   **Top Bi-grams:** Identified the most common two-word phrases.
*   **Tweet Length by Sentiment:** Compared tweet lengths across sentiment categories.
*   **Top Words by Sentiment:** Displayed the most frequent words for each sentiment after cleaning.

## Model Building and Comparison

Two types of models were built and compared for sentiment classification:

1.  **Logistic Regression:** A traditional machine learning model evaluated with two vectorization techniques:
    *   TF-IDF (Term Frequency-Inverse Document Frequency)
    *   Count Vectorization
    Hyperparameter tuning for the `C` parameter was performed using GridSearchCV.

2.  **Long Short-Term Memory (LSTM):** A deep learning model designed for sequential data.
    Text data was processed using tokenization, text-to-sequence conversion, and padding.
    Different batch sizes were tested during training.

## Results and Evaluation

Both models were evaluated using standard classification metrics:

*   **Hyperparameter Tuning Results:**
    *   Logistic Regression (TF-IDF): Best C = 10.0, Test Accuracy = 0.911
    *   Logistic Regression (Count): Best C = 1.0, Test Accuracy = 0.912
    *   LSTM: Batch Size 64 showed slightly better validation accuracy (0.911) compared to 32 (0.909) during tuning.

*   **Final Model Performance:**
    *   **Logistic Regression (using Count Vectorizer with C=1.0):**
        *   Accuracy: 0.900
        *   Classification Report:
