# Release Notes

## Release Summary

This release includes a new feature called vehicle tracking, which has been developed as part of a community project. It aims to capture real-time spatial data by tracking vehicles from their starting coordinates (longitude and latitude) to their destination point. Additionally, it enables an urban local body (ULB) to designate illegal dumping spots, and monitor corresponding alerts

## Functional Changes

* &#x20; Vehicle Tracking&#x20;

## New Feature Additions

<table><thead><tr><th width="219">Feature</th><th>Description</th></tr></thead><tbody><tr><td><ol><li>Assigning drivers to the trips</li></ol></td><td><ul><li>The ULB personnel can assign the driver when assigning the vehicle for a particular trip.</li></ul></td></tr><tr><td><ol start="2"><li>Geo-location</li></ol></td><td><ul><li>Employee form has been enhanced to add geo-location.</li></ul></td></tr><tr><td><ol start="3"><li>Enhancement to application by introducing end trip</li></ol></td><td><ul><li>The vehicle tracking service can be leveraged to automate certain aspects of the disposal process.</li></ul><ol><li>System Verified : The trip is closed automatically if the vehicle is near the geo-fenced area  of the FSTP. In this case, the end type is updated as System Verified .</li><li>FSTP Verified: If the driver concludes the trip at a location that is not necessarily close to the FSTP, the FSTP staff will need to manually finalise the trip. In this case, the end type is updated as FSTP Verified.</li></ol></td></tr><tr><td>4. A standalone mobile application for the drivers </td><td><ul><li>Drivers will be able to see the trips assigned to them with start and end trips provided. With this functionality, the driver can start the trip when he/she reaches the citizen’s location, provide service, and end the trip when he/she reaches the FSTP.</li></ul></td></tr><tr><td>5. Defining Illegal Dumping Spots</td><td><ul><li>The vehicle tracking service can help the ULB personnel to identify and input these locations into the system . If a driver stops at one of these spots for an extended period , the system triggers an alert to notify the ULB of potential illegal dumping activity.</li></ul></td></tr><tr><td>6. Alerts</td><td><ul><li>On events where local authorities should be informed:</li></ul><ol><li>Longer waiting of vehicles near farm lands, water sources, etc., could be a possible indication of the illegal disposal.</li><li>The popular open disposal spots as generally defined as prohibited zones and any desludging vehicles around those areas are also an indication of open disposal.</li></ol></td></tr></tbody></table>

## **Known Issues**

1. A user cannot delete the added Illegal dumping site.
2. A user cannot edit the added illegal dumping site.
3. A driver cannot cancel/reject the trip.

## **Related Documents and Links**

Click [here](https://docs.google.com/spreadsheets/d/e/2PACX-1vQ3K61DK1EftkC1WLvpKQxhvh8kciz9AvznogPVmizNhu5w8qO0XF43JwEiaESGTuIOcj0dOFFs9Ujc/pubhtml) to view the details.\
