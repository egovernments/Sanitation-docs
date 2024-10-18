# Inbox/Update Tests

From the TQM card in the home screen, there is a link to the inbox.

## Update Tests Flow

* Tests are created through the cronjob scheduler at the backend.&#x20;
* These tests created have a two-step workflow: Scheduled (initial state) -> Select Lab ->  Pending Results -> Submitted (final state).
* By default, tests which are in the workflow, will show up in the inbox of a plant operator. The inbox shows a list of cards corresponding to each test.
* Each card contains data relevant to the test such as Test ID, Treatment Process, Stage, Output, Status, etc.
* There is a dynamic action button in each card. According to the current workflow status, it will show either update status (scheduled state) or update results.&#x20;
* Clicking on the update status opens an update test screen which shows data about the test and a dropdown which has a list of labs configured in MDMS. A user can select one of the labs and update the test.&#x20;
* Clicking on update results opens an update test screen, which also shows the same test details, but the bottom card shows a list of benchmarks to be tested in that test. A user can enter these benchmarks and update the test. There is an option to upload a document as well, and at least one benchmark is mandatory to enter.
* A success/failure toast is shown once the test is updated.
* Filter and sort options are available in the inbox.
* A user can filter by -> Treatment Process, Output Type, Date Range, Workflow Status.
* A user can sort by date (latest first/latest last).

<figure><img src="../../../../.gitbook/assets/image (161).png" alt=""><figcaption><p>Plant Operator Inbox</p></figcaption></figure>

## API Details for Update Tests :

* Use the pqm-service.&#x20;
* URL for inbox "/pqm-service/v1/\_update".
* Sample request object:

```
{
    "tests": [
        {
            "id": "591836e7-c38e-4427-ad0d-2ec1f3d5e73b",
            "testId": "1013-PQM-2023-11-24-001079",
            "testCode": null,
            "tenantId": "pg.citya",
            "plantCode": "PURI_FSTP",
            "processCode": "FECAL_SLUDGE_MANAGEMENT",
            "stageCode": "COAGULATION",
            "materialCode": "POTABLE_WATER",
            "deviceCode": null,
            "testCriteria": [
                {
                    "id": "edbaeafe-6db4-413e-9977-01406dd56c87",
                    "testId": "1013-PQM-2023-11-24-001079",
                    "criteriaCode": "TSS_LESST_100",
                    "resultValue": "20",
                    "allowedDeviation": null,
                    "resultStatus": "PENDING",
                    "isActive": true,
                    "auditDetails": {
                        "createdBy": "60cf0229-3334-49bd-a83b-7354080ef2fc",
                        "lastModifiedBy": "60cf0229-3334-49bd-a83b-7354080ef2fc",
                        "createdTime": 1700824652571,
                        "lastModifiedTime": 1700824879822
                    }
                }
            ],
            "status": "PENDING",
            "wfStatus": "PENDINGRESULTS",
            "testType": "LAB_SCHEDULED",
            "scheduledDate": 1700888886872,
            "isActive": true,
            "documents": [],
            "additionalDetails": {},
            "auditDetails": {
                "createdBy": "60cf0229-3334-49bd-a83b-7354080ef2fc",
                "lastModifiedBy": "60cf0229-3334-49bd-a83b-7354080ef2fc",
                "createdTime": 1700824652571,
                "lastModifiedTime": 1700824879822
            },
            "workflow": {
                "action": "UPDATE_RESULT"
            },
            "labAssignedTo": null
        }
    ],
    "RequestInfo": {
        "apiId": "Rainmaker",
        "authToken": "e5d10a5d-b262-47fc-a9ee-fc24c3a0de19",
        "userInfo": {
            "id": 721,
            "uuid": "41488b21-c742-4290-af8e-a2a1dc3749ac",
            "userName": "TQM_DEV_PLANTOPERATOR",
            "name": "Plant operator",
            "mobileNumber": "7281638699",
            "emailId": null,
            "locale": null,
            "type": "EMPLOYEE",
            "roles": [
                {
                    "name": "PQM TP OPERATOR",
                    "code": "PQM_TP_OPERATOR",
                    "tenantId": "pg.citya"
                }
            ],
            "active": true,
            "tenantId": "pg.citya",
            "permanentCity": null
        },
        "msgId": "1701076677904|en_IN",
        "plainAccessRequest": {}
    }
}
```

* #### Sample curl for update:

