# Dependency services of the FSM module

1. _**FSM Service**_ \
   Faecal sludge management (FSM) is a system that enables citizen to raise a request for septic tank cleaning with there ULB’s directly or indirectly reaching out to ULB counter. Citizen can track the application, make a payment for the charges and rate the service.\
   \
   **Actions & Role Action Mapping** : Add Role-Action mapping for the API’s in MDMS. Following are the required entries. They should be mapped to both CITIZEN and appropriate employee roles.

* MDMS Actions & Role Action Mapping for FSM

<pre class="language-json"><code class="lang-json">{
    "id": {{PLACEHOLDER1}},
    "name": "Create FSM Application",
    "url": "/fsm/v1/_create",
    "displayName": "Apply FSM",
    "orderNumber": 0,
    "enabled": false,
    "serviceCode": "FSM",
    "code": "null",
    "path": ""
  },
  {
    "id":  {{PLACEHOLDER2}},
    "name": "Search FSM Application",
    "url": "/fsm/v1/_search",
    "displayName": "Search  FSM Appliacations",
    "orderNumber": 1,
    "enabled": false,
    "serviceCode": "FSM",
    "code": "null",
    "path": ""
  },
  {
    "id": {{PLACEHOLDER3}},
    "name": "Update FSM Application",
    "url": "/fsm/v1/_update",
    "displayName": "Update FSM",
    "orderNumber": 0,
    "enabled": false,
    "serviceCode": "FSM",
    "code": "null",
    "path": ""
  },
<strong>  {
</strong>    "id": {{PLACEHOLDER4}},
    "name": "FSM Application Charge Payment Search",
    "url": "/collection-services/payments/FSM.TRIP_CHARGES/_search",
    "displayName": "FSM Application Charge Payment Search",
    "orderNumber": 1,
    "parentModule": "",
    "enabled": false,
    "serviceCode": "",
    "code": "null",
    "path": ""
  },
  {
    "id": {{PLACEHOLDER5}},
    "name": "FSM Application Audit Search",
    "url": "/fsm/v1/_audit",
    "displayName": "FSM Application Audit serach",
    "orderNumber": 1,
    "parentModule": "",
    "enabled": false,
    "serviceCode": "",
    "code": "null",
    "path": ""
  }, 
  {
    "id": {{PLACEHOLDER7}},
    "name": "Create FSTP FSTPOperator Mapping",
    "url": "/fsm/plantmap/v1/_create",
    "displayName": "Create FSTP FSTPOperator Map",
    "orderNumber": 0,
    "enabled": false,
    "serviceCode": "FSM",
    "code": "null",
    "path": ""
  },
  {
    "id": {{PLACEHOLDER8}},
    "name": "Update FSTP FSTPOperator Mapping",
    "url": "/fsm/plantmap/v1/_update",
    "displayName": "Update FSTP FSTPOperator Map",
    "orderNumber": 0,
    "enabled": false,
    "serviceCode": "FSM",
    "code": "null",
    "path": ""
  },
  {
    "id": {{PLACEHOLDER9}},
    "name": "Search FSTP FSTPOperator Mapping",
    "url": "/fsm/plantmap/v1/_search",
    "displayName": "Search FSTP FSTPOperator Map",
    "orderNumber": 0,
    "enabled": false,
    "serviceCode": "FSM",
    "code": "null",
    "path": ""
  },
  {
    "id": {{PlaceHolder10}},
    "name": "Inbox Search ofr uI",
    "url": "/inbox/v1/_search",
    "displayName": "Inbox Search",
    "orderNumber": 0,
    "enabled": false,
    "serviceCode": "inbox",
    "code": "null",
    "path": ""
  }
 
</code></pre>

* [Role Action Mapping](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/ACCESSCONTROL-ROLEACTIONS/roleactions.json):

