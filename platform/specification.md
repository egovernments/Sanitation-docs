# Specification

### Register DSO Agency

{% tabs %}
{% tab title="Description" %}
Information of the private company or the municipal corporation to which the desludging operator is employed.
{% endtab %}

{% tab title="Attributes" %}
| Attribute                  | Type           | Required | Comments                                                                                                                                                                                                  |
| -------------------------- | -------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Type                       | String         | Y        | Select from options (toilet construction contractor, toilet operation contractor, desludging contractor, treatment construction contractor, treatment operation contractor, testing lab, pharmaceutical). |
| Operational type           | String         | Y        | (Public, private)                                                                                                                                                                                         |
| Locality                   | Location array | Y        |                                                                                                                                                                                                           |
| License type               | String         | Y        | Select from options \[]                                                                                                                                                                                   |
| License Number             | UUID           | Y        |                                                                                                                                                                                                           |
| Owner                      | String         | Y        |                                                                                                                                                                                                           |
| Primary point of contact   | UUID           | Y        |                                                                                                                                                                                                           |
| Secondary point of contact | UUID           | Y        |                                                                                                                                                                                                           |
| Certification              | String         | N        |                                                                                                                                                                                                           |
| Training type              | String         | N        | Select from options \[]                                                                                                                                                                                   |
| Number of workers          | Numeric        | N        |                                                                                                                                                                                                           |
| Contract                   | UUID           | Y        |                                                                                                                                                                                                           |
| Payment choice             | Array          | Y        | (Pre-service, Post-service)                                                                                                                                                                               |


{% endtab %}
{% endtabs %}

### Register Vehicles

{% tabs %}
{% tab title="Description" %}
These are details that vehicle owners should provide to register their vehicle in the system.
{% endtab %}

{% tab title="Attributes" %}
| Attribute                        | Type                 | Required | Comments                                                                                                     |
| -------------------------------- | -------------------- | -------- | ------------------------------------------------------------------------------------------------------------ |
| ID                               | UUID                 | Y        |                                                                                                              |
| DSO agency                       | UUID                 | Y        |                                                                                                              |
| Vehicle owner                    | String               | Y        | (Public, Private)                                                                                            |
| Waste type                       | String               | Y        | (Faecal sludge, solid waste, plastic)                                                                        |
| Desludging service delivery      | UUID array           | Y        | Mapping to all emptying services that a vehicle served.                                                      |
| Status                           | String               | Y        | (Operational, under maintenance, others)                                                                     |
| Registration number              | Numeric              | Y        |                                                                                                              |
| Pollution certificate validity   | Date                 | Y        |                                                                                                              |
| Insurance certificate validity   | Date                 | Y        |                                                                                                              |
| Fitness validity                 | Date                 | Y        |                                                                                                              |
| Road tax paid until              | Date                 | Y        |                                                                                                              |
| Status                           | String               | Y        | Select from options (functional, non-functional)                                                             |
| Availability                     | Numeric Array \[]\[] | Y        |                                                                                                              |
| Last location                    | Geo \[]              | Y        | Keeping a track of last location of the vehicle on a daily basis to increase the speed of service delivered. |
| Vehicle type                     | String               | Y        | Select from options (tractor, trolley, suction, motor, sewer suction, jetting truck).                        |
| Suction type                     | String               | Y        |                                                                                                              |
| Vehicle (tank capacity) capacity | String               | Y        |                                                                                                              |
| Suitable physical accessibility  | String               | Y        | Select from options \[]                                                                                      |
| GPS enabled                      | Boolean              | Y        |                                                                                                              |
{% endtab %}
{% endtabs %}

### Register DSOs

{% tabs %}
{% tab title="Description" %}
This includes details of the desludging operators who are registering in the system.
{% endtab %}

{% tab title="Atributes" %}
| Attribute                | Type       | Required | Comments |
| ------------------------ | ---------- | -------- | -------- |
| DSO agency               | UUID       | Y        |          |
| Name                     | Text       | Y        |          |
| Contact                  | Numeric    | Y        |          |
| Health check             | UUID       | Y        |          |
| Start date of employment | Date       |          |          |
| End date of employment   | Date       |          |          |
| Schemes applied          | UUID array |          |          |
| Schemes eligible         | UUID array |          |          |
| PPE availability         | Bool       |          |          |


{% endtab %}
{% endtabs %}

### Register FSTP

{% tabs %}
{% tab title="First Tab" %}
These are details of the feacal sludge treatment plant tagged to the municipality.
{% endtab %}

{% tab title="Second Tab" %}
| Attribute                   | Type         | Required | Comments                                                                                                                                  |
| --------------------------- | ------------ | -------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Disposal station type       | String       | Y        | (FSTP, STP, decanting station, compost plant)                                                                                             |
| Status                      | String       | Y        | Select from options (under construction, constructed, operational, non-operational, N/A]. If transfer station and no treatment, then N/A. |
| Treatment type              | String       |          | Select from options ().                                                                                                                   |
| Construction vendor         | UUID         | Y        |                                                                                                                                           |
| Operating vendor            | UUID         | Y        |                                                                                                                                           |
| Capacity                    | Numeric      | Y        |                                                                                                                                           |
| Location                    | Geo ()       | Y        |                                                                                                                                           |
| ULB                         | String array | Y        |                                                                                                                                           |
| Associated lab              | UUID         | Y        |                                                                                                                                           |
| Employees                   | UUID array   | Y        |                                                                                                                                           |
| Consent to establish        | Doc          | Y        |                                                                                                                                           |
| Consent to operate          | Doc          | Y        |                                                                                                                                           |
| Treated effluent standards  |              |          |                                                                                                                                           |
| Treated biosolids standards |              |          |                                                                                                                                           |


