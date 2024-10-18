# PQM

Process Quality Management (PQM) is a service that will be responsible for Treatment Quality Monitoring. It will improve the quality of processes, such as waste treatment process, water treatment process, etc. We are building these services on top of the existing building blocks of DIGIT.&#x20;

<figure><img src="../../../.gitbook/assets/Screenshot 2023-09-21 at 1.21.03 PM.png" alt=""><figcaption></figcaption></figure>

## Core Components

To develop a new service, one needs to create a micro-service and make it available through the API gateway. The API gateway calls the [User Service](https://core.digit.org/platform/core-services/user-services) for authentication and the [Access Service](https://core.digit.org/platform/core-services/access-control-services) for authorisation.&#x20;

Implementation users and service developers can configure the roles and map the roles, actions, plants, treatment process, stages, and testing standards will be created using the [Master Data Management Service](https://core.digit.org/platform/core-services/mdms-master-data-management-service).

[Citizen Dashboard: ](https://core.digit.org/guides/developer-guide/ui-developer-guide/citizen-module-setup)The service user interface can be developed as part of the Citizen Dashboard or can be an independent solution. The citizen can log in using a mobile number and OTP. They can apply for a new service using the service UI. The [File Store Service](https://core.digit.org/platform/core-services/filestore-service) allows users to upload relevant documentation.

The [Persister Service](https://core.digit.org/platform/core-services/persister-service) stores the submitted application asynchronously into the registry. The PII data is encrypted using the [Encryption Service](https://core.digit.org/platform/core-services/encryption-service) before storing. All changes are digitally signed and logged using the [Signed Audit Service](https://core.digit.org/focus-areas/data-security/signed-data-audit) (ongoing). The [Indexer Service](https://core.digit.org/platform/core-services/indexer-service) transforms and enriches the application data. The Indexer Service also strips the PII data and sends it to the [Analytics Data Store(ElasticSearch)](https://core.digit.org/guides/operations-guide/availability/backbone-services/elastic-search).

The[ Dashboard Backend Service](https://urban.digit.org/platform/configure-digit/services-overview/business-services/dashboard-analytics-backend) executes configured queries on the stripped data and makes the aggregated data available to the [Dashboard Frontend](https://core.digit.org/guides/operations-guide/availability/dss-dashboard) for the administrator or employee view. The views are in accordance with the user role access which is also configurable.

The [Employee Service](https://core.digit.org/guides/developer-guide/ui-developer-guide/employee-module-setup) allows employee registrations and enables them to log in using the employee dashboard. The dashboard displays the list of pending applications as per the employee's role. The employee can perform actions on these applications using the employee UI for the service. As the status changes or actions are taken on the applications, the relevant [SMS and Email Notification Service](https://core.digit.org/platform/core-services/sms-notification-service) sends the updates to the plant operator and lab collectors. Once the test is completed, the lab/urban local body (ULB) employee can upload and download the test results submitted.

DIGIT has multi-tenant configuration capabilities. The [Location Service](https://core.digit.org/platform/core-services/location-services) allows the configuration of the tenant hierarchy and maps multiple tenants like country, state, district, or state, department, and sub-department. Each tenant can have their own configurations for service, roles, workflows etc. This allows for variations across different agencies in tune with the local context. The [Language Service](https://core.digit.org/platform/core-services/localization-service) facilitates the support of multiple languages in DIGIT. This service stores the translations in multiple languages.

## PQM Components

The [PQM Service](broken-reference) schedules and manages recurring test to evaluate the quality of a process. This can read sensor devices if assigned for a process stage. It can update the treatment quality workflow status based on the results submitted manually or collected through IoT devices. Provides APIs for creating ad-hoc tests, update results, search for results, and anomalies identified.

The [PQM Anomaly Finder](broken-reference) service finds anomalies in the process quality and raises notifications/alerts based on the defined anomaly check configurations.

## ER Diagram

<figure><img src="../../../.gitbook/assets/Screenshot 2023-09-21 at 8.56.48 AM.png" alt=""><figcaption></figcaption></figure>

## Sequence Diagram

#### Create Manual Tests (Cron Job)

<figure><img src="../../../.gitbook/assets/Screenshot 2023-09-21 at 1.23.09 PM.png" alt=""><figcaption></figcaption></figure>

#### Create IoT Tests (Cron Job)

<figure><img src="../../../.gitbook/assets/Screenshot 2023-09-21 at 1.24.26 PM (1).png" alt=""><figcaption></figcaption></figure>

#### Create Test (Ad-hoc)

<figure><img src="../../../.gitbook/assets/Screenshot 2023-09-21 at 1.26.46 PM.png" alt=""><figcaption></figcaption></figure>

#### Update Test

<figure><img src="../../../.gitbook/assets/Screenshot 2023-09-21 at 1.28.03 PM.png" alt=""><figcaption></figcaption></figure>

#### Search Tests

<figure><img src="../../../.gitbook/assets/Screenshot 2023-09-21 at 9.02.52 AM.png" alt=""><figcaption></figcaption></figure>

#### Find Anomaly

<figure><img src="../../../.gitbook/assets/Screenshot 2023-09-21 at 9.04.50 AM.png" alt=""><figcaption></figcaption></figure>
