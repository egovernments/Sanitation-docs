# Technical Specification: Urban-Rural Convergence

## Overview

Initiative to provide access to sanitation services to all gram panchayats (GPs) via urban local bodies (ULBs) located closest to them.

### Objective

DIGIT Sanitation plans to provide a provision of sanitation services to rural areas to their nearby cities.

### Author

| Name     | Role           | Department |
| -------- | -------------- | ---------- |
| Aman Jha | Technical Lead | FSM        |

### Document History

| Date       | Version | Document version and history                  | Document author |
| ---------- | ------- | --------------------------------------------- | --------------- |
| 16-02-2023 | 1.0     | Initial version                               | Kapil Gupta     |
| 17-02-2023 | 1.1     | Updated the solution approach based on review | Aman Jha        |

### Approvals

| Date       | Approver name | Remarks                                                                                                                                                                                                                                                      |
| ---------- | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 15-02-2023 | Ghanshyam     | There is no need to use additional MDMS for Urban-Rural Convergence (URC). We can add the gram panchayat hierarchy in the existing MDMS boundary-data.json.                                                                                                  |
| 21-02-2023 | Ghanshyam     | We can go ahead with the approach in impel, but in product we can generalise this hierarchy. To do that, modification is required in location-service. We can also build the dynamic component in UI for showing a relative dropdown based on the hierarchy. |

## Use Case

As a ULB employee, he/she is creating applications to cater to the sanitation needs of local communities in urban areas. Similarly, he/she should also cater to the same sanitation needs of rural bodies which are close to the urban regions.

ULB employees need a provision in a system while creating a new application whereby they can either choose local municipalities or urban supported villages. Based on their choice, they will be able to select either locality/mohalla or gram panchayat (GP) areas from the respective master data dropdown list. The caveat here is if a ULB employee chooses a GP, then the trip amount field should be editable so that he/she can fill any logical amount based on the offline calculation instead of an auto-calculated amount that is already there in an application in case of urban bodies.

ULB employees or DSO operators should also be able to edit the number of trips. The final amount should be a multiple of the initial amount entered into an application with the number of trips.

### **UI/UX Wireframe** ![](https://lh6.googleusercontent.com/CjrFHwVvdMskb\_fIgRikAcRe1Rey5Fi1t8ayJ67ESmld5BWaN8VDA1x2rGwCW63psGJMli\_CHMWg9-c\_wtwTM8OXHw6xIzi7DGC3SSHSLBNdJVSgUHb0jx72L0lfIl1l8Uy-o\_dnqZfDwUUdVZuZ8vs)

### Technical Components & Design

*   Need to update MDMS data: Boundary-data.json

    \- Need to add a new child hierarchy for GP under city which will be parallel to a locality. A sample is given at the end of this document.
*   System will use the below URL to fetch the localities or GPs and their corresponding villages.

    \- In the case of localities, pass boundaryType as “Locality”.

    * https://dev.digit.org/egov-location/location/v11/boundarys/\_search?hierarchyTypeCode=REVENUE\&boundaryType=Locality\&tenantId=pb.amritsar

    \- In the case of GP/villages, pass the boundaryType as “GP”.

    * https://dev.digit.org/egov-location/location/v11/boundarys/\_search?hierarchyTypeCode=REVENUE\&boundaryType=GP\&tenantId=pb.amritsar
*   By default, the 'Urban' option will be pre-selected in the radio button in the above wireframe and the dropdown will have the locality/mohalla master data (existing behaviour). If an employee selects “ULB supported village”, then the locality/mohalla dropdown will be replaced by GPs and the village dropdown data on the fly.

    \- Also, the "Amount per Trip" field will be editable with no pre-defined calculated value. Hence, the below API will not get called for URC flow (when “ULB supported village” is selected”):

