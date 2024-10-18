# FSM devops setups

## Deployment Details <a href="#deployment-details" id="deployment-details"></a>

1. Deploy the latest version of FSM.
2. Add fsm-persister.yml file in the config folder in git, add that path in persister (the file path is to be added in environment yaml file in param called persist-yml-path), and restart the egov-persister service.
3. If index are to be created, add the indexer config path in the indexer service (the file path is to be added in environment yaml file in param called egov-indexer-yaml-repo-path), and restart egov-indexer service.
4. path:- deploy-as-code/helm/charts/sanitation/fsm/values.yaml - [link](https://github.com/egovernments/DIGIT-DevOps/pull/2256/files)



#### **Infra-Ops Configuration**

Configurations that we can manage through values.yml fsm-calculator in infraops repo as follows:

|                                                                               |                                         |                                                |
| ----------------------------------------------------------------------------- | --------------------------------------- | ---------------------------------------------- |
| **Description**                                                               | **name in values.yml**                  | **Current Value**                              |
| id-gen host, to generate the application number                               | EGOV\_IDGEN\_HOST                       | egov-idgen from egov-service-host              |
| Kafka Consumer Group                                                          | SPRING\_KAFKA\_CONSUMER\_GROUP\_ID      | egov-fsm-service                               |
| kafka topic to which service push data to save new fsm application            | PERSISTER\_SAVE\_FSM\_TOPIC             | save-fsm-application                           |
| kafka topic to which service push data to save workflow status                | PERSISTER\_UPDATE\_FSM\_WORKFLOW\_TOPIC | update-fsm-workflow-application                |
| kafka topic to which service push data to update the existing fsm application | PERSISTER\_UPDATE\_FSM\_TOPIC           | update-fsm-application                         |
| mdms service host                                                             | EGOV\_MDMS\_HOST                        | egov-mdms-service from egov-service-host       |
| billing-service host                                                          | EGOV\_BILLINGSERVICE\_HOST              | billing-service from egov-service-host         |
| fsm-calculator service host                                                   | EGOV\_FSM\_CALCULATOR\_HOST             | fsm-calculator from egov-service-host          |
| workflow v2 service host                                                      | WORKFLOW\_CONTEXT\_PATH                 | egov-workflow-v2 from egov-service-host        |
| ui host, to return send the url of new application in sms notification        | EGOV\_UI\_APP\_HOST                     | egov-services-fqdn-name from egov-service-host |
| vendor service host, to get DSO details                                       | EGOV\_VENDOR\_HOST                      | vendor from egov-service-host                  |
| Vehicle service host, to get vehicle details and manage vehicleTrip           | EGOV\_VEHICLE\_HOST                     | vehicle from egov-service-host                 |
| Collection service host, to get the payment details                           | EGOV\_COLLECTION\_SERVICE\_HOST         | collection-services from egov-service-host     |
| localization service host, to get the locale data                             | EGOV\_LOCALIZATION\_HOST                | egov-localization from egov-service-host       |
| user service host, to get the locale data                                     | EGOV\_USER\_HOST                        | egov-user from egov-service-host               |
| pdf service host, to get the locale data                                      | EGOV\_PDF\_HOST                         | pdf-service from egov-service-host             |
| url shortening service host, to get the short url for the long once           | EGOV\_URL\_SHORTNER\_HOST               | egov-url-shortening from egov-service-host     |

**Sample values.yml**

```
- name: EGOV_IDGEN_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-idgen
  - name: EGOV_MDMS_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-mdms-service
  - name: EGOV_URL_SHORTNER_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-url-shortening
  - name: EGOV_PDF_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: pdf-service
  - name: EGOV_USER_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-user
  - name: EGOV_LOCATION_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-location
  - name: EGOV_LOCALIZATION_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-localization
  - name: EGOV_BILLINGSERVICE_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: billing-service
  - name: EGOV_COLLECTION_SERVICE_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: collection-services
  - name: EGOV_FSM_CALCULATOR_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: fsm-calculator
  - name: EGOV_VEHICLE_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: vehicle
  - name: EGOV_VENDOR_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: vendor
  - name: EGOV_UI_APP_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-config
        key: egov-services-fqdn-name
  - name: WORKFLOW_CONTEXT_PATH
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-workflow-v2
  - name: WORKFLOW_TRANSITION_PATH
    value: "egov-workflow-v2/egov-wf/process/_transition"
  - name: EGOV_IDGEN_FSM_APPLICATIONNUM_FORMAT
    value: "[CITY.CODE]-FSM-[cy:yyyy-MM-dd]-[SEQ_EGOV_FSM]"
  - name: SPRING_KAFKA_CONSUMER_GROUP_ID
    value: egov-fsm-service
  - name: PERSISTER_SAVE_FSM_TOPIC
    value: save-fsm-application
  - name: PERSISTER_UPDATE_FSM_TOPIC
    value: update-fsm-application
  - name: PERSISTER_UPDATE_FSM_WORKFLOW_TOPIC
    value: update-fsm-workflow-application


```

