# FSM Release Notes v1.2.1

## Overview <a href="#overview" id="overview"></a>

This release supports the unrestricted assignment of service requests to a single vehicle and Treatment Plant Management System (TPMS) - logging of vehicle entry, waste disposed of, exit, and other relevant information at FSTP decoupled from the FSM module.

## Release Highlights

* Assignment of multiple service requests to one vehicle.
* Logging of all vehicles utilising the faecal sludge treatment Plant (FSTP) in addition to vehicles servicing requests from FSM module.

## **Release Features**

| Features                                                         | Description                                                                          |
| ---------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| Unrestricted assignment of service requests to a single vehicle. | Unrestricted service request assignment in the urban local body (ULB) employee flow. |
|                                                                  | Unrestricted service request assignment in the DSO flow.                             |
| Vehicle logging at FSTP decoupled from the FSM module.           | FSM decoupled from FSTPO UI desktop view.                                            |
|                                                                  | FSM decoupled from FSTPO UI mobile view.                                             |
| Other                                                            | Photograph and attachment view in the application of the ULB employee UI.            |

## **Enhancements** <a href="#enhancements" id="enhancements"></a>

| Features                                                         | Description                                                                                                                                                                                                                                                                                                                                   |
| ---------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Unrestricted assignment of service requests to a single vehicle. | ULB employee flow.                                                                                                                                                                                                                                                                                                                            |
|                                                                  | Multiple service requests assignment to same DSO.                                                                                                                                                                                                                                                                                             |
|                                                                  | Multiple service requests assignment to the same vehicle.                                                                                                                                                                                                                                                                                     |
|                                                                  | Capability to close multiple service requests assigned to the same vehicle in a randomised order.                                                                                                                                                                                                                                             |
| Vehicle logging at FSTP decoupled from FSM module.               | <p>Logging the service request the vehicle is fulfilling from the FSM module in TPMS.</p><p>Vehicle logs will include the following:</p><ol><li>In and out time</li><li>Waste deposited</li><li>Additional information</li><li>Attachment</li></ol>                                                                                           |
|                                                                  | <p>Logging the service request the vehicle is fulfilling is made outside the FSM module in TPMS. Vehicle logs will include the following: </p><ol><li>Vehicle number</li><li>DSO name</li><li>Locality the vehicle is servicing</li><li>In and out time </li><li>Waste deposited</li><li>Additional information</li><li>Attachments</li></ol> |
| Other                                                            | <ol><li>Display of photographs added by ULB employee/DSO while closing request in the application in the ULB interface.</li><li>Date range search of applications.</li></ol>                                                                                                                                                                  |

## Upcoming Release Features <a href="#upcoming-release-features" id="upcoming-release-features"></a>

* FSM V1.2.2: Advance balance payment model.
* FSM V1.2.2: UI for vehicle, vendor and driver changes.
* Urban and rural convergence.
* FSM UX/UI redesign.
* FSM dashboards.

### Note:&#x20;

* Vehicle logs captured at FSTP for service requests outside of FSM module vehicles will not be reflected in the current dashboard and will be incorporated in the FSM Dashboards release.
* During the updation of multiple trips for different service requests, the system cannot perform this activity within seconds and the user may encounter an error. This will be resolved if they refresh and try to update the trips again.

## Reference document links

| Document links                                                                                                                  | Description                                                                                                                                                                             |
| ------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [FSTP user manual](../../products/faecal-sludge-management-fsm/fsm-user-manual/septage-treatment-plant-operator-user-manual.md) | Revamp of the FSTP UI: This will now act as a standalone module where vehicles entering the FSTP can be logged into the system irrespective of servicing a request from the FSM module. |
| [ULB employee user manual](../../products/faecal-sludge-management-fsm/fsm-user-manual/fsm-employee-user-manual.md)             | The overall process remains the same. We now have the option to open multiple applications and assign the same vehicle to them.                                                         |
|                                                                                                                                 |                                                                                                                                                                                         |



[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)](http://creativecommons.org/licenses/by/4.0/)_All content on this page by_ [_eGov Foundation_](https://egov.org.in/) _is licensed under a_ [_Creative Commons Attribution 4.0 International License_](http://creativecommons.org/licenses/by/4.0/)_._
