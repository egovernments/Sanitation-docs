# Functional Specifications

## Desludging Operator Registration

Desludging operators (DSO) can be registered via a user interface (UI) available to the urban local body (ULB) admin.  Once created, multiple vehicles and drivers can be mapped to a DSO. DSOs can also be enabled/disabled in the system.&#x20;

Desludging operators will have the following details:

| Field Name         | Type                     | Mandatory | Editable (Y/N) | Unique within a ULB (Y/N) |
| ------------------ | ------------------------ | --------- | -------------- | ------------------------- |
| Vendor name        | Free text                | Y         | N              | N                         |
| Gender             | Array                    | Y         | N              | N                         |
| DOB                | Date                     | N         | Y              | N                         |
| Email address      | Free text (Email format) | N         | Y              | N                         |
| Mobile number      | Number                   | Y         | N              | Y                         |
| Door number        | Free text                | N         | Y              | N                         |
| Plot number        | Free text                | N         | Y              | N                         |
| Building name      | Free text                | N         | Y              | N                         |
| Street             | Free text                | N         | Y              | N                         |
| Pincode            | Free text                | N         | Y              | N                         |
| City               | Array                    | Y         | N              | N                         |
| Locality/mohalla   | Array                    | Y         | N              | N                         |
| Landmark           | Free text                | N         | Y              | N                         |
| Additional Details | Free text                | N         | Y              | N                         |
| Status             | Binary                   | Y         | Y              | N                         |

## Driver Registration

Drivers can be registered via a UI available to the ULB admin. Once created, a driver can be mapped to a DSO. Drivers can also be enabled/disabled in the system.&#x20;

Drivers operators will have the following details:

| Field Name            | Type                                         | Mandatory | Editable (Y/N) | Unique within a ULB (Y/N) |
| --------------------- | -------------------------------------------- | --------- | -------------- | ------------------------- |
| Driver name           | Free text                                    | Y         | N              | N                         |
| Driver License Number | Free text (Validation on the license format) | Y         | Y              | N                         |
| Gender                | Array                                        | N         | Y              | N                         |
| DOB                   | Date                                         | N         | Y              | N                         |
| Email address         | Free text (Email format)                     | N         | Y              | N                         |
| Driver phone number   | Number                                       | Y         | N              | N                         |

## Vehicle Registration

Vehicles can be registered via a UI available to the ULB admin. Once created, a vehicle can be mapped to a DSO. Vehicles can also be enabled/disabled in the system.&#x20;

Vehicles operators will have the following details:

| Field Name                       | Type      | Mandatory | Editable (Y/N) | Unique within a ULB (Y/N) |
| -------------------------------- | --------- | --------- | -------------- | ------------------------- |
| Registration number              | Free Text | Y         | N              | Y                         |
| Vehicle model                    | Array     | Y         | Y              | N                         |
| Vehicle type                     | Array     | Y         | Y              | N                         |
| Tank capacity                    | Array     | Y         | Y              | N                         |
| Pollution certificate valid till | Date      | N         | Y              | N                         |
| Insurance valid till             | Date      | N         | Y              | N                         |
| Road tax paid till               | Date      | N         | Y              | N                         |
| Fitness certificate valid till   | Date      | N         | Y              | N                         |
| Vehicle owner name               | Free text | Y         | N              | N                         |
| Vehicle owner phone number       | Number    | Y         | N              | N                         |

## Apply for Desludging Services

The citizen or the ULB official can apply for a desludging request.&#x20;

**Application Channel**

* Citizens can apply online using the web application.
* Citizens can walk into a ULB and submit a request to the counter operator, who then creates an application on behalf of the citizen online.
* Citizens can call the ULB and request for a desludging operation,  which can then be transformed into an online application by the ULB official.

Application Submission

* Desludging applications can be created by a citizen.
* Desludging application requests can be created by a ULB official on behalf of a citizen.

&#x20;    \- If the application is created by a ULB official, then capture the channel in which the request was received. It will be an additional field in the UI to capture the channel.

