---
description: Details for setting up FSM calculator sevice
---

# FSM Calculator

## Overview <a href="#overview" id="overview"></a>

FSM calculator is a system that enables the FSM admin to create billing slabs for the FSM application(s) with different combinations of property type, slum, tank and capacity.

It generates the demand after calculating the charges for the given application using the billing slab already configured. This document contains the details on how to set up the FSM calculator service, describes the functionalities it provides, and  details the enhancements made to the FSM calculator service.

## Pre-requisites

Before you proceed with the configuration, make sure the following pre-requisites are met:&#x20;

* Java 8
* Kafka server is up and running
* egov-persister service is running and has fsm-calculator-persister config path added in it
* PSQL server is running and database is created to store FSM Application data
* The following services should be up and running-

&#x20;      \- egov-perister

&#x20;      \- egov-mdms

&#x20;      \- fsm

&#x20;      \- billing-service

## Key Functionalities <a href="#key-functionalities" id="key-functionalities"></a>

* FSM Admin an Employee of ULB with FSM Admin role can create, update billing slab(s)
* ULB Employee with FSM\_CREATOR and FSM\_EDITOR can search billing slab(s)
* ULB Employee Citizen can file, track and rate the application for cleaning septic tank
* ULB Employee can get the estimate for FSM Application
* FSM service internally call fsm-calculator to generate a demand
* Vehicle type check has been removed from calculator service and bill amount is calculated based on the number of trips entered while submitting the FSM application.
* Bill amount is calculated based on the number of trips entered while updating the number of trips on the FSM application.
* Added validation for advance payment with the configuration.
* Added validation for max total advance payment.
* Added cancellation charges for canceling the application .
* Validation before completing the request with the payment.
* Minimum part payment is configural, that is, it should be fixed or it should be percentage calculation. The calculation should be done based on the MDMS configuration value.
* Minimum cancellation fee is configural, that is, it should be fixed or percentage calculation. The calculation should be done based on the MDMS configuration value.

## Deployment Details <a href="#deployment-details" id="deployment-details"></a>

1. Deploy the latest version of FSM.
2. Add fsm-calculator-persister.yml file in the config folder in GIT, and add that path in persister (the file path is to be added in environment yaml file in param called persist-yml-path).

## Configuration Details <a href="#configuration-details" id="configuration-details"></a>

#### MDMS Configuration

FSM MDMS Configuration is sufficient.

#### Business Service / Workflow Configuration

NA

#### Actions & Role Action Mapping

**Actions**

```
[
  {
    "id": {{PLACEHOLDER1}},
    "name": "FSM BillingSlab Create",
    "url": "/fsm-calculator/v1/billingSlab/_create",
    "displayName": "FSM BillingSlab Create",
    "orderNumber": 1,
    "parentModule": "",
    "enabled": false,
    "serviceCode": "",
    "code": "null",
    "path": ""
  },
  {
    "id": {{PLACEHOLDER2}},
    "name": "FSM BillingSlab Update",
    "url": "/fsm-calculator/v1/billingSlab/_update",
    "displayName": "FSM BillingSlab Update",
    "orderNumber": 1,
    "parentModule": "",
    "enabled": false,
    "serviceCode": "",
    "code": "null",
    "path": ""
  },
  {
    "id": {{PLACEHOLDER3}},
    "name": "FSM BillingSlab Search",
    "url": "/fsm-calculator/v1/billingSlab/_search",
    "displayName": "FSM BillingSlab Search",
    "orderNumber": 1,
    "parentModule": "",
    "enabled": false,
    "serviceCode": "",
    "code": "null",
    "path": ""
  },
  {
    "id": {{PLACEHOLDER4}},
    "name": "FSM Estimate",
    "url": "/fsm-calculator/v1/_estimate",
    "displayName": "FSM Estimate",
    "orderNumber": 1,
    "parentModule": "",
    "enabled": false,
    "serviceCode": "",
    "code": "null",
    "path": ""
  }
]

{
  "id": {{PLACEHOLDER5}},
  "name": "FSM Advance Balance Calculation",
  "url": "/fsm-calculator/v1/_advanceBalanceCalculate",
  "displayName": "FSM Advance Balance Calculation",
  "orderNumber": 1,
  "parentModule": "",
  "enabled": false,
  "serviceCode": "",
  "code": "null",
  "path": ""
},
{
  "id": {{PLACEHOLDER6}},
  "name": "FSM Cancellation Fee Calculation",
  "url": "/fsm-calculator/v1/_cancellationFee",
  "displayName": "FSM Advance Balance Calculation",
  "orderNumber": 1,
  "parentModule": "",
  "enabled": false,
  "serviceCode": "",
  "code": "null",
  "path": ""
}
```

