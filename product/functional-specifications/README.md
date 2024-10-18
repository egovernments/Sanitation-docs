# Functional Specifications

## Treatment Quality Monitoring: Functional Specifications



1. ### Treatment Process

<table data-header-hidden><thead><tr><th width="150"></th><th></th><th width="117"></th><th></th><th></th></tr></thead><tbody><tr><td>Attribute</td><td>Type</td><td>Mandatory</td><td>Comments</td><td>Validation Required?</td></tr><tr><td>Treatment Process ID</td><td>Numeric</td><td>Y</td><td>Auto-generated numeric value which will act as a unique identifier for a process flow</td><td>N, this value should be system generated</td></tr><tr><td><p>Process Name</p><p><br><br><br><br><br><br></p></td><td>Text</td><td>Y</td><td>This is the commonly used identifier for the process flow</td><td>Max characters - 256</td></tr><tr><td>Status</td><td>Array</td><td>Y</td><td>Status of the process flow</td><td>Active/Inactive, Single Select</td></tr><tr><td>Treatment Process Type</td><td>Array</td><td>Y</td><td>The dropdown will be auto populated basis the list of waste maintained in the MDMS</td><td><p>Single Select</p><p><br><br></p></td></tr><tr><td>Treatment Process Subtype</td><td>Array</td><td>Y</td><td>The dropdown will be auto populated basis the list of waste maintained in the MDMS</td><td><p>Single Select</p><p><br><br></p></td></tr></tbody></table>

2. ### Plants

| Attribute                                        | Type               | Mandatory | Comments                                                                       | Validation Required?                                         |
| ------------------------------------------------ | ------------------ | --------- | ------------------------------------------------------------------------------ | ------------------------------------------------------------ |
| Plant ID                                         | Numeric            | Y         | Auto-generated numeric value which will act as a unique identifier for a plan. | Auto-generated                                               |
| <p>Plant Name</p><p><br><br><br><br><br><br></p> | Text               | Y         | This is the commonly used identifier for the plant                             | Maximum charatcters - 128                                    |
| Plant Type                                       | Array              | Y         | <p><br></p>                                                                    | Single select only, faecal sludge, solid waste, co-treatment |
| Tenant Id                                        | Text               | Y         | <p><br></p>                                                                    | <p><br></p>                                                  |
| Status                                           | Array              | Y         | Status of the plant                                                            | Active/inactive, single select                               |
| Geolocation                                      | Latitude-Longitude | Y         | <p><br></p>                                                                    | Capture the exact latitude-longitude                         |

3. ### Stages

| Attribute                                        | Type    | Mandatory | Comments                                                                                                                                                                                                                              | Validation Required?                                           |
| ------------------------------------------------ | ------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| Stage ID                                         | Numeric | Y         | Auto-generated numeric value which will act as a unique identifier for a Job ID                                                                                                                                                       | Auto-generated                                                 |
| <p>Stage Name</p><p><br><br><br><br><br><br></p> | Text    | Y         | This is the commonly-used identifier for the Job                                                                                                                                                                                      | <p>Maximum characters - 128</p><p>Minimum xharacters - NA </p> |
| Status                                           | Boolean | Y         | Status of the stage                                                                                                                                                                                                                   | Active/inactive, single select                                 |
| Input Quality Measurement Required               | Boolean | Y         | This selection will allow the user to set up if the  input quality for the particular input type needs to be monitored. A user should be able to enable and disable input quality measurement requirement independently for each type | Yes/no, single select                                          |
| Output Type                                      | Array   | Y         | The dropdown will be auto-populated basis the list of output types                                                                                                                                                                    | Multi-select                                                   |
| Output Quality Measurement Required              | Boolean | Y         | This selection will allow the user to set up if the output quality for the particular job needs to be monitored. A user should be able to enable and disable the output quality measurement requirement independently for each type   | <p>Yes/no, single select</p><p><br><br></p>                    |

4. ### Testing Parameters

| Attribute                                    | Type    | Mandatory | Validation                                                                                                                                              |
| -------------------------------------------- | ------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Quality Parameter                            | Array   | Y         | <p>Selecting from the predefined of the above-mentioned quality parameters and standards.</p><p>single select</p>                                       |
| Quality Parameter Unit of Measurement        | Array   | Y         | Selection of the unit of measurement (mg/L, Absolute value etc). Single select                                                                          |
| Benchmark Rule                               | Array   | Y         | Options include X>=,<=R, =\<Y and >=Z, single select                                                                                                    |
| Benchmark Value                              | Numeric | Y         | Entered by user, numeric only                                                                                                                           |
| Testing Frequency - Manual (Days)            | Numeric | Y         | Selecting a custom frequency range for laboratory testing based on consent to operate, numeric only                                                     |
| Monitoring Frequency - Quality Sensor (Days) | Numeric | N         | <p>Selecting a custom frequency</p><p><br></p><p>Note: Should be optional if the ULB/state choses not to have sensor-based monitoring. Numeric only</p> |

5. ### Configure IoT Devices

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

6. ### Testing Schedule

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

7. ### Test Results

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

8. ### Alert: Lab & IoT Result Not As Per the Benchmark; Lab & Device Results Do Not Match

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

9. ### &#x20;Alert: No Reading Received From the Device

| Attribute      | Type     | Required? | Comments                                                                  |
| -------------- | -------- | --------- | ------------------------------------------------------------------------- |
| Alert DateTime | Datetime | Y         | Auto captured based on date-time                                          |
| Alert Type     | Text     | Y         | <p>Auto captured</p><ul><li>No reading received from the device</li></ul> |
| Plant Name     | Text     | Y         | <p><br></p>                                                               |
| Process Name   | Text     | Y         | <p><br></p>                                                               |
| Process Type   | Text     | Y         | <p><br></p>                                                               |
| Device ID      | Numeric  | Y         | <p><br></p>                                                               |