| Field Name                    | Type                                                        | Mandatory           | Editable    | Comments                                                                                 |
| ----------------------------- | ----------------------------------------------------------- | ------------------- | ----------- | ---------------------------------------------------------------------------------------- |
| Applicant name                | Text                                                        | Y                   | N           | <p><br></p>                                                                              |
| Mobile number                 | Numeric                                                     | Y                   | N           | <p><br></p>                                                                              |
| Gender                        | Dropdown                                                    | Y                   | N           | <p><br></p>                                                                              |
| City                          | Dropdown                                                    | <p>Y</p><p><br></p> | N           | As per the boundary data defined.                                                        |
| Locality                      | Dropdown                                                    | Y                   | N           | As per the boundary data defined.                                                        |
| Whether property is in a slum | Binary                                                      | Y                   | N           | <p><br></p>                                                                              |
| Slum name                     | Dropdown                                                    | Y                   | N           | Only if the above selection is yes. List of slums  per ULB to be uploaded in the system. |
| Street name                   | Text                                                        | N                   | N           | <p><br></p>                                                                              |
| Door house number             | Text                                                        | N                   | N           | <p><br></p>                                                                              |
| Landmark                      | Text                                                        | N                   | N           | <p><br></p>                                                                              |
| Geo location                  | Lat-Long                                                    | N                   | N           | As per DIGIT standards.                                                                  |
| Onsite sanitation type        | Dropdown                                                    | N                   | Y           | Select one from the list.                                                                |
| PIT size                      | L\*B\*D in feet (This UOM might change from state to state) | N                   | Y           | Numeric                                                                                  |
| Property type                 | Dropdown                                                    | Y                   | N           | Use the same ontology as defined in DIGIT Property Tax.                                  |
| Property sub-type             | Dropdown                                                    | Y                   | N           | Use the same ontology as defined in DIGIT Property Tax.                                  |
| Number of trips required      | Numeric                                                     | Y                   | Y           | Editable by ULB and DSO.                                                                 |
| Vehicle capacity              | Dropdown                                                    | Y                   | N           | Populated as per the vehicle capacities available in the particular ULB.                 |
| Application channel           | Dropdown                                                    | Y                   | <p><br></p> | Required only if the creator is a ULB official.                                          |
| Total amount                  | Numeric, display only                                       | Y                   | N           | Calculated based on the billing slabs.                                                   |
| Minimum amount payable        | Numeric, display only                                       | Y                   | N           | Displayed as per the configuration in the backend.                                       |
| Advance amount                | Numeric                                                     | Y                   | Y           | <p><br></p>                                                                              |

**Service Request Fee**

* Service request fee is calculated as a multiplier of the amount per trip defined in the billing slab table (based on property type, sub-type, whether it is a slum, vehicle capacity) and the number of trips.
* For certain combinations with the above parameters, the pricing can be set at zero. In such cases, demand will not be generated.
* ULBs can configure a minimum advance payment to be collected before starting a request. This can either be a fixed value (starting from 0) or a percentage (ranging from 0-100). Citizens will be able to make a payment above the minimum advance amount, and below the total trip amount as an advance payment.

**Payment: Online/Cash Counter**

* Citizens can make both the advance and balance payments online.
* Citizens can make both the advance and balance payments at the ULB counter.
* Payment receipts will be generated and sent across via SMS. They can be downloaded at the citizen and ULB interfaces.

## Update Application Request by ULB Official

* When a service request is received by a ULB official, he/she can do the following:

&#x20;     \- Search and assign a DSO to the application request.

&#x20;     \- Cancel the application with remarks.

&#x20;     \- Update the application request with the number of trips required to empty the septic tank or Pit and the vehicle details.

&#x20;     \- Change the DSO from an application request if the assigned DSO is not available.

&#x20;     \- Update the status of the request as completed, post desludging.

&#x20;     \- View past records of requests and service delivery.

**Cancellation of application.**

* A citizen or a ULB official can cancel the application online.
* Citizesn can cancel it only if the DSO is not assigned to the service request.
* Application cannot be cancelled if the payment is made already.
* ULB officials can cancel it only if the service is not completed by the DSO.

## SMS and Email Updates

* SMS and email updates are sent on every necessary process of the entire process flow.

## Application view by DSO

* A DSO should get notified about the request that is assigned to him/her. On receiving the request, the following actions can be taken:

&#x20;     \- View the request.

&#x20;     \- Assign request to a vehicle.

&#x20;     \- Update the number of trips.

&#x20;     \- Flag a request ready for disposal.

&#x20;     \- Close the request post desludging.

* One DSO cannot see the details of the other DSO or the request assigned to the other DSOs.

| Field Name                 | Type    | Required | Comments    |
| -------------------------- | ------- | -------- | ----------- |
| Volume of waste collected  | Numeric | Y        | <p><br></p> |

## Feedback by Citizen

Citizens can provide feedback on the desludging request&#x20;

* There will be an option to rate the service provided with comments.
* There will be an option for citizens to update whether safety equipment is used by the sanitary workers during the operation.

## Vehicle entry by FSTP/STP plant Operator

Plant operators can do the following:

* View the list of desludging operations for a day. Since an application may have multiple trips, the plant operator will view multiple line items against an application in the inbox.
* Update the Vehicle entry log against an application request with the details like:

&#x20;     \- Date and time of entry.

&#x20;     \- Volume of sludge dumped at the plant.

| Field Name              | Type           | Required | Comments        |
| ----------------------- | -------------- | -------- | --------------- |
| Vehicle in-time         | Time           | Y        | <p><br><br></p> |
| Vehicle out-time        | Time           | Y        | <p><br></p>     |
| Volume of sludge dumped | Numeric        | Y        | <p><br></p>     |
| Additional details      | Text           | N        | <p><br></p>     |
| Attachments             | Document/Image | N        | <p><br></p>     |

* If a vehicle without a corresponding requests arrives at the FSTP, the FSTP can record the vehicle entry.
*

