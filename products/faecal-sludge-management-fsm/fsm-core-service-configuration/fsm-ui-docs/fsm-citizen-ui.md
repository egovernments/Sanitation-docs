# FSM Citizen UI

There are two new updates introduced in FSM v1.2.1 while creating new application - Stepper Information & Vehicle Capacity Selection in Service Request Screen.

## **Stepper Information**  <a href="#stepper-information" id="stepper-information"></a>

We are introducing stepper information in FSM while creating an application from the citizen side so that they have visibility on how many steps they need to go over to submit their details regarding their tank.&#x20;

![](<../../../../.gitbook/assets/Screenshot 2022-08-09 at 9.50.12 AM.png>)

#### Technical Implementations Details: <a href="#technical-implementations-detail" id="technical-implementations-detail"></a>

TLTimelineInFSM.js file is the common component and used for rendering the stepper information. The path of the file is:

**frontend/micro-ui/web/micro-ui-internals/packages/modules/fsm/src/components/TLTimelineInFSM.js**

The code snippets for defining the steps present in FSM application under case “APPLY”:

![](<../../../../.gitbook/assets/Screenshot 2022-08-09 at 9.56.12 AM.png>)

The code snippets to render the stepper information in each screen using Timeline component:

![using Timeline component to render the stepper Information in each screen provided with step number in currentStep.](<../../../../.gitbook/assets/Screenshot 2022-08-09 at 9.55.22 AM.png>)

## **Service Request Screen** <a href="#service-request-screen" id="service-request-screen"></a>

Citizens can now select vehicle capacity along with the number of trips required while creating an application. If nothing is selected, we will proceed by taking the minimum vehicle capacity available with the number of trips.

![](<../../../../.gitbook/assets/Screenshot 2022-08-09 at 10.01.43 AM.png>)

#### Technical Implementation Details:  <a href="#technical-implementation-details" id="technical-implementation-details"></a>

Code path: frontend/micro-ui/web/micro-ui-internals/packages/modules/fsm/src/pageComponents/SelectTripNo.js

The code snippet for rendering the Vehicle Capacity field in Service Request screen:

![](<../../../../.gitbook/assets/Screenshot 2022-08-09 at 10.03.51 AM.png>)

```
<CardText> {t("ES_VEHICLE CAPACITY")} </CardText>
 <RadioOrSelect
    options={vehicleMenu?.map((vehicle) => ({ ...vehicle, label: vehicle.capacity }))}
    selectedOption={vehicleCapacity}
    optionKey="capacity"
    onSelect={selectVehicle}
    optionCardStyles={{ zIndex: "60" }}
    t={t}
    isMandatory={config.isMandatory}isDropDown={true}
/>
```



The code snippet for fetching the vehicles available under all DSO:

![](<../../../../.gitbook/assets/Screenshot 2022-08-09 at 10.07.17 AM.png>)

```
const allVehicles = dsoData.reduce((acc, curr) => {
  return curr.vehicles && curr.vehicles.length ? acc.concat(curr.vehicles) : acc;
}, []);
const cpacityMenu = Array.from(new Set(allVehicles.map((a) => a.capacity)))
    .map((capacity) => allVehicles.find((a) => a.capacity === capacity));
```

The code snippet for setting the default vehicle capacity to minimum:

![](<../../../../.gitbook/assets/Screenshot 2022-08-09 at 10.09.11 AM.png>)

[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)](http://creativecommons.org/licenses/by/4.0/)All content on this page by [eGov Foundation ](https://egov.org.in/)is licensed under a [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/).
