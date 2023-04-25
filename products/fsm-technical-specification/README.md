# FSM Technical Specification

## Overview

Faecal Sludge Management (FSM) is a system that enables citizens to raise a request for septic tank cleaning with their urban local bodies (ULBs) directly or for reaching out to a ULB counter. Citizens can track the application, make a payment for the charges and rate the service.&#x20;

### Service Dependencies:

* billing-service
* mdms-service
* workflow-v2
* boundary-service
* user-service
* idgen-service
* user-events
* collection-service
* notification-service
* vendor
* vehicle
* fsm-calculator
* egov-url-shortener
* collection-service
* pdf-service

## API Specification

[FSM Swagger Link](https://editor.swagger.io/?url=https://raw.githubusercontent.com/AmanKumar-eGov/municipal-services/master/docs/fsm/v1.3/fsm.yaml)

## Data Model

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-25 at 9.09.51 AM.png" alt=""><figcaption></figcaption></figure>

## Web Sequence Diagrams

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-25 at 9.13.04 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-25 at 9.14.15 AM.png" alt=""><figcaption></figcaption></figure>
