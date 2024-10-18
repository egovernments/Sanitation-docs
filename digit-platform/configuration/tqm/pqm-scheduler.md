# PQM Scheduler

### MDMS Changes

1. Please add Test Standards in mdms v2 under your ULBs (pg.citya, pg.cityb)
2. Add RoleAction Mapping for the scheduler API

File Path -&#x20;

{% code title="actions-test.json" %}
```json
  {
      "id": 367,
      "name": "Schedule PQM Application",
      "url": "/pqm-service/v1/_scheduler",
      "displayName": "Schedule PQM Applications",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "PQM",
      "code": "null",
      "path": ""
    }
```
{% endcode %}

File Path -

{% code title="roleactions.json" %}
```json
{
      "rolecode": "PQM_CRONJOB_SCHEDULER",
      "actionid": 367,
      "actioncode": "",
      "tenantId": "pg"
    }
```
{% endcode %}

3. Make sure that ULBs are configured in tenants.json file

File Path - [https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/pg/tenant/tenants.json](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/pg/tenant/tenants.json)

### Configuration

* Create a role in ACCESSCONTROL-ROLES/roles.json MDMS like[ this](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/pg/ACCESSCONTROL-ROLES/roles.json#L946C5-L950C8).
* Create a SYSTEM user with PQM\_CRONJOB\_SCHEDULER and SYSTEM roles. Find the curl below.
* The same username will be used to generate bills PQM\_SERVICE\_CRONJOB, it’s defined in the environment config.
* Cron job duration will be configured using environment variables from [here](https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/charts/sanitation/pqm-scheduler/values.yaml#L9)

curl --location 'http://localhost:8082/user/users/\_createnovalidate' --header 'Content-Type: application/json' --data-raw '{     "RequestInfo": {         "api\_id": "1",         "ver": "1",         "ts": null,         "action": "create",         "did": "",         "key": "",         "msg\_id": "",         "requester\_id": "",         "userInfo": {             "userName": "BillCreator",             "name": "BillCreator",             "gender": "male",             "mobileNumber": "9999999999",             "active": true,             "type": "EMPLOYEE",             "tenantId": "{STATE\_TANENT\_ID}",             "password": "eGov@123",             "roles": \[                 {                     "code": "SUPERUSER",                     "tenantId": "{STATE\_TANENT\_ID}"                 }             ]         }     },     "User": {         "userName": "PQM\_SERVICE\_CRONJOB",         "name": "PQM Service Cronjob",         "gender": "male",         "mobileNumber": "9999999999",         "active": true,         "type": "SYSTEM",         "tenantId": "pg",         "password": "eGov@123",         "roles": \[             {                 "code": "SYSTEM",                 "tenantId": "pg"             },             {                 "code": "PQM\_CRONJOB\_SCHEDULER",                 "name": "PQM\_CRONJOB\_SCHEDULER",                 "tenantId": "pg"             }         ]     } }'.



### **Deployment**

[Helm Chart](https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/charts/sanitation/pqm-scheduler/values.yaml)

### Update Scheduler

There are two ways to update the configuration of the scheduler:

* Add the config in the DevOps environment file, and restart the service. This will trigger the scheduler based on the updated environment configuration and restart the pqm-service.

&#x20;      Pqm-scheduler:

```
cron:  schedule: "0 0 * * *"
```

* Use the commands given below:&#x20;

```
Change schedule - kubectl patch cronjobs pqm-scheduler -p '{"spec" : {"schedule": "*/10 * * * *" }}'

Pause cron job - kubectl patch cronjobs pqm-scheduler -p '{"spec" : {"suspend" : true }}'

Resume cron job - kubectl patch cronjobs pqm-scheduler -p '{"spec" : {"suspend" : false}}' 

Create a new cronjob scheduler - kubectl create job --from=cronjob/pqm-scheduler pqm-scheduler
```

