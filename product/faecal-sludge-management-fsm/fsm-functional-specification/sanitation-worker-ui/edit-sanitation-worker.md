# Edit Sanitation Worker

From the [FSM Registry](fsm-registry.md) Screen Admin can search for Sanitation worker and go to it's [details page](sanitation-worker-details.md).



## Updating Sanitation Workers

* From the [Sanitation Worker details page](sanitation-worker-details.md) , admin can click on "Edit" action
* Admin will be redirected to the edit sanitation worker page
* This page contains the same form as [Create Sanitation Worker ](create-sanitation-worker.md). The only difference is all the fields are auto populated based on the worker that we are updating
* Admin can update all the details except Sanitation Worker Id and Name
* Clicking on Submit will show a response screen saying Sanitation Worker details updated successfully

### API Details

#### Individual Update

* We are hitting Individual Update endpoint "/individual/v1/\_update" to update the details of a Sanitation worker
* Refer the curl below:

```json
curl 'https://unified-dev.digit.org/individual/v1/_update?tenantId=pg.citya' \
  -H 'authority: unified-dev.digit.org' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9' \
  -H 'content-type: application/json;charset=UTF-8' \
  -H 'origin: https://unified-dev.digit.org' \
  -H 'referer: https://unified-dev.digit.org/sanitation-ui/employee/fsm/registry/edit-worker?id=IND-2023-12-11-011010' \
  -H 'sec-ch-ua: "Not_A Brand";v="8", "Chromium";v="120", "Google Chrome";v="120"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "Windows"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-origin' \
  -H 'user-agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36' \
  --data-raw '{"Individual":{"id":"02bc1a5b-fed9-4176-bada-974aeeb8e613","individualId":"IND-2023-12-11-011010","tenantId":"pg.citya","clientReferenceId":null,"userId":null,"userUuid":null,"name":{"givenName":"sdjhsdhsdkjhs","familyName":null,"otherNames":null},"dateOfBirth":-19800000,"gender":"MALE","bloodGroup":null,"mobileNumber":"7897897899","altContactNumber":null,"email":null,"address":[{"id":"d2a6e81d-c3ce-4608-af11-5b0d0ca0aa0d","clientReferenceId":null,"individualId":"02bc1a5b-fed9-4176-bada-974aeeb8e613","tenantId":"pg.citya","doorNo":null,"latitude":0,"longitude":0,"locationAccuracy":0,"type":"PERMANENT","addressLine1":null,"addressLine2":null,"landmark":null,"city":"pg.citya","pincode":null,"buildingName":null,"street":null,"locality":{"code":"SUN02","name":null,"label":null,"latitude":null,"longitude":null,"children":null,"materializedPath":null},"ward":null,"isDeleted":false,"auditDetails":{"createdBy":"4a747fc5-6a8c-4645-8748-fec35f1b9e17","lastModifiedBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","createdTime":1702288646617,"lastModifiedTime":1702459735736}}],"fatherName":null,"husbandName":null,"relationship":null,"identifiers":null,"skills":[{"type":"Driving","level":"UNSKILLED"}],"photo":null,"additionalFields":{"fields":[{"key":"FUNCTIONAL_ROLE_1","value":"SANITATION_HELPER"},{"key":"EMPLOYMENT_TYPE_1","value":"FIXED"},{"key":"FUNCTIONAL_ROLE_COUNT","value":"01"},{"key":"EMPLOYER","value":"ULB"}]},"isDeleted":false,"rowVersion":11,"auditDetails":{"createdBy":"4a747fc5-6a8c-4645-8748-fec35f1b9e17","lastModifiedBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","createdTime":1702288646617,"lastModifiedTime":1702459735737},"clientAuditDetails":{"createdBy":null,"lastModifiedBy":null,"createdTime":0,"lastModifiedTime":0},"isSystemUser":true,"isSystemUserActive":true,"userDetails":{"username":"7897897899","password":null,"tenantId":"pg.citya","roles":[{"code":"CITIZEN","tenantId":"pg.citya"},{"code":"SANITATION_WORKER","tenantId":"pg.citya"},{"code":"SANITATION_HELPER","tenantId":"pg.citya"}],"type":"CITIZEN"}},"RequestInfo":{"apiId":"Rainmaker","authToken":"06170439-7751-41d9-8043-04ede25e9499","userInfo":{"id":927,"uuid":"49341961-f413-4ae1-b7f8-92a8d9136f38","userName":"ADMIN","name":"Plant operator","mobileNumber":"8282828121","emailId":null,"locale":null,"type":"EMPLOYEE","roles":[{"name":"FSM Administrator","code":"FSM_ADMIN","tenantId":"pg.citya"},{"name":"FSM Employee Application Viewer","code":"FSM_VIEW_EMP","tenantId":"pg.citya"}],"active":true,"tenantId":"pg.citya","permanentCity":null},"msgId":"1702469181914|en_IN","plainAccessRequest":{}}}' \
  --compressed
```



#### Vendor Update

* If during update, vendor details are changed then along with individual update we are calling vendor update "/vendor/v1/\_update"
* Refer the curl below

