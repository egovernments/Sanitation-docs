# Product Requirement Document (PRD)

## Background

To ensure proper disposal of waste, the Swachh Bharat Mission has approved the building of deep row entrenchments for the disposal of sludge for upto three years. With this mandate, there are approximately 10k+ deep row entrenchments that now exist, and are usually unmanned. To confirm disposal to these legal unmanned dumping sites, there is a need for automated verification of disposal at these sites.&#x20;

## Introduction

India’s FSM ecosystem is made of highly interdependent parts, across the value chain of generation, containment, transport, treatment, and disposal/reuse. This means that there are different actors at each stage of the value chain whose behaviours and business models affect how well the next stage functions, creating a complex mesh of constraints that affect the effective functioning of the sanitation service delivery.

While the linear value chain gives a lucid frame to understand the ideal flow of faecal sludge, there are various points of friction between stakeholders that currently undermine the effectiveness of the sanitation value chain. Illegal dumping remains a challenge in regard to the waste value chain.

We want to improve the verifiability of the transport information on faecal sludge through the implementation of vehicle tracking to drive the following benefits:&#x20;

1. Improved verification: The service enhances the verification process of the faecal sludge disposal. By accurately tracking the movement of vehicles carrying the sludge, it ensures that the sludge reaches its designated disposal site, providing transparency and accountability in the disposal process.
2. Removal of manual intervention to confirm disposal: The implementation of the vehicle tracking service removes the need for manual intervention to confirm the disposal of faecal sludge. Traditionally, manual methods involve physical confirmation by the treatment plant operator.
3. Identification of Illegal dumping: By closely monitoring the transportation of faecal sludge from the point of containment to disposal, the vehicle tracking service helps in minimising disposal in illegal sites. It facilitates identifying potential inefficiencies, route deviations, or incidents, allowing for prompt corrective actions.

The vehicle tracking service within DIGIT aims to capture real-time spatial data by tracking vehicles from their starting coordinates (longitude and latitude) to their destination point. This service helps in enhancing the credibility of service delivery by providing a reliable means to track and verify the transportation process. The vehicle tracking service can be seamlessly integrated with various service delivery operations, offering the flexibility to configure it for different purposes.&#x20;

**Future Use Cases**\
\
Apart from the benefits mentioned above, the vehicle tracking functionality can be used to  implement the following use cases in the future:&#x20;

1. Proximity-based discovery: By helping service providers or customers identify the nearest available vehicles for transportation or disposal purposes.
2. Distance-based pricing: Leveraging the tracking data, the vehicle tracking service can support distance-based pricing models.
3. Understanding capacity and capacity utilisation of vehicles: By analysing the metrics around transportation such as average trip time, average distance traveled, number of trips completed per day, idle time, etc., one can arrive at the utilised and available capacity for transportation. Further, these can be used to arrive at the profitability of vendors in transportation.&#x20;

## &#x20;Features

1. Assigning drivers to the trips: The ULB personnel can assign a driver when assigning the vehicle for a particular trip.
2. Employee form has been enhanced to add geo-location.
3. A standalone mobile application for the drivers: Drivers will be able to see the trips assigned to them with start and end trips provided. With this functionality, the driver can start the trip after reaching the citizen’s location, provide service, and end the trip after reaching the FSTP.
4. Enhancement to the application by introducing end trip: The vehicle tracking service can be leveraged to automate certain aspects of the disposal process.
   1. System Verified: The trip is closed automatically if the vehicle is near the geo-fenced area of the FSTP. In this case, the end type is updated as system verified.
   2. FSTP Verified: If the driver concludes the trip at a location that is not necessarily close to the FSTP, the FSTP staff will need to manually finalise the trip. In this case, the end type is updated as FSTP verified.
5. Defining illegal dumping spots: The vehicle tracking service can help the ULB personnel to identify and input these locations into the system. If a driver stops at one of these spots for an extended period , the system triggers an alert to notify the ULB of potential illegal dumping activity.
6. Alerts: On events where local authorities should be informed:&#x20;

&#x20;      \- Longer waiting of vehicles near farm lands, water sources, etc., could be a possible indication of illegal disposal.

&#x20;      \- The popular open disposal spots as generally defined as prohibited zones and any desludging vehicles around those areas are also an indication of open disposal.

## How Vehicle Tracking Will Be Integrated With DIGIT FSM:

## Actors

### Current Actors

| Actor                                                                                                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Citizen                                                                                                       | A citizen can request for a desludging operation online. The user can check the status of the application online, make the payment for the service online, and post desludging, they can rate the quality of the service online.                                                                                                                                                                                                                                |
| ULB employee (Can be assigned roles as creator, collector, editor, report viewer, dashboard viewer, or admin) | A ULB official will act as a regulatory and management authority for the entire desludging process. He/she can receive the request from a citizen online or can create a request on behalf of the citizen online. When the request is received, the user can assign a desludging operator for a request. The official can also update the status of the request on behalf of the DSO after the service is completed at the site, and view the relevant reports. |
| Transportation vendors                                                                                        | The transportation vendor will receive the requests assigned to them, and update the status of the transaction after the collection of faecal sludge is complete.                                                                                                                                                                                                                                                                                               |
| Treatment plant operator                                                                                      | This user can view the current demand, that is, the list of planned desludging requests available in the system. He/she can update the vehicle log which enters the FSTP/STP every day.                                                                                                                                                                                                                                                                         |

