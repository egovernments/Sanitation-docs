# Product Requirement Document (PRD)

## Introduction

Sanitation worker safety is of national importance. The national mandate for the same is issued under the “Emergency Response Sanitation Unit (ERSU)”. The Urban Management Centre (UMC) is leading the implementation of ERSU across Odisha. As part of ERSU, UMC along with the state of Odisha has rolled out a programme on sanitation worker benefits called 'Garima' whose main objective is to identify, monitor, and support sanitation workers and their families.

eGov is collaborating with UMC on “Sanitation worker safety” for Odisha, which includes building the platform and product capabilities for Garima&#x20;

### About UMC&#x20;

The Urban Management Centre is a non-profit organisation with a mission to “Make Cities Work for Everyone”. Since 1997, it has strengthened the local governance through technical support, policy formulation and implementation, and dedicated capacity building. The UMC works closely with the Government of India, as well as state governments across India. The UMC has institutionalised several key innovations in urban governance across India, including a shift towards service-level benchmarking of urban services, evidence-based planning, and capacity building of government stakeholders.

### About Garima

The Housing and Urban Development Department, Odisha, launched the Garima scheme in 2020. The statewide scheme aims to ensure the dignity and welfare of 20,000 core sanitation workers who are exposed to hazardous working conditions, including coming in close contact with faecal sludge in toilets, septic tanks, and sewer treatment facilities.&#x20;

The scheme highlights that the first step to empower sanitation workers is by recognising them as professionals entitled to safety, benefits, and rights with specific skill-sets and capabilities. To identify the number of sanitation workers, the state has rolled out a robust methodology to create a database of sanitation workers through the generation of unique IDs. The state has been able to create a dynamic database of 15,000-plus informal sanitation workers who can now avail the entitled benefits.&#x20;

**Objective**

The objective of the collaboration between eGov and UMC through an integration with Garima is to create a record of service delivery to:&#x20;

* Provide enumeration and benefits to sanitation workers.
* Identify the percentage of services with evidence of safe practices.

eGov, through its DIGIT FSM platform -  implemented in Odisha - can serve as a data capturing layer for the above and provide access to this information to UMC. The plan is to start with Phase 1. The following will be the scope of work across the partnership:&#x20;

<figure><img src="../../../.gitbook/assets/Screenshot 2023-12-14 at 9.58.26 AM.png" alt=""><figcaption></figcaption></figure>

**Scope of Work**

The UMC in Odisha has been able to create a unique database of 15,000-plus sanitation workers. This database will serve as a registry integrated with DIGIT FSM, to capture transactional information around data requests served by these workers. This information will further be made available to the UMC. The following will be a part of this:

1. Provision of ULB/DSO to assign one or more sanitation workers to each request:
   1. Sanitation workers will be made available via integration with the Garima database through API in the workflow.
   2. Since the Garima ID may not be well known to the ULB/DSO, a search functionality is to be made available via the entry of a phone number.
   3. Preview details of the selected sanitation worker for confirmation.
2. Capture sanitation worker details if a sanitation worker is not available in the Garima database. As per discussions with UMC, details required for the generation of a provisional Garima ID are First name, Last name, DOB, Gender, Mobile number and City details.&#x20;
3. Provide aggregated data around how many requests are served by date via unique Garima IDs by API to UMC.&#x20;
4. There will be no linking between the Garima worker and vendor done in Sujog FSM.

**Detailed Solution**

Along with assigning a vehicle, the DSO will assign sanitation workers to a request. The sanitation workers will be assigned by entering the Garima ID. If the Garima ID number exists in the database, details of the sanitation worker, that is, name and Garima ID to be displayed on the screen for the DSO to confirm. In case, the Garima ID does not exist, the DSO will enter sanitation worker details (First Name, Last Name, DOB, Gender, Mobile number). A DSO may assign one to many sanitation workers to a request. However, entering a minimum of one sanitation worker to a request is mandatory.&#x20;

The following data will be made available from Garima to Sujog via APIs:

