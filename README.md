# Spotify Data Engineer Project
#### This is a data engineer project covering data extraction, loading, transforming, modeling, warehousing and visulization utilizing all open source tools.
#### The goal of the project is to build data warehouses on basis of the historic Spotify datasets with 17+ million data points, develop data marts from the warehouses for data analytics on the most popular Spotify artists with their genres and tracks' features, and finally present the insights in data visulizations.
# Technologies
* Ubuntu 20.04.2 LTS
* Python 3.8.10
* PostgreSQL 12.7
* Google Bigquery
* [Meltano](https://meltano.com/docs/) 1.77.0
* [dbt](https://www.getdbt.com/) 0.19.2
* Apache Superset

# Data
The original data comes from [here](https://www.kaggle.com/yamaerenay/spotify-dataset-19212020-160k-tracks)
* tracks.csv (audio features of tracks, 600k rows)
* artists.csv (popularity metrics of artists, 1.1M rows)

# Process
1. Data extracting and loading (`meltano.yml` under `meltano` folder):
   * [tap-csv](https://hub.meltano.com/extractors/csv): extract raw data from csv files
   * [target-postgre](https://hub.meltano.com/loaders/postgres): load raw data extracted into the local PostgreSQL database
   * [target-bigquery](https://hub.meltano.com/loaders/bigquery): load raw data extracted into Google BigQuery on the cloud
2. Data transformation in dbt (`dbt` and `dbt_bigquery` folders):
   Transformed raw data in PostgreSQL and BigQuery seperately in `dbt` and `dbt_bigquery` projects.
   * `dbt_project.yml`: defines the structure of the dbt project
   * `models` folder:
     * staging: handle the initial data transformation that will be reflected in all downstream data models
     * analysis: handle further data transformation on basis of the results generated from staging to build data marts for BI use
   ![dbt server](https://github.com/elliezfan/spotify/blob/main/pic/dbt%20server.png)
   ![linear graph](https://github.com/elliezfan/spotify/blob/main/pic/linear%20relationship.png)
   
3. Data visulization in Apache Superset:
   ![superset1](https://github.com/elliezfan/spotify/blob/main/pic/superset1.png)
   ![superset2](https://github.com/elliezfan/spotify/blob/main/pic/superset2.png)

# Room for improvements
* Get incremental data load using [Spotify APIs](https://developer.spotify.com/documentation/web-api/reference/) to feed data warehouses with fresh data periodically
* Get data in other scopes like users, playlists, markets etc. to broaden the spectrum of the data warehouses as well as benifiting the business analytics user cases followed

# Sources
Special thanks to the below links for the project idea inspiration and the tutorials:
* https://towardsdatascience.com/data-stacks-for-fun-nonprofit-part-iii-dcfd46da9f9f
* https://www.startdataengineering.com/post/dbt-data-build-tool-tutorial/
* Data Source: https://www.kaggle.com/yamaerenay/spotify-dataset-19212020-160k-tracks
