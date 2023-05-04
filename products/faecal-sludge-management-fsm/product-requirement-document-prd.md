# Product Requirement Document (PRD)

## Background

Urban-rural convergence is an initiative that aims to ensure access of sanitation services to all Gram Panchayats (GPs) via Urban Local Bodies (ULBs) located closest to them. With efforts in implementing decentralised waste management across 114 ULBs as well as enabling the rural population to avail sanitation facilities from urban areas located nearby, eGov with CPR (post-field observations and research) decided to include gram panchayats in the FSM application as part of this  initiative. &#x20;

## Introduction

Under the urban-rural convergence (U-RC) GPs are tagged to ULBs which will service desludging requests for households in the respective GPs. The process-flow across the value chain, and actors would remain the same. However, the logic of pricing and billing of requests from GPs may vary from requests within the limits of the ULB itself.

Currently, the factors that are being considered to determine pricing are :&#x20;

1. Location of the GP&#x20;
2. Distance of the GP from ULB&#x20;
3. Distance of GP from the FSTP

Considering these pricing inconsistencies, we are designing and releasing a simple version of the urban-rural convergence system. With the success of a statewide rollout, larger populations and households can have access to and benefit from the FSM module and subsequently the service with speed, and at scale.

#### Core Value Hypothesis

The users’ needs and the value this feature would provide are as follows:

1. If we allow households from GPs to raise (or ULBs to record) requests  in the FSM application, they will use it responsibly which would result in reduced public dumping with the waste collected and disposed of properly.
2. If we allow ULB admins to view inputs from GPs in the FSM module on the dashboard, they will use it responsibly and improve the quality of service by making better data-driven decisions.

## Solution - Quick Win

Using the above, we have outlined modifications in the FSM module to include gram panchayats:

A field/option to select gram panchayats tagged to a locality from a list to be provided while creating a New Desludging Application. The Amount per trip field will be changed to a free text field instead of an auto-calculated and auto-populated amounts field, and the demand will be generated based on the new amount added.&#x20;

As the actual amount will be known once the DSO/driver reaches the citizens’ location and sees the property + distance, an option to update the Amount per trip is provided where the user updates the trip to start the service.&#x20;

## Risk/Limitations&#x20;

Addressed in the Out of Scope section.

## Out of scope:

The above solution should cover the majority of U-RC use cases, but there are scenarios (edge cases)  that deviate from the options. Workarounds for the same are suggested here.

| Use Case                                                                       | Chance of Occurrence\* | Workaround                                                                                                                                                                                      |
| ------------------------------------------------------------------------------ | ---------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| A citizen from GP missed to select GP.                                         | >10%                   | <ol><li>Application can be rejected and updated if any amount has not been paid.</li><li>DSO can share information after inspection/before assigning sanitation workers and vehicles.</li></ol> |
| A citizen from GP missed to select GP and has paid the full amount in advance. | >1%                    |                                                                                                                                                                                                 |

\*assumption to be validated post launch.

From our on-ground research and observations, of the 40-60 requests the ULB receives for desludging, 4-7 of them are from GPs. This implies that approximately 10% of the total requests per month are from GPs. The above percentage of occurrence is within that 10%. These use cases will be handled in future versions.

## Detailed Solution

While creating a New Desludging Application, a radio button to select gram panchayats is provided. The list of GPs is shown in the dropdown and this field will be based on the Locality selected in the Location Details section. The radio button is selected by default on “Within ULB Limits”. By selecting gram panchayat and the name of the gram panchayat from the dropdown, the Amount per trip field (in the Payments Details) section is changed to a free text field. The total and advance are calculated based on the same.&#x20;

Based on field observations, the actual amount is only known once the vehicle reaches the citizens’ location. Hence, an additional field to edit the Amount per trip is provided along with the Update Trips in the pop-up before starting the service. The FSM calculator calculates the total amount and balance based on the same, and the billing service generates the demand accordingly.

#### Which municipal, business and core services would these changes affect?

| Municipal Services | Business Services                                                                                | Core Services |                                                      |                     |                                                                    |
| ------------------ | ------------------------------------------------------------------------------------------------ | ------------- | ---------------------------------------------------- | ------------------- | ------------------------------------------------------------------ |
| What?              | How?                                                                                             | What?         | How?                                                 | What?               | How?                                                               |
| FSM apply          | Additional field to enter GP                                                                     | location      | Additional field- GP + impact on geotag.             | Billing Service     | Bill generates based on the amount entered.                        |
| FSM calculator     | Calculation based on the amount entered instead of auto-calculation based on property type, etc. | mdms service  | New list of GPs tagged to the respective localities. | collections service | Demand generated based on the amount entered.                      |
| Vendor             | Check to see if the vendor is registered to serve the locality.                                  | reports       | New inputs from  GPs tagged to localities.           | Dashboard analytics | New inputs for analysis from  GPs tagged to respective localities. |
| Vehicle            | Check to see if the vehicle is registered to serve  the locality.                                | <p><br></p>   | <p><br></p>                                          | <p><br></p>         | <p><br></p>                                                        |

## Specifications

A new tenant service must be created in the MDMS for gram panchayats. The necessary updates as per the following must be made in fsm-address and fsm-geolocation entity list.

List of entities:

* ULB&#x20;

&#x20;     \- Locality

&#x20;        \- City

&#x20;        \- Gram panchayats\
