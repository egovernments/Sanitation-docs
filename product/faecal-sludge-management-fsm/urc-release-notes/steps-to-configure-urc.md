# Steps to Configure URC

### **MDMS Changes** <a href="#mdms-changes" id="mdms-changes"></a>

| **Feature**                                 | **Service Name**                                  | **PR**                                                                                                                                                                                           |
| ------------------------------------------- | ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Added new component for URC                 | data/pg/FSM/CommonFieldsConfig.JSON               | [https://github.com/egovernments/egov-mdms-data/commit/8117ef65d1da946aad11ce0b230482c1babc7faa](https://github.com/egovernments/egov-mdms-data/commit/8117ef65d1da946aad11ce0b230482c1babc7faa) |
| Create UrcConfig.json to enable URC feature | data/pg/angul/FSM/UrcConfig.json                  | [https://github.com/egovernments/egov-mdms-data/commit/457a65f0da8cd6448fb2687015843a3a0281fd68](https://github.com/egovernments/egov-mdms-data/commit/457a65f0da8cd6448fb2687015843a3a0281fd68) |
| Enabling overRide for tripAmount            | data/pg/FSM/Config.json                           | [https://github.com/egovernments/egov-mdms-data/commit/c18e06d623300cd7bee0d62a9719a66e2489d917](https://github.com/egovernments/egov-mdms-data/commit/c18e06d623300cd7bee0d62a9719a66e2489d917) |
| Added GP data for specific ulb              | data/pg/ulb-name/egov-location/boundary-data.json | [https://github.com/egovernments/egov-mdms-data/commit/bf5533a156af4468995dec496411110eb8644779](https://github.com/egovernments/egov-mdms-data/commit/bf5533a156af4468995dec496411110eb8644779) |

Create UrcConfig.json and Add GP data for all the ulbs for which the URC feature needs to enable.

### Backend Changes <a href="#backend-changes" id="backend-changes"></a>

<table data-header-hidden><thead><tr><th width="215.33333333333326"></th><th width="139"></th><th></th></tr></thead><tbody><tr><td><strong>Feature</strong></td><td><strong>Service Name</strong></td><td><strong>Changes</strong></td></tr><tr><td>URC</td><td>FSM</td><td><a href="https://github.com/egovernments/DIGIT-Dev/pull/5296">https://github.com/egovernments/DIGIT-Dev/pull/5296</a><br><a href="https://github.com/egovernments/DIGIT-Dev/pull/5297">https://github.com/egovernments/DIGIT-Dev/pull/5297</a><br><a href="https://github.com/egovernments/DIGIT-Dev/pull/5308">https://github.com/egovernments/DIGIT-Dev/pull/5308</a><br><a href="https://github.com/egovernments/DIGIT-Dev/pull/5309">https://github.com/egovernments/DIGIT-Dev/pull/5309</a><br><a href="https://github.com/egovernments/DIGIT-Dev/pull/5312">https://github.com/egovernments/DIGIT-Dev/pull/5312</a><br><a href="https://github.com/egovernments/DIGIT-Dev/pull/5315">https://github.com/egovernments/DIGIT-Dev/pull/5315</a><br><a href="https://github.com/egovernments/DIGIT-Dev/pull/5317">https://github.com/egovernments/DIGIT-Dev/pull/5317</a><br><a href="https://github.com/egovernments/DIGIT-Dev/pull/5318">https://github.com/egovernments/DIGIT-Dev/pull/5318</a><br><a href="https://github.com/egovernments/DIGIT-Dev/pull/5319">https://github.com/egovernments/DIGIT-Dev/pull/5319</a><br><a href="https://github.com/egovernments/DIGIT-Dev/pull/5376">https://github.com/egovernments/DIGIT-Dev/pull/5376</a><br><a href="https://github.com/egovernments/DIGIT-Dev/pull/5378">https://github.com/egovernments/DIGIT-Dev/pull/5378</a><br><a href="https://github.com/egovernments/DIGIT-Dev/pull/5399">https://github.com/egovernments/DIGIT-Dev/pull/5399</a><br><a href="https://github.com/egovernments/DIGIT-Dev/pull/5406">https://github.com/egovernments/DIGIT-Dev/pull/5406</a></td></tr></tbody></table>

### UI Changes <a href="#ui-changes" id="ui-changes"></a>

[https://github.com/egovernments/digit-ui/pull/84](https://github.com/egovernments/digit-ui/pull/84)

[https://github.com/egovernments/digit-ui/pull/85](https://github.com/egovernments/digit-ui/pull/85)

[https://github.com/egovernments/digit-ui/pull/86](https://github.com/egovernments/digit-ui/pull/86)

[https://github.com/egovernments/digit-ui/pull/87](https://github.com/egovernments/digit-ui/pull/87)

[https://github.com/egovernments/digit-ui/pull/88](https://github.com/egovernments/digit-ui/pull/88)

[https://github.com/egovernments/digit-ui/pull/88](https://github.com/egovernments/digit-ui/pull/88)

[https://github.com/egovernments/digit-ui/pull/89](https://github.com/egovernments/digit-ui/pull/89)

[https://github.com/egovernments/digit-ui/pull/90](https://github.com/egovernments/digit-ui/pull/90)

[https://github.com/egovernments/digit-ui/pull/91](https://github.com/egovernments/digit-ui/pull/91)

[https://github.com/egovernments/digit-ui/pull/92](https://github.com/egovernments/digit-ui/pull/92)

[https://github.com/egovernments/digit-ui/pull/93](https://github.com/egovernments/digit-ui/pull/93)

[https://github.com/egovernments/digit-ui/pull/95](https://github.com/egovernments/digit-ui/pull/95)

[https://github.com/egovernments/digit-ui/pull/96](https://github.com/egovernments/digit-ui/pull/96)

[https://github.com/egovernments/digit-ui/pull/97](https://github.com/egovernments/digit-ui/pull/97)

[https://github.com/egovernments/digit-ui/pull/98](https://github.com/egovernments/digit-ui/pull/98)

[https://github.com/egovernments/digit-ui/pull/99](https://github.com/egovernments/digit-ui/pull/99)

[https://github.com/egovernments/digit-ui/pull/105](https://github.com/egovernments/digit-ui/pull/105)

[https://github.com/egovernments/digit-ui/commit/e6c4825b3141c02476b31f7907b4c97896d38d20](https://github.com/egovernments/digit-ui/commit/e6c4825b3141c02476b31f7907b4c97896d38d20)

[https://github.com/egovernments/digit-ui/pull/107](https://github.com/egovernments/digit-ui/pull/107)

[https://github.com/egovernments/digit-ui/commit/f3ae54412997da76bc9adc61d177d498eda6b3ac](https://github.com/egovernments/digit-ui/commit/f3ae54412997da76bc9adc61d177d498eda6b3ac)

### Localisation Changes <a href="#localisation-changes" id="localisation-changes"></a>

Following localisations needs to be added :

```json
[
    {
        "code": "CS_FILE_APPLICATION_PROPERTY_LOCATION_GRAM_PANCHAYAT_TEXT",
        "message": "Choose the Grama Panchayat of the Property from the list given below.",
        "module": "rainmaker-fsm",
        "locale": "en_IN"
    },
    {
        "code": "DSS_FSM_TOTAL_REQUESTS_FROM_GP",
        "message": "Applications from Grama Panchayat",
        "module": "rainmaker-fsm",
        "locale": "en_IN"
    },
    {
        "code": "FROM_GRAM_PANCHAYAT",
        "message": "From Gram Panchayat",
        "module": "rainmaker-fsm",
        "locale": "en_IN"
    },
    {
        "code": "WITHIN_ULB_LIMITS",
        "message": "Within ULB Limits",
        "module": "rainmaker-fsm",
        "locale": "en_IN"
    },
    {
        "code": "CS_VILLAGE_NAME",
        "message": "Village Name",
        "module": "rainmaker-common",
        "locale": "en_IN"
    },
    {
        "code": "ES_INBOX_PLEASE_SPECIFY_GRAM_PANCHAYAT",
        "message": "If Others, Specify Gram Panchayat",
        "module": "rainmaker-common",
        "locale": "en_IN"
    },
    {
        "code": "ES_INBOX_PLEASE_SPECIFY_LOCALITY",
        "message": "If Others, Specify Locality",
        "module": "rainmaker-common",
        "locale": "en_IN"
    },
    {
        "code": "ES_INBOX_PLEASE_SPECIFY_VILLAGE",
        "message": "Specify Village",
        "module": "rainmaker-common",
        "locale": "en_IN"
    },
    {
        "code": "CS_GRAM_PANCHAYAT",
        "message": "Gram Panchayat",
        "module": "rainmaker-common",
        "locale": "en_IN"
    },
    {
        "code": "TIP_DSS_FSM_TOTAL_REQUESTS_FROM_GP",
        "message": "Applications from Grama Panchayat",
        "module": "rainmaker-dss",
        "locale": "en_IN"
    },
    {
        "code": "TIP_DSS_FSM_TOTAL_REQUESTS_FROM_GP",
        "message": "Applications from Grama Panchayat",
        "module": "rainmaker-fsm",
        "locale": "en_IN"
    },
    {
        "code": "TIP_DSS_FSM_TOTAL_REQUESTS_FROM_GP",
        "message": "Applications from Grama Panchayat",
        "module": "rainmaker-common",
        "locale": "en_IN"
    },
    {
        "code": "FROM_OTHER_ULB",
        "message": "Outside ULB Limits",
        "module": "rainmaker-fsm",
        "locale": "en_IN"
    }
]
```

### Dashboard Changes <a href="#dashboard-changes" id="dashboard-changes"></a>

In the dashboard, add the following chart:

| **Feature**                                                                                                                                | **Location**                                                                                                                                                 | **PR**                                                                                                                                               |
| ------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| <ol start="1"><li>Add pie chart: Applications by Source</li><li>Add Bar chart: No. of applications per month from Gram Panchayat</li></ol> | <p>configs/egov-dss-dashboards/dashboard-analytics/ChartApiConfig.json,</p><p>configs/egov-dss-dashboards/dashboard-analytics/MasterDashboardConfig.json</p> | [https://github.com/egovernments/punjab-rainmaker-customization/pull/659/](https://github.com/egovernments/punjab-rainmaker-customization/pull/659/) |

\
