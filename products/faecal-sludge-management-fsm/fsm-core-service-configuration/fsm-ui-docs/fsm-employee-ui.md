# FSM Employee UI

There are three main updates in FSM v1.2.1 for employee UI:

1. Application timeline
2. Photo viewed by employee/DSO
3. Payment mode while completing request

### 1. Application Timeline: <a href="#1.-application-timeline" id="1.-application-timeline"></a>

An employee can see the application status in application timeline with provider details.

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 3.49.52 PM.png>)

#### Technical Implementation Details: <a href="#technical-implementation-details" id="technical-implementation-details"></a>

The path for the code:

**frontend/micro-ui/web/micro-ui-internals/packages/modules/fsm/src/pages/employee/ApplicationDetails/index.js**

The code snippet to render application timeline:

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 3.51.55 PM.png>)

The code snippet for extracting the provider info for each status:

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 3.53.34 PM.png>)

### 2. Photo viewed by employee/DSO <a href="#2.-photo-viewed-by-employee-dso" id="2.-photo-viewed-by-employee-dso"></a>

An employee/DSO can view the photo uploaded by the employee/DSO in complete request action.

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 3.56.07 PM.png>)

#### Technical Implementation Details: <a href="#technical-implementation-details-.1" id="technical-implementation-details-.1"></a>

The path for the code:

**frontend/micro-ui/web/micro-ui-internals/packages/modules/fsm/src/pages/employee/ApplicationDetails/index.js**

The code snippets to render the field:

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 3.59.25 PM.png>)

ViewImages.js are the common component used to fetch and render the Image file id. The path is shown below:

**frontend/micro-ui/web/micro-ui-internals/packages/modules/fsm/src/components/ViewImages.js**

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 4.01.43 PM.png>)

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 4.01.53 PM.png>)

### 3. Payment mode while completing request <a href="#3.-payment-mode-while-completing-request" id="3.-payment-mode-while-completing-request"></a>

An employee has to select the payment mode while completing the request.

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 4.05.19 PM.png>)

#### Technical Implementation Details: <a href="#technical-implementation-details-.2" id="technical-implementation-details-.2"></a>

File path:

**frontend/micro-ui/web/micro-ui-internals/packages/modules/fsm/src/pages/employee/ApplicationDetails/config/CompleteApplication.js**

The code snippet to render the field.

![](<../../../../.gitbook/assets/Screenshot 2022-08-08 at 4.07.57 PM.png>)

MDMS file fetch for payment mode:

[egov-mdms-data/ReceivedPaymentType.json at UAT · egovernments/egov-mdms-data](https://github.com/egovernments/egov-mdms-data/blob/UAT/data/pg/FSM/ReceivedPaymentType.json)

```
{
    "tenantId": "pg",
    "moduleName": "FSM",
    "ReceivedPaymentType": [
        {
            "name": "Payed in Cash",
            "code": "PAYED_IN_CASH",
            "active": true
        },
        {
            "name": "Payed in Counter",
            "code": "PAYED_IN_COUNTER",
            "active": true
        },
        {
            "name": "Netbanking",
            "code": "NETBANKING",
            "active": true
        }
    ]
}
```



\
