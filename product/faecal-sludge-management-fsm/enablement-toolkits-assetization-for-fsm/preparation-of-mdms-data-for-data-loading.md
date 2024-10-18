# Preparation of MDMS Data for Data Loading

This document shows the preparation of the mdms changes be to done for data loading.

1. To add data in [tenant/tenants.json](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/tenant/tenants.json) - For showing the tenant at login screen\
   Sample Data :

| DETAILS                                                    | DESCRIPTION                                                                                                        | DATA FROM ULB                                                     |
| ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------- |
| Name of ULB                                                | (E.g.: Berhampur Municipal Corporation or Balasore Municipality or Banki NAC)                                      | ANGUL MUNICIPALITY                                                |
| ULB Census Code (Optional)                                 | ->                                                                                                                 |                                                                   |
| PIN codes covered within ULB Boundary (separate by commas) | (Eg.: 759001, 759013)                                                                                              | 759122, 759132, 759123, 759143                                    |
| District Name                                              | ->                                                                                                                 | ANGUL                                                             |
| District Code (Optional)                                   | ->                                                                                                                 |                                                                   |
| Helpline Phone numbers for Septic tank cleaning            | (Write both Landline with Code and Mobile No. if you have, separated by commas.) (Eg.: 0674-234563, 91-9876786543) | 14420                                                             |
| ULB's full postal Address                                  | ->                                                                                                                 | AT/PO-AMLAPADA, DIST-ANGUL, PIN-759122                            |
| ULB Email Address                                          | ->                                                                                                                 | [angulmunicipality@gmail.com](mailto:angulmunicipality@gmail.com) |

&#x20;

Example : Create a json for new ulb and Add required details given.

```json
{
    "code": "od.angul",
    "name": "Angul",
    "description": "Angul",
    "logoId": "https://digitaldesksujog051120.blob.core.windows.net/assets/Logos/odlogo.png",
    "imageId": null,
    "domainUrl": "https://sujog.odisha.gov.in",
    "type": "CITY",
    "twitterUrl": null,
    "facebookUrl": null,
    "emailId": "angulmunicipality@gmail.com",
    "OfficeTimings": {
        "Mon - Fri": "9.00 AM - 6.00 PM",
        "Sat": "9.00 AM - 12.00 PM"
    },
    "pincode": [
        759122,
        759132,
        759123,
        759143
    ],
    "city": {
        "name": "Angul",
        "localName": null,
        "districtCode": "Angul",
        "districtName": "Angul",
        "regionName": "Angul",
        "ulbGrade": "Angul Municipality",
        "longitude": 0,
        "latitude": 0,
        "shapeFileLocation": null,
        "captcha": null,
        "code": "ANG",
        "ddrName": "Angul",
        "wsBillHeaderLine1": "OFFICE OF THE AE/JE",
        "wsBillHeaderLine2": "PUBLIC HEALTH ENGINEERING ORGANIZATION : Angul",
        "districtTenantCode": "od.angul"
    },
    "address": "AT/PO-Amlapada,Dist-Angul, Pin-759122",
    "contactNumber": "",
    "helpLineNumber": "14420"
}
```

2.  Adding in [tenant/citymodule.json](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/tenant/citymodule.json) - To enable ulb to create application,add new tenant code in FSM module.\


    ```json
    {
        "module": "FSM",
        "code": "FSM",
        "active": true,
        "tenants": [
            {
                "code": "pg.citya"
            },
            {
                "code": "pg.angul"
            }
        ]
    }
    ```
3. Adding FSTP details in [FSM/FSTPPlantInfo.json](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/FSM/FSTPPlantInfo.json)\
   Required Details:

| DETAILS                                     | DESCRIPTION                | DATA FROM ULB                          |
| ------------------------------------------- | -------------------------- | -------------------------------------- |
| FSTP Plant Address                          | ->                         | NUAMAUSA, PANCHAMAHALLA, ANGUL, 759132 |
| B.2. FSTP Installed Capacity in Kilo-Liters | (Eg.: 45 KLD)              | 18 KLD                                 |
| B.3. Plant Operation Timing Duration        | (Eg.: 09:00 AM - 08:00 PM) | 9.00AM-5.00PM                          |

&#x20;

Eg.

```json
{
    "PlantCode": "ANG_001",
    "PlantName": "ANGUL Plant",
    "active": true,
    "PlantType": "SeTP",
    "PlantLocation": "ANGUL",
    "PlusCode": "R3RW+7JQ",
    "PlantOperationalTimings": "09.00am-05.00pm",
    "PlantOperationalCapacityKLD": "18",
    "ULBS": "pg.angul"
}
```

\
\


