# Steps to Configure Garima

## **Overview**

* Provision of urban local bodies (ULBs)/DSO to assign one or more sanitation workers to each request:
  1. Sanitation workers will be made available via integration with the Garima database through API in the workflow.
  2. Since the Garima ID may not be well known to the ULB/DSO, a search functionality is to be made available by entering a phone number.
  3. Preview details of the selected sanitation worker for confirmation.
* Capture sanitation worker details if a sanitation worker is not available in the Garima database.&#x20;
* Provide aggregated data around how many requests are served by date via unique Garima IDs by API to UMC.&#x20;
* No linking will be done between the Garima worker and the vendor in Sujog FSM.
* Provide enumeration and benefits to sanitation workers.&#x20;
* Identify the percentage of services with evidence of safe practices.

## **MDMS Changes** <a href="#mdms-changes" id="mdms-changes"></a>

| **Feature**                                 | **Service Name**                                  | **PR**                                                                                                                                                                                           |
| ------------------------------------------- | ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Added new component for URC                 | data/pg/FSM/CommonFieldsConfig.JSON               | [https://github.com/egovernments/egov-mdms-data/commit/8117ef65d1da946aad11ce0b230482c1babc7faa](https://github.com/egovernments/egov-mdms-data/commit/8117ef65d1da946aad11ce0b230482c1babc7faa) |
| Create UrcConfig.json to enable URC feature | data/pg/angul/FSM/UrcConfig.json                  | [https://github.com/egovernments/egov-mdms-data/commit/457a65f0da8cd6448fb2687015843a3a0281fd68](https://github.com/egovernments/egov-mdms-data/commit/457a65f0da8cd6448fb2687015843a3a0281fd68) |
| Enabling overRide for tripAmount            | data/pg/FSM/Config.json                           | [https://github.com/egovernments/egov-mdms-data/commit/c18e06d623300cd7bee0d62a9719a66e2489d917](https://github.com/egovernments/egov-mdms-data/commit/c18e06d623300cd7bee0d62a9719a66e2489d917) |
| Added GP data for specific ulb              | data/pg/ulb-name/egov-location/boundary-data.json | [https://github.com/egovernments/egov-mdms-data/commit/bf5533a156af4468995dec496411110eb8644779](https://github.com/egovernments/egov-mdms-data/commit/bf5533a156af4468995dec496411110eb8644779) |

Create UrcConfig.json and add GP data for all the ULBs for which the URC feature needs to be enabled.

## Backend Changes <a href="#backend-changes" id="backend-changes"></a>

Created two adaptors for Garima:

&#x20;1\. Create API

&#x20;    \- The adapter calls the UMC API to create records and generate the unique garima ID.

2\. Search API&#x20;

&#x20;    \- Get a response from the UMC API based on the search criteria.

**Changes made in the FSM Update API**

When we update the FSM application, we create a record of Garima in the DIGIT system simultaneously which uses the individual service to create an individual record in the DIGIT database.&#x20;

Accordingly, one needs to set up the individual service for Garima.

## **Devops Changes**

[https://github.com/egovernments/DIGIT-DevOps/commit/0af62303dd48d944c988a2b1fb2e772c5df61b3d](https://github.com/egovernments/DIGIT-DevOps/commit/0af62303dd48d944c988a2b1fb2e772c5df61b3d)

[https://github.com/egovernments/DIGIT-DevOps/tree/unified-env/deploy-as-code/helm/charts/common-services/individual](https://github.com/egovernments/DIGIT-DevOps/tree/unified-env/deploy-as-code/helm/charts/common-services/individual)

| **Feature** | **Service Name** | **Changes**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| ----------- | ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Garima      | FSM              | <p><a href="https://github.com/egovernments/DIGIT-Dev/commit/5f28f07e9a43597da22703964edb00f8f554c1fc">https://github.com/egovernments/DIGIT-Dev/commit/5f28f07e9a43597da22703964edb00f8f554c1fc</a><br><a href="https://github.com/egovernments/DIGIT-Dev/commit/7b325edf26f34aaad0b8a1aa09f132c47232424c">https://github.com/egovernments/DIGIT-Dev/commit/7b325edf26f34aaad0b8a1aa09f132c47232424c</a><br><a href="https://github.com/egovernments/DIGIT-Dev/commit/0405a900dd8a12de03b60bb0f47ab1733ca03e66">https://github.com/egovernments/DIGIT-Dev/commit/0405a900dd8a12de03b60bb0f47ab1733ca03e66</a><br><a href="https://github.com/egovernments/DIGIT-Dev/commit/5f44d9c3dc0b7515beb10b53ba4e6c06d0df2833">https://github.com/egovernments/DIGIT-Dev/commit/5f44d9c3dc0b7515beb10b53ba4e6c06d0df2833</a><br><a href="https://github.com/egovernments/DIGIT-Dev/commit/99f15a522f70f0a44a4335b9492cd4b7d589e0c1">https://github.com/egovernments/DIGIT-Dev/commit/99f15a522f70f0a44a4335b9492cd4b7d589e0c1</a><br><a href="https://github.com/egovernments/DIGIT-Dev/commit/4f16b9e9681ebca19e814ed2ec8cf256cb08946c">https://github.com/egovernments/DIGIT-Dev/commit/4f16b9e9681ebca19e814ed2ec8cf256cb08946c</a><br></p> |

## Builds  <a href="#ui-changes" id="ui-changes"></a>

| Services   | Builds                                                                                                                                        |
| ---------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| FSM        | <p>egovio/fsm:FSM1.3Impl-sujog-Odisha-handover-pqm-4f16b9e968-176</p><p>egovio/fsm-db:FSM1.3Impl-sujog-Odisha-handover-pqm-4f16b9e968-176</p> |
| Individual | <p>egovio/individual-db:sujog-individual-d13a5d35fb-199 </p><p>egovio/individual:sujog-individual-d13a5d35fb-199</p>                          |
| Digit-ui   |  egovio/digit-ui:FSM-Sujog-40157ab-325                                                                                                        |

## Collection <a href="#ui-changes" id="ui-changes"></a>

| Service    | Api                                    | Collection                                                                                                                                                                                                                                                     |
| ---------- | -------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| FSM        | /fsm/v1/\_update                       | [https://api.postman.com/collections/23418568-5c53f370-7a38-41c2-9d87-4d8c7e0e1355?access\_key=PMAT-01HZ44N39TJCNA3KWQN1JMYV4M](https://api.postman.com/collections/23418568-5c53f370-7a38-41c2-9d87-4d8c7e0e1355?access\_key=PMAT-01HZ44N39TJCNA3KWQN1JMYV4M) |
|            | /fsm/v1/\_searchGarimaWorker           | [https://api.postman.com/collections/23418568-5c53f370-7a38-41c2-9d87-4d8c7e0e1355?access\_key=PMAT-01HZ44N39TJCNA3KWQN1JMYV4M](https://api.postman.com/collections/23418568-5c53f370-7a38-41c2-9d87-4d8c7e0e1355?access\_key=PMAT-01HZ44N39TJCNA3KWQN1JMYV4M) |
|            | /fsm/v1/\_createGarimaWorker           | [https://api.postman.com/collections/23418568-5c53f370-7a38-41c2-9d87-4d8c7e0e1355?access\_key=PMAT-01HZ44N39TJCNA3KWQN1JMYV4M](https://api.postman.com/collections/23418568-5c53f370-7a38-41c2-9d87-4d8c7e0e1355?access\_key=PMAT-01HZ44N39TJCNA3KWQN1JMYV4M) |
| Individual | /individual/v1/\_create                | [https://api.postman.com/collections/23418568-5c53f370-7a38-41c2-9d87-4d8c7e0e1355?access\_key=PMAT-01HZ44N39TJCNA3KWQN1JMYV4M](https://api.postman.com/collections/23418568-5c53f370-7a38-41c2-9d87-4d8c7e0e1355?access\_key=PMAT-01HZ44N39TJCNA3KWQN1JMYV4M) |
|            | /individual/v1/\_search                | [https://api.postman.com/collections/23418568-5c53f370-7a38-41c2-9d87-4d8c7e0e1355?access\_key=PMAT-01HZ44N39TJCNA3KWQN1JMYV4M](https://api.postman.com/collections/23418568-5c53f370-7a38-41c2-9d87-4d8c7e0e1355?access\_key=PMAT-01HZ44N39TJCNA3KWQN1JMYV4M) |
| UMC        | api/egov/sanitation-worker/search      | [https://api.postman.com/collections/23418568-9cbef29b-687f-4a34-9bec-7beef6d6eabd?access\_key=PMAT-01HZ44SGFJ64PAHARXDBQFMMD0](https://api.postman.com/collections/23418568-9cbef29b-687f-4a34-9bec-7beef6d6eabd?access\_key=PMAT-01HZ44SGFJ64PAHARXDBQFMMD0) |
|            | /api/v1/egov/sanitation-worker/capture | [https://api.postman.com/collections/23418568-9cbef29b-687f-4a34-9bec-7beef6d6eabd?access\_key=PMAT-01HZ44SGFJ64PAHARXDBQFMMD0](https://api.postman.com/collections/23418568-9cbef29b-687f-4a34-9bec-7beef6d6eabd?access\_key=PMAT-01HZ44SGFJ64PAHARXDBQFMMD0) |

## UI Changes <a href="#ui-changes" id="ui-changes"></a>

#### Step 1:

Create a Garima folder in web\micro-ui-internals\packages\modules\fsm\src\pages\employee

Add the following code.

https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/modules/fsm/src/pages/employee/GarimaDetails/index.js#L1C1-L200C30

#### Step 2:

Add the required Garima custom components and register them.

* [https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/modules/fsm/src/pageComponents/SelectVehicleNumber.js#L1C1-L62C36](https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/modules/fsm/src/pageComponents/SelectVehicleNumber.js#L1C1-L62C36)
* [https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/modules/fsm/src/pageComponents/SelectvehicleCapacity.js#L1C1-L34C36](https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/modules/fsm/src/pageComponents/SelectvehicleCapacity.js#L1C1-L34C36)
* [https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/modules/fsm/src/pageComponents/SelectGarimaTripNo.js#L1C1-L23C35](https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/modules/fsm/src/pageComponents/SelectGarimaTripNo.js#L1C1-L23C35)
* [https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/modules/fsm/src/pageComponents/SelectGraimaDriver.js#L1C1-L144C35](https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/modules/fsm/src/pageComponents/SelectGraimaDriver.js#L1C1-L144C35)
* [https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/modules/fsm/src/pageComponents/SelectGraimaHelper.js#L1C1-L165C35](https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/modules/fsm/src/pageComponents/SelectGraimaHelper.js#L1C1-L165C35)
* [https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/modules/fsm/src/pageComponents/AddSaniationWorker.js#L1C1-L184C35](https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/modules/fsm/src/pageComponents/AddSaniationWorker.js#L1C1-L184C35)
* https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/modules/fsm/src/pageComponents/GarimaPersonalDetails.js#L1C1-L199C38

Register the above custom page components:

* [https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/modules/fsm/src/Module.js#L180C2-L185C22](https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/modules/fsm/src/Module.js#L180C2-L185C22)
* [https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/modules/fsm/src/Module.js#L9C1-L14C70](https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/modules/fsm/src/Module.js#L9C1-L14C70)

#### Step 3:

Add the redirection URL for the "Add vehicle" action option:

[https://github.com/egovernments/digit-ui/commit/900f784b813f0e733ee0b9eae162759345248d42](https://github.com/egovernments/digit-ui/commit/900f784b813f0e733ee0b9eae162759345248d42)

#### Step 4:

&#x20;Add the necessary Garima hooks call:&#x20;

* [https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/libraries/src/hooks/fsm/useSanitationWorker.js#L1C1-L8C36](https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/libraries/src/hooks/fsm/useSanitationWorker.js#L1C1-L8C36)
* [https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/libraries/src/services/molecules/FSM/FileDesludging.js#L1C1-L82C3](https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/libraries/src/services/molecules/FSM/FileDesludging.js#L1C1-L82C3)
* [https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/libraries/src/hooks/fsm/useGarimaSearchActions.js#L1C1-L8C39](https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/libraries/src/hooks/fsm/useGarimaSearchActions.js#L1C1-L8C39)
* [https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/libraries/src/services/molecules/FSM/GarimaSearchActions.js#L1C1-L13C36](https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/libraries/src/services/molecules/FSM/GarimaSearchActions.js#L1C1-L13C36)
* [https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/libraries/src/services/elements/FSM.js#L177C1-L195C6](https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/libraries/src/services/elements/FSM.js#L177C1-L195C6)
* [https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/libraries/src/hooks/index.js#L91C1-L91C61](https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/libraries/src/hooks/index.js#L91C1-L91C61)
* [https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/libraries/src/hooks/index.js#L72C1-L72C67](https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/libraries/src/hooks/index.js#L72C1-L72C67)
* [https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/libraries/src/hooks/index.js#L310C3-L311C1](https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/libraries/src/hooks/index.js#L310C3-L311C1)
* [https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/libraries/src/hooks/index.js#L284C3-L284C26](https://github.com/egovernments/digit-ui/blob/900f784b813f0e733ee0b9eae162759345248d42/web/micro-ui-internals/packages/libraries/src/hooks/index.js#L284C3-L284C26)

## Localisation Changes

The following localisations need to be added:

```json
[
  {
    "code": "ADD_DRIVER_MOBILE_NUMBER",
    "message": "Add driver's mobile number",
    "module": "rainmaker-fsm",
    "locale": "en_IN"
  },
  {
    "code": "ADD_HELPER",
    "message": "Add Helper",
    "module": "rainmaker-fsm",
    "locale": "en_IN"
  },
  {
    "code": "ADD_HELPER_MOBILE_NUMBER",
    "message": "Add helper's mobile number",
    "module": "rainmaker-fsm",
    "locale": "en_IN"
  },
  {
    "code": "ASSIGN_DRIVER",
    "message": "Assign driver",
    "module": "rainmaker-fsm",
    "locale": "en_IN"
  },
  {
    "code": "ASSIGN_HELPER",
    "message": "Assign helper",
    "module": "rainmaker-fsm",
    "locale": "en_IN"
  },
  {
    "code": "ASSIGN_SANIATION_WORKER",
    "message": "Assign sanitation worker",
    "module": "rainmaker-fsm",
    "locale": "en_IN"
  },
  {
    "code": "ES_FSM_ADD_DRIVER_SUCCESS",
    "message": "Driver Added Successfully",
    "module": "rainmaker-fsm",
    "locale": "en_IN"
  },
  {
    "code": "ES_TITLE_DRIVER_DETAILS",
    "message": "Driver Details",
    "module": "rainmaker-fsm",
    "locale": "en_IN"
  },
  {
    "code": "GARIMA_DRIVER",
    "message": "Driver",
    "module": "rainmaker-fsm",
    "locale": "en_IN"
  },
  {
    "code": "FSM_HELPER_LABEL",
    "message": "Helper",
    "module": "rainmaker-fsm",
    "locale": "en_IN"
  },
  {
    "code": "GARIMA_HELPER",
    "message": "Helper",
    "module": "rainmaker-fsm",
    "locale": "en_IN"
  }
]
```

