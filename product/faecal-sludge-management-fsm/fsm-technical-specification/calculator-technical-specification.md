# Calculator Technical Specification

## Overview

FSM Calculator is a system that enables the FSM aAdmin to create billing slabs for the FSM application(s) with different combinations of propertytype, slum, and tank capacity, among others. It generates the demand after calculating the charges for the given application using the billing slabs already configured.

### Service Dependencies:

* billing-service
* mdms-service
* workflow-v2
* User-service
* fsm

## API Specification

[FSM-Calculator Swagger Link](https://editor.swagger.io/?url=https://raw.githubusercontent.com/AmanKumar-eGov/municipal-services/master/docs/fsm/v1.3/fsm-calculator.yaml)

## ​Data Model

<figure><img src="../../../.gitbook/assets/Screenshot 2023-04-25 at 9.48.35 AM.png" alt=""><figcaption></figcaption></figure>
