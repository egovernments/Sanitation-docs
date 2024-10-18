# Workflow Configuration Changes

**PQM  Business Service Request**

Instructions for Production execution:

1. Replace the tenant id for production environment
2. Replace the request info object with production user info details
3.  For PQM new Business service PQM has been created&#x20;

    Create businessService (workflow configuration) using the  `/businessservice/_create`. Following is the product configuration for PQM

````
```postman_json
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
                                "PQM_TP_OPERATOR",
                                "PQM_CRONJOB_SCHEDULER"
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
                        },
                        {
                            "action": "SAVE_AS_DRAFT",
                            "nextState": "DRAFTED",
                            "roles": [
                                "PQM_ADMIN",
                                "PQM_TP_OPERATOR"
                            ],
                            "active": true
                        }
                    ]
                },
                {
                    "sla": null,
                    "state": "DRAFTED",
                    "applicationStatus": "DRAFTED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "action": "UPDATE_RESULT",
                            "nextState": "SUBMITTED",
                            "roles": [
                                "PQM_ADMIN",
                                "PQM_TP_OPERATOR"
                            ],
                            "active": true
                        },
                        {
                            "action": "SAVE_AS_DRAFT",
                            "nextState": "DRAFTED",
                            "roles": [
                                "PQM_ADMIN",
                                "PQM_TP_OPERATOR"
                            ],
                            "active": true
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
````
