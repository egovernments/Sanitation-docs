# FSM Registry

From the FSM card in the home screen, there is a link to the "FSM Registry". FSM admins have access to manage the FSM Registry.

## FSM Registry

* The FSM Registry is multi-tabbed search screen.
* Using the FSM Registry, FSM admins can manage vehicles, vendors, and sanitation workers in the system.
* There are three tabs available, that is, Vendor, Vehicle, Sanitation Worker.
* Vendor and vehicle were already there in FSM 1.3. The Sanitation Worker tab have now been added.

<div data-full-width="true">

<figure><img src="../../../../.gitbook/assets/image (173).png" alt=""><figcaption><p>FSM Registry</p></figcaption></figure>

</div>

#### Sanitation Worker Tab

* This tab shows a list of sanitation workers in the system.
* Admins can search for sanitation workers with the sanitation worker ID, name, and mobile number.
* Clicking on a particular ID takes the user to the [sanitation worker details page](sanitation-worker-details.md).
* Admins can disable/enable sanitation workers.
* There is a vendor dropdown available to each sanitation worker which shows a list of vendors that they can be tagged to. An admin can tag a sanitation worker to a vendor using that dropdown.
* Vendors are listed based on agency type. Currently, there are two types of agency: ULB and private vendor.
* If a sanitation worker is employed by the ULB, then the dropdown will show vendors whose agency type is ULB, and likewise for private vendors.
* The employer selection of a sanitation worker can be done while [creating a sanitation worker](create-sanitation-worker.md).
* We are using the individual registry to create, update, and disable sanitation workers.
* If an admin disables a sanitation worker already tagged to a vendor, then that vendor tagging is also disabled. This implies that the if an admin enables that user, we need to tag the vendor again.
* There is an 'Add' option at the top right of this screen using which admins can create vehicle, vendor, and sanitation worker.

> Note: There is a SANITATION\_WORKER role in the system. All sanitation workers created through the system will have this role.

## API Details

#### Individual Search

* We will hit hit the individual search API to get a list of sanitation workers using the SANITATION\_WORKER system role.
* The curl is given below:

```json
curl 'https://unified-dev.digit.org/individual/v1/_search?tenantId=pg.citya&limit=10&offset=0&sortBy=createdTime&sortOrder=DESC&_=1702466726727' \
  -H 'authority: unified-dev.digit.org' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9' \
  -H 'content-type: application/json;charset=UTF-8' \
  -H 'origin: https://unified-dev.digit.org' \
  -H 'referer: https://unified-dev.digit.org/sanitation-ui/employee/fsm/registry?selectedTabs=WORKER' \
  -H 'sec-ch-ua: "Not_A Brand";v="8", "Chromium";v="120", "Google Chrome";v="120"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "Windows"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-origin' \
  -H 'user-agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36' \
  --data-raw '{"Individual":{"roleCodes":["SANITATION_WORKER"],"tenantId":"pg.citya"},"RequestInfo":{"apiId":"Rainmaker","authToken":"06170439-7751-41d9-8043-04ede25e9499","userInfo":{"id":927,"uuid":"49341961-f413-4ae1-b7f8-92a8d9136f38","userName":"ADMIN","name":"Plant operator","mobileNumber":"8282828121","emailId":null,"locale":null,"type":"EMPLOYEE","roles":[{"name":"FSM Administrator","code":"FSM_ADMIN","tenantId":"pg.citya"},{"name":"FSM Employee Application Viewer","code":"FSM_VIEW_EMP","tenantId":"pg.citya"}],"active":true,"tenantId":"pg.citya","permanentCity":null},"msgId":"1702466726727|en_IN","plainAccessRequest":{}}}' \
  --compressed
```

#### Vendor Search

* We will hit the "vendor/v1/\_search" endpoint to get a list of vendors.
* The curl is given below:

```json
curl 'https://unified-dev.digit.org/vendor/v1/_search?tenantId=pg.citya&vehicleIds=&driverIds=&status=ACTIVE' \
  -H 'authority: unified-dev.digit.org' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9' \
  -H 'content-type: application/json;charset=UTF-8' \
  -H 'origin: https://unified-dev.digit.org' \
  -H 'referer: https://unified-dev.digit.org/sanitation-ui/employee/fsm/registry?selectedTabs=WORKER' \
  -H 'sec-ch-ua: "Not_A Brand";v="8", "Chromium";v="120", "Google Chrome";v="120"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "Windows"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-origin' \
  -H 'user-agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36' \
  --data-raw '{"RequestInfo":{"apiId":"Rainmaker","authToken":"06170439-7751-41d9-8043-04ede25e9499","userInfo":{"id":927,"uuid":"49341961-f413-4ae1-b7f8-92a8d9136f38","userName":"ADMIN","name":"Plant operator","mobileNumber":"8282828121","emailId":null,"locale":null,"type":"EMPLOYEE","roles":[{"name":"FSM Administrator","code":"FSM_ADMIN","tenantId":"pg.citya"},{"name":"FSM Employee Application Viewer","code":"FSM_VIEW_EMP","tenantId":"pg.citya"}],"active":true,"tenantId":"pg.citya","permanentCity":null},"msgId":"1702466726728|en_IN","plainAccessRequest":{}}}' \
  --compressed
```

