# High Level Design

Overview

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

#### 1.1 Design guidelines

Tech design for Tracking service addresses following key design goals. These goals are derived from DIGIT’s view of how a service should evolve and also the constraints arising from the usage of client side application.

1. Client side devices may have network bandwidth constraints, hence the communication between client and Tracking service should be optimized on data.
2. Tracking service should be generic enough to handle any kind of citizen services that involve movement of assets or service delivery by an operator on move. Type of service being rendered decides the monitoring rules (alerts, notifications) that are applied to the trip.
3. Within the DIGIT platform, event based models processing should be used so that newer applications can be plugged in by consuming the event messages.



### Tech use cases

#### Key terms

| Term                    | Definition                                                                                                                                                                                                                         |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Actual route            | Route recorded by the tracking device. This can be different from the designated route. It is not created upfront.                                                                                                                 |
| Designated route        | Pre-designated route to be taken by the person/asset.                                                                                                                                                                              |
| Tracking service        | A software component that stores data related to a trip, applies rules to identify anomalies and notifications.                                                                                                                    |
| Operator                | A user responsible for delivering the service. For example, a PHC staff member doing a door to door survey to check for health details of citizens in a particular area.                                                           |
| Point of interest (POI) | A place on map that is of interest during service delivery. It consists of the geo location, name and additional tags. For example, a legal dumpyard for fecal sludge or customer location where a service has to be delivered..   |
| Polygon                 | This is a type of POI which is formed on the basis of multiple geo-coordinates. It helps in identifying large areas on a map, like an illegal dump yard or a cluster of homes and check the trip progress w.r.t to the polygon.    |
| Supervisor              | A user with additional responsibilities like creation of a trip, registering points of interest.                                                                                                                                   |
| Trip                    | Assignment of a designated route to an operator forms a trip. This is the actual work done by the operator. Monitoring of distance covered, route taken, anomalies, service delivery and payment are linked to completion of trip. |



#### Use cases 

| Use Case | Use cases for the backend service                                                                                                                                         | Triggered by       |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------ |
| UC 1     | Trip management                                                                                                                                                           |                    |
| UC 1.1   | Create a new trip based on citizen service, ULB, operator id, starting location, ending location, designated route (refer UC 2), timestamp and other relevant information | Supervisor         |
| UC 1.2   | Start an assigned trip                                                                                                                                                    | Operator           |
| UC 1.3   | Process continuous updates on geo location of the operator assigned to a trip                                                                                             | User app           |
| UC 1.4   | \[Offline mode] Process the bulk updates related to geo location and timestamps related to operator movement                                                              | User app           |
| UC 1.5   | End a trip automatically once the operator reaches the destination. Supervisor can do a manual override                                                                   | System, Supervisor |
| UC 1.6   | Search for a trip based on trip id, ULB, service, operator, geo codes and other relevant information                                                                      | Supervisor         |
| UC 2     | Citizen service master configuration                                                                                                                                      |                    |
| UC 2.1   | Create designated route for a trip based on points of interest (refer UC 3), ULB and type of service                                                                      | Supervisor         |
| UC 2.2   | Search for designated routes                                                                                                                                              | Supervisor         |
| UC 2.3   | Update designated route status to active or inactive                                                                                                                      | Supervisor         |
| UC 2.4   | Register a new operator                                                                                                                                                   | Supervisor         |
| UC 3     | Points of interests and Geofencing                                                                                                                                        |                    |
| UC 3.1   | Create points of interests based of LatLong coordinates                                                                                                                   | Supervisor         |
| UC 3.2   | Create polygon based geofence using multiple sets of LatLong coordinates                                                                                                  | Supervisor         |
| UC 3.3   | Associate points of interest and geofences with various tags like pickup points, legal dumpyards, illegal dump yards and so on                                            | Supervisor         |
| UC 3.4   | Search for the existing points of interest, geo fences and the associated tags                                                                                            | Supervisor         |
| UC 3.5   | Update geo points status to active or inactive                                                                                                                            | Supervisor         |
| UC 4     | Watcher and alerts                                                                                                                                                        |                    |
| UC 4.1   | Identify trip anomalies based on geo tags assigned in UC 3.                                                                                                               | System             |
| UC 4.2   | Identify time based anomalies in a trip based on specific preconfigured rules                                                                                             | System             |
| UC 4.3   | Generate alerts (email, SMS) on detection of anomalies                                                                                                                    | System             |
| UC 4.4   | Search for anomalies based on trip id, geo location, ULB id and so on                                                                                                     | Supervisor         |
| UC 4.5   | End trip if it goes beyond a time limit                                                                                                                                   | System             |

\


### 3. Tech design

#### 3.1 Components

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



#### API specs

Tracking service has APIs to manage the 3 core entities - Point of interest (POI), Designated route and Trip. Basic details of these APIs are mentioned below.&#x20;

Following are the list of APIs this service will support. For details of the request and response message structure, please refer to Appendix A in this document.

* Point of interest
  * /poi/\_create
  * /poi/\_update
  * /poi/\_search
* Designated route
  * /designated\_route/\_create
  * /designated\_route/\_update
  * /designated\_route/\_search
* Trip
  * /trip/\_create
  * /trip/\_update
  * /trip/\_progress
  * /trip/\_search

#### 3.3 Event entity

Event entity has a generic format. Structure of the event is listed below.

| Field          | Description                                                                                                                                                                                                                                                                                      |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| id             | GUID to uniquely identify an event                                                                                                                                                                                                                                                               |
| type           | Event type indicates the nature of the event and helps consuming applications identify if/how to process it. For example - tracking service generates an event with type “LocationUpdate”. Similarly, trip monitoring service generated events will have the type “TripAnomaly”, “TripCompleted” |
| creation\_time | Time at which the event is created                                                                                                                                                                                                                                                               |
| source         | Application that published this event. This can be a short code / acronym of the source application                                                                                                                                                                                              |
| data           | This is a JSON object. For example, “LocationUpdate” events will have fields like current\_location and received\_time.                                                                                                                                                                          |



Service design

* Tracking service \[New]&#x20;
  * A gateway service for client endpoints. POI, Designated routes and Trips are managed by this service
  * Location updates received from client are published as events in a standard format
* Trip monitoring module \[New]
  * Consumes the location update events received from client (published by Tracking service)
  * Persists the location data, identifies anomalies, marks trips as complete based on rules
  * Events that should be notified are published by this service
* Notification module \[New]
  * Consumes the notification events
  * Fetches contact information from DIGIT User Service and sends SMS in predefined format
* Tracking data store \[New]
  * Data store for POIs, routes, trips, location updates and notifications
* DIGIT user service \[Existing]
  * Provides contact information of the user to which notification will have to be sent
  * User can be a supervisor or operator

<figure><img src="../../../../.gitbook/assets/image (280).png" alt=""><figcaption><p>Process Flow</p></figcaption></figure>

\
