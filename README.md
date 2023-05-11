---
cover: .gitbook/assets/Sanitation Banner GIT.jpeg
coverY: 0
---

# Introducing DIGIT Sanitation

## Mission

Enabling Samaaj, Sarkar & Bazaar partners with a digital platform that would help ensure Zero deaths, disease, and environmental contamination resulting from poor sanitation - a reality for every citizen across the Global South.

DIGIT Sanitation aims to ensure zero untreated waste in 1,000 habitats in 1,000 days by catalysing open digital ecosystems.

## Overview

DIGIT Sanitation is an open-source web and mobile-enabled platform designed to digitisze operations in the waste management value chain, from collection to treatment, and provides the ability to drive coordination across multiple independent and disconnected stakeholders. This ensures that there is a continued chain of custody of waste throughout.&#x20;

According to a United Nations (UN) report, only 54% of the world population have access to safe sanitation. While there have been tremendous efforts from organisations in achieving SDG6, we believe that at the heart of the problems in sanitation are ineffective systems that fail to deliver. Hence, systems must be progressively reformed. To move habitats towards zero untreated waste, we will leverage the capabilities built by the Digital Infrastructure for Governance, Impact & Transformation (DIGIT), and ensure traceability of waste by enabling the ecosystem with the following features:

* Chain of custody: We will ensure a seamless and traceable chain of custody for waste. This will enable stakeholders to track waste from its source to its final destination, ensuring accountability and transparency in the waste management process.
* Actionable data: Our system will provide actionable data on waste management operations, which will enable stakeholders to make informed decisions. This data will be used to optimize waste collection and treatment processes, identify areas for improvement, and drive evidence-based decision-making.
* Code for innovation: We will foster innovation by providing a digital platform that encourages collaboration among stakeholders. Our system will facilitate the sharing of ideas, best practices, and innovative solutions for sanitation challenges, driving continuous improvement in the waste management ecosystem.

### Need for DIGIT Sanitation - Case for Platform&#x20;

Current digital efforts across geographies do not take a “whole of system view” and do not solve the cost of coordination and duplication issues. Each country/state also develops its own systems (MIS, apps, dashboards) individually for waste streams. Such siloed, solution-centric approaches and tools create a new set of problems and inefficiencies for countries:

* Higher costs and time: This is incurred on creating or procuring and maintaining these systems, including the onboarding cost of the same actors in each programme.
* Data exists in multiple systems: They are not interoperable, leading to duplication, inconsistencies, poor adoption by on-ground workers, and sub-optimal decision-making.
* Limited reusability and innovation: Data and capabilities are intertwined and ‘locked,’ making it extremely hard for the wider ecosystem to innovate and build upon.
* Sub-scale: The tools are not able to scale for the national population and across waste streams.

## Platform Scope

DIGIT Sanitation is built on the principles of societal platforms, envisioning a space where sanitation is supported by shared resources, curated knowledge, and evolving solutions that address the needs of the community. We recognise that the challenges of sanitation are systemic and require the collective efforts of all stakeholders to be effectively addressed. Drawing from our insights gained from our urban mission, we embrace the triple helix model, which emphasises partnerships among different stakeholders including civil society (samaaj), government (sarkaar), and industry/market (bazaar), to generate innovation through synergistic collaboration. Leveraging our experience in building large-scale public digital infrastructure, we are well-positioned to create the foundation for this ecosystem and drive progress in solving the most pressing sanitation issues. We believe that by fostering cooperation and collaboration among all stakeholders, we can create sustainable solutions that meet the needs of communities and contribute to the transformation of the sanitation landscape.

While sanitation requirements and solutions may vary among local governments, there are commonalities in the value chain of sanitation waste streams, such as Feacal Sludge Management, Solid Waste Management, Plastic Waste Management, etc. These value chains typically involve steps such as generation, containment, collection, transport, treatment, and disposal/reuse. These similarities provide an opportunity to abstract and digitize various components of the service value chain, with the potential to encode standards and enable data-driven visibility into sanitation services.

The DIGIT Sanitation platform is specifically designed to allow for contextualisation and reuse of components across different waste streams and geographies. By incorporating standards into the platform and leveraging data registries and reusable building blocks in the technology stack, applications can be developed more efficiently and quickly at the solution layer, resulting in lower costs and faster implementation. This approach enables flexibility and scalability in addressing diverse sanitation needs, while also promoting interoperability and consistency in the digital solutions deployed. By leveraging the DIGIT Sanitation platform, stakeholders can build innovative applications tailored to local contexts, while adhering to standardised components and data structures, leading to more effective and sustainable sanitation services.

Following is a glimpse of how this would work:

<figure><img src=".gitbook/assets/Screenshot 2023-04-20 at 11.12.55 AM.png" alt=""><figcaption></figcaption></figure>

The above image illustrates the core infrastructure services, and the enabling services that are built/configured for a Feacal Sludge Management (FSM) solution with the following functionality:

1. Allowing citizens to request for septic tank desludging services.
2. Scheduling desludging services for a certain set of property types/localities, etc.
3. Automated or manual assignment of vendors to perform requests.
4. Tracking sludge from collection to disposal at a treatment plant using internet of things (IoT).
5. Notifications to stakeholders at each point in the workflow.
6. Dashboards and reports.

Now, consider that instead of FSM, a solution needs to be built for Solid Waste Management:

<figure><img src=".gitbook/assets/Screenshot 2023-04-20 at 11.13.52 AM.png" alt=""><figcaption></figcaption></figure>

The same set of infrastructure and enabling services could be used to configure the following functionalities:

1. Scheduling the collection of waste based on different categories.
2. Automated or manual assignment of vendors to perform requests.
3. Tracking adherence to the schedule.
4. Tracking waste movement from pickup to disposal at a treatment facility.
5. Notifications to stakeholders at each point in the workflow.
6. Dashboards and reports.

Further, only an additional service for segregation monitoring would have to be built.

To illustrate this further, imagine building a solution for sanitation worker welfare:

<figure><img src=".gitbook/assets/Screenshot 2023-04-20 at 11.14.52 AM.png" alt=""><figcaption></figcaption></figure>

The same set of services can be used here as well, with the addition of a few components.The DIGIT Sanitation platform is built leveraging the  [DIGIT Core Services](https://core.digit.org/platform/core-services), which are customised into the following key building blocks:

1. Service Request Management

* Define pricing
* Record service requests
* Assign and manage service requests
* Provide subsidies
* Calculate service fees
* Track status
* Collect feedback

2. Transport Management

* Schedule pickup
* Assign vehicles and drivers
* Track status

3. Billing and Payments

* Generate demand
* Generate receipts
* Online payment gateway

4. Notifications&#x20;

* SMS
* In app

5. Service Delivery Monitoring

* Dashboards
* Reports
