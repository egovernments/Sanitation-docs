---
description: Enabling TQM module in DIGIT-UI
---

# How to Enable TQM UI

## Overview

To access the TQM module in DIGIT-UI, enable it from MDMS and add TQM  specific roles for the user to access TQM UI.&#x20;

## Enabling Module from MDMS

Add the following configuration in citymodule.json under this path in MDMS. The reference file is given below.

{% embed url="https://github.com/egovernments/egov-mdms-data/blob/0897a28910f5a5aae182da54cddf963083f16aba/data/pg/tenant/citymodule.json" %}
citymodule.json
{% endembed %}

```json
{
        "module": "Tqm",
        "code": "Tqm",
        "active": true,
        "order": 14,
        "additionalComponent": "TqmAdminNotification",
        "tenants": [
            {
                "code": "pg.cityb"
            },
            {
                "code": "pg.cityc"
            },
            {
                "code": "pg.citya"
            }
        ]
      }
```

## Enabling TQM Module from UI

Add TQM to these files in DIGIT-UI codebase. Add it in enabledModules Array.&#x20;

Note: The name "TQM" should match the name "Tqm" added in mdms(citymodule). However, uppercase or lowercase does not matter.

1. frontend\micro-ui\web\micro-ui-internals\example\src\index.js
2. frontend\micro-ui\web\src\App.js

Files for reference:

{% embed url="https://github.com/egovernments/SANITATION/blob/7e548a49c137d1a0bc876fa517ce3fc94cc30548/frontend/micro-ui/web/micro-ui-internals/example/src/index.js" %}
index.js
{% endembed %}

{% embed url="https://github.com/egovernments/SANITATION/blob/7e548a49c137d1a0bc876fa517ce3fc94cc30548/frontend/micro-ui/web/src/App.js" %}
App.js
{% endembed %}

Sample object:

```javascript
const enabledModules = [
  "DSS",
  "HRMS",
  "Payment",
  "FSM",
  "Utilities",
  "Tqm", // Note -> here case is different than that of in mdms but it does not matter as long as name is same
  
]
```

### Roles Required to Access TQM UI

1. PQM\_TP\_OPERATOR -> This role is for Plant Operator user
2. PQM\_ADMIN -> This role is for ULB Admin user

Note: One user cannot have both these roles because flows and UI is different for these users. These roles are added in the mdms. The reference file is given below

{% embed url="https://github.com/egovernments/egov-mdms-data/blob/5ef0673280bd08850f6cdd359c73f4f88b19de4d/data/pg/ACCESSCONTROL-ROLES/roles.json" %}
Roles.json
{% endembed %}

### Recommended Core UI module version

* Enhancements were made to the core module version to support some of the features in TQM UI such as help section and notification card in ULB admin's home page
* The recommended core version for TQM UI is the following:&#x20;

```json
 "@egovernments/digit-ui-module-core": "1.8.0-beta.13"
```
