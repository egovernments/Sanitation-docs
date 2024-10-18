# Requirements to enable FSM Module in a new evironment

To enable FSM module in any new environment, we would need to perform certain steps.\
Considering an AWS account is already setup, following are the steps to be followed:

### Configuration Requirements <a href="#configuration-requirements" id="configuration-requirements"></a>

1. Update the [Configs repo](https://github.com/egovernments/configs/tree/UAT) with the following requirements:
   * _Indexer config:_\
     We will need following indexer files for setting up any module\
     [FSM indexer](https://github.com/egovernments/configs/blob/fsm-odisha-latest-configs/egov-indexer/egov-fsm.yml)\
     [Vehicle indexer](https://github.com/egovernments/configs/blob/fsm-odisha-latest-configs/egov-indexer/egov-vehicle.yaml)\
     [Vendor indexer](https://github.com/egovernments/configs/blob/fsm-odisha-latest-configs/egov-indexer/egov-vendor.yaml)\
     [Demand/billing indexer](https://github.com/egovernments/configs/blob/fsm-odisha-latest-configs/egov-indexer/billingservices-indexer.yml)\
     [Payment indexer](https://github.com/egovernments/configs/blob/fsm-odisha-latest-configs/egov-indexer/payment-indexer.yml)
   * _Persister config_\
     Persister files required:\
     [Apportion persister](https://github.com/egovernments/configs/blob/fsm-odisha-latest-configs/egov-persister/apportion-persister.yml)\
     [Billing-service persister](https://github.com/egovernments/configs/blob/fsm-odisha-latest-configs/egov-persister/billing-services-persist.yml)\
     [Workflow persister](https://github.com/egovernments/configs/blob/fsm-odisha-latest-configs/egov-persister/egov-workflow-v2-persister.yml)\
     [HRMS persister](https://github.com/egovernments/configs/blob/fsm-odisha-latest-configs/egov-persister/hrms-employee-persister.yml)\
     [Filestore persister](https://github.com/egovernments/configs/blob/fsm-odisha-latest-configs/egov-persister/pdf-filestoreid-update.yml)\
     [PDF gen persister](https://github.com/egovernments/configs/blob/fsm-odisha-latest-configs/egov-persister/pdf-generator.yml)\
     [Pg-service persister](https://github.com/egovernments/configs/blob/fsm-odisha-latest-configs/egov-persister/pg-service-persister.yml)\
     [Upload persister](https://github.com/egovernments/configs/blob/fsm-odisha-latest-configs/egov-persister/uploader-persister.yml)\
     [egov-user-event-persister](https://github.com/egovernments/configs/blob/fsm-odisha-latest-configs/egov-persister/egov-user-event-persister.yml)\
     [FSM persister](https://github.com/egovernments/configs/blob/fsm-odisha-latest-configs/egov-persister/fsm-persister.yaml)\
     [FSM Calculator persister](https://github.com/egovernments/configs/blob/fsm-odisha-latest-configs/egov-persister/fsm-calculator-persister.yaml)\
     [Vehicle persister](https://github.com/egovernments/configs/blob/fsm-odisha-latest-configs/egov-persister/vehicle-persister.yaml)\
     [Vendor persister](https://github.com/egovernments/configs/blob/fsm-odisha-latest-configs/egov-persister/vendor-persister.yaml)
   * _Searcher config_\
     [FSM searcher](https://github.com/egovernments/configs/blob/fsm-odisha-latest-configs/egov-searcher/inboxFSMSearch.yml)
   * _Pdf config_\
     Data config: [fsm-receipt](https://github.com/egovernments/configs/blob/fsm-odisha-latest-configs/pdf-service/data-config/fsm-receipt.json)\
     Format config: [fsm-receipt](https://github.com/egovernments/configs/blob/fsm-odisha-latest-configs/pdf-service/format-config/fsm-receipt.json)
   * _Reports_\
     [fsm-report](https://github.com/egovernments/configs/blob/fsm-odisha-latest-configs/reports/config/fsm-reports.yml)\
     Also mention the path of the above report file [here](https://github.com/egovernments/configs/blob/1239785491ba22e5947703c58198e17bb38779cd/reports/reportFileLocationsv1.txt#L5).
   * _Dashboard configs_\
     \=> [ChartApiConfig.json](https://github.com/egovernments/configs/blob/6314e869dd0a1dd91d13c24fe9dca5f509391ce4/egov-dss-dashboards/dashboard-analytics/ChartApiConfig.json#L4147-L5324)\
     \=> [MasterDashboardConfig.json](https://github.com/egovernments/configs/blob/6314e869dd0a1dd91d13c24fe9dca5f509391ce4/egov-dss-dashboards/dashboard-analytics/MasterDashboardConfig.json#L3879-L4310)\
     \

2. Add all [mdms ](https://github.com/egovernments/egov-mdms-data/tree/v2.3-patch)configs required\

   * Add all Actions/endpoints required for fsm as mentioned in this [file](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/ACCESSCONTROL-ACTIONS-TEST/actions-test.json).\
     Add all actions with respect to core and business-services as well, like those of - egov-_user, egov-mdms-service, apportion-service, collection-service, billing-service, egov-location, egov-common-masters, egov-idgen, egf-master, egov-user-event, otp services, access, egov-workflow-v2, data-uploader, egov-hrms, filestore-service, pdf-service, egov-pdf, report, localization-service, egov-persister, egov-indexer, egov-searcher, eg-pg-service, dasboard-analytics, dashboard-ingest, digit-ui, fsm, fsm-calculator, vendor, vehicle._
   * Add Role-Action mapping in [roleactions.json](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/ACCESSCONTROL-ROLEACTIONS/roleactions.json) file
   * Add required Roles for the respective FSM module in [roles.json](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/ACCESSCONTROL-ROLES/roles.json)
   * Add [BillingService](https://github.com/egovernments/egov-mdms-data/tree/v2.3-patch/data/pg/BillingService), [DIGIT-UI](https://github.com/egovernments/egov-mdms-data/tree/v2.3-patch/data/pg/DIGIT-UI), [DataSecurity](https://github.com/egovernments/egov-mdms-data/tree/v2.3-patch/data/pg/DataSecurity), [FSM](https://github.com/egovernments/egov-mdms-data/tree/v2.3-patch/data/pg/FSM), [Vehicle](https://github.com/egovernments/egov-mdms-data/tree/v2.3-patch/data/pg/Vehicle), [Vendor](https://github.com/egovernments/egov-mdms-data/tree/v2.3-patch/data/pg/Vendor), [Workflow](https://github.com/egovernments/egov-mdms-data/tree/v2.3-patch/data/pg/Workflow), [common-masters](https://github.com/egovernments/egov-mdms-data/tree/v2.3-patch/data/pg/common-masters), [dss-dashboard](https://github.com/egovernments/egov-mdms-data/tree/v2.3-patch/data/pg/dss-dashboard), [egf-master](https://github.com/egovernments/egov-mdms-data/tree/v2.3-patch/data/pg/egf-master), [egov-hrms](https://github.com/egovernments/egov-mdms-data/tree/v2.3-patch/data/pg/egov-hrms) , [tenant](https://github.com/egovernments/egov-mdms-data/tree/v2.3-patch/data/pg/tenant) folders with their respective files.
   * Also add ULB/city specific data in their respective folders, for instance, create a folder [angul](https://github.com/egovernments/egov-mdms-data/tree/v2.3-patch/data/pg/angul) and add the respective data files like _Slum.json, UrcConfig.json, ZeroPricing.json_ required.

**Note:** The data sepecific to any ULB needs to be collected from the ULB officials and need to be present in mdms level.\
Refer the ULB specific data documentation and updation/upsertion [here.](https://sanitation.digit.org/\~/changes/QUGTLlRoUN6QNmvDA1Gb/product/faecal-sludge-management-fsm/fsm-core-service-configuration/enablement-toolkits-assetization-for-fsm/data-templates-for-data-collection)

&#x20;

### DevOps Requirements <a href="#devops-requirements" id="devops-requirements"></a>

1. Add all the helm charts with respect to the business-services, core-services and municipal-services. Refer [here](https://github.com/egovernments/DIGIT-DevOps/tree/master/deploy-as-code/helm/charts).
2. Add DevOps level changes in the evironment file. Refer [here](https://github.com/egovernments/DIGIT-DevOps/blob/master/deploy-as-code/helm/environments/fsm-uat.yaml).\
   Add all the paths for files in the configs in the environment file. For instance, add the the path of indexer, persister and searcher files, etc.\
   Make sure to add required properties at each service level as defined in the above mentioned environment file.\
   \


### Backend/Frontend Requirements <a href="#backend-frontend-requirements" id="backend-frontend-requirements"></a>

1. Deploy all required core-services builds to support this municipal-services(FSM and its dependent services). The core-services include:\
   _egov-accesscontrol, egov-common-masters, egov-data-uploader, egov-document-uploader, egov-enc-service, egov-filestore, egov-idgen,egov-indexer, egov-localization, egov-location, egov-mdms-service, egov-notification-mail, egov-notification-sms, egov-otp, egov-persister, egov-pg-service, egov-searcher, egov-url-shortening, egov-user, egov-workflow-v2, pdf-service, report, user-otp, zuul_
2. Deploy all required business-services builds to support this municipal-service(FSM and its dependent services). The business-services include:\
   _billing-service, collection-services, dashboard-analytics, dashboard-ingest, egf-instrument, egf-master, egov-apportion-service, egov-hrms._
3. Deploy this municipal-service “fsm” as well as dependent municipal-services: fsm-calculator, vendor, vehicle, inbox, egov-user-event.
4. Upsert the required localizations. Refer [this document](https://sanitation.digit.org/\~/changes/QUGTLlRoUN6QNmvDA1Gb/product/faecal-sludge-management-fsm/fsm-core-service-configuration/enablement-toolkits-assetization-for-fsm/data-loading-steps/loading-localisations) for detailed steps.
5. Upsert the workflows as mentioned in the [document](https://sanitation.digit.org/v/v1.3.1/product/faecal-sludge-management-fsm/fsm-core-service-configuration#business-service-workflow-configuration).
6. Upsert the SMS templates as localizations in your environment as well as update them in the SMS portal being used by the state. For detailed infomation, [read here](https://app.gitbook.com/o/-MEQmzNGXk5ajuZujG7E/s/LpfYJCGZoBEmcFf9yWTh/\~/changes/103/product/faecal-sludge-management-fsm/fsm-core-service-configuration/enablement-toolkits-assetization-for-fsm/sms-templates-for-fsm)[.](https://sanitation.digit.org/\~/changes/QUGTLlRoUN6QNmvDA1Gb/product/faecal-sludge-management-fsm/fsm-core-service-configuration/enablement-toolkits-assetization-for-fsm/sms-templates-for-fsm)\


&#x20;
