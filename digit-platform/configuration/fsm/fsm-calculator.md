---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# FSM Calculator

## Configuration Details <a href="#configuration-details" id="configuration-details"></a>

#### MDMS Configuration

FSM MDMS configuration is sufficient.

#### Business Service / Workflow Configuration

NA

#### Actions & Role Action Mapping

**Actions**

```
[
  {
    "id": {{PLACEHOLDER1}},
    "name": "FSM BillingSlab Create",
    "url": "/fsm-calculator/v1/billingSlab/_create",
    "displayName": "FSM BillingSlab Create",
    "orderNumber": 1,
    "parentModule": "",
    "enabled": false,
    "serviceCode": "",
    "code": "null",
    "path": ""
  },
  {
    "id": {{PLACEHOLDER2}},
    "name": "FSM BillingSlab Update",
    "url": "/fsm-calculator/v1/billingSlab/_update",
    "displayName": "FSM BillingSlab Update",
    "orderNumber": 1,
    "parentModule": "",
    "enabled": false,
    "serviceCode": "",
    "code": "null",
    "path": ""
  },
  {
    "id": {{PLACEHOLDER3}},
    "name": "FSM BillingSlab Search",
    "url": "/fsm-calculator/v1/billingSlab/_search",
    "displayName": "FSM BillingSlab Search",
    "orderNumber": 1,
    "parentModule": "",
    "enabled": false,
    "serviceCode": "",
    "code": "null",
    "path": ""
  },
  {
    "id": {{PLACEHOLDER4}},
    "name": "FSM Estimate",
    "url": "/fsm-calculator/v1/_estimate",
    "displayName": "FSM Estimate",
    "orderNumber": 1,
    "parentModule": "",
    "enabled": false,
    "serviceCode": "",
    "code": "null",
    "path": ""
  }
]

{
  "id": {{PLACEHOLDER5}},
  "name": "FSM Advance Balance Calculation",
  "url": "/fsm-calculator/v1/_advanceBalanceCalculate",
  "displayName": "FSM Advance Balance Calculation",
  "orderNumber": 1,
  "parentModule": "",
  "enabled": false,
  "serviceCode": "",
  "code": "null",
  "path": ""
},
{
  "id": {{PLACEHOLDER6}},
  "name": "FSM Cancellation Fee Calculation",
  "url": "/fsm-calculator/v1/_cancellationFee",
  "displayName": "FSM Advance Balance Calculation",
  "orderNumber": 1,
  "parentModule": "",
  "enabled": false,
  "serviceCode": "",
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
    "rolecode": "FSM_CREATOR_EMP",
    "actionid": "{{PLACEHOLDER3}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_EDITOR_EMP",
    "actionid": "{{PLACEHOLDER3}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_ADMIN",
    "actionid": "{{PLACEHOLDER3}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_DSO",
    "actionid": "{{PLACEHOLDER3}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_CREATOR_EMP",
    "actionid": "{{PLACEHOLDER4}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_EDITOR_EMP",
    "actionid": "{{PLACEHOLDER4}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_ADMIN",
    "actionid": "{{PLACEHOLDER4}}",
    "actioncode": "",
    "tenantId": "pb"
  }
]

{
  "rolecode": "CITIZEN",
  "actionid": {{PLACEHOLDER3}},
  "actioncode": "",
  "tenantId": "pb"
} ,
{
  "rolecode": "CITIZEN",
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
  "rolecode": "FSM_CREATOR_EMP",
  "actionid": {{PLACEHOLDER6}},
  "actioncode": "",
  "tenantId": "pb"
},
```

