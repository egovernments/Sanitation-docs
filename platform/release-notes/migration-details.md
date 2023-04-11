# Migration Details

## Steps

1\. Refer to the service build updates in this [document](mdms-configuration-and-service-build-updates.md). The service builds need to be deployed in the dedicated environment.

2\. Run the DB migration script.

* [https://github.com/egovernments/DIGIT-Dev/blob/master/municipal-services/fsm/src/main/resources/db/migration/main/V20229102210823\_\_fsm\_advance\_amount.sql](https://github.com/egovernments/DIGIT-Dev/blob/master/municipal-services/fsm/src/main/resources/db/migration/main/V20229102210823\_\_fsm\_advance\_amount.sql)
* [https://github.com/egovernments/DIGIT-Dev/blob/master/municipal-services/vehicle/src/main/resources/db/migration/main/V20223105113254\_\_update\_null\_vehicle\_status.sql](https://github.com/egovernments/DIGIT-Dev/blob/master/municipal-services/vehicle/src/main/resources/db/migration/main/V20223105113254\_\_update\_null\_vehicle\_status.sql)
* [https://github.com/egovernments/DIGIT-Dev/blob/master/municipal-services/fsm-calculator/src/main/resources/db/migration/main/V20230206110604\_\_RemoveConstraintOnBillingAudit.sql](https://github.com/egovernments/DIGIT-Dev/blob/master/municipal-services/fsm-calculator/src/main/resources/db/migration/main/V20230206110604\_\_RemoveConstraintOnBillingAudit.sql)

3\. The workflow needs to be created or updated. Refer to this [document](workflow-configuration-changes.md) for details.

4\. Refer to this document for the [configuration](mdms-configuration-and-service-build-updates.md) details.&#x20;

5\. Restart the following services:&#x20;

* MDMS
* &#x20;Configs
* Localisation
* PDF
* Workflow

\
[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)](http://creativecommons.org/licenses/by/4.0/)_All content on this page by_ [_eGov Foundation_](https://egov.org.in/) _is licensed under a_ [_Creative Commons Attribution 4.0 International License_](http://creativecommons.org/licenses/by/4.0/)_._
