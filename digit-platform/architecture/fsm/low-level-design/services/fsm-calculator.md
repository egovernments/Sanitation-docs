---
description: Details for setting up FSM calculator sevice
---

# FSM Calculator

## Overview <a href="#overview" id="overview"></a>

FSM calculator is a system that enables the FSM admin to create billing slabs for the FSM application(s) with different combinations of property type, slum, tank, and capacity. It generates the demand after calculating the charges for the given application using the billing slab already configured.&#x20;

This document contains the details on how to set up the FSM calculator service, describes the functionalities it provides, and details the enhancements made to the FSM calculator service.

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

EXISTING

* FSM admin, an employee of ULB with FSM admin role can create, update billing slab(s).
* ULB employee with FSM\_CREATOR and FSM\_EDITOR can search billing slab(s).
* ULB employee citizen can file, track and rate the application for cleaning septic tank.
* ULB employee can get the estimate for the FSM application.
* FSM service internally call fsm-calculator to generate a demand.
* Vehicle type check has been removed from calculator service and the bill amount is calculated based on the number of trips entered while submitting the FSM application.

ENHANCEMENT

* Bill amount is calculated based on the number of trips entered while updating the number of trips in the FSM application.
* Added validation for advance payment with the configuration.
* Added validation for maximum total advance payment.
* Added cancellation charges for canceling the application.
* Validation before completing the request with the payment.
* Minimum part payment is configurable, that is, it should be fixed or percentage calculation, and the calculation should done based on the mdms config value.
* Minimum cancellation fee is configurable, that is, it should be fixed or percentage calculation, and the calculation should done based on the mdms config value.
* Demand generation process: Generating demand every time the trip is updates.
* Demand generation process: Added validation not to complete the application from the ULB side before completing the payment.

### Data Setup <a href="#data-setup" id="data-setup"></a>

#### Billing Slab Setup <a href="#billing-slab-setup" id="billing-slab-setup"></a>

Create billing slab with combination of PropertyType, refer values from[ PropertyType Mdms](https://github.com/egovernments/egov-mdms-data/blob/DEV/data/pb/FSM/PropertyType.json), Slum (YES/NO), capacityFrom and capacityTo refers to the Vehicle Tank Capacity.

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

FSM application to call fsm-calculator/v1/\_advanceBalanceCalculate to calculate the advance charge based on the configuration data, that is, either it will be fixed or a percentage.

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
