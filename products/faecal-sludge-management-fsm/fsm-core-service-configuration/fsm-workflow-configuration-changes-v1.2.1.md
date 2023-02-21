# FSM Workflow Configuration Changes

## **FSM Vehicle Trip Update Business Service Request**

Instructions for production execution:

1. Replace the tenant id for production environment.
2. Replace the request info object with production user info details.
3. Fetch the production instance of the FSM\_VEHICLE\_TRIP business object and add the vehicle decline action. State in the business service definition, and then use the \_update business service for updating the workflow for vehicle trip.

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
            "tenantId": "pg",
            "uuid": "c1ec4e63-587e-4235-a349-c69762b5191f",
            "businessService": "FSM_VEHICLE_TRIP",
            "business": "vehicle",
            "businessServiceSla": 172800000,
            "states": [
                {
                    "auditDetails": {
                        "createdBy": "a32f35d9-2ab1-4d87-af41-657e0e8f1f57",
                        "lastModifiedBy": "f87f0346-ca55-4fbe-beae-8493220ae46c",
                        "createdTime": 1614969539963,
                        "lastModifiedTime": 1658213197555
                    },
                    "uuid": "b04a8f46-85e4-46e0-8163-4c7f5feb3b0a",
                    "tenantId": "pg",
                    "businessServiceId": "c1ec4e63-587e-4235-a349-c69762b5191f",
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
                                "createdBy": "a32f35d9-2ab1-4d87-af41-657e0e8f1f57",
                                "lastModifiedBy": "f87f0346-ca55-4fbe-beae-8493220ae46c",
                                "createdTime": 1614969539963,
                                "lastModifiedTime": 1658213197555
                            },
                            "uuid": "58949914-087e-46b3-a294-bb07e11d66d3",
                            "tenantId": "pg",
                            "currentState": "b04a8f46-85e4-46e0-8163-4c7f5feb3b0a",
                            "action": "SCHEDULE",
                            "nextState": "8516ddfa-0bed-48f7-95fc-514934d0594f",
                            "roles": [
                                "FSM_DSO",
                                "FSM_EDITOR_EMP"
                            ],
                            "active": true
                        },
                        {
                            "auditDetails": {
                                "createdBy": "f87f0346-ca55-4fbe-beae-8493220ae46c",
                                "lastModifiedBy": "f87f0346-ca55-4fbe-beae-8493220ae46c",
                                "createdTime": 1657726885677,
                                "lastModifiedTime": 1658213197555
                            },
                            "uuid": "d9220942-4578-4804-b528-6590fbd2bc42",
                            "tenantId": "pg",
                            "currentState": "b04a8f46-85e4-46e0-8163-4c7f5feb3b0a",
                            "action": "CREATE_FSTPO_VEHICLE_LOG",
                            "nextState": "40f37c60-efe8-4698-a411-ac39bee60dd0",
                            "roles": [
                                "FSM_EMP_FSTPO"
                            ],
                            "active": true
                        }
                    ]
                },
                {
                    "auditDetails": {
                        "createdBy": "a32f35d9-2ab1-4d87-af41-657e0e8f1f57",
                        "lastModifiedBy": "f87f0346-ca55-4fbe-beae-8493220ae46c",
                        "createdTime": 1614969539963,
                        "lastModifiedTime": 1658213197555
                    },
                    "uuid": "8516ddfa-0bed-48f7-95fc-514934d0594f",
                    "tenantId": "pg",
                    "businessServiceId": "c1ec4e63-587e-4235-a349-c69762b5191f",
                    "sla": null,
                    "state": "SCHEDULED",
                    "applicationStatus": "SCHEDULED",
                    "docUploadRequired": false,
                    "isStartState": true,
                    "isTerminateState": false,
                    "isStateUpdatable": false,
                    "actions": [
                        {
                            "auditDetails": {
                                "createdBy": "a32f35d9-2ab1-4d87-af41-657e0e8f1f57",
                                "lastModifiedBy": "f87f0346-ca55-4fbe-beae-8493220ae46c",
                                "createdTime": 1614969539963,
                                "lastModifiedTime": 1658213197555
                            },
                            "uuid": "95fc6c32-349b-4878-bd24-e912e401af00",
                            "tenantId": "pg",
                            "currentState": "8516ddfa-0bed-48f7-95fc-514934d0594f",
                            "action": "READY_FOR_DISPOSAL",
                            "nextState": "189c7485-3942-42db-808b-0c6635228a18",
                            "roles": [
                                "FSM_DSO",
                                "FSM_EDITOR_EMP"
                            ],
                            "active": true
                        }
                    ]
                },
                {
                    "auditDetails": {
                        "createdBy": "a32f35d9-2ab1-4d87-af41-657e0e8f1f57",
                        "lastModifiedBy": "f87f0346-ca55-4fbe-beae-8493220ae46c",
                        "createdTime": 1614969539963,
                        "lastModifiedTime": 1658213197555
                    },
                    "uuid": "189c7485-3942-42db-808b-0c6635228a18",
                    "tenantId": "pg",
                    "businessServiceId": "c1ec4e63-587e-4235-a349-c69762b5191f",
                    "sla": null,
                    "state": "WAITING_FOR_DISPOSAL",
                    "applicationStatus": "WAITING_FOR_DISPOSAL",
                    "docUploadRequired": false,
                    "isStartState": true,
                    "isTerminateState": false,
                    "isStateUpdatable": false,
                    "actions": [
                        {
                            "auditDetails": {
                                "createdBy": "f87f0346-ca55-4fbe-beae-8493220ae46c",
                                "lastModifiedBy": "f87f0346-ca55-4fbe-beae-8493220ae46c",
                                "createdTime": 1647270223008,
                                "lastModifiedTime": 1658213197555
                            },
                            "uuid": "dbb90c77-3b34-4772-a952-a3020e18da4f",
                            "tenantId": "pg",
                            "currentState": "189c7485-3942-42db-808b-0c6635228a18",
                            "action": "DECLINEVEHICLE",
                            "nextState": "1723f1f1-0a58-42fa-bd3c-200c47d12fa0",
                            "roles": [
                                "FSM_EMP_FSTPO"
                            ],
                            "active": true
                        },
                        {
                            "auditDetails": {
                                "createdBy": "a32f35d9-2ab1-4d87-af41-657e0e8f1f57",
                                "lastModifiedBy": "f87f0346-ca55-4fbe-beae-8493220ae46c",
                                "createdTime": 1614969539963,
                                "lastModifiedTime": 1658213197555
                            },
                            "uuid": "07ce0836-b220-4bc9-b56e-0afbb935be9e",
                            "tenantId": "pg",
                            "currentState": "189c7485-3942-42db-808b-0c6635228a18",
                            "action": "DISPOSE",
                            "nextState": "40f37c60-efe8-4698-a411-ac39bee60dd0",
                            "roles": [
                                "FSM_EMP_FSTPO"
                            ],
                            "active": true
                        }
                    ]
                },
                {
                    "auditDetails": {
                        "createdBy": "a32f35d9-2ab1-4d87-af41-657e0e8f1f57",
                        "lastModifiedBy": "f87f0346-ca55-4fbe-beae-8493220ae46c",
                        "createdTime": 1614969539963,
                        "lastModifiedTime": 1658213197555
                    },
                    "uuid": "40f37c60-efe8-4698-a411-ac39bee60dd0",
                    "tenantId": "pg",
                    "businessServiceId": "c1ec4e63-587e-4235-a349-c69762b5191f",
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
                        "createdBy": "f87f0346-ca55-4fbe-beae-8493220ae46c",
                        "lastModifiedBy": "f87f0346-ca55-4fbe-beae-8493220ae46c",
                        "createdTime": 1647270223008,
                        "lastModifiedTime": 1658213197555
                    },
                    "uuid": "1723f1f1-0a58-42fa-bd3c-200c47d12fa0",
                    "tenantId": "pg",
                    "businessServiceId": "c1ec4e63-587e-4235-a349-c69762b5191f",
                    "sla": null,
                    "state": "VEHICLE_DECLINED",
                    "applicationStatus": "VEHICLE_DECLINED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": true,
                    "isStateUpdatable": true,
                    "actions": null
                }
            ],
            "auditDetails": {
                "createdBy": "a32f35d9-2ab1-4d87-af41-657e0e8f1f57",
                "lastModifiedBy": "f87f0346-ca55-4fbe-beae-8493220ae46c",
                "createdTime": 1614969539963,
                "lastModifiedTime": 1658213197555
            }
        }
    ]
}
```



[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)](http://creativecommons.org/licenses/by/4.0/)All content on this page by [eGov Foundation ](https://egov.org.in/)is licensed under a [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/).
