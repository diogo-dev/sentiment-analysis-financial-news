<img src="petrobas.jpg" alt="Petrobras" width=800 />

# Financial News Sentiment Analysis Project

This project analyzes the sentiment of financial news articles related to Petrobras (PETR4, PETR3) and correlates it with stock returns using two different sentiment analysis approaches.

## Project Overview

The project extracts financial news from Brazilian websites, processes them, and applies two sentiment analysis models to evaluate their correlation with stock market returns.

## Project Steps

### 1. Extract News from Websites

- Extract financial news articles related to PETR4 from Brazilian financial websites
- Target sources: InfoMoney and other financial news platforms
- Use web scraping with Selenium and BeautifulSoup
- Apply Google search filters to target specific date ranges (2020-2024)
- Search format: `PETR4 site:infomoney.com.br after:YYYY-01-01 before:YYYY-12-31`
- Extract news metadata: title, date, content, and source

**Output:** CSV files containing news data by year (2020, 2021, 2023, 2024)

### 2. Preprocessing

- Load news data from CSV files
- Text cleaning and normalization:
  - Remove special characters and extra whitespace
  - Tokenization using spaCy
  - Lemmatization to reduce words to their root forms
  - Remove custom stopwords (articles, prepositions, pronouns, etc.)
- Prepare text data for sentiment analysis models

### 3. Create the Loughran & McDonald (L&M) Dictionary Model

- Load the Loughran-McDonald Master Dictionary (1993-2024)
- Translate the English financial sentiment dictionary to Portuguese
- Create lists of positive and negative financial terms
- Apply dictionary-based sentiment scoring:
  - Count positive and negative words in each news article
  - Calculate sentiment polarity scores
  - Classify news as positive, negative, or neutral based on word counts

### 4. Create the XLM-RoBERTa Model

- Fine-tune the `xlm-roberta-base` transformer model for sentiment analysis
- Use a pre-labeled Portuguese sentiment dataset for training
- Configure training parameters:
  - Tokenization with XLM-RoBERTa tokenizer
  - Set up sequence classification (positive/negative/neutral)
  - Train with appropriate hyperparameters (learning rate, epochs, batch size)
- Save the fine-tuned model for inference
- Apply the model to classify sentiment in financial news articles
- Generate sentiment labels and confidence scores for each article

### 5. Perform Correlation Analysis

- Merge sentiment scores with stock return data
- Calculate correlations between:
  - L&M dictionary sentiment scores and stock returns
  - XLM-RoBERTa sentiment scores and stock returns
- Analyze correlations across different time periods:
  - Daily, weekly, monthly, and quarterly aggregations
  - Test with different time lags (same day, 1-day lag, etc.)
- Statistical significance testing (p-values)
- Visualize correlation trends over time
- Compare performance of both sentiment analysis models

## Files in the Repository

- `Scrapping.ipynb` - Web scraping and news extraction notebook
- `SentimentAnalysis.ipynb` - Preprocessing, modeling, and correlation analysis notebook
- `noticias_final_2020.csv` - News data for 2020
- `noticias_final_2021.csv` - News data for 2021
- `noticias_final_2023.csv` - News data for 2023
- `noticias_final_2024.csv` - News data for 2024

## Technologies Used

- **Python** - Main programming language
- **Web Scraping:** Selenium, BeautifulSoup, Requests
- **NLP:** spaCy, Transformers (Hugging Face)
- **Machine Learning:** XLM-RoBERTa, PyTorch
- **Data Analysis:** Pandas, NumPy
- **Statistics:** SciPy (correlation analysis)
- **Visualization:** Matplotlib, Seaborn

## Results

The project evaluates which sentiment analysis approach (dictionary-based vs. transformer-based) shows stronger correlation with actual stock returns, providing insights into the predictive power of news sentiment in the Brazilian financial market.
