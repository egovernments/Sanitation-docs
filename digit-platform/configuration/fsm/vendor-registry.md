# Vendor Registry

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

[PR for updating vendor-persister file for sanitation worker feature.](https://github.com/egovernments/configs/commit/07489d419f3ffad382908b34073da17f1dba263e)

## MDMS Configuration

[SAN-1049: Added role actions for Driver APIs. · egovernments/egov-mdms-data@fb8e530](https://github.com/egovernments/egov-mdms-data/commit/fb8e53037bf5ff40ca78506b02a8d7b04dc96e88)

[SAN-1063: Added the permissiosn for Vehicle trip creation · egovernments/egov-mdms-data@632ee94](https://github.com/egovernments/egov-mdms-data/commit/632ee94e95d74ddb1d3f306ec83e3de02a329a2a)

[SAN-1047: Added role action mapping for vendor and vehicle update · egovernments/egov-mdms-data@3e608a8](https://github.com/egovernments/egov-mdms-data/commit/3e608a844be189d5be1d0657b4d8b1b663b6e94c)

## Business Service / Workflow Configuration <a href="#business-service-workflow-configuration" id="business-service-workflow-configuration"></a>

NA

## Actions & Role Action Mapping <a href="#actions-and-role-action-mapping" id="actions-and-role-action-mapping"></a>

After adding actions and role action mappings, restart the `egov-mdms-service`

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

###
