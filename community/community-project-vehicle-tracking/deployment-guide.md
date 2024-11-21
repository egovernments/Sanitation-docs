# Deployment Guide

## Build and Deployment of vehicle-tracker

## Jenkins Job Builder Configuration:

Configure a Jenkins job builder to automate the build and deployment process.

Configuration File:  build-config.yaml

\


| <p>  #Vehicle tracking web app<br>  - name: 'builds/SANITATION/vehicle-tracker'<br>    build:<br>      - work-dir: 'frontend/vehicle-tracker/map_web_app/route_map'<br>        image-name: 'vehicle-tracker'<br>        dockerfile: 'frontend/vehicle-tracker/map_web_app/docker/Dockerfile'</p> |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

\


## DockerFile And Jenkins Configuration:

Create a docker file for your application

File: Dockerfile

\


| <p># Docker flutter tags https://hub.docker.com/r/cirrusci/flutter/tags?page=1&#x26;name=1.16<br><br>FROM ghcr.io/cirruslabs/flutter:3.10.3 AS build<br>ARG WORK_DIR<br>WORKDIR /app<br># copy the project files<br>COPY ${WORK_DIR} .<br>RUN flutter doctor<br>RUN flutter pub get<br>RUN flutter build web<br># Create runtime image<br>FROM dwssio/nginx:mainline-alpine<br>ENV WEB_DIR=/var/web/vehicle-tracker<br>#RUN mkdir -p ${WEB_DIR}<br>COPY --from=build /app/build/web/ ${WEB_DIR}/<br>COPY --from=build /app/nginx.conf /etc/nginx/conf.d/default.conf</p> |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

\


File: Jenkinsfile

\


| <p>library 'ci-libs'<br><br>buildPipeline(configFile: './build/build-config.yml')</p> |
| ------------------------------------------------------------------------------------- |

\


## Nginx Configuration:

Configure the Nginx to serve the application

File: nginx.conf

\


| <p>server<br>{<br>  listen 80;<br>  underscores_in_headers on;<br>  server_tokens off;<br>  location /vehicle-tracker<br>  {<br>    root /var/web;<br>    index index.html index.htm;<br>    try_files $uri $uri/ /vehicle-tracker/index.html;<br>  }<br>}</p> |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

\
\


## Helm Chart Configuration:

Create a helm chart for deployment&#x20;

Files in the helm chart directory:

\


Chart.yaml

| <p>apiVersion: v2<br>name: vehicle-tracker<br>description: A Helm chart for Kubernetes<br><br># A chart can be either an 'application' or a 'library' chart.<br>#<br># Application charts are a collection of templates that can be packaged into versioned archives<br># to be deployed.<br>#<br># Library charts provide useful utilities or functions for the chart developer. They're included as<br># a dependency of application charts to inject those utilities and functions into the rendering<br># pipeline. Library charts do not define any templates and therefore cannot be deployed.<br>type: application<br><br># This is the chart version. This version number should be incremented each time you make changes<br># to the chart and its templates, including the app version.<br>version: 0.1.0<br><br># This is the version number of the application being deployed. This version number should be<br># incremented each time you make changes to the application.<br>appVersion: 1.16.0<br><br>dependencies:<br>- name: common<br>  version: 0.0.5<br>  repository: file://../../common</p> |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

\
\


values.yaml

| <p>    # Common Labels<br>labels:<br>  app: "vehicle-tracker"<br>  group: "web"<br><br># Ingress Configs<br>ingress:<br>  enabled: true<br>  context: "vehicle-tracker"<br>  namespace : egov<br><br># Init Containers Configs<br>initContainers: {}<br><br># Container Configs<br>image:<br>  repository: "vehicle-tracker"<br>replicas: "1"<br>httpPort: 80<br>healthChecks:<br>  enabled: true<br>  livenessProbePath: "/vehicle-tracker/"<br>  readinessProbePath: "/vehicle-tracker/"<br><br>extraVolumes: |<br>  - name: js-injection<br>    configMap:<br>      name: vehicle-tracker-js-injection<br>extraVolumeMounts: |<br>  - mountPath: /etc/nginx/conf.d/sub_filter.conf<br>    name: js-injection<br>    subPath: sub_filter.conf</p> |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

\
\


templates/Deployment.yaml

| <p># deployment.yaml<br>{{- template "common.deployment" . -}}</p> |
| ------------------------------------------------------------------ |

\


templates/Service.yaml

| <p># service.yaml<br>{{- template "common.service" . -}}</p> |
| ------------------------------------------------------------ |

\


templates/Ingress.yaml

| <p># ingress.yaml<br>{{- template "common.ingress" . -}}</p> |
| ------------------------------------------------------------ |

\


templates/subfilter-injection-configmap.yaml

| <p>{{- $envOverrides := index .Values (tpl .Chart.Name .) -}}<br>{{- $_ := set . "Values" (merge .Values $envOverrides) -}}<br>{{- if index .Values "custom-js-injection" -}}<br>apiVersion: v1<br>kind: ConfigMap<br>metadata:<br>  name: {{ .Chart.Name }}-js-injection<br>{{- if .Values.global.namespace }}<br>  namespace: {{ .Values.global.namespace }}<br>{{- else }}  <br>  namespace: {{ .Values.namespace }}<br>{{- end }} <br>data:<br>{{- index .Values "custom-js-injection" | nindent 2 }}<br>{{- end -}}</p> |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

\
\


Add the custom js injection config in the environment directory

\


| <p>vehicle-tracker:<br>  custom-js-injection: |<br>    sub_filter.conf: "<br>      sub_filter  '&#x3C;head>' '&#x3C;head><br>      &#x3C;script src=https://s3.ap-south-1.amazonaws.com/egov-dev-assets/globalConfigs.js type=text/javascript>&#x3C;/script><br>      ';"</p> |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

\
\


Push these changes to the DevOps repository in the desired environment.

## Run Jenkins Job:

Trigger the Jenkins job manually or set it up to run automatically on every push to the repository.

## Build and Deploy:

Jenkins will build the application using the Dockerfile, and then deploy it using the Helm chart to the desired environment.

\
\


For any more information check this repository:

Repo changes- [https://github.com/egovernments/SANITATION/blob/HLM-5602-vehicle-tracking-web/frontend/vehicle-tracker/map\_web\_app/docker/Dockerfile](https://github.com/egovernments/SANITATION/blob/HLM-5602-vehicle-tracking-web/frontend/vehicle-tracker/map\_web\_app/docker/Dockerfile)

\


DevOps changes-

[https://github.com/egovernments/DIGIT-DevOps/tree/unified-env/deploy-as-code/helm/charts/sanitation/vehicle-tracker](https://github.com/egovernments/DIGIT-DevOps/tree/unified-env/deploy-as-code/helm/charts/sanitation/vehicle-tracker)

\
\


## Technology Stack:

#### Frontend: flutter : version: 3.10.5

#### Backend: java, spring boot

