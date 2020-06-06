# Add a Static Route

>Note: you should be familiar with static routing before you attempt to add a static route to a router. Understanding the concept will make this task trivially easy.

1. Log in to the dashboard.
2. Select the appropriate project from the drop down menu at the top left.
3. On the Project tab, open the Network tab and click Routers category.
4. Click on the router name you wish to add a static route to.
5. Click on the "Static Routes" tab
6. Click on "Add Static Route" to open the static route dialog box
   * Enter the destination CIDR (e.g., `192.168.3.0/24`). This is the remote network that we are trying to let the current router (the one we're adding a static route to) know about.
   * Enter the Next Hop IP address (e.g., `192.168.2.251`). This is the IP address of the next router's interface that will help the current router "get to the remote network and is the next destination where the current router must forward the Layer 3 datagram to.
   * Click Submit.
   * Verify connectivity (typically by pinging from a directly connected network of current router to an IP address in the remote destination network you entered for your route.)
