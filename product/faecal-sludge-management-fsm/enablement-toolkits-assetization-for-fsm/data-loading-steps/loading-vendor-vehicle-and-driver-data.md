# Loading Vendor,Vehicle and Driver Data

Ways to load Vendor details :

* From Api
* By FSM Registry

**Loading from API :**

Steps:

1. Import this collection - [https://www.getpostman.com/collections/59691b6d0a7346a7f29b](https://www.getpostman.com/collections/59691b6d0a7346a7f29b)
2. Change the request url specific to environment.

For Create DSO(URL) : [https://sujog-dev.odisha.gov.in/vendor/v1/\_create](https://sujog-dev.odisha.gov.in/vendor/v1/\_create)

&#x20;For Search DSO(URL) : [https://sujog-dev.odisha.gov.in/vendor/v1/\_search?tenantId=od.anandapur](https://sujog-dev.odisha.gov.in/vendor/v1/\_search?tenantId=od.nimapara)

For Update DSO(URL) : [https://sujog-dev.odisha.gov.in/vendor/v1/](https://sujog-dev.odisha.gov.in/vendor/v1/\_create)[\_update?tenantId=od.anandapur](https://sujog-dev.odisha.gov.in/vendor/v1/\_search?tenantId=od.nimapara)

3. Login from FSM\_ADMINDEV credentials(for sujog-dev) which is having FSM Admin role for all the ulb’s.
4. Copy the auth token. Paste the auth token in the req. Body “authToken” field.
5.  &#x20;Request Info (eg. anandapur ulb) for Create DSO :-\
    \




    ```json
    {
        "RequestInfo": {
            "apiId": "Rainmaker",
            "authToken": "453cf29c-58de-4e47-9821-91f39e2dde3e",
            "userInfo": {
                "id": 3186071,
                "uuid": "2f3851cd-864e-42d7-869c-d5a05abb8f39",
                "userName": "FSM_ADMINDEV",
                "name": "Taresh",
                "mobileNumber": "7721827042",
                "emailId": null,
                "locale": null,
                "type": "EMPLOYEE",
                "roles": [
                    {
                        "name": "FSM Administrator",
                        "code": "FSM_ADMIN",
                        "tenantId": "od.anandapur"
                    }
                ],
                "active": true,
                "tenantId": "od.anandapur",
                "permanentCity": null
            },
            "msgId": "1660805524793|en_IN"
        },
        "vendor": {
            "tenantId": "od.anandapur",
            "name": "NIPS",
            "agencyType": "ULB",
            "paymentPreference": "post-service",
            "address": {
                "tenantId": "od.anandapur",
                "doorNo": "my door",
                "plotNo": "my plot",
                "landmark": "my landmark",
                "city": "anandapur",
                "district": "anandapur",
                "region": "anandapur",
                "state": "odisha",
                "country": "in",
                "pincode": "143001",
                "additionDetails": null,
                "buildingName": "my building",
                "street": "my streat",
                "locality": {
                    "id": 2,
                    "name": "Padampur",
                    "localname": "Padampur",
                    "longitude": null,
                    "latitude": null,
                    "label": "Locality",
                    "code": "VIL1",
                    "children": []
                },
                "geoLocation": {
                    "latitude": 0,
                    "longitude": 0,
                    "additionalDetails": {}
                }
            },
            "owner": {
                "tenantId": "od.anandapur",
                "name": "NIPS",
                "fatherOrHusbandName": "NA",
                "relationship": "FATHER",
                "gender": "MALE",
                "dob": 550261800000,
                "emailId": "test@dso.test",
                "correspondenceAddress": "KPHB",
                "mobileNumber": 8908257220
            },
            "vehicles": [
                {
                    "tenantId": "od.anandapur",
                    "registrationNumber": "OD09J7873",
                    "model": "MAHINDRA",
                    "type": "MAHINDRA.TRUCK1",
                    "tankCapacity": "1000",
                    "suctionType": "SEWER_SUCTION_MACHINE",
                    "pollutionCertiValidTill": 1611584416772,
                    "InsuranceCertValidTill": 1611584416772,
                    "fitnessValidTill": 1611584416772,
                    "roadTaxPaidTill": 1611584416772,
                    "gpsEnabled": true,
                    "source": "Municipal records",
                    "status": "ACTIVE",
                    "vendorVehicleStatus": "ACTIVE",
                    "owner": {
                        "tenantId": "od.anandapur",
                        "name": "NIPS",
                        "fatherOrHusbandName": "NA",
                        "relationship": "FATHER",
                        "gender": "MALE",
                        "dob": 550261800000,
                        "emailId": "test@dso.test",
                        "correspondenceAddress": "KPHB",
                        "mobileNumber": 8908257220
                    }
                }
            ],
            "drivers": [
                {
                    "tenantId": "od.anandapur",
                    "name": "DIPU MUKHI",
                    "licenseNumber": "OR0920040025878",
                    "status": "ACTIVE",
                    "owner": {
                        "tenantId": "od",
                        "name": "DIPU MUKHI",
                        "fatherOrHusbandName": "NA",
                        "relationship": "OTHER",
                        "gender": "MALE",
                        "dob": -19800000,
                        "emailId": "abc@egov.com",
                        "mobileNumber": "6371957727"
                    },
                    "vendorDriverStatus": "ACTIVE"
                }
            ],
            "source": "WhatsApp"
        }
    }
    ```

**Note:**

1. _Before pushing the vendor,first add Vehicle in MDMS. Take Vehicle Make, Model and Capacity from_ [_VehicleMakeModel_](https://github.com/egovernments/egov-mdms-data/blob/v2.3-patch/data/pg/Vehicle/VehicleMakeModel.json) _in MDMS._
2. _**No special characters** allowed in Vendor name._
3. _Vehicle Registration number should be **unique** for every vehicle._
4. _Scenerios for Vendor and Vehicle users:_\
   _- One Vendor can be linked with two or more vehicles._\
   _- One Vehicle is linked with One Vendor._\
   _- Two Vendors can’t have same mobile number because vendor is a user and user is stored uniquely in database._\
   _- Vendor owner, Vehicle owner and Driver owner can be same or different for One Vehicle._\
   \

5. Hit the url it’ll push the data of vendor.

**From FSM Registry :**

Add details of Cesspool Operator,Vehicle and Driver from FSM Registry and link Vehicle with Cesspool operator and Driver with Cesspool Operator.

&#x20;