[https://dev.digit.org/fsm-calculator/v1/billingSlab/\_search?tenantId=pb.amritsar\&propertyType=RESIDENTIAL.APARTMENT\&capacity=2000\&slum=NO&\_=1676626310996](https://dev.digit.org/fsm-calculator/v1/billingSlab/\_search?tenantId=pb.amritsar\&propertyType=RESIDENTIAL.APARTMENT\&capacity=2000\&slum=NO&\_=1676626310996)

* Need to add configuration (mdms: UrcConfig.json) for configuring URC feature (Enable/Disable) and facilitating the switch on/off feature for the URC. MDMS data will be as shown below:

```
{
    "tenantId": "pg.angul",
    "moduleName": "FSM",
    "urcConfig": [{
        "URCEnable": true
    }
    ]
}
```

*   The above MDMS have two configurations:

    \- URCEnable: This flag will be used to enable or disable the URC flow altogether. If this flag is false, then we will not have URC flow (no radio buttons will come) and the existing flow (urban) will happen as it is. If this flag is true, then the radio button will appear. By default, the 'Urban' option will be selected and if the user selects “ULB supported village", then the URC flow will continue as mentioned in above points.
* Need to store GP and Village as part of additional details(in eg\_fsm\_address). Also add one more key as boundarytype in additional details to capture (Locality or GP/Village) to determine if the application created is for RURAL or not so that in the near future it will be helpful for the analytics and statistics in dashboards.
* Default value for this key(boundaryType) will be Locality to support backward compatibility
* Add Vehicle log would also have the option to select Urban (Default option) or Rural. If Rural gets selected the text name of an element would be replaced from “Locality” to “Gram Panchayat” for a text field.
* Introduction of a boundarytype as additionalDetails in vehicle\_trip table to capture if the vehicle log is created for GP or not.
  * Default value for this column will be Locality to support backward compatibility.

**Sample MDMS (boundary-data.json)**

```
{
  "tenantId": "pb.amritsar",
  "moduleName": "egov-location",
  "TenantBoundary": [{
      "hierarchyType": {
        "code": "REVENUE",
        "name": "REVENUE"
      },
      "boundary": {
        "id": 1,
        "boundaryNum": 1,
        "name": "Angul",
        "localname": "Angul",
        "longitude": null,
        "latitude": null,
        "label": "City",
        "code": "od.angul",
        "children": [{
            "id": "2",
            "boundaryNum": 1,
            "name": "Baniabahal",
            "localname": "Baniabahal",
            "longitude": null,
            "latitude": null,
            "label": "Locality",
            "code": "VIL1"
          },
          {
            "id": "3",
            "boundaryNum": 1,
            "name": "Hulurisinga",
            "localname": "Hulurisinga",
            "longitude": null,
            "latitude": null,
            "label": "Locality",
            "code": "VIL2"
          },
          {
            "id": "4",
            "boundaryNum": 1,
            "name": "Angul town",
            "localname": "Angul town",
            "longitude": null,
            "latitude": null,
            "label": "Locality",
            "code": "VIL3"
          },
          {
            "id": "5",
            "boundaryNum": 1,
            "name": "Other",
            "localname": "Other",
            "longitude": null,
            "latitude": null,
            "label": "Locality",
            "code": "VIL4"
          },
          {
            "id": 6,
            "boundaryNum": 1,
            "name": "GP 1",
            "localname": "GP1",
            "longitude": null,
            "latitude": null,
            "label": "GP",
            "code": "GP1",
            "children": [{
                "id": 11,
                "boundaryNum": 1,
                "name": "Village 1",
                "localname": "Village local 1",
                "longitude": 74.871552,
                "latitude": 31.63089,
                "label": "Village",
                "code": "SUN04",
                "pincode": [143001],
                "area": "V-Area1",
                "children": []
              },
              {
                "id": 12,
                "boundaryNum": 1,
                "name": "Village 2",
                "localname": "Village local 2",
                "longitude": null,
                "latitude": null,
                "label": "Village",
                "code": "SUN11",
                "pincode": [143001],
                "area": "V-Area1",
                "children": []
              }
            ]
          },
          {
            "id": 8,
            "boundaryNum": 1,
            "name": "GP 2",
            "localname": "GP2",
            "longitude": null,
            "latitude": null,
            "label": "GP",
            "code": "GP2",
            "children": [{
                "id": 13,
                "boundaryNum": 1,
                "name": "Village 3",
                "localname": "Village local 3",
                "longitude": 74.871552,
                "latitude": 31.63089,
                "label": "Village",
                "code": "SUN04",
                "pincode": [143001],
                "area": "V-Area1",
                "children": []
              },
              {
                "id": 14,
                "boundaryNum": 1,
                "name": "Village 4",
                "localname": "Village local 4",
                "longitude": null,
                "latitude": null,
                "label": "Village",
                "code": "SUN11",
                "pincode": [143001],
                "area": "V-Area1",
                "children": []
              }
            ]
          }
        ]
      }
    },
    {
      "hierarchyType": {
        "code": "ADMIN",
        "name": "ADMIN"
      },
      "boundary": {
        "id": 1,
        "boundaryNum": 1,
        "name": "Angul",
        "localname": "Angul",
        "longitude": null,
        "latitude": null,
        "label": "City",
        "code": "od.angul",
        "children": [{
            "id": "2",
            "boundaryNum": 1,
            "name": "Baniabahal",
            "localname": "Baniabahal",
            "longitude": null,
            "latitude": null,
            "label": "Locality",
            "code": "VIL1"
          },
          {
            "id": "3",
            "boundaryNum": 1,
            "name": "Hulurisinga",
            "localname": "Hulurisinga",
            "longitude": null,
            "latitude": null,
            "label": "Locality",
            "code": "VIL2"
          },
          {
            "id": "4",
            "boundaryNum": 1,
            "name": "Angul town",
            "localname": "Angul town",
            "longitude": null,
            "latitude": null,
            "label": "Locality",
            "code": "VIL3"
          }
        ]
      }
    }
  ]
}
```
