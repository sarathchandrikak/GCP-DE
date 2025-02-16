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

* Send sample message to pubsub from Command Line (Also can publish messages from UI)

          for i in {1..10}
          do
            gcloud pubsub topics publish [TOPIC_NAME] --message '[BIQQUERY_SCHEMA_FORMAT]'
            sleep 1
           done

Examaple:

        for i in {1..10}
        do
          gcloud pubsub topics publish streaming-pubsubtobq --message '{"data": "Sample Input Data '"$i"'"}'
          sleep 1
        done

* Query to see pubsub data in BigQuery (Make sure dataflow job is up and running to send data into BigQuery Table)

        bq query --nouse_legacy_sql 'SELECT * FROM `[PROJECT_ID].[DATASET_ID].[TABLE_NAME]` LIMIT 10'
        bq query --nouse_legacy_sql 'SELECT * FROM `dataflow-pipeline-446610:streaming_data_bq.stream_pubsub_tobq` LIMIT 10'

  
If Pub/Sub data fails, it gets updated to [TABLE_NAME]_error_records





