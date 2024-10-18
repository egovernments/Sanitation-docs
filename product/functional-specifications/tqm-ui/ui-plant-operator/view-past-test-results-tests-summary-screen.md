# View Past Test Results/Test's Summary Screen

From the TQM card in the home screen, there is a link to "View Past Tests".

## View Past Tests/Test's Summary Screen

* The view past tests screen will show the tests whose workflow is completed, that is, they are in the submitted status.
* The screen shows a list of cards, each card corresponding to a test, and shows test details similar to inbox.
* Filters and sort options are available.
* User can filter by Treatment process, Output Type, Test Type and the date range.
* Sort is similar to inbox.

<figure><img src="../../../../.gitbook/assets/image (164).png" alt=""><figcaption><p>View Past Tests</p></figcaption></figure>

## API Details:

* Use the pqm-service.&#x20;
* URL for search "/pqm-service/v1/\_search".
* Sample request object:

```
{
    "testSearchCriteria": {
        "processCodes": [
            "WATER_FILTERING",
            "FECAL_SLUDGE_MANAGEMENT"
        ],
        "materialCodes": [
            "ARSENIC",
            "NA",
            "SCREENED_SLUDGE",
            "FECAL_SLUDGE",
            "EFFLUENTS",
            "BIOSOLID",
            "CHLORINE",
            "SALT",
            "IRON",
            "POTABLE_WATER"
        ],
        "testType": [
            "IOT_SCHEDULED",
            "LAB_ADHOC",
            "LAB_SCHEDULED"
        ],
        "fromDate": 1698777000000,
        "toDate": 1701368999000,
        "wfStatus": [
            "SUBMITTED"
        ],
        "plantCodes": [
            "ANGUL_FSTP",
            "PURI_FSTP"
        ]
    },
    "pagination": {
        "limit": 100
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
        "msgId": "1701076145507|en_IN",
        "plainAccessRequest": {}
    }
}
```

* #### Sample curl for search:

```
curl 'https://unified-dev.digit.org/pqm-service/v1/_search' \
  -H 'authority: unified-dev.digit.org' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9' \
  -H 'content-type: application/json;charset=UTF-8' \
  -H 'cookie: _ga_V2CPZCVTXQ=GS1.1.1695293925.1.1.1695293950.0.0.0; __cuid=59fd9aac25b044f6af006bd4b159cbbf; amp_fef1e8=f4fc07f6-3fb0-4c67-8114-a1beb906e625R...1hf75985a.1hf76uet8.i.8.q; _ga_P1TZCPKF6S=GS1.1.1699974064.1.1.1699975479.60.0.0; _ga=GA1.2.1291438273.1695293925; _ga_0JZG96DZSM=GS1.1.1699977339.2.0.1699977339.60.0.0' \
  -H 'origin: https://unified-dev.digit.org' \
  -H 'referer: https://unified-dev.digit.org/sanitation-ui/employee/tqm/search-test-results' \
  -H 'sec-ch-ua: "Google Chrome";v="119", "Chromium";v="119", "Not?A_Brand";v="24"' \
  -H 'sec-ch-ua-mobile: ?1' \
  -H 'sec-ch-ua-platform: "Android"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-origin' \
  -H 'user-agent: Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.0.0 Mobile Safari/537.36' \
  --data-raw '{"testSearchCriteria":{"processCodes":["WATER_FILTERING","FECAL_SLUDGE_MANAGEMENT"],"materialCodes":["ARSENIC","NA","SCREENED_SLUDGE","FECAL_SLUDGE","EFFLUENTS","BIOSOLID","CHLORINE","SALT","IRON","POTABLE_WATER"],"testType":["IOT_SCHEDULED","LAB_ADHOC","LAB_SCHEDULED"],"fromDate":1698777000000,"toDate":1701368999000,"wfStatus":["SUBMITTED"],"plantCodes":["ANGUL_FSTP","PURI_FSTP"]},"pagination":{"limit":100},"RequestInfo":{"apiId":"Rainmaker","authToken":"e5d10a5d-b262-47fc-a9ee-fc24c3a0de19","userInfo":{"id":721,"uuid":"41488b21-c742-4290-af8e-a2a1dc3749ac","userName":"TQM_DEV_PLANTOPERATOR","name":"Plant operator","mobileNumber":"7281638699","emailId":null,"locale":null,"type":"EMPLOYEE","roles":[{"name":"PQM TP OPERATOR","code":"PQM_TP_OPERATOR","tenantId":"pg.citya"}],"active":true,"tenantId":"pg.citya","permanentCity":null},"msgId":"1701076145507|en_IN","plainAccessRequest":{}}}' \
  --compressed
```

## Role-Action Mapping:

Role-action mapping is done for the search endpoint for a plant operator user role, that is: &#x20;

```json
PQM_TP_OPERATOR
```