* Details of sanitation workers registered in Garima (Name, Mobile Number and Garima ID).

The following data will be made available to UMC via APIs:

* Aggregated data around how many requests are served by date by unique Garima IDs by API to the UMC.

Workflow with Garima integration:

<figure><img src="https://lh7-us.googleusercontent.com/dQB2a0PQUg6_ZaMRxkW9xCM55NaPot7WXCPEf_kCWbDYKQq4fJ3vOzs_MoKzIRqgsLgydeASNT5txc2o8PHhqSFYxnSBk1HUgaHqPrFrEfuLHcZG5tYvuwGhK1rV44ilvGTx3lenWL24s46QzsNse6g" alt=""><figcaption></figcaption></figure>

What changes would affect which municipal, business and core services?

| Municipal Services | Business Services                              | Core Services   |                                                                               |                     |             |
| ------------------ | ---------------------------------------------- | --------------- | ----------------------------------------------------------------------------- | ------------------- | ----------- |
| What?              | How?                                           | What?           | How?                                                                          | What?               | How?        |
| FSM application    | Additional fields to enter sanitation workers. | API integration | API integration with Garima database to pull sanitation worker details.       | Dashboard analytics | <p><br></p> |
| Vendor driver      | No mapping for vendor  driver.                 | API creation    | Creation of API to provide access to unregistered sanitation worker database. | <p><br></p>         | <p><br></p> |
| Vehicle trip       | Driver will not be assigned.                   | Datamart report | Availability of data on Garima ID(s) tagged against each request.             | <p><br></p>         | <p><br></p> |

## Specifications

Updating Application | DSO in Progress

a. Adding sanitation worker

| Attribute            | Type   | Mandatory (Y/N) | Comments                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| -------------------- | ------ | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Garima ID (8 digits) | BIGINT | Y               | <ol><li>Assign sanitation worker to request along with vehicle screen.</li><li><p>Sanitation workers will be added at two levels</p><ol><li>Driver</li><li>Helpers</li></ol></li></ol><ol start="3"><li>Search by entering the Garima ID of the sanitation worker.</li></ol><ol start="4"><li><p>View of details fetched via API:</p><ol><li>Name</li><li>Garima ID</li><li>Phone number.</li></ol></li></ol><ol start="5"><li>It is mandatory to add at least 1 driver to the request.</li></ol><ol start="6"><li>Multiple helpers can be added, but it is not mandatory.</li></ol><ol start="7"><li>If a driver/helper is not available in the system, then there has to be an option to register a sanitation worker through provisional API provided by Garima and in response, we will get a provisional Garima ID.</li></ol><ol start="8"><li>A sanitation worker can be removed post selection by selecting the cross beside the sanitation worker name.</li></ol> |

b. Registering a new sanitation worker

| Attribute               | Type        | Mandatory (Y/N) | Comments                                   |
| ----------------------- | ----------- | --------------- | ------------------------------------------ |
| Last 4 digits of AADHAR | Number      | Y               | Validate only for numbers.                 |
| Name                    | <p><br></p> | Y               | Free text field.                           |
| Phone number            | Number      | Y               | <p>Validated for 10 digits.</p><p><br></p> |
| Date of birth           | Date        | Y               | <p><br></p>                                |
| Gender                  | Array       | Y               | Male/Female/ Transgender.                  |

### Change in the Backend&#x20;

| Backend Table                   | As Is                                                                          | With Garima                                                                                                                 | Action                                   |
| ------------------------------- | ------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------- |
| Driver table                    | Driver details are currently stored in the driver table in FSM.                | Driver details will be fetched from the Garima database.                                                                    | Deactivate the driver table.             |
| Driver vehicle table            | Currently, drivers and vehicles are mapped in the driver vehicle table in FSM. | There will be no driver vehicle mapping. Each transaction will be assigned to sanitation workers/drivers from the frontend. | Deactivate the driver vehicle table.     |
| Unregistered sanitation Workers | NA                                                                             | All details of sanitation workers without a Garima ID entered manually need to be stored in a database.                     | Create a table to store the information. |

