# PQM Service

## Overview

The Process Quality Management (PQM) service will help users to create, update, and search for process quality monitoring tests. The service will evaluate the uploaded test values against benchmarks and produce result (FAIL/PASS) status. Test results will be further processed for anomaly analysis. The service can perform two types of test: Manual Test (Lab), and Automatic Test (IoT-based).\
\
[Low-level design](https://app.gitbook.com/o/-MEQmzNGXk5ajuZujG7E/s/LpfYJCGZoBEmcFf9yWTh/\~/changes/196/platform/architecture/pqm/low-level-design/services/pqm-service)

Functional Specification



## Configuration

Make changes in config accordingly and restart the egov-persister-service and egov-indexer-service.

1. egov-persister/pqm-persister.yaml - file [link](https://github.com/egovernments/configs/blob/UNIFIED-UAT/sanitation/egov-persister/pqm-persister.yaml)
2. egov-indexer/pqm-service-indexer.yml - file [link](https://github.com/egovernments/configs/blob/UNIFIED-UAT/sanitation/egov-indexer/pqm-service-indexer.yml)
3. Add path of indexer in the devOps (pqm-service-indexer.yml) - file [link](https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/environments/unified-dev.yaml#L345C3215-L345C3215)
4. Add path of persister in the devOps (pqm-persister.yaml) - file [link](https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/environments/unified-dev.yaml#L353)
5. Idgen config - file [link](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/pg/common-masters/IdFormat.json#L117C4-L120C6)
6. Add path of pdf data and format config files - PR [link](https://github.com/egovernments/DIGIT-DevOps/commit/f193a5213ff47769592c9818eb5f85dff55a2679) | [link](https://github.com/egovernments/DIGIT-DevOps/commit/171b055edad215f68bea4bfa8eecbefab52bac80)



## MDMS Configuration

## Role-Action Mapping&#x20;

Path: data/pg/ACCESSCONTROL-ACTIONS-TEST/actions-test.json

```
{
      "id": 325,
      "name": "Create PQM Application",
      "url": "/pqm-service/v1/_create",
      "displayName": "Apply PQM Appliacations",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "PQM",
      "code": "null",
      "path": ""
    },
    {
      "id": 326,
      "name": "Update PQM Application",
      "url": "/pqm-service/v1/_update",
      "displayName": "Update PQM Appliacations",
      "orderNumber": 1,
      "enabled": false,
      "serviceCode": "PQM",
      "code": "null",
      "path": ""
    },
   {
      "id": 327,
      "name": "Search PQM Application",
      "url": "/pqm-service/v1/_search",
      "displayName": "Search PQM Appliacations",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "PQM",
      "code": "null",
      "path": ""
    },
    {
      "id": 364,
      "name": "Create Plant User Mapping",
      "url": "/pqm-service/plant/user/v1/_create",
      "displayName": "Create plant-individual mapping",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "PQM",
      "code": "null",
      "path": ""
    },
    {
      "id": 365,
      "name": "Update Plant User Mapping",
      "url": "/pqm-service/plant/user/v1/_update",
      "displayName": "Update plant-individual mapping",
      "orderNumber": 1,
      "enabled": false,
      "serviceCode": "PQM",
      "code": "null",
      "path": ""
    },
    {
      "id": 366,
      "name": "Search Plant User Mapping",
      "url": "/pqm-service/plant/user/v1/_search",
      "displayName": "Search plant-individual mapping",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "PQM",
      "code": "null",
      "path": ""
    },
    {
      "id": 367,
      "name": "Schedule PQM Application",
      "url": "/pqm-service/v1/_scheduler",
      "displayName": "Schedule PQM Applications",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "PQM",
      "code": "null",
      "path": ""
    },
    {
      "id": 358,
      "name": "DSS Dashboard Config PQM",
      "url": "/dashboard-analytics/dashboard/getDashboardConfig/pqm",
      "parentModule": "",
      "displayName": "DSS",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "DSS",
      "code": "null",
      "path": ""
    },
     {
      "id": 21,
      "name": "Workflow search",
      "url": "/egov-workflow-v2/egov-wf/process/_search",
      "parentModule": "",
      "displayName": "Workflow search",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "egov-workflow-v2",
      "code": "null",
      "path": ""
    },
    {
    "id": 359,
    "name": "Event Search",
    "url": "/egov-user-event/v1/events/_search",
    "displayName": "Event Notification",
    "orderNumber": 1,
    "enabled": false,
    "serviceCode": "msea-event-notification",
    "code": "null",
    "path": ""
  },
  {
      "id": 331,
      "name": "Workflow transition",
      "url": "/egov-workflow-v2/egov-wf/process/_transition",
      "parentModule": "",
      "displayName": "Workflow transition",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "egov-workflow-v2",
      "code": "null",
      "path": ""
    },
       {
      "id": 351,
      "name": "Search PQM Application",
      "url": "/inbox/v2/_search",
      "displayName": "Search PQM Applications",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "PQM",
      "code": "null",
      "path": ""
    },
     {
      "id": 371,
      "name": "DSS Dashboard Charts",
      "url": "/dashboard-analytics/dashboard/getChartV2",
      "parentModule": "",
      "displayName": "DSS",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "DSS",
      "code": "null",
      "path": ""
    },
    {
      "id": 65,
      "name": "Inbox service V2",
      "url": "/inbox/v2/_search",
      "parentModule": "inbox-v2",
      "displayName": "Works inbox",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "inbox-v2",
      "code": "null",
      "path": ""
    },
    {
      "id": 371,
      "name": "DSS Dashboard Config PQM",
      "url": "/dashboard-analytics/dashboard/getDashboardConfig/pqm",
      "parentModule": "",
      "displayName": "DSS",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "DSS",
      "code": "null",
      "path": ""
    },
    {
      "id": 391,
      "name": "Download Pdf for PQM Application",
      "url": "/pqm-service/v1/_downloadPdf",
      "displayName": "Download Pdf for PQM Application",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "PQM",
      "code": "null",
      "path": ""
    }
```

Path :- data/pg/ACCESSCONTROL-ROLEACTIONS/roleactions.json

```
 {
      "rolecode": "PQM_TP_OPERATOR",
      "actionid": 371,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "PQM_ADMIN",
      "actionid": 371,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "FSM_DASHBOARD_VIEWER",
      "actionid": 371,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "SUPERUSER",
      "actionid": 371,
      "actioncode": "",
      "tenantId": "pg"
    },
      {
      "rolecode": "FSM_ADMIN",
      "actionid": 65,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "PQM_TP_OPERATOR",
      "actionid": 371,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "PQM_ADMIN",
      "actionid": 325,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "PQM_TP_OPERATOR",
      "actionid": 325,
      "actioncode": "",
      "tenantId": "pg"
    },
      {
      "rolecode": "PQM_ADMIN",
      "actionid": 326,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "PQM_TP_OPERATOR",
      "actionid": 326,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
        "rolecode": "PQM_ADMIN",
        "actionid": 327,
        "actioncode": "",
        "tenantId": "pg"
      },
      {
        "rolecode": "PQM_TP_OPERATOR",
        "actionid": 327,
        "actioncode": "",
        "tenantId": "pg"
     },
    {
      "rolecode": "PQM_ADMIN",
      "actionid": 364,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "FSM_ADMIN",
      "actionid": 364,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "FSM_ADMIN",
      "actionid": 365,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "PQM_ADMIN",
      "actionid": 365,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "PQM_ADMIN",
      "actionid": 366,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "PQM_TP_OPERATOR",
      "actionid": 366,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "FSM_ADMIN",
      "actionid": 366,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "PQM_CRONJOB_SCHEDULER",
      "actionid": 367,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "PQM_TP_OPERATOR",
      "actionid": 358,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "PQM_ADMIN",
      "actionid": 358,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "PQM_TP_OPERATOR",
      "actionid": 21,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "PQM_ADMIN",
      "actionid": 21,
      "actioncode": "",
      "tenantId": "pg"
    },
     {
      "rolecode": "EMPLOYEE",
      "actionid": 359,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "CITIZEN",
      "actionid": 359,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "PQM_ADMIN",
      "actionid": 359,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "PQM_TP_OPERATOR",
      "actionid": 359,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
     "rolecode": "PQM_TP_OPERATOR",
     "actionid": 331,
     "actioncode": "",
     "tenantId": "pg"
   },
   {
     "rolecode": "SUPERUSER",
       "actionid": 356,
     "actioncode": "",
     "tenantId": "pg"
   },
   {
       "rolecode": "PQM_ADMIN",
       "actionid": 21,
       "actioncode": "",
       "tenantId": "pg"
     },
     {
       "rolecode": "PQM_TP_OPERATOR",
       "actionid": 21,
       "actioncode": "",
       "tenantId": "pg"
     },
      {
      "rolecode": "PQM_ADMIN",
      "actionid": 351,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "PQM_TP_OPERATOR",
      "actionid": 351,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "PQM_ADMIN",
      "actionid": 391,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "PQM_TP_OPERATOR",
      "actionid": 391,
      "actioncode": "",
      "tenantId": "pg"
    }
    
```

Role.json

```json
 {
      "code": "PQM_CRONJOB_SCHEDULER",
      "name": "PQM CRONJOB SCHEDULER",
      "description": "Pqm Cronjob Scheduler"
    }
```

##

## I**nbox V2 Integration**

* Add the MDMS changes in the given path and restart the MDMS service.

&#x20;      Path: data/pg/inbox-v2/InboxConfiguration.json

&#x20;       File:  [Mdms file ](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/pg/inbox-v2/InboxConfiguration.json#L410C2-L495C1)

* Add the indexer file in the given path and restart the services .

&#x20;     Path: egov-indexer/egov-pqm-service.yml

&#x20;     File: file which need to add [click here](https://github.com/egovernments/configs/blob/UNIFIED-DEV/egov-indexer/egov-pqm-service.yml)\


## Steps to legacy-index PQM

For re-indexing, refer to this [link](https://app.gitbook.com/o/-MEQmzNGXk5ajuZujG7E/s/LpfYJCGZoBEmcFf9yWTh/\~/changes/144/product/treatment-quality-monitoring-tqm/pqm-technical-specification/legacy-re-indexing-the-pqm-data#pqm-inbox-reindexing).

#### Postman Collection

For re-indexing, refer to this [link](https://app.gitbook.com/o/-MEQmzNGXk5ajuZujG7E/s/LpfYJCGZoBEmcFf9yWTh/\~/changes/144/product/treatment-quality-monitoring-tqm/pqm-technical-specification/legacy-re-indexing-the-pqm-data#pqm-service-re-indexing).



## Deployment Details

1. Deploy the latest version of PQM.
2. Add pqm-persister.yml file in the config folder in git and add that path in persister (the file path is to be added in environment yaml file in param called persist-yml-path), and restart the egov-persister service.
3. If index are to be created, add the indexer config path in the indexer service (the file path is to be added in environment yaml file in param called egov-indexer-yaml-repo-path), and restart egov-indexer service.

**Devops setups for new environment**

Path: deploy-as-code/helm/charts/sanitation/pqm-service

[https://github.com/egovernments/DIGIT-DevOps/tree/unified-env/deploy-as-code/helm/charts/sanitation/pqm-service](https://github.com/egovernments/DIGIT-DevOps/tree/unified-env/deploy-as-code/helm/charts/sanitation/pqm-service)

[https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/environments/sanitation-uat.yaml#L138C5-L138C42](https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/environments/sanitation-uat.yaml#L138C5-L138C42)

Path: build/build-config.yml

<mark style="color:blue;">https://github.com/egovernments/SANITATION/commit/6e4db6ca9d4a52df1df5d4cb67a2df84a0bed420</mark>

Path: deploy-as-code/helm/charts/sanitation/pqm-anomaly-finder

<mark style="color:blue;">https://github.com/egovernments/DIGIT-DevOps/tree/unified-env/deploy-as-code/helm/charts/sanitation/pqm-anomaly-finder</mark>

[https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/environments/sanitation.yaml#L140C1-L141C1](https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/environments/sanitation.yaml#L140C1-L141C1)

Path: build/build-config.yml

<mark style="color:blue;">https://github.com/egovernments/SANITATION/commit/576b1bb9531a2080e039d17af9d3c6a6c63d76e7</mark>

## Business Service/Workflow Configuration

Create businessService (workflow configuration) using the /businessservice/\_create. Following is the product configuration for PQM:

```json
{
    "RequestInfo": {
        "apiId": "Rainmaker",
        "action": "",
        "did": 1,
        "key": "",
        "msgId": "20170310130900|en_IN",
        "requesterId": "",
        "ts": 1513579888683,
        "ver": ".01",
        "authToken": "71fc8bf6-4c3f-4bb3-af74-bc2fabf6252e",
        "userInfo": {{adduserInfo}}
    },
    "BusinessServices": [
        {
            "tenantId": "pg",
            "businessService": "PQM",
            "business": "pqm",
            "businessServiceSla": 432000000,
            "states": [
                {
                    "sla": null,
                    "state": null,
                    "applicationStatus": null,
                    "docUploadRequired": true,
                    "isStartState": true,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "action": "SCHEDULE",
                            "nextState": "SCHEDULED",
                            "roles": [
                                "PQM_ADMIN",
                                "PQM_TP_OPERATOR"

                            ]
                        }
                    ]
                },
                {
                    "sla": null,
                    "state": "SCHEDULED",
                    "applicationStatus": "SCHEDULED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "action": "SUBMIT_SAMPLE",
                            "nextState": "PENDINGRESULTS",
                            "roles": [
                              "PQM_ADMIN",
                                "PQM_TP_OPERATOR"
                            ]
                        }
                    ]
                },
                {
                    "sla": null,
                    "state": "PENDINGRESULTS",
                    "applicationStatus": "PENDINGRESULTS",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": false,
                    "actions": [
                        {
                            "action": "UPDATE_RESULT",
                            "nextState": "SUBMITTED",
                            "roles": [
                                "PQM_ADMIN",
                                "PQM_TP_OPERATOR"
                            ]
                        }
                    ]
                },
                {
                    "sla": null,
                    "state": "SUBMITTED",
                    "applicationStatus": "SUBMITTED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": true,
                    "isStateUpdatable": false,
                    "actions": null
                }
            ]
        }
    ]
}
```

##

## PQM Landing Page Charts&#x20;

File Path- [https://github.com/egovernments/configs/blob/UNIFIED-QA/egov-dss-dashboards/dashboard-analytics/ChartApiConfig.json](https://github.com/egovernments/configs/blob/UNIFIED-QA/egov-dss-dashboards/dashboard-analytics/ChartApiConfig.json)\
After adding the below changes, please restart dashboard-analytics.

```json
{ 
"pqmTestCompliance": {
    "chartName": "DSS_PQM_TEST_COMPLIANCE",
    "queries": [
      {
        "module": "PQM",
        "indexName": "pqm-service",
        "aggrQuery": "{\"size\":0,\"aggs\":{\"total_tests\":{\"cardinality\":{\"field\":\"Data.tests.testId.keyword\"}},\"wfStatus_submitted_count\":{\"filter\":{\"term\":{\"Data.tests.wfStatus.keyword\":\"SUBMITTED\"}}}}}",
        "requestQueryMap": "{\"plantCode\" : \"Data.tests.plantCode.keyword\",\"tenantId\" : \"Data.tests.tenantId\"}",
        "dateRefField": "Data.tests.@timestamp"
      }
    ],
    "chartType": "metric",
    "valueType": "percentage",
    "action": "percentage",
    "isRoundOff": true,
    "drillChart": "none",
    "aggregationPaths": [
      "wfStatus_submitted_count",
      "total_tests"
    ],
    "insight": {
      "chartResponseMap": "pqmTestCompliance",
      "action": "differenceOfNumbers",
      "upwardIndicator": "positive",
      "downwardIndicator": "negative",
      "textMessage": "$indicator$value% than last $insightInterval",
      "colorCode": "#228B22",
      "insightInterval": "year",
      "isRoundOff": true
    },
    "_comment": " PQM Percentage of Test Compliance"
  },
  
   "pqmAlerts": {
    "chartName": "PQM_ANOMALY_TYPE",
    "queries": [
      {
        "module": "PQM",
        "requestQueryMap": "{\"plantCode\" : \"Data.pqmAnomalys.plantCode.keyword\",\"tenantId\" : \"Data.pqmAnomalys.tenantId\"}",
        "dateRefField": "Data.pqmAnomalys.@timestamp",
        "indexName": "pqm-anomaly-finder",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"Data.tenantId.keyword\":\"pg.testing\"}}]}},\"aggs\":{\"Anomaly_type_lab_results\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.pqmAnomalys.anomalyType.keyword\":[\"LAB_RESULTS_NOT_AS_PER_BENCHMARK\"]}}]}},\"aggs\":{\"Count\":{\"value_count\":{\"field\":\"Data.pqmAnomalys.id.keyword\"}}}},\"Anomaly_type_test_result_not_submitted\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.pqmAnomalys.anomalyType.keyword\":[\"TEST_RESULT_NOT_SUBMITTED\"]}}]}},\"aggs\":{\"Count\":{\"value_count\":{\"field\":\"Data.pqmAnomalys.id.keyword\"}}}},\"TotalAlerts\":{\"value_count\":{\"field\":\"Data.pqmAnomalys.id.keyword\"}}}}}}"
      }
    ],
    "isMdmsEnabled": true,
    "isPostResponseHandler": true,
    "postAggregationTheory": "repsonseToDifferenceOfDates",
    "chartType": "xtable",
    "valueType": "number",
    "drillChart": "xBirthDownloadByUlb",
    "documentType": "_doc",
    "action": "",
    "plotLabel": "DDRs",
    "excludedColumns": [],
    "removedFields": [],
    "computedFields": [],
    "isRoundOff": true,
    "aggregationPaths": [
      "Anomaly_type_test_result_not_submitted",
      "Anomaly_type_lab_results",
      "TotalAlerts"
    ],
    "pathDataTypeMapping": [
      {
        "Anomaly_type_test_result_not_submitted": "number"
      },
      {
        "Anomaly_type_lab_results": "number"
      },
      {
        "TotalAlerts": "number"
      }
    ],
    "insight": {},
    "_comment": ""
  },
  
   "pqmPercentageOfTestResultsMeetingBenchmarks": {
    "chartName": "DSS_PQM_PERCENTAGE_OF_TEST_RESULTS_MEETING_BENCHMARKS",
    "queries": [
      {
        "module": "PQM",
        "indexName": "pqm-service",
        "aggrQuery": "{\"size\":0,\"aggs\":{\"PASSED_TESTS\":{\"filter\":{\"term\":{\"Data.tests.status.keyword\":\"PASS\"}}},\"SUBMITTED_TESTS\":{\"filter\":{\"term\":{\"Data.tests.wfStatus.keyword\":\"SUBMITTED\"}}}}}",
        "requestQueryMap": "{\"plantCode\" : \"Data.tests.plantCode.keyword\",\"tenantId\" : \"Data.tests.tenantId\"}",
        "dateRefField": "Data.tests.@timestamp"
      }
    ],
    "chartType": "metric",
    "valueType": "percentage",
    "action": "percentage",
    "isRoundOff": true,
    "drillChart": "none",
    "aggregationPaths": [
      "PASSED_TESTS",
      "SUBMITTED_TESTS"
    ],
    "insight": {
      "chartResponseMap": "pqmPercentageOfTestResultsMeetingBenchmarks",
      "action": "differenceOfNumbers",
      "upwardIndicator": "positive",
      "downwardIndicator": "negative",
      "textMessage": "$indicator$value% than last $insightInterval",
      "colorCode": "#228B22",
      "insightInterval": "year",
      "isRoundOff": true
    },
    "_comment": " PQM Percentage of Test Results Meeting Benchmarks"
  }
  }
```