{% endtab %}
{% endtabs %}

### Apply for Desludging

{% tabs %}
{% tab title="Description" %}
Citizen information that needs to be collected to accept and fulfill the desludging request.
{% endtab %}

{% tab title="Attributes" %}
| Attribute                         | Type            | Required | Comments                    |
| --------------------------------- | --------------- | -------- | --------------------------- |
| Contact                           | Numeric         | Y        |                             |
| Name                              | Numeric         | Y        |                             |
| Address                           | Address         | Y        |                             |
| Urgency level                     | String          | Y        |                             |
| Last desludged date               | Date            |          |                             |
| Onsite sanitation type            | String          |          |                             |
| Onsite sanitation measurements    | L\*B\*H OR D\*D |          |                             |
| Payment choice                    | String          | Y        | (Pre-service, post-service) |
| Number of trips                   | Numeric         | Y        |                             |
| Vehicle capacity                  | Numeric         | Y        |                             |
| Expected date of service delivery | Date            | Y        |                             |


{% endtab %}
{% endtabs %}

### Assign DSO Agency

{% tabs %}
{% tab title="Description" %}
The assignment of DSOs There are various models like ROTA, Price/Bidding, etc for DSO assignment. There are various models of DSO assignment: Rotational, Bidding, Availability-based.
{% endtab %}

{% tab title="Attributes" %}
| Attribute             | Type    | Required | Comments |
| --------------------- | ------- | -------- | -------- |
| Vehicle capacity      | Numeric | Y        |          |
| Vehicle availability  |         | Y        |          |
| Operating boundary    |         | Y        |          |
| Operating ward        |         | Y        |          |
| Last assigned request | Date    | Y        |          |


{% endtab %}
{% endtabs %}

### Assign vehicle&#x20;

{% tabs %}
{% tab title="Description" %}
Selection of vehicles available to service a request.
{% endtab %}

{% tab title="Attributes" %}
| Attribute            | Type | Required | Comments |
| -------------------- | ---- | -------- | -------- |
| Vehicle availability |      |          |          |
| Vehicle type         |      |          |          |
| Vehicle capacity     |      |          |          |
| DSO availability     |      |          |          |


{% endtab %}
{% endtabs %}

### Confirm disposal&#x20;

{% tabs %}
{% tab title="Description" %}
Details that need to be filled at the FSTP user interface to confirm that sludge being disposed of.
{% endtab %}

{% tab title="Attributes" %}
| Attribute          | Type      | Required | Comments |
| ------------------ | --------- | -------- | -------- |
| Vehicle            | UUID      | Y        |          |
| Trip number        | Numeric   | Y        |          |
| Volume             | Numeric   | Y        |          |
| Vehicle in-time    | Date time | Y        |          |
| Vehicle out-time   | Date time | Y        |          |
| Desludging request | UUID      | Y        |          |


{% endtab %}
{% endtabs %}

### Decline disposal&#x20;

{% tabs %}
{% tab title="Description" %}
Details that need to be filled at the feacal sludge treatment plant user interface to reject sludge disposal.
{% endtab %}

{% tab title="Attributes" %}
| Attribute            | Type    | Required | Comments                                                              |
| -------------------- | ------- | -------- | --------------------------------------------------------------------- |
| Vehicle              | UUID    | Y        |                                                                       |
| Trip number          | Numeric | Y        |                                                                       |
| Volume               | Numeric | Y        |                                                                       |
| Desludging request   | UUID    | Y        |                                                                       |
| Reason for declining | String  | Y        | (“Septage Source,” “Outside operational hours,” “Under Maintenance”). |


{% endtab %}
{% endtabs %}

### Calculate payment&#x20;

{% tabs %}
{% tab title="Description" %}
Information needed to calculate the cost of the service request.
{% endtab %}

{% tab title="Attributes" %}
| Attribute        | Type    | Required | Comments |
| ---------------- | ------- | -------- | -------- |
| Number of trips  | Numeric | Y        |          |
| Vehicle capacity | Numeric | Y        |          |
| Location type    | String  | Y        |          |
| Property type    | String  | Y        |          |


{% endtab %}
{% endtabs %}

### Complete service delivery&#x20;

{% tabs %}
{% tab title="Description" %}
Details needed to close a request by the DSO on their User Interface after servicing a request.
{% endtab %}

{% tab title="Attributes" %}
| Attribute       | Type    | Required | Comments |
| --------------- | ------- | -------- | -------- |
| Completion date | Date    | Y        |          |
| Number of trips | Numeric | Y        |          |
| DSO agency      | UUID    | Y        |          |
| Vehicle         | UUID    | Y        |          |


{% endtab %}
{% endtabs %}

### Rate service delivery&#x20;

{% tabs %}
{% tab title="Description" %}
Details filled by the citizen to rate a service.
{% endtab %}

{% tab title="Atributes" %}
|                              |      |   |   |
| ---------------------------- | ---- | - | - |
| Rate                         | Rate | Y |   |
| PPE use                      | Bool | Y |   |
| Spillage                     | Bool | Y |   |
| Additional service provision | Bool | Y |   |


{% endtab %}
{% endtabs %}
