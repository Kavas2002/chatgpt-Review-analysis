# ChatGPT Review Analysis

## Project Overview

This project analyzes ChatGPT user reviews using Python, Pandas, visualization libraries, and NLTK. It explores review ratings, prepares the review data, classifies reviews using rating-based labels, performs VADER sentiment analysis, and examines common words in negative reviews.

## Dataset

The notebook reads a CSV file named `chatgpt_reviews.csv`.

The dataset shown in the notebook contains these columns:

- `Review_ID` – review identifier
- `Review` – text of the user review
- `Ratings` – numerical rating
- `Date` – review date

The notebook initially displays approximately 196,727 records and four columns. The CSV file is loaded from Google Drive in Google Colab.

> Place `chatgpt_reviews.csv` in your Google Drive and update the file path in the notebook if your folder structure is different.

## Tools and Libraries

- Python
- Pandas – data loading, cleaning, and transformation
- NumPy – conditional operations and sentiment labels
- Matplotlib – visualizations
- Seaborn – rating distribution visualization
- NLTK – VADER sentiment analysis and word tokenization

## Analysis Workflow

### 1. Data Loading and Initial Inspection

- Import the required Python libraries.
- Download the required NLTK resources: `vader_lexicon`, `punkt_tab`, and `stopwords`.
- Load the CSV dataset into a Pandas DataFrame.
- Inspect the dataset structure, column information, and rating statistics.

### 2. Data Cleaning

- Standardize column names by trimming spaces, converting them to lowercase, and replacing spaces with underscores.
- Rename the columns to consistent names such as `review_id`, `review`, `ratings`, and `review_date`.
- Convert the review date column to a datetime data type.
- Inspect missing values.
- Fill missing review text with a rating-based experience label where applicable.
- Remove duplicate records using the review ID.

### 3. Data Transformation

Create a `review_type` column based on the rating:

- Rating below 2: `Negative Review`
- Rating up to 3.5: `Neutral Review`
- Rating above 3.5: `Positive Review`

The notebook uses this column to group and compare review counts.

### 4. Exploratory Data Analysis (EDA)

- Generate descriptive statistics for the cleaned dataset.
- Examine the distribution of review ratings.
- Count reviews by `review_type`.
- Visualize the number of positive, negative, and neutral reviews.

### 5. Sentiment Analysis with VADER

- Initialize NLTK's `SentimentIntensityAnalyzer`.
- Calculate the VADER compound sentiment score for each review.
- Create a `sentiment_score` column.
- Classify sentiment using the compound score:
  - Score greater than `0.05`: Positive
  - Score below `-0.05`: Negative
  - Otherwise: Neutral
- Store the resulting label in a `sentiment` column.

### 6. Negative Review Analysis

- Filter the dataset to obtain negative reviews.
- Tokenize the review text using NLTK's `word_tokenize`.
- Count frequently occurring words in negative reviews.
- Plot the most common words to explore recurring terms in negative feedback.

### 7. Time-Series Analysis

- Group reviews by review date.
- Count the number of reviews over time.
- Plot review counts to observe how review activity changes across the available dates.

## Key Outputs

The notebook produces:

- A cleaned review dataset
- Rating-based review categories
- VADER compound sentiment scores and sentiment labels
- A chart showing review counts by review category
- A chart of common words in negative reviews
- A time-series plot of review activity

## How to Run

1. Open the notebook in Google Colab.
2. Upload or mount Google Drive.
3. Make sure `chatgpt_reviews.csv` is available at the path used in the notebook.
4. Run the notebook cells in order.
5. Allow NLTK to download the required resources when prompted.

## Notes and Limitations

- The `review_type` column is based on numerical ratings; it is not the same as text-based sentiment.
- VADER sentiment is calculated from review text and may differ from the rating-based category.
- Frequent words in negative reviews help explore recurring language, but word frequency alone does not identify the cause of a complaint.
- The time-series analysis shows review volume over time; it does not, by itself, measure changes in sentiment over time.
- The notebook's results depend on the dataset and the cleaning steps applied.

## Project Structure

```text
ChatGPT-Review-Analysis/
├── chatgpt_review_analysis.ipynb
├── chatgpt_reviews.csv
└── README.md
```