| **Field Name**        | **Description**                                | **Comments**                                                                                                                                                                                                                                                                                              |
| --------------------- | ---------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Plus code             | Copy paste the plus code of the plant location | <p>Go to google maps , search for the plant and in the left panel you will have option to copy the plus code of the location.</p><p>Plus code is a simple digital address based out of latitude and longitude</p>                                                                                         |
| Unique Code for Plant | This will be an unique code for the SeTP plant | <p>For example : If the plant is the ANGUL Plant then the there can be 3 alphabets to identify the city "ANG_001 "</p><p>001 - is a running sequence number for a state.If the first row is 001 the second row can be 002.</p><p>If the second row plant is from PURI then the code can be "PURI_002"</p> |

&#x20;

*   Creating Boundary data for Gram Panchayat in [ULBNAME/egov-location/boundary-data.json](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/anandapur/egov-location/boundary-data.json)\
    The GP details will be given in Annexure-5,in hierarchyType - REVENUE ,add GP data after locality data.\
    The json format of GP is :\


    ```json
    {
        "id": 6,
        "boundaryNum": 1,
        "name": "GP 1",
        "localname": "GP1",
        "longitude": null,
        "latitude": null,
        "label": "GP",
        "code": "GP1",
        "children": [
            {
                "id": 11,
                "boundaryNum": 1,
                "name": "Village 1",
                "localname": "Village local 1",
                "longitude": 74.871552,
                "latitude": 31.63089,
                "label": "Village",
                "code": "VIL1",
                "pincode": [
                    143001
                ],
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
                "code": "VIL2",
                "pincode": [
                    143001
                ],
                "area": "V-Area1",
                "children": []
            }
        ]
    },
    ```

_**Example:**_

```json
{
    "tenantId": "pg.rourkela",
    "moduleName": "egov-location",
    "TenantBoundary": [
        {
            "hierarchyType": {
                "code": "REVENUE",
                "name": "REVENUE"
            },
            "boundary": {
                "id": 1,
                "boundaryNum": 1,
                "name": "Rourkela",
                "localname": "Rourkela",
                "longitude": null,
                "latitude": null,
                "label": "City",
                "code": "pg.rourkela",
                "children": [
                    {
                        "id": "2",
                        "boundaryNum": 1,
                        "name": "Pradhanpalli",
                        "localname": "Pradhanpalli",
                        "longitude": null,
                        "latitude": null,
                        "label": "Locality",
                        "code": "VIL1"
                    },
                    {
                        "id": "3",
                        "boundaryNum": 1,
                        "name": "Other",
                        "localname": "Other",
                        "longitude": null,
                        "latitude": null,
                        "label": "GP",
                        "code": "OTH1",
                        "children": []
                    }
                ]
            }
        }
    ]
}
```

\
**Steps to create the jsons of GP data** -

* The GP data is given in excel format.
* Copy all the GP’s list and make an excel with format given below

| id | boundaryNum | name      | localname | longitude | latitude | label | code |
| -- | ----------- | --------- | --------- | --------- | -------- | ----- | ---- |
| 10 | 1           | Kodama    | Kodama    | null      | null     | GP    | GUD5 |
| 11 | 1           | M K Rai   | M K Rai   | null      | null     | GP    | GUD6 |
| 12 | 1           | Madhubana | Madhubana | null      | null     | GP    | GUD7 |

* The name and localname is the GP name provided
* The label is always GP and boundaryNum is 1.
* Id is unique for each GP and should be in sequential order.
* Provide a proper format of GP code according to GPname.
* Convert the excel data into json using excel-json online converter.
* Add the GP data after locality data in [boundary-data.json](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/anandapur/egov-location/boundary-data.json) file .
* Check the format once,change id into string if it is in integer format.
* Add **"children": \[]** for each GP separately after converting to json.

&#x20;

4.  Adding Slum Details in [ULBNAME/FSM/Slum.json](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/anandapur/FSM/Slum.json)\
    The name of the slums will be provided.The format of slum adding in mdms is:&#x20;



    ```json
    {
        "name": "slumname",
        "active": true,
        "code": "CODE001",
        "locality": "VIL1"
    }
    ```

&#x20;

**Steps To Create the jsons of Slum data** :\
The slum data is provided in excel format.

* Make an excel with with given format

| name                      | active | code    | locality |
| ------------------------- | ------ | ------- | -------- |
| Adibasi Sahi(Poda khaman) | true   | ANAN001 | VIL1     |
| Badaharijan Sahi          | true   | ANAN002 | VIL1     |

