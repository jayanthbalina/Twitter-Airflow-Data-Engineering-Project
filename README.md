# Twitter ETL Pipeline Project

## Project Overview
The goal of this project is to build an ETL (Extract, Transform, Load) pipeline that gathers tweets from a specific user account, transforms the data for usability, and loads it into a storage system for further analysis. The pipeline is orchestrated using Apache Airflow, enabling automation, scheduling, and management of the data workflow.

## Key Components

### 1. Twitter Data Extraction
- **Library Used**: [Tweepy](https://www.tweepy.org/)
- **Authentication**: I authenticate with the Twitter API using the following credentials:
  - `access_key`
  - `access_secret`
  - `consumer_key`
  - `consumer_secret`
- **Data Extraction**: The pipeline extracts up to 200 tweets from the @elonmusk Twitter account, excluding retweets, and captures the full text of each tweet.

### 2. Data Transformation
The raw tweet data is refined to include only relevant fields:
- **user**: The username of the tweet author.
- **text**: The content of the tweet.
- **favorite_count**: The number of likes the tweet received.
- **retweet_count**: The number of retweets.
- **created_at**: The timestamp of the tweet.

This transformation step organizes the data into a structured format using a Pandas DataFrame, making it easier to work with.

### 3. Data Loading
- The refined tweets are saved as a CSV file named `refined_tweets.csv`.
- In a production environment, this CSV file could be uploaded to cloud storage, such as AWS S3, for further analysis or reporting.

### 4. Airflow Integration
- **Orchestration**: I use Apache Airflow to automate the entire ETL process.
- **DAG Creation**: A Directed Acyclic Graph (DAG) is created with a task that triggers the `run_twitter_etl()` function daily.
  - **Schedule**: `schedule_interval=timedelta(days=1)` ensures that the pipeline runs at regular intervals, automatically fetching the latest tweets and updating the dataset.

## Future Steps
- **Data Analysis**: Future expansions of the project can include analyzing the collected tweets, such as performing sentiment analysis, tracking trends over time, or exploring engagement metrics (likes and retweets).
- **Extended Data Gathering**: The ETL pipeline can be modified to gather data from multiple Twitter accounts or specific hashtags, enhancing its versatility as a social media analytics tool.

## Conclusion
This project enables the development of a fully automated ETL pipeline using Apache Airflow to collect and refine real-time Twitter data. The refined data can then be utilized for deeper analysis, providing valuable insights into social media activity and engagement.

## Skills and Technologies
- **Programming Language**: Python
- **Libraries**: Tweepy, Pandas
- **Data Orchestration**: Apache Airflow
- **Cloud Storage**: AWS S3 (optional for future use)
