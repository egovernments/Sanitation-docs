# PQM Anomaly Finder

## **Overview**

The Process Quality Management (PQM) anomaly finder service helps in monitoring anomalies in process quality and notifies the concerned user groups.&#x20;

### [**MDMS**](https://core.digit.org/platform/core-services/mdms-master-data-management-service)

MDMS changes for user-event in MDMS, and then restart mdms-service.

Path: data/pg/ACCESSCONTROL-ACTIONS-TEST/actions-test.json - file [link](https://github.com/egovernments/egov-mdms-data/commit/a1a9dc388b490b210998783578707f6f17dd7c43)

Path: data/pg/ACCESSCONTROL-ROLEACTIONS/roleactions.json - file [link](https://github.com/egovernments/egov-mdms-data/commit/119f037c96cf13e99937593fc28f252b7f56bdf9)

### **Persister**

Add below file in the given path and then restart persister service in the respective environment.

Path: egov-persister/pqm-anomaly-finder-persister.yaml - [Persister file link](https://github.com/egovernments/configs/blob/UNIFIED-DEV/egov-persister/pqm-anomaly-finder-persister.yaml)

### **Indexer**

Add below file in the given path and then restart indexer service in the respective environment.

Path: egov-indexer/pqm-anomaly-finder-indexer.yml - [Indexer file link](https://github.com/egovernments/configs/blob/UNIFIED-DEV/egov-indexer/pqm-anomaly-finder-indexer.yml)

### **Deployment**

Add the file which is given below pr in the given path and then start deployment

Path: deploy-as-code/helm/charts/sanitation/pqm-anomaly-finder

[https://github.com/egovernments/DIGIT-DevOps/tree/unified-env/deploy-as-code/helm/charts/sanitation/pqm-anomaly-finder](https://github.com/egovernments/DIGIT-DevOps/tree/unified-env/deploy-as-code/helm/charts/sanitation/pqm-anomaly-finder)

[https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/environments/sanitation.yaml#L140C1-L141C1](https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/environments/sanitation.yaml#L140C1-L141C1)

[https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/environments/sanitation.yaml#L230C1-L234C26](https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/environments/sanitation.yaml#L230C1-L234C26)

Path: build/build-config.yml - file [link](https://github.com/egovernments/SANITATION/commit/576b1bb9531a2080e039d17af9d3c6a6c63d76e7)

**For re-indexing refer this** [link](https://app.gitbook.com/o/-MEQmzNGXk5ajuZujG7E/s/LpfYJCGZoBEmcFf9yWTh/\~/changes/144/product/treatment-quality-monitoring-tqm/pqm-technical-specification/legacy-re-indexing-the-pqm-data#pqm-anomaly-reindexing)
