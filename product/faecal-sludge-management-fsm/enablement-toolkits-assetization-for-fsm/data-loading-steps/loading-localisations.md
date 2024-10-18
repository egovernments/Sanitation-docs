# Loading Localisations

1.  Import the curl :\


    ```json
    curl --location --request POST 'https://fsm-2.3.digit.org/localization/messages/v1/_upsert?tenantId=pg' \
    --header 'Content-Type: application/json' \
    --data-raw '{
        "RequestInfo": {
            "apiId": "Rainmaker",
            "ver": ".01",
            "ts": "",
            "action": "_create",
            "did": "1",
            "key": "",
            "msgId": "20170310130900|hi_IN",
            "authToken": "94a4a1dd-5691-4534-88ce-d3440c2e1b85",
            "userInfo": {
                "id": 118,
                "userName": "TLCreator",
                "salutation": null,
                "name": "TLCreator",
                "gender": "MALE",
                "mobileNumber": "6666666666",
                "emailId": null,
                "altContactNumber": null,
                "pan": null,
                "aadhaarNumber": null,
                "permanentAddress": null,
                "permanentCity": null,
                "permanentPinCode": null,
                "correspondenceAddress": "Bang",
                "correspondenceCity": null,
                "correspondencePinCode": null,
                "addresses": [
                    {
                        "pinCode": null,
                        "city": null,
                        "address": "Bang",
                        "type": "CORRESPONDENCE",
                        "id": 235,
                        "tenantId": "uk.haldwani",
                        "userId": 118,
                        "addressType": "CORRESPONDENCE",
                        "lastModifiedDate": null,
                        "lastModifiedBy": null
                    }
                ],
                "active": true,
                "locale": null,
                "type": "EMPLOYEE",
                "accountLocked": false,
                "accountLockedDate": 1571224291053,
                "fatherOrHusbandName": "Test",
                "signature": null,
                "bloodGroup": null,
                "photo": null,
                "identificationMark": null,
                "createdBy": 4,
                "lastModifiedBy": 1,
                "tenantId": "uk.haldwani",
                "roles": [
                    {
                        "code": "PTCEMP",
                        "name": "PT Counter Employee",
                        "tenantId": "uk.haldwani"
                    },
                    {
                        "code": "TL_CEMP",
                        "name": "TL Counter Employee",
                        "tenantId": "uk.haldwani"
                    }
                ],
                "uuid": "573dd472-ebbc-4bbd-b093-897d33f95980",
                "createdDate": "07-10-2019 17:51:18",
                "lastModifiedDate": "13-11-2019 12:19:55",
                "dob": "1/10/2019",
                "pwdExpiryDate": "05-01-2020 17:51:18"
            }
        },
        "tenantId": "pg",
        "messages": [
            {
                "code": "FROM_OTHER_ULB",
                "message": "Other",
                "module": "rainmaker-fsm",
                "locale": "en_IN"
            }
        ]
    }'
    ```
2. Login to Super\_user and copy the auth token&#x20;
3. Change the req. Url to env you want to push also the auth token&#x20;
4. Add the localisation message in the request body.
5. Hit the url.

Reference Localisation Doc :

All localisations of FSM : [https://docs.google.com/spreadsheets/d/1RWqP-h\_s0lJZnQ9RvFOIePdy7Hxle-RN/edit?usp=sharing\&ouid=109809705320882389789\&rtpof=true\&sd=true](https://docs.google.com/spreadsheets/d/1RWqP-h\_s0lJZnQ9RvFOIePdy7Hxle-RN/edit?usp=sharing\&ouid=109809705320882389789\&rtpof=true\&sd=true)

[https://docs.google.com/document/d/1z-V8U8BvT1Ict1gRyf4b4aOCjr\_snJ-Psk6A\_5oKzWs/edit?usp=sharing](https://docs.google.com/document/d/1z-V8U8BvT1Ict1gRyf4b4aOCjr\_snJ-Psk6A\_5oKzWs/edit?usp=sharing)

[https://drive.google.com/drive/folders/1bIv4txLjOSt2L4DsNWkShSgmZFzo73yU?usp=drive\_link](https://drive.google.com/drive/folders/1bIv4txLjOSt2L4DsNWkShSgmZFzo73yU?usp=drive\_link)

Important points :

1. Related modules for FSM : `rainmaker-fsm`,`rainmaker-common`,`rainmaker-dss`
2. Push the localisation for all the modules separately
3. After pushing the localisation,make a file to store all the localisations according to modules.
