# FSM FSTPO UI

In FSTP, we are trying to decouple the vehicle dispose from the FSM application. Whether vehicle is attached to any FSM application or not, we allow the vehicle to dispose in the FSTP plant.

### FSTP Home UI:&#x20;

After logging as a FSTP user, we have now the home button option:

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 4.25.08 PM.png>)

#### Technical Implementation Details: <a href="#technical-implementation" id="technical-implementation"></a>

Code changes path are:

**DIGIT-Dev/frontend/micro-ui/web/micro-ui-internals/packages/modules/fsm/src/components/FsmCard.js**

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 4.28.43 PM.png>)

### FSTP Operations UI:

After moving into “home” option, an FSTP user can choose from the following options:

* FSTP can choose Add Vehicle Log option if he/she wants to check whether a vehicle is linked to any application and dispose.
* FSTP can choose Inbox if he/she wants to check all the applications that are is ready to dispose.

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 4.28.52 PM.png>)

#### Technical Implementation Details:

The path for code:

_**frontend/micro-ui/web/micro-ui-internals/packages/modules/fsm/src/pages/employee/FstpOperations.js**_

The code snippet for populating the options:

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 4.31.22 PM.png>)

The code snippet for rendering the icon:

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 4.33.19 PM.png>)

_**ULBHomeCard.js**_ is the common component used to populate options in the screen.

The paths:

**frontend/micro-ui/web/micro-ui-internals/packages/react-components/src/atoms/ULBHomeCard.js**\


### FSTP Add Vehicle Log UI: <a href="#fstp-add-vehicle-log-ui" id="fstp-add-vehicle-log-ui"></a>

FSTP can add vehicle log using vehicle number (in proper format with spaces, e.g. AB 00 CD 1234). An improper format will throw an error.

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 4.47.24 PM.png>)

#### Techincal Implementation Details:  <a href="#techincal-implementation-details" id="techincal-implementation-details"></a>

The path for the code:

**frontend/micro-ui/web/micro-ui-internals/packages/modules/fsm/src/pages/employee/FstpAddVehicle.js**

The code snippet for populating the add vehicle log field and its validation:

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 5.21.40 PM.png>)

The code snippet for rendering the screen:

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 5.23.35 PM.png>)

### FSTP Service Request Screen: <a href="#fstp-service-request-screen" id="fstp-service-request-screen"></a>

After entering the vehicle number in the add vehicle log screen, we are fetching the FSM application, which is linked to that specific vehicle number. The data is rendered as shown below:&#x20;

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 5.27.21 PM.png>)

#### Technical Implementation Details: <a href="#technical-implementation-details-.1" id="technical-implementation-details-.1"></a>

The path for the code:

**frontend/micro-ui/web/micro-ui-internals/packages/modules/fsm/src/pages/employee/FstpServiceRequest.js**

The code snippets for fetching the FSM application linked to vehicle number:

Fetching the vehicle Id using vehicle number

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 5.29.09 PM.png>)

Fetching the vehicle log using vehicle Id

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 5.31.00 PM.png>)

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 5.31.25 PM.png>)

Extracting out the FSM application number from vehicle log:

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 5.33.56 PM.png>)

Fetching the FSM application details using FSM application number

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 5.35.43 PM.png>)

The code snippets to render the data:

Mobile view

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 5.41.36 PM.png>)

Desktop view

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 5.44.01 PM.png>)

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 5.45.07 PM.png>)

### Vehicle Log screen:

After selecting the application, FSTPO can dispose the vehicle log in the vehicle log screen.

Additional details and attachment fields are introduced in new updates in FSM v1.2.1 .

The screen for the existing vehicle log:

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 5.48.48 PM.png>)

The screen for new vehicle log if no application is found for vehicle is shown below. FSTPO can dispose the new vehicle log by providing all the details below.

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 5.49.03 PM.png>)

#### Technical Implementation Details:

The path for the code:

**frontend/micro-ui/web/micro-ui-internals/packages/modules/fsm/src/pages/employee/FstpOperatorDetails.js**

The code snippet for additional details and attachments field:

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 5.52.03 PM.png>)

For new vehicle log:

The code snippets to render input field for new vehicle log:

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 5.52.18 PM.png>)

[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)](http://creativecommons.org/licenses/by/4.0/)All content on this page by [eGov Foundation ](https://egov.org.in/)is licensed under a [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/).
