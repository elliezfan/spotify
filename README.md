# Spotify Data Engineer Project
#### This is a data engineer project covering data extraction, loading, transforming, modeling, warehousing and visulization utilizing all open source tools.
#### The goal of the project is to build data warehouses on basis of the historic Spotify datasets with 16+ million data points, develop data marts from the warehouses for data analytics on the most popular Spotify artists with their genres and tracks' features, and finally present the insights in data visulizations.
# Technologies
* Ubuntu 20.04.2 LTS
* Python 3.8.10
* PostgreSQL 12.7
* Google Bigquery
* [Meltano](https://meltano.com/docs/) 1.77.0
* [dbt](https://www.getdbt.com/)
* Apache Superset

# Data
The original data comes from [here](https://www.kaggle.com/yamaerenay/spotify-dataset-19212020-160k-tracks)
* tracks.csv (audio features of tracks, 600k rows)
* artists.csv (popularity metrics of artists, 1.1M rows)

# Process
1. Data extracting and loading