#### Vendor Update

* We will hit the "/vendor/v1/\_update" to update tagging of sanitation workers to vendors.
* The curl is given below:

```json
curl 'https://unified-dev.digit.org/vendor/v1/_update?tenantId=pg.citya' \
  -H 'authority: unified-dev.digit.org' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9' \
  -H 'content-type: application/json;charset=UTF-8' \
  -H 'origin: https://unified-dev.digit.org' \
  -H 'referer: https://unified-dev.digit.org/sanitation-ui/employee/fsm/registry?selectedTabs=WORKER' \
  -H 'sec-ch-ua: "Not_A Brand";v="8", "Chromium";v="120", "Google Chrome";v="120"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "Windows"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-origin' \
  -H 'user-agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36' \
  --data-raw '{"vendor":{"id":"da5dae4c-95d7-43b6-a92f-e504d6000ef8","tenantId":"pg.citya","name":"djhdjkdhsjkh","address":{"tenantId":"pg.citya","doorNo":"","plotNo":"","id":"7132305a-ecd1-4f5e-af02-9894103a3742","landmark":"","city":"CityA","district":"CityA","region":"CityA","state":null,"country":"in","pincode":"","additionalDetails":"{\"description\": \"\"}","buildingName":"","street":"","locality":{"code":"SUN01","name":"Ajit Nagar - Area1","label":"Locality","latitude":"31.63089","longitude":"74.871552","children":[],"materializedPath":null},"geoLocation":null,"auditDetails":null},"owner":{"id":933,"uuid":"5b610239-fa1c-4538-b771-90cf255304b3","userName":"7787678673","password":null,"salutation":null,"name":"djhdjkdhsjkh","gender":"MALE","mobileNumber":"7787678673","emailId":"abc@egov.com","altContactNumber":null,"pan":null,"aadhaarNumber":null,"permanentAddress":null,"permanentCity":null,"permanentPinCode":null,"correspondenceCity":null,"correspondencePinCode":null,"correspondenceAddress":null,"active":true,"dob":0,"pwdExpiryDate":1710525714000,"locale":null,"type":"CITIZEN","signature":null,"accountLocked":false,"roles":[{"id":null,"name":"FSM Desluding Operator","code":"FSM_DSO","tenantId":"pg"},{"id":null,"name":"Citizen","code":"CITIZEN","tenantId":"pg"}],"fatherOrHusbandName":"djhdjkdhsjkh","relationship":"OTHER","bloodGroup":null,"identificationMark":null,"photo":null,"createdBy":"927","createdDate":1702393314000,"lastModifiedBy":"927","lastModifiedDate":1702481871000,"otpReference":null,"tenantId":"pg"},"vehicles":null,"drivers":null,"workers":[{"id":"59090353-59f6-4242-86ea-bbd92ecbe674","tenantId":"pg.citya","vendorId":"da5dae4c-95d7-43b6-a92f-e504d6000ef8","individualId":"1e5ad42e-2734-48fc-b934-fc32ef5058a6","additionalDetails":null,"auditDetails":{"createdBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","lastModifiedBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","createdTime":1702373514847,"lastModifiedTime":1702462026145},"vendorWorkerStatus":"ACTIVE"},{"id":"1e19a4f0-3ead-4985-bb59-aa4b57df6af2","tenantId":"pg.citya","vendorId":"da5dae4c-95d7-43b6-a92f-e504d6000ef8","individualId":"c050f0e5-d0a0-4f2a-83c0-63876827d6e1","additionalDetails":null,"auditDetails":{"createdBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","lastModifiedBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","createdTime":1702373514847,"lastModifiedTime":1702462071879},"vendorWorkerStatus":"ACTIVE"},{"id":"acf5a060-08db-4173-9232-c923653a57e4","tenantId":"pg.citya","vendorId":"da5dae4c-95d7-43b6-a92f-e504d6000ef8","individualId":"02bc1a5b-fed9-4176-bada-974aeeb8e613","additionalDetails":null,"auditDetails":{"createdBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","lastModifiedBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","createdTime":1702373514847,"lastModifiedTime":1702457057286},"vendorWorkerStatus":"INACTIVE"},{"id":"0a79d0d1-ac14-4ed4-a6cc-7971a29043e2","tenantId":"pg.citya","vendorId":"da5dae4c-95d7-43b6-a92f-e504d6000ef8","individualId":"f6f99ec9-9fcd-489c-8f66-58a4a63432b3","additionalDetails":null,"auditDetails":{"createdBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","lastModifiedBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","createdTime":1702373514847,"lastModifiedTime":1702459924693},"vendorWorkerStatus":"ACTIVE"},{"id":"39cc81f9-58e7-4912-9743-81f51ba03cd5","tenantId":"pg.citya","vendorId":"da5dae4c-95d7-43b6-a92f-e504d6000ef8","individualId":"8215eb13-f247-4782-9acd-665214d24a98","additionalDetails":null,"auditDetails":{"createdBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","lastModifiedBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","createdTime":1702373514847,"lastModifiedTime":1702461623872},"vendorWorkerStatus":"ACTIVE"}],"additionalDetails":{"description":""},"source":"WhatsApp","description":null,"ownerId":"5b610239-fa1c-4538-b771-90cf255304b3","agencyType":"ULB","paymentPreference":"post-service","status":"ACTIVE","auditDetails":{"createdBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","lastModifiedBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","createdTime":1702373514847,"lastModifiedTime":1702462071879}},"RequestInfo":{"apiId":"Rainmaker","authToken":"06170439-7751-41d9-8043-04ede25e9499","userInfo":{"id":927,"uuid":"49341961-f413-4ae1-b7f8-92a8d9136f38","userName":"ADMIN","name":"Plant operator","mobileNumber":"8282828121","emailId":null,"locale":null,"type":"EMPLOYEE","roles":[{"name":"FSM Administrator","code":"FSM_ADMIN","tenantId":"pg.citya"},{"name":"FSM Employee Application Viewer","code":"FSM_VIEW_EMP","tenantId":"pg.citya"}],"active":true,"tenantId":"pg.citya","permanentCity":null},"msgId":"1702466976575|en_IN","plainAccessRequest":{}}}' \
  --compressed
```

