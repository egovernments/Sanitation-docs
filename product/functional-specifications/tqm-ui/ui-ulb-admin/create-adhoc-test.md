# Create Adhoc Test

ULB admins have an option to create a test. This is an adhoc test which does not have any workflow involved. By default, it will be in the submitted state when created.

## Create Adhoc Test Flow

* From the home screen, click on the Add Test Result link.
* The user is redirected to Create Test screen. This page has two form cards. One is for entering Plant Name, Treatment Process, Stage and output type. The other card has a list of benchmarks according to the selection of the above form.
* Note: After filling the first form, only the list of benchmarks will show up.
* If any quality criteria is not found for the selection of parameters, an error is shown and user has to select another criteria.
* After filling the forms, click on submit to create a test.
* After a successful creation, the system automatically redirects to the view test details screen of the newly-created test.

<figure><img src="../../../../.gitbook/assets/image (170).png" alt=""><figcaption><p>Create Adhoc Test </p></figcaption></figure>

## API Details for Create:

* Use pqm-service.&#x20;
* URL for inbox "/pqm-service/v1/\_create".
* Sample request object:&#x20;

```
{
    "tests": [
        {
            "tenantId": "pg.citya",
            "plantCode": "ANGUL_FSTP",
            "processCode": "FECAL_SLUDGE_MANAGEMENT",
            "stageCode": "SOLID_TREATMENT_VAR",
            "materialCode": "FECAL_SLUDGE",
            "testCriteria": [
                {
                    "criteriaCode": "TSS_LESST_100",
                    "resultValue": "21",
                    "isActive": true
                }
            ],
            "testType": "LAB_ADHOC",
            "scheduledDate": null,
            "isActive": null,
            "documents": [],
            "additionalDetails": {},
            "workflow": null
        }
    ],
    "RequestInfo": {
        "apiId": "Rainmaker",
        "authToken": "a0c56299-3bde-48e2-b0fb-76686fdff3dc",
        "userInfo": {
            "id": 722,
            "uuid": "56e8c2df-af55-46a9-a378-885915cde0ab",
            "userName": "TQM_DEV_ULBADMIN",
            "name": "ULB Admin",
            "mobileNumber": "7281638698",
            "emailId": null,
            "locale": null,
            "type": "EMPLOYEE",
            "roles": [
                {
                    "name": "PQM Admin",
                    "code": "PQM_ADMIN",
                    "tenantId": "pg.citya"
                }
            ],
            "active": true,
            "tenantId": "pg.citya",
            "permanentCity": null
        },
        "msgId": "1701080787582|en_IN",
        "plainAccessRequest": {}
    }
}
```

* #### Sample curl for inbox:

```
curl 'https://unified-dev.digit.org/pqm-service/v1/_create' \
  -H 'authority: unified-dev.digit.org' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9' \
  -H 'content-type: application/json;charset=UTF-8' \
  -H 'cookie: _ga_V2CPZCVTXQ=GS1.1.1695293925.1.1.1695293950.0.0.0; __cuid=59fd9aac25b044f6af006bd4b159cbbf; amp_fef1e8=f4fc07f6-3fb0-4c67-8114-a1beb906e625R...1hf75985a.1hf76uet8.i.8.q; _ga_P1TZCPKF6S=GS1.1.1699974064.1.1.1699975479.60.0.0; _ga=GA1.2.1291438273.1695293925; _ga_0JZG96DZSM=GS1.1.1699977339.2.0.1699977339.60.0.0' \
  -H 'origin: https://unified-dev.digit.org' \
  -H 'referer: https://unified-dev.digit.org/sanitation-ui/employee/tqm/add-test-result' \
  -H 'sec-ch-ua: "Google Chrome";v="119", "Chromium";v="119", "Not?A_Brand";v="24"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "Windows"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-origin' \
  -H 'user-agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.0.0 Safari/537.36' \
  --data-raw '{"tests":[{"tenantId":"pg.citya","plantCode":"ANGUL_FSTP","processCode":"FECAL_SLUDGE_MANAGEMENT","stageCode":"SOLID_TREATMENT_VAR","materialCode":"FECAL_SLUDGE","testCriteria":[{"criteriaCode":"TSS_LESST_100","resultValue":"21","isActive":true}],"testType":"LAB_ADHOC","scheduledDate":null,"isActive":null,"documents":[],"additionalDetails":{},"workflow":null}],"RequestInfo":{"apiId":"Rainmaker","authToken":"a0c56299-3bde-48e2-b0fb-76686fdff3dc","userInfo":{"id":722,"uuid":"56e8c2df-af55-46a9-a378-885915cde0ab","userName":"TQM_DEV_ULBADMIN","name":"ULB Admin","mobileNumber":"7281638698","emailId":null,"locale":null,"type":"EMPLOYEE","roles":[{"name":"PQM Admin","code":"PQM_ADMIN","tenantId":"pg.citya"}],"active":true,"tenantId":"pg.citya","permanentCity":null},"msgId":"1701080787582|en_IN","plainAccessRequest":{}}}' \
  --compressed
```

## Role-Action Mapping:

Role-action mapping is done for the "/pqm-service/v1/\_create" and "/pqm-service/v1/search" endpoint for a ULB admin user role, that is:&#x20;

```json
PQM_ADMIN
```
