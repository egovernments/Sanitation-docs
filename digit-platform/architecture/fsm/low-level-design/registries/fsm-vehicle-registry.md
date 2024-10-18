---
description: Configuration and setup details on registering vehicles in FSM module
---

# FSM Vehicle Registry

## Overview <a href="#overview" id="overview"></a>

Vehicle registry is a system that enables urban local body (ULB) employees to create and search vehicle entities, schedule vehicle trips for FSM application and track vehicle trips. This document contains the details about the new enhancements made to the vehicle service and how to set up the vehicle and describes the functionalities provided.

## Pre-requisites <a href="#pre-requisites" id="pre-requisites"></a>

Before you proceed with the configuration, make sure the following prerequisites are met:&#x20;

* Java 8
* Kafka server is up and running.
* egov-persister service is running and has vehicle-persister config path added in it.
* PSQL server is running and database is created to store FSM Application data.
* Following services should be up and running:

&#x20;     \- egov-perister

&#x20;     \- egov-mdms-service

&#x20;     \- egov-workflow-v2

&#x20;     \- egov-idgen

## Key Functionalities

**EXISTING**

1. DSO or ULB can create multiple vehicle trips based on the number of trips entered while submitting the FSM application.
2. FSTPO can decline the vehicle trip with appropriate reason.
3. Owner attribute has been added to the vehicle.
4. FSTPO Vehicle Log Inbox Enhancements to include Application No search filter so that FSTPO can view all the vehicle trips associated with the application.
5. FSPTO vehicle log API upgraded to show trip numbers in case of multi-trip application.
6. Introduced Vehicle Tab.
7. Option to add/remove/update vehicle individually.
8. Admin can enable or disable the vehicle.
9. Functionality to add/remove vehicles to vendor.

**ENHANCEMENT**

1. **Part Search:** The Vehicle tab now includes the ability to perform a part search by vehicle number. This means that users can enter a partial vehicle number and retrieve all relevant results that contain that specific portion. For example, if the vehicle number is "AA 77 JJ 3324", users can search for any part of the vehicle number, such as "AA", "77", or "JJ", and retrieve all relevant results that contain that specific portion.
2. **Updating Registry Information:** In the Vehicle Tab, the admin has the ability to update certain vehicle information, such as Owner name, Phone Number. Added a new column for gender , Dob and Email address which are updatable.

## Data Setup <a href="#data-setup" id="data-setup"></a>

#### Create Vehicle <a href="#create-vehicle" id="create-vehicle"></a>

Create a vehicle with one of the vehicle types available in the VehicleMakeModel MDMS.

**Sample Curl**

```
curl 'https://dev.digit.org/vehicle/v1/_create?tenantId=pb.amritsar' \
  -H 'authority: dev.digit.org' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-GB,en-US;q=0.9,en;q=0.8' \
  -H 'content-type: application/json;charset=UTF-8' \
  -H 'cookie: _ga=GA1.2.1852108775.1653914860; intercom-id-xp1951jv=17aa7431-3dc0-4524-9956-a22bb67a637f; __cuid=858e6f9f233c4b2c804d3f81109b48ac; amp_fef1e8=7faa94f4-6926-4f98-ac07-be2414f977c6R...1gkkb64lb.1gkkb6kvh.7p.a.83' \
  -H 'origin: https://dev.digit.org' \
  -H 'referer: https://dev.digit.org/digit-ui/employee/fsm/registry/new-vehicle' \
  -H 'sec-ch-ua: "Google Chrome";v="107", "Chromium";v="107", "Not=A?Brand";v="24"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "Linux"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-origin' \
  -H 'user-agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/107.0.0.0 Safari/537.36' \
  --data-raw '{"vehicle":{"tenantId":"pb.amritsar","registrationNumber":"AS 12 AS 1234","model":"MAHINDRA","type":"MAHINDRA.BOLERO_PICKUP","tankCapacity":"5000","suctionType":"SEWER_SUCTION_MACHINE","pollutionCertiValidTill":null,"InsuranceCertValidTill":null,"fitnessValidTill":null,"roadTaxPaidTill":null,"gpsEnabled":true,"source":"Municipal records","owner":{"tenantId":"pb","name":"raj","fatherOrHusbandName":"raj","relationship":"OTHER","gender":"OTHERS","dob":-19800000,"emailId":"abc@egov.com","correspondenceAddress":"","mobileNumber":"9876543210"},"additionalDetails":{"description":""}},"RequestInfo":{"apiId":"Rainmaker","authToken":"df28f073-4caf-456e-bd43-1943ce76548c","userInfo":{"id":28452,"uuid":"5674253d-9c2a-4d47-88ae-450f3fbbcad2","userName":"BPAFieldInspector","name":"lakshmi","mobileNumber":"8656565343","emailId":null,"locale":null,"type":"EMPLOYEE","roles":[{"name":"FSM Administrator","code":"FSM_ADMIN","tenantId":"pb.amritsar"},{"name":"BPA Services Approver","code":"BPA_APPROVER","tenantId":"pb.amritsar"},{"name":"Employee","code":"EMPLOYEE","tenantId":"pb.amritsar"},{"name":"FSM Employee Report Viewer","code":"FSM_REPORT_VIEWER","tenantId":"pb.amritsar"},{"name":"BPA Services verifier","code":"BPA_VERIFIER","tenantId":"pb.amritsar"},{"name":"BPA Field Inspector","code":"BPA_FIELD_INSPECTOR","tenantId":"pb.amritsar"},{"name":"BPAREG doc verifier","code":"BPAREG_DOC_VERIFIER","tenantId":"pb.amritsar"}],"active":true,"tenantId":"pb.amritsar","permanentCity":null},"msgId":"1671428547643|en_IN","plainAccessRequest":{}}}' \
  --compressed
```

