# Sanitation Worker Details

From the [FSM Registry page](fsm-registry.md) Admins can Search for a Sanitation Worker and go to it's details page by clicking on Sanitation Worker Id



## Sanitation Worker Details page

* This page shows all the details about a Sanitation worker&#x20;
* Sample Page Screenshot is given below for reference
*

    <figure><img src="../../../../.gitbook/assets/image (176).png" alt=""><figcaption><p>Sanitation Worker Details</p></figcaption></figure>


* Admin users will get an action bar at the bottom of the page which has two actions&#x20;
* Edit -> This takes the user to [Edit Sanitation worker Page](edit-sanitation-worker.md)
* Delete -> This calls the update Individual API and disables this user ( Soft delete)
* A corresponding toast message is shown
* After taking delete action page is automatically redirected to the [FSM Registry](fsm-registry.md)



### API Details

#### Search Individual

* We are hitting this endpoint "/individual/v1/\_search" to fetch Sanitation Worker Details
* Refer the curl below:

````json
```powershell
curl --location 'https://unified-dev.digit.org/individual/v1/_search?tenantId=pg.citya&offset=0&limit=100&_=1700205653156' \
--header 'authority: unified-dev.digit.org' \
--header 'accept: application/json, text/plain, */*' \
--header 'accept-language: en-GB,en-US;q=0.9,en;q=0.8' \
--header 'content-type: application/json' \
--header 'cookie: MicrosoftApplicationsTelemetryDeviceId=55de1d9a-a0cf-4d5b-9255-85b5b1493061; MicrosoftApplicationsTelemetryFirstLaunchTime=2023-10-16T06:23:27.369Z; PGADMIN_LANGUAGE=en; _oauth2_proxy=eyJFbWFpbCI6InNoYWlsZXNoLmt1bWFyQGVnb3Zlcm5tZW50cy5vcmciLCJVc2VyIjoic2hhaWxlc2gtZWdvdiJ9|1700033260|CTEqBthhJjZd2eND93q4SwyRXNc=; __cuid=9b7e8966323a4b45aa49cdd35080b492; amp_fef1e8=606c34a4-95cc-4a2b-bb9c-23bcfd531c60R...1hfbmtumv.1hfbmu1bc.37.l.3s' \
--header 'origin: https://unified-dev.digit.org' \
--header 'referer: https://unified-dev.digit.org/works-ui/employee/masters/view-wageseeker?tenantId=pg.citya&individualId=IND-2023-09-25-002330' \
--header 'sec-ch-ua: "Google Chrome";v="119", "Chromium";v="119", "Not?A_Brand";v="24"' \
--header 'sec-ch-ua-mobile: ?0' \
--header 'sec-ch-ua-platform: "Windows"' \
--header 'sec-fetch-dest: empty' \
--header 'sec-fetch-mode: cors' \
--header 'sec-fetch-site: same-origin' \
--header 'user-agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.0.0 Safari/537.36' \
--data '{
    "Individual": {
        "roleCodes":["SANITATION_WORKER"],
        "mobileNumber":"9494949494",
        "individualName":"Dummy1",
        "individualId": "IND-2023-11-23-010831"
    },
    "RequestInfo": {
        "apiId": "Rainmaker",
        "authToken": "4ff28c82-654f-4403-9f2d-8547b9c35687",
        "userInfo": {
            "id": 618,
            "uuid": "40e3b45a-0f64-4e8c-8768-aab82c095b2d",
            "userName": "AUTO1",
            "name": "Jagankumar E",
            "mobileNumber": "7654376563",
            "emailId": null,
            "locale": null,
            "type": "EMPLOYEE",
            "roles": [
                {
                    "name": "HRMS Admin",
                    "code": "HRMS_ADMIN",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "ESTIMATE VERIFIER",
                    "code": "ESTIMATE_VERIFIER",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "OFFICER IN CHARGE",
                    "code": "OFFICER_IN_CHARGE",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "PROJECT CREATOR",
                    "code": "PROJECT_CREATOR",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "BILL_CREATOR",
                    "code": "BILL_CREATOR",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "ESTIMATE VIEWER",
                    "code": "ESTIMATE_VIEWER",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "MB_APPROVER",
                    "code": "MB_APPROVER",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "MUKTA Admin",
                    "code": "MUKTA_ADMIN",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "WORK ORDER CREATOR",
                    "code": "WORK_ORDER_CREATOR",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "ESTIMATE APPROVER",
                    "code": "ESTIMATE_APPROVER",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "MB_VERIFIER",
                    "code": "MB_VERIFIER",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "WORK ORDER VERIFIER",
                    "code": "WORK_ORDER_VERIFIER",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "PROJECT VIEWER",
                    "code": "PROJECT_VIEWER",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "MB_CREATOR",
                    "code": "MB_CREATOR",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "MUSTER ROLL VERIFIER",
                    "code": "MUSTER_ROLL_VERIFIER",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "Localisation admin",
                    "code": "LOC_ADMIN",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "Employee Common",
                    "code": "EMPLOYEE_COMMON",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "BILL_VIEWER",
                    "code": "BILL_VIEWER",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "TECHNICAL SANCTIONER",
                    "code": "TECHNICAL_SANCTIONER",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "MUSTER ROLL APPROVER",
                    "code": "MUSTER_ROLL_APPROVER",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "WORK ORDER APPROVER",
                    "code": "WORK_ORDER_APPROVER",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "ESTIMATE CREATOR",
                    "code": "ESTIMATE_CREATOR",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "MDMS Admin",
                    "code": "MDMS_ADMIN",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "MB_VIEWER",
                    "code": "MB_VIEWER",
                    "tenantId": "pg.citya"
                },
                {
                    "name": "SUPER USER",
                    "code": "SUPERUSER",
                    "tenantId": "pg.citya"
                }
            ],
            "active": true,
            "tenantId": "pg.citya",
            "permanentCity": null
        },
        "msgId": "1700205653156|en_IN",
        "plainAccessRequest": {}
    }
}'
```
````



