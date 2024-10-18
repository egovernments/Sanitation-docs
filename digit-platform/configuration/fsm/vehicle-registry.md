# Vehicle Registry

## Configuration Details <a href="#configuration-details" id="configuration-details"></a>

[Update vehicle-persister.yaml · egovernments/configs@32a7e1b](https://github.com/egovernments/configs/commit/32a7e1b606ac2b7466c83007e07d104d75153695)

[Update vehicle-persister.yaml · egovernments/configs@23237c8](https://github.com/egovernments/configs/commit/23237c8f467684c452461c5d0bf88ff54157fb8b)

[added jsonb data type for additionalDetails column in save-vehicle-ap… · egovernments/configs@9b2f604](https://github.com/egovernments/configs/commit/9b2f6043694a2f23e5a2bce83600e4b41a99b7f5)

[Added the audit logging for vehicle and vendor · egovernments/configs@482185f](https://github.com/egovernments/configs/commit/482185f1a79ad094f716e480922374e40c6e217a)

[SAN-1047 - Added the query map for update vehicle and vendor topics. · egovernments/configs@56da639](https://github.com/egovernments/configs/commit/56da639add16c412056aeac119517abd434a5ece)

[History for egov-persister/vehicle-persister.yaml - egovernments/configs](https://github.com/egovernments/configs/commits/DEV/egov-persister/vehicle-persister.yaml)

[configs/vendor-persister.yaml at DEV · egovernments/configs](https://github.com/egovernments/configs/blob/DEV/egov-persister/vendor-persister.yaml)

## MDMS Configuration <a href="#mdms-configuration-hardbreak" id="mdms-configuration-hardbreak"></a>

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

## **Business Service/Workflow Configuration** <a href="#business-service-workflow-configuration" id="business-service-workflow-configuration"></a>

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

## Actions & Role Action Mapping <a href="#actions-and-role-action-mapping" id="actions-and-role-action-mapping"></a>

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

###
