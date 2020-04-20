# Internetworking basics - routing begins at hosts - Connecting two networks with one router

## Lab Purpose

This lab will help you get started with understanding internetworking (i.e. connecting two or more networks together and moving Layer 3 datagrams between networks). It will also help you understand that routing begins at hosts as each host must decide what to do with an outgoing Layer 3 datagram.

### Learning Outcomes

1. Basic understanding of virtual networkign in cloud environments such as OpenStack
2. Create and deploy IP networks.
3. Create and configure routers to interconnect networks.
4. Describe routing process as initiating at the host
5. Describe routing process at a router

### Prerequisites

#### Environment

1. You should have already received instructions on logging into the lab environment from your instructor
2. Any computer with Internet access should work. Latest versions of Chrome and Firefox browsers are preferable.

#### Background Knowledge

1. Familiarity with virtualization concepts and basic working knowledge of Linux command line will be beneficial but not required.
2. Understanding of Network Addresses, Dynamic versus Static IP configuration of hosts, and theory on decision making at hosts and routers as they decide how to forward Layer 3 datagrams.

## Lab Task 1: Create first network

You'll create a private network on which you'll launch your instances. You can create a network from the dashboard. While creating a network, you'll also create a Subnetwork. For the subnetwork, you can pick any RFC 1918 private Internet Protocol Version 4 (IPv4) block you wish. An example setup using private IP addresses and network addresses for IPv4 appears below. You may choose your own network addresses if you wish.

Use the following values/inputs [while following the instructions here](../../tasks/openstack/create-network.md).

1. Network Name: `network-1` (replace with your ssoid or username)
2. Other inputs/check boxes: Not Shared; Admin State enabled; and create a subnet.
3. Subnet:
   * Subnet Name: `network-1-subnet`
   * Network Address: `192.168.1.0/24`
   * Gateway IP: `192.168.1.1`
   * Subnet Details:
      1. DHCP enabled
      2. DHCP Allocation Pools: `192.168.1.10,192.168.1.59`
      3. DNS SERVER: (not needed, leave blank; as these are test networks with no outside connectivity)
      4. Rest of the configuration either blank or default

## Lab Task 2: Create second network

You'll create a private network on which you'll launch your instances. You can create a network from the dashboard. While creating a network, you'll also create a Subnetwork. For the subnetwork, you can pick any RFC 1918 private Internet Protocol Version 4 (IPv4) block you wish. An example setup using private IP addresses and network addresses for IPv4 appears below. You may choose your own network addresses if you wish.

Use the following values/inputs [while following the instructions here](../../tasks/openstack/create-network.md).

1. Network Name: `network-2` (replace with your ssoid or username)
2. Other inputs/check boxes: Not Shared; Admin State enabled; and create a subnet.
3. Subnet:
   * Subnet Name: `network-2-subnet`
   * Network Address: `192.168.2.0/24`
   * Gateway IP: `192.168.2.1`
   * Subnet Details:
      1. DHCP enabled
      2. DHCP Allocation Pools: `192.168.2.10,192.168.2.59`
      3. DNS SERVER: (not needed, leave blank; as these are test networks with no outside connectivity)
      4. Rest of the configuration either blank or default

## Create a router that connects network-1 with network-2

Use the following values/inputs [while following the instructions here](../../tasks/openstack/create-router.md).

1. Router name: `router-1` (replace with your ssoid or username)
2. External Network: LEAVE BLANK
3. Add an interface to this router on your `network-1-subnet`:
   * IP Address: `192.168.1.1` (this will be the gateway for all instances launched in your network-1-subnet)
4. Add a second interface to this router on your `network-2-subnet`:
   * IP Address: `192.168.2.1` (this will be the gateway for all instances launched in your network-2-subnet)

## Create a SSH Key Pair and download to save in your .ssh directory

Use the following values/inputs [while following the instructions here](../../tasks/openstack/create-key-pair.md).

1. Key Pair Name: `ssoid-key` (replace with your ssoid or username)

## Launch an Linux instance; "machine-A" on network-1

With all the steps above, you're now ready to launch an Linux instance. Use the following values/inputs [while following the instructions here](../../tasks/openstack/launch-ubuntu-instance.md).

1. Instance name: `machine-A`
2. Source Image: `Ubuntu-16-04` (no volumes)
3. Flavor: `m1.nano`
4. Network: `network-1` (you created this network earlier;)
5. Security Group: `Default` (no need to create one, this is already present. Every OpenStack project comes with a Default security group that blocks all incoming traffic to the instances in that group and allows all outgoing traffic.)
6. Key Pair: `ssoid-key` (you created this earlier with your ssoid or username)
7. IMPORTANT - Configuration: Use a cloud-init script to set a password for your Ubuntu instance.

## Launch an Linux instance; "machine-B" on network-1

With all the steps above, you're now ready to launch an Linux instance. Use the following values/inputs [while following the instructions here](../../tasks/openstack/launch-ubuntu-instance.md).

1. Instance name: `machine-B`
2. Source Image: `Ubuntu-16-04` (no volumes)
3. Flavor: `m1.nano`
4. Network: `network-1` (you created this network earlier;)
5. Security Group: `Default` (no need to create one, this is already present. Every OpenStack project comes with a Default security group that blocks all incoming traffic to the instances in that group and allows all outgoing traffic.)
6. Key Pair: `ssoid-key` (you created this earlier with your ssoid or username)
7. IMPORTANT - Configuration: Use a cloud-init script to set a password for your Ubuntu instance.

## Launch an Linux instance; "machine-C" on network-2

With all the steps above, you're now ready to launch an Linux instance. Use the following values/inputs [while following the instructions here](../../tasks/openstack/launch-ubuntu-instance.md).

1. Instance name: `machine-A`
2. Source Image: `Ubuntu-16-04` (no volumes)
3. Flavor: `m1.nano`
4. Network: `network-1` (you created this network earlier;)
5. Security Group: `Default` (no need to create one, this is already present. Every OpenStack project comes with a Default security group that blocks all incoming traffic to the instances in that group and allows all outgoing traffic.)
6. Key Pair: `ssoid-key` (you created this earlier with your ssoid or username)
7. IMPORTANT - Configuration: Use a cloud-init script to set a password for your Ubuntu instance.

## Access your instances through the browser using HTML 5 console (noVNC)

The launch [instance instructions](../../tasks/openstack/launch-ubuntu-instance.md#accessing-your-ubuntu-instance-through-the-browser-console) provides details on how to access your instances through the browser itself. Once at the console, you click in the console and then start typing. You can login with the username `ubuntu` and the password you set in the configuration script during launch!

## Test connectivity

Connect to machine-A from the console and check it's IP address.
Connect to machine-B in another browser window and check it's IP address.
From machine-A ping the IP address of machine-B. Go to machine-B and ping the IP address of machine-A.

### Test connectivity across networks

Connect to machine-C in another browser window and check it's IP address.
Ping from machine-A to machine-C and vice-versa
Ping from machine-B to machine-C and vice-versa

### Think of how the packets move

Examine how hosts within the same network (here machine-A and machine-B communicate) at Layer 3. Similarly, examine how hosts send the Layer 3 datagrams to the default gateway for moving packets across networks. Complete the assigned readings.

## Cleaning up after you're done

1. Shutdown and delete the instance
2. Delete each of the interfaces on your router
3. Delete the router itself
4. Delete the network you created (you may have to ensure you delete all ports on this network first if you get an error message when trying to delete the network)
