# Plant Mapping of FSTP

*   Import this curl :\


    ```json
    curl --location --request POST 'https://sujog-dev.odisha.gov.in/fsm/plantmap/v1/_create' \
    --header 'Content-Type: application/json' \
    --data-raw '{
        "RequestInfo": {
            "apiInfo": {
                "id": "string",
                "version": "string",
                "path": "string"
            },
            "deviceDetail": {
                "id": "string",
                "signature": "string"
            },
            "ts": 0,
            "action": "string",
            "key": "string",
            "msgId": "string",
            "requesterId": "string",
            "authToken": "45092a19-3dab-43b0-a9e1-19e8a6c94923",
            "userInfo": {"id":3186071,"userName":"FSM_ADMINDEV","salutation":null,"name":"Taresh","gender":"MALE","mobileNumber":"7721827042","emailId":"vddvd@gmail.com","altContactNumber":null,"pan":null,"aadhaarNumber":null,"permanentAddress":null,"permanentCity":null,"permanentPinCode":null,"correspondenceAddress":null,"correspondenceCity":null,"correspondencePinCode":null,"active":true,"locale":null,"type":"EMPLOYEE","accountLocked":false,"accountLockedDate":0,"fatherOrHusbandName":"Dilip","relationship":"FATHER","signature":null,"bloodGroup":null,"photo":null,"identificationMark":null,"createdBy":575,"lastModifiedBy":1,"tenantId":"od.cuttack","roles":[{"code":"EMPLOYEE","name":"Employee","tenantId":"od"},{"code":"FSM_ADMIN","name":"FSM Administrator","tenantId":"od.cuttack"},{"code":"HRMS_ADMIN","name":"HRMS ADMIN","tenantId":"od.cuttack"},{"code":"SUPERUSER","name":"Super User","tenantId":"od.cuttack"},{"code":"FSM_COLLECTOR","name":"FSM Payment Collector","tenantId":"od"},{"code":"FSM_CREATOR_EMP","name":"FSM Employee Application Creator","tenantId":"od"},{"code":"FSM_EMP_FSTPO","name":"FSM FSTP Opperator","tenantId":"od"},{"code":"SUPERUSER","name":"Super User","tenantId":"od"},{"code":"FSM_EDITOR_EMP","name":"FSM Employee Application Editor","tenantId":"od"},{"code":"FSM_ADMIN","name":"FSM Administrator","tenantId":"od"}],"uuid":"2f3851cd-864e-42d7-869c-d5a05abb8f39","createdDate":"01-09-2022 17:04:45","lastModifiedDate":"17-01-2023 13:49:59","dob":"21/11/1995","pwdExpiryDate":"30-11-2022 17:04:44"}
        },
        "plantMapping": {
            "employeeUuid": "c3249480-b45c-43b6-bfe1-cb78330d258c",
             "plantCode": "ODAG_064",
            "tenantId": "od.odagaon",
            "status":"ACTIVE"
        }
    }'
    ```
* Login from FSTP credientials and copy the uuid of FSTP user.
* Take FSTP plantCode from [MDMS](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/FSM/FSTPPlantInfo.json) PlantInfo.json file for specific ulb.
* The status should be always ACTIVE.
* Login from FSM\_ADMINDEV credentials(for sujog-dev) which is having FSM Admin role for all the ulb’s.
* Copy the auth token and user-info. Paste the auth token in the req. Body “authToken” field.
* Hit the url.
