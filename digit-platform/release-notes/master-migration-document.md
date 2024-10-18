# Master Migration Document

## **Overview**

This page contains the changes related to Process Quality Management-related services (PQM) and Sanitation Worker Welfare along with the MDMS, DevOps and configuration setups required to accommodate these features.

## Migration Steps

### **PQM Service**

The PQM service is required to create, update, search and evaluate tests against benchmarks.\
Follow the steps given below:

1. Add the [PQM-Service](../architecture/pqm/low-level-design/services/pqm-service.md).
2. Add the new persister file: [pqm-service-persister](https://github.com/egovernments/configs/blob/UNIFIED-UAT/sanitation/egov-persister/pqm-persister.yaml).
3. Add the [Helm chart. ](https://github.com/egovernments/DIGIT-DevOps/tree/unified-env/deploy-as-code/helm/charts/sanitation/pqm-service)
4. Configure the build.&#x20;

{% code lineNumbers="true" %}
```yaml
- name: 'builds/SANITATION/pqm'
    build:
      - work-dir: 'pqm'
        image-name: 'pqm-service'
        dockerfile: 'build/maven/Dockerfile'
      - work-dir: 'pqm/src/main/resources/db'
        image-name: 'pqm-service-db'
```
{% endcode %}

5. Make the role action-mapping changes in the MDMS.

[Access Control Actions Test](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/pg/ACCESSCONTROL-ACTIONS-TEST/actions-test.json#L4244C5-L4287C7)

[Access Control Role Actions](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/pg/ACCESSCONTROL-ACTIONS-TEST/actions-test.json#L4244C5-L4287C7)

Master Data for PQM&#x20;

6. Click on the Job-builder once the above steps are complete.
7. Restart the following services: egov-accesscontrol, egov-mdms-service, egov-persister

### PQM Scheduler

1. Add the [PQM Scheduler configuration](../architecture/pqm/low-level-design/services/pqm-scheduler.md).
2. Add the [Helm chart](https://github.com/egovernments/DIGIT-DevOps/tree/unified-env/deploy-as-code/helm/charts/sanitation/pqm-scheduler).
3. Configure the build.&#x20;

{% code lineNumbers="true" %}
```yaml
- name: 'builds/SANITATION/pqm-scheduler'
    build:
      - work-dir: 'pqm-scheduler'
        image-name: 'pqm-scheduler'
        dockerfile: 'pqm-scheduler/Dockerfile'
```
{% endcode %}

5. Make the role action-mapping changes in the MDMS.

[Access Control Actions Test](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/pg/ACCESSCONTROL-ACTIONS-TEST/actions-test.json#L4244C5-L4287C7)

[Access Control Role Actions](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/pg/ACCESSCONTROL-ACTIONS-TEST/actions-test.json#L4244C5-L4287C7)

6. Click on the Job-builder once the above steps are complete.
7. Restart the following services: egov-accesscontrol, egov-mdms-service.

### PQM Anomaly Finder Service

1. Add the [PQM Anomaly Finder service](../architecture/pqm/low-level-design/services/pqm-anomaly-finder.md).
2. Add the [Helm chart](https://github.com/egovernments/DIGIT-DevOps/tree/unified-env/deploy-as-code/helm/charts/sanitation/pqm-anomaly-finder).
3. Configure the build.&#x20;

{% code lineNumbers="true" %}
```yaml
  - name: 'builds/SANITATION/pqm-anomaly-finder'
    build:
      - work-dir: 'pqm-anomaly-finder'
        image-name: 'pqm-anomaly-finder'
        dockerfile: 'build/maven/Dockerfile'
      - work-dir: 'pqm-anomaly-finder/src/main/resources/db'
        image-name: 'pqm-anomaly-finder-db'
```
{% endcode %}

## Sanitation Worker Welfare

1. Add mdms changes, refer to this [link](../architecture/fsm/low-level-design/services/fsm-service.md#sanitation-worker).
2. Add config changes, refer to this [link](../architecture/fsm/low-level-design/services/fsm-service.md#sanitation-worker).
3. Add the Helm chart, refer to this [link](https://github.com/egovernments/DIGIT-DevOps/commit/339bc2674d68e654eacb3700ec1cc23e6105c429).
4. Deploy the latest build of vendor and FSM, refer to this [link](service-build-update/).
5. Sanitation worker depends on the individual  service. Refer to this [link](https://health.digit.org/platform/platform-services/individual-registry).
6. Deploy the latest build of individual service refer link#
7. Migrate all the drivers to individual using [script](driver-individual-migration-script.md)

### **UI Migration Changes**

1. Make sure UI MDMS changes are added from [#ui-related-mdms-files](mdms-changes.md#ui-related-mdms-files "mention").
2. Refer to the technical documentation for TQM UI to run UI [tqm-ui](../../product/functional-specifications/tqm-ui/ "mention")
3. Refer to the technical documentation for sanitation worker UI [sanitation-worker-ui](../../product/faecal-sludge-management-fsm/fsm-functional-specification/sanitation-worker-ui/ "mention")
4. Code PRs for referenceL
   1. [https://github.com/egovernments/SANITATION/pull/399](https://github.com/egovernments/SANITATION/pull/399)
   2. [https://github.com/egovernments/SANITATION/pull/408](https://github.com/egovernments/SANITATION/pull/408)
   3. [https://github.com/egovernments/SANITATION/pull/409](https://github.com/egovernments/SANITATION/pull/409)
