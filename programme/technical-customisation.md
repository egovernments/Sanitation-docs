# Technical Customisation

## DIGIT UI Implementaton: Guidelines & FAQs

### Development Setup

Repo: [https://github.com/egovernments/digit-ui](https://github.com/egovernments/digit-ui)

Use the dev branch as the base branch for development.

Clone the repo and start using the following steps:&#x20;

\## install

yarn install

\## start dev server

yarn start

### Adding or modifying modules

* Modules are enabled by the MDMS config at[ citymodule.json](https://github.com/egovernments/egov-mdms-data/blob/DEV/data/pb/tenant/citymodule.json).&#x20;
* To add and enable any module in the new UI, src/App.js needs to be changed.
* Till PGR, we used to export the Module and Links were added to the registry. Now, adding to the registry is part of the modules themselves. We export only the init function of the module to take care of all the initialisations. Going forward, these init functions will have to be called. We will create the init function of PGR as well. These init modules must be called after initLibraries.

### Changing CS

CSS classes are published over CDN and can be seen at: https://unpkg.com/@egovernments/digit-ui-css/dist/index.css

Any class can be overwritten. Make changes in the src/index.css file.

### Customising Fields in a Form

Add any new component created in the registry,

Digit.ComponentRegistryService.setupRegistry({

&#x20; SelectName: SelectName

});

* If API calls are failing, the do the following:

Check src/setupProxy.js for proxy url in dev mode.

* If API calls are failing with no authorisation token, then do the following:

Create a .env file with following:

REACT\_APP\_USER\_TYPE=

REACT\_APP\_CITIZEN\_TOKEN=a3e5f0a2-4ff0-4680-855e-75051fb3e8f7

REACT\_APP\_EMPLOYEE\_TOKEN=061bad07-c0d5-4200-a74f-ca5ed090cf30

REACT\_APP\_GRO\_TOKEN=43af4c18-6418-4a35-8484-31f0700f465a

REACT\_APP\_LME\_TOKEN=fa9f4184-dc64-495d-bded-31674c71b09e

## FSM UI Implementation: Guidelines & FAQs

### Enable FSM

Modules are enabled by the MDMS config at: [https://github.com/egovernments/egov-mdms-data/blob/DEV/data/pb/tenant/citymodule.json](https://github.com/egovernments/egov-mdms-data/blob/DEV/data/pb/tenant/citymodule.json).&#x20;

It is done on dev via:

[egov-mdms-data: added fsm in citymodule and stateinfo localization moduleCLOSED](https://github.com/egovernments/egov-mdms-data/pull/1386)

Create a new branch for the state if already doesn’t exist from the master of repo:

[egovernments/digit-ui](https://github.com/egovernments/digit-ui).

To add and enable any module in the new UI, src/App.js needs to be changed.

We only export the init function of the module to take care of all the initialisations:

import { initFSMComponents } from "@egovernments/digit-ui-module-fsm";

const enabledModules = \["FSM"];

initFSMComponents();

### Changing CSS

CSS classes are published over CDN and can be seen at: https://unpkg.com/@egovernments/digit-ui-css/dist/index.css

Any class can be overwritten. Make changes in the src/index.css file.

### Customising Fields in a Form

Add any new component created in the registry,

Digit.ComponentRegistryService.setupRegistry({

&#x20;SelectName: SelectName});

Application config: The default config can be found at[ https://github.com/egovernments/egov-mdms-data/blob/DEV/data/pb/FSM/CommonFieldsConfig.json](https://github.com/egovernments/egov-mdms-data/blob/DEV/data/pb/FSM/CommonFieldsConfig.json).&#x20;

The config has different items in the application form. The new config, if made, needs to be initialised at Digit.Customizations.FSM.applicationFormConfig

```
{
  label: "ES_NEW_APPLICATION_PROPERTY_TYPE",
  isMandatory: true,
  type: "component",
  route: "property-type",
  key: "propertyType",
  component: "SelectPropertyType",
  texts: {
    headerCaption: "",
    header: "CS_FILE_APPLICATION_PROPERTY_LABEL",
    cardText: "CS_FILE_APPLICATION_PROPERTY_TEXT",
    submitBarLabel: "CS_COMMON_NEXT",
  },
  nextStep: "property-subtype",
}
```

* label: is the employee side label
* texts: is used for citizen side step form
* component: the component that is to be rendered here. Any component can be created to show here; examples can be seen at[ pageComponents](https://github.com/egovernments/digit-ui-internals/tree/development/packages/modules/fsm/src/pageComponents), These components are passed following params:&#x20;

&#x20;     \- t: translate function to be used to convert a key to localized text. e.g., t("CS\_CREATECOMPLAINT\_MOHALLA")

&#x20;     \- config: current step config as shown above

&#x20;     \- onSelect: on clicking of next or input, this handled to be called to save the data in the form state

&#x20;     \- userType: employee or citizen

&#x20;     \- formData: the current form state

&#x20;Similarly, in case of Applicant Details, MDMS config is located at: [https://github.com/egovernments/egov-mdms-data/blob/DEV/data/pb/FSM/PreFieldsConfig.json](https://github.com/egovernments/egov-mdms-data/blob/DEV/data/pb/FSM/PreFieldsConfig.json)

The Trip Details MDMS config is located at:[ https://github.com/egovernments/egov-mdms-data/blob/DEV/data/pb/FSM/PostFieldsConfig.json](https://github.com/egovernments/egov-mdms-data/blob/DEV/data/pb/FSM/PostFieldsConfig.json)

### Customising Views

Application details can be customised via defining: Digit.Customizations.FSM.getApplicationDetailsTableRows&#x20;

The function will be passed following params:

* id: application id
* service: application response object
* role: currently logged in user role CITIZEN or EMPLOYEE
* t: function used for translation&#x20;

```
getApplicationDetailsTableRows: ({ id, service, role, t }) => {
    if (role === "CITIZEN") {
      return {
        CS_FSM_APPLICATION_APPLICATION_NO: service.applicationNo,
        CS_FSM_APPLICATION_DETAIL_STATUS: t("CS_COMMON_" + service.applicationStatus),
        ...
      };
    }
    return {};
  }
```

### Customising Inbox Status Filter

Status can be filtered and rendered by MDMS config located at: [https://github.com/egovernments/egov-mdms-data/blob/DEV/data/pb/DIGIT-UI/RoleStatusMapping.json](https://github.com/egovernments/egov-mdms-data/blob/DEV/data/pb/DIGIT-UI/RoleStatusMapping.json)

Following customisations are available:

* userRole :  Role of the logged in user for application of customisation.
* statuses : List of statuses that needs to be shown for the specified user.
* zeroCheck : Check if the total application count for any status is 0 to hide or rearrange the list.
* fixed : Limits the status filter list to the specified list.

```
{
        "userRole": "FSM_EDITOR_EMP",
        "statuses": [
            "DSO_REJECTED",
            "ASSING_DSO",
            "CREATED"
        ],
        "zeroCheck" : true,
        "fixed": false
}
```
