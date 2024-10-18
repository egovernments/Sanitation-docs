---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Legacy/Re-Indexing the PQM Data

## Overview

In this document, we will learn how to legacy index/re-index the pqm index



## **PQM-Inbox-Reindexing**

Pre-Requisuites

* Kubectl access to the required environment in which you want to run the re-indexing
* playground pod access
* Legacy index mapping/configuration done in the respective indexer-config ( in this case for pqm , legacy index conifiguration for pqm is done[ here](https://github.com/egovernments/configs/blob/UNIFIED-DEV/egov-indexer/egov-pqm-service.yml))

&#x20;

#### Postman Collection

Postman collection to re-index the data for PQM can be downloaded[ here](https://api.postman.com/collections/23418568-a2738a3b-aa91-432c-95da-04325f103364?access\_key=PMAT-01HETWJGD12W25NXJN5A47961M) .

### Steps to legacy-index PQM

1. After importing the postman collection downloaded from above section, you can find two request
2.
   1. pqm-services-legacy : This request helps to get the data from pqm/plainsearch api and push data to pqm-services-enriched topic by indexer service
   2. pqm-services-legacy-kafkaconnector : This is the request to create a connector which can listen to the pqm-application topic and push data to the elastic search with the new index pqm-application-enriched
3. Run the pqm-legacy-kafkaconnector request in the playground pod, which would create a connector which would intern start listening to the topic pqm-application-legacyindex-enriched-sink
4. Run the pqm-legacy request in the playground pod, which would call indexer service to initiate the process of fetching the data from plainsearch and push the data prepared according to the legacy-index mapping and push the data to the pqm-application-legacyindex-enriched-sink topic
5. Whole process would take some time, meanwhile you can search for the data in pqm-application-legacyindex-enriched index in the elastic search
6. we can go through the logs of the indexer pod, which would help to understand the job is done
7. Once the job is done, delete the kafka connector running the below curl in the playground\
   curl --location --request DELETE 'http://kafka-connect.kafka-cluster:8083/connectors/pqm-application-enriched-es-sink'
8. Once reindexing is completed, please verify the count in pqm-application index and pqm-application-legacyindex-enriched index, then copy the pqm-application-legacyindex-enriched index to pqm-application and delete pqm-application-legacyindex-enriched index.Please use below command for coping.

```
POST _reindex
{
  "source": {
    "index": "pqm-application-legacyindex-enriched"
  },
  "dest": {
    "index": "pqm-application"
  }
}
```





## **PQM-Service Re-Indexing**

### Pre-Requisuites

* Kubectl access to the required environment in which you want to run the re-indexing
* playground pod access
* Legacy index mapping/configuration done in the respective indexer-config ( in this case for pqm , legacy index conifiguration for pqm is done[ here](https://github.com/egovernments/configs/blob/UNIFIED-UAT/sanitation/egov-indexer/pqm-service-indexer.yml))

&#x20;

#### Postman Collection

Postman collection to re-index the data for PQM can be downloaded[ here](https://api.postman.com/collections/23418568-bc374798-b49d-4ed1-92b9-c0194c195aad?access\_key=PMAT-01HJ0MN7QPMYF2EZ0JQ21RKV8J) .

### Steps to legacy-index PQM

1. After importing the postman collection downloaded from above section, you can find two request
2.
   1. pqm-services-legacy : This request helps to get the data from pqm/plainsearch api and push data to pqm-services-enriched topic by indexer service
   2. pqm-services-legacy-kafkaconnector : This is the request to create a connector which can listen to the pqm-application topic and push data to the elastic search with the new index pqm-application-enriched
3. Run the pqm-services-legacy-kafkaconnector request in the playground pod, which would create a connector which would intern start listening to the topic pqm-service-index-enriched-sink
4. Run the pqm-services-legacy request in the playground pod, which would call indexer service to initiate the process of fetching the data from plainsearch and push the data prepared according to the legacy-index mapping and push the data to the pqm-service-index-enriched-sink topic
5. Whole process would take some time, meanwhile you can search for the data in pqm-service-legacyindex-enriched index in the elastic search
6. we can go through the logs of the indexer pod, which would help to understand the job is done
7. Once the job is done, delete the kafka connector running the below curl in the playground\
   curl --location --request DELETE 'http://kafka-connect.kafka-cluster:8083/connectors/pqm-service-index-enriched-es-sink0500'

7.Once reindexing is completed, please verify the count in pqm-service index and pqm-service-index-enriched index, then copy the pqm-service-index-enriched index to pqm-service and delete pqm-service-index-enriched index.Please use below command for coping.

```

POST _reindex
{
  "source": {
    "index": "pqm-service-index-enriched"
  },
  "dest": {
    "index": "pqm-service"
  }
}
```

## **Pqm-Anomaly-Reindexing**

### Pre-requisites

* Kubectl access to the required environment in which you want to run the re-indexing
* playground pod access
* Legacy index mapping/configuration done in the respective indexer-config ( in this case for pqm-Anomaly , legacy index conifiguration for pqm-Anomaly is done[ here](https://github.com/egovernments/configs/blob/UNIFIED-DEV/egov-indexer/pqm-anomaly-finder-indexer.yml))

&#x20;**Postman Collection**

Postman collection to re-index the data for pqm-Anomaly can be downloaded[ here](https://api.postman.com/collections/23418568-578edc92-504f-4401-b09c-7303883de441?access\_key=PMAT-01HG01Y3J4YBQE95MS5RCM423G) .

### Steps to legacy-index PQM-Anomaly

1. After importing the postman collection downloaded from above section, you can find two request
2.
   1. pqm-Anomaly-services-legacy : This request helps to get the data from pqm-Anomaly/plainsearch api and push data to pqm-Anomaly-services-enriched topic by indexer service
   2. pqm-anomaly-services-legacy-kafkaconnector : This is the request to create a connector which can listen to the pqm-anomaly-finder topic and push data to the elastic search with the new index pqm-anomaly-finder-enriched
3. Run the pqm-anomaly-services-legacy-kafkaconnector  request in the playground pod, which would create a connector which would intern start listening to the topic pqm-anomaly-finder-enriched-sink
4. Run the pqm-Anomaly-services-legacy request in the playground pod, which would call indexer service to initiate the process of fetching the data from plainsearch and push the data prepared according to the legacy-index mapping and push the data to the pqm-Anomaly-application-enriched-sink topic
5. Whole process would take some time, meanwhile you can search for the data in pqm-anomaly-finder-enriched index in the elastic search
6. we can go through the logs of the indexer pod, which would help to understand the job is done
7. Once the job is done, delete the kafka connector running the below curl in the playground\
   curl --location --request DELETE 'http://kafka-connect.kafka-cluster:8083/connectors/pqm-Anomaly-services-legacy-enriched-es-sink'
8. Once reindexing is completed, please verify the count in pqm-anomaly-finder index and pqm-anomaly-finder-enriched index, then copy the pqm-anomaly-finder-enriched index to pqm-anomaly-finder and delete pqm-anomaly-finder-enriched index.Please use below command for coping.

```
POST _reindex
{
  "source": {
    "index": "pqm-anomaly-finder-enriched"
  },
  "dest": {
    "index": "pqm-anomaly-finder"
  }
}
```
