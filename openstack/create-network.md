# Create a network

Before you can launch instances in OpenStack, you should first create a network. In OpenStack, networks can provide layer 2 and 3 connectivity to instances. Conceptually, the OpenStack networks you will create work very similarly to physical networks. The steps below apply to most general use cases.

1. Log in to the dashboard.
2. Be sure you have selected the **appropriate** project from the drop down menu at the top left.
3. On the Project tab, open the Network tab and click Networks category.
4. Click Create Network.
5. In the Create Network dialog box, specify the following values.
   * Network Name: Specify a name to identify the network. For assignments, best to name your network as "ssoid-LABNUMBER" (replace ssoid with your ssoid and LABNUMBER with a number)
   * Shared: Un-check, i.e. not shared (if enabled, you will share the network with other projects. Non admin users are not allowed to set shared option.)
   * Admin State: Enabled (the state to start the network in.)
   * Create Subnet: Select this check box to create a subnet (You should create a subnet. Technically, you do not have to specify a subnet when you create a network, but if you do not specify a subnet, the network can not be attached to an instance.).
6. In the Subnet tab:
   * Subnet Name: Specify a name (format: ssoid-LABNUMBER-subnet) for the subnet.
   * Network Address: Specify the network address for the subnet. This identifies the entire network. Typically these are given using RFC 1918 private address classes (unless you've been specifically instructed to use a public block.). For lab assignments, you may simply use something like ``10.1.2.0/24``
   * IP Version: Select IPv4 or IPv6. In most cases, this will be IPv4 only.
   * Gateway IP: Specify an IP address for a specific gateway based on your network address. Typically, this is the first usable address in your network. For example, given the network address above, it will be ``10.1.2.1``. If nothing is specified, the first address from the network you specified earlier is used by default.
   * Disable Gateway: -ed (select this check box to disable a gateway IP address but do it only if you don't need a gateway).
7. In the Subnet Details tab:
   * Enable DHCP: Select this check box to enable DHCP.
   * Allocation Pools: Specify IP address pools. These are addresses that will be assigned to instances by the DHCP service. For lab assignments, you may choose about 50 addresses. For example, based on the network address used above, please simply enter ``10.1.2.10,10.1.2.59``. Note the comma separating the beginning and ending addresses in the DHCP scope.
   * DNS Name Servers: Specify a name or IP address for the DNS servers. Put each entry on a new line. For lab assignments, your instructor will tell you what DNS server to use.
   * Host Routes: Specify the IP address of host routes. In most cases this is left blank unless your instructor specifies further instructions.
8. Click Create.

The dashboard shows the network on the Networks tab.

You can also now see two different types of graphical representations of the newly created network using the "Network Topology" tab. The regular topology view and a Graph view. You can also modify the display using the buttons/options displayed on the screen.
