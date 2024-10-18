---
description: Workbench Setup
---

# User Manual

## Workbench Employee User Manual

### Prerequisites

For the loading of data, the following will be required:

1. State-level user for workbench (to allow for loading of state data).
2. Urban local body (ULB)-level users for workbench (to allow for loading of ULB-specific data). One user for the workbench with access to all ULBs can also be created and the user can navigate across the ULB to upload data for each ULB

### Checklist

| <p>All the below configurations are in order, and the same order should be followed while creating a new test standard:</p><ol><li>BenchmarkRule</li><li>QualityTestLab </li><li>Material </li><li>Parameter </li><li>PlantConfig</li><li>PlantType</li><li>ProcessType </li><li>Unit </li><li>WasteType</li><li>SourceType</li><li>Stage</li><li>Process </li><li>Plant </li><li>QualityCriteria </li><li>TestStandard<br></li></ol><p>Duplications are not allowed.<br></p><p>Common user actions for the below configuration:</p><ul><li>Users can view a list of configurations.</li><li>Users can add a new configuration.</li><li>Users can edit a configuration.</li><li>Users can enable or disable a configuration.</li></ul> |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

### Definitions

<table data-header-hidden><thead><tr><th></th><th width="193"></th><th></th></tr></thead><tbody><tr><td>Configuration</td><td>Which level this has to be defined?</td><td>Definition</td></tr><tr><td>Benchmark rule</td><td>State </td><td>The rules according to which a test value should be tested. (For example, Greater than, less than, equal to).</td></tr><tr><td>Quality Test Lab</td><td>ULB</td><td><p>Quality Test Lab is the laboratory where the testing is happening.</p><p>This can be configured accordingly if it is in-house or the ULB-Geo Corporation.</p></td></tr><tr><td>Material</td><td>State</td><td>Material is a physical substance for which the quality monitoring is done. For example: Effluent or raw water.</td></tr><tr><td>Parameter</td><td>State</td><td>Criteria used to measure te input and the output for a job. Each parameter will have a unit of measurement.</td></tr><tr><td>Plant configuration</td><td>State</td><td>Configuration details for a particular plant.</td></tr><tr><td>Plant type</td><td>State</td><td>The classification of plant based on their processing.</td></tr><tr><td>Process type</td><td>State</td><td>Defines the type of process.</td></tr><tr><td>Unit</td><td>State</td><td>The unit for measuring this particular parameter</td></tr><tr><td>Waste type</td><td>State</td><td>The classification of waste materials based on their characteristics or origin.</td></tr><tr><td>Source type</td><td>State</td><td>The origin of this particular test standard.</td></tr><tr><td>Stage</td><td>State</td><td>Each step within the treatment process. Each job may have one or many input quality parameters, and one or many output quality parameters.</td></tr><tr><td>Process</td><td>State</td><td>Sequential series of steps required to translate input to output.</td></tr><tr><td>Plant</td><td>State</td><td>Respective Plant for which Test Standards are created</td></tr><tr><td>Quality criteria</td><td>State</td><td>The quality criteria which is applicable for the unique combination of plant, process, stage and material.</td></tr><tr><td>Test standard</td><td>ULB</td><td>A combination of a parameter, acceptable benchmark of the parameter and its frequency of testing. For example, ph >= 7 tested weekly.</td></tr></tbody></table>

### Login

ULB employees are provided with credentials to log in to the system. Role-based access for various steps in the workflow, that is, different individuals can be assigned to create an application, modify applications, or manage vendor, driver, and vehicle details.

