# Configuration Updates

## Configuration Changes <a href="#config-changes" id="config-changes"></a>

| Feature               | Service Name | Changes                                                                                                                                                                                                                                     | Description                                                  |
| --------------------- | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| pqm-persister         | PQM          | [Link](https://github.com/egovernments/configs/blob/UNIFIED-QA/sanitation/egov-persister/pqm-persister.yaml)                                                                                                                                | Added persister config for the pqm service.                  |
| pqm-anomaly-persister | PQM-Anomaly  | [Link](https://github.com/egovernments/configs/blob/UNIFIED-QA/sanitation/egov-persister/pqm-anomaly-finder-persister.yaml)                                                                                                                 | Added persister file for the pqm-anomaly service.            |
| pqm-indexer           | PQM          | [Link](https://github.com/egovernments/configs/blob/UNIFIED-QA/sanitation/egov-indexer/pqm-service-indexer.yml)                                                                                                                             | Added indexer file for the pqm service.                      |
| pqm-anomaly-indexer   | PQM-anomaly  | [Link](https://github.com/egovernments/configs/blob/UNIFIED-QA/sanitation/egov-indexer/pqm-anomaly-finder-indexer.yml)                                                                                                                      | Added indexer file for the pqm-anomaly service.              |
| pqm-inbox-indexer     | PQM          | [Link](https://github.com/egovernments/configs/blob/UNIFIED-QA/sanitation/egov-indexer/egov-pqm-service.yml)                                                                                                                                | Added inbox indexer file for the pqm service.                |
| Vendor-persister      | Vendor       | [PR](https://github.com/egovernments/configs/commit/07489d419f3ffad382908b34073da17f1dba263e)                                                                                                                                               | Updated vendor-persister file for sanitation worker feature. |
| FSM-persister         | FSM          | [PR](https://github.com/egovernments/configs/commit/3022f4382c7004b271c0d1841bcdbdf98904a538#diff-896ccb99eda78089037d03c49a6955e80f83b344e270c3af918b16058c26547a)                                                                         | Updated fsm-persister file for sanitation worker feature.    |
| TQM Chart API changes | PQM          | [Link](../architecture/pqm/low-level-design/services/pqm-service.md#pqm-landing-page-charts)                                                                                                                                                | Added chart API configs for TQM plant operator landing page. |
| PQM Download PDF      | PQM          | [data-config](https://github.com/egovernments/configs/blob/UNIFIED-QA/pdf-service/data-config/pqm-adhoctest.json)  \| [format-config](https://github.com/egovernments/configs/blob/UNIFIED-QA/pdf-service/format-config/pqm-adhoctest.json) | Pdf download configuration for test results summary          |

## Kafka Topic Details

| Service            | Type                                                        | Topic Name                           |
| ------------------ | ----------------------------------------------------------- | ------------------------------------ |
| PQM                | Save test on creation                                       | save-test-application                |
|                    | Update test                                                 | update-test-application              |
|                    | Update test workflow                                        | update-workflow-test-application     |
|                    | Save test topic for inbox                                   | save-test-event-application          |
|                    | Update test topic for inbox                                 | update-test-event-application        |
|                    | Anomaly topic for when a test fails                         | create-pqm-anomaly-finder            |
|                    | Anomaly topic for when a test result has not been submitted | testResultNotSubmitted-anomaly-topic |
|                    | Creation of plant-user mapping                              | save-plant-user-mapping              |
|                    | Updation of plant-user mapping                              | update-plant-user-mapping            |
| PQM Anomaly Finder | Anomaly topic for when a test fails                         | save-pqm-test-anomaly-details        |
|                    | Anomaly topic for when test result not submitted            | testResultNotSubmitted-anomaly-topic |
|                    | Save anomaly topic                                          | create-pqm-anomaly-finder            |
|                    | Event (In-App) Notification                                 | persist-user-events-async            |
| FSM                | Save new FSM application                                    | save-fsm-application                 |
|                    | Update FSM application                                      | update-fsm-application               |
|                    | Update FSM application workflow                             | update-fsm-workflow-application      |
|                    | Update vehicle trip details                                 | update-vehicle-trip-Details          |
|                    | Save plant user mapping                                     | save-plant-map-application           |
|                    | Update plant user mapping                                   | update-plant-map-application         |
|                    | Receipts get pushed to this topic                           | egov.collection.payment-create       |
|                    | SMS notification topic                                      | egov.core.notification.sms           |
|                    | Event (In-app) notification topic                           | persist-user-events-async            |
| Vendor             | Save vendor topic                                           | save-vendor-application              |
|                    | Update vendor topic                                         | update-vendor-application            |
|                    | Save driver topic                                           | save-driver-application              |
|                    | Update driver topic                                         | update-driver-application            |
|                    | Update vendor-driver and vendor-vehicle relationship        | save-vendordrivervehicle-application |