| `displayName`                         | **Roles**                                                                                                                                            |
| ------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Create FSM Application                | CITIZEN, FSM\_CREATOR\_EMP, FSM\_SWACHH\_SATHI                                                                                                       |
| Search FSM Application                | CITIZEN,FSM\_DSO,FSM\_CREATOR\_EMP,FSM\_SWACHH\_SATHI,FSM\_EDITOR\_EMP,FSM\_ADMIN,FSM\_DSO,FSM\_DRIVER,FSM\_COLLECTOR,FSM\_VIEW\_EMP,FSM\_EMP\_FSTPO |
| Update FSM Application                | CITIZEN,FSM\_EDITOR\_EMP,FSM\_ADMIN,FSM\_DSO,FSM\_DRIVER                                                                                             |
| FSM Application Charge Payment Search | FSM\_ADMIN,FSM\_DSO,FSM\_DRIVER,FSM\_COLLECTOR,FSM\_EDITOR\_EMP,CITIZEN,FSM\_VIEW\_EMP                                                               |
| FSM Application Audit Search          | CITIZEN, FSM\_CREATOR\_EMP, FSM\_EDITOR\_EMP, FSM\_VIEW\_EMP, FSM\_ADMIN, FSM\_DSO, FSM\_DRIVER, FSM\_EMP\_FSTPO, FSM\_COLLECTOR                     |
| Create FSTP FSTPOperator Mapping      | FSM\_ADMIN                                                                                                                                           |
| Update FSTP FSTPOperator Mapping      | FSM\_ADMIN,FSM\_EMP\_FSTPO                                                                                                                           |
| Search FSTP FSTPOperator Mapping      | CITIZEN                                                                                                                                              |
| Inbox Search ofr uI                   | FSM\_EMP\_FSTPO,FSM\_COLLECTOR,FSM\_EDITOR\_EMP,FSM\_VIEW\_EMP,FSM\_CREATOR\_EMP,FSM\_ADMIN,FSM\_DSO                                                 |

#### API List <a href="#api-list" id="api-list"></a>

