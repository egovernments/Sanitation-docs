# FSM Service

## Configuration Details <a href="#configuration-details" id="configuration-details"></a>

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

#### Fsm v 1.4 Persister Configuration

1. sanitation/egov-persister/fsm-persister.yaml - file [link](https://github.com/egovernments/configs/blob/UNIFIED-UAT/sanitation/egov-persister/fsm-persister.yaml)
2. &#x20;sanitation/egov-persister/vendor-persister.yaml - file [link](https://github.com/egovernments/configs/blob/UNIFIED-UAT/sanitation/egov-persister/vendor-persister.yaml)

## MDMS Configuration <a href="#mdms-configuration-hardbreak" id="mdms-configuration-hardbreak"></a>

Add master data in the MDMS service with module name as FSM and restart the egov-mdms-service.  Following is a sample master data for Application Channel (Source):

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

Checklist (To be answered by a citizen while rating):

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

Configuration (At the application level):

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

FSTP Plant Information (For each city):

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

Pit Type (Type of pit):

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

Property Type:

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

Slums (Mapped to the locality of the city):

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

PaymentType (Payment preference type):

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

Following are the changes that need to be integrated in dashboard-analytics, and restart the “dashboard-analytics” service

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


#### **Fsm v1.4 MDMS Configuration**

1. data/pg/FSM/SanitationWorkerEmployer.json - file [link](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/pg/FSM/SanitationWorkerEmployer.json)
2. data/pg/FSM/SanitationWorkerEmploymentType.json - file [link](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/pg/FSM/SanitationWorkerEmploymentType.json)
3. data/pg/FSM/SanitationWorkerFunctionalRoles.json - file [link](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/pg/FSM/SanitationWorkerFunctionalRoles.json)&#x20;
4. data/pg/FSM/SanitationWorkerSkills.json - file [lin](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/pg/FSM/SanitationWorkerSkills.json)
5. inbox v2 mdms changes

```
 {
      "module": "fsm",
      "index": "fsm-application",
      "allowedSearchCriteria": [
        {
          "name": "tenantId",
          "path": "Data.tenantId.keyword",
          "isMandatory": false,
          "operator": "EQUAL"
        },
        {
          "name": "status",
          "path": "Data.currentProcessInstance.state.uuid.keyword",
          "isMandatory": false
        },
        {
          "name": "mobileNumber",
          "path": "Data.mobileNumber.keyword",
          "isMandatory": false
        },
        {
          "name": "locality",
          "path": "Data.locality.keyword",
          "isMandatory": false
        },
        {
          "name": "assignee",
          "path": "Data.currentProcessInstance.assignes.uuid.keyword",
          "isMandatory": false
        },
        {
          "name": "applicationNos",
          "path": "Data.applicationNo.keyword",
          "isMandatory": false,
          "operator": "WILDCARD"
        },
        {
          "name": "fromDate",
          "path": "Data.auditDetails.createdTime",
          "isMandatory": false,
          "operator": "GTE"
        },
        {
          "name": "toDate",
          "path": "Data.auditDetails.createdTime",
          "isMandatory": false,
          "operator": "LTE"
        }
      ],
      "sortBy": {
        "path": "Data.@timestamp",
        "defaultOrder": "DESC"
      },
      "sourceFilterPathList": [
        "Data.currentProcessInstance",
        "Data.auditDetails",
        "Data.additionalDetails",
        "Data.tenantId",
        "Data.applicationNo",
        "Data.workflow",
        "Data.locality"
      ]
    }
```

## Business Service/Workflow Configuration

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

For post-pay new business service, FSM\_POST\_PAY\_SERVICE has been created. Create businessService (workflow configuration) using the /businessservice/\_create. Following is the product configuration for FSM\_POST\_PAY\_SERVICE:

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

In the system, the FSM\_POST\_PAY\_SERVICE and FSM (that is, the above two business services) are removed and we have introduced a new business service for advance payment application and zero price application.

For advance new business service, FSM\_ADVANCE\_PAY\_SERVICE has been created.

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

For advance zero new business service PAY\_LATER\_SERVICE has been created.

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

## Localisation Setup <a href="#localization-setup" id="localization-setup"></a>

Using/localisation/messages/v1/\_upsert, add localisation (templates) for notification messages to be sent. Following are the product notification templates:

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
        },
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
    ]
}
```

## Actions & Role-Action Mapping <a href="#actions-and-role-action-mapping" id="actions-and-role-action-mapping"></a>

Add role-action mapping for the API’s in MDMS. Following are the required entries. They should be mapped to both CITIZEN and the appropriate employee roles.

#### **Action Configuration**

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

[https://github.com/egovernments/egov-mdms-data/commit/0140a43e110d9677ac69de11d1c1fd1344aa12cd](https://github.com/egovernments/egov-mdms-data/commit/0140a43e110d9677ac69de11d1c1fd1344aa12cd)&#x20;

**Plant user mapping**

1. data/pg/ACCESSCONTROL-ACTIONS-TEST/actions-test.json

```
{
      "id": 388,
      "name": "MDMS",
      "url": "/mdms-v2/v2/_update/FSM.FSTPPlantInfo",
      "displayName": "Update PQM.QualityTestLab",
      "orderNumber": 1,
      "parentModule": "",
      "enabled": true,
      "serviceCode": "MDMS",
      "code": "null",
      "path": ""
    },
    {
      "id": 389,
      "name": "MDMS",
      "url": "/mdms-v2/v2/_create/FSM.FSTPPlantInfo",
      "displayName": "Update PQM.QualityTestLab",
      "orderNumber": 1,
      "parentModule": "",
      "enabled": true,
      "serviceCode": "MDMS",
      "code": "null",
      "path": ""
    }
```

## **Role-Action Mapping**

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

Plant user mapping

1. data/pg/ACCESSCONTROL-ROLEACTIONS/roleactions.json

```
{
      "rolecode": "MDMS_ADMIN",
      "actionid": 388,
      "actioncode": "",
      "tenantId": "pg"
    },
    {
      "rolecode": "MDMS_ADMIN",
      "actionid": 389,
      "actioncode": "",
      "tenantId": "pg"
    }
```

#### **Devops Changes**

For a new environment these changes are required.

path:- deploy-as-code/helm/charts/sanitation/fsm/values.yaml

```
- name: EGOV_MDMS_V2_HOST
    valueFrom:
      configMapKeyRef:
        name: egov-service-host
        key:  mdms-service-v2
```

####
