---
description: Learn how to setup and configure FSM service
---

# FSM Core Service Configuration

### Overview <a href="#overview" id="overview"></a>

Faecal sludge management (FSM) is a system that enables citizens to raise a request for septic tank cleaning with their urban local bodies (ULBs) directly or reaching out to the ULB counter. Citizens can track the application, make a payment for the charges and rate the service. This document contains details on how to set up FSM and describes the functionalities it provides. The document contains the details about the feature enhancements being released as part of FSM v1.3.

### Pre-requisites <a href="#pre-requisites" id="pre-requisites"></a>

Before you proceed with the configuration, make sure the following pre-requisites are met -

* _Java 8_
* Kafka server is up and running
* egov-persister service is running and has fsm-persister config path added in it
* PSQL server is running and a database is created to store FSM Application data
* _(Optional)_ Indexer config for FSM is added in egov-indexer yaml paths to index the generated data. An index is required for data visualisation in kibana or in DSS.
* Following services should be up and running:
  * egov-user
  * egov-workflow-v2
  * egov-perister
  * egov-localisation
  * egov-notification-sms
  * egov-mdms
  * egov-idgen
  * egov-url-shortening
  * vehicle
  * vendor
  * fsm-calculator
  * billing-service
  * collection-services

### Key Functionalities <a href="#key-functionalities" id="key-functionalities"></a>

* Citizens can file, track and rate the application for cleaning septic tank
* ULB Employee can file application for cleaning septic tank on behalf of Citizen
* ULB Employee can assign DSO to the given application with possible service date
* DSO can accept or reject the application
* DSO or ULB Employee can Complete the FSM Application after cleaning the septic tank
* FSM Admin in ULB can cancel the application at any stage before completing the application
* ULB Employee or Admin can view the audit log of the given application
* Capture citizen gender information if not present or pre-populate the gender information when Citizen is creating FSM application.
* Add citizen's choice for payment
* Introducing Pre pay and Post pay service
* Post Pay service : Workflow changes (Desludging Application and Vehicle Trip)
* Post Pay service: Employee Flow Enhancements
* Add payment selection for DSO
* Post Pay service: Number of trips is made editable and price calculation will be now based on number of trips entered by the DSO. &#x20;
* Capture DSO and FSTPO gender
* Show citizen gender on FSM DSS
* Select vehicle capacity instead of vehicle make.
* Citizen Notifications | Payment Options | Timeline Enhancements
* FSTPO Vehicle Log Inbox Enhancements
* FSTPO can decline the vehicle trip
* Add owner attribute for vehicle
* Add ULB contact details in FSM application flow
* DSO can edit pit and property usage details
* Show vehicle trip status in employee inbox along with Desludging application
* Unrestricted assignment of service requests to a single vehicle&#x20;
* Vehicle logging at FSTP decoupled from FSM module
* Photo and attachment view in the application of the ULB employee UI
* Dashboard enhancement
* Advance Pay service: Employee Flow Enhancements
* Introduce two new workflow in the system.

&#x20;     \- FSM\_ADVANCE\_PAY\_SERVICE and FSM\_ZERO\_PAY\_SERVICE .

* Advance Pay service: Number of trips is made editable(increase or decrease based on the requirement) and price calculation will be now based on number of trips entered by the DSO or ULB. &#x20;
* Allowed to pay part payment while creating the application.
* ULB and DSO are allowed to decrease the number of trips if not required and if full payment is not done.
* ULB and DSO are allowed to increase or decrease the number of  trips n number of times.
* With the updated number of trips, an updated bill will be generated .
* Delink the payment from dso in progress state .
* Zero Pay service: Employee Flow Enhancements
* Zero Pay service: System now skip the collection and will not generate the demand for zero price application.
* Demand Generation Process: Generating demand on every time when the trip is update.
* Demand Generation Process: Added validation not to complete the application from ulb side before completing the all payment.
* Enhancement of FSM Receipt

### Deployment Details <a href="#deployment-details" id="deployment-details"></a>

1. Deploy the latest version of fsm
2. Add fsm-persister.yml file in config folder in git and add that path in persister . (The file path is to be added in environment yaml file in param called persist-yml-path ) and restart the egov-persister service.
3. If index are to be created add the indexer config path in indexer service. (The file path is to be added in environment yaml file in param called egov-indexer-yaml-repo-path) and restart egov-indexer service.

### Configuration Details <a href="#configuration-details" id="configuration-details"></a>

Make changes in config accordingly and restart the pdf-services.

1 . pdf-service/format-config/fsm-receipt.json

