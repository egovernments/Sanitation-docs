# FSM Implementation Configuration

## MDMS Configuration

### FSTP Plant Info

The FSTP plant info contains plant operational capacity per day of each ULB and other plant-related information. It is required to calculate the FSTP capacity utilization in percentage form. MDMS file details:

[egov-mdms-data/FSTPPlantInfo.json at QA · egovernments/egov-mdms-data](https://github.com/egovernments/egov-mdms-data/blob/QA/data/pb/FSM/FSTPPlantInfo.json)\`\`

```
{
	"MdmsCriteria": {
		"tenantId": "pb",
		"moduleDetails": [{
			"moduleName": "dss-dashboard",
			"masterDetails": [{
				"name": "dashboard-config"
			}]
		}, {
			"moduleName": "FSM",
			"masterDetails": [{
				"name": "FSTPPlantInfo"
			}]
		}]
	}
}
```



[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)](http://creativecommons.org/licenses/by/4.0/)_All content on this page by_ [_eGov Foundation_](https://egov.org.in/) _is licensed under a_ [_Creative Commons Attribution 4.0 International License_](http://creativecommons.org/licenses/by/4.0/)_._
