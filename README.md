# AE-Bootcamp-Capstone-Project

# Analyzing Earnings Surprises and News Sentiment

## Problem Statement

In the volatile world of financial markets, investors and analysts are constantly seeking ways to gain an edge in predicting stock performance. Two critical factors that can significantly impact stock prices are earnings surprises and news sentiment. This project aims to analyze the relationship between earnings surprises, news sentiment, and subsequent stock price movements, providing valuable insights for investment decision-making.

## Project Scope and Datasets

This project will combine earnings surprise data with news sentiment analysis to create a comprehensive view of market dynamics. We will use the following datasets:

1. **Earnings Sentiment Dataset**
   - Source: Hugging Face (Financial Modeling Prep API)
   - Format: JSON
   - Estimated rows: ~500,000 (considering quarterly earnings for 5,000 stocks over 25 years)

2. **News Sentiment Dataset**
   - Source: Hugging Face (SOV.AI News Sentiment API)
   - Format: CSV
   - Estimated rows: ~2,000,000 (daily sentiment scores for 4,000 stocks over 2 years)

   Additionally, we will utilize:
   - **News Sentiment Analysis Dataset**
     - Source: Hugging Face (fhamborg/roberta-targeted-sentiment-classification-newsarticles)
     - Format: JSON
     - This dataset provides targeted sentiment classification for news articles, which can enhance our analysis of how news affects stock prices.

Total estimated rows: 2,500,000+

## Use Cases

The processed data will be used for:

1. Creating an analytics table in a data warehouse for in-depth analysis and reporting.
2. Powering an interactive dashboard for real-time monitoring of earnings surprises and sentiment trends.
3. Training machine learning models to predict stock price movements based on earnings surprises and news sentiment.

## Tech Stack and Tools

1. **Data Extraction and Processing**:
   - Python (pandas, requests): For data fetching, cleaning, and transformation.
   - Apache Airflow: For orchestrating the data pipeline and scheduling regular updates.

2. **Data Storage**:
   - PostgreSQL: As the primary relational database for structured data storage.
   - Amazon S3: For storing raw data files and backups.

3. **Data Analysis and Visualization**:
   - Jupyter Notebooks: For exploratory data analysis and prototyping.
   - Plotly Dash: For building an interactive web-based dashboard.

4. **Machine Learning**:
   - Scikit-learn: For building predictive models.
   - TensorFlow: For more advanced deep learning models if required.

5. **Version Control and Collaboration**:
   - Git and GitHub: For version control and collaborative development.

Justification for choices:
- Python ecosystem provides robust libraries for data processing and analysis.
- Airflow ensures reliable and scalable data pipeline management.
- PostgreSQL offers a balance of performance and flexibility for structured data.
- Plotly Dash allows for the creation of interactive, web-based dashboards without extensive web development knowledge.
- The chosen ML libraries are industry-standard and well-documented.

## Analytical Frontend

The primary analytical frontend will be an interactive dashboard built with Plotly Dash. This dashboard will feature:

1. A heatmap showing the correlation between earnings surprises and subsequent stock price movements.
2. Time series plots of news sentiment for selected stocks or sectors.
3. A scatter plot comparing earnings surprises with average news sentiment in the week leading up to earnings announcements.
4. A table of stocks with the most significant recent changes in sentiment or largest earnings surprises.
5. Predictive indicators based on our machine learning models, showing potential buy/sell signals.

This dashboard will provide investors and analysts with a comprehensive tool to monitor market sentiment and earnings performance, enabling more informed decision-making in their investment strategies.

## Next Steps

1. Set up the development environment and install necessary dependencies.
2. Implement data extraction scripts for both APIs (Earnings Sentiment from Financial Modeling Prep API and News Sentiment from SOV.AI).
3. Design and create the PostgreSQL database schema.
4. Develop the Airflow DAGs for regular data updates.
5. Begin exploratory data analysis in Jupyter Notebooks using the datasets from Hugging Face.
6. Start building the Plotly Dash dashboard with initial visualizations.
7. Develop and train preliminary machine learning models based on the processed data.
8. Iterate on the dashboard and models based on initial findings.

## Conceptual Data Model

[Company]
    |
    |---- 1:N ----[Earnings Report]
    |                   |
    |                   |---- 1:1 ----[Earnings Surprise]
    |
    |---- 1:N ----[News Article]
                        |
                        |---- 1:1 ----[Sentiment Score]

[Date]
    |
    |---- 1:N ----[Earnings Report]
    |
    |---- 1:N ----[News Article]

[News Source]
    |
    |---- 1:N ----[News Article]

[Theme]
    |
    |---- 1:N ----[News Article]
