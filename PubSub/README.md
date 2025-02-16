# Pub/Sub, DataFlow, Bigquery Streaming Data Pipeline



Commands for creating bucket in GCS 

* Authenticate to google cloud

        gcloud auth login
* Set Google Cloud Project

      gcloud config set project [PROJECT_ID]
* Enable all APIs to use for the project, In this we are using Google Cloud Storage, Google BigQuery, Dataflow, PubSub

      gcloud services enable \
              storage.googleapis.com \
              bigquery.googleapis.com \
              pubsub.googleapis.com \
              dataflow.googleapis.com  
* Create bucket

      gsutil mb -l US gs://[BUCKET_NAME]/
* Create Temp Folder to store Dataflow logs inside this bucket

      gsutil cp /dev/null gs://[BUCKET_NAME]/temp/.empty
* Create Dataset in Bigquery

      bq mk --dataset [PROJECT_ID]:[DATASET_NAME]
* To get Dataset Id from bigquery

      bq show --format=prettyjson [PROJECT_ID]:[DATASET_ID]
* Create Table in Bigquery

      bq mk --table [PROJECT_ID]:[DATASET_ID].[TABLE_NAME] [SCHEMA](ColName:dtype)
* Create pub/sub topic

      gcloud pubsub topics create [TOPIC_NAME]
* Create subscription for topic

      gcloud pubsub subscriptions create [SUBSCRIPTION_NAME] --topic=[TOPIC_NAME]
* Create dataflow job that uses Stream Data PubSub to BigQuery template, reads data from bucket, writes temp logs to a folder in bucket and connects the BigQuery table

      gcloud dataflow jobs run my-dataflow-job \
        --gcs-location gs://dataflow-templates/latest/PubSub_to_BigQuery \
        --region us-central1 \
        --parameters inputTopic=projects/[PROJECT_ID]/topics/[TOPIC_NAME],outputTable=[PROJECT_ID]:[DATASET_ID].[TABLE_NAME] \
        --project [PROJECT_ID] \
        --temp-location gs://[BUCKET_NAME]/temp/
  