* Add all the slums in name field
* change the code according to ulb name
* add locality VIL1 according to boundary-data.
* convert the excel data into json using excel to json converter.
* create a folder of a respective tenant  and inside it add slum.json file in FSM folder.

5. Adding New Vehicles in VehicleMakeModel\
   Before pushing the vehicle data,new vehicle should be added in mdms.

| Vehicle Make                       | Eg.: Swaraj, Eicher, Mahindra etc. -> | Mahindra |
| ---------------------------------- | ------------------------------------- | -------- |
| Vehicle Model                      | Eg.: Truck, Tractor, Pick Up etc. ->  | Truck    |
| GPS Tracker is present in vehicle? | YES **or** NO ->                      | No       |
| Cesspool Tank Capacity (in Litres) | ->                                    | 1000     |

Eg.  new vehicle add&#x20;

```json
{
    "code": "MAHINDRA",
    "name": "Mahindra",
    "active": true
},
{
    "code": "MAHINDRA.TRUCK",
    "name": "Truck",
    "active": true,
    "make": "MAHINDRA",
    "capacity": "1000"
}
```

The code should be different for each vehicle and in format [make.name](http://make.name/) .

6. Billing-slab pricing preparation\
   For adding the rate slabs(pricing) of vehicles,consider different combination of propertyType , slum and tank capacity.
   1. Required combination of property types and Sub-property types added in [MDMS](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/FSM/PropertyType.json) :
   2. RESIDENTIAL and RESIDENTIAL.SUB-PROPERTY\_TYPE
   3. INSTITUTIONAL and INSTITUTIONAL.SUB-PROPERTY\_TYPE
   4. COMMERCIAL and COMMERCIAL.SUB-PROPERTY\_TYPE
   5. Sample Data for pricing :

| <p>Name of the ULB:<br>(Write in right side box)</p> | Anandapur Municipality |           |           |
| ---------------------------------------------------- | ---------------------- | --------- | --------- |
| Details                                              | Description            | Vehicle-1 | Vehicle-2 |
| Cesspool Tank Capacity (in Litres)                   | ->                     | 1000      | 3000      |
| Per trip Pricing for **Residential properties**      | ->                     | 1000      | 2000      |
| Per trip Pricing for **Commercial properties**       | ->                     | 1000      | 3000      |
| Per trip Pricing for **Institutional properties**    | ->                     | 1000      | 2000      |
| Per trip Pricing for **Slum areas**                  | ->                     | 800       | 1500      |

\
**Steps to make billing-slab data:**\
\
A. Create an excel file in given format

| tenantId     | capacityFrom | capacityTo | propertyType                   | slum | price | status |
| ------------ | ------------ | ---------- | ------------------------------ | ---- | ----- | ------ |
| od.anandapur | 0            | 1000       | RESIDENTIAL                    | YES  | 1000  | ACTIVE |
| od.anandapur | 0            | 1000       | RESIDENTIAL.INDEPENDENT\_HOUSE | NO   | 800   | ACTIVE |

B. Consider all property types and sub-property type present in mdms with slum YES and with slum NO.

C. for capacity 1000L,the pricing is given as

For slum NO :

1. RESIDENTIAL and RESIDENTIAL.SUB-PROPERTY\_TYPE - 1000
2. INSTITUTIONAL and INSTITUTIONAL.SUB-PROPERTY\_TYPE - 1000
3. COMMERCIAL and COMMERCIAL.SUB-PROPERTY\_TYPE - 1000

For slum YES(Per trip Pricing for **Slum areas**) :

1. RESIDENTIAL and RESIDENTIAL.SUB-PROPERTY\_TYPE - 800
2. INSTITUTIONAL and INSTITUTIONAL.SUB-PROPERTY\_TYPE - 800
3. COMMERCIAL and COMMERCIAL.SUB-PROPERTY\_TYPE - 800

D. for capacity 3000L,the pricing is given as

For slum NO :

1. RESIDENTIAL and RESIDENTIAL.SUB-PROPERTY\_TYPE - 2000
2. INSTITUTIONAL and INSTITUTIONAL.SUB-PROPERTY\_TYPE - 2000
3. COMMERCIAL and COMMERCIAL.SUB-PROPERTY\_TYPE - 3000

For slum YES(Per trip Pricing for **Slum areas**) :

1. RESIDENTIAL and RESIDENTIAL.SUB-PROPERTY\_TYPE - 1500
2. INSTITUTIONAL and INSTITUTIONAL.SUB-PROPERTY\_TYPE - 1500
3. COMMERCIAL and COMMERCIAL.SUB-PROPERTY\_TYPE - 1500

E. After creating the excel file by considering the combinations,convert the excel file into json.

F. Push the same json file in billing slab api using runner.
