---
description: Details for registering new vendors
---

# FSM Vendor Registry

## Overview <a href="#overview" id="overview"></a>

The vendor registry is a system that enables urban local body (ULB) employees to create and search a vendor, that is, the desludging operator (DSO) and driver entities with appropriate vehicle entities for the FSM application. This document contains the details about how to set up the vendor and describe the functionalities provided.



As part of the worker welfare v1.0, a new worker registry concept is being introduced. The creation of a worker, updation of details, searching and tagging a worker for different operations on sanitation programmes will be covered. We will leverage the Individual Registry for storing and querying details about a worker.&#x20;

The individual service is an enhanced version of the user service that houses data about individuals. The individual service is being re-used from [DIGIT Health](https://health.digit.org/).

## Pre-requisites <a href="#pre-requisites" id="pre-requisites"></a>

Before you proceed with the configuration, make sure the following pre-requisites are met:

* Java 8
* Kafka server is up and running.
* egov-persister service is running and has a vendor-persister config path added in it.
* PSQL server is running and database is created to store FSM application data.
* Following services should be up and running:

&#x20;      \- egov-mdms-service

&#x20;      \- egov-user-service

&#x20;       \- boundary-service

&#x20;       \- vehicle-service

## Key Functionalities <a href="#key-functionalities" id="key-functionalities"></a>

**EXISTING**

1. Added payment payment preference and agency attributes for DSO.
2. Added gender attribute in the create and update APIs for vendor.
3. Updated the vendor search API to add vehicleCapacity in the search parameter to search all vendors matching the vehicle capacity specified in the search parameter.
4. Introduced the vendor tab.
5. Option to add/remove/update vendors individually.
6. User can add vehicle and ~~driver~~.
7. Search for the list of all vehicles not associated with any vendors.&#x20;
8. Users can enable or disable the vendor.
9. Part Search for FSM Registry Vendor Tab by vendor name&#x20;
10. Updating  vendor information, such as Gender, Mobile number, and Locality/Mohalla in FSM Registry.

**ENHANCEMENT**

**Changes from Version 1.3.1 is 1.4.0**

1. Change from driver concept to worker.
2. Deprecation of the driver table.
3. Backward compatibility for existing drivers (converting a driver user into an individual and mapping/backfilling to vendors).
4. Introducing worker vendor mapping.
5. Creation of workers directly using Individual registry APIs.

## Kafka Topic Details

| Description                                          | Topic                                |
| ---------------------------------------------------- | ------------------------------------ |
| Save vendor topic                                    | save-vendor-application              |
| Update vendor topic                                  | update-vendor-application            |
| Save driver topic                                    | save-driver-application              |
| Update driver topic                                  | update-driver-application            |
| Update vendor-driver and vendor-vehicle relationship | save-vendordrivervehicle-application |

## Data Setup

The DSO for the FSM system is a vendor. For every city/ULB, a DSO should be created with the representative details as owner, associated vehicles and drivers.

Sample Curl

```
curl 'https://dev.digit.org/vendor/driver/v1/_update?tenantId=pb.amritsar' \
  -H 'authority: dev.digit.org' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-GB,en-US;q=0.9,en;q=0.8' \
  -H 'content-type: application/json;charset=UTF-8' \
  -H 'cookie: _ga=GA1.2.1852108775.1653914860; intercom-id-xp1951jv=17aa7431-3dc0-4524-9956-a22bb67a637f; __cuid=858e6f9f233c4b2c804d3f81109b48ac; amp_fef1e8=7faa94f4-6926-4f98-ac07-be2414f977c6R...1gkkb64lb.1gkkb6kvh.7p.a.83' \
  -H 'origin: https://dev.digit.org' \
  -H 'referer: https://dev.digit.org/digit-ui/employee/fsm/registry/modify-driver/b967d3ab-4ce4-41eb-931e-343734a673a0' \
  -H 'sec-ch-ua: "Not?A_Brand";v="8", "Chromium";v="108", "Google Chrome";v="108"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "Linux"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-origin' \
  -H 'user-agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/108.0.0.0 Safari/537.36' \
  --data-raw '{"driver":{"id":"b967d3ab-4ce4-41eb-931e-343734a673a0","tenantId":"pb.amritsar","name":"Vinot","owner":{"id":23597,"uuid":"1eaeae8e-e2cb-4736-b0da-2469441c7136","userName":"9876543210","password":null,"salutation":null,"name":"Vinot","gender":"MALE","mobileNumber":"9876543210","emailId":"abc@egov.com","altContactNumber":null,"pan":"","aadhaarNumber":null,"permanentAddress":"xxccc","permanentCity":null,"permanentPinCode":null,"correspondenceCity":null,"correspondencePinCode":null,"correspondenceAddress":"xxccc","active":true,"dob":1575504000000,"pwdExpiryDate":1542493260000,"locale":null,"type":"CITIZEN","signature":null,"accountLocked":false,"roles":[{"id":null,"name":"Citizen","code":"CITIZEN","tenantId":"pb"},{"id":null,"name":"FSM Desluding Operator","code":"FSM_DSO","tenantId":"pb"},{"id":null,"name":"FSM Driver","code":"FSM_DRIVER","tenantId":"pb"}],"fatherOrHusbandName":null,"relationship":"OTHER","bloodGroup":null,"identificationMark":null,"photo":null,"createdBy":"23299","createdDate":1533648094000,"lastModifiedBy":"28452","lastModifiedDate":1655290352000,"otpReference":null,"tenantId":"pb"},"ownerId":"1eaeae8e-e2cb-4736-b0da-2469441c7136","description":null,"licenseNumber":"34567899990","status":"ACTIVE","auditDetails":{"createdBy":"5674253d-9c2a-4d47-88ae-450f3fbbcad2","lastModifiedBy":"5674253d-9c2a-4d47-88ae-450f3fbbcad2","createdTime":1671536878567,"lastModifiedTime":1671536878567},"vendorDriverStatus":null},"RequestInfo":{"apiId":"Rainmaker","authToken":"5aac2f5f-086b-4770-a832-023641a62650","userInfo":{"id":28452,"uuid":"5674253d-9c2a-4d47-88ae-450f3fbbcad2","userName":"BPAFieldInspector","name":"lakshmi","mobileNumber":"8656565343","emailId":null,"locale":null,"type":"EMPLOYEE","roles":[{"name":"FSM Administrator","code":"FSM_ADMIN","tenantId":"pb.amritsar"},{"name":"BPA Services Approver","code":"BPA_APPROVER","tenantId":"pb.amritsar"},{"name":"Employee","code":"EMPLOYEE","tenantId":"pb.amritsar"},{"name":"FSM Employee Report Viewer","code":"FSM_REPORT_VIEWER","tenantId":"pb.amritsar"},{"name":"BPA Services verifier","code":"BPA_VERIFIER","tenantId":"pb.amritsar"},{"name":"BPA Field Inspector","code":"BPA_FIELD_INSPECTOR","tenantId":"pb.amritsar"},{"name":"BPAREG doc verifier","code":"BPAREG_DOC_VERIFIER","tenantId":"pb.amritsar"}],"active":true,"tenantId":"pb.amritsar","permanentCity":null},"msgId":"1671537564062|en_IN","plainAccessRequest":{}}}' \
  --compressed
```

## Integration <a href="#integration" id="integration"></a>

### Integration Scope <a href="#integration-scope" id="integration-scope"></a>

Any system or DIGIT module can be integrated with the vendor service. It helps to manage the vendor with the vehicles, drivers, and owner for representatives, and login for the representative/owner to login into the system to carry our role-specific operations.

### Integration Benefits <a href="#integration-benefits" id="integration-benefits"></a>

* Validation of DSO/vendor availability.
* Fetch the vehicle assigned to the DSO.
* Fetch the drivers assigned to the DSO.

### Steps to Integration <a href="#steps-to-integration" id="steps-to-integration"></a>

* FSM to call vendor/v1/\_search to fetch the DSOs.
* FSM can call vendor/v1/\_search to fetch the DSO’s and the respective vehicles and drivers.

### Interaction Diagrams <a href="#interaction-diagram" id="interaction-diagram"></a>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-03-28 at 3.29.24 PM (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-03-28 at 3.31.24 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-03-28 at 3.33.35 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-03-28 at 3.34.23 PM.png" alt=""><figcaption></figcaption></figure>

#### **Create Worker**

<figure><img src="../../../../../.gitbook/assets/spaces_LpfYJCGZoBEmcFf9yWTh_uploads_YROtFEzhs9iaqS0hBABF_Screenshot 2023-09-22 at 9.webp" alt=""><figcaption></figcaption></figure>

#### **Update Vendor**

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-09-22 at 9.48.03 AM.png" alt=""><figcaption></figcaption></figure>

## Architecture Diagram

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-09-22 at 10.30.37 AM.png" alt=""><figcaption></figcaption></figure>

## Reference Docs <a href="#reference-docs" id="reference-docs"></a>

### Doc Links <a href="#doc-links" id="doc-links"></a>

| Workflow Technical Document         | [Workflow Service](broken-reference)                                                                                                                                                                                                     |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| User technical document             | [User Service  ](broken-reference)                                                                                                                                                                                                       |
| MDMS technical document             | NEEDS TO BE UPDATED                                                                                                                                                                                                                      |
| IDGen technical document            | NEEDS TO BE UPDATED                                                                                                                                                                                                                      |
| Localisation technical document     | NEEDS TO BE UPDATED                                                                                                                                                                                                                      |
| Persister technical document        | NEEDS TO BE UPDATED                                                                                                                                                                                                                      |
| SMS notification technical document | NEEDS TO BE UPDATED                                                                                                                                                                                                                      |
| API contract                        | [Vendor\_Registration\_Contract.yaml](https://raw.githubusercontent.com/egovernments/SANITATION/sanitation\_v1.4\_api\_contracts/API-CONTRACTS/fsm/Vendor\_Registration\_Contract.yaml?token=GHSAT0AAAAAACGUKWUFSEN4KJFWGCJW6P5OZINGSVA) |
| Postman scripts                     | [Postman Collection](https://api.postman.com/collections/13428435-67194a8e-f288-473e-b7cc-8f26fd964ace?access\_key=PMAT-01HK7FAQ5CJ5J1QPAH2ZJRC7H8)                                                                                      |

### API List <a href="#api-list" id="api-list"></a>

| Title                      | Link                                                                                                                                                                       | Deprecation Status |
| -------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------ |
| /vendor/v1/\_create        | [Postman Collection for Vendor Service](https://api.postman.com/collections/13428435-67194a8e-f288-473e-b7cc-8f26fd964ace?access\_key=PMAT-01HK7FAQ5CJ5J1QPAH2ZJRC7H8)     | False              |
| /vendor/v1/\_search        | [Postman Collection for Vendor Service](https://api.postman.com/collections/13428435-67194a8e-f288-473e-b7cc-8f26fd964ace?access\_key=PMAT-01HK7FAQ5CJ5J1QPAH2ZJRC7H8)     | False              |
| /vendor/v1/\_plainsearch   | [Postman Collection for Vendor Service](https://api.postman.com/collections/13428435-67194a8e-f288-473e-b7cc-8f26fd964ace?access\_key=PMAT-01HK7FAQ5CJ5J1QPAH2ZJRC7H8)     | False              |
| /vendor/v1/\_update        | [Postman Collection for Vendor Service](https://api.postman.com/collections/13428435-67194a8e-f288-473e-b7cc-8f26fd964ace?access\_key=PMAT-01HK7FAQ5CJ5J1QPAH2ZJRC7H8)     | False              |
| /vendor/driver/v1/\_create | [Postman Collection for Vendor Service](https://api.postman.com/collections/13428435-67194a8e-f288-473e-b7cc-8f26fd964ace?access\_key=PMAT-01HK7FAQ5CJ5J1QPAH2ZJRC7H8)     | True               |
| /vendor/driver/v1/\_update | [Postman Collection for Vendor Service](https://api.postman.com/collections/13428435-67194a8e-f288-473e-b7cc-8f26fd964ace?access\_key=PMAT-01HK7FAQ5CJ5J1QPAH2ZJRC7H8)     | True               |
| /vendor/driver/v1/\_search | [Postman Collection for Vendor Service](https://api.postman.com/collections/13428435-67194a8e-f288-473e-b7cc-8f26fd964ace?access\_key=PMAT-01HK7FAQ5CJ5J1QPAH2ZJRC7H8)     | True               |
| /individual/v1/\_create    | [Postman Collection for Individual Service](https://api.postman.com/collections/13428435-ce63a6df-99dd-484c-98f3-71782d649b00?access\_key=PMAT-01HK7E6YS9A3VC6ZAFDPHJTVPC) | False              |
| /individual/v1/\_update    | [Postman Collection for Individual Service](https://api.postman.com/collections/13428435-ce63a6df-99dd-484c-98f3-71782d649b00?access\_key=PMAT-01HK7E6YS9A3VC6ZAFDPHJTVPC) | False              |
| /individual/v1/\_search    | [Postman Collection for Individual Service](https://api.postman.com/collections/13428435-ce63a6df-99dd-484c-98f3-71782d649b00?access\_key=PMAT-01HK7E6YS9A3VC6ZAFDPHJTVPC) | False              |