**Role Action Mapping**

```
[
  {
    "rolecode": "FSM_ADMIN",
    "actionid": "{{PLACEHOLDER1}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_ADMIN",
    "actionid": "{{PLACEHOLDER2}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_CREATOR_EMP",
    "actionid": "{{PLACEHOLDER3}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_EDITOR_EMP",
    "actionid": "{{PLACEHOLDER3}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_ADMIN",
    "actionid": "{{PLACEHOLDER3}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_DSO",
    "actionid": "{{PLACEHOLDER3}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_CREATOR_EMP",
    "actionid": "{{PLACEHOLDER4}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_EDITOR_EMP",
    "actionid": "{{PLACEHOLDER4}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_ADMIN",
    "actionid": "{{PLACEHOLDER4}}",
    "actioncode": "",
    "tenantId": "pb"
  }
]

{
  "rolecode": "CITIZEN",
  "actionid": {{PLACEHOLDER3}},
  "actioncode": "",
  "tenantId": "pb"
} ,
{
  "rolecode": "CITIZEN",
  "actionid": {{PLACEHOLDER5}},
  "actioncode": "",
  "tenantId": "pb"
},
{
  "rolecode": "FSM_EDITOR_EMP",
  "actionid": {{PLACEHOLDER5}},
  "actioncode": "",
  "tenantId": "pb"
},
{
  "rolecode": "FSM_CREATOR_EMP",
  "actionid": {{PLACEHOLDER6}},
  "actioncode": "",
  "tenantId": "pb"
},
```

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

### Data Setup <a href="#data-setup" id="data-setup"></a>

#### Billing Slab Setup <a href="#billing-slab-setup" id="billing-slab-setup"></a>

