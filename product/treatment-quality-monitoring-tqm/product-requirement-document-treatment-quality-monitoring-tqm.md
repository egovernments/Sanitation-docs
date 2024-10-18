# Product Requirement Document: Treatment Quality Monitoring (TQM)

## Introduction

The waste value chain has 5 main stages:&#x20;

1. Generation
2. Containment
3. Transport
4. Treatment&#x20;
5. Reuse

For effective waste management, all of these stages need to be focused on. For example, improper containment of Faecal Sludge can lead to percolation of chemicals into the groundwater and its contamination, or ineffective transportation management can lead to waste being dumped illegally into surface water or land. Similarly, an essential part of effective waste management is the proper treatment of Waste.&#x20;

Ineffective treatment of waste and its discharge into the environment has a direct adverse impact on the environment and water quality. Effluents are often discharged into surface water sources. The poor quality of wastewater effluents is responsible for the degradation of the receiving surface water body and the health of its users.

Quality and re-use have a direct relationship: Treated waste output can be reused, be it recycled water or as compost. Acceptance of this by consumers will largely depend on its quality and the value it provides. Nobody wants water in their flush that stinks, or manure that does not fertilise plants enough.

Currently, there is little to no visibility of how waste is being handled and treated at the treatment plant. Keeping this in mind, a **Treatment Quality Monitoring (TQM) will be introduced as an extension to DIGIT Sanitation**.

## Objective

The objective is to improve the quality of treated waste

Our hypothesis of how treatment quality can be improved is as follows:&#x20;

1. Define Treatment Processes and Testing Requirements: Mapping of plants and treatment processes will allow for a consolidated view to the state/TSUs/stakeholders of the treatment processes operational at plants. Additionally, this will allow for the definition of  treatment requirements, frequencies and benchmarks at the state level for various processes and its adoption by plants. This further allows for analysis at the process level of treatment quality, and provides insights for improvements overtime.
2. Ensure Regular Testing: Operationalising regular and high-frequency testing  will allow for the detection of deviations from benchmarks at the earliest.
3. Quick Issue Resolution: Identification of deviations and its diagnosis via an analysis of current and historical data will allow for quick issue resolution.
4. Deepen Enquiry: Is a particular plant consistently performing badly? Is a particular treatment process regularly leading to poor quality output? Which step in the process flow is the deviation starting from? Do quality test results fluctuate often? Looking at trends in data can help deepen enquiry and identify problem areas.

Improvement in processes or a need for further enquiry can be operationalised by redefining treatment processes and testing requirements.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-01 at 11.40.19 AM.png" alt=""><figcaption></figcaption></figure>

## Definitions

| Plant             | <p>A facility that takes raw materials as inputs and converts them into a set out expected outputs through a series of setup processes and with the use of equipment operated by people.  </p><p><br></p> |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Treatment Process | Sequential series of steps required to translate input to output.                                                                                                                                         |
| Stages            | Each step within the treatment Process. Each job may have one or many input quality parameters and one or many output quality parameters.                                                                 |
| Assets            | Physical infrastructure required to execute a job in a treatment Process                                                                                                                                  |
| Parameters        | Criteria used to measure input and output for a job. Each parameter will have a unit of measurement.                                                                                                      |
| Frequency         | The duration of time between two subsequent tests                                                                                                                                                         |
| Benchmarks        | Acceptable value ranges for each parameter                                                                                                                                                                |
| Testing Standards | A combination of a Parameter, acceptable benchmark of the parameter and its frequency of testing. For example, ph >= 7 tested weekly                                                                      |

## Success Criteria

| Goal                                                                                  | Category  | Objective                                                                      | How will it be measured via the product                           | How will we know TQM is successful                                                   |
| ------------------------------------------------------------------------------------- | --------- | ------------------------------------------------------------------------------ | ----------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| Zero deaths, diseases, and environmental contamination resulting from poor sanitation | Primary   | To ensure treated waste is as per the quality standards                        | The percentage of plants with output quality is as per benchmarks | Increase in the percentage of plants with output quality as per benchmarks over time |
| Zero deaths, diseases, and environmental contamination resulting from poor sanitation | Secondary | To ensure treated waste is tested regularly for quick identification of issues | The percentage compliance against testing schedule                | Increase in the percentage compliance against testing schedule over time             |

## Design Guidelines

<table data-header-hidden><thead><tr><th width="175.5"></th><th></th></tr></thead><tbody><tr><td>1</td><td>The TQM module should be configurable for multiple waste streams such as faecal sludge, solid waste, medical waste, waste water etc.</td></tr><tr><td>2</td><td>The TQM module should be usable by itself without the need to set up/deploy the rest of the DIGIT FSM modules</td></tr><tr><td>3</td><td><p>In the design of DIGIT Sanitation v1.3, treatment plant operators are employees of a ULB<br><br></p><p>Based on our learnings, treatment plants can be managed by:</p><ol><li>Self-help groups (as in the case of Orissa and Trichy, Tamil Nadu). In such a case, a member of the SHG performs the role of a treatment plant operator.</li><li>Direct employees of the ULB (as in the case of some plants in Tamil Nadu).</li><li>Vendors who were outsourced on a build and manage model.</li></ol><p>Which requires the capability to enable vendors and individuals to be able to manage the operations, access and use the system. </p></td></tr><tr><td>4</td><td>Currently, in the product, there is a 1-to-1 mapping between ULBs and plants. The TQM module should allow for tagging as per the following:<br><br>Many plant - 1 boundary<br>1 boundary - 1 plant<br>Multiple boundaries - 1 plant</td></tr><tr><td>4</td><td><p>There are multiple operating models when it comes to lab testing and O&#x26;M of a treatment plant. Roles in the system need to be defined to support various operating models.<br></p><p>Case 1:</p><p>The treatment quality workflow defined in the PRD has two steps:</p><ol><li>Submission of sample to a lab</li><li>Uploading test results</li></ol><p>In the case of Orissa, where labs for testing the quality of treated waste are in-house, both these workflow steps are performed by the same person.  However, in Tamil Nadu, testing is outsourced to a central lab for 3 or 4 plants. In this case, the functionality to record test results will be provided to the labs. </p></td></tr></tbody></table>

## Proposed Solution

Given the objective to improve quality of treated waste and the steps required to achieve it, the following are needed at each stage:

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-01 at 2.58.55 PM.png" alt=""><figcaption></figcaption></figure>

Keeping this in mind, the following components will be available in the TQM module:

| Components             | Description                                                                                                                                                                                                                                                                                                                                                                                | Functionality                                                                                                                                                                                                                                                                                                 |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Schedule of Tests      | This component will be used by treatment plant operators and ULB employees to see the schedule of tests                                                                                                                                                                                                                                                                                    | <p>View schedule of  Lab tests and track compliance.</p><p>Track compliance of IoT test results and cases of failures.</p>                                                                                                                                                                                    |
| Recording Test Results | This component will be used by treatment plant operators and ULB employees to upload results manually and track IoT readings                                                                                                                                                                                                                                                               | <p>Create digital records of quality test results</p><p>Alerts in the following cases:</p><ol><li>IoT device not working</li></ol><ol><li>Lab results do not match IoT results</li></ol>                                                                                                                      |
| Anomaly Detection      | This component will be used by treatment plant operators and ULB employees to interpret test results                                                                                                                                                                                                                                                                                       | <p>Identify in real-time/near real time when results of a particular test are not as per benchmarks. </p><p>Alerts in the following cases:</p><ol><li>Results not upto benchmark</li></ol><p><br></p>                                                                                                         |
| Dashboards             | <p>This module will give stakeholders  insights and information regarding operations of the treatment plant. Users can use this to drill down and identify plants and processes where compliance to testing and/or test results are not upto benchmarks.  </p><p><br></p><p>Dashboards will also help users see trends over time to see patterns and identify long-term problem areas.</p> | <p>Dashboard to analyse trends in treatment quality and compliance with treatment schedule. Drill-down will be made available from state to ULB and to a plant level.</p><p><br></p><p>Dashboard to analyse patterns in issues. Drill-down will be made available from state to ULB and to a plant level.</p> |

The aim of the modules is to provide the users of the system information and control at each level - from defining how operations will be run, to updating status against pending operational tasks and viewing operational data to draw insights to refine operations.&#x20;

What is the value being generated?&#x20;

Through the above, we are looking to address the following challenges:

| Category                                                        | Challenge                                                                                                | How will the product address?                                      |
| --------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| Informational                                                   | No knowledge of treatment and disposal processes                                                         | Awareness on when waste has to be tested and for which parameters. |
| Changing Standards for treated waste                            | Operationalising changing standards of waste by configuring additional parameters/frequency for testing. |                                                                    |
| Operational                                                     | No record keeping of waste quality                                                                       | Record and maintain digital records of treatment quality.          |
| <p>No mechanism to monitor </p><p>treatment Plant operators</p> | Track and measure compliance against testing schedule.                                                   |                                                                    |
| No clear definitions of responsibilities for the ULB            | Setup via roles who are responsible for quality testing and issue resolution.                            |                                                                    |

The following value will be created for users:

| User                                                                                       | Value Bundle                                                                                                                                                                                                                                                                                                               |
| ------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| State administration/Pollution control board/Stakeholders (DDWS, WATSAN boards, WATCO etc) | <p>Ease of monitoring treatment quality, treatment quality trends and detect variations across plants.</p><p>Ease of monitoring and ensuring compliance to quality treatment schedule across plants.</p><p>Ability to change testing parameters and frequency basis test results across plants/for a particular plant.</p> |
| Urban local body                                                                           | <p>Ease of monitoring treatment quality and treatment quality trends and detect variations.</p><p>Ease of monitoring and ensuring compliance to quality treatment schedule.</p><p>Centralised view of issues across plants.</p><p>Ability to change testing and maintenance frequency basis test results.</p>              |
| Treatment plant operators/Vendors managing treatment plants                                | <p>Timely reminders to perform testing.</p><p>Ease of sharing records with ULB/stakeholders.</p>                                                                                                                                                                                                                           |

## Scope

### Treatment Quality Monitoring Workflow

The objective of the treatment quality module is to allow data observability of the parameters of treatment quality to improve the performance of the treatment plant. There are two ways to capture data:&#x20;

1. Manual input.
2. Automated capture of test results via configured IoT sensors. While the use of sensors reduces manual intervention in the process, the  availability of infrastructure on the ground is a challenge.&#x20;

Once the initial setup is done, the following image illustrates how the system will be used to monitor treatment quality:

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-04 at 9.14.26 AM.png" alt=""><figcaption></figcaption></figure>

Identified gaps:

1. Irregularity in laboratory testing.
2. Unavailability of actionable information on quality.

The flow will be as follows:

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-04 at 9.27.32 AM.png" alt=""><figcaption></figcaption></figure>

The scope of the Treatment Quality Module is as follows:

1. **Register Testing Standards**

A plant may have one or multiple treatment processes. For example:

1. An FSTP is dedicated to the treatment of faecal sludge such as the aerobic treatment process.
2. A co-treatment plant has two treatment processes: Faecal sludge and septage together.&#x20;

A treatment process has multiple stages/steps. In case of a plant with multiple processes, stages may converge.&#x20;

Define input/output quality testing requirements:

Each stage may have multiple input types and output types (for example, effluents and biosolids), and each stage may need to have the input and output quality tested for each of the input and output types.

The state and the ULB admin should be able to perform the following actions:&#x20;

* Define if one or many Input types needs to be tested for a particular stage.&#x20;
* Define if one or many output types need to be tested for a particular stage.&#x20;
* Enable/disable testing of a particular input/output type for a particular stage.

The UI screen for this should be enabled with the launch of workbench.

Define testing parameters, benchmarks and frequency:

* Testing parameters and benchmarks are set at the national/state level and adhered to by plants. However. based on the geographical location, the benchmarks may vary.
* Testing frequencies are set at the state level and adhered to by plants. These may be adjusted for plants, basis testing results.
* Each output and input type will have one or more testing standards (parameters, benchmarks, and frequency). For example, for output type ‘effluent’, one may need to test PH (daily), BOD (weekly) and COD (weekly).&#x20;
* For a particular plant, testing will be done by one or multiple methods including:

&#x20;      \- Manual testing in a lab&#x20;

&#x20;      \- Testing via IoT devices

The frequency of this will be different.

The state and the ULB admin should be able to perform the following actions:

* Define one or multiple testing standards (parameter, benchmark, and frequency) at an instance level.
* Edit testing Standards (parameter, benchmark, and frequency) for a plant.&#x20;
* Define different standards for manual and IoT-based testing for a particular input/output type for a stage.

This does not require a UI screen.

2. **Generation of Schedule**&#x20;

Schedule for tests will be auto-generated for various parameters based on the frequency.&#x20;

For manual tests, the schedule will be used to:&#x20;

* Display a list of upcoming tests to the plant operator and stakeholders.
* Generation of alerts for upcoming tests.
* Escalation in case of non-adherence to the test schedule.

For IoT tests, the schedule will be used to:

* Generate alerts in case a reading is not received as per the schedule.

Workflow:&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-04 at 11.15.39 AM.png" alt=""><figcaption></figcaption></figure>

Generation of Schedule: For the generation of schedule of testing:

For manual testing:

a. For 1 particular stage of the treatment process:&#x20;

1. Multiple parameters that have the same frequency to be combined to one test.
2. For parameters with different frequency, different tests should be created.

b. For 2 different stages of the treatment process:

1. The same parameter with the same frequency will be two different tests.

For IoT testing:

a. Multiple parameters captured by the same device will be a single test.

View Schedule:

The schedule will be available for view and action to the following users:&#x20;

a. For Labs&#x20;

1. ULB employee: \[X] days prior to test date (Inbox). \[X] here is configurable.&#x20;
2. Treatment plant operator: \[Y] days prior to test date (Inbox). \[Y] here is configurable.&#x20;
3. Treatment plant operator: \[Z] days prior to test date (as a pending task in the UI). \[Z] here is configurable.&#x20;
4. Tests will continue to remain in the inbox/pending tasks list as long as test results are not submitted.

b. For IoT Testing:

1. No schedule will be displayed to users.
2. Generation of alerts in case reading is not received as per schedule.

Escalations:

For Manual Testing: Escalations are triggered in the following case via an in-app alert:

| Role                           | Escalation                                                  |
| ------------------------------ | ----------------------------------------------------------- |
| Governing Body  + ULB employee | Test results pending beyond \[X] days as per test schedule  |

Record Test Results:

Test results may be recorded in 2 ways:

1. Manual Recording  by user (lab testing).
2. Automated recording via integration with IoT device.

For Manual Recording (Lab Testing)-

Recording of test results will be done by the user in two cases:

1. Recording results against schedule.
2. Recording Results on demand: Adhoc tests conducted/instructed by governing authorities.

Recording Results Against Schedule-

The process flow will start with the treatment plant operator receiving a notification regarding an upcoming test. The following is the process flow for the manual recording of test results:

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 9.18.15 AM.png" alt=""><figcaption></figcaption></figure>

Recording Results: Workflow

| Test Result Status | Roles                           | Action                    | Next Status     |
| ------------------ | ------------------------------- | ------------------------- | --------------- |
| Scheduled          | <p>FSTPO</p><p>ULB employee</p> | Submit sample for testing | Pending results |
| Pending results    | <p>FSTPO</p><p>ULB employee</p> | Update Results            | Submitted       |

1. The status of a scheduled test is auto set as “Scheduled”.
2. The sample has to be submitted to the lab (internal or external) for testing. The status of the same will be updated in the system by the user to “Pending Results”.
3. On recording test results, the status will be updated to “Scheduled”.

Recording Results On Demand-

The functionality will be made available to the record results on demand to the user.&#x20;

1. No workflow will be available in case of recording results on demand.
2. The user will be able to record results by filling a form.
3. Selection of a lab used for testing is optional in this case.
4. Status of submitted results will be set as ‘Submitted’.

Automated Recording Via Integration with IoT Device-

In case of integration with IoT devices, results against scheduled tests will be recorded. Alerts in case of non upload are mentioned in the alerts section below.

Anomaly Detection:

Anomalies will be generated in case of the following:

1. Lab results not as per the benchmark.
2. IoT device results are not as per the benchmark.
3. Lab results and device results do not match.
4. Device not working.

Lab results not as per the benchmark-&#x20;

This is to be generated when the manual test results uploaded by the test uploader are not as per the benchmarks defined (adjusted for deviations, configurable at plant level).

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 9.29.38 AM.png" alt=""><figcaption></figcaption></figure>

IoT results not as per the benchmark-&#x20;

This is to be generated when the loT test results recorded via the integration are not as per the benchmarks defined for \[X] days (adjusted for deviations defined while setting testing parameters).

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 9.32.05 AM.png" alt=""><figcaption></figcaption></figure>

Generation of alerts: Device results and lab results do not match-

In case the data that is recorded by the sensor does not match the data in the lab test result, an auto alert will be generated.

| Date to be matched on | <p>Sample collection Date</p><p><br></p><p>If IoT result is not available for the sample collection date, the closest date after for which the IoT data is available will be considered</p> |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Deviation allowed     | X%                                                                                                                                                                                          |

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 9.34.21 AM.png" alt=""><figcaption></figcaption></figure>

Generation of alert: No reading received from the device-

In case no reading is received from the sensor based on the schedule, an auto alert will be generated in the system.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 9.35.21 AM.png" alt=""><figcaption></figcaption></figure>

## Treatment Quality Monitoring: Functional Specifications

1. Treatment Process

<table data-header-hidden><thead><tr><th></th><th></th><th width="287"></th><th></th><th></th></tr></thead><tbody><tr><td>Attribute</td><td>Type</td><td>Mandatory</td><td>Comments</td><td>Validation Required?</td></tr><tr><td>Treatment Process ID</td><td>Numeric</td><td>Y</td><td>Auto-generated numeric value which will act as a unique identifier for a process flow</td><td>N, this value should be system generated</td></tr><tr><td><p>Process Name</p><p><br><br><br><br><br><br></p></td><td>Text</td><td>Y</td><td>This is the commonly used identifier for the process flow</td><td>Max characters - 256</td></tr><tr><td>Status</td><td>Array</td><td>Y</td><td>Status of the process flow</td><td>Active/Inactive, Single Select</td></tr><tr><td>Treatment Process Type</td><td>Array</td><td>Y</td><td>The dropdown will be auto populated basis the list of waste maintained in the MDMS</td><td><p>Single Select</p><p><br><br></p></td></tr><tr><td>Treatment Process Subtype</td><td>Array</td><td>Y</td><td>The dropdown will be auto populated basis the list of waste maintained in the MDMS</td><td><p>Single Select</p><p><br><br></p></td></tr></tbody></table>

2. Plants

| Attribute                                        | Type     | Mandatory | Comments                                                                       | Validation Required?                                         |
| ------------------------------------------------ | -------- | --------- | ------------------------------------------------------------------------------ | ------------------------------------------------------------ |
| Plant ID                                         | Numeric  | Y         | Auto-generated numeric value which will act as a unique identifier for a plan. | Auto-generated                                               |
| <p>Plant Name</p><p><br><br><br><br><br><br></p> | Text     | Y         | This is the commonly used identifier for the plant                             | Maximum charatcters - 128                                    |
| Plant Type                                       | Array    | Y         | <p><br></p>                                                                    | Single select only, faecal sludge, solid waste, co-treatment |
| Tenant Id                                        | Text     | Y         | <p><br></p>                                                                    | <p><br></p>                                                  |
| Status                                           | Array    | Y         | Status of the plant                                                            | Active/inactive, single select                               |
| Geolocation                                      | Lat,Long | Y         | <p><br></p>                                                                    | Capture the exact latitude-longitude                         |

3. Stages

| Attribute                                        | Type    | Mandatory | Comments                                                                                                                                                                                                                              | Validation Required?                                           |
| ------------------------------------------------ | ------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| Stage ID                                         | Numeric | Y         | Auto-generated numeric value which will act as a unique identifier for a Job ID                                                                                                                                                       | Auto-generated                                                 |
| <p>Stage Name</p><p><br><br><br><br><br><br></p> | Text    | Y         | This is the commonly-used identifier for the Job                                                                                                                                                                                      | <p>Maximum characters - 128</p><p>Minimum xharacters - NA </p> |
| Status                                           | Boolean | Y         | Status of the stage                                                                                                                                                                                                                   | Active/inactive, single select                                 |
| Input Quality Measurement Required               | Boolean | Y         | This selection will allow the user to set up if the  input quality for the particular input type needs to be monitored. A user should be able to enable and disable input quality measurement requirement independently for each type | Yes/no, single select                                          |
| Output Type                                      | Array   | Y         | The dropdown will be auto-populated basis the list of output types                                                                                                                                                                    | Multi-select                                                   |
| Output Quality Measurement Required              | Boolean | Y         | This selection will allow the user to set up if the output quality for the particular job needs to be monitored. A user should be able to enable and disable the output quality measurement requirement independently for each type   | <p>Yes/no, single select</p><p><br><br></p>                    |

4. Testing Parameters

| Attribute                                    | Type    | Mandatory | Validation                                                                                                                                              |
| -------------------------------------------- | ------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Quality Parameter                            | Array   | Y         | <p>Selecting from the predefined of the above-mentioned quality parameters and standards.</p><p>single select</p>                                       |
| Quality Parameter Unit of Measurement        | Array   | Y         | Selection of the unit of measurement (mg/L, Absolute value etc). Single select                                                                          |
| Benchmark Rule                               | Array   | Y         | Options include X>=,<=R, =\<Y and >=Z, single select                                                                                                    |
| Benchmark Value                              | Numeric | Y         | Entered by user, numeric only                                                                                                                           |
| Testing Frequency - Manual (Days)            | Numeric | Y         | Selecting a custom frequency range for laboratory testing based on consent to operate, numeric only                                                     |
| Monitoring Frequency - Quality Sensor (Days) | Numeric | N         | <p>Selecting a custom frequency</p><p><br></p><p>Note: Should be optional if the ULB/state choses not to have sensor-based monitoring. Numeric only</p> |

5. Configure IoT Devices

| Attribute            | Type     | Required?   | Comments                                                                                                                   |
| -------------------- | -------- | ----------- | -------------------------------------------------------------------------------------------------------------------------- |
| Configuration Date   | Datetime | Y           | <p><br></p>                                                                                                                |
| Device Type          | Text     | Y           | <p>Selection from the device master data</p><p><br></p><p>[“GPS Sensor”, “pH Sensor”, “Accelerometer”, “Light Sensor”]</p> |
| Plant                | Text     | Y           | <p><br></p>                                                                                                                |
| Treatment Process    | Text     | Y           | <p><br></p>                                                                                                                |
| Stage                | Text     | Y           | <p><br></p>                                                                                                                |
| Output Type          | Text     | Y           | <p><br></p>                                                                                                                |
| Parameters           | Array    | Y           | The parameters are monitored by the device                                                                                 |
| Monitoring Frequency | Numeric  | Y           | Custom frequency for the device                                                                                            |
| Calibration Date     | Datetime | Y           | Input from the user about any change in the calibration/maintenance of the device                                          |
| Calibration Accuracy | Array    | Y           | Range to indicate the permissible deviation in the accuracy                                                                |
| IsConnected?         | Boolean  | Y           | To indicate the connectivity of the device                                                                                 |
| Connectivity History | ?        | Y           | Date-wise device audit log to know the connectivity status                                                                 |
| Verification History | ?        | <p><br></p> | Date-wise device verification log to know the days when device input was verified with laboratory results                  |

6. Testing Schedule