| Field Name              | Type           | Required | Comments                                                    |
| ----------------------- | -------------- | -------- | ----------------------------------------------------------- |
| Vehicle number          | Alphanumeric   | Y        | <p>Only unregistered vehicles in the system.</p><p><br></p> |
| DSO name                | Text           | Y        | <p><br></p>                                                 |
| Locality                | Text           | Y        | <p><br></p>                                                 |
| Vehicle in-time         | Time           | Y        | <p><br></p>                                                 |
| Vehicle out-time        | Time           | Y        | <p><br></p>                                                 |
| Volume of sludge dumped | Numeric        | Y        | <p><br></p>                                                 |
| Additional details      | Text           | N        | <p><br></p>                                                 |
| Attachments             | Document/Image | N        | <p><br></p>                                                 |

* The DSO can also decline an incoming vehicle.&#x20;
*



| Attribute            | Type    | Required? | Comments                                                               |
| -------------------- | ------- | --------- | ---------------------------------------------------------------------- |
| Vehicle              | UUID    | Y         | <p><br></p>                                                            |
| Trip Number          | Numeric | Y         | <p><br></p>                                                            |
| Volume               | Numeric | Y         | <p><br></p>                                                            |
| Desludging request   | UUID    | Y         | <p><br></p>                                                            |
| Reason for declining | String  | Y         | \[ “Septage Source”, “Outside operational hours”, “Under Maintenance”] |

## Feedback by Citizens

Citizens can provide feedback on the desludging request:&#x20;

* Rate the service provided (1-5 stars).
* Multi-select to update whether safety equipment is used by the sanitary workers during the operation.

## List of PDFs

* Acknowledgement Recepit: Confirming receipt of desludging receipts.
* Payment receipts: Multiple payment receipts based on the payments made.

## Reports

### Daily desludging request report

Search criteria

| Field name | Type    | Required                                   |
| ---------- | ------- | ------------------------------------------ |
| ULB name   | Default | Internally pass the ULB name (Y)           |
| From date  | Date    | Y                                          |
| To date    | Date    | Y                                          |
| DSO name   | Search  | N - Auto-populate on typing a few letters. |

Search result

| Application number | Application date | Current Status | DSO Name    | Amount (Rs) | Date of completion |
| ------------------ | ---------------- | -------------- | ----------- | ----------- | ------------------ |
| <p><br></p>        | <p><br></p>      | <p><br></p>    | <p><br></p> | <p><br></p> | <p><br></p>        |
| <p><br></p>        | <p><br></p>      | <p><br></p>    | <p><br></p> | <p><br></p> | <p><br></p>        |
| <p><br></p>        | <p><br></p>      | <p><br></p>    | <p><br></p> | <p><br></p> | <p><br></p>        |

### Area-wise daily collection report

Search criteria

| Field name | Type     | Required                                    |
| ---------- | -------- | ------------------------------------------- |
| ULB name   | Dropdown | Internally pass this info.                  |
| Mohalla    | Dropdown | N                                           |
| DSO        | Search   | N - Auto-populate on typing few characters. |
| From date  | Date     | Y                                           |
| To date    | Date     | Y                                           |

Search result

| Application number /Date | Mohalla     | DSO Name    | Status      | SLA compliance | Volume of waste collected  |
| ------------------------ | ----------- | ----------- | ----------- | -------------- | -------------------------- |
| <p><br></p>              | <p><br></p> | <p><br></p> | <p><br></p> | <p><br></p>    | <p><br></p>                |
| <p><br></p>              | <p><br></p> | <p><br></p> | <p><br></p> | <p><br></p>    | <p><br></p>                |
| <p><br></p>              | <p><br></p> | <p><br></p> | <p><br></p> | <p><br></p>    | <p><br></p>                |

### FSTP/STP plant report with vehicle logs

Search criteria

| Field Name     | Type     | Comments                                                                                                                                                                                                                                       |
| -------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ULB name       | Dropdown | <ul><li>If the logged-in user is a ULB employee, then pass this information internally.</li><li>If the logged-in user is an STP/FSTP operator, then ask the user to select the ULB name as one STP can be attached to multiple ULBs.</li></ul> |
| STP/FSTP name  | Dropdown | Internally pass this information: We have mapping between ULB and STP/FSTP.                                                                                                                                                                    |
| DSO name       | Search   | N - Autopopulate on typing a few letters                                                                                                                                                                                                       |
| Vehicle number | Dropdown | Populate only if the DSO name is selected.                                                                                                                                                                                                     |
| From date      | Date     | Y                                                                                                                                                                                                                                              |
| To date        | Date     | Y                                                                                                                                                                                                                                              |

Search result

| Application number | DSO name /Vehicle number | Vehicle entry date | Vehicle in time | Vehicle out time | Volume of sludge dumped (L) |
| ------------------ | ------------------------ | ------------------ | --------------- | ---------------- | --------------------------- |
| <p><br></p>        | <p><br></p>              | <p><br></p>        | <p><br></p>     | <p><br></p>      | <p><br></p>                 |
| <p><br></p>        | <p><br></p>              | <p><br></p>        | <p><br></p>     | <p><br></p>      | <p><br></p>                 |
| <p><br></p>        | <p><br></p>              | <p><br></p>        | <p><br></p>     | <p><br></p>      | <p><br></p>                 |

Dashboard

Coming soon
