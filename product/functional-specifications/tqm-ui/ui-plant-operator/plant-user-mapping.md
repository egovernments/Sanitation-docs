# Plant-User Mapping

Every plant operator created will be linked to one or more plants under an urban local body (ULB).

## Plant-User Mapping Flow

* When a plant operator logs in to the system, the top bar is populated with a dropdown which shows a list of plants this user (plant operator) is linked to.
* By default, the option "All Plants" is selected.
* When a user selects a plant, lets say, plant A, all the data of plant A will be shown in the app, whether it's inbox, view past results page, home page, etc.
* Whenever a change in a plant is detected through the dropdown, the app is redirected to the landing screen.
* A plant operator is a sanitation worker; while creating a sanitation worker, you can link the sanitation worker to one or multiple plants.
* Data such as a list of the current user's plants and active plant is stored in session storage, and is available to use within the app.

## How a Plant's Dropdown is Populated

* Whenever a plant operator logs in, he/she can make a call to this API endpoint "/pqm-service/plant/user/v1/\_search" to get a list of the plants that the user is linked to .
* Sample payload:

```json
{
    "RequestInfo": {
        "apiId": "asset-services",
        "ver": null,
        "ts": null,
        "action": null,
        "did": null,
        "key": null,
        "msgId": "search with from and to values",
        "authToken": "{{access_token}}",
        "correlationId": null,
        "userInfo": {
            "id": "1",
            "userName": null,
            "name": null,
            "type": null,
            "mobileNumber": null,
            "emailId": null,
            "roles": null,
            "uuid": "d7867ef2-d046-4361-9a82-94c35c98416e"
        }
    },
    "plantUserSearchCriteria": {
        "ids": [],
        "tenantId": "pg",
        "plantCodes": [
        ],
        "individualIds": ["d7867ef2-d046-4361-9a82-94c35c98416e"],
        "additionalDetails": {}
    },
    "pagination": {}
}
```

* Send the user's individual id/uuid in the request object.
* Curl for the above API call:

```json
curl --location 'http://localhost:7008/pqm-service/plant/user/v1/_search' \
--header 'Content-Type: application/json' \
--data '{
    "RequestInfo": {
        "apiId": "asset-services",
        "ver": null,
        "ts": null,
        "action": null,
        "did": null,
        "key": null,
        "msgId": "search with from and to values",
        "authToken": "",
        "correlationId": null,
        "userInfo": {
            "id": "1",
            "userName": null,
            "name": null,
            "type": null,
            "mobileNumber": null,
            "emailId": null,
            "roles": null,
            "uuid": "d7867ef2-d046-4361-9a82-94c35c98416e"
        }
    },
    "plantUserSearchCriteria": {
        "ids": [],
        "tenantId": "pg",
        "plantCodes": [
        ],
        "individualIds": ["d7867ef2-d046-4361-9a82-94c35c98416e"],
        "additionalDetails": {}
    },
    "pagination": {}
}'
```

* You will get a list of plants in the response which is used to populate the dropdown.&#x20;
* By default, the "All Plants" option is selected which is the default behaviour.
* When a user selects a particular plant, it becomes active and one can filter the data (all tests shown in the app) by that plant's code in the UI.
* UI for the top bar:

<figure><img src="../../../../.gitbook/assets/image (160).png" alt="" width="312"><figcaption></figcaption></figure>
