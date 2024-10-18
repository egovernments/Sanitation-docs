# Product Requirement Document

## Introduction&#x20;

Sanitation workers provide an invaluable service that many of us notice only when confronted with locked, blocked, or filthy toilets; overflowing septic tanks; or beaches contaminated with sewage. These workers are vital to the proper functioning of the sanitation systems that underpin daily life, and we need many more of them to achieve the ambitious agenda of Sustainable Development Goal (SDG) 6. Yet sanitation workers are often invisible and too often subject to conditions that expose them to the worst consequences of poor sanitation: debilitating infections, injuries, social stigma, and even death in their daily work. Workers’ rights need to be recognised; workers need freedom and support to organise as a labor force; and their working conditions need to be improved and progressively formalised to safeguard health and labor rights to ensure decent working conditions, as called for by SDG 8.

Sanitation workers range from permanent public or private employees with health benefits, pensions, and clear legal protections to some of the most marginalised, poor, and abused members of society who take on low-grade, labor-intensive, and dangerous work. For those employed informally, their work is financially precarious, with poor pay and few benefits. Sanitation workers often suffer weak legal protection, missing or weak standard operating procedures, and weak enforcement and oversight of laws and policies protecting their rights and health.

**Who is a Sanitation Worker?**

The term sanitation workers refers to all people — employed or otherwise — responsible for cleaning, maintaining, operating, or emptying a sanitation technology at any step of the sanitation chain. This includes toilet cleaners and caretakers in domestic, public, and institutional settings; those who empty pits and septic tanks once full and other faecal sludge handlers; those who clean sewers and manholes; and those who work at sewage and faecal waste treatment and disposal sites (_**Dalberg Advisors 2017; WHO 2018**_).

Key challenges associated with sanitation workers are as follows:

1. Multiple occupational and environmental hazards.
2. Weak legal protection of an invisible workforce.
3. Financial insecurity.
4. Social stigma and discrimination.

There have been considerable initiatives taken in India towards sanitation worker welfare. Some of these include:

1. Institutionalisation of safety practices through the implementation of ERSU.&#x20;
2. Loan financing via the National Safai Karamcharis Finance & Development Corporation (NSKFDC) for entrepreneurship and alternate skill development.
3. Training and skill development programmes towards safe sanitation.

For the implementation and execution of the above initiatives, the first step is to recognise sanitation workers as individuals entitled to safety, benefits and rights with specific skill-sets and capabilities. In certain states (Odisha, Tamil Nadu, and Maharashtra, to name a few), a database of sanitation workers is created through the generation of unique IDs. These aim to provide a formal identity to sanitation workers and further serve as a base for welfare programmes including medical coverage and student fee reimbursement. Training provided to these individuals, ensures that only trained professionals participate in the sanitation value chain. The second step is to monitor the participation of sanitation workers in service delivery to ensure safe sanitation by ensuring defined safety protocols are followed, and ensuring participation of trained sanitation workers in service delivery.

Keeping this in mind, **Sanitation Worker Welfare will be introduced as an extension to DIGIT Sanitation**.

1. V1: Introduction of sanitation worker database and recording participation of sanitation workers in service delivery.
2. V2: Implementation of the ERSU process on DIGIT.

Sanitation Worker Welfare will be rolled out across 2 versions:

## Success Criteria

| Goal                                                                                   | Category  | Objective                                                                                        | How will it be measured via the product?                    | How will we know this is successful?                                            |
| -------------------------------------------------------------------------------------- | --------- | ------------------------------------------------------------------------------------------------ | ----------------------------------------------------------- | ------------------------------------------------------------------------------- |
| Zero deaths, diseases, and environmental contamination resulting from poor sanitation. | Primary   | To ensure every sanitation worker has a valid identity so as to enable distribution of benefits. | Number of sanitation workers registered in the system.      | Increase in the number of sanitation Workers enrolled in the system over time.  |
| Zero deaths, diseases, and environmental contamination resulting from poor sanitation. | Secondary | To ensure only trained sanitation workers service requests.                                      | The percentage of requests serviced by trained sanitation.  | Increase in the percentage of requests serviced by trained sanitation.          |

