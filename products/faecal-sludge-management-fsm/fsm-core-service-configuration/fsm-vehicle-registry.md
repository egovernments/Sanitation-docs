---
description: Configuration and setup details on registering vehicles in FSM module
---

# FSM Vehicle Registry

## Overview <a href="#overview" id="overview"></a>

Vehicle registry is a system that enables urban local body (ULB) employees to create and search vehicle entities, schedule vehicle trips for FSM application and track vehicle trips. This document contains the details about the new enhancements made to the vehicle service and how to set up the vehicle and describes the functionalities provided.

## Pre-requisites <a href="#pre-requisites" id="pre-requisites"></a>

Before you proceed with the configuration, make sure the following prerequisites are met:&#x20;

* Java 8
* Kafka server is up and running.
* egov-persister service is running and has vehicle-persister config path added in it.
* PSQL server is running and database is created to store FSM Application data.
* Following services should be up and running:

&#x20;     \- egov-perister

&#x20;     \- egov-mdms-service

&#x20;     \- egov-workflow-v2

&#x20;     \- egov-idgen

## Key Functionalities

* DSO or ULB can create multiple vehicle trips based on the number of trips entered while submitting the FSM application.
* FSTPO can decline the vehicle trip with appropriate reason.
* Owner attribute has been added to the vehicle.
* FSTPO Vehicle Log Inbox Enhancements to include Application No search filter so that FSTPO can view all the vehicle trips associated with the application.
* FSPTO vehicle log API upgraded to show trip numbers in case of multi-trip application.
* Introduced Vehicle Tab.
* Option to add/remove/update vehicles individually.
* Admin can enable or disable the vehicle.
* Functionality to add/remove vehicles to vendors.

## Deployment Details

