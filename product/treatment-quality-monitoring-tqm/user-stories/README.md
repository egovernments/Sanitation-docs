# User Stories

## User Story 1: Register Testing Standards

#### **Scope:**

This user story aims to enable the state and the urban local body (ULB) admin to define the input/output quality testing requirements, including testing parameters, benchmarks, and frequencies for each treatment process and stage in the plant. It also allows them to specify different standards for manual and IoT-based testing for particular input/output types and stages. No UI is required for the same.

#### Actors:

\- State admin

\- ULB admin

#### Details:

\- Setup plants, treatment process and stages, and map plants to the treatment process and stages.

\- Plants may contain one or more treatment processes, each with a treatment process type and capacity.

\- A treatment process will contain multiple stages.

\- The state or ULB admin can define input/output testing requirements for each treatment process type and stage.

\- They can enable or disable testing for specific input/output types and stages.

\- They can define testing parameters, benchmarks, and frequencies at the national/state level.

\- They can adjust testing frequencies for plants based on their testing results.

\- They can specify different testing standards for manual and IoT-based testing for specific input/output types and stages.

#### Attributes Table

1. Treatment process

| Attribute                                          | Type    | Mandatory | Comments                                                                               | Validation Required?                      |
| -------------------------------------------------- | ------- | --------- | -------------------------------------------------------------------------------------- | ----------------------------------------- |
| Treatment Process ID                               | Numeric | Y         | Auto-generated numeric value which will act as a unique identified for a process flow. | N, this value should be system-generated. |
| <p>Process Name</p><p><br><br><br><br><br><br></p> | Text    | Y         | This is the commonly-used identifier for the process flow.                             | Max characters - 256                      |
| Status                                             | Array   | Y         | Status of the process flow.                                                            | Active/Inactive, Single Select            |
| Treatment Process Type                             | Array   | Y         | The dropdown will be auto-populated basis the list of waste maintained in the MDMS.    | <p>Single Select</p><p><br><br></p>       |
| Treatment Process Sub-type                         | Array   | Y         | The dropdown will be auto-populated basis the list of waste maintained in the MDMS.    | <p>Single Select</p><p><br><br></p>       |

2. Plants

| Attribute                                        | Type     | Mandatory | Comments                                                                        | Validation Required?                                         |
| ------------------------------------------------ | -------- | --------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| Plant ID                                         | Numeric  | Y         | Auto-generated numeric value which will act as a unique identifier for a plant. | Auto-generated                                               |
| <p>Plant Name</p><p><br><br><br><br><br><br></p> | Text     | Y         | This is the commonly-used identifier for the plant                              | Maximum characters - 128                                     |
| Plant Type                                       | Array    | Y         | <p><br></p>                                                                     | Single Select only, Faecal Sludge, Solid Waste, Co-treatment |
| Tenant Id                                        | Text     | Y         | <p><br></p>                                                                     | <p><br></p>                                                  |
| Status                                           | Array    | Y         | Status of the plant                                                             | Active/Inactive, Single Select                               |
| Geolocation                                      | Lat,Long | Y         | <p><br></p>                                                                     | Capture the exact latitude-longitude                         |

3. Stages:

| Attribute                                        | Type    | Mandatory | Comments                                                                                                                                                                                                                                            | Validation Required?                                           |
| ------------------------------------------------ | ------- | --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| Stage ID                                         | Numeric | Y         | Auto-generated numeric value which will act as a unique identifier for a job ID.                                                                                                                                                                    | Auto-generated                                                 |
| <p>Stage Name</p><p><br><br><br><br><br><br></p> | Text    | Y         | This is the commonly-used identifier for the job.                                                                                                                                                                                                   | <p>Maximum characters - 128</p><p>Minimum Characters - NA </p> |
| Status                                           | Boolean | Y         | Status of the stage.                                                                                                                                                                                                                                | Active/Inactive, Single Select                                 |
| Input Quality Measurement Required               | Boolean | Y         | This selection will allow the user to setup if the input quality for the particular input type needs to be monitored. The user should be able to enable and disable input quality measurement requirement independently for each type.              | Yes/No, Single Select                                          |
| Output Type                                      | Array   | Y         | The dropdown will be auto-populated basis the list of output types.                                                                                                                                                                                 | Multi-select                                                   |
| Output Quality Measurement Required              | Boolean | Y         | <p>This selection will allow the user to setup if the output quality for the particular job needs to be monitored. The user should be able to enable and disable output quality measurement requirement independently for each type.</p><p><br></p> | <p>Yes/No, Single Select</p><p><br><br></p>                    |

4. Testing Parameters

| Attribute                                    | Type    | Mandatory | Validation                                                                                                                                   |
| -------------------------------------------- | ------- | --------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| Quality Parameter                            | Array   | Y         | Selecting from the predefined of the above-mentioned quality parameters and standards, Single Select.                                        |
| Quality Parameter Unit of Measurement        | Array   | Y         | Selection of unit of measurement (mg/L, Absolute value etc.), Single Select.                                                                 |
| Benchmark Rule                               | Array   | Y         | Options include X>=,<=R, =\<Y and >=Z, Single Select.                                                                                        |
| Benchmark Value                              | Numeric | Y         | Entered by user, numeric only.                                                                                                               |
| Testing Frequency - Manual (Days)            | Numeric | Y         | Selecting a custom frequency range for laboratory testing based on consent to operate, numeric only.                                         |
| Monitoring Frequency - Quality Sensor (Days) | Numeric | N         | <p>Selecting a custom frequency</p><p>Note: Should be optional if the ULB/State chose NOT to have sensor-based monitoring, numeric only.</p> |

#### Configurations:

This feature can be managed through backend configurations and databases, allowing administrators to make changes easily.

#### User Actions:

\- A state or ULB admin can define the input/output testing requirements for each treatment process and stage.

\- They can enable or disable testing for specific input/output types and stages.

\- They can define and edit testing parameters, benchmarks, and frequencies at the national/state level.

\- They can adjust testing frequencies for plants based on their testing results.

\- They can specify different testing standards for manual and IoT-based testing for specific input/output types and stages.

#### Notifications:

No specific notifications are required for this user story.

#### User Interface:&#x20;

N/A

#### Acceptance Criteria:

1\. A state and ULB admin can define input/output testing requirements for each treatment process and stage.

2\. They can enable or disable testing for specific input/output types and stages.

3\. Testing parameters, benchmarks, and frequencies can be defined and managed at the national/state level.

4\. Administrators can adjust testing frequencies for plants based on their testing results.

5\. Different testing standards can be specified for manual and IoT-based testing for specific input/output types and stages.

## User Story 2: Generate Schedule

#### Scope

This user story aims to automate the generation of schedules for tests based on the frequency of testing for various parameters. The generated schedule will be used for manual and IoT tests to display upcoming tests, generate alerts, and facilitate escalation in case of non-adherence to the test schedule.

#### Actors:

DIGIT Sanitation

#### Details:

As a system, I want to automatically generate schedules for tests based on the frequency of testing for various parameters. This will help in displaying upcoming tests to the plant operator and stakeholders, generate alerts for upcoming tests, and escalate in case of non-adherence to the test schedule.

#### Workflow:

![](https://lh3.googleusercontent.com/MVjxhQ6btJQofvCa2ee7co3Wo4Rr3PJro32-KDUHxjQBJsi9MCJcQUW9ePZFIFwuEEdw7ecuXhYQLEYiv95PWpKjkD3FMKbDtXCfeO\_BoiDFWiVN40EsLODwK3XKKflr27QfU5lfmBHkOIz06heEz28)

#### Attributes Table:

| Attribute              | Type         | Mandatory   | Validation                                                                                                                                                                                                                                                                                                       |
| ---------------------- | ------------ | ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Test ID                | Alphanumeric | View Only   | Auto-generated on the creation of schedule.                                                                                                                                                                                                                                                                      |
| Plant Name             | Text         | View Only   | Auto-populated on the creation of schedule.                                                                                                                                                                                                                                                                      |
| Treatment Process      | Text         | View Only   | Auto-populated on the creation of schedule.                                                                                                                                                                                                                                                                      |
| Treatment Process Type | Text         | View Only   | Auto-populated on the creation of schedule.                                                                                                                                                                                                                                                                      |
| Stage                  | Text         | View Only   | Auto-populated on the creation of schedule.                                                                                                                                                                                                                                                                      |
| Output Type            | Text         | View Only   | Auto-populated on the creation of schedule.                                                                                                                                                                                                                                                                      |
| Test Type              | Array        | <p><br></p> | Lab/IoT, auto-selected to the lab.                                                                                                                                                                                                                                                                               |
| Parameter 1…n          | Text         | View Only   | Auto-populated on the creation of schedule.                                                                                                                                                                                                                                                                      |
| Testing Date           | Date         | View Only   | Date calculated through a predefined laboratory testing schedule.                                                                                                                                                                                                                                                |
| SLA                    | Numeric      | View Only   | Difference between the current date and testing date. The compliance to a testing schedule can be checked through this field. However, the actions based on failed/successful compliance falls under vendor management, which is not in scope currently and will be taken up separately under vendor management. |
| Status                 | Text         | View Only   | Status to be auto set to 'Scheduled'.                                                                                                                                                                                                                                                                            |

#### Configurations:

This feature can be managed through backend configurations and databases, allowing administrators to make changes easily.

#### User Actions:

\- The system will automatically generate schedules for tests based on the frequency of testing for various parameters.

\- Plant operators and stakeholders can view the upcoming tests on the schedule.

\- Alerts will be automatically generated for upcoming tests to notify the relevant parties.

\- In case of manual testing, escalations will be triggered if test results are pending beyond the specified days as per the test schedule.

#### Notifications:

\- Alerts will be sent to the the plant operator and stakeholder \[X] days prior to the test date.

\- Escalations will be triggered for pending test results as per the test schedule.

#### User Interface:

N/A

#### Acceptance Criteria:

1\. The system should automatically generate schedules for tests based on the frequency of testing for each parameter.

2\. Upcoming tests should be displayed to the plant operator and stakeholders.

3\. Alerts should be generated for upcoming tests to notify the relevant parties.

4\. Escalations should be triggered in case of non-adherence to the test schedule for manual testing.

5\. The implementation of this feature should allow for easy configuration and management through backend settings.

## User Story 3: Anomaly Detection 1.0

#### Scope:

This user story aims to implement an anomaly detection system that generates alerts in case of the following anomalies:

1\. Lab results not as per the benchmark.

2\. IoT device results not as per the benchmark.

3\. Lab results and device results do not match.

#### Actors:

\- Test uploader

\- IoT system

\- DIGIT Sanitation

#### Details:

As a system, I want to detect anomalies in the test results and generate alerts for the following scenarios:

#### Attributes Table:

| Field                  | Data Type | Required | Description                                                                                         |
| ---------------------- | --------- | -------- | --------------------------------------------------------------------------------------------------- |
| Anomaly Type           | String    | Yes      | Specifies the type of anomaly detected.                                                             |
| Benchmark              | Float     | Yes      | Defines the benchmark value for the test results.                                                   |
| Deviation Allowed      | Float     | Yes      | Specifies the allowed deviation from the benchmark for anomaly detection.                           |
| Sample Collection Date | DateTime  | Yes      | The date on which the sample was collected for testing.                                             |
| IoT Result Date        | DateTime  | Yes      | The date on which the IoT result was recorded.                                                      |
| Alert Generation Date  | DateTime  | Yes      | The date on which the alert was generated.                                                          |
| Lab Test Result        | Float     | Yes      | The result of the manual lab test.                                                                  |
| IoT Test Result        | Float     | Yes      | The result recorded via IoT integration.                                                            |
| Alert Message          | String    | Yes      | Specifies the message for the generated alert.                                                      |
| Matching Date          | DateTime  | Yes      | The date on which the closest IoT result is matched with the sample collection date for comparison. |

#### Workflows:&#x20;

Lab results not as per the benchmark

This is to be generated when the manual test results uploaded by the test uploader are not as per the benchmarks defined (adjusted for deviations, configurable at plant level).

![](https://lh6.googleusercontent.com/BaUb8Ynj1eKroIL53kMeDqSFPrxkgNenwKgJNnM\_O\_E6gXXW9dRyf9WdEErp5cNw2XNZfNqE1GHMTmK9KzlYH2Nab0pT0pzcqoMHRYv-nijQU0wCaHHYi660W1OLg3oJs7I753eBliBidOvR2NDmjtY)

IoT results not as per the benchmark

This is to be generated when the loT test results recorded via the integration are not as per the benchmarks defined for \[X] days (adjusted for deviations defined while setting testing parameters).

![](https://lh4.googleusercontent.com/0Bkb0sETJEr5JEUnOTIeSehxMcK8ioYaONjh\_AQNtUAr73v3w-Syh7kpE0hwg4jb-3LFBKeVUHB-Gh--1fVXSnMBL6\_wm2kNJfbRJ-7uePR6nIajPJO81AZyor4z\_7O82CDg5dscYe4a1xJ4vKtD9iw)

Generation of alerts: Device results and lab results do not match

In case the data that is recorded by the sensor does not match the data in the lab test result, an auto alert will generated.

| Date to be matched on | <p>Sample Collection Date</p><p><br></p><p>If the IoT result is not available for the sample collection date, the closest date after for which IoT data available to be considered.</p> |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Deviation allowed     | x%                                                                                                                                                                                      |

#### &#x20;Validations:

\- Anomaly types, benchmark values, and allowed deviations should be specified for each scenario.

\- The matching date for comparing IoT results should be calculated based on the sample collection date and the closest available IoT result date.

\- Anomalies should be detected and alerts generated only if the deviation from the benchmark exceeds the allowed deviation.

#### Configurations:

\- The anomaly detection system should be configurable to define benchmark values, allowed deviations, and matching date logic.

#### User Actions:

\- The test uploader uploads manual lab test results.

\- The integration system records IoT test results.

\- DIGIT Sanitation continuously monitors the test results.

\- Alerts are automatically generated if anomalies are detected.

#### Notifications:

\- Alerts will be generated automatically when any of the specified anomalies are detected.

\- The alert message will indicate the type of anomaly and the details of the test results.

#### Acceptance Criteria:

1\. The system should be able to detect and generate alerts for the specified anomalies, including lab results not meeting benchmarks, IoT results not meeting the benchmark, and lab and IoT results not matching

2\. The allowed deviation for each anomaly type should be configurable.

3\. The anomaly detection should be based on the benchmark values set for each type of test result.

4\. Alerts should be generated with the appropriate message indicating the type of anomaly detected and the details of the test results.

5\. The implementation should allow for easy configuration and management through backend settings.

## User Story 4: Anomaly Detection 2.0

#### Scope:

This user story aims to implement an automated alert generation system for cases where no reading is received from a sensor based on the scheduled frequency.

#### Actors:

\- Integration system

\- DIGIT Sanitation

#### Details:

As a system, I want to automatically generate an alert in case no reading is received from a sensor based on the scheduled frequency.

#### Workflow:

![](https://lh6.googleusercontent.com/84AhQj9Ptvc8iUBdZn\_Q5rxO5TMuDwVHqp\_fUdQKotBcsW5vycQnTdh5M4lLP-vv9kWQoKZpp0IUKus2QMIBFPgBw50zsCLXJ9cdXdLkoALC3qIQRKBr1aqxBVFsT7NUpuLeujiSjhkaeJcDe645X3w)

#### Attributes Table:&#x20;

No reading received from device

| Attribute      | Type     | Required? | Comments                                                                   |
| -------------- | -------- | --------- | -------------------------------------------------------------------------- |
| Alert DateTime | Datetime | Y         | Auto-captured based on the date-time.                                      |
| Alert Type     | Text     | Y         | <p>Auto-captured</p><ul><li>No reading received from the device.</li></ul> |
| Plant Name     | Text     | Y         | Auto-captured                                                              |
| Process Name   | Text     | Y         | Auto-captured                                                              |
| Process Type   | Text     | Y         | Auto-captured                                                              |
| Device ID      | Numeric  | Y         | Auto-captured                                                              |

#### Validations:

\- The system should check if a reading was expected from the sensor on the scheduled date.

\- An alert should be generated only if no reading is received from the sensor on the scheduled date.

#### Configurations:

\- The alert generation system should be configured to specify the frequency of expected readings from each sensor.

#### User Actions:

\- The integration system monitors the scheduled frequency of readings from the sensors.

\- The alert generation system automatically detects cases where no reading is received from a sensor based on the scheduled date.

#### Notifications:

\- An alert will be generated automatically if no reading is received from a sensor based on the scheduled date.

\- The alert message will indicate the sensor ID and the scheduled date for the next reading.

#### Acceptance Criteria:

1\. The system should automatically detect cases where no reading is received from a sensor on the scheduled date.

2\. Alerts should be generated with the appropriate message indicating the sensor ID and the scheduled date for the next reading.

3\. The alert generation should be based on the configured frequency of expected readings from each sensor.

4\. The implementation should allow for easy configuration and management through backend settings.

## User Story 5: Landing Page: Plant Operator

#### Scope:

As a plant operator, I want to access the home page after logging in to the system. The landing page should provide an overview of relevant modules, pending tasks, and options to navigate to the specific sections.

#### Actors:

Plant operator

#### Details:

Upon successful login, the plant operator will be directed to the home page. The home page will display the following elements:

1. Plant name: A visible label located on the top right-hand corner of the screen, indicating the name of the plant or facility the operator is associated with.
2. Help button: A clickable button available on every page to provide a guided view and assistance for users.
3. Modules cards: The home page will show cards for the following modules:

a) Vehicle Log Module: Allows the user to record incoming vehicles.

b) Treatment Quality Monitoring module: Provides access to information related to treatment quality.

c) View Dashboard: Navigates the user to a comprehensive dashboard.

4. List of pending tasks: This section will display a list of tests and tasks pending for the plant operator within the next \[X] days. Alongside each pending task, the next action item in the workflow will be displayed, enabling the plant operator to take prompt action.
5. View all pending tasks button: A clickable button that redirects the user to a page displaying all pending tasks.

#### Attributes:&#x20;

N/A

#### Validations:

N/A

#### Configurations:

N/A

#### User Actions:

* The plant operator can click on the cards representing different modules to navigate to their respective home pages for detailed information and functionalities.
* The plant operator can click on the "View All Pending Tasks" button to view all pending tasks in the system.

#### Notifications:

N/A

#### User Interface:

### ![](https://lh3.googleusercontent.com/78vMChzBcucXs6F-GUs34Z8ippKCzTJFKL6tmPr1OIgfJZmsX7cWD4\_RHKvtlX1kwDTj980XRI6UEi7vk4wBR7e9GzqEj2GUpbAOPGi6O4hALkekbbADUPEjNigjzRQIBeCncgLCyC6YQ0lzRB5hEK4)

#### Acceptance Criteria:

* The plant operator should be able to log in successfully and land on the home page.
* The home page should display the plant name, help button, and cards for the different modules.
* The list of pending tasks should be visible and filtered based on the defined time frame \[X].
* Each pending task should display the next action item required.
* Clicking on the cards should redirect the user to the respective module's home page.
* Clicking on the "View All Pending Tasks" button should redirect the user to a page displaying all pending tasks.

## User Story 6: Treatment Quality Monitoring (TQM) Home Page

#### Scope:

As a plant operator, I want to access the Treatment Quality Monitoring (TQM) home page by clicking on the treatment quality card. The TQM home page should provide access to upcoming tests, past test results, IoT readings, sensor monitoring, treatment quality dashboard, and performance metrics related to treatment quality.

#### Actors:

Plant operator

#### Details:

After clicking on the treatment quality card, the plant operator will be redirected to the TQM home page, which will offer the following functionalities:

1. Inbox: The inbox will display the upcoming tests, and the plant operator can take necessary actions related to these tests. A count of the upcoming tests for quick reference will be displayed in brackets.
2. View past test results: This section will present the past results from both ab and IoT devices, allowing the plant operator to review historical data.
3. View IoT readings: The user can access records of IoT readings, enabling them to monitor IoT devices' data.
4. Sensor monitoring: A list of IoT devices and their status will be available for the plant operator to monitor and ensure smooth operations.
5. View dashboard: Clicking on this option will direct the plant operator to the treatment quality dashboard, providing comprehensive insights and visualisations.
6. View performance: This widget will display key performance indicators (KPIs) related to treatment quality, including:

&#x20;      a. Test compliance: The percentage of plant compliance with treatment quality standards, compared to the state-level compliance percentage.

&#x20;      b. Last treatment quality result: Indicates whether the last test result was a pass or fail, along with the date of the test.

&#x20;      c. Count of alerts raised in the past 30 days: Shows the number of alerts generated within the last 30 days.

&#x20;      d. Distribution of alerts based on the alert category: Presents a breakdown of alerts by their respective categories. (Note: For details about the calculation of these metrics, refer to the dashboard user stories).

&#x20;      e. Go back to the landing page: The plant operator can use the back button to return to the landing page.

&#x20;      f. Help button: A clickable button available on every page to provide a guided view and assistance for users.

#### Attributes Table:

N/A

#### Validations:

N/A

#### Configurations:

N/A

#### User Actions:

* The plant operator can view upcoming tests in the inbox and take necessary actions related to them.
* The plant operator can review past test results from both Lab and IoT devices.
* The plant operator can access records of IoT readings for monitoring purposes.
* The plant operator can check the status of IoT devices through sensor monitoring.
* The plant operator can navigate to the treatment quality dashboard for comprehensive insights.
* The plant operator can view the performance metrics related to the treatment quality.
* The plant operator can use the back button to return to the landing page.

#### Notifications:

N/A

#### User Interface:

![](https://lh3.googleusercontent.com/nUTkgu5OfW4\_NU9ML\_JUva9ZUNDM1CxRrvczHMXb0\_2LLEUeQfH8n7kDwZ4ntZ8KIBZBAmFt6ubRoaGwtUtgbTX1aXRIVA7OrzxLp7hM4MlIU2xI4R8Fu5UWVo5hbZh8bcI9JfC8zx\_bDbxprgLNWUg)

#### Acceptance Criteria:

* The plant operator should be able to access the TQM home page by clicking on the treatment quality card.
* The TQM home page should display the inbox with the upcoming tests and their count.
* The plant operator should be able to view the past test results from lab and IoT devices.
* The plant operator should be able to access the records of IoT readings.
* The plant operator should be able to monitor IoT devices and their statuses.
* Clicking on "View Dashboard" should redirect the plant operator to the treatment quality dashboard.
* The performance metrics should accurately display test compliance, last treatment quality result, count of alerts raised in the past 30 days, and distribution of alerts based on their categories.
* The back button should allow the plant operator to return to the landing page.
* The help button should be available and functional on the TQM home page.

## User Story 7: View List of Upcoming Tests

#### Scope:

As a plant operator, I want to view a list of the upcoming tests by clicking on the 'Inbox' option. The list should display only lab tests, and I should be able to perform various tasks, such as filtering, sorting, and accessing the test details.

#### Actors:

Plant operator

#### Details:

Upon clicking on the 'Inbox', the plant operator will be redirected to the list of upcoming lab tests. The following functionalities will be available:

* Total count of the upcoming tests: The total count of the upcoming tests will be displayed beside the inbox, enclosed within brackets.
* View list of the upcoming tests: The list will contain the following fields:

&#x20;     \- Test ID

&#x20;     \- Treatment process (if there is only one treatment process configured for the plant, this field will not be displayed)

&#x20;     \- Stage: Indicates the process stage where the sample is to be collected from.

&#x20;     \- Output type: Specifies whether the test is for biosolids or effluents.

&#x20;     \- Pending date: The scheduled test date.

&#x20;     \- Status: The current status of the test.

&#x20;     \- SLA: Displays the difference between the test due date and today.

#### Workflow:

![](https://lh3.googleusercontent.com/MVjxhQ6btJQofvCa2ee7co3Wo4Rr3PJro32-KDUHxjQBJsi9MCJcQUW9ePZFIFwuEEdw7ecuXhYQLEYiv95PWpKjkD3FMKbDtXCfeO\_BoiDFWiVN40EsLODwK3XKKflr27QfU5lfmBHkOIz06heEz28)

#### Attributes Table:

| Attribute              | Type         | Mandatory   | Validation                                                                                                                                                                                                                                                                                                       |
| ---------------------- | ------------ | ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Test ID                | Alphanumeric | View Only   | Auto-generated on the creation of the schedule.                                                                                                                                                                                                                                                                  |
| Plant Name             | Text         | View Only   | Auto-populated on the creation of the schedule.                                                                                                                                                                                                                                                                  |
| Treatment Process      | Text         | View Only   | Auto-populated on the creation of the schedule.                                                                                                                                                                                                                                                                  |
| Treatment Process Type | Text         | View Only   | Auto-populated on the creation of the schedule.                                                                                                                                                                                                                                                                  |
| Stage                  | Text         | View Only   | Auto-populated on the creation of the schedule.                                                                                                                                                                                                                                                                  |
| Output Type            | Text         | View Only   | Auto-populated on the creation of the schedule.                                                                                                                                                                                                                                                                  |
| Test Type              | Array        | <p><br></p> | Lab/IoT, auto-selected to the lab.                                                                                                                                                                                                                                                                               |
| Parameter 1…n          | Text         | View Only   | Auto-populated on the creation of the schedule.                                                                                                                                                                                                                                                                  |
| Testing Date           | Date         | View Only   | Date calculated through predefined laboratory testing schedule.                                                                                                                                                                                                                                                  |
| SLA                    | Numeric      | View Only   | Difference between the current date and testing date. The compliance to a testing schedule can be checked through this field. However, the actions based on failed/successful compliance falls under vendor management, which is not in scope currently and will be taken up separately under vendor management. |
| Status                 | Text         | View Only   | Status to be auto set to 'Scheduled'.                                                                                                                                                                                                                                                                            |



| Test Result Status | Roles                           | Action                         | Next Status     |
| ------------------ | ------------------------------- | ------------------------------ | --------------- |
| Scheduled          | <p>FSTPO</p><p>ULB employee</p> | Submit the sample for testing. | Pending results |
| Pending Results    | <p>FSTPO</p><p>ULB employee</p> | Update the results.            | Submitted       |

#### Configurations:

N/A

#### User Actions:

* The plant operator can view a list of the upcoming tests with the relevant details.
* The plant operator can use filters to refine the view based on the treatment process, output type, status, and date range.
* The plant operator can use sorting options to arrange the tests based on "Pending Date."
* The plant operator can access test details for further actions.

#### Notifications:

N/A

#### User Interface:

#### ![](https://lh5.googleusercontent.com/DIAjnHXixgwCMfs7sZcriTo\_S-X0u0zCM3DQTm-7MZJkHG7uuk5swBFVA6wTbMROGG\_NjInlb02IXTJYftgITeUBJYL5SkqLJ9uiL63Iw1lu8BnaDdpbKWetJgSwoCNQj4X4E6k63sHciGJ1disoDs4)![](https://lh4.googleusercontent.com/Ebc2v\_9JzSea6Huu6\_aI-wjmHb3\_KCnLhWYjC5wCVrtCcxg0JCpjKory33A8ZZFQ8Sgg8bGRvyxwkJO8y71Voy3\_UvYdhejl3UeBlGR93Q0LUH9NqB55oho\_IGH2a0SF-ekrvirDFyka5j2CAGGbfRw)![](https://lh3.googleusercontent.com/ye\_SbjLNcC2qtKuyQy5nihzXHxrzvODr6UKiOTSOMp7N3\_JDnUK2NnuknYmSX4vG8hb2iQMcWLyZjf2C9aG\_WkF3kWIdElI3zcEjlfBclf5hK\_TxxgH4SuwLkjHL4Wc\_A0F0b8PEBmN45oHK7gOEKaQ)

#### Acceptance Criteria:

* The plant operator should be able to view the list of the upcoming lab tests by clicking on 'Inbox'.
* The list should only display the lab tests.
* The list of the upcoming tests should contain relevant fields as described in the user story.
* The action item displayed should be based on the next status in the treatment quality workflow for each test.
* The filters and sorting options should work correctly, and the data should be updated based on the selected criteria.
* The user should be able to navigate back to the landing page using the back button.
* The help button should be available and functional on the list of upcoming tests page.

## User Story 8: View Test Details

#### Scope:&#x20;

As a plant operator, I want to view the test details for the upcoming tests either via the pending tasks or the inbox. The test details page will provide comprehensive information about the test and allow me to perform specific actions based on the test's status.

#### Actors:

Plant operator

#### Details:

1. &#x20;View test details via the pending tasks:

* The list of pending tasks can be accessed via the landing page for the Treatment Quality Monitoring (TQM).
* The list will display the tests pending within the next \[X] days.
* The next action item in the task workflow will be displayed as a button beside each pending task for the plant operator to take prompt action.
* Clicking on the action item button will redirect the user to the test details page.

2. View test details via the inbox:

* A list of tests can be accessed from the Inbox.
* An action item will be displayed based on the next status in the treatment quality workflow for each test:

&#x20;      \- For tests in the 'Scheduled' stage, the "Update Status" will be shown.

&#x20;      \- For tests in the "Pending Results" stage, the "Update Results" will be displayed.

* Clicking on the action item button will redirect the user to the test details page.

3. Test details page:

It will consist of two cards.\
First card - Test Information:\
The first card will display the following fields:

* Test ID
* Treatment process
* Stage
* Output type
* Pending date
* Status
* Parameters to be tested along with their unit of measurement
* SLA (Displayed in red/green basis SLA. If today is greater than the pending date, it will be shown in red. If today is less than the Pending Date, it will be shown in green.)

Second card -\
Test status specific action: The second card will vary based on the test status:

* For tests in the 'Scheduled' status, the user will be asked to select the lab.
* For tests in the "Pending Results" status, the user will be asked to add test results.

4. Go back using the back button:

* The user can go back using the back button, and the redirection will be based on the page from which the user accessed the test details page (either pending tasks or inbox).

5. Help button:

* A clickable button available on every page to provide a guided view and assistance for users.

#### Test Attributes:

<table data-header-hidden><thead><tr><th></th><th width="163"></th><th width="125"></th><th></th></tr></thead><tbody><tr><td>Attribute</td><td>Type</td><td>Required?</td><td>Comments/Validations</td></tr><tr><td>Test ID</td><td>Numeric</td><td>Y</td><td>Auto-generated by the system.</td></tr><tr><td>Plant Name</td><td>Array</td><td>View Only</td><td>Auto-populated on the creation of the schedule, dingle select for on-demand test.</td></tr><tr><td>Treatment Process</td><td>Array</td><td>View Only</td><td>Auto-populated on the creation of schedule, single select for on-demand test.</td></tr><tr><td>Treatment Process Type</td><td>Array</td><td>View Only</td><td>Auto-populated on the creation of the schedule, single select for on-demand test.</td></tr><tr><td>Stage</td><td>Array</td><td>View Only</td><td>Auto-populated on the creation of the schedule, single select for on-demand test.</td></tr><tr><td>Output Type</td><td>Array</td><td>View Only</td><td>Auto-populated on the creation of the schedule, single select for on-demand test.</td></tr><tr><td>Test Type</td><td>Array</td><td><br></td><td>Lab/IoT, auto-selected to the lab for on-demand.</td></tr><tr><td>Lab Submitted to</td><td>Text</td><td>Y</td><td>This will not be required in case test type = IoT.</td></tr><tr><td>Quality Parameter 1</td><td>Numeric</td><td>Y</td><td>Validation to be applied at impel.</td></tr><tr><td>Quality Parameter 2</td><td>Numeric</td><td>Y</td><td>Validation to be applied at impel.</td></tr><tr><td>Quality Parameter 3</td><td>Numeric</td><td>Y</td><td>Validation to be applied at impel.</td></tr><tr><td>Quality Parameter n</td><td>Numeric</td><td>Y</td><td>Validation to be applied at impel.</td></tr><tr><td>Collection Time</td><td>Date</td><td>Y</td><td>This is the date-time on which user updates the status to pending results. For IoT, this is the time sensor records reading.</td></tr><tr><td>Attachment</td><td>Document</td><td>Y</td><td>For a given collection location, the photo or PDF proof of the laboratory result mentioning the information of the above-mentioned parameters.</td></tr></tbody></table>

#### Configurations:

N/A

#### User Actions:

* The plant operator can view test details either via the pending tasks or the Inbox.
* The plant operator can perform specific actions based on the test's status, such as updating the status or adding test results.

#### Notifications:

#### N/A

#### User Interface:

\
![](https://lh5.googleusercontent.com/DIAjnHXixgwCMfs7sZcriTo\_S-X0u0zCM3DQTm-7MZJkHG7uuk5swBFVA6wTbMROGG\_NjInlb02IXTJYftgITeUBJYL5SkqLJ9uiL63Iw1lu8BnaDdpbKWetJgSwoCNQj4X4E6k63sHciGJ1disoDs4)![](https://lh5.googleusercontent.com/SyqTQEMFwQ90ijdwydWTWXclOsK2YgGMHNFtmR6HlJBcg2qWTiU\_i5Ozx\_cSApfFXl4kJhgjZxRdxwWANIL-bjc7adUt79buFvOqFlAC1XUNfMdtM8yLuTnh2c\_5CpaxKQZ5fYrljXGrJvELXftd0mo)![](https://lh3.googleusercontent.com/W9h8zW47P4MkO41SzU8rpE48lRlRSHS2LP2IkllPcmtteWZwB6cg0uDSw9FcSgrj441ktShXZRCimxJW8bRrWS5Je7Wzc-q8Z5EhRbjG1wAflHk03AOC8Rm8nbY1m2c71rZhSixKCb2lPTVRAUOcNZQ)

#### Acceptance Criteria:

* The plant operator should be able to view the test details via the pending tasks or the inbox.
* The test details page should display accurate information, including test ID, treatment process, stage, output type, pending date, status, parameters, unit of measurement, and SLA.
* The second card on the test details page should prompt the plant operator to take the appropriate action based on the test's status ("Select Lab" for tests in the 'Scheduled' status and "Add Test Results" for tests in the "Pending Results" status).
* The plant operator should be able to navigate back using the back button, and the redirection should be appropriate based on the page from which the test details page was accessed.
* The help button should be available and functional on the test details page.

## User Story 9: Update Tests

#### Scope:

As a plant operator, I want to update the test details from the test details page. The test details page will display the next action item based on the workflow status of the test. I should be able to perform different actions depending on whether the test is in the 'Scheduled' status or the "Pending Results" status.

#### Actors:

\- Plant operator

#### Details:

Updating tests with the workflow status 'Scheduled':

\- The test details page will prompt the plant operator to confirm if the sample has been submitted to the lab for testing.

\- The user can perform the following actions:

&#x20; \- Select lab: The plant operator can choose a lab from a dropdown list configured in the Master Data Management System (MDMS).

&#x20; \- Update the status of the test: The button to update the test status will be deactivated until the lab is selected. Once the lab is chosen, the button will be activated.

\- After clicking on "Update Status," the plant operator will be redirected back to the page from which the test details were accessed. A snack bar will confirm the status update, and the action item button will show the updated next step in the workflow.

\- In case the update of the status fails, the plant operator will remain on the same page, and a failure message will be displayed.

Updating tests with the workflow status "Pending Results":

\- The test details page will prompt the plant operator to fill in the test results.

\- The user can perform the following actions:

&#x20; \- Update parameter readings (mandatory fields): Only numerical values will be allowed. In case non-numerical values are entered, an error message will be displayed, stating "Only numeric values allowed. Please input in the required format."

&#x20; \- Attach documents (non-mandatory): Only files in the formats .png, .jpg, .pdf will be supported. If a file of an unsupported format is selected, an error message will be displayed, stating: "The file type is not supported. Please upload in the following formats: .pdf, .png, .jpg." The file size should be within the permissible limit (X mb), and if the file size is larger, an error message will be displayed, stating: "The file size is too large. Please upload a file below X MB."

&#x20; \- Submit the test results: The button to submit the test results will be deactivated until all mandatory fields are filled. Once all required fields are completed, the button will be activated.

\- On clicking the 'Submit' button, a pop-up will be displayed to the user to confirm the submission.

\- The following actions will be available to the user in the pop-up:

&#x20; \- Confirm submission: The plant operator can confirm the submission by clicking on the 'Submit' button.

&#x20; \- Go back to the test details page: The plant operator can go back to the test details page by clicking on the "Go back" button.

\- In case the submission of test results fails, the plant operator will remain on the same page, and a failure message will be displayed.

After the successful submission of the test results:

\- Upon successful submission, the plant operator will be redirected to the summary page, and a snack bar will confirm the submission.

\- The summary page will display the test results and whether they have passed or failed based on a comparison between the values entered by the user and the benchmarks.

\- If all values are as per the benchmarks, the test results will be displayed as 'Pass'. All values will be shown in green, and the plant operator will receive feedback that all results are as per the benchmarks. The plant operator can go back to the home page by clicking on the back button.

\- If one or more values are not as per the benchmarks, the test results will be displayed as 'Fail'. Values that meet the benchmarks will be shown in green, while values not meeting the benchmarks will be shown in red. The plant operator will be informed that the test results are not as per the benchmark. The plant operator can go back to the home page by clicking on the back button.

#### Workflow:

![](https://lh5.googleusercontent.com/0pxEqH1N06ZHoM3t4vkm18tpqPtxpcRGTBEudTux1JAPe5Bc9WquRdLmeW31Y02iRIpN69KYytvHuVme8pUmLb5KhAg\_8AiWpv\_nyy\_O4vua\_iDyLYc8Cy2hR8RTfnQg5ecYc4dH0A3MCubC4ThaQzQ)

#### Functional Specifications for Tests:

<table data-header-hidden><thead><tr><th></th><th width="146"></th><th width="135"></th><th></th></tr></thead><tbody><tr><td>Attribute</td><td>Type</td><td>Required?</td><td>Comments/Validations</td></tr><tr><td>Test ID</td><td>Numeric</td><td>Y</td><td>Auto-generated by the system.</td></tr><tr><td>Plant Name</td><td>Array</td><td>View Only</td><td>Auto-populated on the creation of the schedule, single select for on-demand test.</td></tr><tr><td>Treatment Process</td><td>Array</td><td>View Only</td><td>Auto-populated on the creation of the schedule, single select for on-demand test.</td></tr><tr><td>Treatment Process Type</td><td>Array</td><td>View Only</td><td>Auto-populated on the creation of the schedule, single select for on-demand test.</td></tr><tr><td>Stage</td><td>Array</td><td>View Only</td><td>Auto-populated on the creation of the schedule, dingle select for on-demand test.</td></tr><tr><td>Output Type</td><td>Array</td><td>View Only</td><td>Auto-populated on the creation of the schedule, single select for on-demand test.</td></tr><tr><td>Test Type</td><td>Array</td><td><br></td><td>Lab/IoT, auto-selected to the lab for on-demand.</td></tr><tr><td>Lab Submitted to</td><td>Text</td><td>Y</td><td>This will not be required in case test type = IoT.</td></tr><tr><td>Quality Parameter 1</td><td>Numeric</td><td>Y</td><td>Validation to be applied at impel.</td></tr><tr><td>Quality Parameter 2</td><td>Numeric</td><td>Y</td><td>Validation to be applied at impel.</td></tr><tr><td>Quality Parameter 3</td><td>Numeric</td><td>Y</td><td>Validation to be applied at impel.</td></tr><tr><td>Quality Parameter n</td><td>Numeric</td><td>Y</td><td>Validation to be applied at impel.</td></tr><tr><td>Collection Time</td><td>Date</td><td>Y</td><td>This is the date-time on which user updates the status to pending results. For IoT, this is the time sensor records reading.</td></tr><tr><td>Attachment</td><td>Document</td><td>Y</td><td>For a given collection location, the photo or PDF proof of the laboratory result mentioning the information of above-mentioned parameters.</td></tr></tbody></table>

#### Configurations:

N/A

#### User Actions:

\- The plant operator can update the test details, including lab selection and test status for tests in the 'Scheduled' status.

\- The plant operator can fill in the test results for tests in the "Pending Results" status, including numerical values for parameter readings and optional document attachments.

\- The plant operator can submit the test results and confirm the submission.

\- The plant operator can go back to the test details page or the home page .

#### Notifications:

N/A

#### User Interface:

![](https://lh5.googleusercontent.com/-Lx9gPsHltridQwS40-tvwmQikQ\_MJWfQm6rlFf-Das7k2CVV6r0D7OEhK2XolhI51JFQufbutjz0dggwkCS2Us5b\_mtxGz3uDR3KcEJCMlryLeogHou8Yz2mng4XqRfFrRB5ZD7RZWumWdjSvJTdlc)![](https://lh4.googleusercontent.com/y0rMSfrkMWtgK9bYv79mmFbuNT7iyjNYnQgDe2HeQ5LFYyZ9K8vua6XrV4zgRPu7CEIm6daXgHOZujnmNacqKMmc-XbgnaXoenfR-M\_oYU10vkqLc-qF6jJdfFmgZ-55cobcD\_Q0XYT91mdPlzepyF0)![](https://lh5.googleusercontent.com/meo-0HAlNnifOjbTPwUSTb05ePv4zChv4XoDFsxdJLhIzqZSzCX5NRoWqm2ri5RDrDtQVSI3imyfVwq2ifR7E\_951PDl9PeyNQb2FE9\_EJJhlmaxBL8T6c-offStZ7XbVhXbH7OITCkgmZaK6WpDYfU)![](https://lh4.googleusercontent.com/OfQ-VH-Fuq5MafROGZrfCh8t9SIR9ktztz96\_g-QRIXbHOz\_2Fhsj5eTLeNb\_xQ-2hAGx1xSV1I8jnkf-7Yyw\_d4O49p4mC\_vsotLdN3pOXZb6cq8AsGBtDxPeK4tuBpsr57xDxs-bE7rSzK8Z8hBJ8)![](https://lh5.googleusercontent.com/JWQAu3gsruTYU0tRKktuTeGoTOyMWo0irKYw1FIt4E-jZDExIdvK0-R9IIMQzSfmndgThj-N3w2Dmj1G8H4KzzloQ70wzvYwCI6EDb17s\_i4ZsCB4bFTReGaYA5fTfjEc9MEAmBGsDz0UPBSCPkUR70)![](https://lh6.googleusercontent.com/28IP6Fw\_1ksLRQ66TmmubDmiW8LqQKddm5Vdy-6s-abs6h2mirchwUnoreaArRPswy3qNoa13h5hzV\_R-G0xSWH1H2O5MXqzYhvkp1NPOp0ap7\_ABZbpnr2HVEPHL2VrP41IoCpE22X8L53L2qRPScA)![](https://lh5.googleusercontent.com/apvjTpUOb5msChlh0EBaLEphPQnaTGRm9vew6oE8U4XWcx8x8AT2VC5up92-uslThnh1Chp97Fv2-NJe\_pXt7KXiRQH3lcyAbLPASEje0dLiGmCLWOJhVe\_hBr3fx7QHM58g1B5KPnyUuAbRS90oe2Q)![](https://lh6.googleusercontent.com/kMhPcqdRhKn-1U4bucgRMlzwv2tE2vjEkX5RsYUASwi8v\_MsQnRqv34idR9sY5yX0XK\_bUI0VJ0cIrV4fbn9Z2bKX5jHPUvj235oAUyDy6A3sZYXfLbC5yTT-tssNwUfVuVzbmMgUj\_vyxgif4Cj8lA)



![](https://lh3.googleusercontent.com/NU0jB6dm-JfF6goshyDFWEb8ZyldQ-r9yqTlUNIrw\_Kn14x06XOAIsnMasadEfggNbBLgDX0g2Jm5aGGVPPpDrdPjw5YAd2VOMJmUUDlFySaVqxJvc4UYJkh0QXpsXDGnXQKXAh709AzmuLmpiUbEaM)![](https://lh6.googleusercontent.com/ALlB0Hi8BELtiojFKgD5rzPcyg3p1YK6xL9y5qrnTPjMh6AejIG7dmXZ3m\_wYkys3vWfSiRRP2K9oqVp3F4c0RX-NN7Vd-Oxc-2itIpx0XZo\_d8RFRZq\_AQ9l9kgt3qv46rwSTCciZf18IvEsfREJ1g)

#### Acceptance Criteria:

\- The plant operator should be able to update the test details for tests in both 'Scheduled' and "Pending Results" status.

\- The test details page should prompt the plant operator with appropriate actions based on the test's workflow status.

\- Validations for numerical values and file formats/sizes should work as described.

\- Successful submission of the test results should redirect the plant operator to the summary page and display the results as 'Pass' or 'Fail' based on the benchmarks.

\- The plant operator should be able to go back to the test details page or the home page using the appropriate buttons.

\- The help button should be available and functional on the test details and summary pages.

## User Story 10: View Past Test Results

#### Scope:

As a plant operator, I want to view past test results (both IoT and lab) by accessing the "Past Tests" section from the Treatment Quality Monitoring (TQM) landing page. I should be able to view a list of past tests, filter and sort them, and access detailed test results for each test.

#### Actors:

\- Plant operator

#### Details:

View past test results:

\- Past test results (both IoT and lab) can be accessed via the TQM landing page by clicking on the "Past Tests" option.

\- Clicking on "Past Tests" will redirect the user to the list of past tests.

\- The user can perform the following tasks:

1\. View the list of past tests:

&#x20;  The list will display the following fields for each test:

&#x20;  \- Test ID

&#x20;  \- Treatment process (if there is only one treatment process configured for the plant, this field will not be displayed).

&#x20;  \- Stage: Indicates the process stage where the sample was collected from.

&#x20;  \- Output type: Specifies whether the test is for biosolids or effluents.

&#x20;  \- Pending date: The test date as per the schedule.

&#x20;  \- Test result: Indicates whether the test result is 'Pass' or 'Fail'.

&#x20;  \- View test details: The user can view detailed test results by clicking on the "View Results" button on each card.

2\. Filter tests:

&#x20;  Clicking on 'Filter' will open a pop-up with the following filter options:

&#x20;  \- Treatment process (if there is only one treatment process configured for the plant, this field will not be displayed): A dropdown with values for treatment processes configured for the plant. The selected treatment process will be displayed upon selection.

&#x20;  \- Output type: A dropdown with values for the output types configured for the plant. The selected output type will be displayed upon selection.

&#x20;  \- Test type: A dropdown with values for test types (IoT/lab). The selected test type will be displayed upon selection.

&#x20;  \- Date range: A calendar view to select a date range. The selected date range will be displayed upon selection.

&#x20;  After selecting the filter values, the user can click on 'Filter' to apply the filters to the list of past tests. To clear filters, the user can click on "Clear All." To close the pop-up, the user can click on the cross on the top right-hand corner of the screen. The selected filter will be displayed on the screen, and clicking the cross button near the displayed filter will remove the filter.

3\. Sort:

&#x20;  Clicking on 'Sort' will open a pop-up allowing tests to be sorted by "Pending Date" with the following options:

&#x20;  \- Date (latest first).

&#x20;  \- Date (latest last).

&#x20;  After selecting the sort criteria, the user can click on 'Sort' to apply the sorting to the list of past tests. To clear the sort, the user can click on "Clear All." To close the pop-up, the user can click on the cross on the top right-hand corner of the screen.

4\. Go back to the landing page:

&#x20;  The plant operator can use the back button to return to the landing page.

5\. Help button:

&#x20;  A clickable button available on every page to provide a guided view and assistance for users.

6. The user can download the list of tests, filtered by selection in excel and pdf formats.

Test details:

\- The test summary page will consist of two cards.

First card - Test information:

The first card will display the following fields:

\- Test ID

\- Treatment process

\- Stage

\- Output type

\- Test type

\- Lab name/Device ID: This will show lab name/device ID based on the test type.

\- Test submission on

\- Test results: Indicates whether the test result is 'Pass' or 'Fail'.

Second card - Parameter details:

The second card will display the following fields:

\- Parameters, their unit of measurement, and the recorded values.

\- The values will be shown in green or red basis whether they are as per benchmarks or not.

#### User Actions:

\- The plant operator can view past test results by accessing the "Past Tests" section.

\- The plant operator can filter and sort the list of past tests based on treatment process, output type, test type, and date range.

\- The plant operator can view detailed test results by clicking on the "View Results" button for each test.

\- The plant operator can navigate back to the landing page or the list of past tests as needed.

\- The help button is available and functional on the test summary page.

#### Functional Specifications for Tests:

| Attribute              | Type     | Required?   | Comments                                                                                                                                   |
| ---------------------- | -------- | ----------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Test ID                | Numeric  | Y           | Auto-generated by the system.                                                                                                              |
| Plant Name             | Array    | View Only   | Auto-populated on the creation of the schedule, single select for on-demand test.                                                          |
| Treatment Process      | Array    | View Only   | Auto-populated on the creation of the schedule, single select for on-demand test.                                                          |
| Treatment Process Type | Array    | View Only   | Auto-populated on the creation of the schedule, single select for on-demand test.                                                          |
| Stage                  | Array    | View Only   | Auto-populated on the creation of the schedule, single select for on-demand test.                                                          |
| Output Type            | Array    | View Only   | Auto-populated on the creation of the schedule, single select for on-demand test.                                                          |
| Test Type              | Array    | <p><br></p> | Lab/IoT, auto-selected to the lab for on-demand.                                                                                           |
| Lab Submitted to       | Text     | Y           | This will not be required in case test type = IoT.                                                                                         |
| Quality Parameter 1    | Numeric  | Y           | Validation to be applied at impel.                                                                                                         |
| Quality Parameter 2    | Numeric  | Y           | Validation to be applied at impel.                                                                                                         |
| Quality Parameter 3    | Numeric  | Y           | Validation to be applied at impel.                                                                                                         |
| Quality Parameter n    | Numeric  | Y           | Validation to be applied at impel.                                                                                                         |
| Collection Time        | Date     | Y           | This is the date-time on which user updates status to pending Results. For IoT, this is the time sensor records reading.                   |
| Attachment             | Document | Y           | For a given collection location, the photo or PDF proof of the laboratory result mentioning the information of above-mentioned parameters. |

#### Validations:

NA

#### Configurations:

N/A

#### Notifications:

N/A

#### User Interface:

![](https://lh3.googleusercontent.com/eI3ShZJfB7-PihRs5MXOuuJ6aQ4GXHmNpWjr1VI6ABxJhMY1VTFV\_luL5vBbiIu\_-bA7mbDzaGo5Z0qomfmpjoduYVl-Mhvm4AUYLeZulC66eeeevC4ljLec4g2fVDsiKzbZEqUvkuS3S8CDHCxibhc)![](https://lh4.googleusercontent.com/AwdjwjFl3JBSk6bV7agMpGb07SKvz0HrZypwzBUlbOLAkK1Eprt06VhwhAIfUk5VoISUYRSjEO78p90RuisB\_MGtZi4sezPWcXEhkrZ0NsoAWdWsbP-UDIdBf0zd-QQx18PabAVeaT1piBrmoeNZpT0)![](https://lh3.googleusercontent.com/vZ9lIAqkbyZCkaWU9tBpgi8Ut2oxvvRFOwl002S3y4A\_gTFxHwZZoV9KVgPR79ddjzgQtJtENOuZA\_xpIxWCxIR014o7kjTn15GPO4Y4Txqmoo8QTGIo9F5VX2ZEOG2w1XiwzqEeuSchWXjD3oZh5GI)

\


![](https://lh6.googleusercontent.com/e6o398LvnZWA9eL4cx\_GPbpJS4t3gZE5RXNo-ZFyrxE2WMtbB2KJw1T8ih7jsQSN3N0-aHV9MCACBzrCtEroS5gHsZfRFx79S-1lIxxsBqSQTDEwmcca5mvRLoLU-s0\_qShity70-cWGuc2LvC3djpc)![](https://lh4.googleusercontent.com/yy9FFbEeY4QxdcAr1hgeF0tRrH76ayE8Tn-t\_GffrbcVJAtgoWsdI4wMsmYelVjBp5ll-bAGE2lRsopWBskm3dVe6\_23fROHF-4MAiY1hmTEyZbWd59\_XPjH\_u6Y8ssBg68eG13B2kurodyVHoa954A)![](https://lh5.googleusercontent.com/W2l2J0NWYIoFYKl7q7IGD1Es4pgcw\_BytMWlthj3xaMOjr82gcB2J8qaWFKtOGVxP08wWSxrpzlLZmTA1fd3D1ZwEBgDHJI5LbK1oD1zCknaVCZmyIpKPkSFFgL4Et8oejl8bA-cR07pjWywLb8lXts)

#### Acceptance Criteria:

\- The plant operator should be able to view past test results by clicking on "Past Tests" from the TQM landing page.

\- The list of past tests should display the relevant fields as described in the user story.

\- The plant operator should be able to filter and sort the list of past tests based on treatment process, output type, test type, and date range.

\- Clicking on the "View Results" button for each test should redirect the plant operator to the test summary page.

\- The test summary page should display accurate information, including test ID, treatment process, stage, output type, test type, lab name/device ID, test submission on, test results.

\- User can download the list past tests (filtered) by clicking on the download button.

## User Story 11: View IoT Results

#### Scope:

As a plant operator, I want to view IoT readings from the Treatment Quality Monitoring (TQM) landing page by clicking on "View IoT Readings." I should be able to access the view tests page and filter the results to view only IoT readings.

#### Actors:

\- Plant operator

#### Functionality of the Page:

\- The functionality of the view tests page for IoT readings remains the same as the view past tests page.

#### Attributes Table:

N/A

#### Validations:

NA

#### Configurations:

N/A

#### Details:

View IoT readings:

\- IoT readings can be accessed via the TQM landing page by clicking on "View IoT Readings."

\- Clicking on "View IoT Readings" will redirect the user to the view tests page, with the filter pre-set to show only IoT readings.

#### Notifications:

N/A

#### User Interface:

![](https://lh3.googleusercontent.com/eI3ShZJfB7-PihRs5MXOuuJ6aQ4GXHmNpWjr1VI6ABxJhMY1VTFV\_luL5vBbiIu\_-bA7mbDzaGo5Z0qomfmpjoduYVl-Mhvm4AUYLeZulC66eeeevC4ljLec4g2fVDsiKzbZEqUvkuS3S8CDHCxibhc)![](https://lh4.googleusercontent.com/AwdjwjFl3JBSk6bV7agMpGb07SKvz0HrZypwzBUlbOLAkK1Eprt06VhwhAIfUk5VoISUYRSjEO78p90RuisB\_MGtZi4sezPWcXEhkrZ0NsoAWdWsbP-UDIdBf0zd-QQx18PabAVeaT1piBrmoeNZpT0)

#### Acceptance Criteria:

\- The plant operator should be able to view IoT readings by clicking on "View IoT Readings" from the TQM landing page.

\- The view tests page should display a list of IoT readings with the relevant fields as described in the user story.

\- The plant operator should be able to filter and sort the list of IoT readings based on treatment process, output type, and date range.

\- Clicking on the "View Results" button for each IoT reading should redirect the plant operator to the test summary page.

\- The test summary page for IoT readings should display accurate information, including test ID, treatment process, stage, output type, test type, lab name/device ID, test submission on, test results.

\- The plant operator should be able to navigate back to the landing page or the list of IoT readings as needed.

\- The help button should be available and functional on the view tests page for IoT readings.

## User Story 12: Sensor Monitoring

#### Scope:

As a plant operator, I want to access sensor monitoring from the Treatment Quality Monitoring (TQM) landing page. I should be able to view a list of IoT devices and their details. Additionally, I should be able to filter the devices based on various criteria and perform a search based on the device ID.

#### Actors:

\- Plant operator

#### Details:

Sensor monitoring:

\- Sensor monitoring can be accessed by clicking on the "Sensor Monitoring" link on the TQM landing page.

\- Clicking on "Sensor Monitoring" will display the list of IoT devices.

#### Details on the Page:

\- The page will display the total number of IoT devices beside the page heading in brackets.

\- For each device, a card will be available, displaying the following details:

&#x20; \- Device ID.

&#x20; \- Treatment process (if there is only one treatment process configured for the plant, this field will not be displayed).

&#x20; \- Stage: Indicates the process stage where the device is used.

&#x20; \- Output type: Specifies whether the device monitors biosolids or effluents.

&#x20; \- Last calibrated date: The date when the device was last calibrated.

&#x20; \- Device Status: Indicates whether the device is 'Active' or 'Inactive'.

&#x20; \- Verification status: Indicates the verification status of the device.

&#x20; \- Last verification date: The date of the last verification.

&#x20; \- Parameters: The parameters that the device monitors.

#### User Actions:

\- Filter devices:

&#x20; Clicking on 'Filter' will open a pop-up with the following filter options:

&#x20; \- Treatment process (if there is only one treatment process configured for the plant, this field will not be displayed): A dropdown with values for treatment processes configured for the plant. The selected treatment process will be displayed upon selection.

&#x20; \- Output type: A dropdown with values for the output types configured for the plant. The selected output type will be displayed upon selection.

&#x20; \- Device status: A radio button showing options 'Active' and 'Inactive' to filter devices based on their status.

&#x20; \- Parameters: Multi-select displaying all parameters configured on the backend. The plant operator can select multiple parameters to filter devices.

&#x20;After selecting filter values, the user can click on 'Filter' to apply the filters to the list of IoT devices. To clear filters, the user can click on "Clear All." To close the pop-up, the user can click on the cross on the top right-hand corner of the screen. The selected filter will be displayed on the screen, and clicking the cross button near the displayed filter will remove the filter.

\- Search:

&#x20; Clicking on 'Search' will open a pop-up for the user to search for a device by the device ID. The search should support partial search (part search) to allow the plant operator to find devices quickly based on the device ID.

\- Go back to the landing page:

&#x20;  The plant operator can use the back button to return to the landing page.

\- Help button:

&#x20;  A clickable button available on every page to provide a guided view and assistance for users.

#### Device Attributes:

| Attribute            | Type     | Required?   | Comments                                                                                                                |
| -------------------- | -------- | ----------- | ----------------------------------------------------------------------------------------------------------------------- |
| Configuration Date   | Datetime | Y           | <p><br></p>                                                                                                             |
| Device Type          | Text     | Y           | <p>Selection from the device master data.</p><p></p><p>[“GPS Sensor”, “pH Sensor”, “Accelerometer”, “Light Sensor”]</p> |
| Plant                | Text     | Y           | <p><br></p>                                                                                                             |
| Treatment Process    | Text     | Y           | <p><br></p>                                                                                                             |
| Stage                | Text     | Y           | <p><br></p>                                                                                                             |
| Output Type          | Text     | Y           | <p><br></p>                                                                                                             |
| Parameters           | Array    | Y           | The parameters monitored by the device.                                                                                 |
| Monitoring Frequency | Numeric  | Y           | Custom frequency for the device.                                                                                        |
| Calibration Date     | Datetime | Y           | Input from the user about any change in the calibration or maintenance of the device.                                   |
| Calibration Accuracy | Array    | Y           | Range to indicate the permissible deviation in the accuracy.                                                            |
| IsConnected?         | Boolean  | Y           | To indicate the connectivity of the device.                                                                             |
| Connectivity History | ?        | Y           | Date-wise device audit log to know the connectivity status.                                                             |
| Verification History | ?        | <p><br></p> | Date-wise device verification log to know the days when device input was verified with the laboratory results.          |

#### Validations:

NA

#### Configurations:

N/A

#### Notifications:

N/A

#### User Interface:

![](https://lh6.googleusercontent.com/YhzgdvMNFLsj1GcR5lqwmye2c0QStHV3wD3h\_nuyut8j85vvmbS8WvQ3nGba3K4p7YUhfZw86NBGZbfCzvhAiPol1bKxpT8mRHj1HBxHuRjaxsXRJDxAVy\_n4-SU1xbbFkw2GJi2WamAq9rt6wAFTKE)

#### Acceptance Criteria:

\- The plant operator should be able to access sensor monitoring by clicking on the "Sensor Monitoring" link from the TQM landing page.

\- The page should display the list of IoT devices with relevant fields as described in the user story.

\- The plant operator should be able to filter devices based on treatment process, output type, device status, and parameters.

\- The plant operator should be able to perform a search based on the device ID with partial search support.

\- The plant operator should be able to navigate back to the landing page or the list of IoT devices as needed.

\- The help button should be available and functional on the sensor monitoring page.

## User Story 13: View Dashboard and Overview KPIs

#### Scope:

As a plant operator, I want to access the dashboards from the Treatment Quality Monitoring (TQM) landing page. I should be able to view different dashboards specific to the treatment process types. Additionally, I should be able to filter the dashboard based on a date range and perform actions like sharing and downloading the dashboard and its charts/tables.

#### Actors:

\- Plant operator

#### Details:

Dashboards:

&#x20; \- Dashboards can be accessed by clicking on the "View Dashboards" link on the TQM landing page.

Navigation:

&#x20; \- On landing on the dashboard, the user can navigate across the treatment process types to view the dashboard specific to the selected treatment process type.

Filters:

&#x20; \- Date range: The user should be able to filter the dashboard based on a date range to view relevant data for the selected time period.

Share:

&#x20;   \- The user should be able to share the filtered dashboard over WhatsApp in the image format.

&#x20;   \- The user should be able to share filtered charts/tables over WhatsApp in the image format.

Download:

&#x20;   \- The user should be able to download the filtered dashboard in PDF and image formats.

&#x20;   \- The user should be able to download filtered charts/tables in PDF and image formats.

Metrics:

\- Overall KPIs:

&#x20;   \- The dashboard will display the following KPIs:

&#x20;     \- Total incoming sludge: The sum of the total sludge that is disposed at the plant for the selected time period.

&#x20;     \- Number of trips: The count of the total incoming vehicles at the treatment plant for the selected time period.

&#x20;     \- Overall quality: The number of tests where all parameters are as per the benchmarks compared to the total number of test results recorded.

&#x20;     \- Compliance percentage: The percentage of tests where results have been recorded.

&#x20;     \- Total alerts: The count of total alerts raised for the following types:

&#x20;       1\. Test results not as per the benchmark.

&#x20;       2\. No reading from the IoT device.

&#x20;       3\. Lab results and IoT results not matching.

Computation of the KPIs can be accessed [here](treatment-quality-monitoring-dashboard-kpis.md).

#### Attributes Table:

&#x20; \- N/A

#### Validations:

NA

#### Configurations:

&#x20; \- N/A

#### Notifications:

&#x20; \- N/A

#### User Interface:

\<To be updated>

#### Acceptance Criteria:

&#x20; \- The plant operator should be able to access the dashboards by clicking on the "View Dashboards" link from the TQM landing page.

&#x20; \- The user should be able to navigate across the treatment process types and view specific dashboards accordingly.

&#x20; \- The user should be able to filter the dashboard based on a date range to view relevant data for the selected time period.

&#x20; \- The user should be able to share the filtered dashboard and charts/tables over WhatsApp in the image format.

&#x20; \- The user should be able to download the filtered dashboard and charts/tables in PDF and image formats.

&#x20; \- The dashboard should display the specified KPIs for the plant operator to monitor and analyse treatment quality effectively.

## User Story 14: Dashboard Card: Treatment Quality Overview

#### Scope:

As a plant operator, I want to view a dashboard card named "Treatment Quality Overview" on the dashboards page in the Treatment Quality Monitoring (TQM). The card should display the key performance indicators (KPIs) related to treatment quality, a table with relevant fields, and options to filter the data, share the dashboard, and download the data.

#### Actors:

&#x20; \- Plant operator

#### Details:

Treatment quality overview dashboard card:

\- The "Treatment Quality Overview" card will be available on the dashboards page in TQM.

\- KPIs:

&#x20; \- The card will display the following KPIs:

&#x20;   \- Total tests: The count of total tests for the filtered date range.

&#x20;   \- The count of tests that have passed treatment quality.

&#x20;   \- The count of tests that have failed treatment quality.

\- Table:

&#x20; \- Heading: Name of the plant

&#x20; \- The table will display the following fields:

&#x20;   \- Stage

&#x20;   \- Output type

&#x20;   \- Value of Parameters

&#x20;   \- Compliance percentage

Detailed metric calculations for the Treatment Quality Monitoring dashboard are viewable [here](treatment-quality-monitoring-dashboard-kpis.md).

\- Filter:

&#x20; \- The user should be able to filter the data displayed in the card based on a date range. This will allow the plant operator to view data for a specific time period.

\- Share:

&#x20; \- The user should be able to share the dashboard card "Treatment Quality Overview" with others over WhatsApp in the image format. This will enable easy sharing of the treatment quality data with relevant stakeholders.

\- Download:

&#x20; \- The user should be able to download the data displayed in the "Treatment Quality Overview" card. This should include the KPIs and table data. The download options should include PDF and image formats. This will allow the plant operator to keep a record of the treatment quality data for further analysis and reporting.

\- View trends:

&#x20; \- For each stage in the table, a button will be available to "View Trends". Clicking on this button will redirect the user to view trends specific to the selected stage. This will help the plant operator analyse the historical performance of the treatment quality for a particular stage.

\- Toggle IoT readings and lab results:

&#x20; \- The user should be able to toggle between viewing the IoT readings and the lab results in the "Treatment Quality Overview" card. This toggle will allow the plant operator to switch between different data sources and gain insights into the treatment quality from different perspectives.

#### Attributes Table:

&#x20; \- N/A

#### Validations:

NA

#### Configurations:

&#x20; \- N/A

#### Notifications:

&#x20; \- N/A

#### User Interface Design:

\<To be updated>

#### Acceptance Criteria:

&#x20; \- The plant operator should be able to view the "Treatment Quality Overview" card on the dashboards page in TQM.

&#x20; \- The card should display the specified KPIs for the filtered date range.

&#x20; \- The table should show relevant fields, including stage, output type, value of parameters, and compliance percentage.

&#x20; \- The plant operator should be able to filter the data based on a date range to view data for a specific time period.

&#x20; \- The plant operator should be able to share the "Treatment Quality Overview" card with others over WhatsApp in the image format.

&#x20; \- The plant operator should be able to download the data from the "Treatment Quality Overview" card in PDF and image formats.

&#x20; \- The plant operator should be able to view trends for specific stages by clicking on the "View Trends" button in the table.

&#x20; \- The plant operator should be able to toggle between viewing the IoT readings and the lab results in the "Treatment Quality Overview" card.

## User Story 15: Dashboard Card: Parameter Trends

#### Scope:

As a plant operator, I want to view the trends of parameter readings over time for a stagein the treatment quality overview table. The chart should provide a comparison with the benchmark and a toggle to navigate between different parameters.

#### Actors:

&#x20; \- Plant operator

#### Details:

&#x20; Trends of parameter readings:

\- The chart will be available once the plant operator clicks on the "View Trend" button in the treatment quality overview table.

\- Chart features:

\- Parameter trend over time:

&#x20;   \- The chart will display the trend of one selected parameter over time.

&#x20;   \- The x-axis of the chart will represent time, showing the data points over a specific time period.

&#x20;   \- The y-axis will represent the parameter values recorded during that time period.

\- Benchmark comparison:

&#x20;   \- The chart will include a benchmark line to provide a comparison with the benchmark value for the selected parameter.

&#x20;   \- The benchmark line will be displayed on the chart, helping the plant operator visualise how the parameter readings compare to the expected standard.

\- Toggle for parameters:

&#x20; \- A toggle will be available to navigate between different parameters for which the trends are available.

&#x20; \- The plant operator can select a different parameter from the toggle to view the trend of that particular parameter.

#### Attributes Table:

&#x20; \- N/A

#### Validations:

NA

#### Configurations:

&#x20; \- N/A

#### Notifications:

&#x20; \- N/A

#### User Interface Design:

\<To be updated>

#### Acceptance Criteria:

&#x20; \- The plant operator should be able to view the trends of parameter readings after clicking on the "View Trend" button in the treatment quality overview table.

&#x20; \- The chart should accurately display the trend of the selected parameter over time.

&#x20; \- The benchmark line should be visible and appropriately represent the expected standard for the selected parameter.

&#x20; \- The plant operator should be able to toggle between different parameters to view their trends.

## User Story 16: Landing Page: ULB Employee

#### Scope:

As a ULB employee, I want to have a card for Treatment Quality Monitoring (TQM) on the landing page. The card should provide an overview of pending tests and tests nearing SLA, allow me to view upcoming tests using the inbox, access past test results, IoT readings, and sensor monitoring. Additionally, I should be able to view the treatment quality dashboard, and receive alerts related to TQM, which I can view in detail or dismiss.

#### Actors:

ULB employee

#### Details:

&#x20; Landing page: ULB employee

\- Treatment Quality Monitoring card:

&#x20; \- The landing page will include a card for Treatment Quality Monitoring.

\- Overview:

&#x20; \- The card will provide an overview of the total pending tests and the count of tests nearing SLA.

\- View the upcoming tests using the inbox:

&#x20; \- The card will display the count of the upcoming tests beside in brackets.

&#x20; \- The ULB employee can click on the inbox to view the upcoming tests.

\- View the past test results:

&#x20; \- The ULB employee can click on a link to view the past results from both lab and IoT devices.

\- View IoT readings:

&#x20; \- The ULB employee can click on a link to access the record of IoT readings.

\- Sensor monitoring:

&#x20; \- The ULB employee can click on a link to access a list of IoT devices along with their status.

\- View dashboard:

&#x20; \- The ULB employee can click on a link to be directed to the treatment quality dashboard.

\- Alerts:

&#x20; \- The card will display a list of alerts regarding Treatment Quality Monitoring.

&#x20; \- Specifically, it will display tests that have crossed SLA for greater than 7 days.

&#x20; \- The ULB employee can view the details of each test by clicking on the "View Details" button.

&#x20; \- The ULB employee can dismiss notifications by clicking on the cross button.

\- Other functionality:

&#x20; \- The rest of the functionality on the landing page will remain the same as the current ULB employee landing page.

#### Attributes Table:

&#x20; \- N/A

#### Validations:

NA

#### Configurations:

&#x20; \- N/A

#### Notifications:

&#x20; \- N/A

#### User Interface Design:

![](https://lh4.googleusercontent.com/4B6rTI5HX0j6HnArLCI8JkEGObIBJqtzVNAr1jlLOISU1y5Vju8xXDl3Kn8k66dsAVr6PpVtfr4DYiK384-pA8Bbbit7n3Q3O0pTe4CqOT1nP9kkRhwlr04EuHy0pyDS9Op-ZOAGmUIo2mweXa\_\_JU0)

#### Acceptance Criteria:

&#x20; \- The ULB employee should be able to view the Treatment Quality Monitoring card on the landing page.

&#x20; \- The card should display an overview of the total pending tests and tests nearing SLA.

&#x20; \- The ULB employee should be able to click on the inbox to view the upcoming tests.

&#x20; \- The ULB employee should be able to click on links to view past test results, IoT readings, sensor monitoring, and the treatment quality dashboard.

&#x20; \- The card should display alerts related to TQM and allow the ULB employee to view the details or dismiss them.

&#x20; \- The rest of the functionality on the landing page should remain unaffected.

## User Story 17: View Upcoming Tests

#### Scope:

As a user, I want to view a list of the upcoming lab tests in the Treatment Quality Monitoring (TQM) module by clicking on the inbox. The list should be sorted by the pending date, displaying the test with the highest SLA first. I should be able to see the test ID, plant name, treatment process, pending date, status, and SLA. Additionally, I should be able to filter the tests, search for specific tests by test ID or plant name, and redirect to other pages in the TQM module using the provided links.

#### Actors:

ULB employee/state employee

#### Details:

&#x20; View the list of upcoming tests:

\- Inbox navigation:

&#x20; \- The user can click on the inbox to be redirected to the list of upcoming lab tests.

\- Total count of upcoming tests:

&#x20; \- The total count of upcoming tests will be displayed beside the inbox in brackets.

\- Sorting:

&#x20; \- The list of upcoming tests will be sorted by the pending date, where the test with the highest SLA is displayed first.

\- Fields displayed:

&#x20; \- The list of upcoming tests will display the following fields:

&#x20;   \- Test ID

&#x20;   \- Plant Name

&#x20;   \- Treatment Process

&#x20;   \- Pending Date: This is the test date as per schedule

&#x20;   \- Status: Status of the test

&#x20;   \- SLA: The difference between the test due date and today. This will be displayed in red if the test due date is earlier than today, and in green if today is before the test due date.

\- View test details:

&#x20; \- The user can view detailed information about a specific test by clicking on the test ID.

\- Filters:

&#x20; \- Filters are displayed on the left-hand panel of the screen.

&#x20; \- The following filters are available:

&#x20;   \- Treatment process: A multi-select showing values for the treatment processes configured for the urban local body (ULB). The selected treatment processes will be displayed as ticks on the multi-select box. If not selected, it is left blank.

&#x20;   \- Stages: A dropdown showing values for the stages configured for the plant. The selected stage is displayed here on selection. If not selected, the field is left blank.

&#x20;   \- Status: A multi-select showing values for the status in the treatment quality workflow.

&#x20; \- The user can select values for the filters and click on filter to filter the inbox accordingly.

&#x20; \- To clear the filters, the user can click on the refresh icon on the top right of the filter panel.

\- Search:

&#x20; \- The user can search for specific tests using the following:

&#x20;   \- Test ID

&#x20;   \- Plant name

&#x20; \- Part search is enabled for both fields.

&#x20; \- The user can fill in either the test ID or the plant name or both and click on the search button.

&#x20; \- The user can clear the search by clicking on the clear search link.

\- Retaining filters, sort, and search:

&#x20; \- In case filters, sort, or search are applied, and the user navigates to the test details page, on going back, the values of the filters, sort, and search should remain the same.

\- Redirecting to other Links:

&#x20; \- Users can redirect to other pages in the TQM module via the links provided on the top left of the page.

&#x20; \- The following links will be displayed:

&#x20;   \- View past results

&#x20;   \- View IoT results

&#x20;   \- Sensor monitoring

&#x20;   \- View dashboard

#### Attributes Table:

&#x20; \- N/A

#### Validations:

NA

#### Configurations:

&#x20; \- N/A

#### Notifications:

&#x20; \- N/A

#### User Interface

&#x20;![](https://lh4.googleusercontent.com/JBMyU6j0TEcxcasJvntX3B12ZSZ6OEQ77yHtrj\_WWoUsUe8m04ACVKn7t1B\_RMFV-FzyqCMziBj0dJUJ91kPZDl3mnO5JOmLpM-MpveRzWXMy\_yH0AFuUDbKnsPg5Orsl2YK1Zui2eiVTDz\_GhylW90)

#### Acceptance Criteria:

&#x20; \- The user should be able to view the list of the upcoming lab tests by clicking on the inbox.

&#x20; \- The list of upcoming tests should be sorted correctly by the pending date, showing the test with the highest SLA first.

&#x20; \- The user should be able to see the test ID, plant name, treatment process, pending date, status, and SLA in the list of upcoming tests.

&#x20; \- The user should be able to view detailed information about a specific test by clicking on the test ID.

&#x20; \- The user should be able to filter the tests based on the treatment process, stages, and status.

&#x20; \- The user should be able to search for specific tests by the test ID or the plant name.

&#x20; \- The user should be able to redirect to other pages in the TQM module using the provided links.

## ​​User Story 18: View Test Details

#### Scope:

As a user, I want to access a test details page by clicking on the test ID in the inbox. The test details page should display detailed information about the test, including test ID, plant name, treatment process, stage, output type, test type, test scheduled date, status, lab name, sample submission date, test results submission date, SLA, a table with parameter details, overall test results (pass/fail), attached documents (if any), and the test timeline. Additionally, I should be able to go back using the breadcrumbs of the page and download the test report.

#### Actors:

ULB employee/State employee

#### Details:

\- Accessing the test details page:

&#x20; \- The user can access the test details page by clicking on the test ID in the inbox.

\- Fields displayed:

&#x20; \- The following information will be displayed on the test details page:

&#x20;   \- Test ID

&#x20;   \- Plant Name

&#x20;   \- Treatment Process

&#x20;   \- Stage

&#x20;   \- Output Type

&#x20;   \- Test Type

&#x20;   \- Test Scheduled Date

&#x20;   \- Status

&#x20;   \- Lab Name

&#x20;   \- Sample Submission Date

&#x20;   \- Test Results Submission Date

&#x20;   \- SLA: This will be displayed in red/green based on SLA. If today > pending date, it will be displayed in red. If today < pending date, it will be displayed in green for open tests. For closed tests, SLA will be displayed.

In case the information on any field is not available, such as lab name/value against parameters based on the status of the test, the value against the fields will be displayed as "To be Updated".

\- Table with parameter details:

&#x20; \- The page will include a table with the following details:

&#x20;   \- S.No

&#x20;   \- Parameter

&#x20;   \- Unit of Measurement (UoM)

&#x20;   \- Benchmark

&#x20;   \- Value Recorded: The value will be displayed in red/green based on comparison to the benchmark.

&#x20;   \- Overall Test Results: Pass/Fail

\- Attached documents:

&#x20; \- The user should be able to view attached documents (if any) by clicking on the document icon. No icon will be present if the documents are not attached.

\- Test timeline:

&#x20; \- The test details page will display the test timeline, showing the various stages and dates involved in the test process.

\- Go back:

&#x20; \- The user can go back to the previous page using the breadcrumbs of the page.

\- Download test report:

&#x20; \- The user can download the test report by clicking on the download button.

#### Attributes Table:

N/A

#### Validations:

N/A

#### Configurations:

N/A

#### Notifications:

N/A

#### User Interface:

![](https://lh3.googleusercontent.com/o3jEQb5EWRYeO6rj\_HJP7VhYDzLTgplGRvoJb7TnOuwp6mfZmV-9vkGwUG83cwy22ZWxPO-3LMIfvNQ5MqW39FUFAkyFul9DKWyqFBa3e95Wovx0aTU3Np2jm4m-M6ROnoCIkWc1WXZ\_ptPSUfnug9g)

#### Acceptance Criteria:

&#x20; \- The user should be able to access the test details page by clicking on the test ID in the inbox.

&#x20; \- The test details page should display detailed information about the test, including Test ID, Plant Name, Treatment Process, Stage, Output Type, Test Type, Test Scheduled Date, Status, Lab Name, Sample Submission Date, Test Results Submission Date, and SLA.

&#x20; \- The page should include a table with parameter details, showing S.No, Parameter, UoM, Benchmark, Value Recorded, and Overall Test Results (Pass/Fail).

&#x20; \- The user should be able to view attached documents (if any) by clicking on the document icon.

&#x20; \- The test details page should display the test timeline, showing the various stages and dates involved in the test process.

&#x20; \- The user should be able to go back using the breadcrumbs of the page.

&#x20; \- The user should be able to download the test report by clicking on the download button.

## ​​User Story 19: View Past Tests

#### Scope:

As a user, I want to view past test results (both IoT and lab) via the TQM landing page by clicking on the "Past Tests" link. The Past Test Results page will display a list of past tests with the ability to view test details, search tests based on various criteria, sort the results, and download test results in Excel and PDF formats. Additionally, I should be able to go back using the breadcrumbs on the top of the page and clicking on the Test ID will redirect me to the test details page.

#### &#x20;Actors:

ULB employee/State employee

#### Details:

&#x20; Past Test Results Page:

\- Accessing Past Test Results Page:

&#x20; \- The user can access the Past Test Results page by clicking on the "Past Tests" link on the TQM landing page.

\- Fields Displayed:

&#x20; \- The page will display a list of past tests sorted on the test date, with the following fields for each test:

&#x20;   \- Test ID

&#x20;   \- Plant

&#x20;   \- Treatment Process (in case there is only 1 treatment process for the plant, this field will not be displayed)

&#x20;   \- Test Type

&#x20;   \- Test Date: This is the date the test results are updated

&#x20;   \- Test Result: Pass/Fail

\- View Test Details:

&#x20; \- The user can view test details by clicking on the "Test ID" link on each row, which will redirect the user to the test details page (same as redirection from Inbox).

\- Search Tests:

&#x20; \- The user can search for past tests based on the following criteria:

&#x20;   \- Test ID: Input Text field, Part search should be enabled.

&#x20;   \- Plant: Dropdown of a list of plants in the ULB.

&#x20;   \- Treatment Process: Dropdown of a list of treatment processes in the ULB.

&#x20;   \- Test Type: This will be a dropdown showing values for Test Type (IoT/lab). Selected test type is displayed here on selection. If not, the field is left blank.

&#x20;   \- Date range: Selection of date range (calendar view): Selected date range is displayed here on selection. If not, the field is left blank.

\- Sort:

&#x20; \- Tests can be sorted by the Test Date by clicking on the date column.

\- Clear Search:

&#x20; \- To clear the search and view all past tests, the user can click on the "Clear Search" button.

\- Download Test Results:

&#x20; \- The user can download list of test results in Excel and PDF formats using the download button.

\- Go Back:

&#x20; \- The user can go back to the previous page using the breadcrumbs on the top of the page. If the user has navigated to the Test details page from the Past Test results list, clicking back will redirect the user to the Past Test Results page.

#### Attributes Table:

&#x20;N/A

#### Validations:

N/A

#### Configurations:

&#x20;N/A

#### Notifications:

&#x20;N/A

#### User Interface:

## ![](https://lh6.googleusercontent.com/C-mlJx78WIWodyK6TUtRpFKvALerUIDVYXbtqtoYgCs9p0ZJ5CxzS0HhCpLeiLJCavSTM8vYTwXi61LYbYEsLMtiV3TJTK4UCv4-DoN8OfvUzB1ahNowW7znlALmabCvWSszhJiC3Q0o-ZgKFZPNYIA)

#### Acceptance Criteria:

&#x20; \- The user should be able to access the Past Test Results page by clicking on the "Past Tests" link on the TQM landing page.

&#x20; \- The Past Test Results page should display a list of past tests sorted on the test date, with relevant fields such as Test ID, Plant, Treatment Process, Test Type, Test Date, and Test Result (Pass/Fail).

&#x20; \- The user should be able to view test details by clicking on the "Test ID" link on each row, redirecting the user to the Test details page (same as redirection from Inbox).

&#x20; \- The user should be able to search for past tests based on Test ID, Plant, Treatment Process, Test Type, and Date range criteria.

&#x20; \- The user should be able to sort past tests by the Test Date.

&#x20; \- The user should be able to clear the search and view all past tests.

&#x20; \- The user should be able to download test results in Excel and PDF formats.

&#x20; \- The user should be able to go back using the breadcrumbs on the top of the page and clicking on the Test ID will redirect the user to the test details page.

## User Story 20: View IoT Readings

#### Scope:

As a user, I want to view IoT readings via the TQM landing page by clicking on the "View IoT Readings" link. On clicking the link, the user should be redirected to the list of past tests, with the search on Test Type selected as "IoT" and the results filtered for IoT readings only. All other functionality of the page should remain the same.

#### Actors:

ULB employee/State employee

\- Details:

&#x20; \- Accessing "View IoT Readings" Page:

&#x20;   \- The user can access the "View IoT Readings" page by clicking on the "View IoT Readings" link on the TQM Landing Page.

&#x20; \- Redirected Page:

&#x20;   \- On clicking "View IoT Readings," the user is redirected to the list of past tests, with the search on Test Type selected as "IoT," and the results filtered for IoT readings only.

&#x20; \- Other Functionality:

&#x20;   \- All other functionality available on the page (e.g., viewing past test results, searching tests, sorting, downloading test results) will remain the same.

#### Attributes Table:

N/A

#### Validations:

N/A

#### Configurations:

N/A

#### Notifications:

N/A

#### User Interface:

N/A

#### Acceptance Criteria:

&#x20; \- The user should be able to access the "View IoT Readings" page by clicking on the "View IoT Readings" link on the TQM landing page.

&#x20; \- On clicking the link, the user should be redirected to the list of past tests, with the search on Test Type selected as "IoT," and the results filtered for IoT readings only.

&#x20; \- All other functionality available on the page should remain the same, allowing the user to view past test results, search tests, sort, and download test results as before.

## User Story 21: Sensor Monitoring

#### Scope:

As a user, I want to view the list of devices via the TQM landing page by clicking on the "Sensor Monitoring" link. On clicking the link, the user should be redirected to the list of devices. The page should display the total number of IoT devices, and each device should have specific details such as Device ID, Plant, Treatment Process, Stage, Output Type, Device Status, and the parameters it is monitoring. The user should be able to search and filter devices based on various criteria.

#### Actors:

ULB employee/State employee

#### Details:

&#x20; \- Accessing "Sensor Monitoring" Page:

&#x20;   \- The user can access the "Sensor Monitoring" page by clicking on the "Sensor Monitoring" link on the TQM Landing Page.

&#x20; \- Redirected Page:

&#x20;   \- On clicking "Sensor Monitoring," the user is redirected to the list of devices.

&#x20; \- List of Devices:

&#x20;   \- The page will display the total number of IoT devices beside the page heading in brackets.

&#x20;   \- Each device will have a row displaying the following details:

&#x20;     \- Device ID

&#x20;     \- Plant

&#x20;     \- Treatment Process

&#x20;     \- Stage

&#x20;     \- Output Type

&#x20;     \- Device Status

&#x20;     \- Parameters: One or multiple parameters that the device is monitoring.

&#x20; \- Filters:

&#x20;   \- Search Devices:

&#x20;     \- On clicking "Filter," a pop-up will be displayed with the following filters:

&#x20;       \- Device ID: Allows part search for Device ID.

&#x20;       \- Plant: Dropdown with values based on plants configured in the MDMS.

&#x20;       \- Treatment Process: Dropdown with values based on the Treatment process type.

&#x20;       \- Stage: Dropdown with values based on the Stage of the selected Treatment process.

&#x20;       \- Output Type: Dropdown with values based on Output types configured for the plant.

&#x20;       \- Device Status: Dropdown with options for Active/Inactive.

&#x20;     \- The user can select values for the filters above and click on "Search" to filter the list of devices based on the selected criteria.

&#x20;     \- To clear the search and view all devices, the user can click on "Clear All."

#### Attributes Table:

| Attribute            | Type     | Required?   | Comments and Validations                                                                                               |
| -------------------- | -------- | ----------- | ---------------------------------------------------------------------------------------------------------------------- |
| Configuration Date   | Datetime | Y           | <p><br></p>                                                                                                            |
| Device Type          | Text     | Y           | <p>Selection from device master data</p><p><br></p><p>[“GPS Sensor”, “pH Sensor”, “Accelerometer”, “Light Sensor”]</p> |
| Plant                | Text     | Y           | <p><br></p>                                                                                                            |
| Treatment Process    | Text     | Y           | <p><br></p>                                                                                                            |
| Stage                | Text     | Y           | <p><br></p>                                                                                                            |
| Output Type          | Text     | Y           | <p><br></p>                                                                                                            |
| Parameters           | Array    | Y           | The parameters monitored by the device                                                                                 |
| Monitoring Frequency | Numeric  | Y           | Custom frequency for the device                                                                                        |
| Calibration Date     | Datetime | Y           | Input from the user about any change in the calibration/maintenance of the device                                      |
| Calibration Accuracy | Array    | Y           | Range to indicate the permissible deviation in the accuracy                                                            |
| IsConnected?         | Boolean  | Y           | To indicate the connectivity of the device                                                                             |
| Connectivity History | ?        | Y           | Date-wise device audit log to know the connectivity status                                                             |
| Verification History | ?        | <p><br></p> | Date-wise device verification log to know the days when device input was verified with laboratory results              |

#### Configurations:

N/A

#### Notifications:

N/A

#### User Interface:

![](https://lh3.googleusercontent.com/mo3gSfAV4g5jPothAHDI2gEwZIBwte3lx6uCM0zkxotUST36PjxRlBf\_t9yaK0-Q9y7zDq9x50k8kiuGR8L5xusYaDtOMa2VAv55fztyJfbZcBji23ZxXvxBYZrTF0GFXsxu9kL9UO-ZK2c6UEMIUPs)

#### Acceptance Criteria:

&#x20; \- The user should be able to access the "Sensor Monitoring" page by clicking on the "Sensor Monitoring" link on the TQM landing page.

&#x20; \- On clicking the link, the user should be redirected to the list of devices, displaying the total number of IoT devices and specific details for each device, such as Device ID, Plant, Treatment Process, Stage, Output Type, Device Status, and the parameters it is monitoring.

&#x20; \- The user should be able to search and filter devices based on various criteria using the available filters.

&#x20; \- The user can perform the search and view the filtered devices based on the selected criteria.

&#x20; \- The user can clear the search and view all devices if needed.

## User Story 22: Record Test Results

#### Scope:

As a user, I want to be able to record test results without a schedule for adhoc tests. A provision will be provided for the user to record test results by clicking on the "Add Test Result" link on the card. Clicking on the link should redirect the user to the "Add Test Result" page where the user can enter the required fields, including Plant Name, Treatment Process, Treatment Stage, Output Type, values against parameters, and any attachments. After submitting the test results, the user should be redirected to the test results page with specific changes to the display compared to the View Test Results page.

#### Actors:

&#x20; ULB employee/State employee

#### Details:

&#x20; \- Accessing "Add Test Result" Page:

&#x20;   \- The user can access the "Add Test Result" page by clicking on the "Add Test Result" link on the Card.

&#x20; \- Redirected Page:

&#x20;   \- Clicking on "Add Test Result" will redirect the user to the "Add Test Result" page.

&#x20; \- Fields to Enter:

&#x20;   \- The user needs to enter the following fields:

&#x20;     \- Plant Name: A dropdown based on the list of Plants available in the system. For a state-level user, this should display all plants in the state. For a ULB, it should also display the names tagged to the ULB.

&#x20;     \- Treatment Process: A dropdown based on the list of Treatment Processes in the selected plant.

&#x20;     \- Treatment Stage: A dropdown based on the list of Stages in the selected Treatment Process.

&#x20;     \- Output Type: A dropdown based on the Output types available in the selected stage.

&#x20;     \- Values against parameters: The user should fill in at least 1 parameter for the Submit button to be enabled. If no parameter is filled, and the user clicks on the Submit button, an error message is displayed as a snack bar.

&#x20;     \- Attachments: If any attachments are required, the user can add them.

&#x20; \- Submitting Test Results:

&#x20;   \- Once the user clicks on the Submit button, the test results page is displayed.

&#x20; \- Changes to "View Test Results" Page:

&#x20;   \- The "View Test Results" page with the following changes:

&#x20;     \- Test Type will be displayed as "Lab."

&#x20;     \- Status, Lab Name, and SLA fields are not displayed.

&#x20;     \- Workflow will not be displayed.

#### Test Attributes:&#x20;

| Attribute              | Type     | Required?   | Comments/Validations                                                                                                              |
| ---------------------- | -------- | ----------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Test ID                | Numeric  | Y           | Autogenerated by system                                                                                                           |
| Plant Name             | Array    | View Only   | Auto populated on creation of schedule, Single select for on demand test                                                          |
| Treatment Process      | Array    | View Only   | Auto populated on creation of schedule, Single select for on demand test                                                          |
| Treatment Process Type | Array    | View Only   | Auto populated on creation of schedule, Single select for on demand test                                                          |
| Stage                  | Array    | View Only   | Auto populated on creation of schedule, Single select for on demand test                                                          |
| Output Type            | Array    | View Only   | Auto populated on creation of schedule, Single select for on demand test                                                          |
| Test Type              | Array    | <p><br></p> | Lab/IoT, Autoselected to Lab for on demand                                                                                        |
| Lab Submitted to       | Text     | Y           | This will not be required in case Test Type = IoT                                                                                 |
| Quality Parameter 1    | Numeric  | Y           | Validation to be applied at impel                                                                                                 |
| Quality Parameter 2    | Numeric  | Y           | Validation to be applied at impel                                                                                                 |
| Quality Parameter 3    | Numeric  | Y           | Validation to be applied at impel                                                                                                 |
| Quality Parameter n    | Numeric  | Y           | Validation to be applied at impel                                                                                                 |
| Collection Time        | Date     | Y           | This is the date-time on which user updates status to Pending Results. For IoT, this is the time sensor records reading           |
| Attachment             | Document | Y           | For a given collection location, photo or PDF proof of laboratory result mentioning the information of above-mentioned parameters |

#### Validations:

\<To be updated>\


#### Configurations:

N/A

#### Notifications:

N/A

#### User Interface:

![](https://lh6.googleusercontent.com/DJUGEkWI3eIMwhYZJEm7fBgvunWUUjM-SVt0hOXTxCMI0R6FGq14xRZBwyky4At2ZPPBf9oa4JIY1yRWhv3Yvt-gEkMd7OkYflIEKWIWdxvxgCwcHLFUutaDeMBAWrCIk0fiFuEUa5TvJTLhesQiZKU)

![](https://lh4.googleusercontent.com/F16Z4ofu-ewIJL3Nhyse0fo4nrZKTtwE\_rwCqhI5uJ7\_WDuEzKqn1C3p6oCyNc6HVIfbLB26N\_9hBlx-cztXOnOV1XXswlDiq9HtpdI4hSeSy9axeqAIl0sBdtbLdfMNWZjoO6-LJiz23dGtTMFdoRI)

![](https://lh4.googleusercontent.com/AP11t2QFqk1gcM1Y4fo\_nEjQT7jNzhdW-XaiQ5PVp2dTp15hKL\_qsH0SKOWLVhrhg5th3YVsuyIvA-ztQ5OkyjGrZ1tFbRmjAxkf5J4n-7\_qpk\_HY56DXuYSuSUk74EsQsumoQS-VopFCydn8tniSsE)

#### Acceptance Criteria:

&#x20; \- The user should be able to access the "Add Test Result" page by clicking on the "Add Test Result" link on the card.

&#x20; \- The "Add Test Result" page should allow the user to enter required fields, including Plant Name, Treatment Process, Treatment Stage, Output Type, values against parameters, and any attachments.

&#x20; \- After submitting the test results, the user should be redirected to the test results page with specific changes to the display compared to the "View Test Results" page.

## User Story 23: View Dashboard and Overview KPIs

#### Scope:

The TQM Dashboard will be available to both ULB employees and state employees. It can be accessed by clicking on the 'Dashboard' link on the landing page. Upon clicking, the user will be directed to the dashboard view. The access to data in the dashboard will be based on the roles, where the ULB admin can view the dashboard for all plants in the ULB, and the state admin can view the dashboard for all plants in the state.

#### Actors:

&#x20; \- ULB Employee

&#x20; \- State Employee

#### Details:

&#x20; \- Accessing "Dashboard" View:

&#x20;   \- The user can access the Dashboard by clicking on the "Dashboard" link on the landing page.

&#x20; \- Redirected to Dashboard:

&#x20;   \- Clicking on "Dashboard" will direct the user to the Dashboard view.

&#x20; \- Navigation:

&#x20;   \- On the Dashboard view, the user can navigate across Treatment Process Types to view specific dashboards for each Treatment Process Type.

&#x20; \- Filters:

&#x20;   \- Date Range: The user should be able to filter the dashboard based on the selected date range.

&#x20;   \- ULB: For ULB Employees, the ULB is automatically selected to the ULB the Plant and Employee is tagged to. For State users, all ULBs should be available in the dropdown.

&#x20;   \- Plant: For ULB Employees, plants tagged to the ULB to which the employee belongs should be available in the dropdown. For State users, all plants should be available.

&#x20; \- Share Functionality:

&#x20;   \- User should be able to share the filtered dashboard over WhatsApp in image format.

&#x20;   \- User should be able to share filtered charts/tables over WhatsApp in image format.

&#x20; \- Download Functionality:

&#x20;   \- User should be able to download the filtered dashboard in PDF and image format.

&#x20;   \- User should be able to download filtered charts/tables in PDF and image format.

&#x20; \- Metrics - Overall KPIs:

&#x20;   \- The Dashboard will display the following KPIs:

&#x20;     \- Total Incoming Sludge: Sum of the total sludge that is disposed of at the plant for the selected time period.

&#x20;     \- # of trips: Count of total incoming vehicles at the Treatment Plant for the selected time period.

&#x20;     \- Overall Quality: Number of tests where all parameters are as per benchmarks compared to the total number of test results recorded.

&#x20;     \- Compliance %: % of tests where results have been recorded.

&#x20;     \- Total Alerts: Count of total alerts raised of the following types:

&#x20;       1\) Test Results not as per benchmark.

&#x20;       2\) No reading from IoT device.

&#x20;       3\) Lab results and IoT results not matching.

Detailed Metric calculations for the Treatment Quality Monitoring Dashboard are viewable [here](treatment-quality-monitoring-dashboard-kpis.md).

#### Attributes Table:

N/A

#### Validations:

The user should have appropriate access rights to view the dashboard.

#### Configurations:

&#x20;N/A

#### Notifications:

&#x20;N/A

#### User Interface:

![](https://lh6.googleusercontent.com/-FQ1Y96MfObdOIdZ4KNJbAuO74pL-bpfWlBEYy89WMSMOuMIy3OdxgiWwfiRUmYrL1GRX0LA1PyQwaQv6tfo6k-0jowmZA4bNARW\_asuGdM5E164oABgSV6VQoe1pkn-MqTFlchbu623yyS7vbHJJX8)![](https://lh6.googleusercontent.com/-FQ1Y96MfObdOIdZ4KNJbAuO74pL-bpfWlBEYy89WMSMOuMIy3OdxgiWwfiRUmYrL1GRX0LA1PyQwaQv6tfo6k-0jowmZA4bNARW\_asuGdM5E164oABgSV6VQoe1pkn-MqTFlchbu623yyS7vbHJJX8)

#### Acceptance Criteria:

&#x20; \- The user should be able to access the dashboard by clicking on the 'Dashboard' link on the landing page.

&#x20; \- The Dashboard view should allow the user to navigate across Treatment Process Types to view specific dashboards for each Treatment Process Type.

&#x20; \- The user should be able to filter the dashboard based on the selected date range, ULB, and plant.

&#x20; \- The user should be able to share the filtered dashboard and charts/tables over WhatsApp in the image format.

&#x20; \- The user should be able to download the filtered dashboard and charts/tables in PDF and image formats.

&#x20; \- The Dashboard should display the overall KPIs, including Total Incoming Sludge, the number of trips, Overall Quality, Compliance percentage, and Total Alerts.

## User Story 24: Dashboard Card: Treatment Quality Monitoring

#### Scope:

The Treatment Quality Overview provides an overview of the Treatment Quality for a particular Treatment Process. It includes KPIs, a map view, and a table of plant-wise details of test results (Pass/Fail) and compliance percentage.

#### Actors:

ULB Employee/State Employee

#### Details:

&#x20; \- KPIs:

&#x20;   \- Total Plants: The count of unique plants for the particular Treatment Process.

&#x20;   \- Count of Plants Passed Treatment Quality: The count of plants that have passed Treatment Quality as per the last recorded test. Treatment Quality is said to have passed if all parameters for final output(s) of a Treatment process are as per benchmarks.

&#x20;   \- Count of Plants Failed Treatment Quality: The count of plants that have failed Treatment Quality as per the last recorded test. Treatment Quality is said to have failed if one or more parameters for final output(s) of a Treatment process are not as per benchmarks.

&#x20; \- Map View:

&#x20;   \- The dashboard will display a map view showing the location of each plant. Plants will be colour-coded based on whether they have passed or failed the last output quality test Treatment Quality. (Red = Failed, Green = Passed)

&#x20; \- Table:

&#x20;   \- The table will show plant-wise details of Test Results (Pass/Fail) and Compliance Percentage based on the last recorded test. The user will also be able to see the change in compliance percentage compared to the last month.

&#x20;   \- Drill down functionality will be available for a plant via this table.

&#x20;   \- For Treatment Plant Users (TRP) and ULBs where only one plant is tagged for the process type, the drilled table is automatically visible.

&#x20; \- Drill Down:

&#x20;   \- When a user drills down on a specific plant from the table, the following information will be viewable:

&#x20;     \- Heading: Name of the Plant

&#x20;     \- Table displaying the following fields:

&#x20;       \- Stage

&#x20;       \- Output Type

&#x20;       \- Value of Parameters

&#x20;       \- Compliance Percentage

&#x20;     \- Button to view Trends for a particular Stage.

&#x20;     \- Toggle to Toggle between IoT readings and Lab Results. The selected test type will appear highlighted.

&#x20; \- Switching between Process Flows:

&#x20;   \- If there are multiple process flows, the user can switch between them using buttons. The selected process flow will appear highlighted.

Detailed Metric calculations for the Treatment Quality Monitoring Dashboard are viewable [here](treatment-quality-monitoring-dashboard-kpis.md).

&#x20;\- Filters:

&#x20;   \- Date Range: The user should be able to filter the dashboard based on the selected date range.

&#x20;   \- ULB: For ULB Employees, the ULB is automatically selected to the ULB the Plant and Employee is tagged to. For State users, all ULBs should be available in the dropdown.

&#x20;   \- Plant: For ULB Employees, plants tagged to the ULB to which the employee belongs should be available in the dropdown. For State users, all plants should be available.

&#x20; \- Share Functionality:

&#x20;       \- User should be able to share filtered charts/tables over WhatsApp in image format.

&#x20; \- Download Functionality:

&#x20;   \- User should be able to download filtered charts/tables in PDF and image format.

#### Attributes Table:

N/A

#### Validations:

The user should have appropriate access rights to view the Treatment Quality Overview dashboard.

#### Configurations:

N/A

#### Notifications:

N/A

#### User Interface:

![](https://lh6.googleusercontent.com/muNjg6gCy23Yv\_m2vjSAtlzr\_DAVLFKNbp2vDq9RFHJ7XHfpBULt8amEHLWGKrecSAoSP7Np2cw0sgm1MqztePCMl6df8TgrPJ2qmWjMTF8PVawgYIwnTlT8fjlPAvcP8lwD-IYCJOmCuP4eJMB\_if8)

![](https://lh6.googleusercontent.com/yYymTLD1uBVrnVGFkAlDQvhs3CIpNBRFhz49-q944R2wlBv7X1Lb3BNgo1D1SlTqmLZ\_13vGB3OGRtQLfSAm9RvKxfo5Kpb49U87er7K5WVvyh52NxjlT902wPiJwDI0RduVmU9VmoCZ9XUHcFDLgec)

#### Acceptance Criteria:

&#x20; \- The Treatment Quality Overview dashboard should display the KPIs: Total Plants, Count of Plants Passed Treatment Quality, and Count of Plants Failed Treatment Quality.

&#x20; \- The map view should show the location of each plant, color-coded based on whether they have passed or failed Treatment Quality.

&#x20; \- The table should show plant-wise details of Test Results (Pass/Fail) and Compliance Percentage based on the last recorded test. The user should be able to see the change in compliance percentage compared to the last month.

&#x20; \- The drill down functionality should provide detailed information about a specific plant's Stage, Output Type, Value of Parameters, and Compliance Percentage.

&#x20; \- The user should be able to toggle between IoT readings and Lab Results for a specific plant.

&#x20; \- If there are multiple process flows, the user should be able to switch between them using buttons.

## User Story 25: Dashboard Card: Trend of Parameter Reading

Scope:

The user will be able to view a trend chart for a specific parameter over time once they click on the "View Trend" button in the table. The chart will provide a comparison with the benchmark.

Actors:

&#x20; \- ULB Employee/State Employee

\- Details:

&#x20; \- When the user clicks on the "View Trend" button in the table, a trend chart will be displayed.

\- The chart should not be visible before Trend chart has been clicked on

&#x20; \- The chart will show the trend of the selected parameter over time.

&#x20; \- The chart will also display the benchmark for the selected parameter to provide a comparison.

&#x20; \- A toggle will be available to navigate between different parameters for viewing their trend charts.

Attributes Table:

&#x20; \- N/A

Validations:

&#x20; \- The user should have appropriate access rights to view trend charts.

Configurations:

&#x20; \- N/A

Notifications:

&#x20; \- N/A

User Interface:

![](https://lh6.googleusercontent.com/-FQ1Y96MfObdOIdZ4KNJbAuO74pL-bpfWlBEYy89WMSMOuMIy3OdxgiWwfiRUmYrL1GRX0LA1PyQwaQv6tfo6k-0jowmZA4bNARW\_asuGdM5E164oABgSV6VQoe1pkn-MqTFlchbu623yyS7vbHJJX8)

Acceptance Criteria:

&#x20; \- The user should be able to view a trend chart for a specific parameter by clicking on the "View Trend" button in the table.

&#x20; \- The chart should show the trend of the selected parameter over time.

&#x20; \- The chart should display the benchmark for the selected parameter to provide a comparison.

&#x20; \- The user should be able to navigate between different parameters using the toggle to view their trend charts.
