# FSM Calculator devops setup

## Deployment Details <a href="#deployment-details" id="deployment-details"></a>

1. Deploy the latest version of FSM.
2. Add fsm-calculator-persister.yml file in the config folder in GIT, and add that path in persister (the file path is to be added in environment yaml file in param called persist-yml-path):

&#x20;      [https://github.com/egovernments/configs/blob/DEV/egov-persister/fsm-calculator-persister.yaml](https://github.com/egovernments/configs/blob/DEV/egov-persister/fsm-calculator-persister.yaml)



### **Infra Ops Configuration**

Configurations that we can manage through values.yml fsm-calculator in infraops repo are as follows. values.yml for fms-calculator can be found[ here](https://github.com/egovernments/eGov-infraOps/blob/master/helm/charts/municipal-services/fsm-calculator/values.yaml).

|                                                                            |                                         |                                          |
| -------------------------------------------------------------------------- | --------------------------------------- | ---------------------------------------- |
| **Description**                                                            | **name in values.yml**                  | **Current Value**                        |
| contextPath of the api’s                                                   | SERVER\_CONTEXTPATH                     | /fsm-calculator                          |
| Kafka Consumer Group                                                       | SPRING\_KAFKA\_CONSUMER\_GROUP\_ID      | fsm-calculator                           |
| kafka topic to which service push data to save new billing slab            | PERSISTER\_SAVE\_BILLING\_SLAB\_TOPIC   | save-fsm-billing-slab                    |
| kafka topic to which service push data to update the existing billing slab | PERSISTER\_UPDATE\_BILLING\_SLAB\_TOPIC | update-fsm-billing-slab                  |
| mdms service host                                                          | EGOV\_MDMS\_HOST                        | egov-mdms-service from egov-service-host |
| billing-service host                                                       | EGOV\_BILLINGSERVICE\_HOST              | billing-service from egov-service-host   |
| fsm service host                                                           | EGOV\_FSM\_HOST                         | fsm from egov-service-host               |

**Configurations sample in Values.yml**

```
 - name: SERVER_CONTEXTPATH
    value: /fsm-calculator
  - name: SPRING_KAFKA_CONSUMER_GROUP_ID
    value: fsm-calculator
  - name: PERSISTER_SAVE_BILLING_SLAB_TOPIC
    value: save-fsm-billing-slab
  - name: PERSISTER_UPDATE_BILLING_SLAB_TOPIC
    value: update-fsm-billing-slab
  - name: SPRING_KAFKA_PRODUCER_KEY_SERIALIZER
    value: org.apache.kafka.common.serialization.StringSerializer
  - name: SPRING_KAFKA_PRODUCER_VALUE_SERIALIZER
    value: org.springframework.kafka.support.serializer.JsonSerializer
  - name: EGOV_MDMS_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-mdms-service
  - name: EGOV_BILLINGSERVICE_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: billing-service
  - name: EGOV_FSM_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: fsm
```
