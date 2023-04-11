---
description: Details for registering new vendors
---

# FSM Vendor Registry

## Overview <a href="#overview" id="overview"></a>

The vendor registry is a system that enables urban local body (ULB)  employees to create and search a vendor, that is, the desludging operator (DSO) and driver entities with appropriate vehicle entities for the FSM application. This document contains the details about how to set up the vendor and describe the functionalities provided.

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

1. Vendor tab
2. Option to add/remove/update the vendor individually.
3. Users can add a vehicle and a driver.
4. Search for the list of all vehicles not associated with any vendors.&#x20;
5. Users can enable or disable the vendor.
6. Driver tab
7. Option to add/remove/update driver individually.
8. Users should be able to create/update/enable/disable a driver from driver screen.

## Deployment Details <a href="#deployment-details" id="deployment-details"></a>

1. Deploy the latest version of the vendor.
2. Add vendor-persister.yml file in the config folder in git and add that path in persister . (The file path is to be added in the environment yaml file in param called persist-yml-path ) and restart egov-persister-service.
3. Integrate the following below changes in vendor-persister.yml [SAN-1063 and 1064 (SAN-1158 and SAN-1157) -  Persister file - Vendor … · egovernments/configs@95dd26f](https://github.com/egovernments/configs/commit/95dd26f926ec44d07448926ee4b6b7e031847a57).
4. [SM-801 Not able to create vendor in UAT using api by madan-kumar-eGov · Pull Request #2237 · egovernments/configs](https://github.com/egovernments/configs/pull/2237/files).

## Configuration Details <a href="#configuration-details" id="configuration-details"></a>

[SAN-1047 - Added the query map for update vehicle and vendor topics. · egovernments/configs@56da639](https://github.com/egovernments/configs/commit/56da639add16c412056aeac119517abd434a5ece)

[SAN-1047: Added the vendor agency and payment preference column in th… · egovernments/configs@1659e4f](https://github.com/egovernments/configs/commit/1659e4fa57b1810eb88b0bae71f41311f37e87b1)

[SAN-1047: Added new columns for vendor vehicle and driver status · egovernments/configs@2337e21](https://github.com/egovernments/configs/commit/2337e21a2650dd9a08a8221f6980ace631e96cb4)

[Added the audit logging for vehicle and vendor · egovernments/configs@482185f](https://github.com/egovernments/configs/commit/482185f1a79ad094f716e480922374e40c6e217a)

[Added new changes for Driver create and update & vendor -vehicle driv… · egovernments/configs@9ee374e](https://github.com/egovernments/configs/commit/9ee374eb8bd94fa91825b938330bac6cd8559f50)

[Update the persister for driver updates · egovernments/configs@04368c7](https://github.com/egovernments/configs/commit/04368c79f56197dec2ccef0bfb2a1e1621645dfc)

[change the VENDOR\_ID to VECHILE\_ID for changing the vehicle status fo… · egovernments/configs@8a6ec56](https://github.com/egovernments/configs/commit/8a6ec5618543509a4b0f600ae663af51cefc3d74)

[updated the column in eg\_vendor\_driver table in update vendor topic · egovernments/configs@71b5297](https://github.com/egovernments/configs/commit/71b52978fc2eff113ffeb25068c8f76e09a7b2b8)

[changes reversed · egovernments/configs@5b86889](https://github.com/egovernments/configs/commit/5b868894bf1e76935cde9c016f263290ba5efbf1)

[unlinking ofdriver from vendor · egovernments/configs@a36bb6e](https://github.com/egovernments/configs/commit/a36bb6e58539fc979ac1542e7382ee0a714d661b)

[SM-766 vendor not getting update in driver Tab · egovernments/configs@ad83851](https://github.com/egovernments/configs/commit/ad83851d7141e939c8e2b9005da568795c9878df)

[SM-766 revert back the changes · egovernments/configs@e95bbeb](https://github.com/egovernments/configs/commit/e95bbeb0d835496dad0dc2ce709d90f31e4d01af)

[SM-766 Not able to change the vendor in driver details. · egovernments/configs@6f42ca2](https://github.com/egovernments/configs/commit/6f42ca265a87dbed277c3897cd8f6c67bd27ca06)

[SM-781 Not able to add vehicle in vendor tab · egovernments/configs@2b79b92](https://github.com/egovernments/configs/commit/2b79b92f10f809dedcb27216061d1e09f0324ae7)

## MDMS Configuration

[SAN-1049: Added role actions for Driver APIs. · egovernments/egov-mdms-data@fb8e530](https://github.com/egovernments/egov-mdms-data/commit/fb8e53037bf5ff40ca78506b02a8d7b04dc96e88)

[SAN-1063: Added the permissiosn for Vehicle trip creation · egovernments/egov-mdms-data@632ee94](https://github.com/egovernments/egov-mdms-data/commit/632ee94e95d74ddb1d3f306ec83e3de02a329a2a)

[SAN-1047: Added role action mapping for vendor and vehicle update · egovernments/egov-mdms-data@3e608a8](https://github.com/egovernments/egov-mdms-data/commit/3e608a844be189d5be1d0657b4d8b1b663b6e94c)

### Business Service / Workflow Configuration <a href="#business-service-workflow-configuration" id="business-service-workflow-configuration"></a>

NA

### Actions & Role Action Mapping <a href="#actions-and-role-action-mapping" id="actions-and-role-action-mapping"></a>

After adding actions and role-action mappings, restart the `egov-mdms-service`

**Actions**

```
{
      "id": {{PLACEHOLDER1}},
      "name": "Create Vendor/DSO",
      "url": "/vendor/v1/_create",
      "displayName": "Create Vehicle",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "vendor",
      "code": "null",
      "path": ""
    },
    {
      "id": {{PLACEHOLDER2}},
      "name": "Search Vendor/DSO",
      "url": "/vendor/v1/_search",
      "displayName": "Search  Vendor",
      "orderNumber": 1,
      "enabled": false,
      "serviceCode": "vendor",
      "code": "null",
      "path": ""
    },
{
  "id": {{PLACEHOLDER3}},
  "name": "Vendor Driver Create",
  "url": "/Vendor/driver/v1/_create",
  "displayName": "Vendor Driver Create",
  "orderNumber": 1,
  "parentModule": "",
  "enabled": false,
  "serviceCode": "vendor",
  "code": "null",
  "path": ""
},
{
  "id": {{PLACEHOLDER4}},
  "name": "Vendor Driver Update",
  "url": "/Vendor/driver/v1/_update",
  "displayName": "Vendor Driver Update",
  "orderNumber": 1,
  "parentModule": "",
  "enabled": false,
  "serviceCode": "vendor",
  "code": "null",
  "path": ""
},
{
  "id": {{PLACEHOLDER5}},
  "name": "Vendor Driver Search",
  "url": "/Vendor/driver/v1/_search",
  "displayName": "Vendor Driver Search",
  "orderNumber": 1,
  "parentModule": "",
  "enabled": false,
  "serviceCode": "vendor",
  "code": "null",
  "path": ""
},
{
  "id": {{PLACEHOLDER6}},
  "name": "Update Vendor/DSO",
  "url": "/vendor/v1/_update",
  "displayName": "Update Vendor",
  "orderNumber": 0,
  "enabled": false,
  "serviceCode": "vendor",
  "code": "null",
  "path": ""
}
```

**Role Action Mapping**

```
[
  {
    "rolecode": "FSM_ADMIN",
    "actionid": "{{PLACEHOLDER1}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_ADMIN",
    "actionid": "{{PLACEHOLDER2}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_DSO",
    "actionid": "{{PLACEHOLDER2}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_EDITOR_EMP",
    "actionid": "{{PLACEHOLDER2}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_VIEW_EMP",
    "actionid": "{{PLACEHOLDER2}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_EMP_FSTPO",
    "actionid": "{{PLACEHOLDER2}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "CITIZEN",
    "actionid": "{{PLACEHOLDER2}}",
    "actioncode": "",
    "tenantId": "pb"
  }
]
{
     "rolecode": "FSM_ADMIN",
     "actionid": {{PLACEHOLDER3}},
     "actioncode": "",
     "tenantId": "pb"
},
{
     "rolecode": "FSM_CREATOR_EMP",
     "actionid": {{PLACEHOLDER3}},
     "actioncode": "",
     "tenantId": "pb"
},
{
     "rolecode": "FSM_DSO",
     "actionid": {{PLACEHOLDER3}},
     "actioncode": "",
     "tenantId": "pb"
},
{
     "rolecode": "FSM_EDITOR_EMP",
     "actionid": {{PLACEHOLDER3}},
     "actioncode": "",
     "tenantId": "pb"
},
{
     "rolecode": "FSM_VIEW_EMP",
     "actionid": {{PLACEHOLDER3}},
     "actioncode": "",
     "tenantId": "pb"
},
{
     "rolecode": "FSM_EMP_FSTPO",
     "actionid": {{PLACEHOLDER3}},
     "actioncode": "",
     "tenantId": "pb"
},
{
     "rolecode": "FSM_ADMIN",
     "actionid": {{PLACEHOLDER4}},
     "actioncode": "",
     "tenantId": "pb"
},
{
     "rolecode": "FSM_CREATOR_EMP",
     "actionid": {{PLACEHOLDER4}},
     "actioncode": "",
     "tenantId": "pb"
},
{
     "rolecode": "FSM_DSO",
     "actionid": {{PLACEHOLDER4}},
     "actioncode": "",
     "tenantId": "pb"
},
{
     "rolecode": "FSM_EDITOR_EMP",
     "actionid": {{PLACEHOLDER4}},
     "actioncode": "",
     "tenantId": "pb"
},
{
     "rolecode": "FSM_VIEW_EMP",
     "actionid": {{PLACEHOLDER4}},
     "actioncode": "",
     "tenantId": "pb"
},
{
     "rolecode": "FSM_EMP_FSTPO",
     "actionid": {{PLACEHOLDER4}},
     "actioncode": "",
     "tenantId": "pb"
},
{
     "rolecode": "FSM_ADMIN",
     "actionid": {{PLACEHOLDER5}},
     "actioncode": "",
     "tenantId": "pb"
},
{
     "rolecode": "FSM_CREATOR_EMP",
     "actionid": {{PLACEHOLDER5}},
     "actioncode": "",
     "tenantId": "pb"
},
{
     "rolecode": "FSM_DSO",
     "actionid": {{PLACEHOLDER5}},
     "actioncode": "",
     "tenantId": "pb"
},
{
     "rolecode": "FSM_EDITOR_EMP",
     "actionid": {{PLACEHOLDER5}},
     "actioncode": "",
     "tenantId": "pb"
},
{
     "rolecode": "FSM_VIEW_EMP",
     "actionid": {{PLACEHOLDER5}},
     "actioncode": "",
     "tenantId": "pb"
},
{
     "rolecode": "FSM_EMP_FSTPO",
     "actionid": {{PLACEHOLDER5}},
     "actioncode": "",
     "tenantId": "pb"
},
{
     "rolecode": "FSM_ADMIN",
     "actionid": {{PLACEHOLDER6}},
     "actioncode": "",
     "tenantId": "pb"
}
```

### **Infra Ops Configuration**

Configurations that we can manage through values.yml vehicle in infra-ops repo are listed below.\
values.yml for the vehicle is available below.\


| Description                                               | Name in values.yml                 | Current value                            |
| --------------------------------------------------------- | ---------------------------------- | ---------------------------------------- |
| Kafka Consumer Group                                      | SPRING\_KAFKA\_CONSUMER\_GROUP\_ID | egov-vendor-services                     |
| kafka topic to which service push data to save new Vendor | PERSISTER\_SAVE\_VENDOR\_TOPIC     | save-vendor-application                  |
| mdms service host                                         | EGOV\_MDMS\_HOST                   | egov-mdms-service from egov-service-host |
| Vehicle service host                                      | EGOV\_VEHICLE\_HOST                | vehicle from egov-service-host           |
| User service host                                         | EGOV\_USER\_HOST                   | egov-user-service from egov-service-host |
| Location service host                                     | EGOV\_LOCATION\_HOST               | egov-location from egov-service-host     |

**Configurations sample in Values.yml**

```
# Common Labels
labels:
  app: "vendor"
  group: "rainmaker"


# Ingress Configs
ingress:
  enabled: true
  zuul: true
  context: "vendor"


# Init Containers Configs
initContainers:
  dbMigration:
    enabled: true
    schemaTable: "vendor_schema"
    image:
      repository: "vendor-db"


# Container Configs
image:
  repository: "vendor"
replicas: "1"
healthChecks:
  enabled: true
  livenessProbePath: "/vendor/health"
  readinessProbePath: "/vendor/health"
appType: "java-spring"
tracing-enabled: true
heap: "-Xmx256m -Xms256m"
java-args: "-Dspring.profiles.active=monitoring"


# Additional Container Envs
env: |
  - name: EGOV_VEHICLE_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: vehicle
  - name: EGOV_MDMS_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-mdms-service
  - name: EGOV_USER_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-user
  - name: EGOV_LOCATION_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-location
  - name: EGOV_HRMS_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-hrms
  - name: SPRING_KAFKA_CONSUMER_GROUP_ID
    value: egov-vendor-services
  - name: PERSISTER_SAVE_VENDOR_TOPIC
    value: save-vendor-application
  - name: PERSISTER_UPDATE_VENDOR_TOPIC
    value: update-vendor-application
  - name: SPRING_KAFKA_PRODUCER_KEY_SERIALIZER
    value: org.apache.kafka.common.serialization.StringSerializer
  - name: SPRING_KAFKA_PRODUCER_VALUE_SERIALIZER
    value: org.springframework.kafka.support.serializer.JsonSerializer
  - name: JAVA_OPTS
    value: {{ index .Values "heap" | quote }}
  - name: JAVA_ARGS
    value: {{ index .Values "java-args" | quote }}
  - name: SERVER_PORT
    value: "8080"
  - name: SECURITY_BASIC_ENABLED
    value: "false"  
  - name: MANAGEMENT_SECURITY_ENABLED
    value: "false"
  {{- if index .Values "tracing-enabled" }}
  - name: TRACER_OPENTRACING_ENABLED
    value: "true" 
  {{- end }}
```

## Data Setup

The DSO for FSM system is a vendor. For every city/ULB, a DSO should be created with the representative details as owner, associated vehicles and drivers.

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

Any system or DIGIT module can be integrated with the vendor service. It helps to manage the vendor with the vehicles, drivers and owner for representatives, and login for the representative/owner to login into the system to carry our role-specific operations.

### Integration Benefits <a href="#integration-benefits" id="integration-benefits"></a>

* Validation of DSO/vendor availability.
* Fetch the vehicle assigned to the DSO.
* Fetch the drivers assigned to the DSO.

### Steps to Integration <a href="#steps-to-integration" id="steps-to-integration"></a>

* FSM to call `vendor/v1/_search` to fetch the DSOs.
* FSM can call `vendor/v1/_search` to fetch the DSOs and the respective vehicles and drivers.

### Interaction Diagrams <a href="#interaction-diagram" id="interaction-diagram"></a>

<figure><img src="../../../.gitbook/assets/Screenshot 2023-03-28 at 3.29.24 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/Screenshot 2023-03-28 at 3.31.24 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/Screenshot 2023-03-28 at 3.33.35 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/Screenshot 2023-03-28 at 3.34.23 PM.png" alt=""><figcaption></figcaption></figure>



## Reference Docs <a href="#reference-docs" id="reference-docs"></a>

### Doc Links <a href="#doc-links" id="doc-links"></a>

| Workflow Technical Document         | [Workflow Service](https://digit-discuss.atlassian.net/wiki/spaces/DD/pages/664174657)                                                                                                |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| User technical document             | [User Service](https://digit-discuss.atlassian.net/wiki/spaces/DD/pages/669450371)                                                                                                    |
| MDMS technical document             | NEEDS TO BE UPDATED                                                                                                                                                                   |
| IDGen technical document            | NEEDS TO BE UPDATED                                                                                                                                                                   |
| Localisation technical document     | NEEDS TO BE UPDATED                                                                                                                                                                   |
| Persister technical document        | NEEDS TO BE UPDATED                                                                                                                                                                   |
| SMS notification technical document | NEEDS TO BE UPDATED                                                                                                                                                                   |
| API contract                        | [API Contract](https://editor.swagger.io/?url=https://raw.githubusercontent.com/egovernments/DIGIT-OSS/master/municipal-services/docs/fsm/Vendor\_Registration\_Contract-v1.1.0.yaml) |
| Postman scripts                     | [Postman Collection](https://www.getpostman.com/collections/c79e98843bcdcc873d09)                                                                                                     |

### API List <a href="#api-list" id="api-list"></a>

| /vendor/v1/\_create        | [https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access\_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0](https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access\_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0) |
| -------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| /vendor/v1/\_search        | [https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access\_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0](https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access\_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0) |
| /vendor/v1/\_plainsearch   | [https://www.getpostman.com/collections/c79e98843bcdcc873d09](https://www.getpostman.com/collections/c79e98843bcdcc873d09)                                                                                                                                     |
| /vendor/v1/\_update        | [https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access\_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0](https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access\_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0) |
| /vendor/driver/v1/\_create | [https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access\_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0](https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access\_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0) |
| /vendor/driver/v1/\_update | [https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access\_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0](https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access\_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0) |
| /vendor/driver/v1/\_search | [https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access\_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0](https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access\_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0) |

\


\




[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)](http://creativecommons.org/licenses/by/4.0/)All content on this page by [eGov Foundation ](https://egov.org.in/)is licensed under a [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/).