## Scope: Sanitation Worker Welfare V1

The following is the scope of V1 for Sanitation Worker Welfare:

1. Maintaining a list of unique sanitation workers in DIGIT Sanitation through a sanitation worker registry:

* Viewing list&#x20;
* Adding a sanitation worker
* Updating details
* Disabling sanitation worker&#x20;
* Tagging sanitation workers to vendors

2. Recording participation of sanitation workers in service delivery by tagging sanitation workers to requests:

* Tagging multiple sanitation workers to a request
* Editing tagged sanitation workers
* SMS to sanitation Worker in case of request assignment
* Report

### 1. Sanitation Worker Registry

With the implementation of the sanitation worker database, we aim to create a unique, verifiable database of sanitation workers, each with a unique ID.

Specifications:

| <p><br></p>            | Type                                          | Mandatory | Editable (Y/N) | Unique within a tenant (Y/N) | Unique within an instance (Y/N) | Validation                                                                     |
| ---------------------- | --------------------------------------------- | --------- | -------------- | ---------------------------- | ------------------------------- | ------------------------------------------------------------------------------ |
| Sanitation worker name | Free text                                     | Y         | N              | N                            | N                               | N                                                                              |
| Sanitation worker ID   | Autogenerated                                 | Y         | N              | Y                            | Y                               | N                                                                              |
| Skills                 | Array, Multiselect                            | Y         | Y              | N                            | N                               | N (examples of these are Driving, Lab Operations, Plant Maintenance etc)       |
| Tenant ID              | Array, Multiselect                            | Y         | Y              | N                            | N                               | N (one sanitation worker may be performing roles in multiple tenants)          |
| Roles                  | Array/Multiselect                             | Y         | Y              | N                            | N                               | N (examples of this is driver, helper, treatment plant operator, lab operator) |
| Gender                 | Array                                         | N         | Y              | N                            | N                               | N                                                                              |
| DOB                    | Date                                          | N         | Y              | N                            | N                               | Must be minimum (Today - 18 years)                                             |
| Email address          | Free text (Email format)                      | N         | Y              | N                            | N                               | Follow email format                                                            |
| Phone number           | Number                                        | Y         | N              | N                            | N                               | Must have 10 digits                                                            |
| Status                 | Boolean                                       | Y         | Y              | N                            | N                               | N                                                                              |
| Employment type        | Array (Fixed/Contractual)                     | Y         | Y              | N                            | N                               | N                                                                              |
| Employer               | Array (ULB/Vendor)                            | Y         | Y              | N                            | N                               | N                                                                              |
| Vendor name            | Array (Populated based on vendors in the ULB) | Y         | Y              | N                            | N                               | N                                                                              |
| Photograph             | File                                          | N         | Y              | N                            | N                               | File size                                                                      |

