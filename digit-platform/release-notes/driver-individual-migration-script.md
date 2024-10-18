# Driver-Individual Migration Script

## Overview

The Driver-Individual Migration Scripts is responsible for fetching all existing drivers in the system and subsequently generating creates corresponding individuals in the system.

## Build

The data migration has been implemented in Vendor Service with latest stable build -&#x20;

```
vendor:develop-fc828adcbe-31
```

## API Spec

[Link](https://github.com/egovernments/SANITATION/blob/master/API-CONTRACTS/fsm/Vendor\_Registration\_Contract.yaml)

## MDMS Roleaction Mapping

File Path -&#x20;

{% code title="actions-test.json" %}
```json
 {
      "id": 376,
      "name": "Migrate Driver Data to Individual",
      "url": "/vendor/v1/_migrate",
      "displayName": "Migrate Driver Data to Individual",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "vendor",
      "code": "null",
      "path": ""
    }
```
{% endcode %}

File Path -&#x20;

{% code title="roleactions.json" %}
```json
{
      "rolecode": "FSM_ADMIN",
      "actionid": 376,
      "actioncode": "",
      "tenantId": "pg"
    }
```
{% endcode %}

Please use FSM\_ADMIN credentials for accessing this API.
