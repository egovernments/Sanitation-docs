# Data loading steps

To add new ulb/tenant for FSM,following steps should be followed:

* Add data in MDMS

| **Reference from Annexure**                                            | **Data**                            | **Location**                                                                                                                                                  | **Description**                                                                                         |
| ---------------------------------------------------------------------- | ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| <p>Annexure -1<br>Sl. No. A1 - A4</p>                                  | Tenant Details                      | [tenant/tenants.json](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/tenant/tenants.json)                                             | To show the tenant at login screen                                                                      |
|                                                                        |                                     | [tenant/citymodule.json](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/tenant/citymodule.json)                                       | To enable ulb to create application,add tenant in FSM module                                            |
| <p>Annexure -1<br>Sl. No. B1 - B6</p>                                  | FSTP Data                           | [FSM/FSTPPlantInfo.json](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/FSM/FSTPPlantInfo.json)                                       | To add FSTP information                                                                                 |
| <p>Annexure-2<br>Vehicle Make,Vehicle Model,Cesspool Tank Capacity</p> | New Vehicles                        | [Vehicle/VehicleMakeModel.json](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/Vehicle/VehicleMakeModel.json)                         | Add Vehicles in application.Before pushing the vehicle data,new vehicle should be added in mdms.        |
| Annexure -3                                                            | Slum Details                        | [ULBNAME/FSM/Slum.json](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/anandapur/FSM/Slum.json)                                       | To add slum data,create a folder of a respective tenant  and inside it add slum.json file in FSM folder |
|                                                                        | URC Feature                         | [ULBNAME/FSM/UrcConfig.json](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/anandapur/FSM/UrcConfig.json)                             | To enable URC(GramPanchayat) feature for ulb                                                            |
| Annexure -4                                                            | Zero pricing feature                | [ULBNAME/FSM/ZeroPricing.json](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/anandapur/FSM/ZeroPricing.json)                         | To enable zero pricing feature                                                                          |
| Annexure -5                                                            | Locality and Gram Panchayat Details | [ULBNAME/egov-location/boundary-data.json](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/anandapur/egov-location/boundary-data.json) | Under specific ulb folder,add locality and gp details under egov-location folder.                       |

* After this,restart the mdms service and check the status in ui.The tenant will be added in ui.
* Create Employee and FSTP login credientials.
* Plant Mapping of tenant
* Push the localisation of all the slums and Gram Panchayat in tenant.
* Push the billing-slab of new tenant
* Push the vendor-vehicle data of new tenant
