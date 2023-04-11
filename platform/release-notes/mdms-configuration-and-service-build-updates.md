---
description: Configuration changes and service build updates
---

# MDMS Configuration & Service Build Updates

## MDMS Changes

| Feature                                       | Service Name                              | Changes                                                                 | Description        |
| --------------------------------------------- | ----------------------------------------- | ----------------------------------------------------------------------- | ------------------ |
| FSM registry zero pricing and advance balance | data/pg/ACCESSCONTROL-ACTIONS-TEST        | [1902](https://github.com/egovernments/egov-mdms-data/pull/2968/files)  | Role actions       |
|                                               | egov-mdms-data/data/pg/FSM/CheckList.json | [1904](https://github.com/egovernments/egov-mdms-data/pull/2969)        | CheckList.json     |
|                                               |                                           | [1904](https://github.com/egovernments/egov-mdms-data/pull/2971)        | Billing service    |
|                                               |                                           | [2972](https://github.com/egovernments/egov-mdms-data/pull/2972)        | CommonFieldsConfig |

## Configuration Changes

| Feature                                       | Service name            | Changes                                                                                                              | Description             |
| --------------------------------------------- | ----------------------- | -------------------------------------------------------------------------------------------------------------------- | ----------------------- |
| FSM registry zero pricing and advance balance | Update fsm-receipt.json | [2572](https://github.com/egovernments/configs/pull/2572), [1902](https://github.com/egovernments/configs/pull/2568) | Update fsm-receipt.json |

## Service Build Updates

| Category                                                                     | Services       | Git TAGS                                                                                                                                  | Docker artifact ID                     | Remarks                     |
| ---------------------------------------------------------------------------- | -------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------- | --------------------------- |
| FSM[ v1.3](https://github.com/egovernments/DIGIT-OSS/releases/tag/fsm\_v1.1) | FSM            | [fsm\_v1.3/municipal-services/fsm](https://github.com/egovernments/DIGIT-OSS/tree/fsm\_v1.3/municipal-services/fsm)                       | fsm-db:v1.3.0-29c64d6941-24            |                             |
|                                                                              | FSM calculator | [fsm\_v1.3/municipal-services/fsm-calculator](https://github.com/egovernments/DIGIT-OSS/tree/fsm\_v1.3/municipal-services/fsm-calculator) | fsm-calculator-db:v1.3.0-bd8f04a21c-12 |                             |
|                                                                              | Vehicle        | [fsm\_v1.3/municipal-services/vehicle](https://github.com/egovernments/DIGIT-OSS/tree/fsm\_v1.3/municipal-services/vehicle)               | vehicle-db:v1.3.0-5682061fd3-18        |                             |
|                                                                              | Vendor         | [fsm\_v1.3/municipal-services/vendor](https://github.com/egovernments/DIGIT-OSS/tree/fsm\_v1.3/municipal-services/vendor)                 | vendor-db:v1.3.0-d0ddde9f1b-45         | No changes in this release. |
|                                                                              | Inbox          | [fsm\_v1.1/municipal-services/inbox](https://github.com/egovernments/DIGIT-OSS/tree/fsm\_v1.1/municipal-services/inbox)                   | inbox:v1.1.1-3d4c447770-60             | Shared service in DIGIT.    |

### DIGIT Dependency Builds

The FSM release is bundled with the DIGIT 2.8 release. Hence, the release builds for the DIGIT 2.8 release can be referred to [here](https://digit-discuss.atlassian.net/wiki/spaces/DD/pages/2088665089/Service+Build+Updates+2.7).

| Category                                                                                                                                                                                                         | Services | Git TAGS                                                                    | Docker artifact ID | Remarks |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- | --------------------------------------------------------------------------- | ------------------ | ------- |
| Configs[ ](https://github.com/https://github.com/egovernments/configs/releases/tag/fsm\_v1.2.1egovernments/configs/releases/tag/fsm\_v1.1)[v1.3](https://github.com/egovernments/configs/releases/tag/fsm\_v1.3) |          | [fsm\_v1.3](https://github.com/egovernments/configs/releases/tag/fsm\_v1.3) |                    |         |
| MDMS[ ](https://github.com/egovernments/egov-mdms-data/releases/tag/fsm\_v1.2.1) [v1.3](https://github.com/egovernments/configs/releases/tag/fsm\_v1.3)                                                          |          | [fsm\_v1.3](https://github.com/egovernments/configs/releases/tag/fsm\_v1.3) |                    |         |
| Localisation[ ](https://github.com/egovernments/releasekit/releases/tag/fsm\_v1.2.1)[v1.3](https://github.com/egovernments/configs/releases/tag/fsm\_v1.3)                                                       |          | [fsm\_v1.3](https://github.com/egovernments/configs/releases/tag/fsm\_v1.3) |                    |         |



\
[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)](http://creativecommons.org/licenses/by/4.0/)_All content on this page by_ [_eGov Foundation_](https://egov.org.in/) _is licensed under a_ [_Creative Commons Attribution 4.0 International License_](http://creativecommons.org/licenses/by/4.0/)_._