1. Deploy the latest version of the vehicle.
2. Add vehicle-persister.yml file in config folder in git and add that path in persister . (The file path is to be added in environment yaml file in param called persist-yml-path ) and restart egov-persister-service.
3. Integrate the following below changes in vehicle-persister.yml\
   [SAN-1063 and 1064 (SAN-1158 and SAN-1157) -  Persister file - Vehicle… · egovernments/configs@2e53637](https://github.com/egovernments/configs/commit/2e536376408a0f09a2afe03c478201f5d81edfe4)
4. [SM-801 removing extra tab space by madan-kumar-eGov · Pull Request #2238 · egovernments/configs](https://github.com/egovernments/configs/pull/2238/files)
5. [SM-801 vehicle not able to create in uat by madan-kumar-eGov · Pull Request #2240 · egovernments/configs](https://github.com/egovernments/configs/pull/2240/files)

## Configuration Details <a href="#configuration-details" id="configuration-details"></a>

[Update vehicle-persister.yaml · egovernments/configs@32a7e1b](https://github.com/egovernments/configs/commit/32a7e1b606ac2b7466c83007e07d104d75153695)

[Update vehicle-persister.yaml · egovernments/configs@23237c8](https://github.com/egovernments/configs/commit/23237c8f467684c452461c5d0bf88ff54157fb8b)

[added jsonb data type for additionalDetails column in save-vehicle-ap… · egovernments/configs@9b2f604](https://github.com/egovernments/configs/commit/9b2f6043694a2f23e5a2bce83600e4b41a99b7f5)

[Added the audit logging for vehicle and vendor · egovernments/configs@482185f](https://github.com/egovernments/configs/commit/482185f1a79ad094f716e480922374e40c6e217a)

[SAN-1047 - Added the query map for update vehicle and vendor topics. · egovernments/configs@56da639](https://github.com/egovernments/configs/commit/56da639add16c412056aeac119517abd434a5ece)

[History for egov-persister/vehicle-persister.yaml - egovernments/configs](https://github.com/egovernments/configs/commits/DEV/egov-persister/vehicle-persister.yaml)

[configs/vendor-persister.yaml at DEV · egovernments/configs](https://github.com/egovernments/configs/blob/DEV/egov-persister/vendor-persister.yaml)

### MDMS Configuration <a href="#mdms-configuration-hardbreak" id="mdms-configuration-hardbreak"></a>

Add master data in MDMS service with module name as vehicle and restart egov-mdms-service. Following are some sample master data for:

**SuctionType**

```
{
    "tenantId": "pb",
    "moduleName": "Vehicle",
    "SuctionType": [
        {
            "code": "SEWER_SUCTION_MACHINE",
            "name": "Sewer suction machine",
            "active": true
        },
        {
            "code": "SEWER_SUCTION_CUM_JETTING_MACHINE",
            "name": "Sewer suction cum jetting machine",
            "active": true
        }
    ]
}
```

**VehicleOwner**

```
{
    "tenantId": "pb",
    "moduleName": "Vehicle",
    "VehicleOwner": [{
            "name": "ULB",
            "code": "ULB",
            "active": true
        },
        {
            "name": "Private",
            "code": "Private",
            "active": true
        }
    ]
}
```

**VehicleMakeModel**

```
{
    "tenantId": "pb",
    "moduleName": "Vehicle",
    "VehicleMakeModel": [
        {
            "code": "MAHINDRA",
            "name": "Mahindra",
            "active": true
        },
        {
            "code": "MAHINDRA.BOLERO_PICKUP",
            "name": "Bolero Pickup",
            "active": true,
            "make": "MAHINDRA",
            "capacity": "5000",
            "amount": "500"
        },
        {
            "code": "TATA",
            "name": "TATA",
            "active": true
        },
        {
            "code": "TATA.LPT709/34",
            "name": "TATA LPT709/34",
            "active": true,
            "make": "TATA",
            "capacity": "2000",
            "amount": "200"
        },
        {
            "code": "TATA.407",
            "name": "TATA 407",
            "active": true,
            "make": "TATA",
            "capacity": "1000",
            "amount": "100"
        },
        {
            "code": "TAFE",
            "name": "TAFE",
            "active": true
        },
        {
            "code": "TAFE.TRACTOR_45DI",
            "name": "TAFE Tractor 45DI",
            "active": true,
            "make": "TAFE",
            "capacity": "10000",
            "amount": "1000"
        },
        {
            "code": "SONALIKA",
            "name": "Sonalika",
            "active": true
        },
        {
            "code": "SONALIKA.TRACTOR_35DI",
            "name": "Sonalika Tractor 35DI",
            "active": true,
            "make": "SONALIKA",
            "capacity": "8000",
            "amount": "1000"
        }
    ]
}
```

**FSTPO Rejection Reason (Vehicle decline reason codes)**

```
{
    "tenantId": "pb",
    "moduleName": "Vehicle",
    "FSTPORejectionReason": [{
            "name": "Septage Source",
            "code": "SEPTAGE_SOURCE",
            "active": true
        },
        {
            "name": "Outside operational hours",
            "code": "OUTSIDE_OPERATIONAL_HOURS",
            "active": true
        },
        {
            "name": "Under Maintenance",
            "code": "UNDER_MAINTENANCE",
            "active": true
        },
        {
            "name": "Others",
            "code": "OTHERS",
            "active": true
        }
    ]
}
```

[SAN-1049: Added role actions for Driver APIs. · egovernments/egov-mdms-data@fb8e530](https://github.com/egovernments/egov-mdms-data/commit/fb8e53037bf5ff40ca78506b02a8d7b04dc96e88)

[SAN-1063: Added the permissiosn for Vehicle trip creation · egovernments/egov-mdms-data@632ee94](https://github.com/egovernments/egov-mdms-data/commit/632ee94e95d74ddb1d3f306ec83e3de02a329a2a)

[SAN-1047: Added role action mapping for vendor and vehicle update · egovernments/egov-mdms-data@3e608a8](https://github.com/egovernments/egov-mdms-data/commit/3e608a844be189d5be1d0657b4d8b1b663b6e94c)

**Business Service/Workflow Configuration**

1. Search the FSM\_VEHICLE\_TRIP workflow by the given search API.

&#x20;/egov-workflow-v2/egov-wf/businessservice/\_search? tenantId=pb.amritsar\&businessServices=FSM\_VEHICLE\_TRIP

2\. Update this below given action at “null” state at line no. 20  for FSM\_VEHICLE\_TRIP in below workflow and restart the workflow service.

```
{
  "action": "READY_FOR_DISPOSAL",
  "currentState": "61e01ccd-be34-4705-ae82-13ae93200fb3",
  "nextState": "e217e14a-7d3a-41bc-ae31-7ab2dce26f02",
  "roles": [
    "FSM_DSO",
    "FSM_EDITOR_EMP",
    "FSM_EMP_FSTPO"
  ],
  "active": true
}

"BusinessServices": [
       {
           "tenantId": "pb.amritsar",
           "uuid": "22c802e6-5354-43be-979a-8a653753459e",
           "businessService": "FSM_VEHICLE_TRIP",
           "business": "vehicle",
           "businessServiceSla": 172800000,
           "states": [
               {
                   "auditDetails": {
                       "createdBy": "11b0e02b-0145-4de2-bc42-c97b96264807",
                       "lastModifiedBy": "157fc9f6-836f-4780-ba89-9e511f65099e",
                       "createdTime": 1613116718088,
                       "lastModifiedTime": 1654241412659
                   },
                   "uuid": "61e01ccd-be34-4705-ae82-13ae93200fb3",
                   "tenantId": "pb.amritsar",
                   "businessServiceId": "22c802e6-5354-43be-979a-8a653753459e",
                   "sla": null,
                   "state": null, 
                   "applicationStatus": null,
                   "docUploadRequired": false,
                   "isStartState": true,
                   "isTerminateState": false,
                   "isStateUpdatable": true,
                   "actions": [
                       {
                           "auditDetails": {
                               "createdBy": "157fc9f6-836f-4780-ba89-9e511f65099e",
                               "lastModifiedBy": "157fc9f6-836f-4780-ba89-9e511f65099e",
                               "createdTime": 1654241412659,
                               "lastModifiedTime": 1654241412659
                           },
                           "uuid": "344d60a6-b415-4937-8a20-e1a70d767f01",
                           "tenantId": "pb.amritsar",
                           "currentState": "61e01ccd-be34-4705-ae82-13ae93200fb3",
                           "action": "CREATE_FSTPO_VEHICLE_LOG",
                           "nextState": "0fec53d3-6940-44c9-8582-2a09bd1f413a",
                           "roles": [
                               "FSM_EMP_FSTPO"
                           ],
                           "active": true
                       },
                       {
                           "auditDetails": {
                               "createdBy": "11b0e02b-0145-4de2-bc42-c97b96264807",
                               "lastModifiedBy": "157fc9f6-836f-4780-ba89-9e511f65099e",
                               "createdTime": 1613116718088,
                               "lastModifiedTime": 1654241412659
                           },
                           "uuid": "96e88b11-25d8-4cc1-b35c-6ce5edcb5904",
                           "tenantId": "pb.amritsar",
                           "currentState": "61e01ccd-be34-4705-ae82-13ae93200fb3",
                           "action": "SCHEDULE",
                           "nextState": "71f17154-40b8-4595-903a-c8d93c124abe",
                           "roles": [
                               "FSM_DSO",
                               "FSM_EDITOR_EMP",
                               "FSM_EMP_FSTPO"
                           ],
                           "active": true
                       },
                       {
                           "action": "READY_FOR_DISPOSAL",
                           "currentState": "61e01ccd-be34-4705-ae82-13ae93200fb3",
                           "nextState": "e217e14a-7d3a-41bc-ae31-7ab2dce26f02",
                           "roles": [
                               "FSM_DSO",
                               "FSM_EDITOR_EMP",
                               "FSM_EMP_FSTPO"
                           ],
                           "active": true
                       }
                   ]
               },
               {
                   "auditDetails": {
                       "createdBy": "11b0e02b-0145-4de2-bc42-c97b96264807",
                       "lastModifiedBy": "157fc9f6-836f-4780-ba89-9e511f65099e",
                       "createdTime": 1613116718088,
                       "lastModifiedTime": 1654241412659
                   },
                   "uuid": "71f17154-40b8-4595-903a-c8d93c124abe",
                   "tenantId": "pb.amritsar",
                   "businessServiceId": "22c802e6-5354-43be-979a-8a653753459e",
                   "sla": null,
                   "state": "SCHEDULED",
                   "applicationStatus": "SCHEDULED",
                   "docUploadRequired": false,
                   "isStartState": true,
                   "isTerminateState": false,
                   "isStateUpdatable": true,
                   "actions": [
                       {
                           "auditDetails": {
                               "createdBy": "11b0e02b-0145-4de2-bc42-c97b96264807",
                               "lastModifiedBy": "157fc9f6-836f-4780-ba89-9e511f65099e",
                               "createdTime": 1613116718088,
                               "lastModifiedTime": 1654241412659
                           },
                           "uuid": "b82e310e-a519-4ee8-8aaf-550cccbe26b2",
                           "tenantId": "pb.amritsar",
                           "currentState": "71f17154-40b8-4595-903a-c8d93c124abe",
                           "action": "READY_FOR_DISPOSAL",
                           "nextState": "e217e14a-7d3a-41bc-ae31-7ab2dce26f02",
                           "roles": [
                               "FSM_DSO",
                               "FSM_EDITOR_EMP",
                               "FSM_EMP_FSTPO"
                           ],
                           "active": true
                       }
                   ]
               },
               {
                   "auditDetails": {
                       "createdBy": "11b0e02b-0145-4de2-bc42-c97b96264807",
                       "lastModifiedBy": "157fc9f6-836f-4780-ba89-9e511f65099e",
                       "createdTime": 1613116718088,
                       "lastModifiedTime": 1654241412659
                   },
                   "uuid": "e217e14a-7d3a-41bc-ae31-7ab2dce26f02",
                   "tenantId": "pb.amritsar",
                   "businessServiceId": "22c802e6-5354-43be-979a-8a653753459e",
                   "sla": null,
                   "state": "WAITING_FOR_DISPOSAL",
                   "applicationStatus": "WAITING_FOR_DISPOSAL",
                   "docUploadRequired": false,
                   "isStartState": true,
                   "isTerminateState": false,
                   "isStateUpdatable": true,
                   "actions": [
                       {
                           "auditDetails": {
                               "createdBy": "11b0e02b-0145-4de2-bc42-c97b96264807",
                               "lastModifiedBy": "157fc9f6-836f-4780-ba89-9e511f65099e",
                               "createdTime": 1643360911202,
                               "lastModifiedTime": 1654241412659
                           },
                           "uuid": "9a8b4fd2-8954-48b4-b593-b5ae273ea33f",
                           "tenantId": "pb.amritsar",
                           "currentState": "e217e14a-7d3a-41bc-ae31-7ab2dce26f02",
                           "action": "DECLINEVEHICLE",
                           "nextState": "15c550df-8369-47fd-816d-c24a07861c5a",
                           "roles": [
                               "FSM_EMP_FSTPO"
                           ],
                           "active": true
                       },
                       {
                           "auditDetails": {
                               "createdBy": "11b0e02b-0145-4de2-bc42-c97b96264807",
                               "lastModifiedBy": "157fc9f6-836f-4780-ba89-9e511f65099e",
                               "createdTime": 1613116718088,
                               "lastModifiedTime": 1654241412659
                           },
                           "uuid": "c83445e8-c658-4a29-b69d-29f30a8be7ff",
                           "tenantId": "pb.amritsar",
                           "currentState": "e217e14a-7d3a-41bc-ae31-7ab2dce26f02",
                           "action": "DISPOSE",
                           "nextState": "0fec53d3-6940-44c9-8582-2a09bd1f413a",
                           "roles": [
                               "FSM_EMP_FSTPO"
                           ],
                           "active": true
                       }
                   ]
               },
               {
                   "auditDetails": {
                       "createdBy": "11b0e02b-0145-4de2-bc42-c97b96264807",
                       "lastModifiedBy": "157fc9f6-836f-4780-ba89-9e511f65099e",
                       "createdTime": 1613116718088,
                       "lastModifiedTime": 1654241412659
                   },
                   "uuid": "0fec53d3-6940-44c9-8582-2a09bd1f413a",
                   "tenantId": "pb.amritsar",
                   "businessServiceId": "22c802e6-5354-43be-979a-8a653753459e",
                   "sla": null,
                   "state": "DISPOSED",
                   "applicationStatus": "DISPOSED",
                   "docUploadRequired": false,
                   "isStartState": false,
                   "isTerminateState": true,
                   "isStateUpdatable": true,
                   "actions": null
               },
               {
                   "auditDetails": {
                       "createdBy": "11b0e02b-0145-4de2-bc42-c97b96264807",
                       "lastModifiedBy": "157fc9f6-836f-4780-ba89-9e511f65099e",
                       "createdTime": 1643360911202,
                       "lastModifiedTime": 1654241412659
                   },
                   "uuid": "15c550df-8369-47fd-816d-c24a07861c5a",
                   "tenantId": "pb.amritsar",
                   "businessServiceId": "22c802e6-5354-43be-979a-8a653753459e",
                   "sla": null,
                   "state": "VEHICLE_DECLINED",
                   "applicationStatus": "VEHICLE_DECLINED",
                   "docUploadRequired": false,
                   "isStartState": false,
                   "isTerminateState": true,
                   "isStateUpdatable": true,
                   "actions": null
               },
               {
                   "auditDetails": {
                       "createdBy": "157fc9f6-836f-4780-ba89-9e511f65099e",
                       "lastModifiedBy": "157fc9f6-836f-4780-ba89-9e511f65099e",
                       "createdTime": 1654105652933,
                       "lastModifiedTime": 1654241412659
                   },
                   "uuid": "4c97dd1b-ebcf-424b-bc68-037c17e29194",
                   "tenantId": "pb.amritsar",
                   "businessServiceId": "22c802e6-5354-43be-979a-8a653753459e",
                   "sla": null,
                   "state": null,
                   "applicationStatus": null,
                   "docUploadRequired": false,
                   "isStartState": true,
                   "isTerminateState": false,
                   "isStateUpdatable": true,
                   "actions": [
                       {
                           "auditDetails": {
                               "createdBy": "157fc9f6-836f-4780-ba89-9e511f65099e",
                               "lastModifiedBy": "157fc9f6-836f-4780-ba89-9e511f65099e",
                               "createdTime": 1654105652933,
                               "lastModifiedTime": 1654241412659
                           },
                           "uuid": "01a3ec24-a89a-4169-98ba-13b483ff417e",
                           "tenantId": "pb.amritsar",
                           "currentState": "4c97dd1b-ebcf-424b-bc68-037c17e29194",
                           "action": "CREATE_FSTPO_LOG",
                           "nextState": "0fec53d3-6940-44c9-8582-2a09bd1f413a",
                           "roles": [
                               "FSM_EMP_FSTPO"
                           ],
                           "active": true
                       }
                   ]
               }
           ],
           "auditDetails": {
               "createdBy": "11b0e02b-0145-4de2-bc42-c97b96264807",
               "lastModifiedBy": "157fc9f6-836f-4780-ba89-9e511f65099e",
               "createdTime": 1613116718088,
               "lastModifiedTime": 1654241412659
           }
       }
   ]
```

### Actions & Role Action Mapping <a href="#actions-and-role-action-mapping" id="actions-and-role-action-mapping"></a>

**Actions**

```
{
      "id": {{PLACEHOLDER1}},
      "name": "Create Vehicle Application",
      "url": "/vehicle/v1/_create",
      "displayName": "Create Vehicle",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "vehicle",
      "code": "null",
      "path": ""
    },
    {
      "id":  {{PLACEHOLDER2}},
      "name": "Search Vehicle Application",
      "url": "/vehicle/v1/_search",
      "displayName": "Search  Vehicle",
      "orderNumber": 1,
      "enabled": false,
      "serviceCode": "vehicle",
      "code": "null",
      "path": ""
    },
    {
      "id": {{PLACEHOLDER3}},
      "name": "Vehicle Trip Search",
       "url": "/vehicle/trip/v1/_search",
      "displayName": "Vehicle Trip Search",
      "orderNumber": 1,
      "parentModule": "",
      "enabled": false,
      "serviceCode": "",
      "code": "null",
      "path": ""
    },
    {
      "id": {{PLACEHOLDER4}},
      "name": "Vehicle Trip Update",
       "url": "/vehicle/trip/v1/_update",
      "displayName": "Vehicle Trip Update",
      "orderNumber": 1,
      "parentModule": "",
      "enabled": false,
      "serviceCode": "",
      "code": "null",
      "path": ""
    },
    {
      "id": {{PLACEHOLDER5}},
      "name": "Vehicle Trip Create",
      "url": "/vehicle/trip/v1/_create",
      "displayName": "Vehicle Trip Create",
      "orderNumber": 1,
      "parentModule": "",
      "enabled": false,
      "serviceCode": "vehicle",
      "code": "null",
      "path": ""
    },

{
  "id": {{PLACEHOLDER6}},
  "name": "Update Vehicle Application",
  "url": "/vehicle/v1/_update",
  "displayName": "Update Vehicle",
  "orderNumber": 0,
  "enabled": false,
  "serviceCode": "vehicle",
  "code": "null",
  "path": ""
}
```

**Role Action Mapping**

```
[
  {
    "rolecode": "FSM_ADMIN",
    "actionid": {{PLACEHOLDER1}},
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_ADMIN",
    "actionid": {{PLACEHOLDER2}},
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_DSO",
    "actionid":  {{PLACEHOLDER2}},
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_EDITOR_EMP",
    "actionid":  {{PLACEHOLDER2}},
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_VIEW_EMP",
    "actionid":  {{PLACEHOLDER2}},
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_EMP_FSTPO",
    "actionid":  {{PLACEHOLDER2}},
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_EMP_FSTPO",
    "actionid": {{PLACEHOLDER3}},
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_EMP_FSTPO",
    "actionid":{{PLACEHOLDER4}},
    "actioncode": "",
    "tenantId": "pb"
  },
  {
      "rolecode": "FSM_EMP_FSTPO",
      "actionid": {{PLACEHOLDER5}},
      "actioncode": "",
      "tenantId": "pb"
    },
]
{
  "rolecode": "FSM_ADMIN",
  "actionid": {{PLACEHOLDER6}},
  "actioncode": "",
  "tenantId": "pb"
},
```

### **Infra Ops Configuration**

Configurations that we can manage through values.yml vehicle in infraops repo are listed below. \
values.yml for the vehicle can be found.

| Description                                                                    | name in values.yml                                | Current Value                                                |
| ------------------------------------------------------------------------------ | ------------------------------------------------- | ------------------------------------------------------------ |
| id-gen host, to generate the application number                                | EGOV\_IDGEN\_HOST                                 | egov-idgen from egov-service-host                            |
| mdms service host                                                              | EGOV\_MDMS\_HOST                                  | egov-mdms-service from egov-service-host                     |
| workflow v2 service host                                                       | WORKFLOW\_CONTEXT\_PATH                           | egov-workflow-v2 from egov-service-host                      |
| user service host, to get the locale data                                      | EGOV\_USER\_HOST                                  | egov-user from egov-service-host                             |
| Kafka Consumer Group                                                           | SPRING\_KAFKA\_CONSUMER\_GROUP\_ID                | egov-vehicle-services                                        |
| kafka topic to which service push data to save new vehicle application         | PERSISTER\_SAVE\_VEHICLE\_TOPIC                   | save-vehicle-application                                     |
| kafka topic to which service push data of the vehicleTrip to save              | PERSISTER\_SAVE\_VEHICLE\_TRIP\_TOPIC             | save-vehicle-trip                                            |
| kafka topic to which service push data of the vehicleTrip to update            | PERSISTER\_UPDATE\_VEHICLE\_TRIP\_TOPIC           | update-vehicle-trip                                          |
| kafka topic to which service push data of the vehicleTrip to update the status | PERSISTER\_UPDATE\_VEHICLE\_TRIP\_WORKFLOW\_TOPIC | update-workflow-vehicle-trip                                 |
| VehicleTrip Appilcatiion Number format\`                                       | egov.idgen.vehicle.trip.applicationNum.format     | "\[CITY.CODE]-VT-\[cy:yyyy-MM-dd]-\[SEQ\_EGOV\_VEHICLETRIP]" |

**Configurations sample in Values.yml**

```
egov.idgen.vehicle.trip.applicationNum.format: "[CITY.CODE]-VT-[cy:yyyy-MM-dd]-[SEQ_EGOV_VEHICLETRIP]"

# Additional Container Envs
env: |
  - name: EGOV_IDGEN_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-idgen
  - name: EGOV_HRMS_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-hrms
  - name: EGOV_MDMS_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-mdms-service
  - name: EGOV_USER_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-user
  - name: WORKFLOW_CONTEXT_PATH
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-workflow-v2
  - name: WORKFLOW_TRANSITION_PATH
    value: "egov-workflow-v2/egov-wf/process/_transition"
  - name: EGOV_IDEN_VEHICLE_TRIP_APPLICATIONNUM_FORMAT
    value: "[CITY.CODE]-VT-[cy:yyyy-MM-dd]-[SEQ_EGOV_VEHICLETRIP]"
  - name: SPRING_KAFKA_CONSUMER_GROUP_ID
    value: egov-vehicle-services
  - name: PERSISTER_SAVE_VEHICLE_TOPIC
    value: save-vehicle-application
  - name: PERSISTER_UPDATE_VEHICLE_TOPIC
    value: update-vehicle-application
  - name: PERSISTER_SAVE_VEHICLE_TRIP_TOPIC
    value: save-vehicle-trip
  - name: PERSISTER_UPDATE_VEHICLE_TRIP_TOPIC
    value: update-vehicle-trip
  - name: PERSISTER_UPDATE_VEHICLE_TRIP_WORKFLOW_TOPIC
    value: update-workflow-vehicle-trip 
  - name: SPRING_KAFKA_PRODUCER_KEY_SERIALIZER
    value: org.apache.kafka.common.serialization.StringSerializer
  - name: SPRING_KAFKA_PRODUCER_VALUE_SERIALIZER
    value: org.springframework.kafka.support.serializer.JsonSerializer
  - name: JAVA_OPTS
    value: {{ index .Values "heap" | quote }}
  - name: JAVA_ARGS
    value: {{ index .Values "java-args" | quote }}
  - name: SERVER_PORT
    value: "8080"
  - name: SECURITY_BASIC_ENABLED
    value: "false"  
  - name: MANAGEMENT_SECURITY_ENABLED
    value: "false"
  {{- if index .Values "tracing-enabled" }}
  - name: TRACER_OPENTRACING_ENABLED
    value: "true" 
  {{- end }}
```

[DIGIT-DevOps/values.yaml at master · egovernments/DIGIT-DevOps](https://github.com/egovernments/DIGIT-DevOps/blob/master/deploy-as-code/helm/charts/sanitation/vehicle/values.yaml)&#x20;

## Data Setup <a href="#data-setup" id="data-setup"></a>

#### Create Vehicle <a href="#create-vehicle" id="create-vehicle"></a>

Create a vehicle with one of the vehicle types available in the VehicleMakeModel MDMS.

**Sample Curl**

```
curl 'https://dev.digit.org/vehicle/v1/_create?tenantId=pb.amritsar' \
  -H 'authority: dev.digit.org' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-GB,en-US;q=0.9,en;q=0.8' \
  -H 'content-type: application/json;charset=UTF-8' \
  -H 'cookie: _ga=GA1.2.1852108775.1653914860; intercom-id-xp1951jv=17aa7431-3dc0-4524-9956-a22bb67a637f; __cuid=858e6f9f233c4b2c804d3f81109b48ac; amp_fef1e8=7faa94f4-6926-4f98-ac07-be2414f977c6R...1gkkb64lb.1gkkb6kvh.7p.a.83' \
  -H 'origin: https://dev.digit.org' \
  -H 'referer: https://dev.digit.org/digit-ui/employee/fsm/registry/new-vehicle' \
  -H 'sec-ch-ua: "Google Chrome";v="107", "Chromium";v="107", "Not=A?Brand";v="24"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "Linux"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-origin' \
  -H 'user-agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/107.0.0.0 Safari/537.36' \
  --data-raw '{"vehicle":{"tenantId":"pb.amritsar","registrationNumber":"AS 12 AS 1234","model":"MAHINDRA","type":"MAHINDRA.BOLERO_PICKUP","tankCapacity":"5000","suctionType":"SEWER_SUCTION_MACHINE","pollutionCertiValidTill":null,"InsuranceCertValidTill":null,"fitnessValidTill":null,"roadTaxPaidTill":null,"gpsEnabled":true,"source":"Municipal records","owner":{"tenantId":"pb","name":"raj","fatherOrHusbandName":"raj","relationship":"OTHER","gender":"OTHERS","dob":-19800000,"emailId":"abc@egov.com","correspondenceAddress":"","mobileNumber":"9876543210"},"additionalDetails":{"description":""}},"RequestInfo":{"apiId":"Rainmaker","authToken":"df28f073-4caf-456e-bd43-1943ce76548c","userInfo":{"id":28452,"uuid":"5674253d-9c2a-4d47-88ae-450f3fbbcad2","userName":"BPAFieldInspector","name":"lakshmi","mobileNumber":"8656565343","emailId":null,"locale":null,"type":"EMPLOYEE","roles":[{"name":"FSM Administrator","code":"FSM_ADMIN","tenantId":"pb.amritsar"},{"name":"BPA Services Approver","code":"BPA_APPROVER","tenantId":"pb.amritsar"},{"name":"Employee","code":"EMPLOYEE","tenantId":"pb.amritsar"},{"name":"FSM Employee Report Viewer","code":"FSM_REPORT_VIEWER","tenantId":"pb.amritsar"},{"name":"BPA Services verifier","code":"BPA_VERIFIER","tenantId":"pb.amritsar"},{"name":"BPA Field Inspector","code":"BPA_FIELD_INSPECTOR","tenantId":"pb.amritsar"},{"name":"BPAREG doc verifier","code":"BPAREG_DOC_VERIFIER","tenantId":"pb.amritsar"}],"active":true,"tenantId":"pb.amritsar","permanentCity":null},"msgId":"1671428547643|en_IN","plainAccessRequest":{}}}' \
  --compressed
```

## Integration <a href="#integration-scope" id="integration-scope"></a>

### Integration Scope <a href="#integration-scope" id="integration-scope"></a>

Integrated with the application through REST API to create, and search vehicles. For any module where the vehicle trip is required, one can integrate REST API trip/v1/create, update, and search.

### Integration Benefits <a href="#integration-benefits" id="integration-benefits"></a>

* Vehicle management would become easy.
* Trip management would become easy.

### Steps to Integration <a href="#steps-to-integration" id="steps-to-integration"></a>

* FSM application can vehicle/v1/\_search to validate the FSM vehicle assignment.
* FSM application call vehicle/trip/v1/\_create on assigning vehicle to the spplication.
* FSTP operators can mark the vehicleTrip as DISPOSED.

### Interaction Diagrams <a href="#interaction-diagram" id="interaction-diagram"></a>

<figure><img src="../../../.gitbook/assets/Screenshot 2023-03-28 at 3.57.53 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/Screenshot 2023-03-28 at 3.58.04 PM.png" alt=""><figcaption></figcaption></figure>

## Reference Docs <a href="#reference-docs" id="reference-docs"></a>

### Doc Links <a href="#doc-links" id="doc-links"></a>

| Workflow Technical Document         | <p> </p><p><a href="https://digit-discuss.atlassian.net/wiki/spaces/DD/pages/664174657">Workflow Service</a></p>                                                                   |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| User technical document             | [User Service](https://digit-discuss.atlassian.net/wiki/spaces/DD/pages/669450371)                                                                                                 |
| MDMS technical document             | NEEDS TO BE UPDATED                                                                                                                                                                |
| IDGen technical document            | NEEDS TO BE UPDATED                                                                                                                                                                |
| Localisation technical document     | NEEDS TO BE UPDATED                                                                                                                                                                |
| Persister technical document        | NEEDS TO BE UPDATED                                                                                                                                                                |
| SMS notification technical document | NEEDS TO BE UPDATED                                                                                                                                                                |
| API contract                        | [API Contract](https://editor.swagger.io/?url=https://raw.githubusercontent.com/egovernments/DIGIT-OSS/master/municipal-services/docs/fsm/Vehicle\_Registry\_Contract-v1.1.0.yaml) |
| Postman scripts                     | [Postman Collection](https://www.getpostman.com/collections/6d99bb40022396f848b2)                                                                                                  |

### API List <a href="#api-list" id="api-list"></a>

&#x20;

| Title                          | Link                                                                                                                                                                                                                                                           |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| vehicle/v1/\_create            | [https://www.getpostman.com/collections/6d99bb40022396f848b2](https://www.getpostman.com/collections/6d99bb40022396f848b2)                                                                                                                                     |
| vehicle/v1/\_search            | [https://www.getpostman.com/collections/6d99bb40022396f848b2](https://www.getpostman.com/collections/6d99bb40022396f848b2)                                                                                                                                     |
| /vehicle/v1/\_plainsearch      | [https://www.getpostman.com/collections/6d99bb40022396f848b2](https://www.getpostman.com/collections/6d99bb40022396f848b2)                                                                                                                                     |
| /vehicle/trip/v1/\_create      | [https://www.getpostman.com/collections/4d425d97a5db5ced11b6](https://www.getpostman.com/collections/4d425d97a5db5ced11b6)                                                                                                                                     |
| vehicle/trip/v1/\_update       | [https://www.getpostman.com/collections/6d99bb40022396f848b2](https://www.getpostman.com/collections/6d99bb40022396f848b2)                                                                                                                                     |
| vehicle/trip/v1/\_search       | [https://www.getpostman.com/collections/6d99bb40022396f848b2](https://www.getpostman.com/collections/6d99bb40022396f848b2)                                                                                                                                     |
| /vehicle/trip/v1/\_plainsearch | [https://www.getpostman.com/collections/6d99bb40022396f848b2](https://www.getpostman.com/collections/6d99bb40022396f848b2)                                                                                                                                     |
| vehicle/v1/\_update            | [https://api.postman.com/collections/23418568-a15793e6-edeb-4393-a6b8-38fd90deca6f?access\_key=PMAT-01GMQPGY7NKF54DP47PEJH6NZG](https://api.postman.com/collections/23418568-a15793e6-edeb-4393-a6b8-38fd90deca6f?access\_key=PMAT-01GMQPGY7NKF54DP47PEJH6NZG) |