#### Update Individual

* When individual is deleted we are making use of individual update "/individual/v1/\_update"
* Refer to the curl below

````json
```powershell
curl --location 'https://unified-dev.digit.org/individual/v1/_update?_=1700205712385' \
--header 'authority: unified-dev.digit.org' \
--header 'accept: application/json, text/plain, */*' \
--header 'accept-language: en-GB,en-US;q=0.9,en;q=0.8' \
--header 'content-type: application/json' \
--header 'cookie: MicrosoftApplicationsTelemetryDeviceId=55de1d9a-a0cf-4d5b-9255-85b5b1493061; MicrosoftApplicationsTelemetryFirstLaunchTime=2023-10-16T06:23:27.369Z; PGADMIN_LANGUAGE=en; _oauth2_proxy=eyJFbWFpbCI6InNoYWlsZXNoLmt1bWFyQGVnb3Zlcm5tZW50cy5vcmciLCJVc2VyIjoic2hhaWxlc2gtZWdvdiJ9|1700033260|CTEqBthhJjZd2eND93q4SwyRXNc=; __cuid=9b7e8966323a4b45aa49cdd35080b492; amp_fef1e8=606c34a4-95cc-4a2b-bb9c-23bcfd531c60R...1hfbmtumv.1hfbmu1bc.37.l.3s' \
--header 'origin: https://unified-dev.digit.org' \
--header 'referer: https://unified-dev.digit.org/works-ui/employee/masters/modify-wageseeker?tenantId=pg.citya&individualId=IND-2023-09-25-002330' \
--header 'sec-ch-ua: "Google Chrome";v="119", "Chromium";v="119", "Not?A_Brand";v="24"' \
--header 'sec-ch-ua-mobile: ?0' \
--header 'sec-ch-ua-platform: "Windows"' \
--header 'sec-fetch-dest: empty' \
--header 'sec-fetch-mode: cors' \
--header 'sec-fetch-site: same-origin' \
--header 'user-agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.0.0 Safari/537.36' \
--data '{"Individual":{"tenantId":"pg.citya","name":{"givenName":"Anjali"},"dateOfBirth":"20/09/1990","gender":"FEMALE","mobileNumber":"7007099195","fatherName":"Belram","relationship":"HUSBAND","additionalFields":{"fields":[{"key":"SOCIAL_CATEGORY","value":"SC"}]},"address":[{"id":"2f96f127-825e-4de0-971a-caaab582d186","individualId":"8b8c53ea-9d47-476d-b5ff-fd70aaf1a6d2","tenantId":"pg.citya","city":"pg.citya","doorNo":"NA","street":"NA","type":"PERMANENT","locality":{"code":"SUN01"},"ward":{"code":"B1"}}],"auditDetails":{"createdBy":"1ec60cb3-a0c1-4d24-97ef-7a57f58e820d","lastModifiedBy":"1ec60cb3-a0c1-4d24-97ef-7a57f58e820d","createdTime":1695621659633,"lastModifiedTime":1695621659633},"id":"8b8c53ea-9d47-476d-b5ff-fd70aaf1a6d2","individualId":"IND-2023-09-25-002330","skills":[{"id":"a41c97c7-73ed-4376-af5e-6e0bc2c8fd68","clientReferenceId":null,"individualId":"8b8c53ea-9d47-476d-b5ff-fd70aaf1a6d2","type":"FEMALE_MULIA","level":"UNSKILLED","experience":null,"isDeleted":false,"auditDetails":{"createdBy":"1ec60cb3-a0c1-4d24-97ef-7a57f58e820d","lastModifiedBy":"1ec60cb3-a0c1-4d24-97ef-7a57f58e820d","createdTime":1695621659638,"lastModifiedTime":1695621659638},"code":"UNSKILLED.FEMALE_MULIA"},{"id":"95c91c30-7e26-4187-9626-46b68e4f6ccc","clientReferenceId":null,"individualId":"8b8c53ea-9d47-476d-b5ff-fd70aaf1a6d2","type":"MALE_MULIA","level":"UNSKILLED","experience":null,"isDeleted":false,"auditDetails":{"createdBy":"1ec60cb3-a0c1-4d24-97ef-7a57f58e820d","lastModifiedBy":"1ec60cb3-a0c1-4d24-97ef-7a57f58e820d","createdTime":1695621659638,"lastModifiedTime":1695621659638},"code":"UNSKILLED.MALE_MULIA"},{"id":"47b92eaf-4e31-4513-908d-ad8bd4b4e9dc","clientReferenceId":null,"individualId":"8b8c53ea-9d47-476d-b5ff-fd70aaf1a6d2","type":"SCAVENGER","level":"UNSKILLED","experience":null,"isDeleted":false,"auditDetails":{"createdBy":"1ec60cb3-a0c1-4d24-97ef-7a57f58e820d","lastModifiedBy":"1ec60cb3-a0c1-4d24-97ef-7a57f58e820d","createdTime":1695621659638,"lastModifiedTime":1695621659638},"code":"UNSKILLED.SCAVENGER"}],"rowVersion":1,"identifiers":[{"id":"3491e99d-d9a3-41d5-bdaf-2538fae19ef9","clientReferenceId":"a73d268a-07b6-ab4f-76c6-fe7e3d38188e","individualId":"8b8c53ea-9d47-476d-b5ff-fd70aaf1a6d2","identifierType":"AADHAAR","identifierId":"********7656","isDeleted":false,"auditDetails":{"createdBy":"1ec60cb3-a0c1-4d24-97ef-7a57f58e820d","lastModifiedBy":"1ec60cb3-a0c1-4d24-97ef-7a57f58e820d","createdTime":1695621659637,"lastModifiedTime":1695621659637}}]},"RequestInfo":{"apiId":"Rainmaker","authToken":"17b86f8a-6063-4028-abef-fbf005c1ba75","userInfo":{"id":618,"uuid":"40e3b45a-0f64-4e8c-8768-aab82c095b2d","userName":"AUTO1","name":"Jagankumar E","mobileNumber":"7654376563","emailId":null,"locale":null,"type":"EMPLOYEE","roles":[{"name":"HRMS Admin","code":"HRMS_ADMIN","tenantId":"pg.citya"},{"name":"ESTIMATE VERIFIER","code":"ESTIMATE_VERIFIER","tenantId":"pg.citya"},{"name":"OFFICER IN CHARGE","code":"OFFICER_IN_CHARGE","tenantId":"pg.citya"},{"name":"PROJECT CREATOR","code":"PROJECT_CREATOR","tenantId":"pg.citya"},{"name":"BILL_CREATOR","code":"BILL_CREATOR","tenantId":"pg.citya"},{"name":"ESTIMATE VIEWER","code":"ESTIMATE_VIEWER","tenantId":"pg.citya"},{"name":"MB_APPROVER","code":"MB_APPROVER","tenantId":"pg.citya"},{"name":"MUKTA Admin","code":"MUKTA_ADMIN","tenantId":"pg.citya"},{"name":"WORK ORDER CREATOR","code":"WORK_ORDER_CREATOR","tenantId":"pg.citya"},{"name":"ESTIMATE APPROVER","code":"ESTIMATE_APPROVER","tenantId":"pg.citya"},{"name":"MB_VERIFIER","code":"MB_VERIFIER","tenantId":"pg.citya"},{"name":"WORK ORDER VERIFIER","code":"WORK_ORDER_VERIFIER","tenantId":"pg.citya"},{"name":"PROJECT VIEWER","code":"PROJECT_VIEWER","tenantId":"pg.citya"},{"name":"MB_CREATOR","code":"MB_CREATOR","tenantId":"pg.citya"},{"name":"MUSTER ROLL VERIFIER","code":"MUSTER_ROLL_VERIFIER","tenantId":"pg.citya"},{"name":"Localisation admin","code":"LOC_ADMIN","tenantId":"pg.citya"},{"name":"Employee Common","code":"EMPLOYEE_COMMON","tenantId":"pg.citya"},{"name":"BILL_VIEWER","code":"BILL_VIEWER","tenantId":"pg.citya"},{"name":"TECHNICAL SANCTIONER","code":"TECHNICAL_SANCTIONER","tenantId":"pg.citya"},{"name":"MUSTER ROLL APPROVER","code":"MUSTER_ROLL_APPROVER","tenantId":"pg.citya"},{"name":"WORK ORDER APPROVER","code":"WORK_ORDER_APPROVER","tenantId":"pg.citya"},{"name":"ESTIMATE CREATOR","code":"ESTIMATE_CREATOR","tenantId":"pg.citya"},{"name":"MDMS Admin","code":"MDMS_ADMIN","tenantId":"pg.citya"},{"name":"MB_VIEWER","code":"MB_VIEWER","tenantId":"pg.citya"},{"name":"SUPER USER","code":"SUPERUSER","tenantId":"pg.citya"}],"active":true,"tenantId":"pg.citya","permanentCity":null},"msgId":"1700205712385|en_IN","plainAccessRequest":{}}}'
```
````