#### Individual Update

* We will utilise the individual update API for disabling/enabling sanitation workers.
* The curl is given below:

```json
curl 'https://unified-dev.digit.org/individual/v1/_update' \
  -H 'authority: unified-dev.digit.org' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9' \
  -H 'content-type: application/json;charset=UTF-8' \
  -H 'origin: https://unified-dev.digit.org' \
  -H 'referer: https://unified-dev.digit.org/sanitation-ui/employee/fsm/registry?selectedTabs=WORKER' \
  -H 'sec-ch-ua: "Not_A Brand";v="8", "Chromium";v="120", "Google Chrome";v="120"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "Windows"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-origin' \
  -H 'user-agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36' \
  --data-raw '{"tenantId":"pg.citya","Individual":{"id":"02bc1a5b-fed9-4176-bada-974aeeb8e613","individualId":"IND-2023-12-11-011010","tenantId":"pg.citya","clientReferenceId":null,"userId":null,"userUuid":null,"name":{"givenName":"sdjhsdhsdkjhs","familyName":null,"otherNames":null},"dateOfBirth":"01/01/1970","gender":"MALE","bloodGroup":null,"mobileNumber":"7897897899","altContactNumber":null,"email":null,"address":[{"id":"d2a6e81d-c3ce-4608-af11-5b0d0ca0aa0d","clientReferenceId":null,"individualId":"02bc1a5b-fed9-4176-bada-974aeeb8e613","tenantId":"pg.citya","doorNo":null,"latitude":0,"longitude":0,"locationAccuracy":0,"type":"PERMANENT","addressLine1":null,"addressLine2":null,"landmark":null,"city":"pg.citya","pincode":null,"buildingName":null,"street":null,"locality":{"code":"SUN01","name":null,"label":null,"latitude":null,"longitude":null,"children":null,"materializedPath":null},"ward":null,"isDeleted":false,"auditDetails":{"createdBy":"4a747fc5-6a8c-4645-8748-fec35f1b9e17","lastModifiedBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","createdTime":1702288646617,"lastModifiedTime":1702459735736}}],"fatherName":null,"husbandName":null,"relationship":null,"identifiers":[{"id":"c29c1d4d-a652-41ed-919e-690ebc26641a","clientReferenceId":null,"individualId":"02bc1a5b-fed9-4176-bada-974aeeb8e613","identifierType":"SYSTEM_GENERATED","identifierId":"********************************e613","isDeleted":false,"auditDetails":{"createdBy":"4a747fc5-6a8c-4645-8748-fec35f1b9e17","lastModifiedBy":"4a747fc5-6a8c-4645-8748-fec35f1b9e17","createdTime":1702288646617,"lastModifiedTime":1702288646617}}],"skills":[{"id":"19a53767-cf30-40ef-b319-448a71543d6b","clientReferenceId":null,"individualId":"02bc1a5b-fed9-4176-bada-974aeeb8e613","type":"DRIVING","level":"UNSKILLED","experience":null,"isDeleted":false,"auditDetails":{"createdBy":"4a747fc5-6a8c-4645-8748-fec35f1b9e17","lastModifiedBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","createdTime":1702288646617,"lastModifiedTime":1702381056019}},{"id":"d033165f-e71a-492d-9047-a0f7a8100bf9","clientReferenceId":null,"individualId":"02bc1a5b-fed9-4176-bada-974aeeb8e613","type":"Driving","level":"UNSKILLED","experience":null,"isDeleted":false,"auditDetails":{"createdBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","lastModifiedBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","createdTime":1702459735089,"lastModifiedTime":1702459735089}},{"id":"83d3c583-4195-49d9-8447-3fdea59a3f47","clientReferenceId":null,"individualId":"02bc1a5b-fed9-4176-bada-974aeeb8e613","type":"Lab Operator","level":"UNSKILLED","experience":null,"isDeleted":false,"auditDetails":{"createdBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","lastModifiedBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","createdTime":1702459735089,"lastModifiedTime":1702459735089}},{"id":"db0d86de-5f6e-42b0-8978-1953bd4a71a4","clientReferenceId":null,"individualId":"02bc1a5b-fed9-4176-bada-974aeeb8e613","type":"Driving","level":"UNSKILLED","experience":null,"isDeleted":false,"auditDetails":{"createdBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","lastModifiedBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","createdTime":1702459735737,"lastModifiedTime":1702459735737}},{"id":"8c623d37-5a83-431a-8c09-5cd6a3bc54c2","clientReferenceId":null,"individualId":"02bc1a5b-fed9-4176-bada-974aeeb8e613","type":"Lab Operator","level":"UNSKILLED","experience":null,"isDeleted":false,"auditDetails":{"createdBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","lastModifiedBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","createdTime":1702459735737,"lastModifiedTime":1702459735737}}],"photo":null,"additionalFields":{"schema":null,"version":null,"fields":[{"key":"FUNCTIONAL_ROLE_1","value":"SANITATION_HELPER"},{"key":"EMPLOYMENT_TYPE_1","value":"FIXED"},{"key":"FUNCTIONAL_ROLE_COUNT","value":"01"},{"key":"EMPLOYER","value":"ULB"}]},"isDeleted":false,"rowVersion":11,"auditDetails":{"createdBy":"4a747fc5-6a8c-4645-8748-fec35f1b9e17","lastModifiedBy":"49341961-f413-4ae1-b7f8-92a8d9136f38","createdTime":1702288646617,"lastModifiedTime":1702459735737},"clientAuditDetails":{"createdBy":null,"lastModifiedBy":null,"createdTime":0,"lastModifiedTime":0},"isSystemUser":true,"isSystemUserActive":false,"userDetails":{"username":"7897897899","password":null,"tenantId":"pg.citya","roles":[{"name":null,"code":"SANITATION_HELPER","description":null,"tenantId":"pg.citya"},{"name":null,"code":"SANITATION_WORKER","description":null,"tenantId":"pg.citya"},{"name":null,"code":"CITIZEN","description":null,"tenantId":"pg.citya"}],"type":"CITIZEN"}},"RequestInfo":{"apiId":"Rainmaker","authToken":"06170439-7751-41d9-8043-04ede25e9499","userInfo":{"id":927,"uuid":"49341961-f413-4ae1-b7f8-92a8d9136f38","userName":"ADMIN","name":"Plant operator","mobileNumber":"8282828121","emailId":null,"locale":null,"type":"EMPLOYEE","roles":[{"name":"FSM Administrator","code":"FSM_ADMIN","tenantId":"pg.citya"},{"name":"FSM Employee Application Viewer","code":"FSM_VIEW_EMP","tenantId":"pg.citya"}],"active":true,"tenantId":"pg.citya","permanentCity":null},"msgId":"1702467231568|en_IN","plainAccessRequest":{}}}' \
  --compressed
```

## Role-Action Mapping

* Role-action mapping is done for the above mentioned API endpoints for FSM admin users with the following role code:

```
FSM_ADMIN
```
