# Workflow Configuration Changes

## FSM vehicle trip update business service request

### Instructions for production execution:

* Replace the tenant id for the production environment.
* Replace the request information object with the production user information details.
* Fetch the production instance of the FSM\_VEHICLE\_TRIP business object and add the vehicle decline action, and state in the business service definition. Then use the \_update business service for updating the workflow for vehicle trips.

```
{
    "RequestInfo": {
        "apiId": "Rainmaker",
        "authToken": "7880fbab-6858-41a1-86ad-444b7e2e75c7",
        "userInfo": {
            "id": 12070,
            "uuid": "97a111f0-e2fc-40ee-976f-96acfa1d085b",
            "userName": "QAEE",
            "name": "Employee Editor",
            "mobileNumber": "9922999999",
            "emailId": "",
            "locale": null,
            "type": "EMPLOYEE",
            "roles": [
                {
                    "name": "FSM Employee Application Viewer",
                    "code": "FSM_VIEW_EMP",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "Employee",
                    "code": "EMPLOYEE",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "FSM Employee Application Editor",
                    "code": "FSM_EDITOR_EMP",
                    "tenantId": "pg.citya"
                }
            ],
            "active": true,
            "tenantId": "pg.citya",
            "permanentCity": null
        },
        "msgId": "1646405030385|en_IN"
    },
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

### Instructions for production execution:

* Replace the tenant id for the production environment.
* Replace the request information object with the production user information details.
* Fetch the production instance of the FSM\_VEHICLE\_TRIP business object, add the READY\_FOR\_DISPOSALaction at state : null  in the Business service definition, and then use the \_update business service for updating the workflow for a vehicle trip.

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
        "authToken": "b314c3d7-98e4-4421-ae29-ef1ef4db8fed"
    },
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

### New additions

In the system, the FSM\_POST\_PAY\_SERVICE and FSM were removed and we introduced a new business service for the advance payment application and the zero price application:

* For the advance new business service FSM\_ADVANCE\_PAY\_SERVICE has been created.
* The advance pay works based on the configuration percentage, that is, how much the payer needs to pay during the application creation.

Create businessService (workflow configuration) using the  /businessservice/\_create. Following is the product configuration for FSM\_ADVANCE\_PAY\_SERVICE.

```
{


    "BusinessServices": [


        {


            "tenantId": "pb",


            "businessService": "FSM_ADVANCE_PAY_SERVICE",


            "business": "fsm",


            "businessServiceSla": 172800000,


            "states": [


                {


                    "tenantId": "pb",


                    "sla": null,


                    "state": null,


                    "applicationStatus": null,


                    "docUploadRequired": false,


                    "isStartState": true,


                    "isTerminateState": false,


                    "isStateUpdatable": true,


                    "actions": [


                        {


                            "tenantId": "pb",


                            "action": "APPLY",


                            "nextState": "PENDING_APPL_FEE_PAYMENT",


                            "roles": [


                                "FSM_CREATOR_EMP"


                            ]


                        },


                        {


                            "tenantId": "pb",


                            "action": "CREATE",


                            "nextState": "CREATED",


                            "roles": [


                                "CITIZEN"


                            ]


                        }


                    ]


                },


                {


                    "tenantId": "pb",


                    "sla": null,


                    "state": "CREATED",


                    "applicationStatus": "CREATED",


                    "docUploadRequired": false,


                    "isStartState": false,


                    "isTerminateState": false,


                    "isStateUpdatable": true,


                    "actions": [


                        {


                            "tenantId": "pb",


                            "action": "REJECT",


                            "nextState": "REJECTED",


                            "roles": [


                                "FSM_ADMIN"


                            ]


                        },


                        {


                            "tenantId": "pb",


                            "action": "SUBMIT",


                            "nextState": "PENDING_APPL_FEE_PAYMENT",


                            "roles": [


                                "FSM_EDITOR_EMP"


                            ]


                        }


                    ]


                },


                {


                    "tenantId": "pb",


                    "sla": null,


                    "state": "PENDING_APPL_FEE_PAYMENT",


                    "applicationStatus": "PENDING_APPL_FEE_PAYMENT",


                    "docUploadRequired": false,


                    "isStartState": false,


                    "isTerminateState": false,


                    "isStateUpdatable": true,


                    "actions": [


                        {


                            "tenantId": "pb",


                            "action": "REJECT",


                            "nextState": "REJECTED",


                            "roles": [


                                "FSM_ADMIN"


                            ]


                        },


                        {


                            "tenantId": "pb",


                            "action": "SENDBACK",


                            "nextState": "CREATED",


                            "roles": [


                                "FSM_ADMIN"


                            ]


                        },


                        {


                            "tenantId": "pb",


                            "action": "PAY",


                            "nextState": "ASSING_DSO",


                            "roles": [


                                "CITIZEN",


                                "FSM_COLLECTOR"


                            ]


                        }


                    ]


                },


                {


                    "tenantId": "pb",


                    "sla": null,


                    "state": "ASSING_DSO",


                    "applicationStatus": "ASSING_DSO",


                    "docUploadRequired": false,


                    "isStartState": false,


                    "isTerminateState": false,


                    "isStateUpdatable": true,


                    "actions": [


                        {


                            "tenantId": "pb",


                            "action": "CANCEL",


                            "nextState": "CANCELED",


                            "roles": [


                                "FSM_ADMIN"


                            ]


                        },


                        {


                            "tenantId": "pb",


                            "action": "ASSIGN",


                            "nextState": "PENDING_DSO_APPROVAL",


                            "roles": [


                                "FSM_EDITOR_EMP"


                            ]


                        }


                    ]


                },


                {


                    "tenantId": "pb",


                    "sla": null,


                    "state": "DSO_REJECTED",


                    "applicationStatus": "DSO_REJECTED",


                    "docUploadRequired": false,


                    "isStartState": false,


                    "isTerminateState": false,


                    "isStateUpdatable": true,


                    "actions": [


                        {


                            "tenantId": "pb",


                            "currentState": "DSO_REJECTED",


                            "action": "CANCEL",


                            "nextState": "CANCELED",


                            "roles": [


                                "FSM_ADMIN"


                            ]


                        },


                        {


                            "tenantId": "pb",


                            "currentState": "DSO_REJECTED",


                            "action": "REASSING",


                            "nextState": "PENDING_DSO_APPROVAL",


                            "roles": [


                                "FSM_EDITOR_EMP"


                            ]


                        },


                        {


                            "tenantId": "pb",


                            "currentState": "DSO_REJECTED",


                            "action": "SENDBACK",


                            "nextState": "PENDING_DSO_APPROVAL",


                            "roles": [


                                "FSM_ADMIN"


                            ]


                        }


                    ]


                },


                {


                    "tenantId": "pb",


                    "sla": null,


                    "state": "DSO_INPROGRESS",


                    "applicationStatus": "DSO_INPROGRESS",


                    "docUploadRequired": false,


                    "isStartState": false,


                    "isTerminateState": false,


                    "isStateUpdatable": true,


                    "actions": [


                        {


                            "tenantId": "pb",


                            "currentState": "DSO_INPROGRESS",


                            "action": "SENDBACK",


                            "nextState": "PENDING_DSO_APPROVAL",


                            "roles": [


                                "FSM_ADMIN"


                            ]


                        },


                        {


                            "tenantId": "pb",


                            "currentState": "DSO_INPROGRESS",


                            "action": "COMPLETED",


                            "nextState": "CITIZEN_FEEDBACK_PENDING",


                            "roles": [


                                "FSM_DSO",


                                "FSM_EDITOR_EMP"


                            ]


                        },


                        {


                            "tenantId": "pb",


                            "currentState": "DSO_INPROGRESS",


                            "action": "CANCEL",


                            "nextState": "CANCELED",


                            "roles": [


                                "FSM_ADMIN"


                            ]


                        },


                        {


                            "tenantId": "pb",


                            "currentState": "DSO_INPROGRESS",


                            "action": "UPDATE",


                            "nextState": "DSO_INPROGRESS",


                            "roles": [


                                "FSM_DSO",


                                "FSM_EDITOR_EMP"


                            ]


                        },


                        {


                            "tenantId": "pb",


                            "action": "PAY",


                            "nextState": "DSO_INPROGRESS",


                            "roles": [


                                "CITIZEN",


                                "FSM_COLLECTOR"


                            ]


                        },


                        {


                            "tenantId": "pb",


                            "currentState": "DSO_INPROGRESS",


                            "action": "REASSING",


                            "nextState": "PENDING_DSO_APPROVAL",


                            "roles": [


                                "FSM_EDITOR_EMP"


                            ]


                        }


                    ]


                },


                {


                    "tenantId": "pb",


                    "sla": null,


                    "state": "PENDING_DSO_APPROVAL",


                    "applicationStatus": "PENDING_DSO_APPROVAL",


                    "docUploadRequired": false,


                    "isStartState": false,


                    "isTerminateState": false,


                    "isStateUpdatable": true,


                    "actions": [


                        {


                            "tenantId": "pb",


                            "currentState": "PENDING_DSO_APPROVAL",


                            "action": "DSO_REJECT",


                            "nextState": "DSO_REJECTED",


                            "roles": [


                                "FSM_DSO",


                                "FSM_EDITOR_EMP"


                            ]


                        },


                        {


                            "tenantId": "pb",


                            "currentState": "PENDING_DSO_APPROVAL",


                            "action": "DSO_ACCEPT",


                            "nextState": "DSO_INPROGRESS",


                            "roles": [


                                "FSM_DSO",


                                "FSM_EDITOR_EMP"


                            ]


                        },


                        {


                            "tenantId": "pb",


                            "currentState": "PENDING_DSO_APPROVAL",


                            "action": "CANCEL",


                            "nextState": "CANCELED",


                            "roles": [


                                "FSM_ADMIN"


                            ]


                        },


                        {


                            "tenantId": "pb",


                            "currentState": "PENDING_DSO_APPROVAL",


                            "action": "REASSING",


                            "nextState": "PENDING_DSO_APPROVAL",


                            "roles": [


                                "FSM_EDITOR_EMP"


                            ]


                        }


                    ]


                },


                {


                    "tenantId": "pb",


                    "sla": null,


                    "state": "COMPLETED",


                    "applicationStatus": "COMPLETED",


                    "docUploadRequired": false,


                    "isStartState": false,


                    "isTerminateState": true,


                    "isStateUpdatable": false


                },


                {


                    "sla": null,


                    "state": "REJECTED",


                    "applicationStatus": "REJECTED",


                    "docUploadRequired": false,


                    "isStartState": false,


                    "isTerminateState": true,


                    "isStateUpdatable": false,


                    "actions": null


                },


                {


                    "tenantId": "pb",


                    "sla": null,


                    "state": "CANCELED",


                    "applicationStatus": "CANCELED",


                    "docUploadRequired": false,


                    "isStartState": false,


                    "isTerminateState": true,


                    "isStateUpdatable": false,


                    "actions": null


                },


                {


                    "tenantId": "pb",


                    "sla": null,


                    "state": "CITIZEN_FEEDBACK_PENDING",


                    "applicationStatus": "CITIZEN_FEEDBACK_PENDING",


                    "docUploadRequired": false,


                    "isStartState": false,


                    "isTerminateState": false,


                    "isStateUpdatable": false,


                    "actions": [


                        {


                            "tenantId": "pb",


                            "currentState": "CITIZEN_FEEDBACK_PENDING",


                            "action": "RATE",


                            "nextState": "COMPLETED",


                            "roles": [


                                "CITIZEN"


                            ]


                        }


                    ]


                }


            ]


        }


    ],


    "RequestInfo": {


        "apiId": "Rainmaker",


        "action": "",


        "did": 1,


        "key": "",


        "msgId": "20170310130900|en_IN",


        "requesterId": "",


        "ts": 1513579888683,


        "ver": ".01",


        "authToken": "c6aa4196-0e1b-4634-802b-b85fa13ae6ce",


        "userInfo": {


            "id": 30074,


            "uuid": "5130f2e3-efc1-401a-94fb-b9e60d9fa17d",


            "userName": "XYZ",


            "name": "XYZ",


            "mobileNumber": "8897970021",


            "emailId": null,


            "locale": null,


            "type": "EMPLOYEE",


            "roles": [


                {


                    "name": "FSM Employee Application Viewer",


                    "code": "FSM_VIEW_EMP",


                    "tenantId": "pb.amritsar"


                },


                {


                    "name": "Employee",


                    "code": "EMPLOYEE",


                    "tenantId": "pb.amritsar"


                },


                {


                    "name": "National Dashboard Administrator",


                    "code": "NATADMIN",


                    "tenantId": "pb.amritsar"


                },


                {


                    "name": "TL Field Inspector",


                    "code": "TL_FIELD_INSPECTOR",


                    "tenantId": "pb.amritsar"


                },


                {


                    "name": "ptcollection emp",


                    "code": "PT_COLLECTION_EMP",


                    "tenantId": "pb.amritsar"


                },


                {


                    "name": "EMPLOYEE ADMIN",


                    "code": "EMPLOYEE ADMIN",


                    "tenantId": "pb.amritsar"


                },


                {


                    "name": "HRMS Admin",


                    "code": "HRMS_ADMIN",


                    "tenantId": "pb.amritsar"


                },


                {


                    "name": "Universal Collection Employee",


                    "code": "UC_EMP",


                    "tenantId": "pb.amritsar"


                },


                {


                    "name": "State Administrator",


                    "code": "STADMIN",


                    "tenantId": "pb.amritsar"


                },


                {


                    "name": "Super User",


                    "code": "SUPERUSER",


                    "tenantId": "pb.amritsar"


                },


                {


                    "name": "FSM Employee Application Creator",


                    "code": "FSM_CREATOR_EMP",


                    "tenantId": "pb.amritsar"


                },


                {


                    "name": "FSM Employee Dashboard Viewer",


                    "code": "FSM_DASHBOARD_VIEWER",


                    "tenantId": "pb.amritsar"


                },


                {


                    "name": "Anonymous User",


                    "code": "ANONYMOUS",


                    "tenantId": "pb.amritsar"


                }


            ],


            "active": true,


            "tenantId": "pb.amritsar",


            "permanentCity": null


        }


    }


}
```

For advance zero a new business service PAY\_LATER\_SERVICE was created.&#x20;

* Create businessService (workflow configuration) using the  /businessservice/\_create. Following is the product configuration for PAY\_LATER\_SERVICE.

```
{
	"BusinessServices": [{
		"tenantId": "pb",
		"businessService": "PAY_LATER_SERVICE",
		"business": "fsm",
		"businessServiceSla": 172800000,
		"states": [{
				"tenantId": "pb",
				"sla": null,
				"state": null,
				"applicationStatus": null,
				"docUploadRequired": false,
				"isStartState": true,
				"isTerminateState": false,
				"isStateUpdatable": true,
				"actions": [{
						"tenantId": "pb",
						"currentState": null,
						"action": "APPLY",
						"nextState": "ASSING_DSO",
						"roles": [
							"FSM_CREATOR_EMP"
						]
					},
					{
						"tenantId": "pb",
						"currentState": null,
						"action": "CREATE",
						"nextState": "CREATED",
						"roles": [
							"CITIZEN"
						]
					}
				]
			},
			{
				"tenantId": "pb",
				"sla": null,
				"state": "CREATED",
				"applicationStatus": "CREATED",
				"docUploadRequired": false,
				"isStartState": false,
				"isTerminateState": false,
				"isStateUpdatable": true,
				"actions": [{
						"tenantId": "pb",
						"currentState": "CREATED",
						"action": "REJECT",
						"nextState": "REJECTED",
						"roles": [
							"FSM_ADMIN"
						]
					},
					{
						"tenantId": "pb",
						"currentState": "CREATED",
						"action": "SUBMIT",
						"nextState": "ASSING_DSO",
						"roles": [
							"FSM_EDITOR_EMP"
						]
					}
				]
			},
			{
				"tenantId": "pb",
				"sla": null,
				"state": "ASSING_DSO",
				"applicationStatus": "ASSING_DSO",
				"docUploadRequired": false,
				"isStartState": false,
				"isTerminateState": false,
				"isStateUpdatable": true,
				"actions": [{
						"tenantId": "pb",
						"currentState": "ASSING_DSO",
						"action": "CANCEL",
						"nextState": "CANCELED",
						"roles": [
							"FSM_ADMIN"
						]
					},
					{
						"tenantId": "pb",
						"currentState": "ASSING_DSO",
						"action": "ASSIGN",
						"nextState": "PENDING_DSO_APPROVAL",
						"roles": [
							"FSM_EDITOR_EMP"
						]
					}
				]
			},
			{
				"tenantId": "pb",
				"sla": null,
				"state": "PENDING_DSO_APPROVAL",
				"applicationStatus": "PENDING_DSO_APPROVAL",
				"docUploadRequired": false,
				"isStartState": false,
				"isTerminateState": false,
				"isStateUpdatable": true,
				"actions": [{
						"tenantId": "pb",
						"currentState": "PENDING_DSO_APPROVAL",
						"action": "DSO_ACCEPT",
						"nextState": "DSO_INPROGRESS",
						"roles": [
							"FSM_DSO",
							"FSM_EDITOR_EMP"
						]
					},
					{
						"tenantId": "pb",
						"currentState": "PENDING_DSO_APPROVAL",
						"action": "CANCEL",
						"nextState": "CANCELED",
						"roles": [
							"FSM_ADMIN"
						]
					},
					{
						"tenantId": "pb",
						"currentState": "PENDING_DSO_APPROVAL",
						"action": "REASSING",
						"nextState": "PENDING_DSO_APPROVAL",
						"roles": [
							"FSM_EDITOR_EMP"
						]
					},
					{
						"tenantId": "pb",
						"currentState": "PENDING_DSO_APPROVAL",
						"action": "DSO_REJECT",
						"nextState": "DSO_REJECTED",
						"roles": [
							"FSM_DSO",
							"FSM_EDITOR_EMP"
						]
					}
				]
			},
			{
				"tenantId": "pb",
				"sla": null,
				"state": "DSO_REJECTED",
				"applicationStatus": "DSO_REJECTED",
				"docUploadRequired": false,
				"isStartState": false,
				"isTerminateState": false,
				"isStateUpdatable": true,
				"actions": [{
						"tenantId": "pb",
						"currentState": "DSO_REJECTED",
						"action": "CANCEL",
						"nextState": "CANCELED",
						"roles": [
							"FSM_ADMIN"
						],
						"active": true
					},
					{
						"tenantId": "pb",
						"currentState": "DSO_REJECTED",
						"action": "REASSING",
						"nextState": "PENDING_DSO_APPROVAL",
						"roles": [
							"FSM_EDITOR_EMP"
						],
						"active": true
					},
					{
						"tenantId": "pb",
						"currentState": "DSO_REJECTED",
						"action": "SENDBACK",
						"nextState": "PENDING_DSO_APPROVAL",
						"roles": [
							"FSM_ADMIN"
						],
						"active": true
					}
				]
			},
			{
				"tenantId": "pb",
				"sla": null,
				"state": "DSO_INPROGRESS",
				"applicationStatus": "DSO_INPROGRESS",
				"docUploadRequired": false,
				"isStartState": false,
				"isTerminateState": false,
				"isStateUpdatable": true,
				"actions": [{
						"tenantId": "pb",
						"currentState": "DSO_INPROGRESS",
						"action": "SENDBACK",
						"nextState": "PENDING_DSO_APPROVAL",
						"roles": [
							"FSM_ADMIN"
						]
					},
					{
						"tenantId": "pb",
						"currentState": "DSO_INPROGRESS",
						"action": "COMPLETED",
						"nextState": "CITIZEN_FEEDBACK_PENDING",
						"roles": [
							"FSM_DSO",
							"FSM_EDITOR_EMP"
						]
					},


					{
						"tenantId": "pb",
						"currentState": "DSO_INPROGRESS",
						"action": "CANCEL",
						"nextState": "CANCELED",
						"roles": [
							"FSM_ADMIN"
						]
					},
					{
						"tenantId": "pb",
						"currentState": "DSO_INPROGRESS",
						"action": "REASSING",
						"nextState": "PENDING_DSO_APPROVAL",
						"roles": [
							"FSM_EDITOR_EMP"
						]
					},
					{
						"tenantId": "pb",
						"currentState": "DSO_INPROGRESS",
						"action": "UPDATE",
						"nextState": "DSO_INPROGRESS",
						"roles": [
							"FSM_DSO",
							"FSM_EDITOR_EMP"
						]
					},
					{
						"tenantId": "pb",
						"action": "PAY",
						"nextState": "DSO_INPROGRESS",
						"roles": [
							"CITIZEN",
							"FSM_COLLECTOR"
						]
					}
				]
			},
			{
				"tenantId": "pb",
				"sla": null,
				"state": "CITIZEN_FEEDBACK_PENDING",
				"applicationStatus": "CITIZEN_FEEDBACK_PENDING",
				"docUploadRequired": false,
				"isStartState": false,
				"isTerminateState": false,
				"isStateUpdatable": false,
				"actions": [{
					"tenantId": "pb",
					"currentState": "CITIZEN_FEEDBACK_PENDING",
					"action": "RATE",
					"nextState": "COMPLETED",
					"roles": [
						"CITIZEN"
					],
					"active": true
				}]
			},
			{
				"tenantId": "pb",
				"sla": null,
				"state": "COMPLETED",
				"applicationStatus": "COMPLETED",
				"docUploadRequired": false,
				"isStartState": false,
				"isTerminateState": true,
				"isStateUpdatable": false,
				"actions": null
			},
			{
				"tenantId": "pb",
				"sla": null,
				"state": "REJECTED",
				"applicationStatus": "REJECTED",
				"docUploadRequired": false,
				"isStartState": false,
				"isTerminateState": true,
				"isStateUpdatable": false,
				"actions": null
			},
			{
				"tenantId": "pb",
				"sla": null,
				"state": "CANCELED",
				"applicationStatus": "CANCELED",
				"docUploadRequired": false,
				"isStartState": false,
				"isTerminateState": true,
				"isStateUpdatable": false,
				"actions": null
			}


		]
	}],
	"RequestInfo": {
		"apiId": "Rainmaker",
		"action": "",
		"did": 1,
		"key": "",
		"msgId": "20170310130900|en_IN",
		"requesterId": "",
		"ts": 1513579888683,
		"ver": ".01",
		"authToken": "3d828f89-c249-4d4a-9098-8230e6040bf5",
		"userInfo": {
			"id": 30074,
			"uuid": "5130f2e3-efc1-401a-94fb-b9e60d9fa17d",
			"userName": "XYZ",
			"name": "XYZ",
			"mobileNumber": "8897970021",
			"emailId": null,
			"locale": null,
			"type": "EMPLOYEE",
			"roles": [{
					"name": "FSM Employee Application Viewer",
					"code": "FSM_VIEW_EMP",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "Employee",
					"code": "EMPLOYEE",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "National Dashboard Administrator",
					"code": "NATADMIN",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "TL Field Inspector",
					"code": "TL_FIELD_INSPECTOR",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "ptcollection emp",
					"code": "PT_COLLECTION_EMP",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "EMPLOYEE ADMIN",
					"code": "EMPLOYEE ADMIN",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "HRMS Admin",
					"code": "HRMS_ADMIN",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "Universal Collection Employee",
					"code": "UC_EMP",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "State Administrator",
					"code": "STADMIN",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "Super User",
					"code": "SUPERUSER",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "FSM Employee Application Creator",
					"code": "FSM_CREATOR_EMP",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "FSM Employee Dashboard Viewer",
					"code": "FSM_DASHBOARD_VIEWER",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "Anonymous User",
					"code": "ANONYMOUS",
					"tenantId": "pb.amritsar"
				}
			],
			"active": true,
			"tenantId": "pb.amritsar",
			"permanentCity": null
		}
	}
}
```

For the zero price application, a new business service FSM\_ZERO\_PAY\_SERVICE has been created.

* In the zero pricing, the application will be created with zero price and the collection step is skipped.
* Create businessService (workflow configuration) using the  /businessservice/\_create. The following is the product configuration for FSM\_ZERO\_PAY\_SERVICE:

```
{
	"BusinessServices": [{
		"tenantId": "pb",
		"businessService": "FSM_ZERO_PAY_SERVICE",
		"business": "fsm",
		"businessServiceSla": 172800000,
		"states": [{
				"tenantId": "pb",
				"sla": null,
				"state": null,
				"applicationStatus": null,
				"docUploadRequired": false,
				"isStartState": true,
				"isTerminateState": false,
				"isStateUpdatable": true,
				"actions": [{
						"tenantId": "pb",
						"currentState": null,
						"action": "APPLY",
						"nextState": "ASSING_DSO",
						"roles": [
							"FSM_CREATOR_EMP"
						]
					},
					{
						"tenantId": "pb",
						"currentState": null,
						"action": "CREATE",
						"nextState": "CREATED",
						"roles": [
							"CITIZEN"
						]
					}
				]
			},
			{
				"tenantId": "pb",
				"sla": null,
				"state": "CREATED",
				"applicationStatus": "CREATED",
				"docUploadRequired": false,
				"isStartState": false,
				"isTerminateState": false,
				"isStateUpdatable": true,
				"actions": [{
						"tenantId": "pb",
						"currentState": "CREATED",
						"action": "REJECT",
						"nextState": "REJECTED",
						"roles": [
							"FSM_ADMIN"
						]
					},
					{
						"tenantId": "pb",
						"currentState": "CREATED",
						"action": "SUBMIT",
						"nextState": "ASSING_DSO",
						"roles": [
							"FSM_EDITOR_EMP"
						]
					}
				]
			},
			{
				"tenantId": "pb",
				"sla": null,
				"state": "ASSING_DSO",
				"applicationStatus": "ASSING_DSO",
				"docUploadRequired": false,
				"isStartState": false,
				"isTerminateState": false,
				"isStateUpdatable": true,
				"actions": [{
						"tenantId": "pb",
						"currentState": "ASSING_DSO",
						"action": "CANCEL",
						"nextState": "CANCELED",
						"roles": [
							"FSM_ADMIN"
						]
					},
					{
						"tenantId": "pb",
						"currentState": "ASSING_DSO",
						"action": "ASSIGN",
						"nextState": "PENDING_DSO_APPROVAL",
						"roles": [
							"FSM_EDITOR_EMP"
						]
					}
				]
			},
			{
				"tenantId": "pb",
				"sla": null,
				"state": "PENDING_DSO_APPROVAL",
				"applicationStatus": "PENDING_DSO_APPROVAL",
				"docUploadRequired": false,
				"isStartState": false,
				"isTerminateState": false,
				"isStateUpdatable": true,
				"actions": [{
						"tenantId": "pb",
						"currentState": "PENDING_DSO_APPROVAL",
						"action": "DSO_ACCEPT",
						"nextState": "DSO_INPROGRESS",
						"roles": [
							"FSM_DSO",
							"FSM_EDITOR_EMP"
						]
					},
					{
						"tenantId": "pb",
						"currentState": "PENDING_DSO_APPROVAL",
						"action": "CANCEL",
						"nextState": "CANCELED",
						"roles": [
							"FSM_ADMIN"
						]
					},
					{
						"tenantId": "pb",
						"currentState": "PENDING_DSO_APPROVAL",
						"action": "REASSING",
						"nextState": "PENDING_DSO_APPROVAL",
						"roles": [
							"FSM_EDITOR_EMP"
						]
					},
					{
						"tenantId": "pb",
						"currentState": "PENDING_DSO_APPROVAL",
						"action": "DSO_REJECT",
						"nextState": "DSO_REJECTED",
						"roles": [
							"FSM_DSO",
							"FSM_EDITOR_EMP"
						]
					}
				]
			},
			{
				"tenantId": "pb",
				"sla": null,
				"state": "DSO_REJECTED",
				"applicationStatus": "DSO_REJECTED",
				"docUploadRequired": false,
				"isStartState": false,
				"isTerminateState": false,
				"isStateUpdatable": true,
				"actions": [{
						"tenantId": "pb",
						"currentState": "DSO_REJECTED",
						"action": "CANCEL",
						"nextState": "CANCELED",
						"roles": [
							"FSM_ADMIN"
						],
						"active": true
					},
					{
						"tenantId": "pb",
						"currentState": "DSO_REJECTED",
						"action": "REASSING",
						"nextState": "PENDING_DSO_APPROVAL",
						"roles": [
							"FSM_EDITOR_EMP"
						],
						"active": true
					},
					{
						"tenantId": "pb",
						"currentState": "DSO_REJECTED",
						"action": "SENDBACK",
						"nextState": "PENDING_DSO_APPROVAL",
						"roles": [
							"FSM_ADMIN"
						],
						"active": true
					}
				]
			},
			{
				"tenantId": "pb",
				"sla": null,
				"state": "DSO_INPROGRESS",
				"applicationStatus": "DSO_INPROGRESS",
				"docUploadRequired": false,
				"isStartState": false,
				"isTerminateState": false,
				"isStateUpdatable": true,
				"actions": [{
						"tenantId": "pb",
						"currentState": "DSO_INPROGRESS",
						"action": "SENDBACK",
						"nextState": "PENDING_DSO_APPROVAL",
						"roles": [
							"FSM_ADMIN"
						]
					},
					{
						"tenantId": "pb",
						"currentState": "DSO_INPROGRESS",
						"action": "COMPLETED",
						"nextState": "CITIZEN_FEEDBACK_PENDING",
						"roles": [
							"FSM_DSO",
							"FSM_EDITOR_EMP"
						]
					},
					{
						"tenantId": "pb",
						"currentState": "DSO_INPROGRESS",
						"action": "CANCEL",
						"nextState": "CANCELED",
						"roles": [
							"FSM_ADMIN"
						]
					},
					{
						"tenantId": "pb",
						"currentState": "DSO_INPROGRESS",
						"action": "REASSING",
						"nextState": "PENDING_DSO_APPROVAL",
						"roles": [
							"FSM_EDITOR_EMP"
						]
					},
					{
						"tenantId": "pb",
						"currentState": "DSO_INPROGRESS",
						"action": "UPDATE",
						"nextState": "DSO_INPROGRESS",
						"roles": [
							"FSM_DSO",
							"FSM_EDITOR_EMP"
						]
					}
				]
			},
			{
				"tenantId": "pb",
				"sla": null,
				"state": "CITIZEN_FEEDBACK_PENDING",
				"applicationStatus": "CITIZEN_FEEDBACK_PENDING",
				"docUploadRequired": false,
				"isStartState": false,
				"isTerminateState": false,
				"isStateUpdatable": false,
				"actions": [{
					"tenantId": "pb",
					"currentState": "CITIZEN_FEEDBACK_PENDING",
					"action": "RATE",
					"nextState": "COMPLETED",
					"roles": [
						"CITIZEN"
					],
					"active": true
				}]
			},
			{
				"tenantId": "pb",
				"sla": null,
				"state": "COMPLETED",
				"applicationStatus": "COMPLETED",
				"docUploadRequired": false,
				"isStartState": false,
				"isTerminateState": true,
				"isStateUpdatable": false,
				"actions": null
			},
			{
				"tenantId": "pb",
				"sla": null,
				"state": "REJECTED",
				"applicationStatus": "REJECTED",
				"docUploadRequired": false,
				"isStartState": false,
				"isTerminateState": true,
				"isStateUpdatable": false,
				"actions": null
			},
			{
				"tenantId": "pb",
				"sla": null,
				"state": "CANCELED",
				"applicationStatus": "CANCELED",
				"docUploadRequired": false,
				"isStartState": false,
				"isTerminateState": true,
				"isStateUpdatable": false,
				"actions": null
			}


		]
	}],
	"RequestInfo": {
		"apiId": "Rainmaker",
		"action": "",
		"did": 1,
		"key": "",
		"msgId": "20170310130900|en_IN",
		"requesterId": "",
		"ts": 1513579888683,
		"ver": ".01",
		"authToken": "3d828f89-c249-4d4a-9098-8230e6040bf5",
		"userInfo": {
			"id": 30074,
			"uuid": "5130f2e3-efc1-401a-94fb-b9e60d9fa17d",
			"userName": "XYZ",
			"name": "XYZ",
			"mobileNumber": "8897970021",
			"emailId": null,
			"locale": null,
			"type": "EMPLOYEE",
			"roles": [{
					"name": "FSM Employee Application Viewer",
					"code": "FSM_VIEW_EMP",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "Employee",
					"code": "EMPLOYEE",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "National Dashboard Administrator",
					"code": "NATADMIN",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "TL Field Inspector",
					"code": "TL_FIELD_INSPECTOR",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "ptcollection emp",
					"code": "PT_COLLECTION_EMP",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "EMPLOYEE ADMIN",
					"code": "EMPLOYEE ADMIN",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "HRMS Admin",
					"code": "HRMS_ADMIN",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "Universal Collection Employee",
					"code": "UC_EMP",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "State Administrator",
					"code": "STADMIN",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "Super User",
					"code": "SUPERUSER",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "FSM Employee Application Creator",
					"code": "FSM_CREATOR_EMP",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "FSM Employee Dashboard Viewer",
					"code": "FSM_DASHBOARD_VIEWER",
					"tenantId": "pb.amritsar"
				},
				{
					"name": "Anonymous User",
					"code": "ANONYMOUS",
					"tenantId": "pb.amritsar"
				}
			],
			"active": true,
			"tenantId": "pb.amritsar",
			"permanentCity": null
		}
	}
}
```



\
[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)](http://creativecommons.org/licenses/by/4.0/)_All content on this page by_ [_eGov Foundation_](https://egov.org.in/) _is licensed under a_ [_Creative Commons Attribution 4.0 International License_](http://creativecommons.org/licenses/by/4.0/)_._
