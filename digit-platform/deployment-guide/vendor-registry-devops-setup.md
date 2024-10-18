# Vendor registry devops setup

## Deployment Details <a href="#deployment-details" id="deployment-details"></a>

1. Deploy the latest version of the vendor.
2. Add vendor-persister.yml file in the config folder in git and add that path in persister  (the file path is to be added in the environment yaml file in param called persist-yml-path), and restart egov-persister-service.
3. Integrate the following below changes in vendor-persister.yml [SAN-1063 and 1064 (SAN-1158 and SAN-1157) -  Persister file - Vendor … · egovernments/configs@95dd26f](https://github.com/egovernments/configs/commit/95dd26f926ec44d07448926ee4b6b7e031847a57).
4. [SM-801 Not able to create vendor in UAT using api by madan-kumar-eGov · Pull Request #2237 · egovernments/configs](https://github.com/egovernments/configs/pull/2237/files).

### **Infra Ops Configuration**

Configurations that we can manage through values.yml vehicle in infra-ops repo are listed below.\
values.yml for the vehicle is available below.\


| Description                                               | Name in values.yml                 | Current value                            |
| --------------------------------------------------------- | ---------------------------------- | ---------------------------------------- |
| Kafka Consumer Group                                      | SPRING\_KAFKA\_CONSUMER\_GROUP\_ID | egov-vendor-services                     |
| Kafka topic to which service push data to save new vendor | PERSISTER\_SAVE\_VENDOR\_TOPIC     | save-vendor-application                  |
| MDMS service host                                         | EGOV\_MDMS\_HOST                   | egov-mdms-service from egov-service-host |
| Vehicle service host                                      | EGOV\_VEHICLE\_HOST                | vehicle from egov-service-host           |
| User service host                                         | EGOV\_USER\_HOST                   | egov-user-service from egov-service-host |
| Location service Host                                     | EGOV\_LOCATION\_HOST               | egov-location from egov-service-host     |

**Configurations sample in Values.yml**

```
# Common Labels
labels:
  app: "vendor"
  group: "rainmaker"


# Ingress Configs
ingress:
  enabled: true
  zuul: true
  context: "vendor"


# Init Containers Configs
initContainers:
  dbMigration:
    enabled: true
    schemaTable: "vendor_schema"
    image:
      repository: "vendor-db"


# Container Configs
image:
  repository: "vendor"
replicas: "1"
healthChecks:
  enabled: true
  livenessProbePath: "/vendor/health"
  readinessProbePath: "/vendor/health"
appType: "java-spring"
tracing-enabled: true
heap: "-Xmx256m -Xms256m"
java-args: "-Dspring.profiles.active=monitoring"


# Additional Container Envs
env: |
  - name: EGOV_VEHICLE_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: vehicle
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
  - name: EGOV_LOCATION_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-location
  - name: EGOV_HRMS_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-hrms
  - name: SPRING_KAFKA_CONSUMER_GROUP_ID
    value: egov-vendor-services
  - name: PERSISTER_SAVE_VENDOR_TOPIC
    value: save-vendor-application
  - name: PERSISTER_UPDATE_VENDOR_TOPIC
    value: update-vendor-application
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
