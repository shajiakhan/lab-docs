# Create a router

1. Log in to the dashboard.
2. Select the appropriate project from the drop down menu at the top left.
3. On the Project tab, open the Network tab and click Routers category. ** Alternatively, click on Network Topology category from the Network tab (you can also perform all the router related tasks right from the Network Topology display).
4. Click Create Router.
5. In the Create Router dialog box, specify a name for the router.
   * Enable Admin State: Leave checked.
   * External Network: Select the "outside" network this router will be connected to. This is analogous to the WAN side of a typical stub router. For lab assignments, your instructor will specify the name of the external network if needed. If you are making internal networks without outside connectivity, or wish to interconnect multiple private networks together, then you may simply leave the External Network selection blank.
   * Click Create Router.
   * The new router is now displayed in the Routers tab.

## Adding interfaces to router

To connect a private network to the newly created router, perform the following steps:

1. On the Routers tab, click the name of the router.
2. On the Router Details page, click the Interfaces tab, then click Add Interface.
3. In the Add Interface dialog box, select a Subnet.
4. Optionally, in the Add Interface dialog box, set an IP Address for the router interface for the selected subnet. If you choose not to set the IP Address value, then by default OpenStack Networking uses the first host IP address in the subnet. In other words, this is the "gateway ip" for the private network. For example, if your subnet is 10.1.2.0/24 then this IP will be 10.1.2.1.
5. The Router Name and Router ID fields are automatically updated.
6. Click Add Interface.

You have successfully created the router. You can view the new topology from the Network Topology tab.
