# PQM Scheduler

## Overview

This pqm scheduler is a cronjob scheduler for scheduling tests. It runs based on environment configuration. It triggers multiple the schedule API from PQM-Service to generate the Tests on the basis of Test Standards present in MDMS.

### Dependency

* MDMS
* User
* PQM-Service

### Key Functionalities

* It creates tests based on MDMS Test Standards using pqm-service /v1/\_scheduler API.

### Sequence Diagram

Create Lab Test (CronJob)

<figure><img src="https://lh7-us.googleusercontent.com/YFndBD-GojeFQvGHs8IuF-kjESGEFugWj6G4VoXoeK5_IYigPQPnu3Qf8hF1crHpuIkmL7del7Mm1c2zBikxyhzRfLRQp6yQYPtoBSFbAw9hkfwromVUjLd25znXoHguK7NABYAKoWOFvVAacEV7rP4" alt=""><figcaption></figcaption></figure>