| Attribute              | Type         | Mandataroy  | Validation                                                                                                                                                                                                                                                                                                      |
| ---------------------- | ------------ | ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Test ID                | Alphanumeric | View only   | Auto-generated on the creation of schedule                                                                                                                                                                                                                                                                      |
| Plant Name             | Text         | View only   | Auto-populated on the creation of schedule                                                                                                                                                                                                                                                                      |
| Treatment Process      | Text         | View only   | Auto-populated on the creation of schedule                                                                                                                                                                                                                                                                      |
| Treatment Process Type | Text         | View only   | Auto-populated on the creation of schedule                                                                                                                                                                                                                                                                      |
| Stage                  | Text         | View only   | Auto-populated on the creation of schedule                                                                                                                                                                                                                                                                      |
| Output Type            | Text         | View only   | Auto-populated on the creation of schedule                                                                                                                                                                                                                                                                      |
| Test Type              | Array        | <p><br></p> | Lab/IoT, auto-selected to Lab                                                                                                                                                                                                                                                                                   |
| Parameter 1…n          | Text         | View only   | Auto-populated on the creation of schedule                                                                                                                                                                                                                                                                      |
| Testing Date           | Date         | View only   | Date calculated through the predefined laboratory testing schedule                                                                                                                                                                                                                                              |
| SLA                    | Numeric      | View only   | Difference between the current date and testing date: The compliance to a testing schedule can be checked through this field. However, the actions based on failed/successful compliance falls under vendor management, which is not in scope currently and will be taken up separately under vendor management |
| Status                 | Text         | View only   | Status to be auto set to ‘Scheduled’                                                                                                                                                                                                                                                                            |

7. Test Results

| Attribute              | Type     | Required?   | Comments                                                                                                                          |
| ---------------------- | -------- | ----------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Test ID                | Numeric  | Y           | Auto-generated by system                                                                                                          |
| Plant Name             | Array    | View only   | Auto-populated on the creation of schedule, single select for on-demand test                                                      |
| Treatment Process      | Array    | View only   | Auto-populated on the creation of schedule, single select for on-demand test                                                      |
| Treatment Process Type | Array    | View only   | Auto-populated on the creation of schedule, single select for on-demand test                                                      |
| Stage                  | Array    | View only   | Auto-populated on the creation of schedule, single select for on-demand test                                                      |
| Output Type            | Array    | View only   | Auto-populated on the creation of schedule, single select for on-demand test                                                      |
| Test Type              | Array    | <p><br></p> | Lab/IoT, auto-selected to lab for on demand                                                                                       |
| Lab Submitted to       | Text     | Y           | This will not be required in case test type = IoT                                                                                 |
| Quality Parameter 1    | Numeric  | Y           | Validation to be applied at impel                                                                                                 |
| Quality Parameter 2    | Numeric  | Y           | Validation to be applied at impel                                                                                                 |
| Quality Parameter 3    | Numeric  | Y           | Validation to be applied at impel                                                                                                 |
| Quality Parameter n    | Numeric  | Y           | Validation to be applied at impel                                                                                                 |
| Collection Time        | Date     | Y           | This is the date-time during which the user updates status to pending Results. for IoT, this is the time sensor records reading   |
| Attachment             | Document | Y           | For a given collection location, photo or PDF proof of laboratory result mentioning the information of above-mentioned parameters |

8. Alert: Lab and IoT Result Not As Per the Benchmark; Lab and Device Results Do Not Match

| Attribute      | Type     | Required? | Comments                                                                                              |
| -------------- | -------- | --------- | ----------------------------------------------------------------------------------------------------- |
| Alert DateTime | Datetime | Y         | Auto-captured based on date-time                                                                      |
| Alert Type     | Text     | Y         | <p>Auto-captured</p><p><br></p><ul><li>Lab test results not as per the benchmark</li></ul><p><br></p> |
| Plant Name     | Text     | Y         | <p><br></p>                                                                                           |
| Process Name   | Text     | Y         | <p><br></p>                                                                                           |
| Process Type   | Text     | Y         | <p><br></p>                                                                                           |
| Parameter 1…n  | Text     | Y         | <p><br></p>                                                                                           |
| UoM            | Text     | Y         | <p><br></p>                                                                                           |
| Benchmark      | Number   | Y         | <p><br></p>                                                                                           |
| Results        | Number   | Y         | <p><br></p>                                                                                           |
| Test Type      | Text     | Y         | Auto-selected to lab/IoT, or both                                                                     |

9. Alert: No Reading Received From the Device

| Attribute      | Type     | Required? | Comments                                                                  |
| -------------- | -------- | --------- | ------------------------------------------------------------------------- |
| Alert DateTime | Datetime | Y         | Auto captured based on date-time                                          |
| Alert Type     | Text     | Y         | <p>Auto captured</p><ul><li>No reading received from the device</li></ul> |
| Plant Name     | Text     | Y         | <p><br></p>                                                               |
| Process Name   | Text     | Y         | <p><br></p>                                                               |
| Process Type   | Text     | Y         | <p><br></p>                                                               |
| Device ID      | Numeric  | Y         | <p><br></p>                                                               |

## Sensor Monitoring

Below is an illustration of the communication between monitoring sensor and DIGIT:

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 9.55.57 AM.png" alt=""><figcaption></figcaption></figure>

* Monitoring sensor - Communicates the actual readings (in AMP etc) to the vendor’s system.
* Sensor vendor - Converts the readings into the values against the parameters.
* Sensor adaptor - Communicates the values through the standardised APIs designed by DIGIT.
* Sensors will be installed at one or multiple stages of the plant, and device details will be recorded in the system.&#x20;
* Sensor monitoring: The user will have a view of all the devices available at the plant along with their status using the sensor monitoring tab at the front end.

## Treatment Quality Monitoring: Dashboard

The TQM dashboard will be made available to both the TRP, the ULB admin and the state admin. The access to data in the dashboard will be based on the following roles:

1. TRP will be available to view dashboard only for the assigned plant.
2. The ULB admin will be able to view the dashboard for all the plants in the ULB.
3. The state admin will be able to view the dashboard for all the plants in the ULB.

Navigation:

On landing on the dashboard, the user can navigate across treatment process types, to view the dashboard specific to the treatment process type.

Filters:

1. Date range: Users should be able to filter based on the date range.
2. ULB: Users should be able to filter based on the ULB. For plant TRP and ULB employees, the ULB is auto-selected to the ULB the plant and employee is tagged to. For a state user, all ULBs are available.
3. Plant: Users should be able to filter based on the plant: For plant TRP, plants that the TRP is tagged to is auto-selected. For ULB employees, plants tagged to the ULB to which the employee belongs should be available in the dropdown. For a state user, all plants are available.

Other functionalities:

Share:&#x20;

* Users should be able to share a filtered dashboard over WhatsApp in an image format.
* Users should be able to share filtered charts/tables over WhatsApp in an image format.

Download:&#x20;

* Users should be able to download the filtered dashboard in PDF and image formats.
* Users should be able to download filtered charts/tables in PDF and image formats.

Metrics:

Overall KPIs- The dashboard will display the following KPIs:

* Total incoming sludge: The sum of the total sludge that is disposed of at the plant for the selected time period.
* Number of trips: A count of the total incoming vehicles at the treatment plant for the selected time period.
* Overall quality: The number of tests where all parameters are as per the benchmarks as compared to the total number of test results recorded.
* Compliance percentage: The percentage of tests where results have been recorded.
* Total alerts: A count of the total alerts raised of the following types: Test results not as per the benchmark, no reading from the IoT device, and lab results and IoT results not matching.

Treatment Quality Overview:&#x20;

KPIs:

* Total plants: A count of the unique plants for the particular treatment process.
* Count of plants who have passed the treatment quality as per the last recorded test.
* Count of plants who have failed the treatment quality as per the last recorded test.
* Treatment quality is said to have passed if all parameters for final output(s) of a treatment process are as per the benchmarks.&#x20;
* Treatment quality is said to have failed if one or more parameters for final output(s) of a treatment process is not as per the benchmarks.

Map:

A map view of the location of each plant will be displayed as part of the dashboard. Plants here will be colour coded, based on whether it has passed/failed the treatment quality. (Red = Failed, Green = passed).

Table:

A table will be available on the plant-wise details of the test results (pass/fail) and compliance percentage. This will be as per the last test result. The user will also be able to see a change in the compliance percentage as compared to the last month. A drilldown will be made available for a plant via this table. For TRP users and ULBs where only one plant is tagged for the process type, the drilled table is automatically visible.On drilldown, the following is viewable to the user:

1. Heading - Name of the plant.
2. Table displaying the following fields:

&#x20;       a. Stage, output type, value of parameters, and compliance percentage.

&#x20;       b. Button to view the trends for a particular stage.

3. Toggle to toggle between IoT readings and lab results.

Trends of parameter readings:

This chart will be available once the user clicks on the view trend button in the table button.

The table shows the trend for one parameter over time, and provides a view of the benchmark for comparison. A toggle is available to navigate between the parameters. Detailed metric details for the Treatment Quality Monitoring dashboard are viewable below:

| [S.No](http://s.no/) | Section Heading                     | Chart Heading            | Subheading | Definitions ((This will appear on the dashboard whenever a user hovers on the metric wherever applicable))                                                                              | Chart Type       | X-Axis     | Y-Axis          | Value                                                                                                                         | Columns                                            | How to calculate                                                                                                                                                                                                                                                                                                                                               | Boundary         | Dtill down/Toggle | Comparsion KPIs, if any | Show comparison in | Specific to State/ULB/ TRP/all | Tooltip on Hover on Data Point                          | Input Fields |
| -------------------- | ----------------------------------- | ------------------------ | ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | ---------- | --------------- | ----------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | ----------------- | ----------------------- | ------------------ | ------------------------------ | ------------------------------------------------------- | ------------ |
| 1                    | Input                               | Total Incoming Sludge    | NA         | Total Incoming sludge from registered and unregistered vehicles                                                                                                                         | KPI              | NA         | NA              | Total Incoming Sludge                                                                                                         | NA                                                 | Total incoming sludge = (Volume of Waste Disposed for Registered Vehicles) + (Volume of Waste Disposed for Unregistered Vehicles)                                                                                                                                                                                                                              | State, Plant ULB | NA                | NA                      | NA                 | NA                             |                                                         |              |
| 2                    | Input                               | # incoming trips         | NA         | Number of trips disposed at the Treatment plant                                                                                                                                         | KPI              | NA         | NA              | Count of Trips to the Treatment plant from registered and unregistered vehicles                                               | NA                                                 | Number of trips disposed = Count(DISTINCT Trip ID)                                                                                                                                                                                                                                                                                                             | State, Plant ULB | NA                | NA                      | NA                 | NA                             |                                                         |              |
| 3                    | Treatment Quality                   | Overall Quality          | NA         | % of tests where all parameters are as per benchmarks                                                                                                                                   | KPI              | NA         | NA              | % of test results meeting benchmarks                                                                                          | NA                                                 | Overall Quality = (Number of tests where all parameters meet benchmarks / Total number of tests) \* 100                                                                                                                                                                                                                                                        | State, Plant ULB | NA                | NA                      | NA                 | NA                             |                                                         |              |
| 4                    | Treatment Quality                   | Compliance               | NA         | % of tests where results have been recorded                                                                                                                                             | KPI              | NA         | NA              | % of tests with Status as submitted out of total tests                                                                        |                                                    | Compliance % = (Count of Test ID in status 'Submitted' / Count (Distinct Trip ID) \* 100                                                                                                                                                                                                                                                                       | State, Plant ULB | NA                | NA                      | NA                 | NA                             |                                                         |              |
| 5                    | Alerts                              | Total Alerts             | NA         | Total Alerts raised by the system in the following categories: 1) Test Results not as per benchmark 2) No reading from IoT device 3) Lab results and IoT results not matching           | KPI              | NA         | NA              | Total Alerts                                                                                                                  |                                                    | Count(DISTINCT AlertID)                                                                                                                                                                                                                                                                                                                                        | State, Plant ULB | NA                | NA                      | NA                 | NA                             |                                                         |              |
| 6                    | Treatment Quality Plants            | Total Plants             | NA         | NA                                                                                                                                                                                      | NA               | NA         | NA              | Count of Plants                                                                                                               |                                                    | Count (Distinct PlantID)                                                                                                                                                                                                                                                                                                                                       | State, Plant ULB | NA                | NA                      | NA                 | NA                             |                                                         |              |
| 7                    | Treatment Quality Plants            | Treatment Quality Passed | NA         | Treatment quality is considered passed if all parameters of both Biosolids and Effluents are as per benchmarks for the output of the Treatment Process in the last test recorded.       | NA               | NA         | NA              | Count of Plants with Treatment Quality Passed                                                                                 |                                                    | <p>Treatment Quality for Output type =IF(COUNTIF(All Parameters Meet Benchmarks, FALSE) = 0, "Treatment Quality for Output type passed ", "Treatment Quality for Output type failed")<br><br>Treatment Quality for Plant passed = =IF(COUNTIF(Treatment Quality for Output type, FALSE) = 0, " Treatment Quality Passed ", "Treatment Quality Failed")<br></p> | State, Plant ULB | NA                | NA                      | NA                 | NA                             |                                                         |              |
| 8                    | Treatment Quality Plants            | Treatment Quality Failed | NA         | Treatment quality is considered failed when 1 or more parameters of Biosolids or Effluents are not as per benchmarks for the output of the Treatment Process in the last test recorded. | NA               | NA         | NA              | Count of Plants with Treatment Quality Failed                                                                                 |                                                    | Count (Distinct PlantID) - Treatment Quality Passed                                                                                                                                                                                                                                                                                                            | State, Plant ULB | NA                | NA                      | NA                 | NA                             |                                                         |              |
| 9                    | Treatment Quality Plants            | NA                       | NA         | NA                                                                                                                                                                                      | Map              | NA         | NA              | <p>Point = Geolocation of Plant<br>Plant Icon Colour - Green if Treatment Quality Passed, Red if Treatment Quality Failed</p> |                                                    | Same as [S.No](http://s.no/) 7 and [S.No](http://s.no/) 8                                                                                                                                                                                                                                                                                                      | State, Plant ULB | NA                | NA                      | NA                 | NA                             | Name of Plant                                           |              |
| 10                   | Treatment Quality Plants            | NA                       | NA         | NA                                                                                                                                                                                      | Table            | NA         | NA              | NA                                                                                                                            | Plant Name, Test Result, Compliance %              | Test Result Same as S.No 7 and S.No 8                                                                                                                                                                                                                                                                                                                          | State, Plant ULB | NA                | NA                      | NA                 | NA                             |                                                         |              |
| 11                   | Treatment Quality Plants            | NA                       | NA         | NA                                                                                                                                                                                      | Table            | NA         | NA              | NA                                                                                                                            | Stage, Output Type, Parameters 1...n, Compliance % | Mentioned above                                                                                                                                                                                                                                                                                                                                                | State, Plant ULB | NA                | Compliance %            | % from last month  | NA                             |                                                         |              |
| 12                   | Trend in \[Parameter Name] Readings | NA                       | NA         | NA                                                                                                                                                                                      | Multi-Line Chart | Test Dates | Parameter Value | <p>- Value of Device Reading<br>- Value of Lab results</p>                                                                    | NA                                                 | NA                                                                                                                                                                                                                                                                                                                                                             | Plant            | NA                | NA                      | NA                 | NA                             | <p>Date<br>Lab result - X<br>Device Reading - Y<br></p> |              |

Guided navigation:

If the user clicks on the help button, it will give a walkthrough of the entire screen, including the role of each button placed with two buttons:

* Skip: If the user wants to skip the walkthrough at any point.
* Next: It will proceed to the next action aligned.

## Treatment Quality Monitoring: Noun Verb Mapping

| <p><br></p><p>Entities</p> | Actions     |             |             |             |             |             |
| -------------------------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| Create                     | Read        | Search      | Update      | Delete      | Deactivate  |             |
| Test Schedule              | X           | <p><br></p> | <p><br></p> | X           | X           | <p><br></p> |
| Status                     | X           | <p><br></p> | <p><br></p> | <p><br></p> | <p><br></p> | <p><br></p> |
| Lab Result (Evidence)      | <p><br></p> | <p><br></p> | <p><br></p> | X           | X           | <p><br></p> |
| Device Result              | <p><br></p> | <p><br></p> | <p><br></p> | X           | X           | <p><br></p> |
| Anomalieis                 | X           | <p><br></p> | <p><br></p> | <p><br></p> | <p><br></p> | <p><br></p> |

## Roles

There are multiple business models when it comes to lab testing and O\&M of a treatment plant. In case of some FSTPs in Tamil Nadu, treatment plant operators are employees of a vendor who have a build-and-manage-model, and are directly responsible for resolving issues. Some FSTPs have an in-house lab to test the quality, whereas others send samples to other labs for testing. In certain cases, the ULB employee is responsible for testing and resolution of issues. Keeping this in mind, it is imperative that we design roles in the system in a flexible way such that the product can be implemented in various models.\


| Super Admin      | All                                                                                                                                                                                                                                                                                                                  |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Plant Admin      | <ol><li>Create, edit and disable plants</li><li>Create, edit and disable Workcentres</li><li>Create, edit and disable assets</li><li>Create, edit and disable Devices</li><li>Map assets and devices</li><li>Map process flow and workcentres</li><li>Map assets and jobs</li><li>Set up escalation matrix</li></ol> |
| Process Admin    | <ol><li>Create, edit and disable process flow</li><li>Create, edit and disable Jobs</li><li>Map jobs and process flow</li></ol>                                                                                                                                                                                      |
| Test Viewer      | 1) View upcoming tests and status                                                                                                                                                                                                                                                                                    |
| Plant Operator   | 1) Update status of test to Sample Submitted                                                                                                                                                                                                                                                                         |
| Test Uploader    | 1) Upload test results                                                                                                                                                                                                                                                                                               |
| Dashboard Viewer | 1) View dashboards                                                                                                                                                                                                                                                                                                   |

See noun verb mapping for roles below:

<table><thead><tr><th width="303">Platform: Master: Overall Scope</th><th></th><th></th><th></th><th></th><th></th><th></th></tr></thead><tbody><tr><td>Entity</td><td>Actions</td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Create (C)</td><td>Read (R)</td><td>Search (S)</td><td>Update (U)</td><td>Delete (D)</td><td>Deactivate</td><td></td></tr><tr><td>Process Flows</td><td></td><td></td><td></td><td></td><td>X</td><td></td></tr><tr><td>Jobs</td><td></td><td></td><td></td><td></td><td>X</td><td></td></tr><tr><td>Standards</td><td></td><td></td><td></td><td></td><td>x</td><td></td></tr><tr><td>Plant</td><td></td><td></td><td></td><td></td><td>X</td><td></td></tr><tr><td>Workcentre</td><td></td><td></td><td></td><td></td><td>X</td><td></td></tr><tr><td>Assets</td><td></td><td></td><td></td><td></td><td>X</td><td></td></tr><tr><td>Test Schedule</td><td>X</td><td></td><td></td><td>X</td><td>X</td><td></td></tr><tr><td>Status</td><td>X</td><td></td><td></td><td></td><td>X</td><td></td></tr><tr><td>Lab Result (Evidence)</td><td></td><td></td><td></td><td></td><td>X</td><td></td></tr><tr><td>Device Result</td><td></td><td></td><td></td><td>X</td><td>X</td><td></td></tr><tr><td>Anomalieis</td><td>X</td><td></td><td></td><td></td><td>X</td><td></td></tr><tr><td>Issue</td><td></td><td></td><td></td><td></td><td>x</td><td></td></tr><tr><td>Dashboards</td><td>x</td><td></td><td></td><td></td><td>x</td><td></td></tr><tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Plant Admin</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Entity</td><td>Actions</td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Create (C)</td><td>Read (R)</td><td>Search (S)</td><td>Update (U)</td><td>Delete (D)</td><td>Deactivate</td><td></td></tr><tr><td>Process Flows</td><td>x</td><td></td><td></td><td>x</td><td>x</td><td>x</td></tr><tr><td>Jobs</td><td>x</td><td></td><td></td><td>x</td><td>x</td><td>x</td></tr><tr><td>Standards</td><td>x</td><td></td><td></td><td>x</td><td>x</td><td>x</td></tr><tr><td>Plant</td><td></td><td></td><td></td><td></td><td>X</td><td></td></tr><tr><td>Workcentre</td><td></td><td></td><td></td><td></td><td>X</td><td></td></tr><tr><td>Assets</td><td></td><td></td><td></td><td></td><td>X</td><td></td></tr><tr><td>Test Schedule</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Status</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Lab Result (Evidence)</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Device Result</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Anomalieis</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Issue</td><td>X</td><td>X</td><td>X</td><td>X</td><td>x</td><td></td></tr><tr><td>Dashboards</td><td>X</td><td>X</td><td>X</td><td>X</td><td>x</td><td></td></tr><tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Process Admin</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Entity</td><td>Actions</td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Create (C)</td><td>Read (R)</td><td>Search (S)</td><td>Update (U)</td><td>Delete (D)</td><td>Deactivate</td><td></td></tr><tr><td>Process Flows</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Jobs</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Standards</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Plant</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Workcentre</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Assets</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Test Schedule</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Status</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Lab Result (Evidence)</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Device Result</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Anomalieis</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Issue</td><td>X</td><td>X</td><td>X</td><td>X</td><td>x</td><td></td></tr><tr><td>Dashboards</td><td>X</td><td>X</td><td>X</td><td>X</td><td>x</td><td></td></tr><tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Process Admin</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Entity</td><td>Actions</td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Create (C)</td><td>Read (R)</td><td>Search (S)</td><td>Update (U)</td><td>Delete (D)</td><td>Deactivate</td><td></td></tr><tr><td>Process Flows</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Jobs</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Standards</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Plant</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Workcentre</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Assets</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Test Schedule</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Status</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Lab Result (Evidence)</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Device Result</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Anomalieis</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Issue</td><td>X</td><td>X</td><td>X</td><td>X</td><td>x</td><td></td></tr><tr><td>Dashboards</td><td>X</td><td>X</td><td>X</td><td>X</td><td>x</td><td></td></tr><tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Test Viewer</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Entity</td><td>Actions</td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Create (C)</td><td>Read (R)</td><td>Search (S)</td><td>Update (U)</td><td>Delete (D)</td><td>Deactivate</td><td></td></tr><tr><td>Process Flows</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Jobs</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Standards</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Plant</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Workcentre</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Assets</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Test Schedule</td><td>X</td><td></td><td></td><td>X</td><td>X</td><td></td></tr><tr><td>Status</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Lab Result (Evidence)</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Device Result</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Anomalieis</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Issue</td><td>X</td><td>X</td><td>X</td><td>X</td><td>x</td><td></td></tr><tr><td>Dashboards</td><td>X</td><td>X</td><td>X</td><td>X</td><td>x</td><td></td></tr><tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Plant Operator</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Entity</td><td>Actions</td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Create (C)</td><td>Read (R)</td><td>Search (S)</td><td>Update (U)</td><td>Delete (D)</td><td>Deactivate</td><td></td></tr><tr><td>Process Flows</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Jobs</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Standards</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Plant</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Workcentre</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Assets</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Test Schedule</td><td></td><td></td><td></td><td>X</td><td>X</td><td></td></tr><tr><td>Status</td><td></td><td></td><td></td><td></td><td>X</td><td></td></tr><tr><td>Lab Result (Evidence)</td><td></td><td></td><td></td><td></td><td>X</td><td></td></tr><tr><td>Device Result</td><td>X</td><td></td><td></td><td>X</td><td>X</td><td></td></tr><tr><td>Anomalieis</td><td>X</td><td></td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Issue</td><td>X</td><td>X</td><td>X</td><td>X</td><td>x</td><td></td></tr><tr><td>Dashboards</td><td>X</td><td>X</td><td>X</td><td>X</td><td>x</td><td></td></tr><tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Test Uploader</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Entity</td><td>Actions</td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Create (C)</td><td>Read (R)</td><td>Search (S)</td><td>Update (U)</td><td>Delete (D)</td><td>Deactivate</td><td></td></tr><tr><td>Process Flows</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Jobs</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Standards</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Plant</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Workcentre</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Assets</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Test Schedule</td><td></td><td></td><td></td><td>X</td><td>X</td><td></td></tr><tr><td>Status</td><td></td><td></td><td></td><td></td><td>X</td><td></td></tr><tr><td>Lab Result (Evidence)</td><td></td><td></td><td></td><td></td><td>X</td><td></td></tr><tr><td>Device Result</td><td>X</td><td></td><td></td><td>X</td><td>X</td><td></td></tr><tr><td>Anomalieis</td><td>X</td><td></td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Issue</td><td>X</td><td>X</td><td>X</td><td>X</td><td>x</td><td></td></tr><tr><td>Dashboards</td><td>X</td><td>X</td><td>X</td><td>X</td><td>x</td><td></td></tr><tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Plant Operator</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Entity</td><td>Actions</td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Create (C)</td><td>Read (R)</td><td>Search (S)</td><td>Update (U)</td><td>Delete (D)</td><td>Deactivate</td><td></td></tr><tr><td>Process Flows</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Jobs</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Standards</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Plant</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Workcentre</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Assets</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Test Schedule</td><td></td><td></td><td></td><td>X</td><td>X</td><td></td></tr><tr><td>Status</td><td></td><td></td><td></td><td></td><td>X</td><td></td></tr><tr><td>Lab Result (Evidence)</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Device Result</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Anomalieis</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Issue</td><td>X</td><td>X</td><td>X</td><td>X</td><td>x</td><td></td></tr><tr><td>Dashboards</td><td>X</td><td>X</td><td>X</td><td>X</td><td>x</td><td></td></tr><tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Issue Creator</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Entity</td><td>Actions</td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Create (C)</td><td>Read (R)</td><td>Search (S)</td><td>Update (U)</td><td>Delete (D)</td><td>Deactivate</td><td></td></tr><tr><td>Process Flows</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Jobs</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Standards</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Plant</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Workcentre</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Assets</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Test Schedule</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Status</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Lab Result (Evidence)</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Device Result</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Anomalieis</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Issue</td><td></td><td></td><td></td><td>X</td><td>x</td><td></td></tr><tr><td>Dashboards</td><td>X</td><td>X</td><td>X</td><td>X</td><td>x</td><td></td></tr><tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Issue Editor (different for different types of issues)</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Entity</td><td>Actions</td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Create (C)</td><td>Read (R)</td><td>Search (S)</td><td>Update (U)</td><td>Delete (D)</td><td>Deactivate</td><td></td></tr><tr><td>Process Flows</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Jobs</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Standards</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Plant</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Workcentre</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Assets</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Test Schedule</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Status</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Lab Result (Evidence)</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Device Result</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Anomalieis</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Issue</td><td>X</td><td></td><td></td><td></td><td>x</td><td></td></tr><tr><td>Dashboards</td><td>X</td><td>X</td><td>X</td><td>X</td><td>x</td><td></td></tr><tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Dashboards</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Entity</td><td>Actions</td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Create (C)</td><td>Read (R)</td><td>Search (S)</td><td>Update (U)</td><td>Delete (D)</td><td>Deactivate</td><td></td></tr><tr><td>Process Flows</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Jobs</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Standards</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Plant</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Workcentre</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Assets</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td></tr><tr><td>Test Schedule</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Status</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Lab Result (Evidence)</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Device Result</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Anomalies</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Issue</td><td>X</td><td>X</td><td>X</td><td>X</td><td>X</td><td></td></tr><tr><td>Dashboards</td><td>X</td><td></td><td></td><td>X</td><td>x</td><td></td></tr></tbody></table>

