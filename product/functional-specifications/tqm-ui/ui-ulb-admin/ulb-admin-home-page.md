# ULB Admin Home Page

Logging in with ULB admin role takes the user to the home page of DIGIT-UI.

## Home Page

* If a ULB admin user is logged in, he/she will have access to TQM, and a TQM card will be visible on this screen.
* Links such as Inbox, View Past Tests, and create test are available on this card.
* A notification card is available on the bottom, which is specific to TQM. All the TQM-related notifications configured will show up here. Currently, it shows notifications for tests whose results are not updated on time (crossed scheduled date).

<figure><img src="../../../../.gitbook/assets/image (166).png" alt=""><figcaption><p>ULB Admin Home Page</p></figcaption></figure>

## API Details for TQM

* Use the egov-user-event service.&#x20;
* Sample request object:

```
{
    "RequestInfo": {
        "apiId": "Rainmaker",
        "authToken": "a0c56299-3bde-48e2-b0fb-76686fdff3dc",
        "userInfo": {
            "id": 722,
            "uuid": "56e8c2df-af55-46a9-a378-885915cde0ab",
            "userName": "TQM_DEV_ULBADMIN",
            "name": "ULB Admin",
            "mobileNumber": "7281638698",
            "emailId": null,
            "locale": null,
            "type": "EMPLOYEE",
            "roles": [
                {
                    "name": "PQM Admin",
                    "code": "PQM_ADMIN",
                    "tenantId": "pg.citya"
                }
            ],
            "active": true,
            "tenantId": "pg.citya",
            "permanentCity": null
        },
        "msgId": "1701078884762|en_IN",
        "plainAccessRequest": {}
    }
}
```

* The API returns a list of notifications relevant to the logged in user.
* Sample curl for notifications:

```
curl 'https://unified-dev.digit.org/egov-user-event/v1/events/_search?tenantId=pg.citya' \
  -H 'authority: unified-dev.digit.org' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9' \
  -H 'content-type: application/json;charset=UTF-8' \
  -H 'cookie: _ga_V2CPZCVTXQ=GS1.1.1695293925.1.1.1695293950.0.0.0; __cuid=59fd9aac25b044f6af006bd4b159cbbf; amp_fef1e8=f4fc07f6-3fb0-4c67-8114-a1beb906e625R...1hf75985a.1hf76uet8.i.8.q; _ga_P1TZCPKF6S=GS1.1.1699974064.1.1.1699975479.60.0.0; _ga=GA1.2.1291438273.1695293925; _ga_0JZG96DZSM=GS1.1.1699977339.2.0.1699977339.60.0.0' \
  -H 'origin: https://unified-dev.digit.org' \
  -H 'referer: https://unified-dev.digit.org/sanitation-ui/employee' \
  -H 'sec-ch-ua: "Google Chrome";v="119", "Chromium";v="119", "Not?A_Brand";v="24"' \
  -H 'sec-ch-ua-mobile: ?1' \
  -H 'sec-ch-ua-platform: "Android"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: same-origin' \
  -H 'user-agent: Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.0.0 Mobile Safari/537.36' \
  --data-raw '{"RequestInfo":{"apiId":"Rainmaker","authToken":"a0c56299-3bde-48e2-b0fb-76686fdff3dc","userInfo":{"id":722,"uuid":"56e8c2df-af55-46a9-a378-885915cde0ab","userName":"TQM_DEV_ULBADMIN","name":"ULB Admin","mobileNumber":"7281638698","emailId":null,"locale":null,"type":"EMPLOYEE","roles":[{"name":"PQM Admin","code":"PQM_ADMIN","tenantId":"pg.citya"}],"active":true,"tenantId":"pg.citya","permanentCity":null},"msgId":"1701078884762|en_IN","plainAccessRequest":{}}}' \
  --compressed
```

* The role-action mapping for /egov-user-event/v1/events/\_search is added for this user that is, the ULB admin whose role code is PQM\_ADMIN.