## Integration <a href="#integration-scope" id="integration-scope"></a>

### Integration Scope <a href="#integration-scope" id="integration-scope"></a>

Integrated with the application through REST API to create, and search vehicles. For any module where the vehicle trip is required, one can integrate REST API trip/v1/create, update, and search.

### Integration Benefits <a href="#integration-benefits" id="integration-benefits"></a>

* Vehicle management would become easy.
* Trip management would become easy.

### Steps to Integration <a href="#steps-to-integration" id="steps-to-integration"></a>

* FSM application can vehicle/v1/\_search to validate the FSM vehicle assignment.
* FSM application call vehicle/trip/v1/\_create on assigning vehicle to the spplication.
* FSTP operators can mark the vehicleTrip as DISPOSED.

### Interaction Diagrams <a href="#interaction-diagram" id="interaction-diagram"></a>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-03-28 at 3.57.53 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-03-28 at 3.58.04 PM.png" alt=""><figcaption></figcaption></figure>

## Reference Docs <a href="#reference-docs" id="reference-docs"></a>

### Doc Links <a href="#doc-links" id="doc-links"></a>

| Workflow Technical Document         | <p> </p><p><a href="https://digit-discuss.atlassian.net/wiki/spaces/DD/pages/664174657">Workflow Service</a></p>                                                                   |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| User technical document             | [User Service](https://digit-discuss.atlassian.net/wiki/spaces/DD/pages/669450371)                                                                                                 |
| MDMS technical document             | NEEDS TO BE UPDATED                                                                                                                                                                |
| IDGen technical document            | NEEDS TO BE UPDATED                                                                                                                                                                |
| Localisation technical document     | NEEDS TO BE UPDATED                                                                                                                                                                |
| Persister technical document        | NEEDS TO BE UPDATED                                                                                                                                                                |
| SMS notification technical document | NEEDS TO BE UPDATED                                                                                                                                                                |
| API contract                        | [API Contract](https://editor.swagger.io/?url=https://raw.githubusercontent.com/egovernments/DIGIT-OSS/master/municipal-services/docs/fsm/Vehicle\_Registry\_Contract-v1.1.0.yaml) |
| Postman scripts                     | [Postman Collection](https://www.getpostman.com/collections/6d99bb40022396f848b2)                                                                                                  |

### API List <a href="#api-list" id="api-list"></a>

&#x20;

| Title                          | Link                                                                                                                                                                                                                                                           |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| vehicle/v1/\_create            | [https://www.getpostman.com/collections/6d99bb40022396f848b2](https://www.getpostman.com/collections/6d99bb40022396f848b2)                                                                                                                                     |
| vehicle/v1/\_search            | [https://www.getpostman.com/collections/6d99bb40022396f848b2](https://www.getpostman.com/collections/6d99bb40022396f848b2)                                                                                                                                     |
| /vehicle/v1/\_plainsearch      | [https://www.getpostman.com/collections/6d99bb40022396f848b2](https://www.getpostman.com/collections/6d99bb40022396f848b2)                                                                                                                                     |
| /vehicle/trip/v1/\_create      | [https://www.getpostman.com/collections/4d425d97a5db5ced11b6](https://www.getpostman.com/collections/4d425d97a5db5ced11b6)                                                                                                                                     |
| vehicle/trip/v1/\_update       | [https://www.getpostman.com/collections/6d99bb40022396f848b2](https://www.getpostman.com/collections/6d99bb40022396f848b2)                                                                                                                                     |
| vehicle/trip/v1/\_search       | [https://www.getpostman.com/collections/6d99bb40022396f848b2](https://www.getpostman.com/collections/6d99bb40022396f848b2)                                                                                                                                     |
| /vehicle/trip/v1/\_plainsearch | [https://www.getpostman.com/collections/6d99bb40022396f848b2](https://www.getpostman.com/collections/6d99bb40022396f848b2)                                                                                                                                     |
| vehicle/v1/\_update            | [https://api.postman.com/collections/23418568-a15793e6-edeb-4393-a6b8-38fd90deca6f?access\_key=PMAT-01GMQPGY7NKF54DP47PEJH6NZG](https://api.postman.com/collections/23418568-a15793e6-edeb-4393-a6b8-38fd90deca6f?access\_key=PMAT-01GMQPGY7NKF54DP47PEJH6NZG) |