| <h4 id="title"><strong>Title</strong> </h4> | **Link**                                                                                                                   |
| ------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
|  `/fsm/v1/_create`                          | [https://www.getpostman.com/collections/a51486db12539a2aa597](https://www.getpostman.com/collections/a51486db12539a2aa597) |
|  `/fsm/v1/_update`                          | [https://www.getpostman.com/collections/a51486db12539a2aa597](https://www.getpostman.com/collections/a51486db12539a2aa597) |
| `/fsm/v1/_search`                           | [https://www.getpostman.com/collections/a51486db12539a2aa597](https://www.getpostman.com/collections/a51486db12539a2aa597) |
| `/fsm/v1/_audit`                            | [https://www.getpostman.com/collections/a51486db12539a2aa597](https://www.getpostman.com/collections/a51486db12539a2aa597) |
| `/fsm/v1/_plainsearch`                      | [https://www.getpostman.com/collections/a51486db12539a2aa597](https://www.getpostman.com/collections/a51486db12539a2aa597) |
| `/fsm/plantmap/v1/_create`                  | [https://www.getpostman.com/collections/a51486db12539a2aa597](https://www.getpostman.com/collections/a51486db12539a2aa597) |
| `/fsm/plantmap/v1/_update`                  | [https://www.getpostman.com/collections/a51486db12539a2aa597](https://www.getpostman.com/collections/a51486db12539a2aa597) |
| `/fsm/plantmap/v1/_search`                  | [https://www.getpostman.com/collections/a51486db12539a2aa597](https://www.getpostman.com/collections/a51486db12539a2aa597) |
| `/inbox/v1/_search`                         | [https://www.getpostman.com/collections/a51486db12539a2aa597](https://www.getpostman.com/collections/a51486db12539a2aa597) |
| /fsm/v1/\_schedular                         | [https://www.getpostman.com/collections/a51486db12539a2aa597](https://www.getpostman.com/collections/a51486db12539a2aa597) |

2. _**FSM Calculator Service**_&#x20;

* FSM Calculator is a system that enables FSM Admin to create billing slab for the FSM application(s) with different combination of propertyType , slum , tank capacity and etc..
* MDMS Actions & Role Action Mapping for FSM Calculator:

```ini
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
      }
    ]
```

* [Role Action Mapping](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/ACCESSCONTROL-ROLEACTIONS/roleactions.json):

| `displayName`          | **Roles**                                                        |
| ---------------------- | ---------------------------------------------------------------- |
| FSM BillingSlab Create | SUPERUSER,FSM\_ADMIN                                             |
| FSM BillingSlab Update | FSM\_CREATOR\_EMP,FSM\_EDITOR\_EMP,FSM\_ADMIN,FSM\_DSO,SUPERUSER |
| FSM BillingSlab Search | FSM\_CREATOR\_EMP,FSM\_EDITOR\_EMP,FSM\_DSO,CITIZEN,SUPERUSER    |

#### API List <a href="#api-list.1" id="api-list.1"></a>

<table data-header-hidden><thead><tr><th width="386.5"></th><th></th></tr></thead><tbody><tr><td><h4 id="title.1"><strong>Title</strong> </h4></td><td><strong>Link</strong></td></tr><tr><td> <code>fsm-calulator/v1/_calculate</code></td><td><a href="https://www.getpostman.com/collections/8b9eb951a810486f41a4">https://www.getpostman.com/collections/8b9eb951a810486f41a4</a></td></tr><tr><td> <code>fsm-calculator/v1/_estimate</code></td><td><a href="https://www.getpostman.com/collections/8b9eb951a810486f41a4">https://www.getpostman.com/collections/8b9eb951a810486f41a4</a></td></tr><tr><td><code>fsm-calculator/v1/billingSlab/_create</code></td><td><a href="https://www.getpostman.com/collections/8b9eb951a810486f41a4">https://www.getpostman.com/collections/8b9eb951a810486f41a4</a></td></tr><tr><td><code>fsm-calculator/v1/billingSlab/_update</code></td><td><a href="https://www.getpostman.com/collections/8b9eb951a810486f41a4">https://www.getpostman.com/collections/8b9eb951a810486f41a4</a></td></tr><tr><td><code>fsm-calculator/v1/billingSlab/_search</code></td><td><a href="https://www.getpostman.com/collections/8b9eb951a810486f41a4">https://www.getpostman.com/collections/8b9eb951a810486f41a4</a></td></tr><tr><td><code>fsm-calculator/v1/_cancellationfee</code></td><td><a href="https://api.postman.com/collections/23418568-77e3f5fb-dd9d-4f05-92e7-b15dcbeecffe?access_key=PMAT-01GN93ZP6B68E0T5TZ62GR02W0">https://api.postman.com/collections/23418568-77e3f5fb-dd9d-4f05-92e7-b15dcbeecffe?access_key=PMAT-01GN93ZP6B68E0T5TZ62GR02W0</a></td></tr><tr><td><code>fsm-calculator/v1/_advancebalancecalculate</code></td><td><a href="https://api.postman.com/collections/23418568-77e3f5fb-dd9d-4f05-92e7-b15dcbeecffe?access_key=PMAT-01GN93ZP6B68E0T5TZ62GR02W0">https://api.postman.com/collections/23418568-77e3f5fb-dd9d-4f05-92e7-b15dcbeecffe?access_key=PMAT-01GN93ZP6B68E0T5TZ62GR02W0</a></td></tr></tbody></table>

2. _**Vendor Service**_

Vendor Registry is a system that enables ULBEmployees to create and search Vendor i.e Desluding Operator (DSO) and driver entities with appropriate vehicle Entities for FSM Application. This document contains the details about how to setup the Vendor and describe the functionalities provided.

* MDMS Actions & Role Action Mapping for Vendor

```json
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
  "id": {{PLACEHOLDER6}},
  "name": "Update Vendor/DSO",
  "url": "/vendor/v1/_update",
  "displayName": "Update Vendor",
  "orderNumber": 0,
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
}
```

* [Role Action Mapping:](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/ACCESSCONTROL-ROLEACTIONS/roleactions.json)

<table data-header-hidden><thead><tr><th width="257.5"></th><th></th></tr></thead><tbody><tr><td><strong>Actions</strong></td><td><strong>Roles</strong></td></tr><tr><td>Create Vendor/DSO</td><td>SUPERUSER,FSM_ADMIN</td></tr><tr><td>Search Vendor/DSO</td><td>FSM_ADMIN,FSM_DSO,FSM_EDITOR_EMP,FSM_VIEW_EMP,FSM_EMP_FSTPO,CITIZEN,FSM_COLLECTOR,FSM_CREATOR_EMP,FSM_REPORT_VIEWER,FSM_DASHBOARD_VIEWERFSM_DRIVER,FSM_CREATOR_EMP,SUPERUSER</td></tr><tr><td>Update Vendor/DSO</td><td>FSM_EMP_FSTPO,FSM_ADMIN,SUPERUSER</td></tr><tr><td>Vendor Driver Create</td><td>FSM_ADMIN,FSM_CREATOR_EMP,FSM_DSO,FSM_EDITOR_EMP,FSM_VIEW_EMP,FSM_EMP_FSTPO</td></tr><tr><td>Vendor Driver Update</td><td>FSM_ADMIN,FSM_CREATOR_EMP,FSM_DSO,FSM_EDITOR_EMP,FSM_VIEW_EMP,FSM_EMP_FSTPO</td></tr><tr><td>Vendor Driver Search</td><td>FSM_ADMIN,FSM_CREATOR_EMP,FSM_DSO,FSM_EDITOR_EMP,FSM_VIEW_EMP,FSM_EMP_FSTPO</td></tr></tbody></table>

#### API List <a href="#api-list.2" id="api-list.2"></a>

<table data-header-hidden><thead><tr><th width="319.5"></th><th></th></tr></thead><tbody><tr><td><h4 id="title.2"><strong>Title</strong> </h4></td><td><strong>Link</strong></td></tr><tr><td><code>/vendor/v1/_create</code></td><td><a href="https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0">https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0</a></td></tr><tr><td><code>/vendor/v1/_search</code></td><td><a href="https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0">https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0</a></td></tr><tr><td><code>/vendor/v1/_plainsearch</code></td><td><a href="https://www.getpostman.com/collections/c79e98843bcdcc873d09">https://www.getpostman.com/collections/c79e98843bcdcc873d09</a></td></tr><tr><td><code>/vendor/v1/_update</code></td><td><a href="https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0">https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0</a></td></tr><tr><td><code>/vendor/driver/v1/_create</code></td><td><a href="https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0">https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0</a></td></tr><tr><td><code>/vendor/driver/v1/_update</code></td><td><a href="https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0">https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0</a></td></tr><tr><td><code>/vendor/driver/v1/_search</code></td><td><a href="https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0">https://api.postman.com/collections/23418568-17e45900-5801-462d-a6b1-2cf108b37c8d?access_key=PMAT-01GMQRX9YME11ZQKFV30QW4AP0</a></td></tr></tbody></table>

3. _**Vehicle Service**_

Vehicle Registry is a system that enables ULB Employees to create and search Vehicle Entities and schedule Vehicle Trip for FSM Application and track the VehicleTrip.

* MDMS Actions & Role Action Mapping for Vendor

<pre class="language-json"><code class="lang-json"> {
    "id": {{PLACEHOLDER1}},
    "name": "Create Vehicle Application",
    "url": "/vehicle/v1/_create",
    "displayName": "Create Vehicle",
    "orderNumber": 0,
    "enabled": false,
    "serviceCode": "vehicle",
    "code": "null",
    "path": ""
  },
  {
    "id":  {{PLACEHOLDER2}},
    "name": "Search Vehicle Application",
    "url": "/vehicle/v1/_search",
    "displayName": "Search  Vehicle",
    "orderNumber": 1,
    "enabled": false,
    "serviceCode": "vehicle",
    "code": "null",
    "path": ""
  },
  {
    "id": {{PLACEHOLDER3}},
    "name": "Vehicle Trip Search",
     "url": "/vehicle/trip/v1/_search",
    "displayName": "Vehicle Trip Search",
    "orderNumber": 1,
    "parentModule": "",
    "enabled": false,
    "serviceCode": "",
    "code": "null",
    "path": ""
  },
  {
    "id": {{PLACEHOLDER4}},
    "name": "Vehicle Trip Update",
     "url": "/vehicle/trip/v1/_update",
    "displayName": "Vehicle Trip Update",
    "orderNumber": 1,
    "parentModule": "",
    "enabled": false,
    "serviceCode": "",
    "code": "null",
    "path": ""
  },
  {
    "id": {{PLACEHOLDER5}},
    "name": "Vehicle Trip Create",
    "url": "/vehicle/trip/v1/_create",
    "displayName": "Vehicle Trip Create",
    "orderNumber": 1,
    "parentModule": "",
    "enabled": false,
    "serviceCode": "vehicle",
    "code": "null",
    "path": ""
  },
  {
<strong>    "id": {{PLACEHOLDER6}},
</strong>    "name": "Update Vehicle Application",
    "url": "/vehicle/v1/_update",
    "displayName": "Update Vehicle",
    "orderNumber": 0,
    "enabled": false,
    "serviceCode": "vehicle",
    "code": "null",
    "path": ""
  }
</code></pre>

* [Role Action Mapping:](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/ACCESSCONTROL-ROLEACTIONS/roleactions.json)

<table data-header-hidden><thead><tr><th width="279.5"></th><th></th></tr></thead><tbody><tr><td><code>displayName</code></td><td><strong>Roles</strong></td></tr><tr><td>Create Vehicle Application</td><td>FSM_ADMIN</td></tr><tr><td>Search Vehicle Application</td><td>FSM_ADMIN,FSM_DSO,FSM_EDITOR_EMP,FSM_VIEW_EMP,FSM_EMP_FSTPO,FSM_CREATOR_EMP</td></tr><tr><td>Vehicle Trip Search</td><td>FSM_EMP_FSTPO,FSM_EDITOR_EMP,FSM_CREATOR_EMP,FSM_ADMIN</td></tr><tr><td>Vehicle Trip Update</td><td>FSM_EMP_FSTPO</td></tr><tr><td>Update Vehicle Application</td><td>FSM_ADMIN</td></tr><tr><td>Vehicle Trip Create</td><td>FSM_EMP_FSTPO</td></tr></tbody></table>

#### API List <a href="#api-list.3" id="api-list.3"></a>

| <h4 id="title.3"><strong>Title</strong> </h4> | **Link**                                                                                                                                                                                                                                                       |
| --------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `vehicle/v1/_create`                          | [https://www.getpostman.com/collections/6d99bb40022396f848b2](https://www.getpostman.com/collections/6d99bb40022396f848b2)                                                                                                                                     |
| `vehicle/v1/_search`                          | [https://www.getpostman.com/collections/6d99bb40022396f848b2](https://www.getpostman.com/collections/6d99bb40022396f848b2)                                                                                                                                     |
| `/vehicle/v1/_plainsearch`                    | [https://www.getpostman.com/collections/6d99bb40022396f848b2](https://www.getpostman.com/collections/6d99bb40022396f848b2)                                                                                                                                     |
| /vehicle/trip/v1/\_create                     | [https://www.getpostman.com/collections/4d425d97a5db5ced11b6](https://www.getpostman.com/collections/4d425d97a5db5ced11b6)                                                                                                                                     |
| `vehicle/trip/v1/_update`                     | [https://www.getpostman.com/collections/6d99bb40022396f848b2](https://www.getpostman.com/collections/6d99bb40022396f848b2)                                                                                                                                     |
| `vehicle/trip/v1/_search`                     | [https://www.getpostman.com/collections/6d99bb40022396f848b2](https://www.getpostman.com/collections/6d99bb40022396f848b2)                                                                                                                                     |
| `/vehicle/trip/v1/_plainsearch`               | [https://www.getpostman.com/collections/6d99bb40022396f848b2](https://www.getpostman.com/collections/6d99bb40022396f848b2)                                                                                                                                     |
| `vehicle/v1/_update`                          | [https://api.postman.com/collections/23418568-a15793e6-edeb-4393-a6b8-38fd90deca6f?access\_key=PMAT-01GMQPGY7NKF54DP47PEJH6NZG](https://api.postman.com/collections/23418568-a15793e6-edeb-4393-a6b8-38fd90deca6f?access\_key=PMAT-01GMQPGY7NKF54DP47PEJH6NZG) |

\