```
curl 'https://unified-dev.digit.org/pqm-service/v1/_update' \
  -H 'authority: unified-dev.digit.org' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9' \
  -H 'content-type: application/json;charset=UTF-8' \
  -H 'cookie: _ga_V2CPZCVTXQ=GS1.1.1695293925.1.1.1695293950.0.0.0; __cuid=59fd9aac25b044f6af006bd4b159cbbf; amp_fef1e8=f4fc07f6-3fb0-4c67-8114-a1beb906e625R...1hf75985a.1hf76uet8.i.8.q; _ga_P1TZCPKF6S=GS1.1.1699974064.1.1.1699975479.60.0.0; _ga=GA1.2.1291438273.1695293925; _ga_0JZG96DZSM=GS1.1.1699977339.2.0.1699977339.60.0.0' \
  -H 'origin: https://unified-dev.digit.org' \
  -H 'referer: https://unified-dev.digit.org/sanitation-ui/employee/tqm/test-details?id=1013-PQM-2023-11-24-001079' \
  -H 'sec-ch-ua: "Google Chrome";v="119", "Chromium";v="119", "Not?A_Brand";v="24"' \
  -H 'sec-ch-ua-mobile: ?1' \
  -H 'sec-ch-ua-platform: "Android"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-origin' \
  -H 'user-agent: Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.0.0 Mobile Safari/537.36' \
  --data-raw '{"tests":[{"id":"591836e7-c38e-4427-ad0d-2ec1f3d5e73b","testId":"1013-PQM-2023-11-24-001079","testCode":null,"tenantId":"pg.citya","plantCode":"PURI_FSTP","processCode":"FECAL_SLUDGE_MANAGEMENT","stageCode":"COAGULATION","materialCode":"POTABLE_WATER","deviceCode":null,"testCriteria":[{"id":"edbaeafe-6db4-413e-9977-01406dd56c87","testId":"1013-PQM-2023-11-24-001079","criteriaCode":"TSS_LESST_100","resultValue":"20","allowedDeviation":null,"resultStatus":"PENDING","isActive":true,"auditDetails":{"createdBy":"60cf0229-3334-49bd-a83b-7354080ef2fc","lastModifiedBy":"60cf0229-3334-49bd-a83b-7354080ef2fc","createdTime":1700824652571,"lastModifiedTime":1700824879822}}],"status":"PENDING","wfStatus":"PENDINGRESULTS","testType":"LAB_SCHEDULED","scheduledDate":1700888886872,"isActive":true,"documents":[],"additionalDetails":{},"auditDetails":{"createdBy":"60cf0229-3334-49bd-a83b-7354080ef2fc","lastModifiedBy":"60cf0229-3334-49bd-a83b-7354080ef2fc","createdTime":1700824652571,"lastModifiedTime":1700824879822},"workflow":{"action":"UPDATE_RESULT"},"labAssignedTo":null}],"RequestInfo":{"apiId":"Rainmaker","authToken":"e5d10a5d-b262-47fc-a9ee-fc24c3a0de19","userInfo":{"id":721,"uuid":"41488b21-c742-4290-af8e-a2a1dc3749ac","userName":"TQM_DEV_PLANTOPERATOR","name":"Plant operator","mobileNumber":"7281638699","emailId":null,"locale":null,"type":"EMPLOYEE","roles":[{"name":"PQM TP OPERATOR","code":"PQM_TP_OPERATOR","tenantId":"pg.citya"}],"active":true,"tenantId":"pg.citya","permanentCity":null},"msgId":"1701076677904|en_IN","plainAccessRequest":{}}}' \
  --compressed
```

## Role-Action Mapping:

Role-action mapping is done for the "/pqm-service/v1/\_update" endpoint for a plant operator user role, that is:&#x20;

```json
PQM_TP_OPERATOR
```

<figure><img src="../../../../.gitbook/assets/image (162).png" alt=""><figcaption><p>Update Tests (Select Lab)</p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/image (163).png" alt=""><figcaption><p>Update Test(Add test result)</p></figcaption></figure>

## API Details for Inbox:

* Use the inbox-v2 API.&#x20;
* URL for inbox "/inbox/v2/\_search".
* Sample request object:&#x20;