## User Interface Design (Exemplar)

### Landing Page: Plant Operator

The user will land on the home page post login. The following actions can be performed by the user:

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 10.28.10 AM.png" alt=""><figcaption></figcaption></figure>

1. The plant name is visible on the top right hand corner of the screen.
2. A help button is available for the user to get a guided view of the page. This is available on every page.
3. Cards are viewable for the following modules:

&#x20;      a. Vehicle log module (record incoming vehicles)

&#x20;      b. Treatment quality module

&#x20;      c. View dashboard

Clicking on each of these cards will take the user to the Homepage for the specific module.

4. List of pending tasks: This will show the list of tests pending within the next \[X] days.\
   The next action item in the task workflow will be displayed beside a pending task for a user to take prompt action. A button for “View All Pending Tasks” will be displayed which will redirect the user to “All Pending Tasks”.

### Treatment Quality Module (TQM) Home Page

On clicking on the treatment quality card, the user is redirected to the TQM home page. The following actions can be performed by the user:

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 10.33.02 AM.png" alt=""><figcaption></figcaption></figure>

1. View and take action on upcoming tests using the inbox. The inbox will show a count of upcoming tests beside it.
2. View past test results: Past results from both lab and IoT devices will be displayed here.
3. View IoT readings: The user can access the record of IoT readings here.
4. Sensor Monitoring: The user can access a list of IoT devices along with their status here.
5. View dashboard: The user will be directed to the treatment quality dashboard.
6. View performance: This widget will show the performance of the plant in regards to treatment quality and will display the following KPIs:

&#x20;      a. Test compliance: Compliance percentage of plant with regards to the treatment quality and its comparison to state level compliance percentage.

&#x20;     b. Last treatment quality result - Pass/fail and date of the test.

&#x20;     c. Count of alerts raised in the past 30 days.

&#x20;     d. Distribution of alerts based on the alert category.

7. Go back to the Landing page using the back button.
8. A help button is available for the user to get a guided view of the page. This is available on every page.

**View List of Upcoming Tests**

On clicking on inbox, the user is redirected to the list of upcoming tests. This will show only a list of lab tests. The user can perform the following tasks:

1. Total count of upcoming tests are displayed beside the inbox in brackets.
2. View list of upcoming tests. The following will be the fields displayed:

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 10.40.21 AM.png" alt=""><figcaption></figcaption></figure>

1. Total count of upcoming tests are displayed beside the inbox in brackets.
2. View list of upcoming tests. The following will be the fields displayed:

&#x20;      a. Test ID.

&#x20;      b. Treatment process (in case there is only 1 treatment process for the plant, this field will not be displayed).

&#x20;      c. Stage: This will display the process stage where the sample is to be collected from.

&#x20;      d. Output type: Biosolids/effluents.

&#x20;      e. Pending date: This is the test date as per schedule.

&#x20;      f. Status: status of the test.

&#x20;      g. SLA: Show difference between test due date and today.

3. An action item available based on the next status in the workflow will be displayed:

&#x20;     a. For test results in the scheduled stage, update status will be displayed.

&#x20;     b. For tests in the pending results stage, update results will be displayed.

4. Filter tests: On clicking on filter, a pop-up will be displayed:

&#x20;      a. The following filters are available:

1. Treatment process: (In case there is only 1 treatment process for the plant, this field will not be displayed). This will be a dropdown showing the values for treatment processes configured for the plant. The selected treatment process is displayed here on selection. If not, the field is left blank.
2. Output type: This will be a dropdown showing values for output types configured for the plant. The selected output type is displayed here on selection. If not, the field is left blank.
3. Status: This will be a dropdown showing values for the status in the treatment quality workflow. The selected status is displayed here on selection. If not, the field is left blank.
4. Date range: Selection of date range (calendar view):  Selected date range is displayed here on selection. If not, the field is left blank.

&#x20;     b. On selecting values for the filters above, a user can click on filter to filter the inbox.&#x20;

&#x20;     c. To clear filters, a user can click on clear all.&#x20;

&#x20;     d. To close the pop-up, a user can click on the cross on the top right hand corner of the screen.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 10.47.17 AM (1).png" alt=""><figcaption></figcaption></figure>

5. Sort: On clicking on sort, a pop-up will be displayed:

&#x20;      a. Tests can be sorted by the pending date:

&#x20;          Date (Latest first)

&#x20;          Date (Latest Last)

&#x20;     b. On selecting values for sort above, the user can click on sort to sort the inbox.

&#x20;     c. To clear sort, a user can click on clear all.

&#x20;     d. To close the pop-up, a user can click on the cross on the top right hand corner of the screen.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 10.51.22 AM.png" alt=""><figcaption></figcaption></figure>

6. Go back to the landing page using the back button.
7. A help button is available for the user to get a guided view of the page. This is available on every page.

**View Test Details**

Test  Details can be viewed by the user in 2 ways:

* Via the pending tasks.
* Via inbox.

View Test Details Via Pending Tasks

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 11.00.32 AM.png" alt=""><figcaption></figcaption></figure>

* The list of pending tasks can be accessed via the landing page for TQM. This will show the list of tests pending within the next \[X] days.
* &#x20;The next action item in the task workflow will be displayed as a button beside a pending task for a user to take prompt action. On clicking on the button, the user will be redirected to the test details page.

View Test Details Via Inbox

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 11.04.19 AM (1).png" alt=""><figcaption></figcaption></figure>

A list of tests can be accessed on the inbox. An action item is available based on the next status in the workflow will be displayed:

1. For test results in the scheduled stage, the update status will be displayed.
2. For tests in the pending results stage, the update results will be displayed.

On clicking on the action item, the user will be redirected to the test details page.&#x20;

The test details page will consist of 2 cards:

1. The first card will display the following fields:

* Test ID
* Treatment Process
* Stage
* Output Type
* Pending Date
* Status
* Parameters to be tested along with their unit of measurement
* SLA (This will be displayed in Red/green basis SLA. If today>Pending date, this is red, If today\<pending date, then green).

2. The second card will be based on the test status:

* For tests in status ‘Scheduled’, the user will be asked to select a lab.&#x20;
* For tests in status “Pending Results”, the user will be asked to add test results

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 11.11.33 AM.png" alt=""><figcaption></figcaption></figure>

The user can go back using the back button - The redirection will be based on the page the user has accessed the test details page from. A help button is available for the user to get a guided view of the page. This is available on every page.

**Update Tests**

Tests can be updated by the user from the test details page. The test details page will display the next action item for the user based on the workflow test. For tests with the wWorkflow status ‘Scheduled’, the user will be prompted to confirm if sample has been submitted to the lab for testing.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 11.13.54 AM.png" alt=""><figcaption></figcaption></figure>

The user can perform the following actions:

1. Select a lab from a dropdown list configured in the MDMS.&#x20;
2. Update status of the test. The button will be deactivated if Lab is not selected, and will only be activated once selection is made. Once the user clicks on update status, he/she is redirected back to the page from which test details were accessed and a snack bar confirms the status update and the action Item button shows updated next step.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 11.15.53 AM.png" alt=""><figcaption></figcaption></figure>

In case an update of status fails, the user will remain on the same page and a failure message will be displayed to the user.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 11.17.00 AM.png" alt=""><figcaption></figcaption></figure>

For tests with the workflow status “Pending Status”, the user will be prompted to fill test results.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 11.18.49 AM.png" alt=""><figcaption></figcaption></figure>

The user can perform the following actions:

1. Update parameter readings (mandatory fields) The following validations will be applied:

&#x20;      a. Only numerical values will be viewable here.  In case of non numerical values, the following error message is displayed “Only numeric values allowed. Please input in the required format”.

2. Attach documents (non-mandatory): The following validations will be applied:

&#x20;     a. Only files in the following formats will be supported: .png, .jpg. .pdf. In case a file of unsupported format is selected, the following error will be displayed “The file type is not supported. Please upload in the following formats: .pdf, .png, .jpg”.

&#x20;    b. File size of maximum X mb allowed. In case file size is larger than permitted value, the following error will be displayed “The file size is too large. Please upload a file below x mbs”.

3. Submit test results by clicking on the ‘Submit’ button. The button will be deactivated if all is not selected, and will only be activated once selection is made. On clicking the submit button, a pop-up will be displayed to the user to confirm submission.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 11.22.07 AM (1).png" alt=""><figcaption></figcaption></figure>

The following actions will be made available to the user:

1. Confirm submission by clicking on the ‘Submit’ button.
2. Go back to the test details page by clicking on the “Go back” button.

