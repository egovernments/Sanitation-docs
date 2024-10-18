# Loading Billing Slab Data

For adding the rate slabs(pricing) of vehicles,consider different combination of propertyType , slum and tank capacity.

* Required combination of property types and Sub-property types added in [MDMS](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/FSM/PropertyType.json) :

1. RESIDENTIAL and RESIDENTIAL.SUB-PROPERTY\_TYPE
2. INSTITUTIONAL and INSTITUTIONAL.SUB-PROPERTY\_TYPE
3. COMMERCIAL and COMMERCIAL.SUB-PROPERTY\_TYPE

* Consider billing slab property types and Sub-property types for both slum and non-slum areas.Take slum='YES' for slum areas and take slum='NO' for non-slum areas.
* Sample Data for pricing :\
  \- The pricing is provided according to Vehicle capacity,property-types and slum areas.

| <p>Name of the ULB:<br>(Write in right side box)</p> | Anandapur Municipality |           |           |           |
| ---------------------------------------------------- | ---------------------- | --------- | --------- | --------- |
| Details                                              | Description            | Vehicle-1 | Vehicle-2 | Vehicle-3 |
| Cesspool Tank Capacity (in Litres)                   | ->                     | 1000      | 3000      | 1000      |
| Per trip Pricing for **Residential properties**      | ->                     | 1000      | 2000      | 1000      |
| Per trip Pricing for **Commercial properties**       | ->                     | 1000      | 2000      | 1000      |
| Per trip Pricing for **Institutional properties**    | ->                     | 1000      | 2000      | 1000      |
| Per trip Pricing for **Slum areas**                  | ->                     | 800       | 1500      | 800       |

Within the tenant,For two Vehicles having the same capacity,the pricing should be same.\
Example : In Vehicle-1 and Vehicle-3,for capacity 1000,pricing for\
Residential properties with Slum='NO' = 1000\
Commercial properties with Slum='NO' = 1000\
Institutional properties with Slum='NO' = 1000\
Residential properties with Slum='YES' = 800\
Commercial properties with Slum='YES' = 800\
Institutional properties with Slum='YES' = 800

* Loading Rate Slabs Steps:

1. Import this collection - [https://www.getpostman.com/collections/d039948bfdf20f7286ad](https://www.getpostman.com/collections/d039948bfdf20f7286ad)
2. Change the request url specific to environment.

&#x20;For search billing-slab(url) - [https://sujog-dev.odisha.gov.in/fsm-calculator/v1/billingSlab/\_search? tenantId=od.rourkela\&limit=-1](http://localhost:8094/fsm-calculator/v1/billingSlab/\_search?tenantId=pg.rourkela\&limit=-1)

&#x20;  For create billing-slab(url) - [https://sujog-dev.odisha.gov.in/fsm-calculator/v1/billingSlab/\_create](http://localhost:8094/fsm-calculator/v1/billingSlab/\_create)

&#x20; For update billing-slab(url) - [https://sujog-dev.odisha.gov.in/fsm-calculator/v1/billingSlab/\_update](http://localhost:8094/fsm-calculator/v1/billingSlab/\_create)

3. Login from FSM\_ADMINDEV credentials(for sujog-dev) which is having FSM Admin role for all the ulb’s.
4. Copy the auth token. Paste the auth token in the req. Body “authToken” field.
5. Download these files -  [https://drive.google.com/drive/folders/1cmEcpnvOHiGeq0pKpuznzWKoIYXL4VEI?usp=sharing](https://drive.google.com/drive/folders/1cmEcpnvOHiGeq0pKpuznzWKoIYXL4VEI?usp=sharing)\
   and update the file by changing the different combination of propertyType , slum and tank capacity with respect to tenant/ulb.
6. Open the runner tab (ctrl+shift+R) and import the file which is shared in the step 5. (For  example: billing-athagarh.json for pushing athagarh billing slab).
7. Drag the api which is provided in Step 1 collection.
8. Hit the postman collection.

&#x20;

IMPORTANT POINTS:

1.The format of billing slab data is:

```json
{
    "tenantId": "{{tenantId}}",
    "capacityFrom": "{{capacityFrom}}",
    "capacityTo": "{{capacityTo}}",
    "propertyType": "{{propertyType}}",
    "slum": "{{slum}}",
    "price": "{{price}}",
    "status": "{{status}}"
}
```

Eg.

```json
{
    "tenantId": "pg.rourkela",
    "capacityFrom": 0,
    "capacityTo": 1000,
    "propertyType": "RESIDENTIAL",
    "slum": "YES",
    "price": 800,
    "status": "ACTIVE"
}
```

2.The capacity always starts from 0.

3.Example. If the given capacity is 1000 and 3000 then the range should be:

"capacityFrom": 0,

&#x20;"capacityTo": 1000,

"capacityFrom": 1001,

&#x20;"capacityTo": 3000,

4.Consider billing-slab for both slum and non-slum areas.

5.The status is always ACTIVE.

6.If the price of all the slums is given as 0,then mark zeroPricingStatus as true otherwise mark it as false in [MDMS](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/anandapur/FSM/ZeroPricing.json).

&#x20;

How to update billing slab data:

1. The format of updating billing slab data is:

```json
{
    "id": "{{id}}",
    "tenantId": "{{tenantId}}",
    "capacityFrom": "{{capacityFrom}}",
    "capacityTo": "{{capacityTo}}",
    "propertyType": "{{propertyType}}",
    "slum": "{{slum}}",
    "price": "{{price}}",
    "status": "{{status}}",
    "auditDetails": {
        "createdBy": "0ea42eb0-4406-4acf-91b0-52eca31403ab",
        "lastModifiedBy": "0ea42eb0-4406-4acf-91b0-52eca31403ab",
        "createdTime": 1685258218048,
        "lastModifiedTime": 1685258218048
    }
}
```

2.If the need is to update the price for all the slums from 800 to 500,for this Take the response from search api for slum “YES”,make a json file with updated price and push it using runner with the syntax mentioned in point 1.

Eg. [https://drive.google.com/file/d/11GqEB3mtDO2A9g5P6ilbBOUSuN0kPGgx/view?usp=sharing](https://drive.google.com/file/d/11GqEB3mtDO2A9g5P6ilbBOUSuN0kPGgx/view?usp=sharing) &#x20;

**Zero Pricing property in billing-slab :**

| <p>Name of the ULB<br>(Write in right side box)</p> | Anandapur Municipality |                                                                |
| --------------------------------------------------- | ---------------------- | -------------------------------------------------------------- |
| E. Zero Pricing Properties of ULB                   |                        |                                                                |
| Sl No.                                              | Property Type          | **Property Sub Type**                                          |
| 1                                                   | Institutional          | CT,PT, Temple, Govt. High School, Govt. Hospital, Govt. School |

For some combination of property types and sub-property types,the zero pricing property is given.For that,the price will be considered as 0(zero) for all the capacities and slum areas.

&#x20;