## Design

Find the mock-ups below:

The DSO/ULB employee can assign a sanitation worker and vehicle in a single screen.&#x20;

<figure><img src="https://lh7-us.googleusercontent.com/YK-AtWU74c3tQ8MQOih4H8Mx8eGy4MKDpCm2ONjj41mZA-RkkbkbL1BbjI1N6vMjaxxFRFFzHr4F8MqTatLXIq1GqmeGZtujpK-0Y5x9kou8ApAgxGsg-OvbEyUbS3qd4tplxnXHBzTrGWAk3DpZcvo" alt=""><figcaption></figcaption></figure>

The DSO can assign the vehicle and search for a sanitation worker using the Garima ID. The exact available match is displayed.\
Note: When we search with the Garima ID, the API will return name and mobile number along with the searched ID.

* Single driver can be assigned.
* Multiple helpers can be assigned.

<figure><img src="https://lh7-us.googleusercontent.com/_IPiZ6DjdTtCpgqMJFVV_oh9K4vVECqTPBkDHa9iq0VZ_lpy8WaqlIjczzDRdyRLtXRbh_ZSezyKtWhiiYLHkA6DVWSvGHhijjF65A5y4dV97nSPm6BBYA83SwVwMSZvGnAXsXQSLDgielfSZkNvnUk" alt=""><figcaption></figcaption></figure>

If the searched worker is not available, an error message "Worker not found! Please register!"  is displayed. The DSO can register the sanitation worker by clicking on “Register New Sanitation Worker”. The sanitation worker can either be added as a driver or helper as per requirement

Once the details are filled , the DSO clicks on “Register and Assign”.

<figure><img src="https://lh7-us.googleusercontent.com/3wPPJwcIivmQy_2eSGBEDvo5iEeuxwFoInNN0_7rDb9S_5ypbEMOGXRDlVKDQOFtajCAhyrvgUF11__2oMbsSe0CByT4rhyf_gwl8RTeQXqr0b-BWzxCzDGbqVXUie7pmSq3Gi3nsYVCzfTq7UPBOIg" alt=""><figcaption></figcaption></figure>

The details of the worker should be auto-populated in the previous screen, that is, “Assign Vehicle and Sanitation Worker”.

<figure><img src="https://lh7-us.googleusercontent.com/B042pIxAMQj7nNW9uIPCRD_ICQ254qZk-C3aq0sW03pDRJSrbyqf84M_ioD93GON7JbSh7u4VbOy5dw43t5KxxgptvIQC1W6YmCV9Tnysh9PAyGJQ-EC69D71C4P_E7i7fbpgDkGwC_zI-BRg3_QVrU" alt=""><figcaption></figcaption></figure>

The sanitation worker is assigned and the details are displayed in the application page.

<figure><img src="https://lh7-us.googleusercontent.com/3aSh4NbNgMt9lUB-WcjiEooiWs53X_koTsrlExsmzyE3-XHnE2gM1DbXlr_AsxaAp_uVF4x9XZicnV5dDAc_dGuyXUdsMr7llVtynBuY4YESNsEjSJsq128uBZn9UZNoskk3hTat2ACYNqJm6leUyHc" alt=""><figcaption></figcaption></figure>

## Risks/Limitations

* There is no way to validate the correctness/uniqueness/verifiability of the Garima database.&#x20;
* For sanitation workers not available in the system, the same details will have to be added multiple times for requests assigned to the workers until they are included in the system.
* The collection of information on safety equipment used is based on citizen feedback and may not be accurate or complete.

## Out of Scope

The above solution should cover the majority of Garima use cases. However, there are scenarios that deviate from the options:

| A DSO assigns a sanitation worker who has not worked on the request.                             |
| ------------------------------------------------------------------------------------------------ |
| Multiple sanitation workers service a request. Only a subset of them are assigned in the system. |
