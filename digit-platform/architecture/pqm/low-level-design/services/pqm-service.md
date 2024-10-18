# PQM Service

## Overview

The Process Quality Management (PQM) service will help users to create, update, and search for process quality monitoring tests. The service will evaluate the uploaded test values against benchmarks and produce result (FAIL/PASS) status. Test results will be further processed for anomaly analysis. The service can perform two types of test: Manual Test (Lab), and Automatic Test (IoT-based).

### Plant User Mapping

The service enables mapping plant codes to operators and ULB admins, ensuring that each is only authorised to manage plants linked to their account, enhancing control and accountability. In the mapping process need to check below mention things

* `PlantCode` :  Unique plant code which is configured in the mdms
* `PlantUserType` : User type will be either plant-operation or the ulb-admin&#x20;
* `PlantUserUuid` : Unique user id of the employee which have the type of ulb-admin or the plant-operator.

## Service Dependencies:

List of services that PQM service depends on:

* [MDMS](https://core.digit.org/platform/core-services/mdms-master-data-management-service)
* [Workflow](https://core.digit.org/platform/core-services/workflow-service)
* [Notification](https://core.digit.org/platform/core-services/sms-notification-service)
* Localisation
* [Access Control](https://core.digit.org/platform/core-services/access-control-services)
* [User](https://core.digit.org/platform/core-services/user-services)
* [IDGen](https://core.digit.org/platform/core-services/id-generation-service)

## Master Data

The following masters need to be created as part of this module:

* Plant
* PlantType&#x20;
* PlantConfig&#x20;
* Process&#x20;
* ProcessType&#x20;
* ProcessSubType&#x20;
* Stage&#x20;
* Material&#x20;
* Parameter&#x20;
* Unit&#x20;
* BenchmarkRule&#x20;
* TestingStandard&#x20;
* QualityCriteria&#x20;
* Device&#x20;
* DeviceDetails&#x20;
* DeviceConfig



## Kafka Topic Details

| Description                                                 | Topic Name                           |
| ----------------------------------------------------------- | ------------------------------------ |
| Save Test on creation                                       | save-test-application                |
| Update Test                                                 | update-test-application              |
| Update Test Workflow                                        | update-workflow-test-application     |
| Save test topic for Inbox                                   | save-test-event-application          |
| Update test topic for Inbox                                 | update-test-event-application        |
| Anomaly topic for when a test fails                         | create-pqm-anomaly-finder            |
| Anomaly topic for when a test result has not been submitted | testResultNotSubmitted-anomaly-topic |
| Creation of plant-user mapping                              | save-plant-user-mapping              |
| Updation of plant-user mapping                              | update-plant-user-mapping            |



## Postman-Collection

PQM- [Api collection](https://api.postman.com/collections/28207698-c82829bb-6272-48e4-b31b-d6a9c9f66b2d?access\_key=PMAT-01HDRGDET199YSWB72QVM3E2TZ)

Plant User Mapping- [Api collection](https://api.postman.com/collections/23418568-f6fb8dd4-c830-4389-a7d3-84ddc7a63a97?access\_key=PMAT-01HGW7JCWWXAYQ2ECAQTH84V1Y)

## API Specification

[PQM Swagger Link](https://github.com/egovernments/SANITATION/blob/develop/API-CONTRACTS/pqm/PQM\_API\_Contract.yaml)



## Data Model

<figure><img src="../../../../../.gitbook/assets/image (171).png" alt=""><figcaption></figcaption></figure>

## Sequence Diagrams

**Create New**&#x20;

<figure><img src="https://lh7-us.googleusercontent.com/NAtQliYBsozTosV22TE4ZgkJU1LF51r3Yk1K5nCTKjyCs2SfSvtEIF6ee0C4Z36TwiwQmVabLbOtbgUepa_gXhIiKvpaDJs5ppLSKxeNkGxMPLGhubrhFAYDW_7hPeQ08nTwcgNfGMSRSbsiUgjXqJY" alt=""><figcaption></figcaption></figure>

**Update - new**

<figure><img src="https://lh7-us.googleusercontent.com/TZD0IUQFDR2hjkxwyy8ewA8wFRZDcOjdZF3CvZGDkz5FuOWCMF8lZnabmDfXX-1P2XBn9tY99PCixcHB4mw9ud-lhfnVm-QXfJjGYnSryFsjtQtGs8D6mBJ5VFvUOdcbDZ3FP4oin4gxLbplp9QGp5k" alt=""><figcaption></figcaption></figure>

**Search**

<figure><img src="https://lh7-us.googleusercontent.com/8Xz5IFWtVQGk5PzslwrqfEsumW0-HtUcrc44rtdZMPIwsw2YpVUimWEPQjx2FZsLdpnZcsm57ib24vwqBjFuG7oDnR40zX6FR2V1Pc8lDN4J3hRnFMMhW448WcluRa5yhMQ-fCAueeWYEBHp5MVLwZ0" alt=""><figcaption></figcaption></figure>

## Reference Docs <a href="#reference-docs" id="reference-docs"></a>

### Doc Links <a href="#doc-links" id="doc-links"></a>

<table><thead><tr><th width="611"></th><th></th></tr></thead><tbody><tr><td><strong>Title</strong></td><td><strong>Link</strong></td></tr><tr><td>Workflow Technical Document</td><td><a href="https://core.digit.org/platform/core-services/workflow-service">Workflow Service</a></td></tr><tr><td>User Technical Document</td><td><a href="https://core.digit.org/platform/core-services/user-services">User Service</a></td></tr><tr><td>MDMS Technical Document</td><td><a href="https://core.digit.org/platform/core-services/mdms-master-data-management-service">M<strong>dms service</strong></a></td></tr><tr><td>IDGen Technical Document</td><td><a href="https://digit-discuss.atlassian.net/wiki/spaces/DD/pages/2002845709/ID+Generation+Service">Idgen service</a></td></tr><tr><td>Localisation Technical Document</td><td><a href="https://core.digit.org/platform/core-services/location-services">Localization service</a></td></tr><tr><td>Persister Technical Document</td><td><a href="https://core.digit.org/platform/core-services/persister-service">Persister service</a></td></tr></tbody></table>

### API List <a href="#api-list" id="api-list"></a>

<table data-header-hidden><thead><tr><th width="301.3333333333333"></th><th></th></tr></thead><tbody><tr><td><h4>Title </h4></td><td>Link</td></tr><tr><td>pqm-service/v1/_create</td><td><a href="https://api.postman.com/collections/23418568-472daff5-384b-4e6f-a853-890a7e211fdf?access_key=PMAT-01HKSE8HEXK19ZT9ZGGXE9PJQ9">Postman Collection</a></td></tr><tr><td>pqm-service/v1/_update</td><td><a href="https://api.postman.com/collections/23418568-472daff5-384b-4e6f-a853-890a7e211fdf?access_key=PMAT-01HKSE8HEXK19ZT9ZGGXE9PJQ9">Postman Collection</a></td></tr><tr><td>/pqm-service/v1/_search</td><td><a href="https://api.postman.com/collections/23418568-472daff5-384b-4e6f-a853-890a7e211fdf?access_key=PMAT-01HKSE8HEXK19ZT9ZGGXE9PJQ9">Postman Collection</a></td></tr><tr><td>/pqm-service/v1/_create  Adhoc</td><td><a href="https://api.postman.com/collections/23418568-472daff5-384b-4e6f-a853-890a7e211fdf?access_key=PMAT-01HKSE8HEXK19ZT9ZGGXE9PJQ9">Postman Collection</a></td></tr><tr><td>/pqm-anomaly-finder/v1/_plainsearch</td><td><a href="https://api.postman.com/collections/23418568-472daff5-384b-4e6f-a853-890a7e211fdf?access_key=PMAT-01HKSE8HEXK19ZT9ZGGXE9PJQ9">Postman Collection</a></td></tr><tr><td>/pqm-service/plant/user/v1/_create</td><td><a href="https://api.postman.com/collections/23418568-472daff5-384b-4e6f-a853-890a7e211fdf?access_key=PMAT-01HKSE8HEXK19ZT9ZGGXE9PJQ9">Postman Collection</a></td></tr><tr><td>/pqm-service/plant/user/v1/_update</td><td><a href="https://api.postman.com/collections/23418568-472daff5-384b-4e6f-a853-890a7e211fdf?access_key=PMAT-01HKSE8HEXK19ZT9ZGGXE9PJQ9">Postman Collection</a></td></tr><tr><td>/pqm-service/plant/user/v1/_search</td><td><a href="https://api.postman.com/collections/23418568-472daff5-384b-4e6f-a853-890a7e211fdf?access_key=PMAT-01HKSE8HEXK19ZT9ZGGXE9PJQ9">Postman Collection</a></td></tr><tr><td>/inbox/v2/_search</td><td><a href="https://api.postman.com/collections/23418568-472daff5-384b-4e6f-a853-890a7e211fdf?access_key=PMAT-01HKSE8HEXK19ZT9ZGGXE9PJQ9">Postman Collection</a></td></tr></tbody></table>