```
{
    "inbox": {
        "processSearchCriteria": {
            "businessService": [
                "PQM"
            ],
            "moduleName": "pqm",
            "tenantId": "pg.citya"
        },
        "moduleSearchCriteria": {
            "sortBy": "createdTime",
            "plantCodes": [
                "ANGUL_FSTP",
                "PURI_FSTP"
            ],
            "processCodes": [
                "WATER_FILTERING",
                "FECAL_SLUDGE_MANAGEMENT"
            ],
            "materialCodes": [
                "ARSENIC",
                "NA",
                "SCREENED_SLUDGE",
                "CHLORINE",
                "SALT",
                "IRON",
                "FECAL_SLUDGE",
                "EFFLUENTS",
                "BIOSOLID",
                "POTABLE_WATER"
            ],
            "wfStatus": [
                "SCHEDULED",
                "PENDINGRESULTS"
            ],
            "fromDate": 1698777000000,
            "toDate": 1701368999000
        },
        "limit": 100,
        "offset": 0,
        "tenantId": "pg.citya"
    },
    "RequestInfo": {
        "apiId": "Rainmaker",
        "authToken": "e5d10a5d-b262-47fc-a9ee-fc24c3a0de19",
        "userInfo": {
            "id": 721,
            "uuid": "41488b21-c742-4290-af8e-a2a1dc3749ac",
            "userName": "TQM_DEV_PLANTOPERATOR",
            "name": "Plant operator",
            "mobileNumber": "7281638699",
            "emailId": null,
            "locale": null,
            "type": "EMPLOYEE",
            "roles": [
                {
                    "name": "PQM TP OPERATOR",
                    "code": "PQM_TP_OPERATOR",
                    "tenantId": "pg.citya"
                }
            ],
            "active": true,
            "tenantId": "pg.citya",
            "permanentCity": null
        },
        "msgId": "1701076328474|en_IN",
        "plainAccessRequest": {}
    }
}
```

* #### Sample curl for inbox:

```
curl 'https://unified-dev.digit.org/inbox/v2/_search' \
  -H 'authority: unified-dev.digit.org' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9' \
  -H 'content-type: application/json;charset=UTF-8' \
  -H 'cookie: _ga_V2CPZCVTXQ=GS1.1.1695293925.1.1.1695293950.0.0.0; __cuid=59fd9aac25b044f6af006bd4b159cbbf; amp_fef1e8=f4fc07f6-3fb0-4c67-8114-a1beb906e625R...1hf75985a.1hf76uet8.i.8.q; _ga_P1TZCPKF6S=GS1.1.1699974064.1.1.1699975479.60.0.0; _ga=GA1.2.1291438273.1695293925; _ga_0JZG96DZSM=GS1.1.1699977339.2.0.1699977339.60.0.0' \
  -H 'origin: https://unified-dev.digit.org' \
  -H 'referer: https://unified-dev.digit.org/sanitation-ui/employee/tqm/inbox' \
  -H 'sec-ch-ua: "Google Chrome";v="119", "Chromium";v="119", "Not?A_Brand";v="24"' \
  -H 'sec-ch-ua-mobile: ?1' \
  -H 'sec-ch-ua-platform: "Android"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-origin' \
  -H 'user-agent: Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.0.0 Mobile Safari/537.36' \
  --data-raw '{"inbox":{"processSearchCriteria":{"businessService":["PQM"],"moduleName":"pqm","tenantId":"pg.citya"},"moduleSearchCriteria":{"sortBy":"createdTime","plantCodes":["ANGUL_FSTP","PURI_FSTP"],"processCodes":["WATER_FILTERING","FECAL_SLUDGE_MANAGEMENT"],"materialCodes":["ARSENIC","NA","SCREENED_SLUDGE","CHLORINE","SALT","IRON","FECAL_SLUDGE","EFFLUENTS","BIOSOLID","POTABLE_WATER"],"wfStatus":["SCHEDULED","PENDINGRESULTS"],"fromDate":1698777000000,"toDate":1701368999000},"limit":100,"offset":0,"tenantId":"pg.citya"},"RequestInfo":{"apiId":"Rainmaker","authToken":"e5d10a5d-b262-47fc-a9ee-fc24c3a0de19","userInfo":{"id":721,"uuid":"41488b21-c742-4290-af8e-a2a1dc3749ac","userName":"TQM_DEV_PLANTOPERATOR","name":"Plant operator","mobileNumber":"7281638699","emailId":null,"locale":null,"type":"EMPLOYEE","roles":[{"name":"PQM TP OPERATOR","code":"PQM_TP_OPERATOR","tenantId":"pg.citya"}],"active":true,"tenantId":"pg.citya","permanentCity":null},"msgId":"1701076328474|en_IN","plainAccessRequest":{}}}' \
  --compressed
```

## Role-Action Mapping:

Role action mapping is done for the "/inbox/v2/\_search" endpoint for a plant operator user role, that is:&#x20;

```json
PQM_TP_OPERATOR
```
