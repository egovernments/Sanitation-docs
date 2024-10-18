# Vehicle registry devops setup

## Deployment Details

1. Deploy the latest version of the vehicle.
2. Add vehicle-persister.yml file in config folder in git and add that path in persister . (The file path is to be added in environment yaml file in param called persist-yml-path ) and restart egov-persister-service.
3. Integrate the following below changes in vehicle-persister.yml\
   [SAN-1063 and 1064 (SAN-1158 and SAN-1157) -  Persister file - Vehicle… · egovernments/configs@2e53637](https://github.com/egovernments/configs/commit/2e536376408a0f09a2afe03c478201f5d81edfe4)
4. [SM-801 removing extra tab space by madan-kumar-eGov · Pull Request #2238 · egovernments/configs](https://github.com/egovernments/configs/pull/2238/files)
5. [SM-801 vehicle not able to create in uat by madan-kumar-eGov · Pull Request #2240 · egovernments/configs](https://github.com/egovernments/configs/pull/2240/files)

### **Infra Ops Configuration**

Configurations that we can manage through values.yml vehicle in infraops repo are listed below. \
values.yml for the vehicle can be found.

| Description                                                                    | name in values.yml                                | Current Value                                                |
| ------------------------------------------------------------------------------ | ------------------------------------------------- | ------------------------------------------------------------ |
| id-gen host, to generate the application number                                | EGOV\_IDGEN\_HOST                                 | egov-idgen from egov-service-host                            |
| mdms service host                                                              | EGOV\_MDMS\_HOST                                  | egov-mdms-service from egov-service-host                     |
| workflow v2 service host                                                       | WORKFLOW\_CONTEXT\_PATH                           | egov-workflow-v2 from egov-service-host                      |
| user service host, to get the locale data                                      | EGOV\_USER\_HOST                                  | egov-user from egov-service-host                             |
| Kafka Consumer Group                                                           | SPRING\_KAFKA\_CONSUMER\_GROUP\_ID                | egov-vehicle-services                                        |
| kafka topic to which service push data to save new vehicle application         | PERSISTER\_SAVE\_VEHICLE\_TOPIC                   | save-vehicle-application                                     |
| kafka topic to which service push data of the vehicleTrip to save              | PERSISTER\_SAVE\_VEHICLE\_TRIP\_TOPIC             | save-vehicle-trip                                            |
| kafka topic to which service push data of the vehicleTrip to update            | PERSISTER\_UPDATE\_VEHICLE\_TRIP\_TOPIC           | update-vehicle-trip                                          |
| kafka topic to which service push data of the vehicleTrip to update the status | PERSISTER\_UPDATE\_VEHICLE\_TRIP\_WORKFLOW\_TOPIC | update-workflow-vehicle-trip                                 |
| VehicleTrip Appilcatiion Number format\`                                       | egov.idgen.vehicle.trip.applicationNum.format     | "\[CITY.CODE]-VT-\[cy:yyyy-MM-dd]-\[SEQ\_EGOV\_VEHICLETRIP]" |

**Configurations sample in Values.yml**

```
egov.idgen.vehicle.trip.applicationNum.format: "[CITY.CODE]-VT-[cy:yyyy-MM-dd]-[SEQ_EGOV_VEHICLETRIP]"

# Additional Container Envs
env: |
  - name: EGOV_IDGEN_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-idgen
  - name: EGOV_HRMS_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-hrms
  - name: EGOV_MDMS_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-mdms-service
  - name: EGOV_USER_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-user
  - name: WORKFLOW_CONTEXT_PATH
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-workflow-v2
  - name: WORKFLOW_TRANSITION_PATH
    value: "egov-workflow-v2/egov-wf/process/_transition"
  - name: EGOV_IDEN_VEHICLE_TRIP_APPLICATIONNUM_FORMAT
    value: "[CITY.CODE]-VT-[cy:yyyy-MM-dd]-[SEQ_EGOV_VEHICLETRIP]"
  - name: SPRING_KAFKA_CONSUMER_GROUP_ID
    value: egov-vehicle-services
  - name: PERSISTER_SAVE_VEHICLE_TOPIC
    value: save-vehicle-application
  - name: PERSISTER_UPDATE_VEHICLE_TOPIC
    value: update-vehicle-application
  - name: PERSISTER_SAVE_VEHICLE_TRIP_TOPIC
    value: save-vehicle-trip
  - name: PERSISTER_UPDATE_VEHICLE_TRIP_TOPIC
    value: update-vehicle-trip
  - name: PERSISTER_UPDATE_VEHICLE_TRIP_WORKFLOW_TOPIC
    value: update-workflow-vehicle-trip 
  - name: SPRING_KAFKA_PRODUCER_KEY_SERIALIZER
    value: org.apache.kafka.common.serialization.StringSerializer
  - name: SPRING_KAFKA_PRODUCER_VALUE_SERIALIZER
    value: org.springframework.kafka.support.serializer.JsonSerializer
  - name: JAVA_OPTS
    value: {{ index .Values "heap" | quote }}
  - name: JAVA_ARGS
    value: {{ index .Values "java-args" | quote }}
  - name: SERVER_PORT
    value: "8080"
  - name: SECURITY_BASIC_ENABLED
    value: "false"  
  - name: MANAGEMENT_SECURITY_ENABLED
    value: "false"
  {{- if index .Values "tracing-enabled" }}
  - name: TRACER_OPENTRACING_ENABLED
    value: "true" 
  {{- end }}
```

[DIGIT-DevOps/values.yaml at master · egovernments/DIGIT-DevOps](https://github.com/egovernments/DIGIT-DevOps/blob/master/deploy-as-code/helm/charts/sanitation/vehicle/values.yaml)&#x20;