On clicking the submit button and failure to submit test results, the user will remain on the same page and a failure message will be displayed.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 11.29.22 AM.png" alt=""><figcaption></figcaption></figure>

On clicking the submit button and successful submission of the test results, the user will be redirected to the summary page and a snack bar will confirm the submission.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 11.30.38 AM.png" alt=""><figcaption></figcaption></figure>

At this stage, the user will be displayed the summary of test results and whether it has passed/failed based on a comparison between the values entered by the user and the benchmarks. In case all values are as per the benchmarks, the test results will be displayed as ‘Pass’. All values will be shown in green and the user receives feedback that all results are as per benchmarks. The user can go back to the home page by clicking on the ‘Back’ button.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 11.32.07 AM.png" alt=""><figcaption></figcaption></figure>

In case one or more values are not as per the benchmarks, the test results will be displayed as ‘Fail’. All values as per benchmarks will be shown in green. Values not as per the benchmarks are shown in red. The user is provided with information that the test results are not as per benchmark. The user can go back to the Home page by clicking on the ‘Back’ button.

**View Past Test Results**

Past test results (both IoT and Lab) can be viewed via the TQM landing page and by clicking on past tests.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 11.35.31 AM.png" alt=""><figcaption></figcaption></figure>

On clicking on past tests, the user is redirected to the list of past tests.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 11.36.16 AM.png" alt=""><figcaption></figcaption></figure>

The user can perform the following tasks:

1. View the list of past tests. The following will be the fields displayed:

&#x20;      a. Test ID.

&#x20;      b. Treatment process (in case there is only 1 treatment process for the plant, this field will not be displayed).

&#x20;      c. Stage: This will display the process stage where the sample is to be collected from.

&#x20;      d. Output type: Biosolids/effluents

&#x20;      e. Pending date: This is the test date as per schedule.

&#x20;      f. Test result: Pass/fail.

&#x20;  2\. View test details: The user can view test details by clicking on “View Results” button on each card.

3. Filter tests: On clicking on Filter, a pop-up will be displayed. The following filters are available:

&#x20;      i. Treatment process: (in case there is only 1 treatment process for the plant, this field will not be displayed). This will be a dropdown showing values for Treatment Processes configured for the plant. The selected treatment process is displayed here on selection. If not, the field is left blank.

&#x20;     ii. Output type: This will be a dropdown showing values for the output types configured for the plant. The selected output type is displayed here on selection. If not, the field is left blank.

&#x20;     iii. Test type: This will be a dropdown showing values for the test type (IoT/Lab). The selected test type is displayed here on selection. If not, the field is left blank.

&#x20;     iv. Date range: The selection of date range (calendar view) - The selected date range is displayed here on selection. If not, the field is left blank.

On selecting values for filters above, the user can click on filter to filter the inbox. To clear filters, the user can click on clear all. To close the pop-up, a user can click on the cross on the top right hand corner of the screen. On selection of the filter, the selected filter is displayed on the screen. On clicking the cross button near the displayed filter, the filter is removed.\


<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 11.46.54 AM.png" alt=""><figcaption></figcaption></figure>

3. Sort: On clicking on sort, a pop-up will be displayed:

&#x20;      a. Tests can be sorted by the pending date:&#x20;

1. Date (Latest first)
2. Date (Latest last)

&#x20;       b. On selecting values for sort above, the user can click on sort to sort the inbox.

&#x20;       c. To clear sort, the user can click on clear all.

&#x20;       d. To close the pop-up, the user can click on the cross on the top right hand corner of the screen.

4. In case filters/sort/search is applied and the user navigates to the test details page, on going back, the values of the filters/sort/search should remain the same.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 11.50.20 AM.png" alt=""><figcaption></figcaption></figure>

5. The user can download the list of tests, filtered by selection in Excel and PDF format.
6. Go back to the Landing page using the back button.
7. A help button is available for the user to get a guided view of the page. This is available on every page.

On clicking the “View Results” button, the user will be redirected to the test summary page.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 11.52.20 AM.png" alt=""><figcaption></figcaption></figure>

The page will have 2 cards:&#x20;

The first card will display the following fields:

* Test ID.
* Treatment Process.
* Stage.
* Output Type.
* Test Type.
* Lab Name/Device ID: This will show Lab Name/Device ID based on the Test type.
* Test submitted on.
* Test Results: Pass/Fail.

The second card will display the following fields:

* Parameters, their unit of measurement and the values of the parameters recorded. The values will be read/green basis whether they are as per benchmarks or not.

The user can go back to the list of tests by clicking on the ‘Back’ button, both on the top and bottom of the page.

**View IoT Readings**

IoT readings can be viewed via the TQM landing page and clicking on view IoT readings.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 11.56.08 AM.png" alt=""><figcaption></figcaption></figure>

On clicking on View IoT readings, the user is redirected to the view tests page filter on test type: IoT.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 11.57.42 AM.png" alt=""><figcaption></figcaption></figure>

The functionality of the page remains the same as the “View Past Tests” page.

**Sensor Monitoring**

Sensor monitoring can be accessed by clicking on the sensor monitoring link on the TQM landing page.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 12.00.50 PM.png" alt=""><figcaption></figcaption></figure>

On clicking on sensor monitoring, the list of IoT devices are displayed.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 12.01.40 PM.png" alt=""><figcaption></figcaption></figure>

The following details are displayed on the page:

* Total number of IoT devices is displayed beside the page heading in brackets.
* A card is available for each device. The following details will be displayed:

&#x20;     \- Device ID.

&#x20;     \- Treatment Process.

&#x20;     \- Stage.

&#x20;     \- Output Type.

&#x20;     \- Last Calibrated Date.

&#x20;     \- Device Status.

&#x20;     \- Verification Status.

&#x20;     \- Last Verification Date.

&#x20;     \- Parameters that the device monitors.

The user can perform the following actions:

1. Filter devices: On clicking on filter, a pop-up will be displayed. &#x20;

&#x20;      a. The following filters are available:

&#x20;      i. Treatment process: (in case there is only 1 treatment process for the plant, this field will not be displayed). This will be a dropdown showing values for the treatment processes configured for the plant. The selected treatment process is displayed here on selection. If not, the field is left blank.

&#x20;     ii. Output type: This will be a dropdown showing values for the output types configured for the plant. The selected output type is displayed here on selection. If not, the field is left blank.

&#x20;     iii. Device status: This will be a radio button showing active/inactive

&#x20;     iv. Parameters: This will be a multi-select displaying all parameters configured on the backend.

&#x20;      b. On selecting values for filters above, the user can click on filter to filter the inbox.

&#x20;      c. To clear filters, the user can click on clear all.

&#x20;      d. To close the pop up, the user can click on the cross on the top right hand corner of the screen.

&#x20;      e. On selection of the filter, the selected filter is displayed on the screen. On clicking the cross button near the displayed filter, the filter is removed.

2. Search: On clicking on search, a pop-up will be displayed.

&#x20;     a. The user can search a device by device ID. Part search to be enabled.

**View Dashboard**

Dashboards can be accessed by clicking on the “View Dashboards” link on the TQM landing page.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 12.24.38 PM.png" alt=""><figcaption></figcaption></figure>

Navigation:

On landing on the dashboard, the user can navigate across the treatment process types to view the dashboard specific to the treatment process type.

Filter:

Date range: Users should be able to filter based on the date range basis which dashboard is to be filtered.

Other functionalities:

Share:&#x20;

* Users should be able to share a filtered dashboard over WhatsApp in an image format.
* Users should be able to share filtered charts/tables over WhatsApp in an image format.

Download:&#x20;

* Users should be able to download the filtered dashboard in PDF and image formats.
* Users should be able to download filtered charts/tables in PDF and image formats.

Metrics:

* Total incoming sludge: The sum of the total sludge that is disposed of at the plant for the selected time period.
* Number of trips: A count of the total incoming vehicles at the treatment plant for the selected time period.
* Overall quality: The number of tests where all parameters are as per the benchmarks as compared to the total number of test results recorded.
* Compliance percentage: The percentage of tests where results have been recorded.
* Total alerts: A count of the total alerts raised of the following types: Test results not as per the benchmark, no reading from the IoT device, and lab results and IoT results not matching.

Treatment Quality Overview:&#x20;

KPIs:

* Total tests - A count of the total tests for the filtered date range.
* A count of tests that have passed treatment quality.
* A count of tests that have failed the treatment quality.

Table:

1. Heading - Name of the plant.
2. Table displaying the following fields:

&#x20;       a. Stage, output type, value of parameters, and compliance percentage.

&#x20;       b. Button to view the trends for a particular stage.

3. Toggle to toggle between IoT readings and lab results.

Trends of parameter readings:

This chart will be available once the user clicks on the view trend button in the table button.

The table shows the trend for one parameter over time, and provides a view of the benchmark for comparison. A toggle is available to navigate between the parameters. Detailed metric details for the Treatment Quality Monitoring dashboard are viewable below:

| [S.No](http://s.no/) | Section Heading                     | Chart Heading            | Subheading | Definitions ((This will appear on the dashboard whenever a user hovers on the metric wherever applicable))                                                                              | Chart Type       | X-Axis     | Y-Axis          | Value                                                                                                                         | Columns                                            | How to calculate                                                                                                                                                                                                                                                                                                                                               | Boundary         | Dtill down/Toggle | Comparsion KPIs, if any | Show comparison in | Specific to State/ULB/ TRP/all | Tooltip on Hover on Data Point                          | Input Fields |
| -------------------- | ----------------------------------- | ------------------------ | ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | ---------- | --------------- | ----------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | ----------------- | ----------------------- | ------------------ | ------------------------------ | ------------------------------------------------------- | ------------ |
| 1                    | Input                               | Total Incoming Sludge    | NA         | Total Incoming sludge from registered and unregistered vehicles                                                                                                                         | KPI              | NA         | NA              | Total Incoming Sludge                                                                                                         | NA                                                 | Total incoming sludge = (Volume of Waste Disposed for Registered Vehicles) + (Volume of Waste Disposed for Unregistered Vehicles)                                                                                                                                                                                                                              | State, Plant ULB | NA                | NA                      | NA                 | NA                             |                                                         |              |
| 2                    | Input                               | # incoming trips         | NA         | Number of trips disposed at the Treatment plant                                                                                                                                         | KPI              | NA         | NA              | Count of Trips to the Treatment plant from registered and unregistered vehicles                                               | NA                                                 | Number of trips disposed = Count(DISTINCT Trip ID)                                                                                                                                                                                                                                                                                                             | State, Plant ULB | NA                | NA                      | NA                 | NA                             |                                                         |              |
| 3                    | Treatment Quality                   | Overall Quality          | NA         | % of tests where all parameters are as per benchmarks                                                                                                                                   | KPI              | NA         | NA              | % of test results meeting benchmarks                                                                                          | NA                                                 | Overall Quality = (Number of tests where all parameters meet benchmarks / Total number of tests) \* 100                                                                                                                                                                                                                                                        | State, Plant ULB | NA                | NA                      | NA                 | NA                             |                                                         |              |
| 4                    | Treatment Quality                   | Compliance               | NA         | % of tests where results have been recorded                                                                                                                                             | KPI              | NA         | NA              | % of tests with Status as submitted out of total tests                                                                        |                                                    | Compliance % = (Count of Test ID in status 'Submitted' / Count (Distinct Trip ID) \* 100                                                                                                                                                                                                                                                                       | State, Plant ULB | NA                | NA                      | NA                 | NA                             |                                                         |              |
| 5                    | Alerts                              | Total Alerts             | NA         | Total Alerts raised by the system in the following categories: 1) Test Results not as per benchmark 2) No reading from IoT device 3) Lab results and IoT results not matching           | KPI              | NA         | NA              | Total Alerts                                                                                                                  |                                                    | Count(DISTINCT AlertID)                                                                                                                                                                                                                                                                                                                                        | State, Plant ULB | NA                | NA                      | NA                 | NA                             |                                                         |              |
| 6                    | Treatment Quality Plants            | Total Plants             | NA         | NA                                                                                                                                                                                      | NA               | NA         | NA              | Count of Plants                                                                                                               |                                                    | Count (Distinct PlantID)                                                                                                                                                                                                                                                                                                                                       | State, Plant ULB | NA                | NA                      | NA                 | NA                             |                                                         |              |
| 7                    | Treatment Quality Plants            | Treatment Quality Passed | NA         | Treatment quality is considered passed if all parameters of both Biosolids and Effluents are as per benchmarks for the output of the Treatment Process in the last test recorded.       | NA               | NA         | NA              | Count of Plants with Treatment Quality Passed                                                                                 |                                                    | <p>Treatment Quality for Output type =IF(COUNTIF(All Parameters Meet Benchmarks, FALSE) = 0, "Treatment Quality for Output type passed ", "Treatment Quality for Output type failed")<br><br>Treatment Quality for Plant passed = =IF(COUNTIF(Treatment Quality for Output type, FALSE) = 0, " Treatment Quality Passed ", "Treatment Quality Failed")<br></p> | State, Plant ULB | NA                | NA                      | NA                 | NA                             |                                                         |              |
| 8                    | Treatment Quality Plants            | Treatment Quality Failed | NA         | Treatment quality is considered failed when 1 or more parameters of Biosolids or Effluents are not as per benchmarks for the output of the Treatment Process in the last test recorded. | NA               | NA         | NA              | Count of Plants with Treatment Quality Failed                                                                                 |                                                    | Count (Distinct PlantID) - Treatment Quality Passed                                                                                                                                                                                                                                                                                                            | State, Plant ULB | NA                | NA                      | NA                 | NA                             |                                                         |              |
| 9                    | Treatment Quality Plants            | NA                       | NA         | NA                                                                                                                                                                                      | Map              | NA         | NA              | <p>Point = Geolocation of Plant<br>Plant Icon Colour - Green if Treatment Quality Passed, Red if Treatment Quality Failed</p> |                                                    | Same as [S.No](http://s.no/) 7 and [S.No](http://s.no/) 8                                                                                                                                                                                                                                                                                                      | State, Plant ULB | NA                | NA                      | NA                 | NA                             | Name of Plant                                           |              |
| 10                   | Treatment Quality Plants            | NA                       | NA         | NA                                                                                                                                                                                      | Table            | NA         | NA              | NA                                                                                                                            | Plant Name, Test Result, Compliance %              | Test Result Same as S.No 7 and S.No 8                                                                                                                                                                                                                                                                                                                          | State, Plant ULB | NA                | NA                      | NA                 | NA                             |                                                         |              |
| 11                   | Treatment Quality Plants            | NA                       | NA         | NA                                                                                                                                                                                      | Table            | NA         | NA              | NA                                                                                                                            | Stage, Output Type, Parameters 1...n, Compliance % | Mentioned above                                                                                                                                                                                                                                                                                                                                                | State, Plant ULB | NA                | Compliance %            | % from last month  | NA                             |                                                         |              |
| 12                   | Trend in \[Parameter Name] Readings | NA                       | NA         | NA                                                                                                                                                                                      | Multi-Line Chart | Test Dates | Parameter Value | <p>- Value of Device Reading<br>- Value of Lab results</p>                                                                    | NA                                                 | NA                                                                                                                                                                                                                                                                                                                                                             | Plant            | NA                | NA                      | NA                 | NA                             | <p>Date<br>Lab result - X<br>Device Reading - Y<br></p> |              |

### Landing Page: ULB Employee

A card for Treatment Quality Monitoring will be made available on the landing page of the employee.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-13 at 9.40.04 AM.png" alt=""><figcaption></figcaption></figure>

1. The treatment quality contain the following:&#x20;

&#x20;      a. An overview of the total pending tests and how many are nearing SLA.

&#x20;      b. View upcoming tests using the inbox. The inbox will show a count of upcoming tests beside in brackets.

&#x20;      c. View past test results: Past results from both lab and IoT devices will be displayed here.

&#x20;      d. View IoT readings: The user can access the record of IoT readings here.

&#x20;      e. Sensor monitoring: The user can access a list of IoT devices along with their status here.

&#x20;     f. View dashboard: The user will be directed to the treatment quality dashboard.

Clicking on each of these links will take the user to the specific page.

2. Notifications: This will show the list of alerts regarding TQM. Currently, this will display the tests that have crossed SLA for greater than 7 days. The user can view the details of the test by clicking on the “View Details” button. The user can dismiss the notification by clicking on the cross button.
3. Rest of the functionality will remain the same as the current ULB employee landing page.

**View List of Upcoming Tests**

On clicking on Inbox, the user is redirected to the list of upcoming tests. This will show only a list of lab tests. The user can perform the following tasks:

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-13 at 9.46.59 AM.png" alt=""><figcaption></figcaption></figure>

1. The total count of upcoming tests are displayed beside the inbox in brackets.
2. View a list of upcoming tests. The list of upcoming tests will be sorted by the pending date, where the test with the highest SLA is displayed first. The following fields will be displayed:

&#x20;      a. Test ID

&#x20;      b. Plant Name

&#x20;      c. Treatment Process&#x20;

&#x20;      d. Pending Date: This is the test date as per schedule

&#x20;     e. Status: Status of the test

&#x20;     f. SLA: Show difference between test due date and today. This will be displayed in red if test due date\<today and in green if today>test due date.

The user can view test details by clicking on the test ID.

3. Filter tests: Filters are displayed on the left hand panel of the screen. The following filters are available:

&#x20;      i. Treatment process: This will be multi-select showing values for the treatment processes configured for the ULB. The selected treatment process will be displayed as a tick on the multi-select box. If not, it is left blank.

&#x20;      ii. Stages: This will be a dropdown showing values for stages configured for the plant. The selected stage is displayed here on selection. If not, the field is left blank.

&#x20;      iii. Status: This will be a multi-select showing values for the status in the treatment quality workflow.

On selecting values for filters above, the user can click on filter to filter the inbox. To clear filters, the user can click on the refresh icon on the top right of the filter panel.

4. Sort: Tests can be sorted by the pending date by clicking on the date column.
5.  Search:

    a. Tests can be searched using the following:

&#x20;          i. Test ID.

&#x20;          ii.  Plant Name.&#x20;

&#x20;      b. Part search to be enabled for both.&#x20;

&#x20;      c. Users can fill either test ID or plant or both and click on the search button.&#x20;

&#x20;      d. Users can clear search by clicking on the clear search link.

6. In case filters/sort/search is applied and the user navigates to the test details page, on going back, the values of the filters/sort/search should remain the same.
7. Redirecting to other links in the TQM module: Users can redirect to other pages in the TQM module via the links provided on the top left of the page. The following links will be displayed:

&#x20;      a. View Past Results&#x20;

&#x20;      b. View IoT Results&#x20;

&#x20;      c. Sensor Monitoring&#x20;

&#x20;      d. View Dashboard

**View Test Details**

A test details page can be accessed by clicking on the test ID in the inbox. The test details page will consist of the following fields:

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-13 at 11.02.08 AM.png" alt=""><figcaption></figcaption></figure>

* The following information will be displayed. In case the information on any field is not available such as the lab name/value against parameters based on the status of the test, the value against the fields will be displayed as “To be Updated”

&#x20;     \- Test ID

&#x20;     \- Plant Name

&#x20;     \- Treatment Process

&#x20;     \- Stage

&#x20;     \- Output Type

&#x20;     \- Test Type

&#x20;     \- Test Scheduled on

&#x20;     \- Status

&#x20;     \- Lab Name

&#x20;     \- Sample submitted on

&#x20;     \- Test results submitted on

&#x20;     \- SLA (This will be displayed in red/green based on the SLA. If today>pending date, this is red, If today\<pending date, then green for open tests. For closed tests, SLA will be displayed).

&#x20;    \- Table containing the following details:

&#x20;       i. S.No

&#x20;       ii. Parameter

&#x20;       iii. UoM

&#x20;       iv. Benchmark

&#x20;       v. Value Recorded - The value will be displayed in red/green based on comparison to the benchmark

&#x20;       vi. Overall Test results - Pass/Fail

&#x20;      \- Attached documents, if any. The user should be able to view the document by clicking on the document icon. No icon will be present if documents are not attached.

&#x20;      \- Test Timeline

* The user can go back using the breadcrumbs of the page.
* The user can download the test report by clicking on the 'Download' button.

&#x20;**View Past Test Results**

Past test results (both IoT and Lab) can be viewed via the TQM landing page and clicking on past tests.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-13 at 11.09.10 AM.png" alt=""><figcaption></figcaption></figure>

On clicking on past test results, the user is redirected to the list of past tests.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-13 at 11.10.18 AM.png" alt=""><figcaption></figcaption></figure>

The user can perform the following tasks:

1. View the list of past tests. The results will be sorted on the test date. The following will be the fields displayed:

&#x20;      a. Test ID

&#x20;      b. Plant

&#x20;      c. Treatment Process (in case the there is only 1 treatment process for the plant, this field will not be displayed).

&#x20;      d. Test Type

&#x20;      e. Test Date: This is the date the test results are updated

&#x20;      f. Test Result: Pass/Fail

2. View test details: The user can view test details by clicking on the “Test ID” link in each row.
3. Search tests: The user can search based on the following:

&#x20;      i Test ID: Input text field, part search should be enabled.

&#x20;      ii. Plant: Dropdown of list of plants in the ULB.

&#x20;      iii. Treatment process: Dropdown of list oftTreatment Process in the ULB.

&#x20;      iv. Test type: This will be a dropdown showing values for the test type (IoT/Lab). The selected test type is displayed here on selection. If not, the field is left blank.

&#x20;      v. Date range: Selection of date range (calendar view):  The selected date range is displayed here on selection. If not, the field is left blank.

On selecting values for search above, the user can click on search to filter the inbox. To clear search and view all past tests, the user can click on “Clear Search”.

4. Sort: Tests can be sorted by the pending date by clicking on the date column.
5. In case filters/sort/search is applied and the user navigates to the test details page, on going back, the values of the filters/sort/search should remain the same.
6. Download test results in Excel and PDF formats using the download button.
7. The user can go back using the breadcrumbs on the top of the page. In case the user has navigated to the test details page from the past test results list, on clicking back, the user should be redirected to the test details page.

On clicking on any test ID button, the user will be redirected to the test details page (same as redirection from the inbox).

&#x20;**View IoT Readings**

IoT readings can be viewed via the TQM landing page and clicking on “View IoT Reading”.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-13 at 11.53.04 AM.png" alt=""><figcaption></figcaption></figure>

On clicking on IoT readings, the user is redirected to the list of past tests, with the search on test type selected as IoT and the results filtered for IoT readings only. All other functionality will remain the same.

**Sensor Monitoring**

The list of devices can be viewed via the TQM landing page and by clicking on ‘Sensor Monitoring’’.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-13 at 11.55.23 AM.png" alt=""><figcaption></figcaption></figure>

On clicking on sensor monitoring, the user is redirected to the list of devices.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-13 at 11.56.15 AM.png" alt=""><figcaption></figcaption></figure>

The user can perform the following:

* View total devices: The total number of IoT devices is displayed beside the page heading in brackets.
* A row  is available for each device. The following details will be displayed:

&#x20;     \- Device ID

&#x20;    \- Plant

&#x20;    \- Treatment Process

&#x20;    \- Stage

&#x20;    \- Output Type

&#x20;    \- Device Status

&#x20;    \- Parameters: One or multiple parameters that the device is monitoring.

The user can perform the following actions:

&#x20;a. Search Devices: On clicking on the filter, a pop up will be displayed. The following filters are available:

1. Device ID: Part search should be available here.
2. Plant: Dropdown based on plants configured in the MDMS.
3. Treatment process: Dropdown-based on the treatment process type.
4. Stage: Dropdown-based stage of selected treatment process.
5. Output type: This will be a drop down showing values for Output types configured for the plant.&#x20;
6. Device status: Dropdown contains active/Inactive as options.

b. On selecting values for filters above, the user can click on Search to filter the inbox.

c. To clear search, the user can click on clear all.

**Record Test Result**

Since actors such as PCB might conduct adhoc tests, a provision will be provided to the user to record test results without a schedule. A user can record test results  by clicking on the “Add Test Result” link on the card.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-13 at 12.01.18 PM.png" alt=""><figcaption></figcaption></figure>

Clicking on the “Add Test Result” button will redirect the user to the “Add Test Result” page.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-13 at 12.02.22 PM.png" alt=""><figcaption></figcaption></figure>

The following fields need to be entered by the user:

* Plant Name: This is a dropdown based on the list of plants available in the system. For a state level user, this should display all plants in the state. For a ULB, it should also display the names tagged to the ULB.
* Treatment Process: This is a dropdown based on the list of treatment processes in the plant selected.
* Treatment Stage: This is a dropdown based on the list of stages in the treatment process selected.
* Output Type: This is a dropdown based on the output types available in the stage
* Values against parameters. Atlease 1 parameter needs to be filled for the submit button to be enabled. If no parameter is filled and the user clicks on the submit button, an error message is displayed as a snack bar.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-13 at 12.03.56 PM.png" alt=""><figcaption></figcaption></figure>

* Attachments, if any.

Once the user clicks on the Submit button, the test results page is displayed.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-13 at 12.04.54 PM.png" alt=""><figcaption></figcaption></figure>

This is the same as the “View Test Results” page with the following changes:

* TesttType will be displayed as Lab.
* Status, lab name and SLA field are not displayed.
* Workflow will not be displayed.

The user can go back to the “Add Test Results” page via the breadcrumbs.

### View Dashboard

The TQM Dashboard will be made available to both the ULB employee and the state employee, and can be accessed by clicking on the dashboard link on the landing page.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-13 at 12.07.10 PM.png" alt=""><figcaption></figcaption></figure>

On clicking on the dashboard, the user is directed to the dashboard view.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-13 at 12.08.10 PM.png" alt=""><figcaption></figcaption></figure>

The access to data in the dashboard will be based on the following roles:

1. ULB admin will be able to view the dashboard for all plants in the ULB.
2. A state admin will be able to view the dashboard for all plants in the ULB.

Navigation:

On landing on the dashboard, the user can navigate across the treatment process types to view the dashboard specific to the treatment process type.

Filters:

1. Date range: Users should be able to filter based on the date range.
2. ULB: Users should be able to filter based on the ULB. For a ULB employee, the ULB is auto-selected to the ULB the plant and employee is tagged to. For a state user, all ULBs are available.
3. Plant: Users should be able to filter based on the plant. For ULB employees, plants tagged to the ULB to which the employee belongs should be available in the dropdown. For state users, all plants are available.

Other functionalities:

* Share:&#x20;

&#x20;     \- Users should be able to share a filtered dashboard over WhatsApp in an image format.

&#x20;     \- Users should be able to share filtered charts/tables over WhatsApp in an image format.

* Download:&#x20;

&#x20;     \- Users should be able to download the filtered dashboard in PDF and image formats.

&#x20;     \- Users should be able to download the filtered charts/tables in PDF and image formats.

**Metrics**

Overall KPIs:&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-15 at 10.09.55 AM.png" alt=""><figcaption></figcaption></figure>

The dashboard will display the following KPIs:

* Total incoming sludge: The sum of the total sludge that is disposed of at the plant for the selected time period.
* Number of trips: A count of total incoming vehicles at the treatment plant for the selected time period.
* Overall quality: The number of tests where all parameters are as per benchmarks as compared to the total number of test results recorded.
* Compliance percentage: The percentage of tests where results have been recorded
* Total alerts: A Count of total alerts raised of the following types: Test results not as per benchmark, the number reading from IoT device, and lab results and IoT results not matching.

Treatment quality overview:

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-15 at 10.12.41 AM.png" alt=""><figcaption></figcaption></figure>

KPIs:

* Total plants - A count of the unique plants for the particular treatment process.
* Count of plants who have passed the treatment quality as per the last recorded test.
* Count of plants who have failed the treatment quality as per the last recorded test.

Treatment quality is said to have passed if all parameters for final output(s) of a treatment process are as per benchmarks. Treatment quality is said to have failed if 1 or more parameters for final output(s) of a treatment process is not as per benchmarks.&#x20;

Map:

A map view of the location of each plant will be displayed as part of the dashboard. Plants here will be colour coded, based on whether it has passed/failed the treatment quality. (Red = failed, Green = passed).

Table:

A table will be available to plant-wise details of test results (pass/fail), and the compliance percentage. This will be as per the last test result. The user will also be able to see a change in compliance percentage compared to the last month. A drilldown will be made available for a plant via this table. For TRP users and ULBs, where only 1 plant is tagged for the process type, the drilled table is automatically visible.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-15 at 10.15.56 AM.png" alt=""><figcaption></figcaption></figure>

On drilldown, the following is viewable to the user:

1. Heading - Name of plant.
2. Table displaying the following fields:

&#x20;      a. Stage, output type, value of parameters, and compliance percentage.

&#x20;      b. Button to view the trends for a particular stage.

3. Toggle to toggle between IoT readings and lab results.The selected test type will appear highlighted.
4. If there are multiple process flows, then the user can switch between process flows by using the buttons. The selected process flow will appear highlighted.

Trends of parameter readings:

This chart will be available once the user clicks on the view trend button in the table button.

The table shows the trend for one parameter over time and provides a view of the benchmark for comparison. A toggle is available to navigate between parameters.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-15 at 10.18.09 AM.png" alt=""><figcaption></figcaption></figure>

## Out of Scope

The following is out of scope:

1. Testing for parameters beyond those defined for a plant. If testing needs to be recorded for an additional parameter, these need to be configured for a plant first before testing can be performed.
2. Verification of test result documents uploaded by the user: While the system will mandate the user to upload the test result document, verification of the document and ensuring correctness of the information recorded is not in scope.
3. There is some initial uptake in the market for mobile treatment units, which bring treatment onsite to the citizen. Here treatment is done within the mobile treatment unit. We are unaware of how this technology works in terms of recording and storing treatment quality and hence this is out of scope. &#x20;
4. Editing test results once recorded by the user in case of manual testing.
5. Editing IoT device readings.
6. Recording of the data trail in cases when testing parameters have been added/deleted/updated.
7. Testing parameters may be changed at any point. However, test schedules may already be generated and testing will be done based on old parameters defined when the test schedule is generated.
8. No tracking of reason if test results are not recorded as per schedule.
9. In case a schedule for a test is available, but the user fills the test results directly via the “Record Result” page, this will not be adjusted.
10. Escalation in case of non-compliance to the testing schedule will be done once per test. If test results are still not recorded, no further action will be taken.
11. UI for defining testing requirements and adding/disabling/editing testing parameters.
12. As per our field study, one plant has only one treatment process per treatment process type. The dashboard does not cover calculations for a plant that may have 2 processes for the same treatment process type. For example, For faecal sludge, the plant will either run an aerobic or an anaerobic process and not 2 process flows, one for aerobic and one for anaerobic.
13. Activating/deactivating IoT devices from the frontend.

## Assumptions

| Theme                            | Assumption                                                                                                                                                                                                                                                                                                                                                                                                |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Testing Parameters and Standards | Testing parameters are a defined set for a particular process type, stage and input/output type combination, and so do not vary at a high frequency. Hence, they can be configured in the MDMS.                                                                                                                                                                                                           |
| Testing                          | <p>1 user will be responsible for managing the treatment quality of 1 plant for a process type.</p><p><br></p><p>Multiple parameters at one stage of a plant with the same testing frequency are tested together and monitored as one test.</p><p><br></p><p>Governing bodies such as the PCB perform adhoc tests, and will use the system to create a record of the results for the same.</p><p><br></p> |
| Anomaly Detection                | <p>For a test result containing multiple parameters, if 1 parameter is not as per benchmark, we can categorise the test results as not as per benchmarks</p><p><br></p><p>Since IoT readings will be captured at high frequency, anomalies will be generated only if the test value for a parameter is not as per benchmarks for [X] days.</p>                                                            |
| IoT Integration                  | A standard adaptor will be made available for IoT integration. However, the adaptor may need to be modified on a case basis during implementation.                                                                                                                                                                                                                                                        |

## Reference Policies

**Effluent Parameters**

While each state is free to monitor the parameters applicable in their context, the platform mandates [MOEFCC’s October 13, 2017 Notification](http://ismenvis.nic.in/database/notification\_13th\_oct\_2017-gsr1265e\_15634.aspx) as the minimum requirement for effluent quality monitoring.

| Parameter   | Unit        | Value Range | Location                                                                                                                                                                                                                                                                                             |
| ----------- | ----------- | ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| pH          | -           | 6.5 - 9     | Anywhere                                                                                                                                                                                                                                                                                             |
| BOD         | mg/L        | 20          | Metro Cities and all State Capitals except in the State of Arunachal Pradesh, Assam, Manipur, Meghalaya Mizoram, Nagaland, Tripura Sikkim, Himachal Pradesh, Uttarakhand, Jammu and Kashmir and Union Territory of Andaman and Nicobar Islands, Dadar and Nagar Haveli Daman and Diu and Lakshadweep |
| 30          | Other areas |             |                                                                                                                                                                                                                                                                                                      |
| TSS         | mg/L        | < 50        | Metro Cities and all State Capitals except in the State of Arunachal Pradesh, Assam, Manipur, Meghalaya Mizoram, Nagaland, Tripura Sikkim, Himachal Pradesh, Uttarakhand, Jammu and Kashmir and Union Territory of Andaman and Nicobar Islands, Dadar and Nagar Haveli Daman and Diu and Lakshadweep |
| < 100       | Other areas |             |                                                                                                                                                                                                                                                                                                      |
| F. Coliform | N/100mL     | < 1000      | Anywhere                                                                                                                                                                                                                                                                                             |
| COD         | mg/L        | <p><br></p> | (?)                                                                                                                                                                                                                                                                                                  |

\*Metro Cities are Mumbai, Delhi, Kolkata, Chennai, Bengaluru, Hyderabad, Ahmedabad, and Pune.

During implementation, these will be setup by the system integrators as per the state policy.

**Biosolids Parameters**

Regulations for biosolids are unclear - we currently don't have a definitive GoI-notified standard for faecal sludge-derived biosolids. The Advisory and Primer on FSSM (along with the CPHEEO Manual) recommended US EPA Class A Biosolids criteria (looking at E Coli/F Coli, Salmonella, Helminth Eggs). The National Policy on FSSM issued after all these three makes mention of SWM Rules, 2016, as the guiding document for processed sludge quality.&#x20;

Taking from the [Quality in Faecal Sludge Management (Benchmarks, Standards, and Specifications)](https://fssmquality.org/uploads/documents/Quality%20in%20FSM%20v1.0.pdf) by NFSSMA and [Plain English Guide Part 503 Biosolids Rule](https://www.epa.gov/sites/default/files/2018-12/documents/plain-english-guide-part503-biosolids-rule.pdf),[ SWM Rules 2016](https://moef.gov.in/wp-content/uploads/2017/08/SWM-2016-English.pdf), the platform mandates minimum parameters as listed below, while keeping the flexibility for the States to choose or add as per its context.

| Parameter                                                                      | Unit           | Value Range                                                                                                                     |
| ------------------------------------------------------------------------------ | -------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Temperature                                                                    | Degree Celsius | (?)                                                                                                                             |
| Moisture                                                                       | Percentage     | (?)                                                                                                                             |
| <p>E.Coli </p><p>OR</p><p>F. Coli</p>                                          | MPN            | <p>&#x3C; 1000 MPN (E-coli)/g Total solids </p><p>OR </p><p>&#x3C; 1000 CFU (Faecal coliform)/g Total solids by dry weight)</p> |
| Heavy metals (Arsenic, cadmium, chromium, copper, lead, mercury, nickel, zinc) | grams          | (?)                                                                                                                             |

**Medical Waste: Brazil**

The following are the acceptable parameters for medical waste according to Brazilian Standard NBR:

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-15 at 11.19.12 AM.png" alt=""><figcaption></figcaption></figure>