![](https://lh7-us.googleusercontent.com/04wJtSbBlgwepA5kah8XinZ8H7oog7EkSPucwL6R8EStqpiYizlJMoVwGjebHNxT-vmQBJI356cv-NVFGSiPTs\_GIplZjWeiK9GQryM\_iSa87dDAV-HAdClZzSG8FSo59o-WR7A3FpHON8AJ1UogkrQ)

**User actions**

On this page, the following actions can be performed:

* Enter username and password.
* Select a city for login.
* Reset your password by clicking on the “Forgot Password” link.

On clicking continue, employees are redirected to the Workbench home page

### ​Create Benchmark Rule

For the proper working of the platform, the following benchmark rules should be configured. If  any other benchmark rules are configured, the system will not function:\


<figure><img src="https://lh7-us.googleusercontent.com/IP0A96Ptgw47EjGPtCwWlwxjc5XVLbdp19tVMnbTGKoIClpqQr8HrozZekQm4VCOlVXeJm7MqsTQ9561AuiSe-b85s5SRUfxguvnzuDv4V6MIDsIjeiyKoP_QXz_-ASSyJ4cJ_VENHBRZHu5wcUg5RM" alt=""><figcaption></figcaption></figure>

Inbox

<figure><img src="https://lh7-us.googleusercontent.com/T5djzQCaueC-1zKlR0hd0yol2stVI-sTx3-1gW-Lz49FvosAad1qEtvqrtU4z64vRxa6ceJ1CrVo4Z7sG8TbRJ6SjbCLFgM7xA0K-kebiGcwmcX3naVyuudKAR_9huzvepDB49Jm45JPjt2y-HFwg-4" alt=""><figcaption></figcaption></figure>

Click on “Add Master Data” to add a new benchmark rule

| Code    | Name                   |
| ------- | ---------------------- |
| LSTOREQ | Less Than Or Equals    |
| GTROREQ | Greater Than Or Equals |
| NEQ     | Not Equals             |
| EQ      | Equals                 |
| OSD     | Outside Range          |
| BTW     | Between                |
| LST     | Less Than              |
| GTR     | Greater Than           |

<figure><img src="https://lh7-us.googleusercontent.com/_b25M9CbJ8WAKD5dZNssRpmiO9TFvV9JmJi_lpLpk8wX25VlK4bpeqJwLX0v8Rc5K3_SwYNVm1P_eGfN00ld814wOXr0EsnIfWr5FntdimxdwvXSwsplmliM8Us3s8xLMolkWR9UGTsON3nwg58Fuf0" alt=""><figcaption></figcaption></figure>

### Create Quality Test Lab

<figure><img src="https://lh7-us.googleusercontent.com/Yil7Z1ZaDPjvQcfxGHzJoTL99XWKzNz5YBMYefrQhUNVzCoeXyNE9YT3PI_QP1EurC0f44ZOFmR5A-Utffo_qeIJ0QqrxF80QE2XVSb2ztaWp7zc8uJx0kXbacxcmdAJ9WLomSXilHPPMLHcX2KSth8" alt=""><figcaption></figcaption></figure>

Inbox

<figure><img src="https://lh7-us.googleusercontent.com/9bQf93jK6hvDaoXHKeuPNsy18g0f9a8raG8apxUPi6r5Vs2_Pdc1wVIl-TLutnsj8t_gvB7Eq8CZH7IHSNfh75gTCQRmRzzxRKHB7Jyt8H-XKyQH-Zg3wbvJQdbkjvDEVtf-vBViaNlN-MR9mxaKeeE" alt=""><figcaption></figcaption></figure>

Click on “Add Master Data” to create new a Quality Test Lab

| Field | Description                                                                     | Example                                            |
| ----- | ------------------------------------------------------------------------------- | -------------------------------------------------- |
| Code  | Alphanumeric or numeric representation assigned to uniquely identify the field. | <p>JATNI_In_House<br>Puri_Third_Party</p>          |
| Name  | Textual or human-readable identity given to a record.                           | <p>Jatni in-house lab,<br>Puri third-party lab</p> |

<figure><img src="https://lh7-us.googleusercontent.com/By4MMZMxa-Z3-vvbJuAlejG_81Eutxhyed9znwgIQaN6v7d_09HFVWBovFEBFu9Qh4qke9qdsumkgTV7IG3XXuWnXI2s_MB18bu_6KccKcMpwK3VDWdtIxf_axiUMOtRz2Io-ueD8-_cH29C1ZvhyMI" alt=""><figcaption></figcaption></figure>

### Create Material 

<figure><img src="https://lh7-us.googleusercontent.com/dNyMg0FGNnhFmdmcoUoS5WZMrHpEgHPLo0sHdVn7bgF8u3J7-XX7N43pXLtpL5zdXLRFuX2nPjIKXScqj8IUhim3NfGVdRsA1UH4oQw7lgHTDViKFFR-bz8HN9QohvY7jCNovryEYx3aYVYOWdfxHIg" alt=""><figcaption></figcaption></figure>

Inbox

<figure><img src="https://lh7-us.googleusercontent.com/wrPIUjqi33M3lhOy4q3bBpZf_X7aCPh1xa96ceND-Vo_I3nfI0oIPTIip8StZji6pbVBVOU-GtngCidrurQBm3vwJupIUdSP-Z4eHUEDFKXW365s9-3Ok1_vJXUxjWN75STofhW-xIFscMGTeaswnjk" alt=""><figcaption></figcaption></figure>

Click on “Add Master Data” to create new a material\


| Field | Description                                                                     | Example                             |
| ----- | ------------------------------------------------------------------------------- | ----------------------------------- |
| Code  | Alphanumeric or numeric representation assigned to uniquely identify the field. | <p>MM_01<br>MM_02</p>               |
| Name  | Textual or human-readable identity given to a record.                           | <p>Effluent<br>Treated effluent</p> |

<figure><img src="https://lh7-us.googleusercontent.com/LvCO1bA7Bvm21qbr3hDS-NguvbaXtWq_o9-6DONyzpU_LAA0_LHPJj_fWhaxZvV0TFkokydMmuCkG7xXFCcVoeJtmMc1fH-s5UkRmA2P2BuQTZ5JcuF3vyg2mqWUwJ4f4IFBHEtg13UgVWf_u_wdygY" alt=""><figcaption></figcaption></figure>

### Create Parameter

<figure><img src="https://lh7-us.googleusercontent.com/v4-XOrpn7el8JvZd6J3y7Uqqf7S7tvMFsqMs2vNF2YyqyeV5MSUxCv5bqXcbpSoXUEoUSmaEPevu8JVSaoT2eJsUpbhZd4ygsEgNh4RZvZ2nbErgZySv9gmFtCG7wN0Dx4IWkXshjE16xanS_6SBEdw" alt=""><figcaption></figcaption></figure>

Inbox

<figure><img src="https://lh7-us.googleusercontent.com/N4r1I3snye9lvP1jiRR6288eWWmJK0P-mF-GUCPX-HAePZt-0PuFubb-1FcCk6lQMzhkpgR47LozDtOeYHsDrUw7ULqBRkQSy8Yl9ccV_VxRowwu1VcMIV6O6zzMIw-81FXqxoGdus2SxNRkhVzmNnA" alt=""><figcaption></figcaption></figure>

Click on “Add Master Data” to create a new parameter

| Field       | Description                                                                     | Example                                                    |
| ----------- | ------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| Code        | Alphanumeric or numeric representation assigned to uniquely identify the field. | <p>PP_01<br>PP_02</p>                                      |
| Name        | Textual or human-readable identity given to a record.                           | <p>COD<br>BOD</p>                                          |
| Description | Details or explanation for a record.                                            | <p>Chemical oxygen demand,<br>Biological oxygen demand</p> |

<figure><img src="https://lh7-us.googleusercontent.com/BXc1kLy7Hc6zGA5MViMMmVwLLxZIh5BkipE4OJ2X6gbGgjUlhyTwtpDQN049nDww_VN_6m6_IyZwonlVFzXXZySGH4rFkVub7hvweSXEyv1uyjFCvxHJx-05ZHnsONUzGv2sLQrYpWxg1FD1jCiqmRI" alt=""><figcaption></figcaption></figure>

### Create Plant Configuration

<figure><img src="https://lh7-us.googleusercontent.com/C5TTksPCXyBSuxp6f2uCuzxxMPxJdiZ1k3LXthHqQvPBAyZWC6q9_ieoEp3uLzbumw_zlN7AD4q6lWg0uySUyXu71CxZYBk0dSeN9mzycfFWwmtwJ3Oc2hYmxswgxMAktzXPRYKsW-NE_qV3i9Mk81w" alt=""><figcaption></figcaption></figure>

Inbox

<figure><img src="https://lh7-us.googleusercontent.com/jXbD4CyYwQQb0H64DTRqYiGRO1Wgixa9PiF1U3oFl2JHjg6vGjQ_jmu-9Q9OP0Pg4WELOEjiIYfx5Cdg4e8O9jgnHx7O8gokpzbVFFWsmiDBAfVLifMwsjL38cBGL3XNISetRnZFFsCxIjfzJ6Es2Fo" alt=""><figcaption></figcaption></figure>

Click on “Add Master Data” to create a plant configuration

| Field                                | Description                                                                                                   | Example                                                              |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| Code                                 | Alphanumeric or numeric representation assigned to uniquely identify the field.                               | DEFAULT\_CONFIGURATION                                               |
| Lab test escalation days             | The number of days after which a scheduled test that is still pending requires escalation.                    | Decided by the state and the programme team to configure these days. |
| Pending tests to display within days | The number of days within which pending tests, assessments, or evaluations should be displayed or considered. | Decided by the state and the programme team to configure these days. |



<figure><img src="https://lh7-us.googleusercontent.com/Ih6N9BZlvlqBIVIDwfOO5iQ6DpJLqPpmhiptVSLzecNuBLLH_GWDL9dt2JHklz12Zt-_bG6z6zind-SWdF2x3KTxviGcSkbJEs659BoKqTnkaG33z1pD3XO_ZiDSZR2MwgV639TKmHr6EYat_TD_Tx4" alt=""><figcaption></figcaption></figure>

### Create Plant Type 

<figure><img src="https://lh7-us.googleusercontent.com/DWMngTl47aXpz0UtIm9x2WKJpCvtJamQYo4jAbnWkjsr4kttb97NKMd3cVm502IYlNg19-Sqm7qM1mwBPAuVvL9KqfBcTsQ3PDkMkJ4IYm0_trw1cB7PgNsUa1_NKkQRIm4_7vAOZzGai4AKLVtv4o8" alt=""><figcaption></figcaption></figure>

Inbox

<figure><img src="https://lh7-us.googleusercontent.com/TGJhUj0qY6Wvx0qm89pnJNx9hdZBbvBnjx7ZwijXWNPcIv4uT2fll6s1keQuByO0XbHZJoZp0ZiQqhtv4nmJ8SgohOwHQ9_cBpi86IBNxEFuxTLUZSMfp7jvcu9WJp7Cz-1xtOEtUoEGVZNUbNDjxno" alt=""><figcaption></figcaption></figure>

Click on “Add Master Date” to create a plant type

| Field       | Description                                                                     | Example                                                    |
| ----------- | ------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| Code        | Alphanumeric or numeric representation assigned to uniquely identify the field. | <p>FECAL_SLUDGE_TREATMENT_PLANT<br>CO_TREATMENT_PLANT</p>  |
| Name        | Textual or human-readable identity given to a record                            | <p>Faecal sludge treatment plant<br>Co-treatment plant</p> |
| Description | Details or explanation for a record.                                            | Any description related to the plant.                      |

<figure><img src="https://lh7-us.googleusercontent.com/xuL0lDL0kSCzvxbERyJ5QDsLvCDva487N7VUG950wCCQgt_bguyEnSOWi-_3hVQQeeWsayY2n-Pzr3dGHx5wJjpKggi8FqSAHtYwuuThs8A8QpB-oIpq6GCJwAFFpmJ626JmF-1iHUuem43_PDclumM" alt=""><figcaption></figcaption></figure>

### ​Create Process Type

<figure><img src="https://lh7-us.googleusercontent.com/BX5GkVERBg8FqkDC_sdEPZqwaMuCaBbZSp7ef4OlEGAKu_vSgMSsQNWvX0e6hbbbRJmPx_ztXxI7gaYLxUDYyDBEUVbAieYj-XjIxboRT7uooaXWSjtENYkIbT961VRLOOoJHFKexv8NEzfW-iwKa7w" alt=""><figcaption></figcaption></figure>

Inbox

<figure><img src="https://lh7-us.googleusercontent.com/tagkAJ0bzqIB7voeneQjK4IJPBgi_ucJTf9khUgcMT7uVAkPbuOOUuAu7FUfoKLQAHxwc7Or4ursJMbOSXjlFfOzLItKc6gOrkLIHpoIlvBO5rCO3nXXOfLKFEDuJBF_invowf4rhf1cemK2pu0T48w" alt=""><figcaption></figcaption></figure>

Click on “Add Master Data” to create a new process type\


| Field | Description                                                                     | Example                                                    |
| ----- | ------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| Code  | Alphanumeric or numeric representation assigned to uniquely identify the field. | <p>FECAL_SLUDGE_TREATMENT<br>5_STAGE_WATER_TREATMENT</p>   |
| Name  | Textual or human-readable identity given to a record                            | <p>Faecal sludge treatment,<br>5-stage water treatment</p> |

<figure><img src="https://lh7-us.googleusercontent.com/1SAd1KbN0ben4G2SYr9TlPiv0fo2P2jB4Zr31t0ZjdNgyRMe38_PW0l4UWOF9XpBkoEP4P0RdiqvT3PEvdS4G3WcHpXOqyQ7dv68AIRPdSnaro2ftp9Mpsz08IA9d8-yEZH5esU0MvnzoVeacVCb7p8" alt=""><figcaption></figcaption></figure>

### ​Create Unit

<figure><img src="https://lh7-us.googleusercontent.com/shCElchzi5Ph4poMIMrvqGr1PwoiNuoK_1gPMSD-KPZAoFKwWrcCaJFzFc8GpeF7fNsIFwLpm0blosH30BIsOhNlBn7jfA_ZohY8xYli_4XQ4BifYF-XElFnkX0Hc2Z4SFAzVyNeVCBLjt9cwKAJp38" alt=""><figcaption></figcaption></figure>

Inbox

<figure><img src="https://lh7-us.googleusercontent.com/_ZHXAN1tqonFL_HmwqdkfB5hgu6yJa3z94iqd4Nnql88Mk8UqTHMud4Up3tuB_8Zni5x2dmYpVIT9ndebh6DmeB1mImqtv7cymh2fjlVyjqJ2_LpSwk6z5pk8OHGwK9WYmmcDpw8JAbxC42WLTsExuE" alt=""><figcaption></figcaption></figure>

Click on “Add Master Data” to create a new unit

| Field | Description                                                                     | Example                               |
| ----- | ------------------------------------------------------------------------------- | ------------------------------------- |
| Code  | Alphanumeric or numeric representation assigned to uniquely identify the field. | <p>MGPL<br>DC</p>                     |
| Name  | Textual or human-readable identity given to a record.                           | <p>Mg per liter<br>Degree celsius</p> |

<figure><img src="https://lh7-us.googleusercontent.com/lsH4AcTwSYSj4IPD3oM-vD4faCdawtiP70bWP_pXiwsgarqhzdvS2iGvVBE-cbWZbnwHYAxlEhDHilE4ocCERmF_OkMhLDZXYrwADvYonm7-oXcO4_F3LUh4jskVSrF7rdSgnCON2KGrV-SAvJdUles" alt=""><figcaption></figcaption></figure>

### ​Create Waste Type

<figure><img src="https://lh7-us.googleusercontent.com/lMrbDno9DFEDiVe4wRJ8QjCmeeiz1LCw1wO4RsnOrpQJHj7zaO3GnrWtLgOqqgZmRvbyz3CQ4FLLNwXA0kObZ6CCulFzfK9w6JtPph15fvIN1J6IVqdyXcRVm2AUvdddEnVCktiJ7kY1ybe4BZf2riI" alt=""><figcaption></figcaption></figure>

Inbox

<figure><img src="https://lh7-us.googleusercontent.com/iFzGwVrTNicIFYr2NeIk607OXwLVlkFEXeYXJdY0PV46jIlxQSHhllmJePJtgD2bKDMnhO7MLFw7_F-RU2tKsAy4qHy_8xs1kyW7pjY4XScP8eOf7SzeSONhQguQnHSxerFcvw8Xku4xikcbby4E58o" alt=""><figcaption></figcaption></figure>

Click on “Add Master Data” to create new Waste Type

| Field | Description                                                                     | Example                                          |
| ----- | ------------------------------------------------------------------------------- | ------------------------------------------------ |
| Code  | Alphanumeric or numeric representation assigned to uniquely identify the field. | <p>FECAL_SLUDGE<br>MEDICAL_INFECTIOUS_WASTE</p>  |
| Name  | Textual or human-readable identity given to a record.                           | <p>Faecal sludge<br>Medical infectious waste</p> |

<figure><img src="https://lh7-us.googleusercontent.com/DVZtmiSzRi2gCkUeq8KhrOdnlkLBqEyTuaWfzNzFzQGeqDkmIDFN9IyJK8YkVmXXAHZBdJbu5XTa1VXgy388OMn9G4b9yTCkULumY1fd4SlQ-cvQeWQLEjRk0RD8_CWL7zGvfdW0rVBscXwsagLjEig" alt=""><figcaption></figcaption></figure>

### ​Create Source Type

<figure><img src="https://lh7-us.googleusercontent.com/k-o521m7ftEoKUzBPDukx_SPMjGQBWnoi0kWgkKdJZ3IOqsMVoM-Szf_DMPwHDzvno27tygSRl0PTwT48IYtDL64UCriWrHXzfRSpzVYc6iPHekfyTIY-wrfAk5JmzMERQWXlEcr1ANnN_73aUOfjEU" alt=""><figcaption></figcaption></figure>

Inbox

<figure><img src="https://lh7-us.googleusercontent.com/LDJpC7XLwj66s_YNndszCwZb-fJhJUJHKwyw2F8k2W8EJYeb72ZLbHsus82ey8rIIitJSH-Cx0N9dkjNkrtofAul4rMsjmQXIeb2wh_Tj2saj0SpxHB38SkJkvCTqQ43jCDjGmGI-doRSOGmq9eDa0Y" alt=""><figcaption></figcaption></figure>

Click on “Add Master Data” to create a new source type

| Field       | Description                                                                     | Example                               |
| ----------- | ------------------------------------------------------------------------------- | ------------------------------------- |
| Code        | Alphanumeric or numeric representation assigned to uniquely identify the field. | <p>LAB_ADHOC<br>LAB_SCHEDULED</p>     |
| Name        | Textual or human-readable identity given to a record.                           | <p>Adhoc tests<br>Scheduled tests</p> |
| Description | Details or explanation for a record.                                            | Any explanation regarding the tests   |

\


<figure><img src="https://lh7-us.googleusercontent.com/FoSoLb-8ep5eSrSpB_LQVJXCPWQ7G7-AeNsBdkjbrOa0KVpAQdMLZhOaeA0TX1xgEADbL_XVCnjEGv3yCRW5XwdGabVpd_OCCHN-RoNR3mQZfzA4Inw9_nOfatWqhVa5iVLDMgiZFpxhX-kS5WtftAw" alt=""><figcaption></figcaption></figure>

### ​Create Stage

<figure><img src="https://lh7-us.googleusercontent.com/fLjkywHte4a7YmjSp7YUXso3BKp0rcy8ugbb9COYIp-WB3lyeDS_ovdTVdld1-DtZ8ff4tv46iL8kTYowI7QLSlA3idsxXYyqHNB1FVy4LLr9VEcgM-au4dRojqtiAiPbQaBHICF6TraVcrpCBXdD4s" alt=""><figcaption></figcaption></figure>

Inbox

<figure><img src="https://lh7-us.googleusercontent.com/h99k2VPdhm86w0jR1xF5ewyEa40txsJqvquQbFpa0uGyRIYA5F-iQLDLEK3IAHtFq4FflgBqKQF3LEizI19JumDgyXWQFK4MUQ69zSvWMzABXq1XIJtkH69mrBbYOOI79uoev4Ut49efiJG0BBNb4u8" alt=""><figcaption></figcaption></figure>

Click on “Add Master Data” to add a new stage\


| Field           | Description                                                                     | Example                                                                                                                                                     |
| --------------- | ------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Code            | Alphanumeric or numeric representation assigned to uniquely identify the field. | OUTLET\_OF\_POLISHING\_POND                                                                                                                                 |
| Name            | Textual or human-readable identity given to a record.                           | Outlet of Polishing Pond                                                                                                                                    |
| Input material  | Materials provided as an input to a dtage                                       | <p>Effluent<br>faecal sludge<br><br>Decided by the state and the programme team to configure the input and output material based on the data collected.</p> |
| Output material | Materials provided as an output to a stage                                      | <p>Treated effluent<br><br>Decided by the state and the programme team to configure the input and output material based on the data collected.<br><br></p>  |
| Description     | Details or explanation for a record.                                            | Description of the stage.                                                                                                                                   |

<figure><img src="https://lh7-us.googleusercontent.com/uXolYWWQ7cel0kH4_dxL64dR0kSPT0NKs9SsUp37ZtDwQOzEfelMX5sqlGgK1-CJMZrNevHXRqqtmr7bU5-r4NtJIqBnwvwFa-OgmLF-VLY_mAlBXk63p3w0FYmYYp5ATZemF4Hs69d9BotTkXrLUgM" alt=""><figcaption></figcaption></figure>

### ​Create Process

<figure><img src="https://lh7-us.googleusercontent.com/gv2tjDL_rp8ZUToJPO5XV_pDY1VhTbeoZoHySzGc8c5lCsDqTAKav-CKCGUk_21nk7eWD0fr_J4IqHo-_zTPHw_9h4O9cXpacnG-EA05pDtdSi7ZchC61oSqooNZG2zBLP07trPb-zlfpd1uqrUW4AE" alt=""><figcaption></figcaption></figure>

Inbox

<figure><img src="https://lh7-us.googleusercontent.com/mYXNc-Rgrp2S47Vme9kZ_c98CbiQ1tfF2ztjYkqAOv9JwXlQAbGvwZG9gc1a2_puhKc9qpUA0V37chDQqDL837CRt_74ogNH9p9LE0byexC2G6sZtnT2pwj-2V5xawtwnQX1OFN-FX3dJUaGLhTsg-4" alt=""><figcaption></figcaption></figure>

Click on “Add Master Data” to create a new process\


| Field        | Description                                                                                                                            | Example                                           |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------- |
| Code         | Alphanumeric or numeric representation assigned to uniquely identify the field.                                                        | FECAL\_SLUDGE\_TREATMENT\_PROCESS                 |
| Name         | Textual or human-readable identity given to a record.                                                                                  | Faecal sludge treatment process                   |
| Process Type | Defines the type of process. Here the previously defined process type has to be entered.                                               | Faecal sludge treatment                           |
| Order        | Order can be a number for which the stage can be defined. This is a non-mandatory field.                                               | 1                                                 |
| Stage Code   | A list of stages that come under a particular process. Here the previously defined stage has to entered.                               | Outlet of polishing pond                          |
| Waste Type   | The classification of waste materials based on their characteristics or origin. Here the previously defined waste type has to entered. | Faecal Sludge                                     |
| Description  | Details or explanation for a record.                                                                                                   | Description regarding the process can be entered. |

<figure><img src="https://lh7-us.googleusercontent.com/tjBCSpDDJc_v8dgf3Sqbb6HIMxm30GZKR1277nDT3EWjdkMyli8qQZJEyvXIdNwNYy8u8OC_A-TYKuJLoSugAJqqUVQxuLEx6nGRZDnpJe12-YUq7F1eq9dxWf5uUgcvLj3p2oEO9cttLORIrncxohA" alt=""><figcaption></figcaption></figure>

### ​Create Plant

Once the plant is created, the plant user mapping has to be done through the backend.\
\
If there is already an FSM instance created and running, then the V1 of codes for plant and ULB has to be taken for V2 and the backend team will have to create the plants using the same codes.

<figure><img src="https://lh7-us.googleusercontent.com/NvBvPLV2ugHSoBxtNJlpb8IEFBBYcjeHYAY9oQm2vKnu-Jrn-RqgTHE94Fi7EUAypdzH4CQfXAWshDivNN63GocjUqqzL5T0SBapIHOXK-M7J-FI5AT4iRm-Ja1kaioqomErOKtCwf-ZtG5b7wfF1As" alt=""><figcaption></figcaption></figure>

Inbox

<figure><img src="https://lh7-us.googleusercontent.com/o-tVdCL9J09FCxzj4qetNJtLcpaWdJfxkA8L9eo4T5SmZadFwFA7n1PBg10ZRyu9bq96LLHG-HVMDu_5cLX5uQ-Ppxak3Ds1UZoOtJXu3FdhZbcbsdbp-afLgZfNdiPDwTnBgcWmii6s71pDzVlxcBs" alt=""><figcaption></figcaption></figure>

Click on “Add Master Data” to add a new plant\


| Field                          | Description                                                                                                                                                   | Example                                           |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------- |
| ULBs                           | The respective ULBs the plant belongs to.                                                                                                                     | <p>od.berhampur<br>od.dhenkanal</p>               |
| Code                           | The plant code this is the same code from V1.                                                                                                                 | <p>BEHR_001<br>DHKL_001</p>                       |
| Name                           | Textual or human-readable identity given to a record.                                                                                                         | <p>BeMC Plant<br>Dhenkanal Plant</p>              |
| PlusCode                       | This is the geo-location of the plant.                                                                                                                        | 7PJQ+Q8 Kusumi, Odisha                            |
| Latitude                       | Latitude of the plant.                                                                                                                                        | <p><br></p>                                       |
| Longitude                      | Longitude of the plant.                                                                                                                                       | <p><br></p>                                       |
| Plant Type                     | <p>The classification of plant based on their processing.<br>Note: Here the previously defined plant type has to entered</p>                                  | Faecal sludge treatment plant                     |
| Process                        | <p>A list of process that happen under a particular plant.<br>Note: Here the previously defined process has to entered.</p>                                   | <p>Faecal sludge treatment process</p><p><br></p> |
| Waste type                     | <p>The classification of waste materials based on their characteristics or origin.<br>Note: Here the previously defined waste type has to entered.</p>        | <p>Faecal sludge<br>Medical infectious waste</p>  |
| Description                    | Details or explanation for a record.                                                                                                                          | Can be the description of a plant.                |
| Plant Configuration            | <p>Configuration details for a particular plant.<br>Note:  Here the previously defined plant configuration has to entered. This is also a mandatory field</p> | DEFAULT\_CONFIGURATION                            |
| Plant Location                 | Location of the plant.                                                                                                                                        | <p><br></p>                                       |
| Plant Operational timings      | Timings of the plant.                                                                                                                                         | <p><br></p>                                       |
| Plant Operational Capacity KLD | Total capacity of the plant.                                                                                                                                  | <p><br></p>                                       |

<figure><img src="https://lh7-us.googleusercontent.com/kdfysclExEAh1oso7k3Jg3Arwxr746QAOnO40I0_byMDK_1TJuJQ3EUhyFxb9PxqseJnmoZk5wmaguegtR2fkBGy37Av980eLwuYwXwbpvh8uCrlrtTaU5N9QE0_N4U1nIVTjAXExpGgjTUA7pANl5o" alt=""><figcaption></figcaption></figure>

<figure><img src="https://lh7-us.googleusercontent.com/D12bXSjbBv4KX5OWrxVHXDTahKGvSfnSWWBVNQYm_0WLCuwD_33ik1zEgf6k9oNp3q7O7Lk8LVgOgrOvozQqi8eYzrkzK1PY6Mepl8k1v_nKDlBzpF8aqMyRuCgrZoCTZs6Fo8DddQh_kBZ4xH2mN1I" alt=""><figcaption></figcaption></figure>

### ​Create Quality Criteria

<figure><img src="https://lh7-us.googleusercontent.com/1_XB4Vs_Pi4xxFcEhxJYcLhCgd2hPDTtIdWq5NR7Yh-UFRcZ-X9lBHIgfNdASj7W99CrXmkawRKK9qLkI6dBIP4sAEJYwMvwR82HEn8uJInIbUSrh7XMCqfilFtKi2nK0K__VMxUyZJBLEYYKb02Jn4" alt=""><figcaption></figcaption></figure>

Inbox

<figure><img src="https://lh7-us.googleusercontent.com/SMMgMXn3wdnpl6irQtEzdKdXDSNCHX7BvzItIOFYo8YQP1DEkD5sqPxHgYYpu5bPbS7kb5bT1ZOErcbGviLHOwXC4r2CmkK3QjqLfwFIcH-QZ20OtBZYKO2H0c9a2zwHnjoC9xW_EelUGVWEliHbZM0" alt=""><figcaption></figcaption></figure>

Click on “Add Master Data” to add a new quality criteria\


| Field               | Description                                                                                                                                                                                                                      | Example                                           |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------- |
| Code                | Alphanumeric or numeric representation assigned to uniquely identify the field.                                                                                                                                                  | COD\_MGPL                                         |
| Unit Of Measurement | <p>The unit for measuring this particular parameter<br>Note: Here the previously defined units will be shown in the dropdown and the respectives can be selected.</p>                                                            | MGPL                                              |
| Paramaeter          | <p>Anything that is measurable as an input/output for a particular stage.<br>Note: Whatever the quality criteria is entered, the previously defined parameter is shown in the drop-down and the respectives can be selected.</p> | COD                                               |
| Benchmark rule      | The rules according to which a test value should be tested. (For example, Greater than, less than, equals to).                                                                                                                   | This is entered as per the master data collected. |
| Benchmark values    | Specific numbers on which the benchmark rule is applied for a test value.                                                                                                                                                        | This is entered as per the master data collected. |
| Allowed deviation   | The acceptable difference from the benchmark values.                                                                                                                                                                             | This is entered as per the master data collected. |

<figure><img src="https://lh7-us.googleusercontent.com/bCcQh0JuFMYvA1bzoyFFgaZLAxFXseH_J19UJgaj706rmIi8bSvJZxiiBNg4x2x_V7L9c0CfQoD5g3kakG2HtExitVKvQqFnlVeaAxKVylw0OOJ4xaR7p5qD6WVYG1bsSCiC6HexMITGjbXQ0BKPutQ" alt=""><figcaption></figcaption></figure>

### ​Create Test Standard

<figure><img src="https://lh7-us.googleusercontent.com/4IeLTqeCPErVdS-DNxeDA3pDAJ31Dh1iMEKbhnlgLVn_3zw-jy7_AEmAcesXVRyUtBYCcO12VGgaGgly5BqNN_Ne_CT42liRaIrxFP4uCmJN0bIjY110XrYne3jVKDlOeBKXT--pkntTLmB0AyoJaXU" alt=""><figcaption></figcaption></figure>

Inbox

<figure><img src="https://lh7-us.googleusercontent.com/_BnWShCJra7qbphGED5dAKyN3Avk_WjL8G5nAMhTIjofp2lo735skme7nACfd9gQZ-e1Nb86cGr5LabgkdpBZ3W417PM8ilVJ_kFRxlkhecmZwREe4XlylwnjFTFClLECK9h02Hhhp_eQ8pGooaL4uQ" alt=""><figcaption></figcaption></figure>

Click on “Add Master Data” to add a new test standard

| Field            | Description                                                                                                                             | Example                                                                                                                              |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Code             | Alphanumeric or numeric representation assigned to uniquely identify the field.                                                         | TEST\_PURI\_QM1                                                                                                                      |
| Plant code       | <p>Plant Code for which this Test Standard is registered.<br>NOTE: The plant codes must match the above added plant codes for Plant</p> | <p>BEHR_001</p><p> DHKL_001</p><p><br></p>                                                                                           |
| Stage code       | Stage Code for which this Test Standard is registered.                                                                                  | Outlet of polishing pond                                                                                                             |
| Process code     | <p>Process Code for which this Test Standard is registered.<br><br></p>                                                                 | Fecal Sludge Management                                                                                                              |
| Material code    | Material Code for which this Test Standard is registered                                                                                | Effluent                                                                                                                             |
| Frequency        | The frequency at which this test standard should be scheduled.                                                                          | Decided by the state and the programme team to configure the input and output material based on the data collected. For example: 14. |
| Source type      | The origin of this particular test standard.                                                                                            | Lab                                                                                                                                  |
| Quality criteria | The quality criteria which is applicable for the unique combination of plant, process, stage and material.                              | <p>COD<br>BOD<br>TSS</p>                                                                                                             |

<figure><img src="https://lh7-us.googleusercontent.com/9q47l94yLPDFRRk8IVt01vEQNHMV7ZHbOgY094Inc0LePyWbozsP2QA13_qswROOwqapo0XjIkG_26zJa9cTaFsHBed-sSgZnWhE9bEqaD6PBdyNC9TOH88by6CJP7UXZGx-EJ3wkWbCVgf2Zc-XKNs" alt=""><figcaption></figcaption></figure>

<figure><img src="https://lh7-us.googleusercontent.com/5Cdfhbyavk-YkMG88xzb8-J6TiBtqEtdws-6gh_dpzaPce2DOyUqHeNbVgrwvovSdWWtwz5_Vs9Zu28iVtLOR8gEB5FAg6IlN6Z3VtZLMszu_AdC2XGk4C6pYZTKi7ejDVkiv9RpYFjYyjnANY_JYZ8" alt=""><figcaption></figcaption></figure>