Create billing slab with combination of PropertyType refer values form[ PropertyType Mdms](https://github.com/egovernments/egov-mdms-data/blob/DEV/data/pb/FSM/PropertyType.json), Slum (YES/NO), capacityFrom and capacityTo refers to Vehicle Tank Capacity.

Sample Curl

```
curl --location --request POST 'http://localhost:9098/fsm-calculator/v1/billingSlab/_create' \
--header 'Content-Type: application/json' \
--data-raw '{
    "RequestInfo": {
        "apiInfo": {
            "id": "string",
            "version": "string",
            "path": "string"
        },
        "deviceDetail": {
            "id": "string",
            "signature": "string"
        },
        "ts": 0,
        "action": "string",
        "key": "string",
        "msgId": "string",
        "requesterId": "string",
        "authToken": "a35b5ba7-2d5f-4272-8a67-0303cfab2c9f"
    },
   "billingSlab":{
          
            "tenantId": "pb.amritsar",
            "capacityFrom": 1000.00,
            "capacityTo": 50000.00,
            "propertyType": "RESIDENTIAL.ROW_HOUSES",
            "slum": "NO",
            "price": 9000.00,
            "status": "ACTIVE"
        },
    "workflow": null
}'
```

## Integration <a href="#integration" id="integration"></a>

### Integration Scope <a href="#integration-scope" id="integration-scope"></a>

The FSM-calculator will be integrated with the FSM application. The FSM application internally will invoke the fsm-calculator service to calculate and generate demand for the charges.

### Integration Benefits <a href="#integration-benefits" id="integration-benefits"></a>

* The calculation and demand generation logic will be separated from the FSM service. For each implementation, the calculation implementation can be changed, if required, without modifying the FSM service.

### Steps to Integration <a href="#steps-to-integration" id="steps-to-integration"></a>

1. FSM application to call fsm-calulator/v1/\_calculate to calculate and generate the demand for the fsm application.
2. ULB employee can call fsm-calculator/v1/\_estimate to get the estimates for the fsm application.
3. ULB Employee can create billing slab calling fsm-calculator/v1/billingSlab/\_create
4. ULB employee can update billing slab calling fsm-calculator/v1/billingSlab/\_update
5. ULB Employee can search billing slab calling fsm-calculator/v1/billingSlab/\_search
6. FSM application to call fsm-calculator/v1/\_cancellationFee to calculate cancellation charge based on the configuration data, that is, either it will be fixed or it will be a percentage.

FSM application to call fsm-calculator/v1/\_advanceBalanceCalculate to calculate advance charge based on the configuration data, that is, either it will be fixed or a percentage.

## Interaction Diagram <a href="#interaction-diagram" id="interaction-diagram"></a>

TBD

## Reference Docs <a href="#reference-docs" id="reference-docs"></a>

### Doc Links <a href="#doc-links" id="doc-links"></a>

| Workflow Technical Document         | <p> </p><p><a href="https://digit-discuss.atlassian.net/wiki/spaces/DD/pages/664174657">Workflow Service</a></p>                                                     |
| ----------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| User Technical Document             | [User Service](https://digit-discuss.atlassian.net/wiki/spaces/DD/pages/669450371)                                                                                   |
| MDMS Technical Document             | NEEDS TO BE UPDATED                                                                                                                                                  |
| IDGen Technical Document            | NEEDS TO BE UPDATED                                                                                                                                                  |
| Localization Technical Document     | NEEDS TO BE UPDATED                                                                                                                                                  |
| Persister Technical Document        | NEEDS TO BE UPDATED                                                                                                                                                  |
| SMS Notification Technical Document | NEEDS TO BE UPDATED                                                                                                                                                  |
| API Contract                        | [API Contract](https://editor.swagger.io/?url=https://raw.githubusercontent.com/egovernments/DIGIT-OSS/master/municipal-services/docs/fsm/Fsm\_Apply\_Contract.yaml) |
| Postman Scripts                     | [Postman Scripts](https://www.getpostman.com/collections/8b9eb951a810486f41a4)                                                                                       |

### API List <a href="#api-list" id="api-list"></a>

####

| Title                                       | Link                                                                                                                                                                                                                                                           |
| ------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| fsm-calulator/v1/\_calculate                | [https://www.getpostman.com/collections/8b9eb951a810486f41a4](https://www.getpostman.com/collections/8b9eb951a810486f41a4)                                                                                                                                     |
| fsm-calculator/v1/\_estimate                | [https://www.getpostman.com/collections/8b9eb951a810486f41a4](https://www.getpostman.com/collections/8b9eb951a810486f41a4)                                                                                                                                     |
| fsm-calculator/v1/billingSlab/\_create      | [https://www.getpostman.com/collections/8b9eb951a810486f41a4](https://www.getpostman.com/collections/8b9eb951a810486f41a4)                                                                                                                                     |
| fsm-calculator/v1/billingSlab/\_update      | [https://www.getpostman.com/collections/8b9eb951a810486f41a4](https://www.getpostman.com/collections/8b9eb951a810486f41a4)                                                                                                                                     |
| fsm-calculator/v1/billingSlab/\_search      | [https://www.getpostman.com/collections/8b9eb951a810486f41a4](https://www.getpostman.com/collections/8b9eb951a810486f41a4)                                                                                                                                     |
| fsm-calculator/v1/\_cancellationfee         | [https://api.postman.com/collections/23418568-77e3f5fb-dd9d-4f05-92e7-b15dcbeecffe?access\_key=PMAT-01GN93ZP6B68E0T5TZ62GR02W0](https://api.postman.com/collections/23418568-77e3f5fb-dd9d-4f05-92e7-b15dcbeecffe?access\_key=PMAT-01GN93ZP6B68E0T5TZ62GR02W0) |
| fsm-calculator/v1/\_advancebalancecalculate | [https://api.postman.com/collections/23418568-77e3f5fb-dd9d-4f05-92e7-b15dcbeecffe?access\_key=PMAT-01GN93ZP6B68E0T5TZ62GR02W0](https://api.postman.com/collections/23418568-77e3f5fb-dd9d-4f05-92e7-b15dcbeecffe?access\_key=PMAT-01GN93ZP6B68E0T5TZ62GR02W0) |

&#x20;