### Proposed Actors

As per the understanding on the field, collection and transportation services are provided by the sanitation workers (usually a driver plus helper). Given that the driver is operating the vehicle, it makes sense for us to add an additional actor in the workflow:&#x20;

| Actor  | Description                                                  |
| ------ | ------------------------------------------------------------ |
| Driver | A driver is responsible for pickup, and disposal of sludge.  |

## Workflows:

Current workflow (Without vehicle tracking) :&#x20;

![](https://lh7-us.googleusercontent.com/P8AgHtHKYTDKGgO7Z6HGz041-kJuDW2VGKnq0VV1F6aGocPs5AkaJ1IuItcP3Fk2AwxpW0LqIf\_lo9Qu5Tm2CSaQmtwUZ0OaRC651GYyzYZzrbNBfn8j6tampCQ4rwCl-D\_jumyt4VUoX097vCWHJPQ)

Proposed workflow (With vehicle tracking) :&#x20;

![](https://lh7-us.googleusercontent.com/42OnxkvKesQJMWOfAGjrR2FbuvpSdiMepdRiiuxgDUP8oEYlCCxVJdOqt5XzWwDNPZlHRzS3JSUSkJhqVF8GUulSMeyCkrvAUAPUKw\_Y3YHITX-S5WRf7nhyGYGT4Ci6upWg9FplmUEJkMCzJMdvPRs)

## Actions by User Persona

| Persona | Priority | Use Case                                                                                                                                                                   |
| ------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Driver  | P0       | <ul><li>Should be able to start and end the trip.</li></ul>                                                                                                                |
| FSTPO   | P0       | <ul><li>Should be able to view if the vehicle has reached the FSTP or not via the inbox.</li></ul>                                                                         |
| ULB     | P0       | <ul><li>Should be able to view the route followed by the vehicle and stoppage. They should also be able to view metrics such as movement time and stoppage time.</li></ul> |
| ULB     | P0       | <ul><li>Should get alerts for  long stoppages, and stoppages near illegal dumping spots.</li></ul>                                                                         |

**Assign Driver**

The driver will be assigned to a request.

[See flow diagram here](https://www.figma.com/file/9yESIjpkfUqFhDdgVusS5B/DIGIT-Community?type=design\&node-id=693-1553\&mode=design\&t=ugAWoDK2OKpk3l98-0)

**Start and End Trip**

Trips will be started and ended by the driver using a mobile app.

[See flow diagram here\
](https://www.figma.com/file/9yESIjpkfUqFhDdgVusS5B/DIGIT-Community?type=design\&node-id=693-1510\&mode=design\&t=ugAWoDK2OKpk3l98-0)\
**View Trip Details**\
\
ULBs can currently view the applications. This needs to be enhanced with the following:

* Trip details need to be viewable along with status and route of the trip.
* Alerts need to be viewable if there has been an illegal stoppage on the trip.
* The ULB can deep-dive and view the route taken and the number of stops by the vehicle.

[See flow diagram here](https://www.figma.com/file/9yESIjpkfUqFhDdgVusS5B/DIGIT-Community?type=design\&node-id=693-1510\&mode=design\&t=ugAWoDK2OKpk3l98-0)

**Mark Illegal Dumping Zones**

[See flow diagram here](https://www.figma.com/file/9yESIjpkfUqFhDdgVusS5B/DIGIT-Community?type=design\&node-id=700-1593\&mode=design\&t=sJJrKXgKPm639XQi-0)

**Edit Illegal Dumping Zones**

[See flow diagram here](https://www.figma.com/file/9yESIjpkfUqFhDdgVusS5B/DIGIT-Community?type=design\&node-id=700-1617\&mode=design\&t=sJJrKXgKPm639XQi-0)

## Users and Value bundles

<figure><img src="https://lh7-us.googleusercontent.com/U9CwIqiCQo59nsMIlF_lXuyTf7lgj0HrWKAw-sqU93uwFcU5JUK9eUJNAsyFY-aC_bC3Yi9FUkM8CJOwSbN4q-NsRWweJOc_O6xWCTz1HZbiKTfBFM_TW_7G4hLyQSs0piwRbyQ5D_SQyZU5gVnOSdc" alt=""><figcaption></figcaption></figure>

## Assumptions and Validations:

<table data-header-hidden><thead><tr><th width="173.66666666666666"></th><th width="226"></th><th></th></tr></thead><tbody><tr><td>Serial number</td><td>Theme </td><td>Assumption</td></tr><tr><td>1</td><td>Customer persona</td><td>The drivers using the application are not digitally literate and need training before being able to use the application independently.</td></tr><tr><td>2</td><td>Device and services</td><td>The drivers using the mobile application must have internet connection to get the trip details in the application.</td></tr><tr><td>3</td><td>Start trip </td><td>The driver is required to click on “Start Trip” before commencing the desludging service.</td></tr><tr><td>4</td><td>End trip</td><td>The driver is expected to click on "End Trip" upon the completion of the desludging process at the FSTP.</td></tr><tr><td>6</td><td>Geo-tagging precision</td><td>The latitude-longitude added within the system are sufficiently accurate to pinpoint the exact locations.</td></tr><tr><td>9</td><td>Additional fields</td><td>All the non-mandatory fields must be taken care of during implementation. This must be done across all the flows.</td></tr><tr><td>10</td><td>Dropdown</td><td>If the field contains only one value, then it must be auto-populated by the system.</td></tr></tbody></table>

#### 1 . Driver Login

| Field    | Data Type | Data Validation                             | Required (Y/N) | Comments    |
| -------- | --------- | ------------------------------------------- | -------------- | ----------- |
| User Id  | String    | <p>Min Length = 2</p><p>Max Length = 64</p> | Y              | <p><br></p> |
| Password | String    | <p>Min Length = 2</p><p>Max Length = 64</p> | Y              | <p><br></p> |

#### 2. Driver Home & Inbox

| Field            | Data Type | Data Validation | Required (Y/N) | Comments                                                                                                 |
| ---------------- | --------- | --------------- | -------------- | -------------------------------------------------------------------------------------------------------- |
| Start Trip       | Button    | <p><br></p>     | Y              | The "Start Trip" button initiates the tracking and monitoring of the desludging service journey.         |
| Route StartPoi   | Text      | <p><br></p>     | Y              | Captured when the driver starts the trip                                                                 |
| End Trip         | Button    | <p><br></p>     | Y              | The "End Trip" button signifies the completion of the desludging service journey and finalizes tracking. |
| Route EndPoi     | Text      | <p><br></p>     | Y              | Captured when the driver ends the trip                                                                   |
| Name             | Text      | <p><br></p>     | Y              | Auto-generated on the creation of trip                                                                   |
| Trip ID          | String    | <p><br></p>     | Y              | Auto-generated on the creation of trip                                                                   |
| Trip Status      | Text      | <p><br></p>     | Y              | Status of the trip                                                                                       |
| Vehicle Number   | String    | <p><br></p>     | Y              | Auto-generated on the creation of trip                                                                   |
| Route ID         | Text      | <p><br></p>     | Y              | Predefined route id, which has the list of POIs for that the trip should follow                          |
| Pick Up Location | String    | <p><br></p>     | Y              | Auto-generated on the creation of trip                                                                   |
| Drop Location    | String    | <p><br></p>     | Y              | Auto-generated on the creation of trip                                                                   |
| Date             | Date      | <p><br></p>     | Y              | Auto-generated on the creation of trip , Expected date of completion                                     |

#### 3. View Applications: ULB

| Field                   | Data Type | Data Validation | Required (Y/N) | Comments                                                                |
| ----------------------- | --------- | --------------- | -------------- | ----------------------------------------------------------------------- |
| Vehicle Number          | Dropdown  | <p><br></p>     | Y              | All the vehicle numbers in the registry should be shown in the dropdown |
| Vehicle Capacity        | Numeric   | View only       | Y              | Auto-populated based on what is selected while filling the application  |
| Assign Driver           | String    | <p><br></p>     | Y              | Driver associated with the vehicle number to be shown in the dropdown   |
| Possible Service Date   | Date      | <p><br></p>     | Y              | Expected date of completion                                             |
| Trip Id                 | Text      | <p><br></p>     | Y              | <p><br></p>                                                             |
| Trip Designated RoutId  | Text      | <p><br></p>     | N              | <p><br></p>                                                             |
| Trip Expected StartTime | Text      | <p><br></p>     | N              | <p><br></p>                                                             |
| Trip Expected EndTime   | Text      | <p><br></p>     | N              | <p><br></p>                                                             |
| Trip CurrentStatus      | Text      | <p><br></p>     | Y              | <p><br></p>                                                             |

#### 4. Add Illegal Dumping Sites : ULB

| Field                        | Data Type        | Data Validation                                             | Required (Y/N) | Comments                                                                                                                                                             |
| ---------------------------- | ---------------- | ----------------------------------------------------------- | -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Site Name                    | Text             | Max character - 256                                         | Y              | Name of the illegal dumping site                                                                                                                                     |
| Site Type                    | Array            | Single select                                               | Y              | The dropdown will be auto populated basis the list of possible dumping sites in the MDMS                                                                             |
| Alert                        | Numeric          | <p>Min distance = 20m</p><p>Max distance = 50-100 (TBD)</p> | Y              | Generate an alert when the vehicle is within a specified proximity.                                                                                                  |
| LocationDetails              | Array            | <p><br></p>                                                 | Y              | List of locations that are part of a POI. This can be a single LatLong or group of LatLongs (line, polygon)                                                          |
| locationDetails -> latitude  | Decimal          | <p><br></p>                                                 | Y              | <p><br></p>                                                                                                                                                          |
| locationDetails -> longitude | Decimal          | <p><br></p>                                                 | Y              | <p><br></p>                                                                                                                                                          |
| alert                        | Array of Strings | <p><br></p>                                                 | N              | One or more alert codes can be mapped to the point of interest. This is optional and can be set only in cases where the POI is related to some illegal dump yard etc |
| POI Id                       | Text             | <p><br></p>                                                 | Y              | <p><br></p>                                                                                                                                                          |
| POI Type                     | Array            | <p><br></p>                                                 | Y              | <p><br></p>                                                                                                                                                          |
| POI PositionPoint            | Text             | <p><br></p>                                                 | Y              | <p><br></p>                                                                                                                                                          |
| POI PositionLine             | Text             | <p><br></p>                                                 | Y              | <p><br></p>                                                                                                                                                          |
| POI PositionPolygon          | Text             | <p><br></p>                                                 | Y              | <p><br></p>                                                                                                                                                          |
| POI Alert                    | Text             | <p><br></p>                                                 | Y              | <p><br></p>                                                                                                                                                          |

#### Noun Verb Mapping

| <p><br></p><p>Entities</p> | Actions     |             |        |             |             |
| -------------------------- | ----------- | ----------- | ------ | ----------- | ----------- |
| Create                     | Read        | Search      | Update | Delete      |             |
| Add Point Location         | <p><br></p> | <p><br></p> | X      | X           | X           |
| Edit Existing Site         | X           | <p><br></p> | X      | <p><br></p> | <p><br></p> |
| Trip                       | <p><br></p> | <p><br></p> | X      | X           | X           |
| Anomalies                  | X           | <p><br></p> | X      | X           | X           |

## Detailed Scope

### Use Case 1: Enhancing Verifiability of Information & Identifying Illegal Dumping Spots

#### Features

1. Capturing the geo-locations with timestamps of the driver at configurable frequency thresholds.
2. Creating geo-boundaries at particular spots earmarked as illegal dumping spots.&#x20;
3. Defining anomalies based on rules, and sending alerts to the ULB employee when an anomaly is detected.

#### Users

ULB employee: To track the locations and cross-verify the alerts received.

Driver: Responsible for pickup and completing disposal, and ensuring proper sludge disposal.

#### Detailed process diagram for anomaly detection

<figure><img src="../../.gitbook/assets/Screenshot 2023-12-07 at 9.36.07 AM.png" alt=""><figcaption></figcaption></figure>

#### Description

Driver

After the driver is assigned, they proceed to the pickup location. Before providing any services, the driver must initiate the trip by selecting the 'Start' option. After the service is complete, and the disposal is done, the driver can choose to 'End' the trip. If the end trip is within the geo-fenced area of an FSTP, then the trip automatically gets closed. However, if the driver tries to end the trip outside the FSTP geo-fence area, the FSTPO has to confirm that the disposal is successful. Simultaneously, the DSO gets a notification that the respective trip has ended.

In cases where the actions are performed offline, the system records the timestamps of both the 'Start' and 'End' trips, and the transportation to ensure accurate tracking and documentation.

**Tracking Transportation**

By utilising the tracking feature, assigned vehicles can be monitored for respective applications. If a vehicle halts near any marked illegal dumping sites on the map or for a duration exceeding the configurable threshold, an alert is promptly sent to the DSO, ensuring timely awareness of potential unauthorised dumping activities.

* Notifications and alerts: The tracking system is configured to generate alerts within the application.&#x20;
* A new "Trip Details" table is introduced which displays the number of alerts generated during the trip, the trips start and end times, the end type, and offers a link to view the route taken by the driver.

1. Upon initiating the trip, the driver's geo-locations are continuously recorded at a configurable threshold, enabling the DSO or a ULB employee to track each vehicle's movements. If the driver halts at spots apart from the disposal site for a duration exceeding a configurable threshold, the DSO receives an alert. The system records alerts in real-time when the driver is online, while geo-locations are updated once the driver reconnects, generating corresponding alerts for offline periods.
2. The ULB has a centralised inbox to effectively monitor and track the drivers' trips. The inbox shows the alerts raised per trip respective to the application.&#x20;
3. The application details page needs to be enhanced for the following:&#x20;
   1. Geo-location to be added on the employee form.
   2. Display driver details.
   3. View route details: This shows the ULB employee a map showing route taken by driver and points of stoppages along with time of stoppage. &#x20;
      1. Display a map view showing the stops (exceeding a certain time) made during the trip.
      2. Vehicle route: Utilise the tracked geo-location coordinates to generate and display the vehicle's route on the map with respect to each trip.
4. Illegal dumping zones:&#x20;
   1. ULB defined: ULB personnel/admin can define illegal dumping zones.

Clicking on illegal dumping sites on menu options will allow users to see the illegal dumping sites in the ULB. If no sites are present, then user will only see the option to “Add new site”.

1. Clicking on “Add new site” will allow users to create a new illegal dumping site as an anomaly object.&#x20;
2. User will need to add following details to create an anomaly object:
   1. Site name - Name of the site (For example, Dhenkanal Lake).
   2. Location category - The type of geographical body (For example, Lake/Road/Highway/Bridge/Old building/Open field/Rainwater pipe, etc.).
   3. Buffer area (in metres) (Distance from these coordinates which can considered an anomaly).
   4. Map UI
      1. For Polygon - (For example, a pond):
         1. Upto 20 points are allowed on the screen.
         2. Each point will have a cross icon.&#x20;
         3. If two points are already added. User has to remove one point to add a new point.&#x20;
         4. If a buffer is added. Show a corresponding figure of ‘X’ metres buffer perpendicular to line in all directions, with highlighted colour (even before saving), so that the user is clearly aware of the boundaries he/she is making.&#x20;
         5. Polygon should be a closed figure.
3. &#x20;Once saved, the coordinates are saved in the anomaly object. &#x20;
4. To edit or make changes to an illegal dumping site click on an anomaly object from the list of objects in the menu.
   1. In the next screen, click on actions. Actions will open edit and delete.
   2. Clicking on edit will make the menu editable (until then it will be non-editable).
   3. Users are allowed to edit all options. There is no restriction.&#x20;
   4. Buttons will be shown as “Save Changes” and 'Cancel'.
   5. Clicking on save changes will save all the changes made to the anomaly object.
   6. Clicking on cancel will take the user to the previous screen.
5. Alerts on Illegal dumping:
   1. If any vehicle is found stopping in these locations, including buffer areas, for more than 'X' minutes, should send an alert immediately. Who to send:
      1. ULB employee - He/she will receive the alerts raised against the trip ID.

#### Acceptance Criteria

* Alerts should be generated for a ULB employee when vehicles are stationary near the marked illegal dumping spots for a configurable duration.
* The system should provide the ability for the DSO to add illegal dumping zones, allowing flexibility in response to changing circumstances.

#### Out of Scope

1. There is no other activity tracking of disposal vehicles other than the duration between the start and end trips.
2. No verification of which vehicle is being tracked. For example, if the mobile of the disposal truck driver is given to a two-wheeler driver, then the geo-location of the two-wheeler driver is recorded.
3. No verification of the disposal truck driver for example the registered driver and the actual disposal driver might be different.

### Use Case 2: Automation of Disposal and Completion of Requests:&#x20;

#### Features

1. Capturing the location of the vehicle at the disposal site.
2. Verification of whether the vehicle location is within the geo-fenced boundary of the disposal site.
3. Automated confirmation of the disposal based on positive verification.

#### Users

Admin portal: Geo-fencing data need to be added at the backend in the MDMS of disposal spots.

Driver: Responsible for completing disposal requests and ensuring proper sludge disposal.

#### Workflow

![](https://lh7-us.googleusercontent.com/QETtZVBprMSXX6UsiVN79Z3sotMSYkSNO-Ay6WOrBQZsWLfJhMRvVqajNTSTqe0sEkqKFRlrYGQFceLwgxj\_C-bcXYb1S2gFKpC\_SQ6kA8ETjEQ953Jott-8mxYYZ9v508uo4ne5K9ugHgBWOYG1r28)

#### Description

1. The vehicle tracking service in FSM helps to automate the disposal process requests in legal dumping sites. By utilising geo-tagging and proximity data, the system can verify if the driver has disposed off waste at the designated disposal spot.
2. Admin functionality (no UI required):
   1. Allows administrators to view, add, delete, and modify the MDMS at the backend.
   2. Define the proximity radius for verification (for example, 50 meters) at the backend.
3. Driver:
   1. When a driver is completing  a disposal request, the system captures their geo-tags (longitude and latitude) at the time of disposal. The system compares the driver's geo-tags with the predefined disposal spots set by the admin. There are two possibilities:
      1. If the driver's geo-tags are within the specified proximity radius (for example, 50 metres) of the disposal spot, the disposal is considered system verified, then the system automatically closes the disposal request, marking it as system verified.

#### Acceptance Criteria

1. The driver should be able to start the trip, and the system should capture and record the geo-location coordinates (longitude and latitude) at the start of the trip.
2. At a specific configurable frequency (for example, every 2 minutes; this is configurable), the driver's geo-location coordinates should be recorded and stored by the system.
3. The system compares driver geo-tags with the predefined disposal spots.
4. Upon reaching the plant, the driver should be  able to end the disposal request from his/her mobile phone and the system should capture the geo-location coordinates at the time of closure.
5. Automated closure at the disposal location:
   1. If the driver's geo-location coordinates indicate that they are within the geo-fenced area of an FSTP, the disposal request should be automatically closed and marked as system verified.
   2. The closure should trigger an automated notification or confirmation to the driver and the admin.

#### Out of Scope

1. If the driver ends the trip outside a geo-fenced area, the driver uploads a picture and the FSTPO is required to verify the end of trip from their end.
2. Alert for non-closure at the legal disposal site:
   1. If the distance between the driver's coordinates at closure and the designated disposal location is greater than the defined threshold (for example, 50 meters), an alert should be generated.
3. There is no other activity tracking of disposal vehicles other than the duration between the start and the end trips.
4. If the driver goes offline during the trip, the driver application should continue recording the geo-location coordinates at the predefined frequency. The recorded coordinates should be stored locally on the device until an internet connection is available. Once the driver's device regains internet connectivity, the recorded geo-location coordinates should be synced with the server or the backend system.

## Design

Find the mock-ups below:

| <p>Driver Login Screen</p><ul><li>After a specific request is generated, the ULB employee assigns a driver, who is then prompted with a login screen. The driver receives a user ID and password from the ULB employee, and has to select the respective city from the dropdown, enabling access to the system.</li></ul><p><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br></p><p>The back button takes the user to the language selection screen.</p><p><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br></p><p>Upon clicking the "Forgot Password" hyperlink, the screen displays a message instructing users to get in touch with the ULB in case they have forgotten their password.</p> | <p><img src="https://lh7-us.googleusercontent.com/bZ_7s78tTSjIGtpAoEEvBxH4AwbzvAg_UzMm7f5vB5zRMRCtZAxxgDevDYkBkTVitHFd6aH1K-7lJoBN3ymkEZtPvN8IkdaO-BEyjlKd_IbS2xX9j4b6h18fEF6WDs3xPHyTor1z-Fu9L1oWj8fcwZ8" alt=""></p><p><img src="https://lh7-us.googleusercontent.com/AP8pnvIlOdtVMl37_qaSeS1VEwGD9Q3dvtklTbzQjXWSaEPEPd29NmDHq6y91ZXP207IKEZ33ctUfNtPMnjVB60rW-ULI2PtAo7oIaRkRbWF-Kba-vXACsS5sK31EBsGM0098sGvv9qA8c0jeuNRZ_0" alt=""></p><p><img src="https://lh7-us.googleusercontent.com/_aXe5SHg6VlNNO7muS5z23KFnqUvB4djdZxzt8quhhMKyzk2UKtd6zq2i7pUxNM1vAByJ0bX-RPz0YhSWb5CRwcjqxqsuBXkfwt62u5QxKc9nJVeUYW8VmCa-rMBjqiiWQudCklPxTs4SM8MrQEnrXw" alt=""></p> |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <p>Driver Home &#x26; Inbox</p><p></p><p>Upon the driver's successful login, their inbox interface will present a layout featuring both assigned trips and completed ones. The hamburger menu offers options for navigation:<br></p><p>Home: This option displays the assigned trips, serving as the central hub for trip management.</p><p>Language: Drivers have the flexibility to select their preferred language for a more convenient experience.</p><p>Logout: This option allows the driver to exit the system.</p><p><br></p>                                                                                                                                                                                                                                           | <p><img src="https://lh7-us.googleusercontent.com/QkqCrhTpoQacjXE_uxaaiwU3dQ5q5vLAZRuoJ3lMH4Il9I0m-C6vUq718vtCPC2Y-oh-RYo1TziORu4v2Ub15kP3BHSp2paV3ouLJZajru3gJJFLpVOz9jxT_kw3a4LoCZ8DiTlEO_PUuB9gCicyPBU" alt=""></p><p><img src="https://lh7-us.googleusercontent.com/hlwr8MTEuYsMsHic0r_OtX69nlZ1Se9hCar5BVClc-0jdpaPDlQhimKFarR25ug-frbOFEECWqlVHAEtPqVoE_82Aq26UXm_PU3gGNHoMqbv9c9q8A4IpnIUV3HPPRRgA8xc3TthmOr_7cqgcMI1PkI" alt=""></p>                                                                                                                                                                                                                       |
| <p>Upon successfully login, the driver gains access to an overview of all assigned trips. The key features of this interface include:</p><ul><li>Efficient trip search: The inclusion of a search bar empowers the driver to easily locate a specific trip using the applicant’s name and contact number.</li><li>Organised trip categorisation: The screen presents two distinct tabs:</li></ul><p>       - "In progress" tab: This section shows trips that are pending initiation and assignment.</p><p>      - 'Completed' tab: Here, the driver can view a compiled list of the completed trips.</p><p><br><br><br><br></p>                                                                                                                                                 | <p><br></p><p><img src="https://lh7-us.googleusercontent.com/RiOUN1iHW0q_okaAl52CX_xbgqQMbweQISefTbolMUlW7q_GhDUNjLAD-WvZy5ybADSl1yQkTITH-_13Pwztj0qLjBlrphM4gVMFjLizzlLZh4EI38DqfvYxFtvVZO9EJ0YJUtUzlWi2B3zeicJ2pXs" alt=""></p>                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| <p>Upon selecting the "View Details" hyperlink, the driver can see the information of the applicant, including both the pickup location and the designated drop-off point (referred to as the "FSTP plant").</p><p></p><p>The "Start Trip” button triggers the commencement of the desludging service's tracking and monitoring process.</p><p><br><br><br></p>                                                                                                                                                                                                                                                                                                                                                                                                                  | ![](https://lh7-us.googleusercontent.com/lcl-kCtwartOTdwdWsnQL43wYXlyUmQqX2Mldv1q9eQ4XWw2waj7iyRU-4UjxY-5bs50ux7UBCNhrd4yuMqh-VjaxvvFsZqdI9HDRUE6q2pw8dMqeP198cGVcHYKTPpAXLh\_VWG6wo2tURdvcRDy8L0)                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Upon clicking the "Start Trip" button, the system displays a warning: “Start the trip only after reaching the pickup location. Have you reached the applicant location?”                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | ![](https://lh7-us.googleusercontent.com/q8scvg-62xQ-QQjxVqz65t3xQR-\_DHZEo1OD-Oxvcl9\_Pq79W8kGwKOEetUknE1RrV5PKa0oxdre872SE6APtinu-kqIIqJEYJHlG\_sO9td6d7y21raGcApkJleiS518\_dog7tsNhfvtdNamngKzsiA)                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| When the driver clicks on 'Yes', a toast message - “Trip Started Successfully” - is displayed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | ![](https://lh7-us.googleusercontent.com/o6w2wsTW1NtBKt\_43aEaO\_reOS6-PQUZ09dLZWoWC9pinRBLJOu3qJWuPEVLv7MqDuYEpTsbBR42bdtPmrM\_mYEAfzH6ZXBzoZToy9ThVUYxzIp\_Aqk4Kxut40YqYMBQ\_LUbx1vtXOLk2V0vrhYBCA0)                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| After the trip has been initiated and the driver has concluded the desludging process, the driver proceeds to the provided FSTP (to finalise the desludging task and complete the request). After successful completion of the desludging process in the FSTP, the driver has  to click on the "End Trip" button to conclude and finalise the request.                                                                                                                                                                                                                                                                                                                                                                                                                           | ![](https://lh7-us.googleusercontent.com/JAhDnO9wEWXkSmvip\_JNWvTBBuMD9h79u3l2Vs9WfPc4qADFT7aN4EHCMSIOsBjGLyyfs4QNmKQ7viPxKZthNtkc6L-ExchmR2lxP\_H\_WFGboBuUUSU4lOPNaJIxZJml0RCrW6tKmWLTsGp9nR\_2zCI)                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| <p>Upon selecting the "End Trip" button, the system shows a warning message: "Are you sure you want to end the trip for Locality 1...?" Following the acknowledgment of this warning, the trip reaches its completion status.</p><p><br><br><br><br><br><br><br><br></p><p>When the driver clicks on 'Yes', a toast message - “Trip Ended Successfully” - is displayed.</p><p><br><br></p>                                                                                                                                                                                                                                                                                                                                                                                       | <p><img src="https://lh7-us.googleusercontent.com/JgkSV11JqeYuLPw70Pi06QHQXql-TsuQSxQWsihys03x2obUGeDUeJIDP-8RmVnPQtjQYX-3c-mmj0O1WfoP9y7vwU6ofkDVK9tOrV9uAFlh25CguZqIxEj41tFLPH-dAiGMHI3F9Oh99lbcOvWN3sQ" alt=""></p><p><img src="https://lh7-us.googleusercontent.com/rk3U553may_N_hO8OJPZrUb0HVprESteNOBFaiStomXvu-1RoziaIMmCgi6FXdFMkYziAJky-5LzhvzTEHoIYKisALfKBlSUjt0bq70Je7hpr0yOxGSIUmpdAXQxXk2RTs9k_iXuNoytp1vkTU_rzkM" alt=""></p>                                                                                                                                                                                                                       |
| <p>View Applications: ULB</p><p><br>The ULB employee can access the trip details and review any raised alerts. </p><p>Upon selecting the "View Route" option from the new table “Trip Details”, the path taken by the driver is shown.<br>The trip details table also shows-<br>Date: Start date of the trip.<br>Start time: Start time of the trip.<br>End time: End time of the trip.<br>Alerts: The number of alerts raised for the respective trips.<br>Route: Shows the route taken by the driver, which also shows the "Stop Locations", "Alert Locations", "Pickup and End Location".</p>                                                                                                                                                                                 | <p><img src="https://lh7-us.googleusercontent.com/BjnmzSH4D5Hy0ulOC7zPGt8s_Rhca_VtmXOVCt_pk2gn49l83hKHKAStzsSZTEXVR-EdJoXiSxVGmMQsMH0uOaPITnXYlsRfgm7ERHAxAdi13Ft2YPXwuDzBArakBHxNF3CktoIZiPAUdEOUqCiMv-o" alt=""></p><p><br></p><p><img src="https://lh7-us.googleusercontent.com/DpGBSFAnNwVG9cphjNZ6eHanmIKpBeBeLk0SyiDjNoVZBEZQv9qyPoqhOnOhRR5x1GM32sGvqXLfd2ExuGplYAKeiE-VHA_DwmyS6ulviFdAnqALu30UEypIieOEnuvu5TbB7-cfOKtTSUpu2F421ic" alt=""></p>                                                                                                                                                                                                            |
| <p>Add Illegal Dumping Sites: ULB</p><p></p><p>An additional feature has been introduced under the "Faecal Sludge" section, labeled as "Vehicle Tracking".</p><p>Upon clicking on this, the page is redirected to options such as ‘Alerts’ and "Illegal Dumping Sites".</p><ul><li>Alerts are set up as an inbox that showcases the application ID, the corresponding vehicle, and the type of generated alert.</li><li>Upon clicking on illegal dumping sites, the user can add the pint location and define the spots.</li></ul>                                                                                                                                                                                                                                               | <p><img src="https://lh7-us.googleusercontent.com/SQI6YDCbqxZDs8dBjZOGIdA6FAPR66M53IN0eTuQnNPRUvyM-VcnFIZhVx3g_Kzyeee6vrYJdCBtsrZPvJo8BdM6rwLRE3Z7Rtcw5gp83tZotWUn3pH6almIP4vDa1umUr339kESw3HoYiZ05-ILjfg" alt=""></p><p><img src="https://lh7-us.googleusercontent.com/6DZQfWtJloxf5_lxa4fG4k1mVGUyUNVuZQObE12SXgdRVLGY6Vq11_VYWLrPdgST0S1ldI75eoLDjN8AnGhnbl4PoPxk6cz0NjRcB18DpSGlqcOHePGpk5USuQgn2-dHivbwvW6gzB_DmCIgGNn9y34" alt=""></p><p><img src="https://lh7-us.googleusercontent.com/t5YCYf7fnjcNt4Bmm2Fwj7HxqAhjYVS5IFn9urnkOLvoLjSiMVOMM__FPnDKg9HAJVnAaXwr4gSW1tZjLFlUH11rSIflFiYc63BsOvx_65XRKRno0_TUtNWscCxceICh_whYCqU0KjkuEiVsGLPaCtM" alt=""></p> |
| <p>Add Point Location</p><p></p><p>By clicking on "Add Point Location", the ULB employee can add a new dumping site. They can then proceed to furnish all the essential particulars, including the Site Name, Site Type, and the distance threshold for triggering an alert when within proximity.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | ![](https://lh7-us.googleusercontent.com/SNgQ3m4p7PmAGucZ8uFYy\_MssyxJJzIwXO9\_YMikvAcyJiezQXBx8cOkaXqS0fbq5HByFExcUlWUDYSuK0N9TV3IbhfpUPT5CIvFZmXiL-fqCQS8CQ\_W3bL5LoVttBB8STDbGjwIYDF6seuv3BbkDCg)                                                                                                                                                                                                                                                                                                                                                                                                                                                               |

## Success Metrics

| Goal                                                                                  | How will we know vehicle tracking is successful                                                                                                                                                              |
| ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <ol><li>Introducing end type </li></ol><p>- System Verified</p><p>- FSTP Verified</p> | <ul><li>The percentage reduction in manual intervention required for status updates.</li><li>Count of applications closed with end type -  System verified.<br><br></li></ul>                                |
| <ol start="2"><li>Mobile application for drivers</li></ol>                            | <ul><li>Driver engagement.</li><li>The number of trips initiated (in-progress)  and completed.</li><li>The number of trips started by the driver.</li><li>The number of trips ended by the driver.</li></ul> |
| <ol start="3"><li>Identifying illegal dumping spots</li></ol>                         | <ul><li>The percentage reduction in unauthorised sludge disposal incidents through the intervention of alerts.</li></ul>                                                                                     |
| <ol start="4"><li>Alerting</li></ol>                                                  | <ul><li>The number of alerts triggered per application for longer waiting near marked illegal dumping sites.</li></ul>                                                                                       |

## Future Roadmap

1. Users to be able to delete and edit the added illegal dumping.
2. Include the process of adding point locations for a polyline, creating a line through the user interface.
3. Incorporate additional alerts for prolonged stops at regular sites when sludge is collected for a duration exceeding 'X' minutes.
4. System generated illegal dumping spots: These are identified based on multiple drivers being stationary at the same location for a predetermined period. The DSO or ULB employee has the authority to designate or remove such zones, enhancing the system's ability to pinpoint areas prone to unauthorised waste disposal.
5. Bringing in the safety measures screen, and making it mandatory in the driver application.
6. Explore on advanced analytics for vehicle tracking, including metrics such as the number of trip requests, average distance covered, and the number of closed applications, with a focus on distinguishing between FSTP verified and system verified cases.
