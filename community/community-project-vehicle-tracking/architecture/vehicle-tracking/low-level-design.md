# Low Level Design

### Overview

Urban Local Bodies (ULB) and other government agencies provide citizen centric services. Some of these services involve/require movement of people or assets(eg : vehicle, equipment etc). Below is a sample list of such services:

* Pickup of Fecal sludge from a citizen’s premises and offloading at a designated place
* Garbage pickup truck visits multiple collection points and deposits the load at a designated waste segregation yard
* ULB assigns a drinking water tanker to supply water to schools in a particular area. The water tanker visits the assigned schools and supplies the required amount of water.
* Fumigation to contain mosquitoes spread involves an operator moving in a 2-wheeler from one street to another.
* Medicines have to be moved from district headquarters to mandal level villages.



Key challenges in the above scenarios are :&#x20;

1. Ensuring the vehicle / person took the designated route&#x20;
2. Checking if all pickup/dropoff locations are visited&#x20;
3. Monitoring if a restricted location is visited&#x20;
4. Tracking of live location&#x20;

Challenges listed above are solved with a new tracking service component. This document captures the technical design of such a tracking service. For functional use cases related to a specific citizen service (Fecal Sludge Management), please refer to [this doc](https://docs.google.com/document/d/139o9uT-7lR3L9TP8nwKKdwKtwxfKPUlcD-vrRCNRlsU/edit#heading=h.4xc9v8n4mj).



#### Design guidelines

Tech design for Tracking service addresses following key design goals. These goals are derived from DIGIT’s view of how a service should evolve and also the constraints arising from the usage of client side application.

\


1. Client side devices may have network bandwidth constraints, hence the communication between client and Tracking service should be optimized on data.
2. Tracking service should be generic enough to handle any kind of citizen services that involve movement of assets or service delivery by an operator on move. Type of service being rendered decides the monitoring rules (alerts, notifications) that are applied to the trip.
3. Within the DIGIT platform, event based models processing should be used so that newer applications can be plugged in by consuming the event messages.

\


### Tech design

#### Components

Below is the list of entities, actors and tech components involved in tracking service.

Entities

* Point of Interest (POI) - Latitude, longitude coordinates of various locations. Types of locations include citizen pickup point, intermediate points, destination location, polygons to identify larger areas and tags to identify anomalies (like illegal dump yards).
* Designated route - A sequence of POIs which indicate the route an operator should take.
* Trip - Created for each service delivery involving an operator. It is either created based on request or through an automatic scheduler. Trip is made up of operator details and designated routes. Actual route taken by the operator is also associated with the trip.

Actors

* Supervisor - Individual is responsible for making configuration level changes. These can be two separate roles or just one
* Operator - Travels from source to destination of a trip as part of service delivery.
* System - Tracking service has the intelligence to take some actions on its own.

Tech components&#x20;

* Mobile App - User facing application to manage routes, trips and POIs
* Tracking service - Stores entities, applies automated rules and generates alerts.

\
Low level design

**Tracking service**



Controller classes

* ConfigController, PoiController, RouteController, TripController

Service classes

* ConfigService, POIService, RouteService, TripAlertService, TripService

Data access

* ConfigDao, PoiDao, RouteDao, TripAlertDao, TripDao, TripProgressDao

Service access

* POISao, TripSao

Model

* FsmApplication, FsmVehicleTrip, TripAlert

**Trip monitoring module**

Monitoring logic

\
**Trip data store**

Database schema

![](https://lh7-us.googleusercontent.com/OfXKaYJ2rTfneZQ114ODl-m-33VSXln\_Fy7PDYwE4EMBZh3bPJ2QPcSSU7pYi\_EkwutGJ1ecrZvo\_JBj38Mgj1Ovd7K\_v9zGYbW04YcQHEa11dTD6bBwG0qUNBLJ6xjp3W-NKebeG9xZ6XS2gJDRXP8)



[PlanUML link with source](https://www.plantuml.com/plantuml/uml/ZLBDYjim4BxhAKIEXhn0MPPTsh0OKYSallHKL6lOJAiV8OrAmsxVlPApHd5id5vq6Cqtty\_CKo3XAMh5mYyqJdYXkK83T7R0hQUJPIUKm3lqdGB6m13IcQ\_skth5trY5ad\_Y17-8Fpp4YFBnaQtNh5As4uJMD4B3HmEh4XN5KFh1H9twgymrhGe5dahvPx0cbsC0Nm-ah78sO2RQMpIvE-bgsbBUeicZjtMpERQ7kdcvHgZpgpKzPlljPTUmlyNUmKQ25LzmsEUMM2UV5HWvMpV\_aqLo0Lw3H46GfeHx0LnfRZswfPtux2aZ5uLP1rwGzLFYnFiRE\_XivLqROv7b79xpJgUURapilNtr4CAI6KfzCrxS1\_G0pde2sQA6qbGVTz-\_FBURjlwwISrZaVEND0nS7AG5TIV8Mx-LD3QtlOxXSbrTIVFY2qd1p7AFb\_3RiuFL3Ovdu7Y9KVqOdGXBPlZx-tfjttX\_sgn\_Xr8EdUMd5CeMMA4U0qPkXfz4DF-H8Ld6BCKJ61cr-WS0)



Rule management schema

![](https://lh7-us.googleusercontent.com/WG3\_TTmDoWf1j3KLI2E3J8fbcy-BrVcJYYTZgjtTEY-VE6GIwWPdg6rlalViAmm0a4hbELV1EUi-zYGCKKwq1DHx4WdrZUw4hLmaubKiyM29hmK6wPP-PaO7utPytIwSbu3wN3zM2PJUXvUmzUr9Gkw)\


[PlantUML link with source](https://www.plantuml.com/plantuml/uml/RO\_1QiD034Jl-WhXey4\_K4m8zDH3Bsr-OF4AHtIjNMHjgKdwxxNQqgHERcAOcQVPpnRKwfHWVcCfGSE4YOLiAOHPxPZXo95mO1qI0P0OsuBDIqtKu0bQNO\_7l3eUqEZ3eEkWZJGFoiKuow-CqF9KaXl\_bC\_\_RS-X59QnGM\_bkDfOZ4PIxFjGBNSZ2MamYhkTKpPaHnX947kA5sKcVUVXshR57fJBzn1RZqkqxsjb9zqTkDdYdTw5vtFNvHDUpRdHdGUlFsyTbd8tuvwR3En9OftI5m00)



**3.4.6 Use case to API mapping (with FSM integration)**

Vehicle tracking system (VTS) and FMS are the two systems that provide these APIs

Driver use cases (mobile app)

![](https://lh7-us.googleusercontent.com/p6nDG2sGhJCdaIsCGGtGYVDKpOQOrfwBQpCOAnnuFJcyMUEjZHN3hcjeGDGJuF1MIWt8gU6xM4opvUxKyZVkNXNwvUChsTt97PED-MB45Rzu6gnZyh8UBeLpVO57EYjfmSMxGKYQR97I8I0MIPC8H7c)

[PlantUML link](https://www.plantuml.com/plantuml/uml/dL9DZzCm4BtdLunwu5HlilrGQQM51QqgSIW7kk9K2Jds91cHs9OzYSI\_nsu8jAk2W9CzdkStRsRUOs3fkU\_QJ2gs7hId0JraBhwI8YSDWtGEP83PmPRKOWfdL\_dFpyUNyTFxyuzu0orPbZBWzP\_zuNX6f3EW7qX5G5PxspkOFL5mhVm6xCa580FTHUKV2iMR5C8ESkae7vPv0kTV0aglcYob8YBLtu7ikM7x5SryQe\_q71XD4a8wIwW8Jb9si4TMJQ9kIKacQy3qNOa-d4nbFN23lqWoOnd1Kztm3Xfc5tPvtXkg2BNGEDnfgedlhA\_pAdJvS3\_fUpiM\_w0VN7adEqySf3-PLoDpV5QgMcsthvN0ZQp42bTQoEsc4kkjMj-NPRLQu\_gMxZG4qCYIsW2LZPpSuArk\_a7wW0sf5iS1N\_GGkMztuR52RnH-jE7XljY8\_V4W5iLYAOgjM2n4KHJBnNB-kyngwcjSRwgQzZLUZEnm3e4bzs5-CcVpGessjMDxyKrZO3Bdw38pMM8SSIJ-XC5P4p13etywxvW8nr9\_ijs5loQrPzE\_uBBk\_wakjdl5-fm8dRUrnn2WTreoXjbV2NhNekVa3bHf8hC9UVjJzXYFlck\_0m00)

### Appendix

Appendix A - REST APIs for client applications

Note -

(i) Additional attributes will be added to cater to integration with other entities within the DIGIT ecosystem. For example, Tenant Id, User Id, ULB id/name, auth token etc &#x20;

\


(ii) All API requests will include timestamps and other information necessary for auditing.

a.1. /poi/\_create (Implemented)

Request message

| Name                         | Type             | Mandatory? | Comments                                                                                                                                                             |
| ---------------------------- | ---------------- | ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| locationName                 | Text             | Yes        | <p><br></p>                                                                                                                                                          |
| locationDetails              | Array            | Yes        | List of locations that are part of a POI. This can be a single LatLong or group of LatLongs (line, polygon)                                                          |
| locationDetails -> lattitude | Decimal          | Yes        | <p><br></p>                                                                                                                                                          |
| locationDetails -> longitude | Decimal          | Yes        | <p><br></p>                                                                                                                                                          |
| alert                        | Array of Strings | No         | One or more alert codes can be mapped to the point of interest. This is optional and can be set only in cases where the POI is related to some illegal dump yard etc |
| userId                       | Text             | Yes        | DIGIT user id of the individual performing the create operation                                                                                                      |



Response message

| Name            | Type | Mandatory? | Comments                           |
| --------------- | ---- | ---------- | ---------------------------------- |
| responseCode    | Text | Yes        | <p><br></p>                        |
| responseMessage | Text | Yes        | <p><br></p>                        |
| id              | Text | No         | GUID of the POI created on success |



a.2. /poi/\_update (Implemented)

\


Request

| Name         | Type | Mandatory? | Comments                                                        |
| ------------ | ---- | ---------- | --------------------------------------------------------------- |
| id           | Text | Yes        | POI to be updated                                               |
| status       | Text | No         | Can be set to active or Inactive                                |
| locationName | Text | No         | <p><br></p>                                                     |
| userId       | Text | No         | DIGIT user id of the individual performing the create operation |



Response

| Name            | Type    | Mandatory? | Comments                |
| --------------- | ------- | ---------- | ----------------------- |
| responseCode    | Integer | Yes        | <p><br></p>             |
| responseMessage | Text    | Yes        | <p><br></p>             |
| id              | Text    | No         | GUID of the POI updated |

\


a.3. /poi/\_search

\*\* Additional search filters will be added to restrict the results to ULB, user role and other related restrictions.\


Request

| Name                | Type    | Mandatory? | Comments    |
| ------------------- | ------- | ---------- | ----------- |
| poi\_id             | Text    | No         | <p><br></p> |
| poi\_status         | Text    | No         | <p><br></p> |
| location\_name      | Text    | No         | <p><br></p> |
| location\_lattitude | Decimal | No         | <p><br></p> |
| location\_longitude | Decimal | No         | <p><br></p> |
| geofence\_radius    | Integer | No         | <p><br></p> |
| illegal\_dumpyard   | Boolean | No         | <p><br></p> |



Response

An array of below objects will be returned for the POIs matching with search criteria.

| Name                                     | Type    | Mandatory? | Comments    |
| ---------------------------------------- | ------- | ---------- | ----------- |
| poi\_id                                  | Text    | Yes        | <p><br></p> |
| poi\_status                              | Text    | Yes        | <p><br></p> |
| location\_name                           | Text    | Yes        | <p><br></p> |
| location\_details                        | Array   | Yes        | <p><br></p> |
| location\_details -> location\_lattitude | Decimal | Yes        | <p><br></p> |
| location\_details -> location\_longitude | Decimal | Yes        | <p><br></p> |
| location\_details -> geofence\_radius    | Integer | Yes        | <p><br></p> |
| location\_details -> illegal\_dumpyard   | Boolean | Yes        | <p><br></p> |

\


b.1. /designated\_route/\_create

Request

| Name                               | Type          | Mandatory? | Comments                                                                                           |
| ---------------------------------- | ------------- | ---------- | -------------------------------------------------------------------------------------------------- |
| designated\_route\_name            | Text          | Yes        | <p><br></p>                                                                                        |
| designated\_route\_status          | Boolean       | No         | <p>This will be used to inactivate a route when needed</p><p><br></p><p>Default value is true.</p> |
| start\_poi\_id                     | Text          | Yes        | <p><br></p>                                                                                        |
| intermediate\_poi\_id              | Array \<Text> | No         | Defaults to null                                                                                   |
| end\_poi\_id                       | Text          | Yes        | <p><br></p>                                                                                        |
| designated\_route\_traversal\_time | Integer       | No         | <p>Estimated time to complete a trip on this route.</p><p><br></p><p>Default value is 0.</p>       |



Response message

| Name                  | Type    | Mandatory? | Comments                                        |
| --------------------- | ------- | ---------- | ----------------------------------------------- |
| response\_code        | Numeric | Yes        | <p><br></p>                                     |
| response\_message     | Text    | Yes        | <p><br></p>                                     |
| designated\_route\_id | Text    | No         | GUID of the Designated route created on success |

\


b.2. /designated\_route/\_update

Request

| Name                               | Type          | Mandatory? | Comments    |
| ---------------------------------- | ------------- | ---------- | ----------- |
| designated\_route\_id              | Text          | Yes        | <p><br></p> |
| designated\_route\_name            | Text          | No         | <p><br></p> |
| designated\_route\_status          | Boolean       | No         | <p><br></p> |
| start\_poi\_id                     | Text          | No         | <p><br></p> |
| intermediate\_poi\_id              | Array \<Text> | No         | <p><br></p> |
| end\_poi\_id                       | Text          | No         | <p><br></p> |
| designated\_route\_traversal\_time | Integer       | No         | <p><br></p> |

\


Response

| Name                  | Type    | Mandatory? | Comments                             |
| --------------------- | ------- | ---------- | ------------------------------------ |
| response\_code        | Integer | Yes        | <p><br></p>                          |
| response\_message     | Text    | Yes        | <p><br></p>                          |
| designated\_route\_id | Text    | No         | GUID of the Designated route updated |



b.3. /designated\_route/\_search

\*\* Additional search filters will be added to restrict the results to ULB, user role and other related restrictions.



Request

| Name                      | Type    | Mandatory? | Comments    |
| ------------------------- | ------- | ---------- | ----------- |
| designated\_route\_id     | Text    | No         | <p><br></p> |
| designated\_route\_name   | Text    | No         | <p><br></p> |
| designated\_route\_status | Boolean | No         | <p><br></p> |
| start\_poi\_code          | Text    | No         | <p><br></p> |
| intermediate\_poi\_code   | Text    | No         | <p><br></p> |
| end\_poi\_code            | Text    | No         | <p><br></p> |
| start\_poi\_name          | Text    | No         | <p><br></p> |
| intermediate\_poi\_name   | Text    | No         | <p><br></p> |
| end\_poi\_name            | Text    | No         | <p><br></p> |



Response

An array of below objects will be returned for the designated routes matching with search criteria.

| Name                               | Type    | Mandatory? | Comments    |
| ---------------------------------- | ------- | ---------- | ----------- |
| designated\_route\_id              | Text    | Yes        | <p><br></p> |
| designated\_route\_name            | Text    | Yes        | <p><br></p> |
| designated\_route\_status          | Boolean | Yes        | <p><br></p> |
| start\_poi\_code                   | Text    | Yes        | <p><br></p> |
| intermediate\_poi\_codes           | Array   | No         | <p><br></p> |
| end\_poi\_code                     | Text    | Yes        | <p><br></p> |
| start\_poi\_name                   | Text    | Yes        | <p><br></p> |
| intermediate\_poi\_names           | Array   | No         | <p><br></p> |
| end\_poi\_name                     | Text    | Yes        | <p><br></p> |
| designated\_route\_traversal\_time | Integer | No         | <p><br></p> |

\
\


c.1. /trip/\_create (Implemented)

Request\


| Name                      | Type   | Mandatory   | Comments                                                                        |
| ------------------------- | ------ | ----------- | ------------------------------------------------------------------------------- |
| routeId                   | Text   | Yes         | Predefined route id, which has the list of POIs for that the trip should follow |
| serviceCode               | Text   | Yes         | Type of service the trip is performing                                          |
| status                    | Text   | Yes         | Client passes “created” value initially                                         |
| operator                  | Object | <p><br></p> | <p><br></p>                                                                     |
| operator -> id            | Text   | No          | DIGIT user id of the operator delivering this service                           |
| operator -> name          | Text   | No          | <p><br></p>                                                                     |
| operator -> email         | Text   | No          | <p><br></p>                                                                     |
| operator -> contactNumber | Text   | No          | <p><br></p>                                                                     |
| operator -> vehicleNumber | Text   | No          | <p><br></p>                                                                     |
| plannedStartTime          | Text   | No          | <p><br></p>                                                                     |
| plannedEndTime            | Text   | No          | <p><br></p>                                                                     |
| userId                    | Text   | Yes         | DIGIT user id of the person performing this create activity                     |



Response

| Name            | Type | Mandatory? | Comments                            |
| --------------- | ---- | ---------- | ----------------------------------- |
| responseCode    | Text | Yes        | <p><br></p>                         |
| responseMessage | Text | Yes        | <p><br></p>                         |
| id              | Text | No         | GUID of the trip created on success |



c.2. /trip/\_update

Request\


| Name                        | Type | Mandatory | Comments    |
| --------------------------- | ---- | --------- | ----------- |
| trip\_id                    | Text | Yes       | <p><br></p> |
| trip\_designated\_route\_id | Text | No        | <p><br></p> |
| trip\_expected\_start\_time | Text | No        | <p><br></p> |
| trip\_expected\_end\_time   | Text | No        | <p><br></p> |
| trip\_current\_status       | Text | Yes       | <p><br></p> |



Response

| Name              | Type    | Mandatory? | Comments    |
| ----------------- | ------- | ---------- | ----------- |
| response\_code    | Integer | Yes        | <p><br></p> |
| response\_message | Text    | Yes        | <p><br></p> |

\


c.3. /trip/\_progress

Request

| Name                                     | Type    | Mandatory | Comments                                                                                                 |
| ---------------------------------------- | ------- | --------- | -------------------------------------------------------------------------------------------------------- |
| trip\_id                                 | Text    | Yes       | <p><br></p>                                                                                              |
| location\_details                        | Array   | Yes       | Array is used to support bulk updates in case the device comes online after being offline during a trip. |
| location\_details -> location\_lattitude | Decimal | Yes       | <p><br></p>                                                                                              |
| location\_details -> location\_longitude | Decimal | Yes       | <p><br></p>                                                                                              |
| location\_details -> progress\_timestamp | Text    | Yes       | <p><br></p>                                                                                              |

\


Response

| Name              | Type    | Mandatory? | Comments    |
| ----------------- | ------- | ---------- | ----------- |
| response\_code    | Integer | Yes        | <p><br></p> |
| response\_message | Text    | Yes        | <p><br></p> |

\


c.4. /trip/\_search

\*\* Additional search filters will be added to restrict the results to ULB, user role and other related restrictions.

Request

| Name       | Type | Mandatory | Comments                                          |
| ---------- | ---- | --------- | ------------------------------------------------- |
| operatorId | Text | No        | DIGIT id of the person to whom a trip is assigned |
| tripName   | Text | No        | Partial name search is supported                  |
| status     | Text | No        | <p><br></p>                                       |
| userId     | Text | No        | DIGIT id of the person who created the trip       |

\


Response

Array of trips is returned

| Name                      | Type   | Mandatory? | Comments                                                                                         |
| ------------------------- | ------ | ---------- | ------------------------------------------------------------------------------------------------ |
| id                        | Text   | Yes        | Trip id                                                                                          |
| routeId                   | Text   | No         | <p><br></p>                                                                                      |
| serviceCode               | Text   | No         | <p><br></p>                                                                                      |
| status                    | Text   | No         | <p><br></p>                                                                                      |
| operator                  | Object | No         | <p><br></p>                                                                                      |
| operator -> id            | Text   | No         | DIGIT user id of the operator delivering this service                                            |
| operator -> name          | Text   | No         | <p><br></p>                                                                                      |
| operator -> email         | Text   | No         | <p><br></p>                                                                                      |
| operator -> contactNumber | Text   | No         | <p><br></p>                                                                                      |
| operator -> vehicleNumber | Text   | No         | <p><br></p>                                                                                      |
| plannedStartTime          | Text   | No         | <p><br></p>                                                                                      |
| plannedEndTime            | Text   | No         | <p><br></p>                                                                                      |
| userId                    | Text   | No         | DIGIT user id of the person performing this create activity                                      |
| actualStartTime           | Text   | No         | <p><br></p>                                                                                      |
| actualEndTime             | Text   | No         | <p><br></p>                                                                                      |
| locationAlerts            | Text   | No         | Alerts are assigned by backend service, in case the operator takes a path that triggers an alert |

\


c.5. /trip/\_search/{tripId} (Implemented)

Request

| Name | Type | Mandatory | Comments                   |
| ---- | ---- | --------- | -------------------------- |
| id   | Text | Yes       | Trip id to be searched for |

\


#### Appendix B - Event data examples



Event type = LocationUpdate

Event data

{

“latitude” :&#x20;

“longitude” :&#x20;

“update\_time” :&#x20;

“trip\_id” :&#x20;

}

\


Event type = TripAnomaly

Event data

{

“anomaly\_poi\_id” :&#x20;

“duration\_at\_poi” :&#x20;

“update\_time” :&#x20;

“trip\_id” :&#x20;

}

\


Event type = TripComplete

Event data

{

“update\_time” :

“completion\_time” : &#x20;

“trip\_id” :&#x20;

}\


#### Appendix C - API to Database mapping

Mobile app\


| Use case                         | VTS database fields                                                                                                                                                                                                                            |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| User login functionality         | VTS is not used. DIGIT user login API is invoked                                                                                                                                                                                               |
| List of trips assigned to driver | <p>VTS API is called but all data is retrieved from FSM vehicle trip APIs.</p><p><br></p><p>Additional details stored in VTS db:</p><p>Trip.status</p><p>Trip.id</p><p>Trip.routeId</p><p>Route.Id</p><p>Route.startPoi</p><p>Route.endPoi</p> |
| Trip details                     | Trip details are fetched from FSM vehicle trip API. VTS does not store trip details in its db                                                                                                                                                  |
| Trip progress once vehicle moves | <p>VTS db stores trip progress information:</p><p>TripProgress.id</p><p>TripProgress.tripId</p><p>TripProgress.progressReportedTime</p><p>TripProgress.userId</p><p>TripProgress.positionPoint</p><p>TripProgress.progressTime</p><p><br></p>  |
| Illegal dumpyard creation        | <p>Illegal dumpyard details are stored in VTS db:</p><p>POI.id</p><p>POI.locatioName</p><p>POI.type</p><p>POI.positionPoint</p><p>POI.positionLine</p><p>POI.positionPolygon</p><p>POI.alert</p>                                               |



FSM portal

| Use case                  | VTS database fields                                                                                                                                                                                                               |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Trip details              | <p>Fields in VTS db:</p><p>Trip.id</p><p>Trip.status</p><p>Trip.actualStartTime</p><p>Trip.actualEndTime</p><p>TripAlert.id</p><p>TripAlert.tripId</p><p>TripAlert.alert</p><p>TripAlert.alertDateTime</p>                        |
| Trip actual route details | <p>Fields in VTS db:</p><p><br></p><p>TripProgress.id</p><p>TripProgress.tripId</p><p>TripProgress.progressReportedTime</p><p>TripProgress.userId</p><p>TripProgress.positionPoint</p><p>TripProgress.progressTime</p><p><br></p> |

\
\
