# Vendor Registry

## Overview

As part of the worker welfare v1.0, a new worker registry concept is being introduced. The creation of a worker, updation of details, searching and tagging a worker for different operations on sanitation programmes will be covered. We will leverage the Individual Registry for storing and querying details about a worker.&#x20;

The individual service is an enhanced version of the user service that houses data about individuals. The individual service is being re-used from [DIGIT Health](https://health.digit.org/).

Click [here](https://health.digit.org/platform/architecture/low-level-design/registries/individual) to access the Individual Service.

## Architecture Diagram

<figure><img src="../../../.gitbook/assets/Screenshot 2023-09-22 at 10.30.37 AM (1).png" alt=""><figcaption></figcaption></figure>

## Vendor Registry

#### Changes from Version 1.3.1 is 1.4.0

1. Change from driver concept to worker.
2. Deprecation of the driver table.
3. Backward compatibility for existing drivers (converting a driver user into an individual and mapping/backfilling to vendors).
4. Introducing worker vendor mapping.
5. Creation of workers directly using Individual registry APIs.

## API Specification

[Vendor\_Registration\_Contract.yaml](https://raw.githubusercontent.com/egovernments/SANITATION/sanitation\_v1.4\_api\_contracts/API-CONTRACTS/fsm/Vendor\_Registration\_Contract.yaml?token=GHSAT0AAAAAACGUKWUFSEN4KJFWGCJW6P5OZINGSVA)

## ER Diagram

<figure><img src="../../../.gitbook/assets/Screenshot 2023-09-22 at 9.46.21 AM.png" alt=""><figcaption></figcaption></figure>

## Sequence Diagram

#### **Create Worker**

<figure><img src="../../../.gitbook/assets/Screenshot 2023-09-22 at 9.47.13 AM.png" alt=""><figcaption></figcaption></figure>

#### **Update Vendor**

<figure><img src="../../../.gitbook/assets/Screenshot 2023-09-22 at 9.48.03 AM (1).png" alt=""><figcaption></figcaption></figure>
