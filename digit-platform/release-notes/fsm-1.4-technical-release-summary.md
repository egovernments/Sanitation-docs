---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# FSM 1.4 - Technical Release Summary

## Impacted Service:

## Process Quality Management (PQM):

Introduced three new services: PQM Service, PQM Anomaly Service, and PQM Scheduler Service.

## PQM Service

* Create, update, and search for process quality monitoring tests.
* Record test results gradually for a test and submit  from evaluation when all the test results available
* Evaluation of test values against benchmarks configured in MDMS, for producing a test result (FAIL/PASS) status.
* Test results undergo anomaly analysis for comprehensive insights.
* Plant performance related charts.

## PQM Anomaly Finder Service

* Actively monitors anomalies in process quality.
* Added notification for relevant user groups promptly for proactive anomaly management.

## PQM Scheduler (CronJob Scheduler)

* Automation of test scheduling based on environment configuration and MDMS test standard configurations.
* Triggers schedule APIs from PQM-Scheduler to generate tests at defined frequency.
* Efficiently runs tests at specified intervals, ensuring a configurable approach.

## Sanitation Worker:

A new worker registry concept has been introduced. Creating a worker, updating details, searching and tagging a worker for different operations on sanitation programmes. Sanitation workers' creation, updation, and search operations are performed using the individual registry.

* Added functionality for creating, updating, and searching for sanitation workers.
* Deprecated the drivers tab and added the driver concept from the FSM registry.
* Introduced the sanitation workers tab to the FSM registry.

## Vendor:

* Added functionality for assigning. a sanitation worker to a vendor.
* Migration of existing drivers to sanitation workers.
* Deprecation of delinking of a driver with vendors introduced in v1.3.

## FSM:

* Tag sanitation workers (drivers and helpers) to an FSM application for capturing the workers' activities.
* The inbox for FSM has been upgraded from V1 to V2.

No core services have been modified. Workflow details, flow diagram, and API details are given in confluence.

## API List (Modified and New):

| Service                    | API's                                | Description                                                             | New/Update  |
| -------------------------- | ------------------------------------ | ----------------------------------------------------------------------- | ----------- |
| PQM Service                | <p><br></p>                          | <p><br></p>                                                             | <p><br></p> |
| <p><br></p>                | /pqm-service/v1/\_create             | Adhoc create test                                                       | New         |
| <p><br></p>                | /pqm-service/v1/\_update             | Update test with results, save test with partial results as drafts      | New         |
| <p><br></p>                | /pqm-service/v1/\_search             | Search for PQM tests                                                    | New         |
| <p><br></p>                | /pqm-service/v1/\_scheduler          | Schedule test based on the test standards in MDMS                       | New         |
| <p><br></p>                | /pqm-service/v1/\_plainsearch        | API for redexing the data                                               | New         |
| <p><br></p>                | pqm-service/plant/user/v1/\_create   | Add plant and user mapping                                              | New         |
| <p><br></p>                | pqm-service/plant/user/v1/\_update   | Update plant and user mapping                                           | New         |
| <p><br></p>                | pqm-service/plant/user/v1/\_search   | Search for plant user mapping                                           | New         |
| PQM Anomaly FInder Service | <p><br></p>                          | <p><br></p>                                                             | <p><br></p> |
| <p><br></p>                | /pqm-anomaly-finder/v1/\_search      | Search for anomalies                                                    | New         |
| <p><br></p>                | /pqm-anomaly-finder/v1/\_plainsearch | Reindex the anomaly data                                                | New         |
| FSM                        | <p><br></p>                          | <p><br></p>                                                             | <p><br></p> |
| <p><br></p>                | /fsm/v1/\_update                     | Added list of workers object for tagging workers to the FSM application | Updated     |
| Vendor                     | <p><br></p>                          | <p><br></p>                                                             | <p><br></p> |
| <p><br></p>                | /vendor/v1/\_update                  | Added list of workers object to assign sanitation worker to vendor      | Updated     |