#### Update Vendor

* When we delete a Sanitation worker who is tagged to a vendor we are updating the worker - vendor tagging to inactive.
* Refer to the curl below:

{% code overflow="wrap" %}
````json
```powershell
curl --location 'http://localhost:3000/vendor/v1/_update?tenantId=pg.citya' \
--header 'Accept: application/json, text/plain, */*' \
--header 'Accept-Language: en-US,en;q=0.9' \
--header 'Connection: keep-alive' \
--header 'Content-Type: application/json;charset=UTF-8' \
--header 'Origin: http://localhost:3000' \
--header 'Referer: http://localhost:3000/sanitation-ui/employee/fsm/registry?selectedTabs=DRIVER' \
--header 'Sec-Fetch-Dest: empty' \
--header 'Sec-Fetch-Mode: cors' \
--header 'Sec-Fetch-Site: same-origin' \
--header 'User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.0.0 Safari/537.36' \
--header 'sec-ch-ua: "Google Chrome";v="119", "Chromium";v="119", "Not?A_Brand";v="24"' \
--header 'sec-ch-ua-mobile: ?0' \
--header 'sec-ch-ua-platform: "Windows"' \
--data-raw '{
    "vendor":   {
            "id": "ea138945-f35b-42a3-96af-9ded096fb809",
            "tenantId": "pg.citya",
            "name": "Raj",
            "address": {
                "tenantId": "pg.citya",
                "doorNo": "",
                "plotNo": "",
                "id": "894f60f2-0d27-4f24-b1ec-a0017920b51a",
                "landmark": "",
                "city": "CityA",
                "district": "CityA",
                "region": "CityA",
                "state": null,
                "country": "in",
                "pincode": "",
                "additionalDetails": "{\"description\": \"\"}",
                "buildingName": "",
                "street": "",
                "locality": {
                    "code": "SUN01",
                    "name": "Ajit Nagar - Area1",
                    "label": "Locality",
                    "latitude": "31.63089",
                    "longitude": "74.871552",
                    "children": [],
                    "materializedPath": null
                },
                "geoLocation": null,
                "auditDetails": null
            },
            "owner": {
                "id": 861,
                "uuid": "31b14828-1c46-42bb-9364-8f456509c375",
                "userName": "6543217890",
                "password": null,
                "salutation": null,
                "name": "Raj",
                "gender": "MALE",
                "mobileNumber": "6543217890",
                "emailId": "abc@egov.com",
                "altContactNumber": null,
                "pan": null,
                "aadhaarNumber": null,
                "permanentAddress": null,
                "permanentCity": null,
                "permanentPinCode": null,
                "correspondenceCity": null,
                "correspondencePinCode": null,
                "correspondenceAddress": null,
                "active": true,
                "dob": 1700611200000,
                "pwdExpiryDate": 1708695918000,
                "locale": null,
                "type": "CITIZEN",
                "signature": null,
                "accountLocked": false,
                "roles": [
                    {
                        "id": null,
                        "name": "FSM Desluding Operator",
                        "code": "FSM_DSO",
                        "tenantId": "pg"
                    },
                    {
                        "id": null,
                        "name": "Citizen",
                        "code": "CITIZEN",
                        "tenantId": "pg"
                    }
                ],
                "fatherOrHusbandName": "Raj",
                "relationship": "OTHER",
                "bloodGroup": null,
                "identificationMark": null,
                "photo": null,
                "createdBy": "715",
                "createdDate": 1700820918000,
                "lastModifiedBy": "715",
                "lastModifiedDate": 1700826327000,
                "otpReference": null,
                "tenantId": "pg"
            },
            "vehicles": null,
            "drivers": [
                {
                    "id": "f24d113e-c163-4aa1-a1b3-b54807308a40",
                    "tenantId": "pg.citya",
                    "name": "pintu",
                    "owner": {
                        "id": 820,
                        "uuid": "fc688f84-6b5c-4da5-ae69-3580d3d81fc6",
                        "userName": "1111111149",
                        "password": null,
                        "salutation": null,
                        "name": "pintu",
                        "gender": "MALE",
                        "mobileNumber": "1111111149",
                        "emailId": "abc@egov.com",
                        "altContactNumber": null,
                        "pan": null,
                        "aadhaarNumber": null,
                        "permanentAddress": null,
                        "permanentCity": null,
                        "permanentPinCode": null,
                        "correspondenceCity": null,
                        "correspondencePinCode": null,
                        "correspondenceAddress": null,
                        "active": true,
                        "dob": 0,
                        "pwdExpiryDate": 1706888228000,
                        "locale": null,
                        "type": "CITIZEN",
                        "signature": null,
                        "accountLocked": false,
                        "roles": [
                            {
                                "id": null,
                                "name": "FSM Driver",
                                "code": "FSM_DRIVER",
                                "tenantId": "pg.citya"
                            },
                            {
                                "id": null,
                                "name": "FSM Driver",
                                "code": "FSM_DRIVER",
                                "tenantId": "pg"
                            }
                        ],
                        "fatherOrHusbandName": "pintu",
                        "relationship": "OTHER",
                        "bloodGroup": null,
                        "identificationMark": null,
                        "photo": null,
                        "createdBy": "715",
                        "createdDate": 1699013642000,
                        "lastModifiedBy": "715",
                        "lastModifiedDate": 1700827360000,
                        "otpReference": null,
                        "tenantId": "pg"
                    },
                    "ownerId": "fc688f84-6b5c-4da5-ae69-3580d3d81fc6",
                    "additionalDetails": null,
                    "description": null,
                    "licenseNumber": "12345678999995",
                    "status": "DISABLED",
                    "auditDetails": {
                        "createdBy": "4a747fc5-6a8c-4645-8748-fec35f1b9e17",
                        "lastModifiedBy": "4a747fc5-6a8c-4645-8748-fec35f1b9e17",
                        "createdTime": 1698993428899,
                        "lastModifiedTime": 1700807560471
                    },
                    "vendorDriverStatus": "ACTIVE"
                }
            ],
            "workers": [
                {

                    "id": "f3104f07-9b62-460d-8b9c-e16a4b6c740f",
                    "tenantId": "pg.citya",
                    "vendorId": "ea138945-f35b-42a3-96af-9ded096fb809",
                    "individualId": "IND-2023-11-23-010844",
                    "additionalDetails": null,
                    "auditDetails": {
                        "createdBy": "4a747fc5-6a8c-4645-8748-fec35f1b9e17",
                        "lastModifiedBy": "4a747fc5-6a8c-4645-8748-fec35f1b9e17",
                        "createdTime": 1700801118082,
                        "lastModifiedTime": 1700803699721
                    },
                    "vendorWorkerStatus": "ACTIVE"
                },
                {
                    "individualId":"IND-2023-11-23-010831",
                    "vendorWorkerStatus":"ACTIVE"
                }

            ],
            "additionalDetails": {
                "description": ""
            },
            "source": "WhatsApp",
            "description": null,
            "ownerId": "31b14828-1c46-42bb-9364-8f456509c375",
            "agencyType": "ULB",
            "paymentPreference": "post-service",
            "status": "ACTIVE",
            "auditDetails": {
                "createdBy": "4a747fc5-6a8c-4645-8748-fec35f1b9e17",
                "lastModifiedBy": "4a747fc5-6a8c-4645-8748-fec35f1b9e17",
                "createdTime": 1700801118082,
                "lastModifiedTime": 1700806527779
            }
        },
    "RequestInfo": {
        "apiId": "Rainmaker",
        "authToken": "4ff28c82-654f-4403-9f2d-8547b9c35687",
        "userInfo": {
            "id": 715,
            "uuid": "4a747fc5-6a8c-4645-8748-fec35f1b9e17",
            "userName": "ADMIN",
            "name": "ADMIN",
            "mobileNumber": "9035169725",
            "emailId": "",
            "locale": null,
            "type": "EMPLOYEE",
            "roles": [
                {
                    "name": "FSM Administrator",
                    "code": "FSM_ADMIN",
                    "tenantId": "pg.citya"
                }
            ],
            "active": true,
            "tenantId": "pg.citya",
            "permanentCity": "CityA"
        },
        "msgId": "1700732793623|en_IN",
        "plainAccessRequest": {}
    }
}'
```
````
{% endcode %}



### Role Action Mapping

Role Action mapping is done for the above three endpoints for FSM\_ADMIN role

```
FSM_ADMIN
```