```json
curl 'https://unified-dev.digit.org/vendor/v1/_update?tenantId=pg.citya' \
  -H 'authority: unified-dev.digit.org' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9' \
  -H 'content-type: application/json;charset=UTF-8' \
  -H 'origin: https://unified-dev.digit.org' \
  -H 'referer: https://unified-dev.digit.org/sanitation-ui/employee/fsm/registry/edit-worker?id=IND-2023-12-11-011010' \
  -H 'sec-ch-ua: "Not_A Brand";v="8", "Chromium";v="120", "Google Chrome";v="120"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "Windows"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-origin' \
  -H 'user-agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36' \
  --data-raw '{"vendor":{"id":"da5dae4c-95d7-43b6-a92f-e504d6000ef8","tenantId":"pg.citya","name":"djhdjkdhsjkh","address":{"tenantId":"pg.citya","doorNo":"","plotNo":"","id":"7132305a-ecd1-4f5e-af02-9894103a3742","landmark":"","city":"CityA","district":"CityA","region":"CityA","state":null,"country":"in","pincode":"","additionalDetails":"{\"description\": \"\"}","buildingName":"","street":"","locality":{"code":"SUN01","name":"Ajit Nagar - Area1","label":"Locality","latitude":"31.63089","longitude":"74.871552","children":[],"materializedPath":null},"geoLocation":null,"auditDetails":null},"owner":{"id":933,"uuid":"5b610239-fa1c-4538-b771-90cf255304b3","userName":"7787678673","password":null,"salutation":null,"name":"djhdjkdhsjkh","gender":"MALE","mobileNumber":"7787678673","emailId":"abc@egov.com","altContactNumber":null,"pan":null,"aadhaarNumber":null,"permanentAddress":null,"permanentCity":null,"permanentPinCode":null,"correspondenceCity":null,"correspondencePinCode":null,"correspondenceAddress":null,"active":true,"dob":0,"pwdExpiryDate":1710545514000,"locale":null,"type":"CITIZEN","signature":null,"accountLocked":false,"roles":[{"id":null,"name":"FSM Desluding Operator","code":"FSM_DSO","tenantId":"pg"},{"id":null,"name":"Citizen","code":"CITIZEN","tenantId":"pg"}],"fatherOrHusbandName":"djhdjkdhsjkh","relationship":"OTHER","bloodGroup":null,"identificationMark":null,"photo":null,"createdBy":"927","createdDate":1702393314000,"lastModifiedBy":"927","lastModifiedDate":1702486776000,"otpReference":null,"tenantId":"pg"},"vehicles":null,"drivers":null,"workers":[{"id":"59090353-59f6-4242-86ea-bbd92ecbe674","tenantId":"pg.citya","vendorId":"da5dae4c-95d7-43b6-a92f-e504d6000ef8","individualId":"1e5ad42e-2734-48fc-b934-fc32ef5058a6","additionalDetails":null,"auditDetails":{"createdBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","lastModifiedBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","createdTime":1702373514847,"lastModifiedTime":1702462026145},"vendorWorkerStatus":"ACTIVE"},{"id":"1e19a4f0-3ead-4985-bb59-aa4b57df6af2","tenantId":"pg.citya","vendorId":"da5dae4c-95d7-43b6-a92f-e504d6000ef8","individualId":"c050f0e5-d0a0-4f2a-83c0-63876827d6e1","additionalDetails":null,"auditDetails":{"createdBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","lastModifiedBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","createdTime":1702373514847,"lastModifiedTime":1702462071879},"vendorWorkerStatus":"ACTIVE"},{"id":"0a79d0d1-ac14-4ed4-a6cc-7971a29043e2","tenantId":"pg.citya","vendorId":"da5dae4c-95d7-43b6-a92f-e504d6000ef8","individualId":"f6f99ec9-9fcd-489c-8f66-58a4a63432b3","additionalDetails":null,"auditDetails":{"createdBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","lastModifiedBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","createdTime":1702373514847,"lastModifiedTime":1702459924693},"vendorWorkerStatus":"ACTIVE"},{"id":"39cc81f9-58e7-4912-9743-81f51ba03cd5","tenantId":"pg.citya","vendorId":"da5dae4c-95d7-43b6-a92f-e504d6000ef8","individualId":"8215eb13-f247-4782-9acd-665214d24a98","additionalDetails":null,"auditDetails":{"createdBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","lastModifiedBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","createdTime":1702373514847,"lastModifiedTime":1702461623872},"vendorWorkerStatus":"ACTIVE"},{"individualId":"02bc1a5b-fed9-4176-bada-974aeeb8e613","vendorWorkerStatus":"ACTIVE"}],"additionalDetails":{"description":""},"source":"WhatsApp","description":null,"ownerId":"5b610239-fa1c-4538-b771-90cf255304b3","agencyType":"ULB","paymentPreference":"post-service","status":"ACTIVE","auditDetails":{"createdBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","lastModifiedBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","createdTime":1702373514847,"lastModifiedTime":1702466976705}},"RequestInfo":{"apiId":"Rainmaker","authToken":"06170439-7751-41d9-8043-04ede25e9499","userInfo":{"id":927,"uuid":"49341961-f413-4ae1-b7f8-92a8d9136f38","userName":"ADMIN","name":"Plant operator","mobileNumber":"8282828121","emailId":null,"locale":null,"type":"EMPLOYEE","roles":[{"name":"FSM Administrator","code":"FSM_ADMIN","tenantId":"pg.citya"},{"name":"FSM Employee Application Viewer","code":"FSM_VIEW_EMP","tenantId":"pg.citya"}],"active":true,"tenantId":"pg.citya","permanentCity":null},"msgId":"1702469182205|en_IN","plainAccessRequest":{}}}' \
  --compressed
```



### Role Action Mapping

* Role action mapping is done for the above 2 endpoints for "FSM\_ADMIN" role
