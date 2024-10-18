# Assign Sanitation Workers to FSM Applications

In FSM 1.3 EDITOR users could take workflow actions and assign drivers to FSM Applications now we have changed that assignment. Now EDITOR users can assign a driver and multiple helpers to an FSM Application. And both driver and helper are Sanitation workers now.

EDITOR User role code:

```json
FSM_EDITOR_EMP
```

### Assigning Sanitation workers to FSM Applications

* Login with EDITOR user and go to FSM Inbox
* From Inbox choose any application whose status is pending for DSO assignment
* Go to the application details page from inbox
* From the Action bar options click on "Assign Vehicle and Sanitation Workers"
* A Popup window will open which looks like the following
*

    <figure><img src="../../../../.gitbook/assets/image (178).png" alt=""><figcaption></figcaption></figure>


* We have two new options here, Assign Driver and Assign Sanitation Worker
* Assign Driver is single select and mandatory
* Assign Sanitation worker is multi-select and we can assign multiple Sanitation workers. Assigning worker is non mandatory though
* Both these dropdowns are searchable i.e., EDITOR can search by name and Sanitation worker ID&#x20;
* These dropdowns are populated based on the vendor that is tagged to the current FSM Application.
* User can click on Assign to take this action. A toast message is displayed showing the update is successful.
* After this action, added Sanitation workers are displayed on the Application Details screen under DSO Details Section
*

    <figure><img src="../../../../.gitbook/assets/image (179).png" alt=""><figcaption><p>FSM Application Details</p></figcaption></figure>



### API Details

#### FSM Search

* To fetch FSM application details we are hitting this endpoint "/fsm/v1/\_search"
* Refer the below curl:

```json
curl 'https://unified-dev.digit.org/fsm/v1/_search?tenantId=pg.citya&applicationNos=1013-FSM-2023-12-13-000381&_=1702476865870' \
  -H 'authority: unified-dev.digit.org' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9' \
  -H 'content-type: application/json;charset=UTF-8' \
  -H 'origin: https://unified-dev.digit.org' \
  -H 'referer: https://unified-dev.digit.org/sanitation-ui/employee/fsm/application-details/1013-FSM-2023-12-13-000381' \
  -H 'sec-ch-ua: "Not_A Brand";v="8", "Chromium";v="120", "Google Chrome";v="120"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "Windows"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-origin' \
  -H 'user-agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36' \
  --data-raw '{"RequestInfo":{"apiId":"Rainmaker","authToken":"f8eee39f-1194-4d39-85de-12dc9c572a7c","msgId":"1702476865870|en_IN","plainAccessRequest":{}}}' \
  --compressed
```



#### FSM Update

* To update FSM application we are hitting this endpoint "/fsm/v1/\_update"
* Refer to the below curl:

```json
curl 'https://unified-dev.digit.org/fsm/v1/_update?tenantId=pg.citya&_=1702476876985' \
  -H 'authority: unified-dev.digit.org' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9' \
  -H 'content-type: application/json;charset=UTF-8' \
  -H 'origin: https://unified-dev.digit.org' \
  -H 'referer: https://unified-dev.digit.org/sanitation-ui/employee/fsm/application-details/1013-FSM-2023-12-13-000381' \
  -H 'sec-ch-ua: "Not_A Brand";v="8", "Chromium";v="120", "Google Chrome";v="120"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "Windows"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-origin' \
  -H 'user-agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36' \
  --data-raw '{"fsm":{"citizen":{"id":960,"uuid":"d75d542f-a3bb-42c3-884a-d7fb5e6f14b3","userName":"d90dffe9-05b2-42cd-b87f-9756b0782dec","name":"Janu","password":null,"mobileNumber":"9035169720","tenantId":"pg","salutation":null,"emailId":null,"altContactNumber":null,"pan":null,"aadhaarNumber":null,"permanentAddress":null,"permanentCity":null,"permanentPinCode":null,"correspondenceCity":null,"correspondencePinCode":null,"active":true,"dob":null,"pwdExpiryDate":1710251842000,"locale":null,"type":"CITIZEN","signature":null,"accountLocked":false,"roles":[{"id":null,"name":"Citizen","code":"CITIZEN","tenantId":"pg"}],"bloodGroup":null,"identificationMark":null,"photo":null,"createdBy":"925","createdDate":1702475842000,"lastModifiedBy":"925","lastModifiedDate":1702475842000,"otpReference":null,"gender":null},"id":"f25e914d-e14e-4a9e-97d1-dc2cc51611f3","tenantId":"pg.citya","applicationNo":"1013-FSM-2023-12-13-000381","description":null,"accountId":"d75d542f-a3bb-42c3-884a-d7fb5e6f14b3","additionalDetails":{"tripAmount":750},"applicationStatus":"DSO_INPROGRESS","source":"COUNTER","sanitationtype":null,"propertyUsage":"RESIDENTIAL.ROW_HOUSES","vehicleType":null,"noOfTrips":1,"vehicleCapacity":"1000","status":null,"vehicleId":null,"driverId":"3d916d24-5756-4d01-b547-b4f2feac4366","vehicle":null,"dsoId":"e427ddf2-7c49-47f1-ba0f-4418bb10f0b7","dso":null,"possibleServiceDate":1702425600000,"pitDetail":{"type":null,"id":"ca0cb638-eaec-4b7a-8f5d-5924c4a4bc4a","tenantId":"pg.citya","height":0,"length":0,"width":0,"diameter":0,"distanceFromRoad":0,"auditDetails":{"createdBy":"7e1c6207-49e9-41b4-a965-dea0cdeb677c","lastModifiedBy":"12c0c924-ec4f-41e8-aa41-92c00226ce85","createdTime":1702475842827,"lastModifiedTime":1702475982894},"additionalDetails":null},"address":{"tenantId":"pg.citya","doorNo":null,"plotNo":null,"id":"f5c6c3d9-8634-46e2-b662-22efc130ea03","landmark":null,"city":"CityA","district":null,"region":null,"state":null,"country":null,"pincode":"143001","additionalDetails":null,"auditDetails":{"createdBy":"7e1c6207-49e9-41b4-a965-dea0cdeb677c","lastModifiedBy":"12c0c924-ec4f-41e8-aa41-92c00226ce85","createdTime":1702475842827,"lastModifiedTime":1702475982894},"buildingName":null,"street":null,"slumName":null,"locality":{"code":"SUN03","name":"Bharath Colony","label":"Locality","latitude":null,"longitude":null,"children":[],"materializedPath":null},"geoLocation":{"id":"66d6755a-7ca3-41ab-8a76-89ebbb1166b4","latitude":20.2099797,"longitude":85.6973022,"additionalDetails":null}},"auditDetails":{"createdBy":"7e1c6207-49e9-41b4-a965-dea0cdeb677c","lastModifiedBy":"12c0c924-ec4f-41e8-aa41-92c00226ce85","createdTime":1702475842827,"lastModifiedTime":1702475982894},"wasteCollected":null,"completedOn":0,"advanceAmount":0,"applicationType":"Adhoc Service","oldApplicationNo":null,"paymentPreference":null,"processInstance":null},"workflow":{"action":"REASSING","comments":"VEHICLE_REPAIR"},"RequestInfo":{"apiId":"Rainmaker","authToken":"f8eee39f-1194-4d39-85de-12dc9c572a7c","userInfo":{"id":926,"uuid":"12c0c924-ec4f-41e8-aa41-92c00226ce85","userName":"EDITOR","name":"Plant operator","mobileNumber":"8282828121","emailId":null,"locale":null,"type":"EMPLOYEE","roles":[{"name":"FSM Employee Application Editor","code":"FSM_EDITOR_EMP","tenantId":"pg.citya"},{"name":"FSM Employee Application Viewer","code":"FSM_VIEW_EMP","tenantId":"pg.citya"}],"active":true,"tenantId":"pg.citya","permanentCity":null},"msgId":"1702476876985|en_IN","plainAccessRequest":{}}}' \
  --compressed
```

#### Vendor Search

* To get a particular vendor data tagged to the current application we are hitting this endpoint "/vendor/v1/\_search"
* Refer to the below curl&#x20;

```
curl 'https://unified-dev.digit.org/vendor/v1/_search?tenantId=pg.citya&ids=e427ddf2-7c49-47f1-ba0f-4418bb10f0b7' \
  -H 'authority: unified-dev.digit.org' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9' \
  -H 'content-type: application/json;charset=UTF-8' \
  -H 'origin: https://unified-dev.digit.org' \
  -H 'referer: https://unified-dev.digit.org/sanitation-ui/employee/fsm/application-details/1013-FSM-2023-12-13-000381' \
  -H 'sec-ch-ua: "Not_A Brand";v="8", "Chromium";v="120", "Google Chrome";v="120"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "Windows"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-origin' \
  -H 'user-agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36' \
  --data-raw '{"RequestInfo":{"apiId":"Rainmaker","authToken":"f8eee39f-1194-4d39-85de-12dc9c572a7c","userInfo":{"id":926,"uuid":"12c0c924-ec4f-41e8-aa41-92c00226ce85","userName":"EDITOR","name":"Plant operator","mobileNumber":"8282828121","emailId":null,"locale":null,"type":"EMPLOYEE","roles":[{"name":"FSM Employee Application Editor","code":"FSM_EDITOR_EMP","tenantId":"pg.citya"},{"name":"FSM Employee Application Viewer","code":"FSM_VIEW_EMP","tenantId":"pg.citya"}],"active":true,"tenantId":"pg.citya","permanentCity":null},"msgId":"1702476878085|en_IN","plainAccessRequest":{}}}' \
  --compressed
```

### Role Action Mapping

Role action mapping for the above three endpoints is done for this role

```
FSM_EDITOR_EMP
```