[#SM-1265 FSM V1.2: ULB collecting advance Receipt Page · egovernments/configs@57259f7](https://github.com/egovernments/configs/commit/57259f78f5e8974a6e5039c8030d44f5a0589de7)

[#SM-1265 pdf  Receipt table alignment · egovernments/configs@1e0625e](https://github.com/egovernments/configs/commit/1e0625e3cdfe06a7a58281e26f5d0bf8a62fecfb)

[https://github.com/egovernments/configs/commit/1b3c14bfcf74ec23e30aed1910dfe0d016439543](https://github.com/egovernments/configs/commit/1b3c14bfcf74ec23e30aed1910dfe0d016439543)

[https://github.com/egovernments/configs/commit/f6f7f513799dfcae80817fe1f1866d0084291006](https://github.com/egovernments/configs/commit/f6f7f513799dfcae80817fe1f1866d0084291006)

2 . pdf-service/data-config/fsm-receipt.json

[#SM-1265 FSM V1.2: ULB collecting advance Receipt Page · egovernments/configs@ed9220a](https://github.com/egovernments/configs/commit/ed9220ab82d8732e4c50f3b9a4bfb17ec0756cd9)

[https://github.com/egovernments/configs/commit/2a221ad39756c2ca4476c0669c2f4f79c3ce958e](https://github.com/egovernments/configs/commit/2a221ad39756c2ca4476c0669c2f4f79c3ce958e)

[https://github.com/egovernments/configs/commit/a07318256f21240df71f87af21acd3dc56fb1118](https://github.com/egovernments/configs/commit/a07318256f21240df71f87af21acd3dc56fb1118)

[https://github.com/egovernments/configs/commit/e307007a6e9f69f32134caac7d3b571411dfa840](https://github.com/egovernments/configs/commit/e307007a6e9f69f32134caac7d3b571411dfa840)

egov-persister/fsm-persister.yaml

[#807 updating advance amount column · egovernments/configs@413c9d1](https://github.com/egovernments/configs/commit/413c9d158e2afcd312a2d59cd04cae7315566f5a)

[https://github.com/egovernments/configs/commit/89ab16cc3c58d161183a58e85d4d9fdbe32a67f5](https://github.com/egovernments/configs/commit/89ab16cc3c58d161183a58e85d4d9fdbe32a67f5)

[https://github.com/egovernments/configs/commit/4c3acfe57d9ef6770a814d9e3d8bd88493e5c4bb](https://github.com/egovernments/configs/commit/4c3acfe57d9ef6770a814d9e3d8bd88493e5c4bb)

#### MDMS Configuration <a href="#mdms-configuration-hardbreak" id="mdms-configuration-hardbreak"></a>

Add master data in MDMS service with module name as FSM and restart the egov-mdms-service  Following is some sample master data for Application Channel (Source).

```
{
    "tenantId": "pb",
    "moduleName": "FSM",
    "ApplicationChannel": [
        {
            "name": "Telephone",
            "code": "TELEPHONE",
            "active": true,
            "citizenOnly":false
        },
        {
            "name": "Counter",
            "code": "COUNTER",
            "active": true,
            "citizenOnly":false
        },
        {
            "name": "Online",
            "code": "ONLINE",
            "active": true,
            "citizenOnly":true
        }
    ]
}
```

Checklist (Checklist to be answered by a citizen while rating)

```
{
	"tenantId": "pb",
	"moduleName": "FSM",
	"CheckList": [{
			"code": "SPILAGE",
			"active": true,
			"required": true,
			"type": "SINGLE_SELECT",
			"options": [
				"YES",
				"NO",
				"NA"
			]
		},
		{
			"code": "SAFETY_GEARS_USED",
			"active": true,
			"type": "MULTI_SELECT",
			"required": true,
			"options": [
				"EYE_GEAR",
				"HAND_GLOVES",
				"NOSE_MASK"
			]
		},
		{
			"code": "NUMBER_OF_TRIPS",
			"active": true,
			"type": "DROP_DOWN",
			"required": false,
			"options": [
				"1",
				"2",
				"3",
				"4",
				"5",
				"6",
				"7",
				"8",
				"9",
				"10"
			]
		}
	]
}
```

Config (Configuration at the application level)

```
{
    "tenantId": "pb",
    "moduleName": "FSM",
    "Config": [
        {
            "code":"noOfTrips",
            "override":true,
            "default":1,
            "active":true,
            "description":"override:true indicates, noOfTrips poperty is allowed to override in FSM."
        },
        {
            "code":"additionalDetails.tripAmount",
            "override":false,
            "active":true,
            "description":"override:true indicates, tripAmount poperty is allowed to override in FSM."
        },
        {
            "code":"slumName",
            "override":true,
            "active":true,
            "description":"override:true indicates, tripAmount poperty is allowed to override in FSM."
        },
        {
            "code":"ALLOW_MODIFY",
            "WFState":"CREATED",
            "override":[
                "propertyUsage",
                "vehicleType",
                "sanitationtype",
                "address.pincode",
                "address.city",
                "address.locality",
                "address.street",
                "address.doorNo",
                "address.landmark",
                "pitDetail"
            ],
            "active":true,
            "description":"properties in override allowed to modify when FSM application moving from CREATED Status to next status."
        }
        
    ]
}
```

FSTP Plant Info (FSTP information for each city)

```
{
    "tenantId": "pb",
    "moduleName": "FSM",
    "FSTPPlantInfo": [
        {
            "PlantCode": "AMR001",
            "PlantName": "Amritsar FSTP",
            "active": true,
            "PlantType":"FSTP",
            "PlantLocation":"Amritsar",
            "PlusCode":"JQ2R+7G Khapar Kheri, Punjab",
            "PlantOperationalTimings":"10.00am-08.00pm",
            "PlantOperationalCapacityKLD":"50",
            "ULBS":"pb.jalandhar,pb.amritsar,pb.nayagaon"
        },
        {
            "PlantCode": "MOH002",
            "PlantName": "Mohali SeTPP",
            "active": true,
            "PlantType":"SeTP",
            "PlantLocation":"Mohali",
            "PlusCode":"MPFQ+V2 Sahibzada Ajit Singh Nagar, Punjab",
            "PlantOperationalTimings":"10.00am-06.00pm",
            "PlantOperationalCapacityKLD":"100",
            "ULBS":"pb.mohali,pb.phagwara,pb.nawanshahr,pb.derabassi"
        }
    ]
}
```

Pit Type (Type of pit)

```
{
    "tenantId": "pb",
    "moduleName": "FSM",
    "PitType": [
        {
            "name": "Conventional septic tank",
            "code": "CONVENTIONAL_SPECTIC_TANK",
            "active": true,
            "dimension":"lbd"
        },
        {
            "name": "Septic tank with soak pit",
            "code": "SEPTIC_TANK_WITH_SOAK_PIT",
            "active": true,
            "dimension":"dd"
        }
    ]
}
```

Property Type

```
{
  "tenantId": "pb",
  "moduleName": "FSM",
  "PropertyType": [
    {
      "name": "Residential",
      "code": "RESIDENTIAL",
      "active": true,
      "minAmount":"100",
      "maxAmount":"500"
    },
     {
      "name": "Independent House",
      "code": "RESIDENTIAL.INDEPENDENT_HOUSE",
      "active": true,
      "propertyType": "RESIDENTIAL",
      "minAmount":"100",
      "maxAmount":"300"
    },
    {
      "name": "Apartment",
      "code": "RESIDENTIAL.APARTMENT",
      "active": true,
      "propertyType": "RESIDENTIAL",
      "minAmount":"400",
      "maxAmount":"600"
    },
    {
      "name": "Row Houses",
      "code": "RESIDENTIAL.ROW_HOUSES",
      "active": true,
      "propertyType": "RESIDENTIAL",
      "minAmount":"700",
      "maxAmount":"900"
    },
    {
      "name": "Commercial",
      "code": "COMMERCIAL",
      "active": true,
      "minAmount":"2000",
      "maxAmount":"5000"
    },
    {
      "name": "Community Toilets",
      "code": "COMMERCIAL.COMMUNITY_TOILETS",
      "active": true,
      "propertyType": "COMMERCIAL",
      "minAmount":"1000",
      "maxAmount":"1200"
    },
    {
      "name": "Hotel",
      "code": "COMMERCIAL.HOTEL",
      "active": true,
      "propertyType": "COMMERCIAL",
      "minAmount":"1300",
      "maxAmount":"1500"
    },
    {
      "name": "Restaurant",
      "code": "COMMERCIAL.RESTAURANT",
      "active": true,
      "propertyType": "COMMERCIAL",
      "minAmount":"1600",
      "maxAmount":"1800"
    },
    {
      "name": "Shopping Mall",
      "code": "COMMERCIAL.SHOPPING_MALL",
      "active": true,
      "propertyType": "COMMERCIAL",
      "minAmount":"1900",
      "maxAmount":"2100"
    },
    {
      "name": "Community hall",
      "code": "COMMERCIAL.COMMUNITY_HALL",
      "active": true,
      "propertyType": "COMMERCIAL",
      "minAmount":"2200",
      "maxAmount":"2500"
    },
    {
      "name": "Bank",
      "code": "COMMERCIAL.BANK",
      "active": true,
      "propertyType": "COMMERCIAL",
      "minAmount":"2600",
      "maxAmount":"2800"
    },
    {
      "name": "Private office",
      "code": "COMMERCIAL.PRIVATE_OFFICE",
      "active": true,
      "propertyType": "COMMERCIAL",
      "minAmount":"2900",
      "maxAmount":"3200"
    },
    {
      "name": "Market",
      "code": "COMMERCIAL.MARKET",
      "active": true,
      "propertyType": "COMMERCIAL",
      "minAmount":"3300",
      "maxAmount":"3500"
    },
    {
      "name": "Hostel",
      "code": "COMMERCIAL.HOSTEL",
      "active": true,
      "propertyType": "COMMERCIAL",
      "minAmount":"3600",
      "maxAmount":"3900"
    },
    {
      "name": "Warehouse",
      "code": "COMMERCIAL.WAREHOUSE",
      "active": true,
      "propertyType": "COMMERCIAL",
      "minAmount":"400",
      "maxAmount":"4200"
    },
    {
      "name": "Petrol pumps",
      "code": "COMMERCIAL.PETROL_PUMPS",
      "active": true,
      "propertyType": "COMMERCIAL",
      "minAmount":"4300",
      "maxAmount":"4500"
    },
    {
      "name": "Resort",
      "code": "COMMERCIAL.RESORT",
      "active": true,
      "propertyType": "COMMERCIAL",
      "minAmount":"4600",
      "maxAmount":"4800"
    },
    {
      "name": "Theme park",
      "code": "COMMERCIAL.THEME_PARK",
      "active": true,
      "propertyType": "COMMERCIAL",
      "minAmount":"4900",
      "maxAmount":"5100"
    },
    {
      "name": "Sports center",
      "code": "COMMERCIAL.SPORTS_CENTER",
      "active": true,
      "propertyType": "COMMERCIAL",
      "minAmount":"5200",
      "maxAmount":"5500"
    },
     {
      "name": "Institutional",
      "code": "INSTITUTIONAL",
      "active": true,
      "minAmount":"1000",
      "maxAmount":"3000"
    },
     {
      "name": "Temple",
      "code": "INSTITUTIONAL.TEMPLE",
      "active": true,
      "propertyType": "INSTITUTIONAL",
      "minAmount":"5600",
      "maxAmount":"5900"
    },
     {
      "name": "Mosque",
      "code": "INSTITUTIONAL.MOSQUE",
      "active": true,
      "propertyType": "INSTITUTIONAL",
      "minAmount":"6000",
      "maxAmount":"6200"
    },
     {
      "name": "Church",
      "code": "INSTITUTIONAL.CHURCH",
      "active": true,
      "propertyType": "INSTITUTIONAL",
      "minAmount":"6300",
      "maxAmount":"6500"
    },
     {
      "name": "Gurudwara",
      "code": "INSTITUTIONAL.GURUDWARA",
      "active": true,
      "propertyType": "INSTITUTIONAL",
      "minAmount":"6600",
      "maxAmount":"6800"
    },
     {
      "name": "Monastery",
      "code": "INSTITUTIONAL.MONASTERY",
      "active": true,
      "propertyType": "INSTITUTIONAL",
      "minAmount":"6900",
      "maxAmount":"7200"
    },
     {
      "name": "School",
      "code": "INSTITUTIONAL.SCHOOL",
      "active": true,
      "propertyType": "INSTITUTIONAL",
      "minAmount":"7300",
      "maxAmount":"7500"
    },
     {
      "name": "College",
      "code": "INSTITUTIONAL.COLLEGE",
      "active": true,
      "propertyType": "INSTITUTIONAL",
      "minAmount":"7600",
      "maxAmount":"7900"
    },
     {
      "name": "University",
      "code": "INSTITUTIONAL.UNIVERSITY",
      "active": true,
      "propertyType": "INSTITUTIONAL",
      "minAmount":"8000",
      "maxAmount":"8200"
    },
     {
      "name": "Anganwadi",
      "code": "INSTITUTIONAL.ANGANWADI",
      "active": true,
      "propertyType": "INSTITUTIONAL",
      "minAmount":"8300",
      "maxAmount":"8500"
    },
     {
      "name": "Training Institutes",
      "code": "INSTITUTIONAL.TRAINING_INSTITUTES",
      "active": true,
      "propertyType": "INSTITUTIONAL",
      "minAmount":"8600",
      "maxAmount":"8800"
    },
     {
      "name": "Hospital",
      "code": "INSTITUTIONAL.HOSPITAL",
      "active": true,
      "propertyType": "INSTITUTIONAL",
      "minAmount":"8900",
      "maxAmount":"9200"
    },
     {
      "name": "Nursing home",
      "code": "INSTITUTIONAL.NURSING_HOME",
      "active": true,
      "propertyType": "INSTITUTIONAL",
      "minAmount":"9300",
      "maxAmount":"9500"
    },
     {
      "name": "Community health center",
      "code": "INSTITUTIONAL.COMMUNITY_HEALTH_CENTER",
      "active": true,
      "propertyType": "INSTITUTIONAL",
      "minAmount":"9400",
      "maxAmount":"9600"
    },
     {
      "name": "Jail",
      "code": "INSTITUTIONAL.JAIL",
      "active": true,
      "propertyType": "INSTITUTIONAL",
      "minAmount":"9700",
      "maxAmount":"1000"
    },
     {
      "name": "Police station",
      "code": "INSTITUTIONAL.POLICE_STATION",
      "active": true,
      "propertyType": "INSTITUTIONAL",
      "minAmount":"10100",
      "maxAmount":"10500"
    }
  
  ]
}
```

Slum (Slums mapped to the locality of the city)

```
{
	"tenantId": "pb",
	"moduleName": "FSM",
	"Slum": [{
			"code": "SL0001",
			"active": true,
			"name": "Kathagada juanga sahi",
			"locality": "SUN20"
		},
		{
			"code": "SL0002",
			"active": true,
			"name": "Kathagada Parbatia Sahi",
			"locality": "SUN20"
		},
		{
			"code": "SL0003",
			"active": true,
			"name": "Gangadhar Sahi",
			"locality": "SUN35"
		},
		{
			"code": "SL0004",
			"active": true,
			"name": "Pandab Nagar",
			"locality": "SUN35"
		},
		{
			"code": "SL0005",
			"active": true,
			"name": "Haridakhandi Harijana sahi",
			"locality": "SUN35"
		},
		{
			"code": "SL0006",
			"active": true,
			"name": "Haridakhandi Kadalibada Sahi",
			"locality": "SUN55"
		},
		{
			"code": "SL0007",
			"active": true,
			"name": "Haridakhandi Bada sahi",
			"locality": "SUN55"
		},
		{
			"code": "SL0008",
			"active": true,
			"name": "Haridakhandi Redika Sahi",
			"locality": "SUN55"
		},
		{
			"code": "SL0009",
			"active": true,
			"name": "Golapali Sahi",
			"locality": "SUN18"
		},
		{
			"code": "SL0010",
			"active": true,
			"name": "Surya Nagar",
			"locality": "SUN18"
		},
		{
			"code": "SL0011",
			"active": true,
			"name": "Damba Sahi",
			"locality": "SUN18"
		},
		{
			"code": "SL0012",
			"active": true,
			"name": "Raju Dhoba Sahi",
			"locality": "SUN08"
		}
	]
}
```

PaymentType (Payment preference type)

```
{
    "tenantId": "pb",
    "moduleName": "FSM",
    "PaymentType": [
        {
            "name": "Pay Now",
            "code": "PRE_PAY",
            "active": true
        },
        {
            "name": "Pay on Service",
            "code": "POST_PAY",
            "active": true
        }
    ]
}
```

data/pg/FSM/ReceivedPaymentType.json

[https://github.com/egovernments/egov-mdms-data/commit/4c028a70ccb715df9574d86dc99d11d93057d30e](https://github.com/egovernments/egov-mdms-data/commit/4c028a70ccb715df9574d86dc99d11d93057d30e)

[https://github.com/egovernments/egov-mdms-data/commit/5a190371c2305131eac40b87b41c7b3f0eef092c](https://github.com/egovernments/egov-mdms-data/commit/5a190371c2305131eac40b87b41c7b3f0eef092c)

data/pg/FSM/CommonFieldsConfig.json

[https://github.com/egovernments/egov-mdms-data/commit/4fac292e055665e5fbe4bfeaa7991c574a2289dc](https://github.com/egovernments/egov-mdms-data/commit/4fac292e055665e5fbe4bfeaa7991c574a2289dc)

FSM Persister YML

Integrate following below changes in fsm-persister.yml [https://github.com/egovernments/configs/commit/634a4fdd842ec69bdf735e8c985e36499661512f](https://github.com/egovernments/configs/commit/634a4fdd842ec69bdf735e8c985e36499661512f)

data/pb/BillingService/BusinessService.json

[Update BusinessService.json · egovernments/egov-mdms-data@96cd829](https://github.com/egovernments/egov-mdms-data/commit/96cd829846e3cca0b0143b73748d57b268a8bef1)&#x20;

data/pb/DIGIT-UI/RoleStatusMapping.json

[#SM-528 updating the status role for fsm collector · egovernments/egov-mdms-data@0d4b0c7](https://github.com/egovernments/egov-mdms-data/commit/0d4b0c7e6c1102c17f8fbc1d0fa31cb655687502)

data/pb/BillingService/BusinessService.json

[#SM-1435 added minAmountpayable in fsm · egovernments/egov-mdms-data@13e867b](https://github.com/egovernments/egov-mdms-data/commit/13e867bfdcca5c357d09024ba7da3ec8894a875e)

data/pb/amritsar/FSM/ZeroPricing.json

[https://github.com/egovernments/egov-mdms-data/commit/bccf684bd1343b3d280c1b87b1f03dcf62c96159](https://github.com/egovernments/egov-mdms-data/commit/bccf684bd1343b3d280c1b87b1f03dcf62c96159)

[https://github.com/egovernments/egov-mdms-data/commit/7f3e6a02fc62bfdd9ee38dce2da9572ca9885866](https://github.com/egovernments/egov-mdms-data/commit/7f3e6a02fc62bfdd9ee38dce2da9572ca9885866)

data/pb/ACCESSCONTROL-ACTIONS-TEST/actions-test.json

[https://github.com/egovernments/egov-mdms-data/commit/06a1bcaca5693a6037cce52eecd53083dd6bd26f](https://github.com/egovernments/egov-mdms-data/commit/06a1bcaca5693a6037cce52eecd53083dd6bd26f)Dashboard Analytics Configuration

Following are the changes that need to be integrate in dashboard-analytics and restart the “dashboard-analytics” service

egov-dss-dashboards/dashboard-analytics/ChartApiConfig.json

[https://github.com/egovernments/configs/commit/2ae2feecd343d17b908820b86664cee38293a719](https://github.com/egovernments/configs/commit/2ae2feecd343d17b908820b86664cee38293a719)

[https://github.com/egovernments/configs/commit/18e547df409b625b0934e4dc7251590c5f834f83](https://github.com/egovernments/configs/commit/18e547df409b625b0934e4dc7251590c5f834f83)

[https://github.com/egovernments/configs/commit/f05d41d983a9ec5381183d3f26497dc2295ad169](https://github.com/egovernments/configs/commit/f05d41d983a9ec5381183d3f26497dc2295ad169)

[https://github.com/egovernments/configs/commit/47c3592252b4236b9a785adf6dd7d0b4dd66e482](https://github.com/egovernments/configs/commit/47c3592252b4236b9a785adf6dd7d0b4dd66e482)

[https://github.com/egovernments/configs/commit/5b716c195766a573fb542e41d3ca94b54b6aa248](https://github.com/egovernments/configs/commit/5b716c195766a573fb542e41d3ca94b54b6aa248)

egov-dss-dashboards/dashboard-analytics/MasterDashboardConfig.json

[https://github.com/egovernments/configs/commit/c1c4b2ed5e5eb1b153c2648c3307f006566a5a6b](https://github.com/egovernments/configs/commit/c1c4b2ed5e5eb1b153c2648c3307f006566a5a6b)

egov-indexer/egov-vehicle.yaml

[https://github.com/egovernments/configs/commit/3d9faae0f42550a4e15dcad69630846ba0482de8](https://github.com/egovernments/configs/commit/3d9faae0f42550a4e15dcad69630846ba0482de8)\


#### Business Service / Workflow Configuration

Create businessService (workflow configuration) using the /businessservice/\_create. Following is the product configuration for FSM:

```
{
  "RequestInfo": {
    "apiId": "Rainmaker",
    "action": "",
    "did": 1,
    "key": "",
    "msgId": "20170310130900|en_IN",
    "requesterId": "",
    "ts": 1513579888683,
    "ver": ".01",
    "authToken": "{{devAuth}}",
    "userInfo": {
      "id": 73,
      "userName": null,
      "name": null,
      "type": "EMPLOYEE",
      "mobileNumber": null,
      "emailId": null,
      "roles": [
        {
          "id": 2,
          "name": "Customer Support Representative",
          "code": null,
          "tenantId": null
        }
      ],
      "tenantId": null,
      "uuid": "uuid"
    }
  },
  "BusinessServices": [
        {
            "tenantId": "pb",
            "businessService": "FSM",
            "business": "fsm",
            "businessServiceSla": 172800000,
            "states": [
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": null,
                    "applicationStatus": null,
                    "docUploadRequired": false,
                    "isStartState": true,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
                            "action": "APPLY",
                            "nextState": "PENDING_APPL_FEE_PAYMENT",
                            "roles": [
                                "FSM_CREATOR_EMP"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "action": "CREATE",
                            "nextState": "CREATED",
                            "roles": [
                                "CITIZEN"
                            ]
                        }
                    ]
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "CREATED",
                    "applicationStatus": "CREATED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
                            "action": "REJECT",
                            "nextState": "REJECTED",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "action": "SUBMIT",
                            "nextState": "PENDING_APPL_FEE_PAYMENT",
                            "roles": [
                                "FSM_EDITOR_EMP"
                            ]
                        }
                    ]
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "PENDING_APPL_FEE_PAYMENT",
                    "applicationStatus": "PENDING_APPL_FEE_PAYMENT",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
                            "action": "REJECT",
                            "nextState": "REJECTED",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "action": "SENDBACK",
                            "nextState": "CREATED",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "action": "PAY",
                            "nextState": "ASSING_DSO",
                            "roles": [
                                "CITIZEN",
                                "FSM_COLLECTOR"
                            ]
                        }
                    ]
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "ASSING_DSO",
                    "applicationStatus": "ASSING_DSO",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
                            "action": "CANCEL",
                            "nextState": "CANCELED",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "action": "ASSIGN",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_EDITOR_EMP"
                            ]
                        }
                    ]
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "DSO_REJECTED",
                    "applicationStatus": "DSO_REJECTED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_REJECTED",
                            "action": "CANCEL",
                            "nextState": "CANCELED",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_REJECTED",
                            "action": "REASSING",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_EDITOR_EMP"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_REJECTED",
                            "action": "SENDBACK",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        }
                    ]
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "DSO_INPROGRESS",
                    "applicationStatus": "DSO_INPROGRESS",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_INPROGRESS",
                            "action": "SENDBACK",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_INPROGRESS",
                            "action": "DECLINE",
                            "nextState": "ASSING_DSO",
                            "roles": [
                                "FSM_DSO",
                                "FSM_EDITOR_EMP"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_INPROGRESS",
                            "action": "COMPLETED",
                            "nextState": "CITIZEN_FEEDBACK_PENDING",
                            "roles": [
                                "FSM_DSO",
                                "FSM_EDITOR_EMP"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_INPROGRESS",
                            "action": "CANCEL",
                            "nextState": "CANCELED",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_INPROGRESS",
                            "action": "REASSING",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_EDITOR_EMP"
                            ]
                        }
                    ]
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "PENDING_DSO_APPROVAL",
                    "applicationStatus": "PENDING_DSO_APPROVAL",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
                            "currentState": "PENDING_DSO_APPROVAL",
                            "action": "DSO_REJECT",
                            "nextState": "DSO_REJECTED",
                            "roles": [
                                "FSM_DSO"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "PENDING_DSO_APPROVAL",
                            "action": "DSO_ACCEPT",
                            "nextState": "DSO_INPROGRESS",
                            "roles": [
                                "FSM_DSO"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "PENDING_DSO_APPROVAL",
                            "action": "CANCEL",
                            "nextState": "CANCELED",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "PENDING_DSO_APPROVAL",
                            "action": "REASSING",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_EDITOR_EMP"
                            ]
                        }
                    ]
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "COMPLETED",
                    "applicationStatus": "COMPLETED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": true,
                    "isStateUpdatable": false
                },
                {
                    "sla": null,
                    "state": "REJECTED",
                    "applicationStatus": "REJECTED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": true,
                    "isStateUpdatable": false,
                    "actions": null
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "CANCELED",
                    "applicationStatus": "CANCELED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": true,
                    "isStateUpdatable": false,
                    "actions": null
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "CITIZEN_FEEDBACK_PENDING",
                    "applicationStatus": "CITIZEN_FEEDBACK_PENDING",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": false,
                    "actions": [
                        {
                            "tenantId": "pb",
                            "currentState": "CITIZEN_FEEDBACK_PENDING",
                            "action": "RATE",
                            "nextState": "COMPLETED",
                            "roles": [
                                "CITIZEN"
                            ]
                        }
                    ]
                }
            ]
        }
    ]
}
```

For post new Business service FSM\_POST\_PAY\_SERVICE has been created .Create businessService (workflow configuration) using the /businessservice/\_create. Following is the product configuration for FSM\_POST\_PAY\_SERVICE:

```
{
  "BusinessServices": [
        {
            "tenantId": "pb",
            "businessService": "FSM_POST_PAY_SERVICE",
            "business": "fsm",
            "businessServiceSla": 172800000,
            "states": [
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": null,
                    "applicationStatus": null,
                    "docUploadRequired": false,
                    "isStartState": true,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
							"currentState": null,
                            "action": "APPLY",
                            "nextState": "ASSIGN_DSO",
                            "roles": [
                                "FSM_CREATOR_EMP"
                            ]
                        },
                        {
                            "tenantId": "pb",
							"currentState": null,
                            "action": "CREATE",
                            "nextState": "CREATED",
                            "roles": [
                                "CITIZEN"
                            ]
                        }
                    ]
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "CREATED",
                    "applicationStatus": "CREATED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
							"currentState": "CREATED",
                            "action": "REJECT",
                            "nextState": "REJECTED",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        },
                        {
                            "tenantId": "pb",
							"currentState": "CREATED",
                            "action": "SUBMIT",
                            "nextState": "ASSIGN_DSO",
                            "roles": [
                                "FSM_EDITOR_EMP"
                            ]
                        }
                    ]
                },
                
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "ASSIGN_DSO",
                    "applicationStatus": "ASSIGN_DSO",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
							"currentState": "ASSIGN_DSO",
                            "action": "CANCEL",
                            "nextState": "CANCELED",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        },
                        {
                            "tenantId": "pb",
							"currentState": "ASSIGN_DSO",
                            "action": "ASSIGN",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_EDITOR_EMP"
                            ]
                        }
                    ]
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "PENDING_DSO_APPROVAL",
                    "applicationStatus": "PENDING_DSO_APPROVAL",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                       	{
                            "tenantId": "pb",
                            "currentState": "PENDING_DSO_APPROVAL",
                            "action": "DSO_ACCEPT",
                            "nextState": "DSO_INPROGRESS",
                            "roles": [
                                 "FSM_DSO",
                                 "FSM_EDITOR_EMP"
                            ]
                        },
						{
                            "tenantId": "pb",
                            "currentState": "PENDING_DSO_APPROVAL",
                            "action": "CANCEL",
                            "nextState": "CANCELED",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        },
						{
                            "tenantId": "pb",
                            "currentState": "PENDING_DSO_APPROVAL",
                            "action": "REASSING",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_EDITOR_EMP"
                            ]
                        },
						{
                            "tenantId": "pb",
                            "currentState": "PENDING_DSO_APPROVAL",
                            "action": "DSO_REJECT",
                            "nextState": "DSO_REJECTED",
                            "roles": [
                                 "FSM_DSO",
                                 "FSM_EDITOR_EMP"
                            ]
                        }
                    ]
                },
				 {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "DSO_REJECTED",
                    "applicationStatus": "DSO_REJECTED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_REJECTED",
                            "action": "CANCEL",
                            "nextState": "CANCELED",
                            "roles": [
                                "FSM_ADMIN"
                            ],
							"active": true
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_REJECTED",
                            "action": "REASSING",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_EDITOR_EMP"
                            ],
							 "active": true
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_REJECTED",
                            "action": "SENDBACK",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_ADMIN"
                            ],
							"active": true
                        }
                    ]
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "DSO_INPROGRESS",
                    "applicationStatus": "DSO_INPROGRESS",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_INPROGRESS",
                            "action": "SENDBACK",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_INPROGRESS",
                            "action": "DECLINE",
                            "nextState": "ASSIGN_DSO",
                            "roles": [
                                "FSM_DSO",
                                "FSM_EDITOR_EMP"
                            ]
                        },
                       
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_INPROGRESS",
                            "action": "CANCEL",
                            "nextState": "CANCELED",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_INPROGRESS",
                            "action": "REASSING",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_EDITOR_EMP"
                            ]
                        },
						{
                            "tenantId": "pb",
                            "currentState": "DSO_INPROGRESS",
                            "action": "SCHEDULE",
                            "nextState": "PENDING_APPL_FEE_PAYMENT",
                            "roles": [
                                "FSM_EDITOR_EMP",
								"FSM_DSO"
							]
                        }
                    ]
                },
				{
                    "tenantId": "pb",
                    "sla": null,
                    "state": "PENDING_APPL_FEE_PAYMENT",
                    "applicationStatus": "PENDING_APPL_FEE_PAYMENT",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
                            "currentState": "PENDING_APPL_FEE_PAYMENT",
                            "action": "CANCEL",
                            "nextState": "CANCELED",
                            "roles": [
                                "FSM_ADMIN"
                            ],
                            "active": true
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "PENDING_APPL_FEE_PAYMENT",
                            "action": "SENDBACK",
                            "nextState": "DSO_INPROGRESS",
                            "roles": [
                                "FSM_ADMIN"
                            ],
                            "active": true
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "PENDING_APPL_FEE_PAYMENT",
                            "action": "PAY",
                            "nextState": "DISPOSAL_IN_PROGRESS",
                            "roles": [
                                "CITIZEN",
                                "FSM_COLLECTOR"
                            ],
                            "active": true
                        }
                    ]
                },
				{
                    "tenantId": "pb",
                    "sla": null,
                    "state": "DISPOSAL_IN_PROGRESS",
                    "applicationStatus": "DISPOSAL_IN_PROGRESS",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
                            "currentState": "DISPOSAL_IN_PROGRESS",
                            "action": "CANCEL",
                            "nextState": "CANCELED",
                            "roles": [
                                "FSM_ADMIN"
                            ],
                            "active": true
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "DISPOSAL_IN_PROGRESS",
                            "action": "COMPLETED",
                            "nextState": "CITIZEN_FEEDBACK_PENDING",
                            "roles": [
                                "FSM_DSO",
                                "FSM_EDITOR_EMP"
                            ],
                            "active": true
                        }
                       
                    ]
                },
				{
                    "tenantId": "pb",
                    "sla": null,
                    "state": "CITIZEN_FEEDBACK_PENDING",
                    "applicationStatus": "CITIZEN_FEEDBACK_PENDING",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": false,
                    "actions": [
                        {
                            "tenantId": "pb",
                            "currentState": "CITIZEN_FEEDBACK_PENDING",
                            "action": "RATE",
                            "nextState": "COMPLETED",
                            "roles": [
                                "CITIZEN"
                            ],
						    "active": true
                        }
                    ]
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "COMPLETED",
                    "applicationStatus": "COMPLETED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": true,
                    "isStateUpdatable": false,
					"actions": null
                },
                {
                    "tenantId": "pb",
					"sla": null,
                    "state": "REJECTED",
                    "applicationStatus": "REJECTED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": true,
                    "isStateUpdatable": false,
                    "actions": null
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "CANCELED",
                    "applicationStatus": "CANCELED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": true,
                    "isStateUpdatable": false,
                    "actions": null
                }
                
            ]
        }
    ],
	 "RequestInfo": {
    "apiId": "Rainmaker",
    "authToken": "e37d7087-6436-492f-ad5b-692a515cba58",
    "userInfo": {
      "id": 24226,
      "uuid": "11b0e02b-0145-4de2-bc42-c97b96264807",
      "userName": "amr001",
      "name": "leela",
      "mobileNumber": "9814424443",
      "emailId": "leela@llgmail.com",
      "locale": null,
      "type": "EMPLOYEE",
      "roles": [
        {
          "name": "NoC counter employee",
          "code": "NOC_CEMP",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "Grievance Routing Officer",
          "code": "GRO",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "WS Document Verifier",
          "code": "WS_DOC_VERIFIER",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "autoescalation emp",
          "code": "AUTO_ESCALATE",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "FSM Employee Report Viewer",
          "code": "FSM_REPORT_VIEWER",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "PGR Last Mile Employee",
          "code": "PGR_LME",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "TL Field Inspector",
          "code": "TL_FIELD_INSPECTOR",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "BPA Field Inspector",
          "code": "BPA_FIELD_INSPECTOR",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "TL Approver",
          "code": "TL_APPROVER",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "BPA Services Approver",
          "code": "BPA_APPROVER",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "Fire Noc Department Approver",
          "code": "FIRE_NOC_APPROVER",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "Field Employee",
          "code": "FEMP",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "Counter Employee",
          "code": "CEMP",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "WS Counter Employee",
          "code": "WS_CEMP",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "BPAREG Approver",
          "code": "BPAREG_APPROVER",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "WS Field Inspector",
          "code": "WS_FIELD_INSPECTOR",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "Collection Operator",
          "code": "COLL_OPERATOR",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "TL doc verifier",
          "code": "TL_DOC_VERIFIER",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "CSC Collection Operator",
          "code": "CSC_COLL_OPERATOR",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "Employee",
          "code": "EMPLOYEE",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "TL Counter Employee",
          "code": "TL_CEMP",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "FSM Desluding Operator",
          "code": "FSM_DSO",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "TL Creator",
          "code": "TL_CREATOR",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "BPAREG doc verifier",
          "code": "BPAREG_DOC_VERIFIER",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "Customer Support Representative",
          "code": "CSR",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "NoC counter Approver",
          "code": "NOC_APPROVER",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "HRMS Admin",
          "code": "HRMS_ADMIN",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "Universal Collection Employee",
          "code": "UC_EMP",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "WS Approver",
          "code": "WS_APPROVER",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "BPA Services verifier",
          "code": "BPA_VERIFIER",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "PT Counter Approver",
          "code": "PT_APPROVER",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "NoC Field Inpector",
          "code": "NOC_FIELD_INSPECTOR",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "Grievance Officer",
          "code": "GO",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "Super User",
          "code": "SUPERUSER",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "NOC Department Approver",
          "code": "NOC_DEPT_APPROVER",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "WS Clerk",
          "code": "WS_CLERK",
          "tenantId": "pb.amritsar"
        },
        {
          "name": "NoC Doc Verifier",
          "code": "NOC_DOC_VERIFIER",
          "tenantId": "pb.amritsar"
        }
      ],
      "active": true,
      "tenantId": "pb.amritsar",
      "permanentCity": null
    },
    "msgId": "1646071179143|en_IN"
  }
}

```

In system the FSM\_POST\_PAY\_SERVICE and FSM (i.e above two Business service) are removed and we introduced below new Business service for advance payment application and zero price application.

For Advance new Business service FSM\_ADVANCE\_PAY\_SERVICE has been created.

Create businessService (workflow configuration) using the  /businessservice/\_create. Following is the product configuration for FSM\_ADVANCE\_PAY\_SERVICE:

```
{

    "BusinessServices": [

        {

            "tenantId": "pb",

            "businessService": "FSM_ADVANCE_PAY_SERVICE",

            "business": "fsm",

            "businessServiceSla": 172800000,

            "states": [

                {

                    "tenantId": "pb",

                    "sla": null,

                    "state": null,

                    "applicationStatus": null,

                    "docUploadRequired": false,

                    "isStartState": true,

                    "isTerminateState": false,

                    "isStateUpdatable": true,

                    "actions": [

                        {

                            "tenantId": "pb",

                            "action": "APPLY",

                            "nextState": "PENDING_APPL_FEE_PAYMENT",

                            "roles": [

                                "FSM_CREATOR_EMP"

                            ]

                        },

                        {

                            "tenantId": "pb",

                            "action": "CREATE",

                            "nextState": "CREATED",

                            "roles": [

                                "CITIZEN"

                            ]

                        }

                    ]

                },

                {

                    "tenantId": "pb",

                    "sla": null,

                    "state": "CREATED",

                    "applicationStatus": "CREATED",

                    "docUploadRequired": false,

                    "isStartState": false,

                    "isTerminateState": false,

                    "isStateUpdatable": true,

                    "actions": [

                        {

                            "tenantId": "pb",

                            "action": "REJECT",

                            "nextState": "REJECTED",

                            "roles": [

                                "FSM_ADMIN"

                            ]

                        },

                        {

                            "tenantId": "pb",

                            "action": "SUBMIT",

                            "nextState": "PENDING_APPL_FEE_PAYMENT",

                            "roles": [

                                "FSM_EDITOR_EMP"

                            ]

                        }

                    ]

                },

                {

                    "tenantId": "pb",

                    "sla": null,

                    "state": "PENDING_APPL_FEE_PAYMENT",

                    "applicationStatus": "PENDING_APPL_FEE_PAYMENT",

                    "docUploadRequired": false,

                    "isStartState": false,

                    "isTerminateState": false,

                    "isStateUpdatable": true,

                    "actions": [

                        {

                            "tenantId": "pb",

                            "action": "REJECT",

                            "nextState": "REJECTED",

                            "roles": [

                                "FSM_ADMIN"

                            ]

                        },

                        {

                            "tenantId": "pb",

                            "action": "SENDBACK",

                            "nextState": "CREATED",

                            "roles": [

                                "FSM_ADMIN"

                            ]

                        },

                        {

                            "tenantId": "pb",

                            "action": "PAY",

                            "nextState": "ASSING_DSO",

                            "roles": [

                                "CITIZEN",

                                "FSM_COLLECTOR"

                            ]

                        }

                    ]

                },

                {

                    "tenantId": "pb",

                    "sla": null,

                    "state": "ASSING_DSO",

                    "applicationStatus": "ASSING_DSO",

                    "docUploadRequired": false,

                    "isStartState": false,

                    "isTerminateState": false,

                    "isStateUpdatable": true,

                    "actions": [

                        {

                            "tenantId": "pb",

                            "action": "CANCEL",

                            "nextState": "CANCELED",

                            "roles": [

                                "FSM_ADMIN"

                            ]

                        },

                        {

                            "tenantId": "pb",

                            "action": "ASSIGN",

                            "nextState": "PENDING_DSO_APPROVAL",

                            "roles": [

                                "FSM_EDITOR_EMP"

                            ]

                        }

                    ]

                },

                {

                    "tenantId": "pb",

                    "sla": null,

                    "state": "DSO_REJECTED",

                    "applicationStatus": "DSO_REJECTED",

                    "docUploadRequired": false,

                    "isStartState": false,

                    "isTerminateState": false,

                    "isStateUpdatable": true,

                    "actions": [

                        {

                            "tenantId": "pb",

                            "currentState": "DSO_REJECTED",

                            "action": "CANCEL",

                            "nextState": "CANCELED",

                            "roles": [

                                "FSM_ADMIN"

                            ]

                        },

                        {

                            "tenantId": "pb",

                            "currentState": "DSO_REJECTED",

                            "action": "REASSING",

                            "nextState": "PENDING_DSO_APPROVAL",

                            "roles": [

                                "FSM_EDITOR_EMP"

                            ]

                        },

                        {

                            "tenantId": "pb",

                            "currentState": "DSO_REJECTED",

                            "action": "SENDBACK",

                            "nextState": "PENDING_DSO_APPROVAL",

                            "roles": [

                                "FSM_ADMIN"

                            ]

                        }

                    ]

                },

                {

                    "tenantId": "pb",

                    "sla": null,

                    "state": "DSO_INPROGRESS",

                    "applicationStatus": "DSO_INPROGRESS",

                    "docUploadRequired": false,

                    "isStartState": false,

                    "isTerminateState": false,

                    "isStateUpdatable": true,

                    "actions": [

                        {

                            "tenantId": "pb",

                            "currentState": "DSO_INPROGRESS",

                            "action": "SENDBACK",

                            "nextState": "PENDING_DSO_APPROVAL",

                            "roles": [

                                "FSM_ADMIN"

                            ]

                        },

                        {

                            "tenantId": "pb",

                            "currentState": "DSO_INPROGRESS",

                            "action": "COMPLETED",

                            "nextState": "CITIZEN_FEEDBACK_PENDING",

                            "roles": [

                                "FSM_DSO",

                                "FSM_EDITOR_EMP"

                            ]

                        },

                        {

                            "tenantId": "pb",

                            "currentState": "DSO_INPROGRESS",

                            "action": "CANCEL",

                            "nextState": "CANCELED",

                            "roles": [

                                "FSM_ADMIN"

                            ]

                        },

                        {

                            "tenantId": "pb",

                            "currentState": "DSO_INPROGRESS",

                            "action": "UPDATE",

                            "nextState": "DSO_INPROGRESS",

                            "roles": [

                                "FSM_DSO",

                                "FSM_EDITOR_EMP"

                            ]

                        },

                        {

                            "tenantId": "pb",

                            "action": "PAY",

                            "nextState": "DSO_INPROGRESS",

                            "roles": [

                                "CITIZEN",

                                "FSM_COLLECTOR"

                            ]

                        },

                        {

                            "tenantId": "pb",

                            "currentState": "DSO_INPROGRESS",

                            "action": "REASSING",

                            "nextState": "PENDING_DSO_APPROVAL",

                            "roles": [

                                "FSM_EDITOR_EMP"

                            ]

                        }

                    ]

                },

                {

                    "tenantId": "pb",

                    "sla": null,

                    "state": "PENDING_DSO_APPROVAL",

                    "applicationStatus": "PENDING_DSO_APPROVAL",

                    "docUploadRequired": false,

                    "isStartState": false,

                    "isTerminateState": false,

                    "isStateUpdatable": true,

                    "actions": [

                        {

                            "tenantId": "pb",

                            "currentState": "PENDING_DSO_APPROVAL",

                            "action": "DSO_REJECT",

                            "nextState": "DSO_REJECTED",

                            "roles": [

                                "FSM_DSO",

                                "FSM_EDITOR_EMP"

                            ]

                        },

                        {

                            "tenantId": "pb",

                            "currentState": "PENDING_DSO_APPROVAL",

                            "action": "DSO_ACCEPT",

                            "nextState": "DSO_INPROGRESS",

                            "roles": [

                                "FSM_DSO",

                                "FSM_EDITOR_EMP"

                            ]

                        },

                        {

                            "tenantId": "pb",

                            "currentState": "PENDING_DSO_APPROVAL",

                            "action": "CANCEL",

                            "nextState": "CANCELED",

                            "roles": [

                                "FSM_ADMIN"

                            ]

                        },

                        {

                            "tenantId": "pb",

                            "currentState": "PENDING_DSO_APPROVAL",

                            "action": "REASSING",

                            "nextState": "PENDING_DSO_APPROVAL",

                            "roles": [

                                "FSM_EDITOR_EMP"

                            ]

                        }

                    ]

                },

                {

                    "tenantId": "pb",

                    "sla": null,

                    "state": "COMPLETED",

                    "applicationStatus": "COMPLETED",

                    "docUploadRequired": false,

                    "isStartState": false,

                    "isTerminateState": true,

                    "isStateUpdatable": false

                },

                {

                    "sla": null,

                    "state": "REJECTED",

                    "applicationStatus": "REJECTED",

                    "docUploadRequired": false,

                    "isStartState": false,

                    "isTerminateState": true,

                    "isStateUpdatable": false,

                    "actions": null

                },

                {

                    "tenantId": "pb",

                    "sla": null,

                    "state": "CANCELED",

                    "applicationStatus": "CANCELED",

                    "docUploadRequired": false,

                    "isStartState": false,

                    "isTerminateState": true,

                    "isStateUpdatable": false,

                    "actions": null

                },

                {

                    "tenantId": "pb",

                    "sla": null,

                    "state": "CITIZEN_FEEDBACK_PENDING",

                    "applicationStatus": "CITIZEN_FEEDBACK_PENDING",

                    "docUploadRequired": false,

                    "isStartState": false,

                    "isTerminateState": false,

                    "isStateUpdatable": false,

                    "actions": [

                        {

                            "tenantId": "pb",

                            "currentState": "CITIZEN_FEEDBACK_PENDING",

                            "action": "RATE",

                            "nextState": "COMPLETED",

                            "roles": [

                                "CITIZEN"

                            ]

                        }

                    ]

                }

            ]

        }

    ],

    "RequestInfo": {

        "apiId": "Rainmaker",

        "action": "",

        "did": 1,

        "key": "",

        "msgId": "20170310130900|en_IN",

        "requesterId": "",

        "ts": 1513579888683,

        "ver": ".01",

        "authToken": "c6aa4196-0e1b-4634-802b-b85fa13ae6ce",

        "userInfo": {

            "id": 30074,

            "uuid": "5130f2e3-efc1-401a-94fb-b9e60d9fa17d",

            "userName": "XYZ",

            "name": "XYZ",

            "mobileNumber": "8897970021",

            "emailId": null,

            "locale": null,

            "type": "EMPLOYEE",

            "roles": [

                {

                    "name": "FSM Employee Application Viewer",

                    "code": "FSM_VIEW_EMP",

                    "tenantId": "pb.amritsar"

                },

                {

                    "name": "Employee",

                    "code": "EMPLOYEE",

                    "tenantId": "pb.amritsar"

                },

                {

                    "name": "National Dashboard Administrator",

                    "code": "NATADMIN",

                    "tenantId": "pb.amritsar"

                },

                {

                    "name": "TL Field Inspector",

                    "code": "TL_FIELD_INSPECTOR",

                    "tenantId": "pb.amritsar"

                },

                {

                    "name": "ptcollection emp",

                    "code": "PT_COLLECTION_EMP",

                    "tenantId": "pb.amritsar"

                },

                {

                    "name": "EMPLOYEE ADMIN",

                    "code": "EMPLOYEE ADMIN",

                    "tenantId": "pb.amritsar"

                },

                {

                    "name": "HRMS Admin",

                    "code": "HRMS_ADMIN",

                    "tenantId": "pb.amritsar"

                },

                {

                    "name": "Universal Collection Employee",

                    "code": "UC_EMP",

                    "tenantId": "pb.amritsar"

                },

                {

                    "name": "State Administrator",

                    "code": "STADMIN",

                    "tenantId": "pb.amritsar"

                },

                {

                    "name": "Super User",

                    "code": "SUPERUSER",

                    "tenantId": "pb.amritsar"

                },

                {

                    "name": "FSM Employee Application Creator",

                    "code": "FSM_CREATOR_EMP",

                    "tenantId": "pb.amritsar"

                },

                {

                    "name": "FSM Employee Dashboard Viewer",

                    "code": "FSM_DASHBOARD_VIEWER",

                    "tenantId": "pb.amritsar"

                },

                {

                    "name": "Anonymous User",

                    "code": "ANONYMOUS",

                    "tenantId": "pb.amritsar"

                }

            ],

            "active": true,

            "tenantId": "pb.amritsar",

            "permanentCity": null

        }

    }

}
```

For Advance Zero new Business service PAY\_LATER\_SERVICE has been created&#x20;

Create businessService (workflow configuration) using the  /businessservice/\_create. Following is the product configuration for PAY\_LATER\_SERVICE:

```
{
    "BusinessServices":[
        {
            "tenantId": "pb",
            "businessService": "PAY_LATER_SERVICE",
            "business": "fsm",
            "businessServiceSla": 172800000,
            "states": [
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": null,
                    "applicationStatus": null,
                    "docUploadRequired": false,
                    "isStartState": true,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
                            "currentState": null,
                            "action": "APPLY",
                            "nextState": "ASSING_DSO",
                            "roles": [
                                "FSM_CREATOR_EMP"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "currentState": null,
                            "action": "CREATE",
                            "nextState": "CREATED",
                            "roles": [
                                "CITIZEN"
                            ]
                        }
                    ]
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "CREATED",
                    "applicationStatus": "CREATED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
                            "currentState": "CREATED",
                            "action": "REJECT",
                            "nextState": "REJECTED",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "CREATED",
                            "action": "SUBMIT",
                            "nextState": "ASSING_DSO",
                            "roles": [
                                "FSM_EDITOR_EMP"
                            ]
                        }
                    ]
                },
                
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "ASSING_DSO",
                    "applicationStatus": "ASSING_DSO",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
                            "currentState": "ASSING_DSO",
                            "action": "CANCEL",
                            "nextState": "CANCELED",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "ASSING_DSO",
                            "action": "ASSIGN",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_EDITOR_EMP"
                            ]
                        }
                    ]
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "PENDING_DSO_APPROVAL",
                    "applicationStatus": "PENDING_DSO_APPROVAL",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
                            "currentState": "PENDING_DSO_APPROVAL",
                            "action": "DSO_ACCEPT",
                            "nextState": "DSO_INPROGRESS",
                            "roles": [
                                 "FSM_DSO",
                                 "FSM_EDITOR_EMP"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "PENDING_DSO_APPROVAL",
                            "action": "CANCEL",
                            "nextState": "CANCELED",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "PENDING_DSO_APPROVAL",
                            "action": "REASSING",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_EDITOR_EMP"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "PENDING_DSO_APPROVAL",
                            "action": "DSO_REJECT",
                            "nextState": "DSO_REJECTED",
                            "roles": [
                                 "FSM_DSO",
                                 "FSM_EDITOR_EMP"
                            ]
                        }
                    ]
                },
                 {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "DSO_REJECTED",
                    "applicationStatus": "DSO_REJECTED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_REJECTED",
                            "action": "CANCEL",
                            "nextState": "CANCELED",
                            "roles": [
                                "FSM_ADMIN"
                            ],
                            "active": true
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_REJECTED",
                            "action": "REASSING",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_EDITOR_EMP"
                            ],
                             "active": true
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_REJECTED",
                            "action": "SENDBACK",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_ADMIN"
                            ],
                            "active": true
                        }
                    ]
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "DSO_INPROGRESS",
                    "applicationStatus": "DSO_INPROGRESS",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_INPROGRESS",
                            "action": "SENDBACK",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_INPROGRESS",
                            "action": "COMPLETED",
                            "nextState": "CITIZEN_FEEDBACK_PENDING",
                            "roles": [
                                "FSM_DSO",
                                "FSM_EDITOR_EMP"
                            ]
                        },
                       
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_INPROGRESS",
                            "action": "CANCEL",
                            "nextState": "CANCELED",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_INPROGRESS",
                            "action": "REASSING",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_EDITOR_EMP"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_INPROGRESS",
                            "action": "UPDATE",
                            "nextState": "DSO_INPROGRESS",
                            "roles": [
                                "FSM_DSO",
                                "FSM_EDITOR_EMP"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "action": "PAY",
                            "nextState": "DSO_INPROGRESS",
                            "roles": [
                                "CITIZEN",
                                "FSM_COLLECTOR"
                            ]
                        }
                    ]
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "CITIZEN_FEEDBACK_PENDING",
                    "applicationStatus": "CITIZEN_FEEDBACK_PENDING",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": false,
                    "actions": [
                        {
                            "tenantId": "pb",
                            "currentState": "CITIZEN_FEEDBACK_PENDING",
                            "action": "RATE",
                            "nextState": "COMPLETED",
                            "roles": [
                                "CITIZEN"
                            ],
                            "active": true
                        }
                    ]
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "COMPLETED",
                    "applicationStatus": "COMPLETED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": true,
                    "isStateUpdatable": false,
                    "actions": null
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "REJECTED",
                    "applicationStatus": "REJECTED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": true,
                    "isStateUpdatable": false,
                    "actions": null
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "CANCELED",
                    "applicationStatus": "CANCELED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": true,
                    "isStateUpdatable": false,
                    "actions": null
                }
                
            ]
        }
    ],
    "RequestInfo": {
        "apiId": "Rainmaker",
        "action": "",
        "did": 1,
        "key": "",
        "msgId": "20170310130900|en_IN",
        "requesterId": "",
        "ts": 1513579888683,
        "ver": ".01",
        "authToken": "3d828f89-c249-4d4a-9098-8230e6040bf5",
        "userInfo": {
            "id": 30074,
            "uuid": "5130f2e3-efc1-401a-94fb-b9e60d9fa17d",
            "userName": "XYZ",
            "name": "XYZ",
            "mobileNumber": "8897970021",
            "emailId": null,
            "locale": null,
            "type": "EMPLOYEE",
            "roles": [
                {
                    "name": "FSM Employee Application Viewer",
                    "code": "FSM_VIEW_EMP",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "Employee",
                    "code": "EMPLOYEE",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "National Dashboard Administrator",
                    "code": "NATADMIN",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "TL Field Inspector",
                    "code": "TL_FIELD_INSPECTOR",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "ptcollection emp",
                    "code": "PT_COLLECTION_EMP",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "EMPLOYEE ADMIN",
                    "code": "EMPLOYEE ADMIN",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "HRMS Admin",
                    "code": "HRMS_ADMIN",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "Universal Collection Employee",
                    "code": "UC_EMP",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "State Administrator",
                    "code": "STADMIN",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "Super User",
                    "code": "SUPERUSER",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "FSM Employee Application Creator",
                    "code": "FSM_CREATOR_EMP",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "FSM Employee Dashboard Viewer",
                    "code": "FSM_DASHBOARD_VIEWER",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "Anonymous User",
                    "code": "ANONYMOUS",
                    "tenantId": "pb.amritsar"
                }
            ],
            "active": true,
            "tenantId": "pb.amritsar",
            "permanentCity": null
        }
    }
}
```

For Zero Price Application new Business service FSM\_ZERO\_PAY\_SERVICE has been created&#x20;

Create businessService (workflow configuration) using the  /businessservice/\_create. Following is the product configuration for FSM\_ZERO\_PAY\_SERVICE:

```
{
    "BusinessServices": [
        {
            "tenantId": "pb",
            "businessService": "FSM_ZERO_PAY_SERVICE",
            "business": "fsm",
            "businessServiceSla": 172800000,
            "states": [
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": null,
                    "applicationStatus": null,
                    "docUploadRequired": false,
                    "isStartState": true,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
							"currentState": null,
                            "action": "APPLY",
                            "nextState": "ASSING_DSO",
                            "roles": [
                                "FSM_CREATOR_EMP"
                            ]
                        },
                        {
                            "tenantId": "pb",
							"currentState": null,
                            "action": "CREATE",
                            "nextState": "CREATED",
                            "roles": [
                                "CITIZEN"
                            ]
                        }
                    ]
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "CREATED",
                    "applicationStatus": "CREATED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
							"currentState": "CREATED",
                            "action": "REJECT",
                            "nextState": "REJECTED",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        },
                        {
                            "tenantId": "pb",
							"currentState": "CREATED",
                            "action": "SUBMIT",
                            "nextState": "ASSING_DSO",
                            "roles": [
                                "FSM_EDITOR_EMP"
                            ]
                        }
                    ]
                },
                
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "ASSING_DSO",
                    "applicationStatus": "ASSING_DSO",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
							"currentState": "ASSING_DSO",
                            "action": "CANCEL",
                            "nextState": "CANCELED",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        },
                        {
                            "tenantId": "pb",
							"currentState": "ASSING_DSO",
                            "action": "ASSIGN",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_EDITOR_EMP"
                            ]
                        }
                    ]
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "PENDING_DSO_APPROVAL",
                    "applicationStatus": "PENDING_DSO_APPROVAL",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                       	{
                            "tenantId": "pb",
                            "currentState": "PENDING_DSO_APPROVAL",
                            "action": "DSO_ACCEPT",
                            "nextState": "DSO_INPROGRESS",
                            "roles": [
                                 "FSM_DSO",
                                 "FSM_EDITOR_EMP"
                            ]
                        },
						{
                            "tenantId": "pb",
                            "currentState": "PENDING_DSO_APPROVAL",
                            "action": "CANCEL",
                            "nextState": "CANCELED",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        },
						{
                            "tenantId": "pb",
                            "currentState": "PENDING_DSO_APPROVAL",
                            "action": "REASSING",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_EDITOR_EMP"
                            ]
                        },
						{
                            "tenantId": "pb",
                            "currentState": "PENDING_DSO_APPROVAL",
                            "action": "DSO_REJECT",
                            "nextState": "DSO_REJECTED",
                            "roles": [
                                 "FSM_DSO",
                                 "FSM_EDITOR_EMP"
                            ]
                        }
                    ]
                },
				 {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "DSO_REJECTED",
                    "applicationStatus": "DSO_REJECTED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_REJECTED",
                            "action": "CANCEL",
                            "nextState": "CANCELED",
                            "roles": [
                                "FSM_ADMIN"
                            ],
							"active": true
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_REJECTED",
                            "action": "REASSING",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_EDITOR_EMP"
                            ],
							 "active": true
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_REJECTED",
                            "action": "SENDBACK",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_ADMIN"
                            ],
							"active": true
                        }
                    ]
                },
                 {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "DSO_INPROGRESS",
                    "applicationStatus": "DSO_INPROGRESS",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_INPROGRESS",
                            "action": "SENDBACK",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        },
						{
                            "tenantId": "pb",
                            "currentState": "DSO_INPROGRESS",
                            "action": "COMPLETED",
                            "nextState": "CITIZEN_FEEDBACK_PENDING",
                            "roles": [
                                "FSM_DSO",
                                "FSM_EDITOR_EMP"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_INPROGRESS",
                            "action": "CANCEL",
                            "nextState": "CANCELED",
                            "roles": [
                                "FSM_ADMIN"
                            ]
                        },
                        {
                            "tenantId": "pb",
                            "currentState": "DSO_INPROGRESS",
                            "action": "REASSING",
                            "nextState": "PENDING_DSO_APPROVAL",
                            "roles": [
                                "FSM_EDITOR_EMP"
                            ]
                        },
						{
                            "tenantId": "pb",
                            "currentState": "DSO_INPROGRESS",
                            "action": "UPDATE",
                            "nextState": "DSO_INPROGRESS",
                            "roles": [
                                "FSM_DSO",
                                "FSM_EDITOR_EMP"
                            ]
                        }
                    ]
                },
				{
                    "tenantId": "pb",
                    "sla": null,
                    "state": "CITIZEN_FEEDBACK_PENDING",
                    "applicationStatus": "CITIZEN_FEEDBACK_PENDING",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": false,
                    "actions": [
                        {
                            "tenantId": "pb",
                            "currentState": "CITIZEN_FEEDBACK_PENDING",
                            "action": "RATE",
                            "nextState": "COMPLETED",
                            "roles": [
                                "CITIZEN"
                            ],
						    "active": true
                        }
                    ]
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "COMPLETED",
                    "applicationStatus": "COMPLETED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": true,
                    "isStateUpdatable": false,
					"actions": null
                },
                {
                    "tenantId": "pb",
					"sla": null,
                    "state": "REJECTED",
                    "applicationStatus": "REJECTED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": true,
                    "isStateUpdatable": false,
                    "actions": null
                },
                {
                    "tenantId": "pb",
                    "sla": null,
                    "state": "CANCELED",
                    "applicationStatus": "CANCELED",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": true,
                    "isStateUpdatable": false,
                    "actions": null
                }
                
            ]
        }
    ],
    "RequestInfo": {
        "apiId": "Rainmaker",
        "action": "",
        "did": 1,
        "key": "",
        "msgId": "20170310130900|en_IN",
        "requesterId": "",
        "ts": 1513579888683,
        "ver": ".01",
        "authToken": "3d828f89-c249-4d4a-9098-8230e6040bf5",
        "userInfo": {
            "id": 30074,
            "uuid": "5130f2e3-efc1-401a-94fb-b9e60d9fa17d",
            "userName": "XYZ",
            "name": "XYZ",
            "mobileNumber": "8897970021",
            "emailId": null,
            "locale": null,
            "type": "EMPLOYEE",
            "roles": [
                {
                    "name": "FSM Employee Application Viewer",
                    "code": "FSM_VIEW_EMP",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "Employee",
                    "code": "EMPLOYEE",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "National Dashboard Administrator",
                    "code": "NATADMIN",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "TL Field Inspector",
                    "code": "TL_FIELD_INSPECTOR",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "ptcollection emp",
                    "code": "PT_COLLECTION_EMP",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "EMPLOYEE ADMIN",
                    "code": "EMPLOYEE ADMIN",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "HRMS Admin",
                    "code": "HRMS_ADMIN",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "Universal Collection Employee",
                    "code": "UC_EMP",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "State Administrator",
                    "code": "STADMIN",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "Super User",
                    "code": "SUPERUSER",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "FSM Employee Application Creator",
                    "code": "FSM_CREATOR_EMP",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "FSM Employee Dashboard Viewer",
                    "code": "FSM_DASHBOARD_VIEWER",
                    "tenantId": "pb.amritsar"
                },
                {
                    "name": "Anonymous User",
                    "code": "ANONYMOUS",
                    "tenantId": "pb.amritsar"
                }
            ],
            "active": true,
            "tenantId": "pb.amritsar",
            "permanentCity": null
        }
    }
}
```

#### Localisation Setup <a href="#localization-setup" id="localization-setup"></a>

Using /localization/messages/v1/\_upsert , add localisation (templates) for notification messages to be sent. Following are the product notification templates:

```
{
  "messages":[
          {
            "code": "FSM_SMS_CREATED_CREATE",
            "message": "Dear Applicant,Your application for cleaning septic tank/pit is created with application reference no.<2>.You will be notified to make an application fee shortly.Request is expected to be completed within <SLA_HOURS>hrs of making the payment.",
            "module": "rainmaker-common",
            "locale": "en_IN"
        },
          {
            "code": "FSM_SMS_PENDING_APPL_FEE_PAYMENT_SUBMIT",
            "message": "Dear Applicant, Please pay the application fee Rs.<AMOUNT_TO_BE_PAID>/- for cleaning the septic tank/pit with request number <2>.Click this link <PAY_LINK> to make the payment.Request is expected to be completed within <SLA_HOURS>hrs of making the payment.",
            "module": "rainmaker-common",
            "locale": "en_IN"
        },
        {
            "code": "FSM_SMS_PENDING_APPL_FEE_PAYMENT_APPLY",
            "message": "Dear Applicant, Your application for cleaning septic tank /pit is created with application number <2>.Please click this link <PAY_LINK> to pay the application fee for processing the application.Request is expected to be completed within <SLA_HOURS>hrs of making the payment.",
            "module": "rainmaker-common",
            "locale": "en_IN"
        },
        {
            "code": "FSM_SMS_ASSING_DSO_PAY",
            "message": "Dear Applicant, Amount of Rs.<AMOUNT_TO_BE_PAID>/- is received towards the payment of cleaning septic tank /pit with reference no. <RECEIPT_NO>.You will be notified when an operator is assigned to a request. Please click this link <RECEIPT_LINK> to download the receipt",
            "module": "rainmaker-common",
            "locale": "en_IN"
        },
        {
            "code": "FSM_SMS_DSO_INPROGRESS_DSO_ACCEPT",
            "message": "Dear Applicant, Vehicle <VEHICLE_REG_NO> will be reaching your location to clean the septic tank/pit on <POSSIBLE_SERVICE_DATE> with reference to your application number <2>. You can contact the operator in +91 <DSO_MOBILE_NUMBER>.",
            "module": "rainmaker-common",
            "locale": "en_IN"
        },
        {
            "code": "FSM_SMS_CITIZEN_FEEDBACK_PENDING_COMPLETED",
            "message": "Dear Applicant, Your request for cleaning septic tank/pit is completed.Please take some time to rate us using the link <FSM_APPL_LINK>.",
            "module": "rainmaker-common",
            "locale": "en_IN"
        },
        {
            "code": "FSM_SMS_DSO_REJECTED_DSO_REJECT",
            "message": "Dear Applicant, Your request for cleaning the septic tank/pit is rejected with the reason <FSM_DSO_REJECT_REASON> . Please use this link <NEW_FSM_LINK> to create a new request if needed.",
            "module": "rainmaker-common",
            "locale": "en_IN"
        },
        {
            "code": "FSM_SMS_CANCELED_CANCEL",
            "message": "Dear Applicant, Your request for cleaning the septic tank/pit is cancelled with the reason <FSM_CANCEL_REASON> . Please use this link <NEW_FSM_LINK> to create a new request if needed.",
            "module": "rainmaker-common",
            "locale": "en_IN"
        }
    ]
}
```

```
{
            "code": "PDF_STATIC_LABEL_CONSOLIDATED_RECEIPT_NO_OF_TRIP",
            "message":"No. Of Trips",
            "locale": "en_IN",
            "module": "rainmaker-common"
        },
         {
            "code": "PDF_STATIC_LABEL_CONSOLIDATED_RECEIPT_AMOUNT_PER_TRIP",
            "message":"Amount Per Trip",
            "locale": "en_IN",
            "module": "rainmaker-common"
        },
        {
            "code": "PDF_STATIC_LABEL_CONSOLIDATED_RECEIPT_TOTAL_AMOUNT_DUE",
            "message":"Total Amount Due",
            "locale": "en_IN",
            "module": "rainmaker-common"
        },
        {
            "code": "PDF_STATIC_LABEL_CONSOLIDATED_RECEIPT_BALANCE_AMOUNT_PAID",
            "message":"Balance Amount Paid",
            "locale": "en_IN",
            "module": "rainmaker-common"
        },
        {
            "code": "PDF_STATIC_LABEL_CONSOLIDATED_RECEIPT_ADVANCE_AMOUNT_PAID",
            "message":"Advance Amount Paid",
            "locale": "en_IN",
            "module": "rainmaker-common"
        },
        {
            "code": "PDF_STATIC_LABEL_CONSOLIDATED_RECEIPT_TOTAL_AMOUNT",
            "message":"Total Amount",
            "locale": "en_IN",
            "module": "rainmaker-common"
        }
```

#### Actions & Role Action Mapping <a href="#actions-and-role-action-mapping" id="actions-and-role-action-mapping"></a>

Add Role-Action mapping for the API’s in MDMS. Following are the required entries. They should be mapped to both CITIZEN and appropriate employee roles.

**Action Configuration**

```
{
      "id": {{PLACEHOLDER1}},
      "name": "Create FSM Application",
      "url": "/fsm/v1/_create",
      "displayName": "Apply FSM",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "FSM",
      "code": "null",
      "path": ""
    },
    {
      "id":  {{PLACEHOLDER2}},
      "name": "Search FSM Application",
      "url": "/fsm/v1/_search",
      "displayName": "Search  FSM Appliacations",
      "orderNumber": 1,
      "enabled": false,
      "serviceCode": "FSM",
      "code": "null",
      "path": ""
    },
    {
      "id": {{PLACEHOLDER3}},
      "name": "Update FSM Application",
      "url": "/fsm/v1/_update",
      "displayName": "Update FSM",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "FSM",
      "code": "null",
      "path": ""
    },
{
      "id": {{PLACEHOLDER4}},
      "name": "FSM Application Charge Payment Search",
      "url": "/collection-services/payments/FSM.TRIP_CHARGES/_search",
      "displayName": "FSM Application Charge Payment Search",
      "orderNumber": 1,
      "parentModule": "",
      "enabled": false,
      "serviceCode": "",
      "code": "null",
      "path": ""
    },
     {
      "id": {{PLACEHOLDER5}},
      "name": "FSM Application Audit Search",
      "url": "/fsm/v1/_audit",
      "displayName": "FSM Application Audit serach",
      "orderNumber": 1,
      "parentModule": "",
      "enabled": false,
      "serviceCode": "",
      "code": "null",
      "path": ""
    }, 
    {
      "id": {{PLACEHOLDER6}},
      "name": "Search FSM Application",
      "url": "/fsm/v1/_plainsearch",
      "displayName": "Search  FSM Appliacations",
      "orderNumber": 1,
      "enabled": false,
      "serviceCode": "FSM",
      "code": "null",
      "path": ""
    },
    {
      "id": {{PLACEHOLDER7}},
      "name": "Create FSTP FSTPOperator Mapping",
      "url": "/fsm/plantmap/v1/_create",
      "displayName": "Create FSTP FSTPOperator Map",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "FSM",
      "code": "null",
      "path": ""
    },
    {
      "id": {{PLACEHOLDER8}},
      "name": "Update FSTP FSTPOperator Mapping",
      "url": "/fsm/plantmap/v1/_update",
      "displayName": "Update FSTP FSTPOperator Map",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "FSM",
      "code": "null",
      "path": ""
    },
    {
      "id": {{PLACEHOLDER9}},
      "name": "Search FSTP FSTPOperator Mapping",
      "url": "/fsm/plantmap/v1/_search",
      "displayName": "Search FSTP FSTPOperator Map",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "FSM",
      "code": "null",
      "path": ""
    },
    {
      "id": {{PlaceHolder10}},
      "name": "Inbox Search ofr uI",
      "url": "/inbox/v1/_search",
      "displayName": "Inbox Search",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "inbox",
      "code": "null",
      "path": ""
    }
```

**data/pg/ACCESSCONTROL-ACTIONS-TEST/actions-test.json**

[https://github.com/egovernments/egov-mdms-data/commit/3979963cd0281245c69f015da233a5501fb5f99f](https://github.com/egovernments/egov-mdms-data/commit/3979963cd0281245c69f015da233a5501fb5f99f)

data/pg/ACCESSCONTROL-ACTIONS-TEST/actions-test.json

[https://github.com/egovernments/egov-mdms-data/commit/50b83c118d57f49920c51216a2f6596d81d6ed79](https://github.com/egovernments/egov-mdms-data/commit/50b83c118d57f49920c51216a2f6596d81d6ed79)

data/pg/ACCESSCONTROL-ACTIONS-TEST/actions-test.json

[https://github.com/egovernments/egov-mdms-data/commit/0140a43e110d9677ac69de11d1c1fd1344aa12cd](https://github.com/egovernments/egov-mdms-data/commit/0140a43e110d9677ac69de11d1c1fd1344aa12cd)

**Role Action Mapping**

```
[
 {
    "rolecode": "CITIZEN",
    "actionid": "{{PLACEHOLDER1}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_CREATOR_EMP",
    "actionid": "{{PLACEHOLDER1}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "CITIZEN",
    "actionid": "{{PLACEHOLDER2}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_CREATOR_EMP",
    "actionid": "{{PLACEHOLDER2}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_EDITOR_EMP",
    "actionid": "{{PLACEHOLDER2}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_VIEW_EMP",
    "actionid": "{{PLACEHOLDER2}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_ADMIN",
    "actionid": "{{PLACEHOLDER2}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_DSO",
    "actionid": "{{PLACEHOLDER2}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_DRIVER",
    "actionid": "{{PLACEHOLDER2}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_EMP_FSTPO",
    "actionid": "{{PLACEHOLDER2}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_COLLECTOR",
    "actionid": "{{PLACEHOLDER2}}",
    "actioncode": "",
    "tenantId": "pb"
  },
   {
    "rolecode": "FSM_EDITOR_EMP",
    "actionid": "{{PLACEHOLDER3}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_ADMIN",
    "actionid": "{{PLACEHOLDER3}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_DSO",
    "actionid": "{{PLACEHOLDER3}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_DRIVER",
    "actionid": "{{PLACEHOLDER3}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "CITIZEN",
    "actionid": "{{PLACEHOLDER3}}",
    "actioncode": "",
    "tenantId": "pb"
  },
   {
    "rolecode": "FSM_ADMIN",
    "actionid": "{{PLACEHOLDER4}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_DSO",
    "actionid": "{{PLACEHOLDER4}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_DRIVER",
    "actionid": "{{PLACEHOLDER4}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_COLLECTOR",
    "actionid": "{{PLACEHOLDER4}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "CITIZEN",
    "actionid": "{{PLACEHOLDER4}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_EDITOR_EMP",
    "actionid": "{{PLACEHOLDER4}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_VIEW_EMP",
    "actionid": "{{PLACEHOLDER4}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "CITIZEN",
    "actionid": "{{PLACEHOLDER5}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_CREATOR_EMP",
    "actionid": "{{PLACEHOLDER5}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_EDITOR_EMP",
    "actionid": "{{PLACEHOLDER5}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_VIEW_EMP",
    "actionid": "{{PLACEHOLDER5}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_ADMIN",
    "actionid": "{{PLACEHOLDER5}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_DSO",
    "actionid": "{{PLACEHOLDER5}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_DRIVER",
    "actionid": "{{PLACEHOLDER5}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_EMP_FSTPO",
    "actionid": "{{PLACEHOLDER5}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "FSM_COLLECTOR",
    "actionid": "{{PLACEHOLDER5}}",
    "actioncode": "",
    "tenantId": "pb"
  },
  {
      "rolecode": "FSM_EDITOR_EMP",
      "actionid": {{PLACEHOLDER6}},
      "actioncode": "",
      "tenantId": "pb"
    },
    {
      "rolecode": "FSM_VIEW_EMP",
      "actionid": {{PLACEHOLDER6}},
      "actioncode": "",
      "tenantId": "pb"
    },
    {
      "rolecode": "FSM_ADMIN",
      "actionid": {{PLACEHOLDER6}},
      "actioncode": "",
      "tenantId": "pb"
    },
    {
      "rolecode": "FSM_DSO",
      "actionid": {{PLACEHOLDER6}},
      "actioncode": "",
      "tenantId": "pb"
    },
    {
      "rolecode": "FSM_DRIVER",
      "actionid": {{PLACEHOLDER6}},
      "actioncode": "",
      "tenantId": "pb"
    },
    {
      "rolecode": "FSM_EMP_FSTPO",
      "actionid": {{PLACEHOLDER6}},
      "actioncode": "",
      "tenantId": "pb"
    },
    {
      "rolecode": "FSM_COLLECTOR",
      "actionid": {{PLACEHOLDER6}},
      "actioncode": "",
      "tenantId": "pb"
    },
  {
      "rolecode": "FSM_ADMIN",
      "actionid": {{PLACEHOLDER7}},
      "actioncode": "",
      "tenantId": "pb"
    },
     {
      "rolecode": "FSM_ADMIN",
      "actionid": {{PLACEHOLDER8}},
      "actioncode": "",
      "tenantId": "pb"
    },
    {
      "rolecode": "FSM_EMP_FSTPO",
      "actionid": {{PLACEHOLDER8}},
      "actioncode": "",
      "tenantId": "pb"
    },
    {
      "rolecode": "PT_CEMP",
      "actionid": {{PLACEHOLDER9}},
      "actioncode": "",
      "tenantId": "pb"
    },
    {
      "rolecode": "CITIZEN",
      "actionid": {{PLACEHOLDER9}},
      "actioncode": "",
      "tenantId": "pb"
    },
    {
      "rolecode": "SUPERUSER",
      "actionid": {{PLACEHOLDER9}},
      "actioncode": "",
      "tenantId": "pb"
    }, 
        {
      "rolecode": "FSM_EMP_FSTPO",
      "actionid": {{PlaceHolder10}},
      "actioncode": "",
      "tenantId": "pb"
    },
    {
      "rolecode": "FSM_COLLECTOR",
      "actionid": {{PlaceHolder10}},
      "actioncode": "",
      "tenantId": "pb"
    },
    {
      "rolecode": "FSM_EDITOR_EMP",
      "actionid": {{PlaceHolder10}},
      "actioncode": "",
      "tenantId": "pb"
    },
    {
      "rolecode": "FSM_VIEW_EMP",
      "actionid": {{PlaceHolder10}},
      "actioncode": "",
      "tenantId": "pb"
    },
     {
      "rolecode": "FSM_CREATOR_EMP",
      "actionid": {{PlaceHolder10}},
      "actioncode": "",
      "tenantId": "pb"
    },
    {
      "rolecode": "FSM_ADMIN",
      "actionid": {{PlaceHolder10}},
      "actioncode": "",
      "tenantId": "pb"
    },
    {
      "rolecode": "FSM_DSO",
      "actionid": {{PlaceHolder10}},
      "actioncode": "",
      "tenantId": "pb"
    },
    {
      "rolecode": "PT_CEMP",
      "actionid": {{PlaceHolder10}},
      "actioncode": "",
      "tenantId": "pb"
    },
    {
      "rolecode": "PT_DOC_VERIFIER",
      "actionid": {{PlaceHolder10}},
      "actioncode": "",
      "tenantId": "pb"
    },
    {
      "rolecode": "PT_FIELD_INSPECTOR",
      "actionid": {{PlaceHolder10}},
      "actioncode": "",
      "tenantId": "pb"
    },
    {
      "rolecode": "PT_APPROVER",
      "actionid": {{PlaceHolder10}},
      "actioncode": "",
      "tenantId": "pb"
    },
    {
    "rolecode": "TL_CEMP",
    "actionid": {{PlaceHolder10}},
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "TL_DOC_VERIFIER",
    "actionid": {{PlaceHolder10}},
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "TL_FIELD_INSPECTOR",
    "actionid": {{PlaceHolder10}},
    "actioncode": "",
    "tenantId": "pb"
  },
  {
    "rolecode": "TL_APPROVER",
    "actionid": {{PlaceHolder10}},
    "actioncode": "",
    "tenantId": "pb"
  },
]
```

data/pg/ACCESSCONTROL-ROLEACTIONS/roleactions.json

[https://github.com/egovernments/egov-mdms-data/commit/4d58943d8ab04aa5d8816821406b6e40017ec722](https://github.com/egovernments/egov-mdms-data/commit/4d58943d8ab04aa5d8816821406b6e40017ec722)

data/pg/ACCESSCONTROL-ROLEACTIONS/roleactions.json

[https://github.com/egovernments/egov-mdms-data/commit/1b5962693ac70b7ac56fd312f4b2febab00f9c93](https://github.com/egovernments/egov-mdms-data/commit/1b5962693ac70b7ac56fd312f4b2febab00f9c93)

&#x20;data/pg/ACCESSCONTROL-ROLEACTIONS/roleactions.json

[https://github.com/egovernments/egov-mdms-data/commit/9f9b1340b42f25bca44fdcfa474a3413cc21ec03](https://github.com/egovernments/egov-mdms-data/commit/9f9b1340b42f25bca44fdcfa474a3413cc21ec03)

**Infra Ops Configuration**

Configurations that we can manage through values.yml fsm-calculator in infraops repo as follows:

|                                                                               |                                         |                                                |
| ----------------------------------------------------------------------------- | --------------------------------------- | ---------------------------------------------- |
| **Description**                                                               | **name in values.yml**                  | **Current Value**                              |
| id-gen host, to generate the application number                               | EGOV\_IDGEN\_HOST                       | egov-idgen from egov-service-host              |
| Kafka Consumer Group                                                          | SPRING\_KAFKA\_CONSUMER\_GROUP\_ID      | egov-fsm-service                               |
| kafka topic to which service push data to save new fsm application            | PERSISTER\_SAVE\_FSM\_TOPIC             | save-fsm-application                           |
| kafka topic to which service push data to save workflow status                | PERSISTER\_UPDATE\_FSM\_WORKFLOW\_TOPIC | update-fsm-workflow-application                |
| kafka topic to which service push data to update the existing fsm application | PERSISTER\_UPDATE\_FSM\_TOPIC           | update-fsm-application                         |
| mdms service host                                                             | EGOV\_MDMS\_HOST                        | egov-mdms-service from egov-service-host       |
| billing-service host                                                          | EGOV\_BILLINGSERVICE\_HOST              | billing-service from egov-service-host         |
| fsm-calculator service host                                                   | EGOV\_FSM\_CALCULATOR\_HOST             | fsm-calculator from egov-service-host          |
| workflow v2 service host                                                      | WORKFLOW\_CONTEXT\_PATH                 | egov-workflow-v2 from egov-service-host        |
| ui host, to return send the url of new application in sms notification        | EGOV\_UI\_APP\_HOST                     | egov-services-fqdn-name from egov-service-host |
| vendor service host, to get DSO details                                       | EGOV\_VENDOR\_HOST                      | vendor from egov-service-host                  |
| Vehicle service host, to get vehicle details and manage vehicleTrip           | EGOV\_VEHICLE\_HOST                     | vehicle from egov-service-host                 |
| Collection service host, to get the payment details                           | EGOV\_COLLECTION\_SERVICE\_HOST         | collection-services from egov-service-host     |
| localization service host, to get the locale data                             | EGOV\_LOCALIZATION\_HOST                | egov-localization from egov-service-host       |
| user service host, to get the locale data                                     | EGOV\_USER\_HOST                        | egov-user from egov-service-host               |
| pdf service host, to get the locale data                                      | EGOV\_PDF\_HOST                         | pdf-service from egov-service-host             |
| url shortening service host, to get the short url for the long once           | EGOV\_URL\_SHORTNER\_HOST               | egov-url-shortening from egov-service-host     |

**Sample values.yml**

```
- name: EGOV_IDGEN_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-idgen
  - name: EGOV_MDMS_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-mdms-service
  - name: EGOV_URL_SHORTNER_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-url-shortening
  - name: EGOV_PDF_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: pdf-service
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
  - name: EGOV_LOCALIZATION_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-localization
  - name: EGOV_BILLINGSERVICE_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: billing-service
  - name: EGOV_COLLECTION_SERVICE_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: collection-services
  - name: EGOV_FSM_CALCULATOR_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: fsm-calculator
  - name: EGOV_VEHICLE_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: vehicle
  - name: EGOV_VENDOR_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: vendor
  - name: EGOV_UI_APP_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-config
        key: egov-services-fqdn-name
  - name: WORKFLOW_CONTEXT_PATH
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key: egov-workflow-v2
  - name: WORKFLOW_TRANSITION_PATH
    value: "egov-workflow-v2/egov-wf/process/_transition"
  - name: EGOV_IDGEN_FSM_APPLICATIONNUM_FORMAT
    value: "[CITY.CODE]-FSM-[cy:yyyy-MM-dd]-[SEQ_EGOV_FSM]"
  - name: SPRING_KAFKA_CONSUMER_GROUP_ID
    value: egov-fsm-service
  - name: PERSISTER_SAVE_FSM_TOPIC
    value: save-fsm-application
  - name: PERSISTER_UPDATE_FSM_TOPIC
    value: update-fsm-application
  - name: PERSISTER_UPDATE_FSM_WORKFLOW_TOPIC
    value: update-fsm-workflow-application


```

**Users**

|               |                   |                                                                                                                                                    |                                                                                                                                           |
| ------------- | ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| **User**      | **Role**          | **Description**                                                                                                                                    | **How to create**                                                                                                                         |
| FSM Creator   | FSM\_CREATOR\_EMP | Can create FSM Application on behalf of Citizen                                                                                                    | Through HRMS with role                                                                                                                    |
| FSM Editor    | FSM\_EDITOR\_EMP  | <ul><li>Can edit the application created by citizen for demand generation</li><li>Assing/ Re-Assign DSO</li><li>Complete the Application</li></ul> | Through HRMS with role                                                                                                                    |
| FSM Admin     | FSM\_ADMIN        | <ul><li>Can cancel the application at any stage of workflow</li></ul>                                                                              | Through HRMS with role                                                                                                                    |
| DSO           | FSM\_DSO          | <ul><li>can accept/Reject the assigned Application</li><li>can complete the FSM Application</li></ul>                                              | Through vendor service, use the create DSO Request from [postman Collection](https://www.getpostman.com/collections/2d55f98479499672a23e) |
| FSTP Operator | FSM\_EMP\_FSTPO   | <ul><li>Can mark the vehicle Trip as disposed. Not FSM Service User</li></ul>                                                                      | Through HRMS with role                                                                                                                    |
| Collector     | FSM\_COLLECTOR    | <ul><li>Can collect the payment amount for application based on demand</li></ul>                                                                   | Through HRMS with role                                                                                                                    |

* User with userType employee and role FSM\_CREATOR\_EMP role,

### Integration <a href="#integration" id="integration"></a>

#### Integration Scope <a href="#integration-scope" id="integration-scope"></a>

FSM can be integrated with any ULB or system which wants to track the FSM application. The organisations can customise the workflow depending on their product requirements.

#### Integration Benefits <a href="#integration-benefits" id="integration-benefits"></a>

* Easy tracking and resolution FSM Application
* Configurable workflow according to client requirement

#### Steps to Integration <a href="#steps-to-integration" id="steps-to-integration"></a>

1. Citizen/ULB Employee can file Application request using the /fsm/v1/\_create
2. Organisation or System can search the FSM Applications using /fsm/v1/\_searchendpoint
3. Once the Application is files the organisation or system can call /fsm/v1/\_update endpoint to move the application further in workflow until it get resolved

**Inbox API**

* Introduced new inbox service to get the FSM applications in registered ULB employee inbox, With this ULB employee can track the application or perform the actions based on employee role.
* ULB employees can also apply the filter to check the particular state or applications or any other filter as required.

**FSM apply as service**

As of now we are providing FSM as an adhoc service.To avoid multiple times, a user has to create the FSM request every time. In the system itself after some days, we will create the same FSM application and if the user wants a service, he/she will pay the amount.

**MDMS changes**

As we mentioned above, we need to define the time parameter, in order to create a periodic application. For that we added the periodic service master where we configure the time limit and whether the schedular is enabled or not. Please find the below configuration and location.

{% embed url="https://github.com/egovernments/egov-mdms-data/blob/DEV/data/pb/amritsar/FSM/PeriodicService.json" %}

```
{ "tenantId": "pb.amritsar",
"moduleName": "FSM",
"PeriodicService":[
{
"timeLimit" : 864000000,
"isSchedularConfiguration":true
}
]
}

```

cronjob will read the cron job’s configured in the cronjobapiconfig.json and based on the schedular time it will call the API which is configured. Please find the below configuration and file location.

{% embed url="https://github.com/egovernments/egov-mdms-data/blob/DEV/data/pb/common-masters/CronJobAPIConfig.json" %}

```
{ "jobName": "daily",
"active": "true",
"method": "POST",
"url": "http://fsm.egov:8080/fsm/v1/_schedular",
"payload": {
"RequestInfo": "{DEFAULT_REQUESTINFO}" },
"header": { "Content-Type": "application/json"
}

```

We are using the fsm/v1/\_schedular api. This api will read the master data for each tenant and based on the time limit configured for that tenant, it will get all eligible aplications and create periodic applications for those fsm applications.

data/pb/FSM/AdvancePayment.json

[SM-499 : mdms file for advanceBalance and cancellationfee · egovernments/egov-mdms-data@3b3233e](https://github.com/egovernments/egov-mdms-data/commit/3b3233e8f3e812fb4fe2833fa24d1c6b92078c9f)

[Update AdvancePayment.json · egovernments/egov-mdms-data@a864a90](https://github.com/egovernments/egov-mdms-data/commit/a864a90735749d0ec17e6df75fc80b831653551d)

[Update CancellationFee.json · egovernments/egov-mdms-data@3a614e5](https://github.com/egovernments/egov-mdms-data/commit/3a614e5273397a25d0d5cdefc95fc75d04f0088f)

master-config.json

[SM-499 adding advancepayment and cancellationfee · egovernments/egov-mdms-data@c4efb2e](https://github.com/egovernments/egov-mdms-data/commit/c4efb2e890fcc56fbeb969a9162c0d11aad03dec)

**Infra changes**

We added a new chart called mdms-read-cronjob. Please find the below chart location:

[https://github.com/egovernments/DIGIT-DevOps/tree/master/deploy-as-code/helm/charts/utilities/mdms-read-cronjob](https://github.com/egovernments/DIGIT-DevOps/tree/master/deploy-as-code/helm/charts/utilities/mdms-read-cronjob)

### Interaction Diagram <a href="#interaction-diagram" id="interaction-diagram"></a>

#### 1. Advance Amount Workflow

#### 2. Zero Price Application Workflow

### Reference Docs <a href="#reference-docs" id="reference-docs"></a>

#### Doc Links <a href="#doc-links" id="doc-links"></a>

|                                     |                                                                                                                                                                |
| ----------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Title**                           | **Link**                                                                                                                                                       |
| Workflow Technical Document         | [Workflow Service](https://digit-discuss.atlassian.net/wiki/spaces/DD/pages/664174657/Workflow+Service)                                                        |
| User Technical Document             | [User Service](https://digit-discuss.atlassian.net/wiki/spaces/DD/pages/669450371/User+Service)                                                                |
| MDMS Technical Document             | **NEEDS TO BE UPDATED**                                                                                                                                        |
| IDGen Technical Document            | **NEEDS TO BE UPDATED**                                                                                                                                        |
| Localization Technical Document     | **NEEDS TO BE UPDATED**                                                                                                                                        |
| Persister Technical Document        | **NEEDS TO BE UPDATED**                                                                                                                                        |
| SMS Notification Technical Document | **NEEDS TO BE UPDATED**                                                                                                                                        |
| HRMS Technical Document             | **NEEDS TO BE UPDATED**                                                                                                                                        |
| API Contract                        | [FSM API Contract](https://editor.swagger.io/?url=https://raw.githubusercontent.com/egovernments/municipal-services/master/docs/fsm/Fsm\_Apply\_Contract.yaml) |
| Postman Collection                  | [FSM Postman Collection](https://www.getpostman.com/collections/8b9eb951a810486f41a4)                                                                          |

#### API List <a href="#api-list" id="api-list"></a>

| <h4>Title </h4>           | Link                                                                                                                                                                                                                                                           |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| /fsm/v1/\_create          | [https://api.postman.com/collections/23418568-946a158e-9391-44b2-9d2b-48f30ea8cd63?access\_key=PMAT-01GSPRPC338T9RR0GAKTRCRDP8](https://api.postman.com/collections/23418568-946a158e-9391-44b2-9d2b-48f30ea8cd63?access\_key=PMAT-01GSPRPC338T9RR0GAKTRCRDP8) |
| /fsm/v1/\_update          | [https://api.postman.com/collections/23418568-946a158e-9391-44b2-9d2b-48f30ea8cd63?access\_key=PMAT-01GSPRPC338T9RR0GAKTRCRDP8](https://api.postman.com/collections/23418568-946a158e-9391-44b2-9d2b-48f30ea8cd63?access\_key=PMAT-01GSPRPC338T9RR0GAKTRCRDP8) |
| /fsm/v1/\_search          | [https://www.getpostman.com/collections/a51486db12539a2aa597](https://www.getpostman.com/collections/a51486db12539a2aa597)                                                                                                                                     |
| /fsm/v1/\_audit           | [https://www.getpostman.com/collections/a51486db12539a2aa597](https://www.getpostman.com/collections/a51486db12539a2aa597)                                                                                                                                     |
| /fsm/v1/\_plainsearch     | [https://www.getpostman.com/collections/a51486db12539a2aa597](https://www.getpostman.com/collections/a51486db12539a2aa597)                                                                                                                                     |
| /fsm/plantmap/v1/\_create | [https://www.getpostman.com/collections/a51486db12539a2aa597](https://www.getpostman.com/collections/a51486db12539a2aa597)                                                                                                                                     |
| /fsm/plantmap/v1/\_update | [https://www.getpostman.com/collections/a51486db12539a2aa597](https://www.getpostman.com/collections/a51486db12539a2aa597)                                                                                                                                     |
| /fsm/plantmap/v1/\_search | [https://www.getpostman.com/collections/a51486db12539a2aa597](https://www.getpostman.com/collections/a51486db12539a2aa597)                                                                                                                                     |
| /inbox/v1/\_search        | [https://www.getpostman.com/collections/a51486db12539a2aa597](https://www.getpostman.com/collections/a51486db12539a2aa597)                                                                                                                                     |
| /fsm/v1/\_schedular       | [https://www.getpostman.com/collections/a51486db12539a2aa597](https://www.getpostman.com/collections/a51486db12539a2aa597)                                                                                                                                     |

\


[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)](http://creativecommons.org/licenses/by/4.0/)All content on this page by [eGov Foundation ](https://egov.org.in/)is licensed under a [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/).