Sanitation workers can be managed via the [**FSM Registry**](https://sanitation.digit.org/product/faecal-sludge-management-fsm/fsm-user-manual/fsm-employee-user-manual/manage-vendor-driver-and-vehicle-details) implemented as part of V1.3. The FSM Registry allows for ULB admins to manage the list of vendors, vehicles and drivers.

Changes required:

| Backend table                        | As Is                                                                          | With sanitation worker registry                                                                                             | Action                                           |
| ------------------------------------ | ------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------ |
| Driver Table                         | Driver details are currently stored in the driver table in FSM.                | Driver details will be fetched from the sanitation worker table.                                                            | Deactivate driver table.                         |
| Sanitation Worker Table              | NA                                                                             | Sanitation worker details will be stored in the sanitation worker table.                                                    | Create sanitation worker table.                  |
| Driver Vehicle Table                 | Currently, drivers and vehicles are mapped in the driver vehicle table in FSM. | There will be no driver vehicle mapping. Each transaction will be assigned to sanitation workers/drivers from the frontend. | Deactivate driver vehicle mapping table.         |
| Sanitation Worker and Vendor Mapping | NA                                                                             | Sanitation workers will be mapped to a vendor.                                                                              | Create a sanitation worker vendor mapping table. |

The following functionality will be available to the user via the frontend to manage sanitation worker database:

1. View list of sanitation workers
2. Adding a sanitation worker
3. Updating details
4. Disabling sanitation worker&#x20;
5. Tagging sanitation workers to vendors

#### Sanitation Worker: Noun Verb Mapping

| <p><br></p><p>Entities</p> | Actions     |             |             |             |            |             |
| -------------------------- | ----------- | ----------- | ----------- | ----------- | ---------- | ----------- |
| Create                     | Read        | Search      | Update      | Delete      | Deactivate |             |
| Sanitation Worker          | <p><br></p> | <p><br></p> | <p><br></p> | <p><br></p> | X          | <p><br></p> |

### 2. Recording Participation of Sanitation Workers in Service Delivery

Assign sanitation workers to a request:

Along with assigning a vehicle, the DSO will assign sanitation workers to a request. The sanitation workers will be assigned either by entering the unique SW ID or the phone number of the sanitation worker. If the unique SW ID/phone no. exists in the database, details of the sanitation worker, that is, name, phone number, SW ID, and photograph to be displayed on the screen for the DSO to confirm. In case the Garima ID/phone number does not exist, an error message will be displayed.

A DSO may assign one to many sanitation workers to a request. However, entering a minimum of one sanitation worker to a request is mandatory.

Specifications:

1. Updating Application | DSO in Progress

&#x20;       1.1 Tagging Sanitation Worker to Request

| Attribute                     | Type   | Mandatory (Y/N) | Comments                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ----------------------------- | ------ | --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SW ID (8 Digits)/Phone number | BIGINT | Y               | <ol><li>Post assigning vehicles, the “Take Action” button will show an option to assign sanitation workers. </li><li>Search by entering Garima ID and phone number of the sanitation worker.</li><li>View of details fetched via API:</li><li><p></p><ol><li>Name</li><li>Garima ID</li><li>Phone no.</li><li>Photograph</li></ol></li><li>Confirm sanitation workers.</li><li>It is mandatory to add atleast 1 sanitation worker to a request.</li><li>Edit of sanitation worker/workers possible by deleting a sanitation worker. </li></ol> |

2. Notification to Sanitation Worker

An SMS notification will be triggered to the sanitation worker when a request is assigned to them with the citizen name and phone number.

## Design&#x20;

Add a new sanitation worker by clicking on the ‘Add’ button on the FSM registry landing page and select Sanitation Worker User Actions. The following actions can be performed:

* Add a new vendor by clicking on vendor.&#x20;
* Add a new vehicle by clicking on vehicle.&#x20;
* Add a new sanitation worker by clicking on sanitation worker.&#x20;

On clicking on “Sanitation Worker”, the user will be redirected to the add the sanitation worker page.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-18 at 1.31.14 PM.png" alt=""><figcaption></figcaption></figure>

User Actions

The following actions can be performed:

* Enter the sanitation workers details. The fields are mentioned in the functional specifications table.&#x20;
* Go back by using the breadcrumbs.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-18 at 1.32.20 PM.png" alt=""><figcaption></figcaption></figure>

Once the user submits an application, a snack bar will confirm the successful addition of a sanitation worker.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-18 at 1.33.40 PM.png" alt=""><figcaption></figcaption></figure>

Details of the added sanitation worker will be displayed in the sanitation worker list on the top.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-18 at 1.34.32 PM.png" alt=""><figcaption></figcaption></figure>

#### View Sanitation Worker List

Login as an ULB admin and navigate to the FSM Registry by clicking on it. Click on the sanitation worker tab.A list of all sanitation workers in the system are visible along with the details of the vendor they are tagged to.&#x20;

User Actions&#x20;

The following actions can be performed:&#x20;

* View list of all sanitation workers in the system along with the details of tagged vendors.&#x20;
* Search for a sanitation worker using the search box. Results should be displayed in case of part match.&#x20;
* Clear search by using the “Clear Search” button&#x20;
* Enable/disable a sanitation worker by using the toggle.&#x20;
* Sort sanitation workers by creation date.&#x20;
* Add a new vendor, sanitation worker or vehicle by clicking on the ‘Add’ button.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-18 at 1.36.37 PM.png" alt=""><figcaption></figcaption></figure>

#### View and Edit Sanitation Worker

Sanitation worker details can be viewed by clicking on the sanitation worker’s name. All details of the sanitation worker captured while creating a sanitation worker will be displayed here.

User Actions&#x20;

The following actions can be performed:&#x20;

* View details of the sanitation worker.&#x20;
* Edit vendor tagging by clicking on the edit icon besides the vendor name.&#x20;
* Remove vendor tagging by clicking on the delete icon beside the vendor name.&#x20;
* Click on the “Take Action” button to edit or delete a vehicle.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-18 at 1.38.04 PM.png" alt=""><figcaption></figcaption></figure>

Sanitation worker details can be edited by clicking on the “Take Action" button and selecting edit.

User Actions The following actions can be performed:

* Click on edit to edit the sanitation worker.&#x20;
* Click on delete to delete the sanitation worker.&#x20;
* Click anywhere else on the screen to go back to the sanitation worker details.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-18 at 1.39.44 PM.png" alt=""><figcaption></figcaption></figure>

On clicking the Edit button, the user will be redirected to the “Edit Sanitation Worker” page.

User Actions&#x20;

The following actions can be performed:&#x20;

* Edit sanitation worker details.&#x20;
* Click on ‘Submit’.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-18 at 1.41.04 PM.png" alt=""><figcaption></figcaption></figure>

The user will be redirected to the sanitation worker details page and the edits will be reflected.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-18 at 1.41.45 PM.png" alt=""><figcaption></figcaption></figure>

The user will be redirected to the sanitation worker details page and the edits will be reflected. can be deleted by clicking on the “Take Action” button. The user will be redirected to the sanitation worker details page, and the edits will be reflected in the details page and selecting delete.

User Actions&#x20;

The following actions can be performed:&#x20;

* Click on Edit to edit the sanitation worker.&#x20;
* Click on Delete to delete the sanitation worker.&#x20;
* Click anywhere else on the screen to go back to the sanitation worker details.&#x20;
* On clicking the ‘Delete’ button, a pop-up will be displayed for confirmation.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-18 at 1.43.11 PM.png" alt=""><figcaption></figcaption></figure>

The following actions can be performed:

* Close the pop-up by clicking on the ‘Close’ button on the pop-up.
* Close the pop-up by clicking on the cross icon on the top right of the pop-up.
* Confirm deletion by clicking on the ‘Delete’ button.

On clicking on ‘Delete’, the user will be directed to a list of SW and a snack bar will be displayed as confirmation.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-18 at 1.44.10 PM.png" alt=""><figcaption></figcaption></figure>

#### Tagging a Sanitation Worker to a Vendor

Method 1:&#x20;

Apart from tagging a sanitation worker to a vendor from the sanitation worker details page, tagging can also be done from the sanitation worker details page by clicking on the add new vendor button.

User Actions

The following actions can be performed:

* View details of the sanitation worker.
* Tag SW to a vendor by clicking on the + icon besides the “Add New Vendor”.

A pop-up will be displayed with a dropdown to select a vendor.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-18 at 1.47.59 PM.png" alt=""><figcaption></figcaption></figure>

User Actions

The following actions can be performed:

* Selection of a vendor from the dropdown.
* Close pop-up by clicking on the cross icon on the top right of the pop-up.
* Close pop-up by clicking on ‘Cancel’.
* Confirm vendor selection by clicking on ‘Submit’.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-18 at 1.48.51 PM.png" alt=""><figcaption></figcaption></figure>

On clicking on submit, the added vendor details will be displayed in the sanitation worker details page and a snack bar is displayed for confirmation.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-18 at 1.49.40 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-18 at 1.50.08 PM.png" alt=""><figcaption></figcaption></figure>

Method 2:

A sanitation worker can also be tagged to a vendor from the sanitation worker list page. Select a vendor from the dropdown. The sanitation worker will be tagged to the selected vendor.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-18 at 1.51.05 PM.png" alt=""><figcaption></figcaption></figure>

### Recording the Participation of Sanitation Workers in Service Delivery

The DSO assigns a sanitation worker by clicking on the “Take Action” button and clicking an option of adding a vehicle and sanitation workers.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-18 at 1.52.02 PM.png" alt=""><figcaption></figcaption></figure>

A pop-up is displayed. The user can perform the following actions:

1. Select a vehicle number from dropdown. This is mandatory.
2. Assign a driver by typing the name or the sanitation worker ID in the search field. A list of matching results will be displayed and the user can select one. On selection, the name and sanitation worker will be displayed in the field. The driver can be edited by editing the field and retyping the name of the sanitation. This is mandatory
3. Assign helpers by typing the name or sanitation worker ID. A list of matching results will be displayed and the user can select multiple. The selected sanitation workers will be displayed below the field and the user can remove them by clicking on the cross beside their name. This is non mandatory.
4. The user can confirm the assignment by clicking on confirm.
5. The user can close the pop-up by clicking on the cross icon on the top right hand side of the pop up or clicking on the cancel button. No entered details will be saved in this case.
6. The assign button will only be activated once the vehicle and driver is selected.

Part search to be enabled for both fields.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-18 at 1.54.58 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-18 at 1.55.17 PM.png" alt=""><figcaption></figcaption></figure>

Sanitation worker details are displayed in the application in the DSO details section:&#x20;

1. Driver: Name and sanitation worker ID.
2. Sanitation 1: Name and sanitation worker ID.

If there are more than 1 sanitation worker assigned, multiple rows for sanitation workers will be visible. Driver and sanitation worker fields will not be displayed unless they are assigned.\


<figure><img src="../../.gitbook/assets/Screenshot 2023-09-18 at 1.57.01 PM.png" alt=""><figcaption></figcaption></figure>

## Out of Scope

1. Login for sanitation workers to accept/decline requests.
2. Login access via sanitation worker registry: Sanitation worker registries will contain information on drivers and treatment plant operators, who participate in the DIGIT sanitation workflow. Ideally, login for the product for the role should be via the registry. However, this will not be implemented.
3. Verification of whether the job roles tagged to the sanitation worker are the actual roles they are performing on field.
4. Verification of whether the correct sanitation worker is tagged to the request.
5. Verification of training status of sanitation workers will be maintained by the partner agency and we are dependent on them to compute the percentage.
6. Multiple sanitation workers service a request. Only a subset of them are assigned in the system.

## Implementation in Orissa

Sanitation worker safety is of national importance. The national mandate for the same is issued under “Emergency Response Sanitation Unit (ERSU)”. The Urban Management Centre (UMC) is leading the implementation of ERSU across Odisha. As part of ERSU, UMC along with the state of Odisha has also rolled out a programme for “Sanitation worker benefits” called 'Garima' whose main objective is to identify, monitor and support sanitation workers and their families.

eGov is collaborating with UMC on “Sanitation worker safety” for Odisha, which includes building platform and product capabilities for Garima. The objective of of the collaboration between eGov and UMC through an integration with Garima is to create a record of service delivery to:&#x20;

* Provide enumeration and benefits to sanitation workers
* Identify the percentage of services with evidence of safe practices

eGov, through its DIGIT FSM platform implemented in Odisha can serve as a data capturing layer for the above and provide access of this information to UMC. The following will be the scope of work across the partnership:&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-15 at 4.01.39 PM.png" alt=""><figcaption></figcaption></figure>

The Sanitation Worker Welfare module v1.0 will be rolled out to Orissa as part of Sujog v1.4. Click [**here**](broken-reference) to know more.&#x20;
