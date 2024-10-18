# FSM-DSS Technical Documentation

## Overview

DSS has two sides to it: One being the process in which the data is pooled to ElasticSearch, and the other being the way it is fetched, aggregated, computed, transformed and sent across. As this revolves around a variety of data sets, there is a need for making this configurable so that, if a new scenario is introduced, then it is a configuration away from getting the newly-introduced scenario involved in this flow of process.

This document explains the steps on how to define the configurations for the analytics side of DSS for FSM.

## **What is analytics?**

**Analytics:** Micro-service that is responsible for building, fetching, aggregating, and computing the data on ElasticSearch to a consumable data response, which will be later used for visualisations and graphical representations.

### **Analytics Configurations**

Analytics contains multiple configurations. We need to add the changes related to FSM in this dashboard-analytics.\
Here is the location:[ ![](https://github.com/fluidicon.png)configs/egov-dss-dashboards/dashboard-analytics at qa · egovernments/configs](https://github.com/egovernments/configs/tree/qa/egov-dss-dashboards/dashboard-analytics)\
Below is a list of configurations that need to be changed to run FSM successfully.

1. Chart API Configuration
2. Master Dashboard Configuration
3. Role Dashboard Mappings Configuration

### **Description**

**Chart API Configuration**

Each visualisation has its own properties, and comes from different data sources (sometimes it is a combination of different data sources).

In order to configure each visualisation and their properties, we have a chart API configuration document. In this, the visualisation code, which happens to be the key, will have its properties configured as a part of configuration, and are easily changeable.

Here is the sample ChartApiConfiguration.json data for FSM.

```
  "fsmTotalrequest": {
    "chartName": "DSS_FSM_TOTAL_REQUESTS",
    "queries": [
      {
        "module": "FSM",
        "indexName": "fsm",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"Data.fsm.tenantId.keyword\":\"pb.testing\"}}]}},\"aggs\":{\"Total Application\":{\"value_count\":{\"field\":\"Data.fsm.@timestamp\"}}}}}}",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtCode\"}",
        "dateRefField": "Data.fsm.@timestamp"
      }
    ],
    "chartType": "metric",
    "valueType": "number",
    "action": "",
    "drillChart": "none",
    "aggregationPaths": [
      "Total Application"
    ],
    "insight": {
      "chartResponseMap" : "totalApplication",
      "action" : "differenceOfNumbers",
      "upwardIndicator" : "positive",
      "downwardIndicator" : "negative",
      "textMessage" : "$indicator$value% than last $insightInterval",
      "colorCode" : "#228B22",
      "insightInterval" : "year",
      "isRoundOff": true
    },
    "_comment": " FSM Total Applications"
  },
  "totalSludgeTreated": {
    "chartName": "DSS_FSM_TOTAL_SLUDGE_TREATED",
    "queries": [
      {
        "module": "FSM",
        "indexName": "vehicletrip",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"Data.vehicleTrip.tenantId.keyword\":\"pb.testing\"}}]}},\"aggs\":{\"Total Sludge Collection\":{\"sum\":{\"script\":{\"source\":\"(doc['Data.vehicleTrip.volumeCarried'].value)/1000.0\"}}}}}}}",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtCode\"}",
        "dateRefField": "Data.vehicleTrip.@timestamp"
      }
    ],
    "chartType": "metric",
    "valueType": "number",
    "action": "",
    "drillChart": "none",
    "aggregationPaths": [
      "Total Sludge Collection"
    ],
    "insight": {
      "chartResponseMap" : "totalSludgeTreated",
      "action" : "differenceOfNumbers",
      "upwardIndicator" : "positive",
      "downwardIndicator" : "negative",
      "textMessage" : "$indicator$value% than last $insightInterval",
      "colorCode" : "#228B22",
      "insightInterval" : "year",
      "isRoundOff": true
    },
    "_comment": " FSM Total Sludge Treated"
  },
  "avgFSMCostRequest": {
    "chartName": "DSS_FSM_AVG_FSM_COST_OR_REQ",
    "queries": [
      {
        "module": "FSM",
        "indexName": "fsm",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"Data.tenantId.keyword\":\"pb.testing\"}}],\"must\":[{\"term\":{\"Data.payments.paymentDetails.businessService.keyword\":\"FSM.TRIP_CHARGES\"}}]}},\"aggs\":{\"Average Collection\":{\"avg\":{\"field\":\"Data.payments.paymentDetails.bill.billDetails.amountPaid\"}}}}}}",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtCode\"}",
        "dateRefField": "Data.fsm.@timestamp"
      }
    ],
    "chartType": "metric",
    "valueType": "amount",
    "action": "",
    "drillChart": "none",
    "isRoundOff": true,
    "aggregationPaths": [
      "Average Collection"
    ],
    "insight": {
      "chartResponseMap" : "averageCollection",
      "action" : "differenceOfNumbers",
      "upwardIndicator" : "positive",
      "downwardIndicator" : "negative",
      "textMessage" : "$indicator$value% than last $insightInterval",
      "colorCode" : "#228B22",
      "insightInterval" : "year",
      "isRoundOff": true
    },
    "_comment": " FSM Average Collection"
  },
  "totalCollectioninLacs": {
    "chartName": "DSS_FSM_TOTAL_COLLECTION",
    "queries": [
      {
        "module": "FSM",
        "indexName": "fsm",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"Data.tenantId.keyword\":\"pb.testing\"}}],\"must\":[{\"term\":{\"Data.payments.paymentDetails.businessService.keyword\":\"FSM.TRIP_CHARGES\"}}]}},\"aggs\":{\"Total Collection\":{\"sum\":{\"field\":\"Data.payments.paymentDetails.bill.billDetails.amountPaid\"}}}}}}",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtCode\"}",
        "dateRefField": "Data.fsm.@timestamp"
      }
    ],
    "chartType": "metric",
    "valueType": "amount",
    "action": "",
    "drillChart": "none",
    "documentType": "_doc",
    "aggregationPaths": [
      "Total Collection"
    ],
    "insight": {
      "chartResponseMap" : "totalCollection",
      "action" : "differenceOfNumbers",
      "upwardIndicator" : "positive",
      "downwardIndicator" : "negative",
      "textMessage" : "$indicator$value% than last $insightInterval",
      "colorCode" : "#228B22",
      "insightInterval" : "year",
      "isRoundOff": true
    },
    "_comment": " FSM Total Collection"
  },
  "slaCompliance": {
    "chartName": "DSS_FSM_SLA_COMPLIANCE",
    "queries": [
      {
        "module": "FSM",
        "indexName": "fsm",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"Data.service.tenantId.keyword\":\"pb.testing\"}}]}},\"aggs\":{\"Closed With In Sla\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}},{\"script\":{\"script\":{\"source\":\"doc['Data.fsm.auditDetails.lastModifiedTime'].value - doc['Data.fsm.auditDetails.createdTime'].value < params.threshold\",\"lang\":\"painless\",\"params\":{\"threshold\":172800000}}}}]}},\"aggs\":{\"count\":{\"terms\":{\"field\":\"Data.fsm.tenantId.keyword\"},\"aggs\":{\"tenant_count\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}}}}}},\"Total Applications\":{\"terms\":{\"field\":\"Data.fsm.tenantId.keyword\"},\"aggs\":{\"tenant_count\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}}}}}}}}",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtCode\"}",
        "dateRefField": "Data.fsm.@timestamp"
      }
    ],
    "chartType": "metric",
    "valueType": "percentage",
    "drillChart": "none",
    "documentType": "_doc",
    "action": "percentage",
    "isRoundOff": true,
    "aggregationPaths": [
      "Closed With In Sla",
      "Total Applications"
    ],
    "insight": {
      "chartResponseMap" : "slaCompliance",
      "action" : "differenceOfNumbers",
      "upwardIndicator" : "positive",
      "downwardIndicator" : "negative",
      "textMessage" : "$indicator$value% than last $insightInterval",
      "colorCode" : "#228B22",
      "insightInterval" : "year",
      "isRoundOff": true
    },
    "_comment": " SLA Compliance"
  },
  "citizenAvgRating": {
    "chartName": "DSS_FSM_CITIZEN_AVG_RATING",
    "queries": [
      {
        "module": "FSM",
        "indexName": "fsm",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"Data.fsm.tenantId.keyword\":\"pb.testing\"}}],\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\"]}},{\"term\":{\"Data.history.action.keyword\":\"RATE\"}},{\"exists\":{\"field\":\"Data.history\"}},{\"range\":{\"Data.history.rating\":{\"gte\":1}}}]}},\"aggs\":{\"Citizen Average Rating\":{\"avg\":{\"script\":\"int sum = 0;int count =0;if(params['_source']['Data']['history']!=null){ for (item in params['_source']['Data']['history']) {if(item.rating!=null){ sum += item.rating;} }} return sum;\"}}}}}}",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtCode\"}",
        "dateRefField": "Data.fsm.@timestamp"
      }
    ],
    "chartType": "metric",
    "valueType": "number",
    "action": "",
    "drillChart": "none",
    "documentType": "_doc",
    "aggregationPaths": [
      "Citizen Average Rating"
    ],
    "postAggregationTheory": "",
    "insight": {},
    "_comment": " Citizen Average rating"
  },
  "fsmCollectionByUsageType": {
    "chartName": "DSS_FSM_COLLECTION_BY_USAGE_TYPE",
    "queries": [
      {
        "module": "FSM",
        "dateRefField": "Data.fsm.@timestamp",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtCode\"}",
        "indexName": "fsm",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"Data.fsm.tenantId.keyword\":\"pb.testing\"}}]}},\"aggs\":{\"Usage Type\":{\"terms\":{\"field\":\"Data.fsm.propertyUsage.keyword\"},\"aggs\":{\"Assessed Properties\":{\"sum\":{\"field\":\"Data.payments.paymentDetails.bill.billDetails.amountPaid\"}}}}}}}}"
      }
    ],
    "chartType": "pie",
    "valueType": "amount",
    "action": "",
    "documentType": "_doc",
    "drillChart": "none",
    "aggregationPaths": [
      "Usage Type"
    ],
    "insight": {
    },
    "_comment": " "
  },
  "fsmTotalCumulativeCollection": {
    "chartName": "DSS_FSM_TOTAL_CUMULATIVE_COLLECTION",
    "queries": [
      {
        "module": "FSM",
        "dateRefField": "Data.fsm.@timestamp",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtCode\"}",
        "indexName": "fsm",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"Data.fsm.tenantId.keyword\":\"pb.testing\"}}]}},\"aggs\":{\"Total Collection\":{\"date_histogram\":{\"field\":\"Data.fsm.@timestamp\",\"interval\":\"intervalvalue\"},\"aggs\":{\"Count\":{\"sum\":{\"field\":\"Data.payments.paymentDetails.bill.billDetails.amountPaid\"}}}}}}}}"
      }
    ],
    "chartType": "line",
    "valueType": "amount",
    "action": "",
    "drillChart": "none",
    "documentType": "_doc",
    "aggregationPaths": [
      "Total Collection"
    ],
    "isCumulative": true,
    "interval": "month",
    "insight": {
    },
    "_comment": " "
  },
  "fsmTopUlbByPerformance": {
    "chartName": "DSS_FSM_TOP_ULB_BY_PERFORMANCE",
    "queries": [
      {
        "module": "FSM",
        "dateRefField": "Data.fsm.@timestamp",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtCode\"}",
        "indexName": "fsm",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"Data.fsm.tenantId.keyword\":\"pb.testing\"}}]}},\"aggs\":{\"Closed With In Sla\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}},{\"script\":{\"script\":{\"source\":\"doc['Data.fsm.auditDetails.lastModifiedTime'].value - doc['Data.fsm.auditDetails.createdTime'].value < params.threshold\",\"lang\":\"painless\",\"params\":{\"threshold\":172800000}}}}]}},\"aggs\":{\"count\":{\"terms\":{\"field\":\"Data.fsm.tenantId.keyword\"},\"aggs\":{\"tenant_count\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}}}}}},\"Total Applications\":{\"terms\":{\"field\":\"Data.fsm.tenantId.keyword\"},\"aggs\":{\"tenant_count\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}}}}}}}}"
      }
    ],
    "chartType": "perform",
    "valueType": "percentage",
    "drillChart": "none",
    "documentType": "_doc",
    "drillChart": "ulbTopDrillChart",
    "action": "percentage",
    "plotLabel": "DSS_COMPLETION_RATE",
    "isRoundOff": true,
    "order": "desc",
    "limit": 3,
    "aggregationPaths": [
      "Closed With In Sla",
      "Total Applications"
    ],
    "isCumulative": false,
    "interval": "month",
    "insight": {
    },
    "_comment": ""
  },
  "ulbTopDrillChart": {
    "chartName": "DSS_FSM_ULB_PERFORMANCE",
    "queries": [
      {
        "module": "FSM",
        "dateRefField": "Data.fsm.@timestamp",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtCode\"}",
        "indexName": "fsm",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"data.fsm.tenantId.keyword\":\"pb.testing\"}}]}},\"aggs\":{\"ULB\":{\"terms\":{\"field\":\"Data.fsm.tenantId.keyword\",\"size\":1000,\"order\":{\"_count\":\"desc\"}},\"aggs\":{\"TotalRequests\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}},\"ClosedWithInSLA\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}},{\"script\":{\"script\":{\"source\":\"doc['Data.fsm.auditDetails.lastModifiedTime'].value - doc['Data.fsm.auditDetails.createdTime'].value < params.threshold\",\"lang\":\"painless\",\"params\":{\"threshold\":172800000}}}}]}},\"aggs\":{\"valueCount\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}}}},\"ClosedOutsideSLA\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}},{\"script\":{\"script\":{\"source\":\"doc['Data.fsm.auditDetails.lastModifiedTime'].value - doc['Data.fsm.auditDetails.createdTime'].value > params.threshold\",\"lang\":\"painless\",\"params\":{\"threshold\":172800000}}}}]}},\"aggs\":{\"valueCount\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}}}},\"CitizenAverageRating\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\"]}},{\"term\":{\"Data.history.action.keyword\":\"RATE\"}},{\"exists\":{\"field\":\"Data.history\"}},{\"range\":{\"Data.history.rating\":{\"gte\":1}}}]}},\"aggs\":{\"CitizenAvgRating\":{\"avg\":{\"script\":\"int sum = 0;int count =0;if(params['_source']['Data']['history']!=null){ for (item in params['_source']['Data']['history']) {if(item.rating!=null){ sum += item.rating;} }} return sum;\"}}}}}}}}}}"
      }
    ],
   "filterKeys": [
      {"key": "tenantId", "column": "ULB"}
    ],
    "isPostResponseHandler": true,
    "chartType": "table",
    "valueType": "number",
    "action": "",
    "documentType": "_doc",
    "drillChart": "none",
    "plotLabel":"ULB",
    "aggregationPaths": [
      "TotalRequests",
      "ClosedWithInSLA",
      "ClosedOutsideSLA",
      "CitizenAverageRating"
    ],
    "pathDataTypeMapping": [
      {
        "TotalRequests" : "number"
      },
      {
        "ClosedWithInSLA" : "number"
      },
      {
        "ClosedOutsideSLA" : "number"
      },
      {
        "CitizenAverageRating" : "number"
      }
    ],
    "isCumulative": true,
    "interval": "month",
    "insight": {
    },
    "_comment": " "
  },
  "fsmBottomUlbByPerformance": {
    "chartName": "DSS_FSM_BOTTOM_ULB_BY_PERFORMANCE",
    "queries": [
      {
        "module": "FSM",
        "dateRefField": "Data.fsm.@timestamp",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtCode\"}",
        "indexName": "fsm",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"Data.fsm.tenantId.keyword\":\"pb.testing\"}}]}},\"aggs\":{\"Closed With In Sla\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}},{\"script\":{\"script\":{\"source\":\"doc['Data.fsm.auditDetails.lastModifiedTime'].value - doc['Data.fsm.auditDetails.createdTime'].value < params.threshold\",\"lang\":\"painless\",\"params\":{\"threshold\":172800000}}}}]}},\"aggs\":{\"count\":{\"terms\":{\"field\":\"Data.fsm.tenantId.keyword\"},\"aggs\":{\"tenant_count\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}}}}}},\"Total Applications\":{\"terms\":{\"field\":\"Data.fsm.tenantId.keyword\"},\"aggs\":{\"tenant_count\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}}}}}}}}"
      }
    ],
    "chartType": "perform",
    "valueType": "percentage",
    "drillChart": "none",
    "documentType": "_doc",
    "drillChart": "ulbBottomDrillChart",
    "action": "percentage",
    "isRoundOff": true,
    "plotLabel": "DSS_COMPLETION_RATE",
    "order": "asc",
    "limit": 3,
    "aggregationPaths": [
      "Closed With In Sla",
      "Total Applications"
    ],
    "isCumulative": false,
    "interval": "month",
    "insight": {
    },
    "_comment": ""
  },
  "ulbBottomDrillChart": {
    "chartName": "DSS_FSM_ULB_PERFORMANCE",
    "queries": [
      {
        "module": "FSM",
        "dateRefField": "Data.fsm.@timestamp",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtCode\"}",
        "indexName": "fsm",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"data.fsm.tenantId.keyword\":\"pb.testing\"}}]}},\"aggs\":{\"ULB\":{\"terms\":{\"field\":\"Data.fsm.tenantId.keyword\",\"size\":1000,\"order\":{\"_count\":\"asc\"}},\"aggs\":{\"TotalRequests\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}},\"ClosedWithInSLA\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}},{\"script\":{\"script\":{\"source\":\"doc['Data.fsm.auditDetails.lastModifiedTime'].value - doc['Data.fsm.auditDetails.createdTime'].value < params.threshold\",\"lang\":\"painless\",\"params\":{\"threshold\":172800000}}}}]}},\"aggs\":{\"valueCount\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}}}},\"ClosedOutsideSLA\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}},{\"script\":{\"script\":{\"source\":\"doc['Data.fsm.auditDetails.lastModifiedTime'].value - doc['Data.fsm.auditDetails.createdTime'].value > params.threshold\",\"lang\":\"painless\",\"params\":{\"threshold\":172800000}}}}]}},\"aggs\":{\"valueCount\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}}}},\"CitizenAverageRating\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\"]}},{\"term\":{\"Data.history.action.keyword\":\"RATE\"}},{\"exists\":{\"field\":\"Data.history\"}},{\"range\":{\"Data.history.rating\":{\"gte\":1}}}]}},\"aggs\":{\"CitizenAvgRating\":{\"avg\":{\"script\":\"int sum = 0;int count =0;if(params['_source']['Data']['history']!=null){ for (item in params['_source']['Data']['history']) {if(item.rating!=null){ sum += item.rating;} }} return sum;\"}}}}}}}}}}"
      }
    ],
   "filterKeys": [
      {"key": "tenantId", "column": "ULB"}
    ],
    "isPostResponseHandler": true,
    "chartType": "table",
    "valueType": "number",
    "action": "",
    "documentType": "_doc",
    "drillChart": "none",
    "plotLabel":"ULB",
    "aggregationPaths": [
      "TotalRequests",
      "ClosedWithInSLA",
      "ClosedOutsideSLA",
      "CitizenAverageRating"
    ],
    "pathDataTypeMapping": [
      {
        "TotalRequests" : "number"
      },
      {
        "ClosedWithInSLA" : "number"
      },
      {
        "ClosedOutsideSLA" : "number"
      },
      {
        "CitizenAverageRating" : "number"
      }
    ],
    "isCumulative": true,
    "interval": "month",
    "insight": {
    },
    "_comment": " "
  },
  "fsmCapacityUtilization": {
    "chartName": "DSS_FSTP_CAPACITY_UTILIZATION",
    "queries": [
      {
        "module": "FSM",
        "dateRefField": "Data.vehicleTrip.@timestamp",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtCode\"}",
        "indexName": "vehicletrip",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"Data.vehicleTrip.tenantId.keyword\":\"pb.testing\"}}]}},\"aggs\":{\"Capacity Utilization\":{\"date_histogram\":{\"field\":\"Data.vehicleTrip.@timestamp\",\"interval\":\"month\"},\"aggs\":{\"Count\":{\"sum\":{\"script\":{\"source\":\"(doc['Data.vehicleTrip.volumeCarried'].value)/1000.0\"}}}}}}}}}"
      }
    ],
    "chartType": "line",
    "valueType": "amount",
    "action": "",
    "isRoundOff": true,
    "documentType": "_doc",
    "drillChart": "none",
    "aggregationPaths": [
      "Capacity Utilization"
    ],
    "isCumulative": true,
    "interval": "month",
    "insight": {
    },
    "_comment": " "
  },
  "fsmMonthlyWasteCal": {
    "chartName": "DSS_FSM_MONTHLY_WASTE_CAL",
    "queries": [
      {
        "module": "FSM",
        "dateRefField": "Data.vehicleTrip.@timestamp",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtCode\"}",
        "indexName": "vehicletrip",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"Data.vehicleTrip.tenantId.keyword\":\"pb.testing\"}}]}},\"aggs\":{\"Septage Dumped At Plant\":{\"date_histogram\":{\"field\":\"Data.vehicleTrip.@timestamp\",\"interval\":\"month\"},\"aggs\":{\"Count\":{\"sum\":{\"script\":{\"source\":\"(doc['Data.vehicleTrip.volumeCarried'].value)/1000.0\"}}}}},\"Septage Collected\":{\"date_histogram\":{\"field\":\"Data.vehicleTrip.@timestamp\",\"interval\":\"month\"},\"aggs\":{\"Count\":{\"sum\":{\"script\":{\"source\":\"(doc['Data.vehicleTrip.tripDetails.volume'].value)/1000.0\"}}}}}}}}}"
      }
    ],
    "chartType": "line",
    "valueType": "number",
    "action": "",
    "isRoundOff": true,
    "documentType": "_doc",
    "drillChart": "none",
    "aggregationPaths": [
      "Septage Collected",
      "Septage Dumped At Plant"
    ],
    "isCumulative": false,
    "interval": "month",
    "insight": {
    },
    "_comment": " "
  },
  "fsmTopDsoByPerformance": {
    "chartName": "DSS_FSM_TOP_DSO_BY_PERFORMANCE",
    "queries": [
      {
        "module": "FSM",
        "dateRefField": "Data.fsm.@timestamp",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtCode\"}",
        "indexName": "fsm",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"Data.fsm.tenantId.keyword\":\"pb.testing\"}}]}},\"aggs\":{\"Raised\":{\"terms\":{\"field\":\"Data.vendor.name.keyword\",\"size\":3,\"order\":{\"_count\":\"desc\"}},\"aggs\":{\"Count\":{\"value_count\":{\"field\":\"Data.vendor.name.keyword\"}}}},\"Closed Within SLA\":{\"terms\":{\"field\":\"Data.vendor.name.keyword\",\"size\":3,\"order\":{\"_count\":\"desc\"}},\"aggs\":{\"Count\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}},{\"script\":{\"script\":{\"source\":\"doc['Data.fsm.auditDetails.lastModifiedTime'].value - doc['Data.fsm.auditDetails.createdTime'].value < params.threshold\",\"lang\":\"painless\",\"params\":{\"threshold\":172800000}}}}]}},\"aggs\":{\"valueCount\":{\"value_count\":{\"field\":\"Data.vendor.name.keyword\"}}}}}},\"Closed Outside SLA\":{\"terms\":{\"field\":\"Data.vendor.name.keyword\",\"size\":3,\"order\":{\"_count\":\"desc\"}},\"aggs\":{\"Count\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}},{\"script\":{\"script\":{\"source\":\"doc['Data.fsm.auditDetails.lastModifiedTime'].value - doc['Data.fsm.auditDetails.createdTime'].value > params.threshold\",\"lang\":\"painless\",\"params\":{\"threshold\":172800000}}}}]}},\"aggs\":{\"valueCount\":{\"value_count\":{\"field\":\"Data.vendor.name.keyword\"}}}}}}}}}}"
      }
    ],
    "chartType": "line",
    "valueType": "number",
    "action": "",
    "drillChart": "dsoTopDrillChart",
    "documentType": "_doc",
    "aggregationPaths": [
      "Raised",
      "Closed Within SLA",
      "Closed Outside SLA"
    ],
    "isCumulative": false,
    "interval": "month",
    "insight": {
    },
    "_comment": ""
  },
  "dsoTopDrillChart": {
    "chartName": "DSS_FSM_DSO_PERFORMANCE",
    "queries": [
      {
        "module": "FSM",
        "dateRefField": "Data.fsm.@timestamp",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtCode\"}",
        "indexName": "fsm",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"data.fsm.tenantId.keyword\":\"pb.testing\"}}]}},\"aggs\":{\"DSOName\":{\"terms\":{\"field\":\"Data.vendor.name.keyword\",\"size\":1000,\"order\":{\"_count\":\"desc\"}},\"aggs\":{\"TotalRequest\":{\"value_count\":{\"field\":\"Data.vendor.name.keyword\"}},\"ClosedWithinSLA\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}},{\"script\":{\"script\":{\"source\":\"doc['Data.fsm.auditDetails.lastModifiedTime'].value - doc['Data.fsm.auditDetails.createdTime'].value < params.threshold\",\"lang\":\"painless\",\"params\":{\"threshold\":172800000}}}}]}},\"aggs\":{\"valueCount\":{\"value_count\":{\"field\":\"Data.vendor.name.keyword\"}}}},\"ClosedOutsideSLA\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}},{\"script\":{\"script\":{\"source\":\"doc['Data.fsm.auditDetails.lastModifiedTime'].value - doc['Data.fsm.auditDetails.createdTime'].value > params.threshold\",\"lang\":\"painless\",\"params\":{\"threshold\":172800000}}}}]}},\"aggs\":{\"valueCount\":{\"value_count\":{\"field\":\"Data.vendor.name.keyword\"}}}},\"CitizenAverageRating\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\"]}},{\"term\":{\"Data.history.action.keyword\":\"RATE\"}},{\"exists\":{\"field\":\"Data.history\"}},{\"range\":{\"Data.history.rating\":{\"gte\":1}}}]}},\"aggs\":{\"CitizenAvgRating\":{\"avg\":{\"script\":\"int sum = 0;int count =0;if(params['_source']['Data']['history']!=null){ for (item in params['_source']['Data']['history']) {if(item.rating!=null){ sum += item.rating;} }} return sum;\"}}}}}}}}}}"
      }
    ],
    "filterKeys": [
      {"key": "dsoName", "column": "DSOName"}
    ],
    "isPostResponseHandler": true,
    "chartType": "table",
    "valueType": "number",
    "action": "",
    "documentType": "_doc",
    "drillChart": "none",
    "plotLabel":"DSOName",
    "aggregationPaths": [
      "TotalRequest",
      "ClosedWithinSLA",
      "ClosedOutsideSLA",
      "CitizenAverageRating"
    ],
    "pathDataTypeMapping": [
      {
        "TotalRequest" : "number"
      },
      {
        "ClosedWithinSLA" : "number"
      },
        {
        "ClosedOutsideSLA" : "number"
      },
      {
        "CitizenAverageRating" : "number"
      }
    ],
    "isCumulative": true,
    "interval": "month",
    "insight": {
    },
    "_comment": " "
  },
  "fsmBottomDsoByPerformance": {
    "chartName": "DSS_FSM_BOTTOM_DSO_BY_PERFORMANCE",
    "queries": [
      {
        "module": "FSM",
        "dateRefField": "Data.fsm.@timestamp",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtCode\"}",
        "indexName": "fsm",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"Data.fsm.tenantId.keyword\":\"pb.testing\"}}]}},\"aggs\":{\"Raised\":{\"terms\":{\"field\":\"Data.vendor.name.keyword\",\"size\":3,\"order\":{\"_count\":\"asc\"}},\"aggs\":{\"Count\":{\"value_count\":{\"field\":\"Data.vendor.name.keyword\"}}}},\"Closed Within SLA\":{\"terms\":{\"field\":\"Data.vendor.name.keyword\",\"size\":3,\"order\":{\"_count\":\"asc\"}},\"aggs\":{\"Count\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}},{\"script\":{\"script\":{\"source\":\"doc['Data.fsm.auditDetails.lastModifiedTime'].value - doc['Data.fsm.auditDetails.createdTime'].value < params.threshold\",\"lang\":\"painless\",\"params\":{\"threshold\":172800000}}}}]}},\"aggs\":{\"valueCount\":{\"value_count\":{\"field\":\"Data.vendor.name.keyword\"}}}}}},\"Closed Outside SLA\":{\"terms\":{\"field\":\"Data.vendor.name.keyword\",\"size\":3,\"order\":{\"_count\":\"asc\"}},\"aggs\":{\"Count\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}},{\"script\":{\"script\":{\"source\":\"doc['Data.fsm.auditDetails.lastModifiedTime'].value - doc['Data.fsm.auditDetails.createdTime'].value > params.threshold\",\"lang\":\"painless\",\"params\":{\"threshold\":172800000}}}}]}},\"aggs\":{\"valueCount\":{\"value_count\":{\"field\":\"Data.vendor.name.keyword\"}}}}}}}}}}"
      }
    ],
    "chartType": "line",
    "valueType": "number",
    "action": "",
    "drillChart": "dsoBottomDrillChart",
    "documentType": "_doc",
    "aggregationPaths": [
      "Raised",
      "Closed Within SLA",
      "Closed Outside SLA"
    ],
    "isCumulative": false,
    "interval": "month",
    "insight": {
    },
    "_comment": ""
  },
  "dsoBottomDrillChart": {
    "chartName": "DSS_FSM_DSO_PERFORMANCE",
    "queries": [
      {
        "module": "FSM",
        "dateRefField": "Data.fsm.@timestamp",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtCode\"}",
        "indexName": "fsm",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"data.fsm.tenantId.keyword\":\"pb.testing\"}}]}},\"aggs\":{\"DSOName\":{\"terms\":{\"field\":\"Data.vendor.name.keyword\",\"size\":1000,\"order\":{\"_count\":\"asc\"}},\"aggs\":{\"TotalRequest\":{\"value_count\":{\"field\":\"Data.vendor.name.keyword\"}},\"ClosedWithinSLA\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}},{\"script\":{\"script\":{\"source\":\"doc['Data.fsm.auditDetails.lastModifiedTime'].value - doc['Data.fsm.auditDetails.createdTime'].value < params.threshold\",\"lang\":\"painless\",\"params\":{\"threshold\":172800000}}}}]}},\"aggs\":{\"valueCount\":{\"value_count\":{\"field\":\"Data.vendor.name.keyword\"}}}},\"ClosedOutsideSLA\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}},{\"script\":{\"script\":{\"source\":\"doc['Data.fsm.auditDetails.lastModifiedTime'].value - doc['Data.fsm.auditDetails.createdTime'].value > params.threshold\",\"lang\":\"painless\",\"params\":{\"threshold\":172800000}}}}]}},\"aggs\":{\"valueCount\":{\"value_count\":{\"field\":\"Data.vendor.name.keyword\"}}}},\"CitizenAverageRating\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\"]}},{\"term\":{\"Data.history.action.keyword\":\"RATE\"}},{\"exists\":{\"field\":\"Data.history\"}},{\"range\":{\"Data.history.rating\":{\"gte\":1}}}]}},\"aggs\":{\"CitizenAvgRating\":{\"avg\":{\"script\":\"int sum = 0;int count =0;if(params['_source']['Data']['history']!=null){ for (item in params['_source']['Data']['history']) {if(item.rating!=null){ sum += item.rating;} }} return sum;\"}}}}}}}}}}"
      }
    ],
    "filterKeys": [
      {"key": "dsoName", "column": "DSOName"}
    ],
    "isPostResponseHandler": true,
    "chartType": "table",
    "valueType": "number",
    "action": "",
    "documentType": "_doc",
    "drillChart": "none",
    "plotLabel":"DSOName",
    "aggregationPaths": [
      "TotalRequest",
      "ClosedWithinSLA",
      "ClosedOutsideSLA",
      "CitizenAverageRating"
    ],
    "pathDataTypeMapping": [
      {
        "TotalRequest" : "number"
      },
      {
        "ClosedWithinSLA" : "number"
      },
      {
        "ClosedOutsideSLA" : "number"
      },
      {
        "CitizenAverageRating" : "number"
      }
    ],
    "isCumulative": true,
    "interval": "month",
    "insight": {
    },
    "_comment": " "
  },
  "fsmTotalReqByDistrict": {
    "chartName": "DSS_FSM_TOTAL_REQ_BY_DISTRICT",
    "queries": [
      {
        "module": "FSM",
        "dateRefField": "Data.fsm.@timestamp",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtName\"}",
        "indexName": "fsm",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"Data.fsm.tenantId.keyword\":\"pb.testing\"}}]}},\"aggs\":{\"Open_Req\":{\"filter\":{\"bool\":{\"must_not\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}}]}},\"aggs\":{\"OpenReq\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}}}},\"Closed_Req\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}}]}},\"aggs\":{\"ClosedReq\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}}}},\"TotalReq\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}},\"Closed_With_In_Sla\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}},{\"script\":{\"script\":{\"source\":\"doc['Data.fsm.auditDetails.lastModifiedTime'].value - doc['Data.fsm.auditDetails.createdTime'].value < params.threshold\",\"lang\":\"painless\",\"params\":{\"threshold\":172800000}}}}]}},\"aggs\":{\"ClosedWithInSla\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}}}},\"TotalCollection\":{\"sum\":{\"field\":\"Data.payments.paymentDetails.bill.billDetails.amountPaid\"}}}}}}"
      }
    ],
    "isMdmsEnabled": true,
    "filterKeys": [
      {"key": "tenantId", "column": "District"}
    ],
    "chartType": "xtable",
    "valueType": "number",
    "isRoundOff": true,
    "drillChart": "fsmTotalReqByTenant",
    "plotLabel": "District",
    "excludedColumns": ["ClosedWithInSla"],
    "computedFields": [
      {
        "postAggregationTheory" : "",
        "actionName": "PercentageComputedField",
        "fields" : ["ClosedReq", "TotalReq"],
        "newField" : "CompletionRateIn%",
        "_comments": "fields are field names picked from its aggregation query to use post aggregation newField value with given new field name  "
      },
      {
        "postAggregationTheory" : "",
        "actionName": "PercentageComputedField",
        "fields" : ["ClosedWithInSla","TotalReq"],
        "newField" : "SLAAchievedIn%",
        "_comments": "fields are field names picked from its aggregation query to use post aggregation newField value with given new field name  "
      }
    ],
     "chartSpecificProperty": {
     "XtableColumnOrder":[
     "S.N.",
     "District",
     "OpenReq",
     "ClosedReq",
     "TotalReq",
     "CompletionRateIn%",
     "SLAAchievedIn%",
     "TotalCollection"
     ]
     },
    "insight": {
    },
    "_comment": " "
  },
  "fsmTotalReqByTenant": {
    "chartName": "DSS_FSM_TOTAL_REQ_BY_ULB",
    "queries": [
      {
        "module": "FSM",
        "dateRefField": "Data.fsm.@timestamp",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtName\"}",
        "indexName": "fsm",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"Data.fsm.tenantId.keyword\":\"pb.testing\"}}]}},\"aggs\":{\"ULBs\":{\"terms\":{\"field\":\"Data.fsm.tenantId.keyword\",\"size\":1000},\"aggs\":{\"Open_Req\":{\"filter\":{\"bool\":{\"must_not\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}}]}},\"aggs\":{\"OpenReq\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}}}},\"Closed_Req\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}}]}},\"aggs\":{\"ClosedReq\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}}}},\"TotalReq\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}},\"Closed_With_In_Sla\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}},{\"script\":{\"script\":{\"source\":\"doc['Data.fsm.auditDetails.lastModifiedTime'].value - doc['Data.fsm.auditDetails.createdTime'].value < params.threshold\",\"lang\":\"painless\",\"params\":{\"threshold\":172800000}}}}]}},\"aggs\":{\"ClosedWithInSla\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}}}},\"TotalCollection\":{\"sum\":{\"field\":\"Data.payments.paymentDetails.bill.billDetails.amountPaid\"}}}}}}}}"
      }
    ],
    "filterKeys": [
      {"key": "tenantId", "column": "ULB"}
    ],
    "chartType": "xtable",
    "valueType": "number",
    "isRoundOff": true,
    "drillChart": "fsmTotalReqByWard",
    "plotLabel": "ULB",
    "excludedColumns": ["ClosedWithInSla"],
    "computedFields": [
      {
        "postAggregationTheory" : "",
        "actionName": "PercentageComputedField",
        "fields" : ["ClosedReq", "TotalReq"],
        "newField" : "CompletionRateIn%",
        "_comments": "fields are field names picked from its aggregation query to use post aggregation newField value with given new field name  "
      },
      {
        "postAggregationTheory" : "",
        "actionName": "PercentageComputedField",
        "fields" : ["ClosedWithInSla","TotalReq"],
        "newField" : "SLAAchievedIn%",
        "_comments": "fields are field names picked from its aggregation query to use post aggregation newField value with given new field name  "
      }
    ],
    "chartSpecificProperty": {
     "XtableColumnOrder":[
     "S.N.",
     "ULB",
     "OpenReq",
     "ClosedReq",
     "TotalReq",
     "CompletionRateIn%",
     "SLAAchievedIn%",
     "TotalCollection"
     ]
     },
    "insight": {
    },
    "_comment": " "
  },
  "fsmTotalReqByWard": {
    "chartName": "DSS_FSM_TOTAL_REQ_BY_WARD",
    "queries": [
      {
        "module": "FSM",
        "dateRefField": "Data.fsm.@timestamp",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtCode\"}",
        "indexName": "fsm",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"Data.fsm.tenantId.keyword\":\"pb.testing\"}}]}},\"aggs\":{\"Ward\":{\"terms\":{\"field\":\"Data.ward.name.keyword\",\"size\":1000},\"aggs\":{\"Open_Req\":{\"filter\":{\"bool\":{\"must_not\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}}]}},\"aggs\":{\"OpenReq\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}}}},\"Closed_Req\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}}]}},\"aggs\":{\"ClosedReq\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}}}},\"TotalReq\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}},\"Closed_With_In_Sla\":{\"filter\":{\"bool\":{\"must\":[{\"terms\":{\"Data.fsm.applicationStatus.keyword\":[\"COMPLETED\",\"CITIZEN_FEEDBACK_PENDING\"]}},{\"script\":{\"script\":{\"source\":\"doc['Data.fsm.auditDetails.lastModifiedTime'].value - doc['Data.fsm.auditDetails.createdTime'].value < params.threshold\",\"lang\":\"painless\",\"params\":{\"threshold\":172800000}}}}]}},\"aggs\":{\"ClosedWithInSla\":{\"value_count\":{\"field\":\"Data.fsm.tenantId.keyword\"}}}},\"TotalCollection\":{\"sum\":{\"field\":\"Data.payments.paymentDetails.bill.billDetails.amountPaid\"}}}}}}}}"
      }
    ],
    "filterKeys": [
      {"key": "wardId", "column": "Ward"},
      {"key": "ulbId", "column": "ULB"}
    ],
    "chartType": "xtable",
    "valueType": "number",
    "isRoundOff": true,
    "drillChart": "none",
    "action": "",
    "documentType": "_doc",
    "plotLabel": "Ward",
    "excludedColumns": ["ClosedWithInSla"],
    "computedFields": [
      {
        "postAggregationTheory" : "",
        "actionName": "PercentageComputedField",
        "fields" : ["ClosedReq", "TotalReq"],
        "newField" : "CompletionRateIn%",
        "_comments": "fields are field names picked from its aggregation query to use post aggregation newField value with given new field name  "
      },
      {
        "postAggregationTheory" : "",
        "actionName": "PercentageComputedField",
        "fields" : ["ClosedWithInSla","TotalReq"],
        "newField" : "SLAAchievedIn%",
        "_comments": "fields are field names picked from its aggregation query to use post aggregation newField value with given new field name  "
      }
    ],
     "chartSpecificProperty": {
     "XtableColumnOrder":[
     "S.N.",
     "Ward",
     "OpenReq",
     "ClosedReq",
     "TotalReq",
     "CompletionRateIn%",
     "SLAAchievedIn%",
     "TotalCollection"
     ]
     },
    "insight": {
    },
    "_comment": " "
  },
  "fsmVehicleLogReportByDDR": {
    "chartName": "DSS_FSM_VECHILE_LOG_REPORT",
    "queries": [
      {
        "module": "FSM",
        "dateRefField": "Data.vehicleTrip.@timestamp",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtName\"}",
        "indexName": "vehicletrip",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"data.vehicleTrip.tenantId.keyword\":\"pb.testing\"}}]}},\"aggs\":{\"NoOfTrips\":{\"value_count\":{\"field\":\"Data.vehicleTrip.@timestamp\"}},\"TotalSeptageCollected\":{\"sum\":{\"script\":{\"source\":\"(doc['Data.vehicleTrip.tripDetails.volume'].value)/1000.0\"}}},\"TotalSeptageDumped\":{\"sum\":{\"script\":{\"source\":\"(doc['Data.vehicleTrip.volumeCarried'].value)/1000.0\"}}},\"CapacityUtilization\":{\"sum\":{\"script\":{\"source\":\"(doc['Data.vehicleTrip.volumeCarried'].value)/1000.0\"}}}}}}}"
      }
    ],
    "isMdmsEnabled": true,
    "filterKeys": [
      {"key": "tenantId", "column": "District"}
    ],
    "isPostResponseHandler": true,
    "chartType": "xtable",
    "valueType": "number",
    "action": "",
    "isRoundOff": true,
    "documentType": "_doc",
    "drillChart": "fsmVehicleLogReportByTenant",
    "plotLabel":"District",
    "aggregationPaths": [
      "NoOfTrips",
      "TotalSeptageCollected",
      "TotalSeptageDumped",
      "CapacityUtilization"
    ],
    "pathDataTypeMapping": [
      {
        "NoOfTrips" : "number"
      },
      {
        "TotalSeptageCollected" : "number"
      },
      {
        "TotalSeptageDumped" : "number"
      },
      {
        "CapacityUtilization" : "number"
      }
    ],
    "isCumulative": true,
    "interval": "month",
    "insight": {
    },
    "_comment": " "
  },
  "fsmVehicleLogReportByTenant": {
    "chartName": "DSS_FSM_VECHILE_LOG_REPORT",
    "queries": [
      {
        "module": "FSM",
        "dateRefField": "Data.vehicleTrip.@timestamp",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtName\"}",
        "indexName": "vehicletrip",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"data.vehicleTrip.tenantId.keyword\":\"pb.testing\"}}]}},\"aggs\":{\"ULBs \":{\"terms\":{\"field\":\"Data.vehicleTrip.tenantId.keyword\",\"size\":1000},\"aggs\":{\"NoOfTrips\":{\"value_count\":{\"field\":\"Data.vehicleTrip.@timestamp\"}},\"TotalSeptageCollected\":{\"sum\":{\"script\":{\"source\":\"(doc['Data.vehicleTrip.tripDetails.volume'].value)/1000.0\"}}},\"TotalSeptageDumped\":{\"sum\":{\"script\":{\"source\":\"(doc['Data.vehicleTrip.volumeCarried'].value)/1000.0\"}}},\"CapacityUtilization\":{\"sum\":{\"script\":{\"source\":\"(doc['Data.vehicleTrip.volumeCarried'].value)/1000.0\"}}}}}}}}}"
      }
    ],
    "filterKeys": [
      {"key": "tenantId", "column": "Boundary"}
    ],
    "isPostResponseHandler": true,
    "chartType": "xtable",
    "valueType": "number",
    "action": "",
    "isRoundOff": true,
    "documentType": "_doc",
    "drillChart": "fsmVehicleLogReportByVehicleNo",
    "plotLabel":"Boundary",
    "aggregationPaths": [
      "NoOfTrips",
      "TotalSeptageCollected",
      "TotalSeptageDumped",
      "CapacityUtilization"
    ],
    "pathDataTypeMapping": [
      {
        "NoOfTrips" : "number"
      },
      {
        "TotalSeptageCollected" : "number"
      },
      {
        "TotalSeptageDumped" : "number"
      },
      {
        "CapacityUtilization" : "number"
      }
    ],
    "isCumulative": true,
    "interval": "month",
    "insight": {
    },
    "_comment": " "
  },
  "fsmVehicleLogReportByVehicleNo": {
    "chartName": "DSS_FSM_VECHILE_LOG_REPORT",
    "queries": [
      {
        "module": "FSM",
        "dateRefField": "Data.vehicleTrip.@timestamp",
        "requestQueryMap": "{\"wardId\" : \"Data.ward.name.keyword\", \"tenantId\" : \"Data.tenantData.code\" ,  \"district\" : \"Data.tenantData.city.districtCode\"}",
        "indexName": "vehicletrip",
        "aggrQuery": "{\"aggs\":{\"AGGR\":{\"filter\":{\"bool\":{\"must_not\":[{\"term\":{\"data.vehicleTrip.tenantId.keyword\":\"pb.testing\"}}]}},\"aggs\":{\"Vehicle Reg No\":{\"terms\":{\"field\":\"Data.vehicleTrip.vehicle.registrationNumber.keyword\",\"size\":1000},\"aggs\":{\"NoOfTrips\":{\"value_count\":{\"field\":\"Data.vehicleTrip.@timestamp\"}},\"TotalSeptageCollected\":{\"sum\":{\"script\":{\"source\":\"(doc['Data.vehicleTrip.tripDetails.volume'].value)/1000.0\"}}},\"TotalSeptageDumped\":{\"sum\":{\"script\":{\"source\":\"(doc['Data.vehicleTrip.volumeCarried'].value)/1000.0\"}}},\"CapacityUtilization\":{\"sum\":{\"script\":{\"source\":\"(doc['Data.vehicleTrip.volumeCarried'].value)/1000.0\"}}},\"TankCapacity\":{\"sum\":{\"script\":{\"source\":\"(doc['Data.vehicleTrip.vehicle.tankCapacity'].value)/1000.0\"}}}}}}}}}"
      }
    ],
    "filterKeys": [
      {"key": "registrationNumber", "column": "Vehicle_No"},
      {"key": "wardId", "column": "Ward"},
      {"key": "ulbId", "column": "ULB"}
    ],
    "isPostResponseHandler": true,
    "chartType": "xtable",
    "valueType": "number",
    "action": "",
    "isRoundOff": true,
    "documentType": "_doc",
    "drillChart": "none",
    "plotLabel":"Vehicle_No",
    "aggregationPaths": [
      "NoOfTrips",
      "TotalSeptageCollected",
      "TotalSeptageDumped",
      "CapacityUtilization",
      "TankCapacity"
    ],
    "pathDataTypeMapping": [
      {
        "NoOfTrips" : "number"
      },
      {
        "TotalSeptageCollected" : "number"
      },
      {
        "TotalSeptageDumped" : "number"
      },
      {
        "CapacityUtilization" : "number"
      },
      {
        "TankCapacity" : "number"
      }
    ],
    "isCumulative": true,
    "interval": "month",
    "insight": {
    },
    "_comment": " "
  }
```

[Click here to check the complete configuration](https://github.com/egovernments/configs/blob/qa/egov-dss-dashboards/dashboard-analytics/ChartApiConfig.json)

### **Master Dashboard Configuration**

Master Dashboard Configuration is the main configuration which defines as which are the Dashboards which are to be painted on screen.

It includes all the Visualizations, their groups, the charts which comes within them and even their dimensions as what should be their height and width.

```
{
      "name": "DSS_FSM_DASHBOARD",
      "id": "fsm",
      "isActive": "",
      "style": "linear",
      "visualizations": [
        {
          "row": 1,
          "name": "DSS_REVENUE",
          "vizArray": [
            {
              "id": 311,
              "name": "DSS_OVERVIEW",
              "dimensions": {
                "height": 450,
                "width": 4
              },
              "vizType": "metric-collection",
              "label": "DSS_OVERVIEW",
              "noUnit": true,
              "isCollapsible": false,
              "charts": [
                {
                  "id": "fsmTotalrequest",
                  "name": "DSS_FSM_TOTAL_REQUESTS",
                  "code": "",
                  "chartType": "metric",
                  "filter": "",
                  "headers": []
                },
                {
                  "id": "totalSludgeTreated",
                  "name": "DSS_FSM_TOTAL_SLUDGE_TREATED",
                  "code": "",
                  "chartType": "metric",
                  "filter": "",
                  "headers": []
                },
                {
                  "id": "avgFSMCostRequest",
                  "name": "DSS_FSM_AVG_FSM_COST_OR_REQ",
                  "code": "",
                  "chartType": "metric",
                  "filter": "",
                  "headers": []
                },
                {
                  "id": "totalCollectioninLacs",
                  "name": "DSS_FSM_TOTAL_COLLECTION",
                  "code": "",
                  "chartType": "metric",
                  "filter": "",
                  "headers": []
                },
                {
                  "id": "slaCompliance",
                  "name": "DSS_FSM_SLA_COMPLIANCE",
                  "code": "",
                  "chartType": "metric",
                  "filter": "",
                  "headers": []
                },
                {
                  "id": "citizenAvgRating",
                  "name": "DSS_FSM_CITIZEN_AVG_RATING",
                  "code": "",
                  "chartType": "metric",
                  "filter": "",
                  "headers": []
                }
              ]
            },
            {
              "id": 322,
              "name": "DSS_FSM_TOTAL_CUMULATIVE_COLLECTION",
              "dimensions": {
                "height": 450,
                "width": 6
              },
              "vizType": "chart",
              "label": "",
              "noUnit": true,
              "isCollapsible": false,
              "charts": [
                {
                  "id": "fsmTotalCumulativeCollection",
                  "name": "Monthly",
                  "code": "",
                  "chartType": "line",
                  "filter": "",
                  "headers": []
                }
              ]
            }
          ]
        },
        {
          "row": 2,
          "name": "DSS_REVENUE",
          "vizArray": [
            {
              "id": 321,
              "name": "DSS_FSM_TOP_ULB_BY_PERFORMANCE",
              "dimensions": {
                "height": 250,
                "width": 3
              },
              "vizType": "performing-metric",
              "label": "",
              "noUnit": false,
              "isCollapsible": false,
              "charts": [
                {
                  "id": "fsmTopUlbByPerformance",
                  "name": "Monthly",
                  "code": "",
                  "chartType": "bar",
                  "filter": "",
                  "headers": []
                }
              ]
            },
            {
              "id": 322,
              "name": "DSS_FSM_BOTTOM_ULB_BY_PERFORMANCE",
              "dimensions": {
                "height": 250,
                "width": 3
              },
              "vizType": "performing-metric",
              "label": "",
              "noUnit": false,
              "isCollapsible": false,
              "charts": [
                {
                  "id": "fsmBottomUlbByPerformance",
                  "name": "Monthly",
                  "code": "",
                  "chartType": "bar",
                  "filter": "",
                  "headers": []
                }
              ]
            },
            {
              "id": 323,
              "name": "DSS_FSM_COLLECTION_BY_USAGE_TYPE",
              "dimensions": {
                "height": 250,
                "width": 4
              },
              "vizType": "chart",
              "label": "",
              "noUnit": false,
              "isCollapsible": false,
              "charts": [
                {
                  "id": "fsmCollectionByUsageType",
                  "name": "DSS_FSM_COLLECTION_BY_USAGE_TYPE",
                  "code": "",
                  "chartType": "donut",
                  "filter": "",
                  "headers": []
                }
              ]
            }
          ]
        },
        {
          "row": 3,
          "name": "DSS_REVENUE",
          "vizArray": [
            {
              "id": 325,
              "name": "DSS_FSTP_CAPACITY_UTILIZATION",
              "dimensions": {
                "height": 450,
                "width": 5
              },
              "vizType": "chart",
              "label": "",
              "noUnit": true,
              "isCollapsible": false,
              "charts": [
                {
                  "id": "fsmCapacityUtilization",
                  "name": "Monthly",
                  "code": "",
                  "chartType": "line",
                  "filter": "",
                  "headers": []
                }
              ]
            },
            {
              "id": 326,
              "name": "DSS_FSM_MONTHLY_WASTE_CAL",
              "dimensions": {
                "height": 450,
                "width": 5
              },
              "vizType": "chart",
              "label": "",
              "noUnit": true,
              "isCollapsible": false,
              "charts": [
                {
                  "id": "fsmMonthlyWasteCal",
                  "name": "Monthly",
                  "code": "",
                  "chartType": "bar",
                  "filter": "",
                  "headers": []
                }
              ]
            }
          ]
        },
        {
          "row": 4,
          "name": "DSS_REVENUE",
          "vizArray": [
            {
              "id": 327,
              "name": "DSS_FSM_TOP_DSO_BY_PERFORMANCE",
              "dimensions": {
                "height": 450,
                "width": 5
              },
              "vizType": "chart",
              "label": "",
              "noUnit": true,
              "isCollapsible": false,
              "charts": [
                {
                  "id": "fsmTopDsoByPerformance",
                  "name": "Monthly",
                  "code": "",
                  "chartType": "horizontalBar",
                  "filter": "",
                  "headers": []
                }
              ]
            },
            {
              "id": 329,
              "name": "DSS_FSM_BOTTOM_DSO_BY_PERFORMANCE",
              "dimensions": {
                "height": 450,
                "width": 5
              },
              "vizType": "chart",
              "label": "",
              "noUnit": true,
              "isCollapsible": false,
              "charts": [
                {
                  "id": "fsmBottomDsoByPerformance",
                  "name": "Monthly",
                  "code": "",
                  "chartType": "horizontalBar",
                  "filter": "",
                  "headers": []
                }
              ]
            }
          ]
        },
        {
          "row": 5,
          "name": "DSS_REVENUE",
          "vizArray": [
            {
              "id": 339,
              "name": "DSS_FSM_TOTAL_REQ_BY_DISTRICT",
              "dimensions": {
                "height": 350,
                "width": 10
              },
              "vizType": "chart",
              "label": "",
              "noUnit": false,
              "isCollapsible": true,
              "charts": [
                {
                  "id": "fsmTotalReqByDistrict",
                  "name": "DSS_FSM_TOTAL_REQ_BY_DISTRICT",
                  "code": "",
                  "chartType": "table",
                  "filter": "",
                  "headers": [],
                  "tabName": "Boundary"
                }
              ]
            }
          ]
        },
        {
          "row": 6,
          "name": "DSS_REVENUE",
          "vizArray": [
            {
              "id": 331,
              "name": "DSS_FSM_VECHILE_LOG_REPORT",
              "dimensions": {
                "height": 350,
                "width": 10
              },
              "vizType": "chart",
              "label": "",
              "noUnit": false,
              "isCollapsible": true,
              "charts": [
                {
                  "id": "fsmVehicleLogReportByDDR",
                  "name": "DSS_FSM_VECHILE_LOG_REPORT",
                  "code": "",
                  "chartType": "table",
                  "filter": "",
                  "headers": [],
                  "tabName": "Boundary"
                }
              ]
            }
          ]
        }
      ]
    },
```

[Click here for the complete configuration](https://github.com/egovernments/configs/blob/qa/egov-dss-dashboards/dashboard-analytics/MasterDashboardConfig.json).

### **Role Dashboard Mappings Configuration**

The master dashboard configuration, which was explained earlier, holds the list of dashboards that are available.

Given the instance where role action mapping is not maintained in the application service, this configuration will act as Role - Dashboard Mapping Configuration. In this, each role is mapped against the dashboard which they are authorised to see. This was used earlier when the role action mapping of eGov was not integrated. Later, when the role action mapping started controlling the dashboards to be seen on the client side, this configuration was only used to enable the dashboards for viewing.

```
{
  "_comment": "Holds mapping for each role with and its associated dashboards",
  "roles" : [
    {
      "_comment":"This role is super role which can access all the available dashboards: [other/new roles are suppose to be added]",
      "roleId": 6,
      "roleName" : "Admin",
      "isSuper" : "",
      "orgId": "",
      "dashboards": [
        {
          "name": "Facial Sludge Management",
          "id": "fsm"
        }
      ]
    },
    {
      "_comment":"This role is super role which can access all the available dashboards: [other/new roles are suppose to be added]",
      "roleId": 7,
      "roleName" : "Commissioner",
      "isSuper" : "",
      "orgId": "",
      "dashboards": [
        {
          "id": "ulb-fsm"
        }
      ]
    }

  ]
}
```

[Click here to check the configuration](https://github.com/egovernments/configs/blob/qa/egov-dss-dashboards/dashboard-analytics/RoleDashboardMappingsConf.json)

### **MDMS Configuration to be added**

_common-masters/uiCommonConstants.json_

```
"fsm":{
                 "routePath":"/dashboard/fsm",
                 "isOrigin":true
              },
              "ulb-fsm":{
                 "routePath":"/dashboard/ulb-fsm",
                 "isOrigin":true
              }
```

[Click here to check the complete configuration](https://github.com/egovernments/egov-mdms-data/blob/QA/data/pb/common-masters/uiCommonConstants.json).

roleaction.json

```
 {
      "rolecode": "STADMIN",
      "actionid": {{PlaceHolder1}},
      "actioncode": "",
      "tenantId": "pb"
    }
    
    
    {
      "rolecode": "STADMIN",
      "actionid": {{PlaceHolder2}},
      "actioncode": "",
      "tenantId": "pb"
    },
     {
      "rolecode": "EMPLOYEE",
      "actionid": {{PlaceHolder2}},
      "actioncode": "",
      "tenantId": "pb"
    },  
     {
      "rolecode": "UC_EMP",
      "actionid": {{PlaceHolder2}},
      "actioncode": "",
      "tenantId": "pb"
    },
```

[Click here to check the complete configuration](https://github.com/egovernments/egov-mdms-data/blob/QA/data/pb/ACCESSCONTROL-ROLEACTIONS/roleactions.json).

Action test.json:

```
{
      "id": {{PlaceHolder1}},
      "name": "DSS Dashboard Config Facial Sludge Management",
      "url": "/dashboard-analytics/dashboard/getDashboardConfig/fsm",
      "parentModule": "",
      "displayName": "DSS",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "DSS",
      "code": "null",
      "path": ""
    },
  {
      "id": {{PlaceHolder2}},
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
    
```

[Click here to check the complete configuration](https://github.com/egovernments/egov-mdms-data/blob/QA/data/pb/ACCESSCONTROL-ACTIONS-TEST/actions-test.json).

FSM-DSS Consists of multiple graphs which represent the data of FSM. Each graph has its own configuration which will describe the chart and its type.

DSS Consists of following charts in FSM:

* Overview
* Total Cumulative Collection
* Top ULB By Performance
* Bottom ULB by Performance
* FSM Collection by Usage Type
* FSTP - Capacity Utilization
* Monthly Septage Collected
* Top DSO By Performance
* Bottom DSO By Performance
* Desludging Request Report
* Vehicle Log Report

## **Overview**

Overview graph contains multiple data information as below in the selected time period.

* **Total requests:** Which represents the number of FSM applications.
* **Total sludge treated:** This represents the total sludge dumped at the yard in KL.
* **Average FSM cost:** This represents the average collection amount for the FSM applications.
* **Total collection:** This represents the total collection amount for the FSM applications.
* **SLA compliance:** This represents the total SLA achieved in percentage.
* **Average citizen rating:** This represents the citizen average rating value.

![](<../../.gitbook/assets/Screenshot 2022-05-17 at 9.26.55 AM.png>)

## **Total Cumulative Collection**

This graph contains the collection amount information in the monthly base as a cumulative line graph. This will change as per the denomination amount filter selection.

**Line** - This graph/chart is data representation on date histograms or date groupings.![](blob:https://digit-discuss.atlassian.net/a94232b7-556f-44ac-8ab9-a81ba1207dd5#media-blob-url=true\&id=1ea67496-c39f-4bb0-a93f-8ff914975afe\&collection=contentId-1821016076\&contextId=1821016076\&mimeType=image%2Fpng\&name=image-20210730-105012.png\&size=39544\&width=932\&height=450)

![](<../../.gitbook/assets/Screenshot 2022-05-17 at 9.28.54 AM.png>)

## **Top ULB By Performance**

This graph represents the ULBs based on the SLA achieved in bar chart representation with the percentage of SLA achieved in ascending order. This chart also contains the drill-down to give the complete information regarding each ULB.

**Drill chart:** If there is a drill-down on the visualisation, then the code of the drill-down visualisation is added here. This will be used by client service to manage drill-downs.

![](<../../.gitbook/assets/Screenshot 2022-05-17 at 9.30.47 AM.png>)

This chart consists of a drill-down, so, we gave the drill-down chart key as a reference in this chart (as shown in the picture above).

Here is the drill down chart config params.

**Table chart sample:** This chart comes with 2 kinds: Table and xtable.

The table type allows aggregated fields added as available in the query keys. Hence, to extract the values based on the key, **aggegationPaths** needs to add along with their data type as in **pathDataTypeMapping**.

![](<../../.gitbook/assets/Screenshot 2022-05-17 at 9.32.56 AM.png>)

### **Bottom ULB by Performance** <a href="#bottom-ulb-by-performance" id="bottom-ulb-by-performance"></a>

This graph represents the ULB’s based on the SLA achieved in bar chart representation with the percentage of SLA achieved in descending order. This chart also contains the drill-down to give the complete information regarding each ULB.![](blob:https://digit-discuss.atlassian.net/dd364c4c-2d03-4f43-aedf-cf4f29996ae9#media-blob-url=true\&id=8e1ca71b-593e-4a91-8553-fd2dcb125bc3\&collection=contentId-1821016076\&contextId=1821016076\&mimeType=image%2Fpng\&name=image-20210730-105307.png\&size=22133\&width=472\&height=454)

![](<../../.gitbook/assets/Screenshot 2022-05-17 at 9.36.33 AM.png>)

When you click on "Show More," you will navigate to a tabular chart of the bottom ULB by performance.

![](<../../.gitbook/assets/Screenshot 2022-05-17 at 9.38.14 AM.png>)

### **FSM Collection by Usage Type** <a href="#fsm-collection-by-usage-type" id="fsm-collection-by-usage-type"></a>

This graph shows the collection amount based on the usage/property type, and this amount will change as per the denomination filter change. This also shows the percentage of the top four properties; the remaining properties will go under the 'Others' category.

![](<../../.gitbook/assets/Screenshot 2022-05-17 at 9.40.55 AM.png>)

### **FSTP - Capacity Utilisation** <a href="#fstp-capacity-utilization" id="fstp-capacity-utilization"></a>

This graph is in the line chart representation, and shows the data in cumulative format. It contains the information about the waste collecting plant capacity utilisation in percentage as well as the total waste dumped at plant in KL at the top of the graph.

![](<../../.gitbook/assets/Screenshot 2022-05-17 at 9.42.49 AM.png>)

### **Monthly Septage Collected** <a href="#monthly-septage-collected" id="monthly-septage-collected"></a>

This graph shows the data in horizontal bar representation, and the bars contain data monthly wide as well as non-cumulative data. This graph contains the monthly information of septage collected and dumped at the plant in KL.\


![](<../../.gitbook/assets/Screenshot 2022-05-17 at 9.44.59 AM.png>)

### **Top DSO By Performance** <a href="#top-dso-by-performance" id="top-dso-by-performance"></a>

This graph represents the DSOs based on the number of DSO requests and on SLA achievement in bar chart representation in ascending order. This chart also contains the drill-down to give the complete information regarding each DSO.\


![](<../../.gitbook/assets/Screenshot 2022-05-17 at 9.46.56 AM.png>)

When you click on "Show More", you can see the details of the available DSOs under the selected ULB.

![](<../../.gitbook/assets/Screenshot 2022-05-17 at 9.47.09 AM.png>)

### **Bottom DSO By Performance** <a href="#bottom-dso-by-performance" id="bottom-dso-by-performance"></a>

This graph represents the DSOs based on the number of DSO requests and on SLA achievement in bar chart representation in descending order. This chart also contains the drill-down to give the complete information regarding each DSO.

This is the bottom DSO drill-down chart which represents the table chart type.

![](<../../.gitbook/assets/Screenshot 2022-05-17 at 10.19.40 AM.png>)

When you click on "Show More", you can see the details of the available DSOs under the selected ULB.

![](<../../.gitbook/assets/Screenshot 2022-05-17 at 10.19.54 AM.png>)

### **Desludging Request Report** <a href="#desludging-request-report" id="desludging-request-report"></a>

This tabular chart representation graph shows multiple FSM information, such as the number of open application requests, closed requests, total requests, completion rate in percentage, SLA achieved in percentage, and total collection amount. This table shows the data at the district-level and also has the drill-down chart from each district to ULB, as well from ULB to the ward-level data for the same.

The _**xtable**_ type allows you to add multiple computed fields with the aggregated fields dynamically added.

To add multiple computed columns, **computedFields** \[] where actionName (IComputedField\<T> interface), fields \[] names as in exist in query key, newField as name to appear for computation must be defined.

**chartSpecificProperty**: This is specific to FSM-DSS, and it is used to achieve the xtable column order along with the computed fields. This property is not used in any other module till now.

![](<../../.gitbook/assets/Screenshot 2022-05-17 at 10.23.04 AM.png>)

When you click on any district name, you will see the drill-down charts, which will represent that specific district data.

![](<../../.gitbook/assets/Screenshot 2022-05-17 at 10.23.16 AM.png>)

When you click on the ULB, you will navigate towards under that specific ULB and each ward will show the data specific to that ward.

![](<../../.gitbook/assets/Screenshot 2022-05-17 at 10.23.34 AM.png>)

### **Vehicle Log Report** <a href="#vehicle-log-report" id="vehicle-log-report"></a>

This table shows the data of vehicle trips, and it includes the number of trips, total septage collected, total septage dumped, and capacity utilisation in percentage. This graph also contains the drills-downs from district to ULB and from ULB to the vehicle level, which shows the vehicle number.

![](<../../.gitbook/assets/Screenshot 2022-05-17 at 10.53.25 AM.png>)

When you click on any district name, you will see the drill-down charts, which will represent the data specific to that district.

![](<../../.gitbook/assets/Screenshot 2022-05-17 at 10.53.36 AM.png>)

When you click on any boundary/ULB, you will navigate to the specific vehicle details which will be as shown below.

![](<../../.gitbook/assets/Screenshot 2022-05-17 at 10.53.58 AM.png>)

#### **Newly-Introduced Property** <a href="#newly-introduced-property" id="newly-introduced-property"></a>

**isRoundOff**: This property is introduced to round-off the decimal values. For example, if the value is 25.43 by using isRoundOff property in configuration, you will get it 25. If value is 22.56, the round-off value will be 23. This can be used for insights configuration as well as overview graph.

#### Common Properties Available <a href="#common-properties-available" id="common-properties-available"></a>

**Key (Example: fsmTotalrequest):** This is the visualisation code. This key will be referred to in further visualisation configurations. This is the key which will be used by the client application to indicate which visualisation is needed for display.

**chartName:** The name of the chart which has to be used as a label on the dashboard. The name of the chart will be a detailed name. In this configuration, the name of the chart will be the code of localisation which will be used by the client side.

**queries:** Some visualisations are derived from a specific data source, while some others are derived from different data sources and are combined together to get a meaningful representation. The queries of aggregation, which are to be used to fetch out the right data in the right aggregated format, are configured here.

**queries.module:** The module/domain level on which the query should be applied on. Faecal Sludge Management is FSM.

**queries.indexName:** The name of the index on which the query has to be executed is configured here.

**queries.aggrQuery:** The aggregation query in itself is added here. Based on the module and the index name specified, this query is attached to the filter part of the complete search request and then executed against that index.

**queries.requestQueryMap:** Client request will carry certain fields which are to be filtered. The parameters specified in the client request are different from the parameters in each of these indexed documents. To map the parameters of the request to the parameters of the ElasticSearch Document, this mapping is maintained.

**queries.dateRefField :** Each of these modules have separate indexes, and all of them have their own date fields. When a date filter is applied against these visualisations, each of them has to apply it against their own date reference fields. To maintain what is the date field in which index, we have this configured in this configuration parameter.

**chartType :** As there are different types of visualisations, this field defines what is the type of chart/visualisation that this data should be used to represent.

**Chart types available are**:

**Metric** - This represents the aggregated amount/value for records filter by the aggregate as query

**Pie** - This represents the aggregated data on grouping. This can be used to represent any line graph, bar graph, pie chart, or donuts.

**Line** - This graph/chart is data representation on date histograms or date groupings.

**Perform** - This chart represents groping data performance wise.

**Table** - Represents a form of plots and value with headers as grouped on and list of its key, values pairs.

**xtable -** Represents an advanced feature of table; it has addition capabilities for dynamic adding header values.

**valueType:** In any case of data, the values which are sent to plot, might be a percentage, an amount, or a count. To represent them and differentiate the numbers from amount and percentage, this field is used to indicate the type of value that this visualisation will send.

**Action:** Some visualisations are not just aggregation on data source. There might be cases where we have to do a post-aggregation computation. For example, in the case of top 3 performing ULBs, the target and total collection is obtained, and then the percentage is calculated. In such cases, the action that has to be performed on that data is defined in this parameter.

**documentType:** The type of document on which the query has to be executed is defined here.

**drillChart:** If there is a drill-down on the visualisation, then the code of the drill-down visualization is added here. This will be used by client service to manage drill-downs.

**aggregationPaths:** All the queries will have aggregation names in it. To fetch the value out of each aggregation response, the name of the aggregation in the query will be needed. These aggregation paths will have the names of aggregation in it.

**insights:** It is to show the data with the comparison of last year with arrow symbols. It will show the data as percentage is increased or decreased.

**\_comment:** To display information on the “i” symbol of each visualisation, the visualisation information is maintained in this field.

**Postman collection for fsm-dss:** [https://www.getpostman.com/collections/119ee90dd54c04617c3a](https://www.getpostman.com/collections/119ee90dd54c04617c3a)
