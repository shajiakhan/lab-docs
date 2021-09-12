# Cloud Computing Basics - Launch a Linux Instance in OpenStack Cloud

## Lab Purpose

This lab will help you get familiar with the OpenStack based lab environment.

### Learning Outcomes

1. Basic understanding of an Infrastructure as a Service (IaaS) cloud management platform such as OpenStack
2. Familiarity with the “Horizon” self-service dashboard interface accessible through the browser
3. Ability to launch a simple test virtual machine instance
   * Creating key-pair
   * Selecting “flavors”
   * Use a cloud-init injection script to allow the user to login to the instance from the browser console
   * Creating a network on which the instance will be launched
   * Accessing the Virtual Machine through the browser using HTML 5 consoles

### Prerequisites

#### Environment

1. You should have already received instructions on logging into the lab environment from your instructor
2. Any computer with Internet access should work. Latest versions of Chrome and Firefox browsers are preferable.

#### Background Knowledge

1. Familiarity with virtualization concepts and basic working knowledge of Linux command line will be beneficial but not required.

## Lab Task 1: Login and explore the Horizon dashboard

1. In your web browser address bar, enter the URL for the OpenStack Horizon Dashboard.  This will be provided by your instructor.
2. Enter your User Name and Password provided by the instructor/sysadmin and click on login.
3. You should now see the OpenStack Horizon Dashboard.
4. Familiarize with the OpenStack Horizon Dashboard
   * On the left-hand side will be several drop-down menus.
   * Spend a few minutes navigating through the menus to become familiar with where to find various functions you may want to perform

## Lab Task 2: Launch an instance

Launching an instance requires certain prerequisite steps. In OpenStack you launch an instance attached to either a particular network or a port or a combination of both. Similarly, you must create a Key Pair and use that when you launch an instance. Sometimes you may have to create a router and connect your private network to another network. Details coming up in links below.

### Lab Task 2-1: Create a private network

You'll create your own private network on which you'll launch your instance. You can create a network from the dashboard. While creating a network, you'll also create a Subnetwork. For the subnetwork, you can pick any RFC 1918 private Internet Protocol Version 4 (IPv4) block you wish. For this lab, please choose the following if you are not familiar with private IP addresses and/or network addresses for IPv4.

>Use the below values/inputs [while following the instructions on how to create a network in OpenStack Dashboard here](../../tasks/openstack/create-network.md).

1. Network Name: `ssoid-test` (replace with your ssoid or username)
2. Other inputs/check boxes: Not Shared; Admin State enabled; and create a subnet.
3. Subnet:
   * Subnet Name: `ssoid-test-subnet`
   * Network Address: `192.168.1.0/24`
   * Gateway IP: `192.168.1.1`
   * Subnet Details:
      1. DHCP enabled
      2. DHCP Allocation Pools: `192.168.1.10,192.168.1.59`
      3. DNS SERVER: Enter your DNS server IP addresses one on each line ( `Your instructor will provide you with these`)
      4. Rest of the configuration either blank or default

### Lab Task 2-2: Create a router that connects your network with an "external" network for Internet access

>Use the below values/inputs [while following the instructions on how to create a router in OpenStack Dashboard here](../../tasks/openstack/create-router.md).

1. Router name: `ssoid-router` (replace with your ssoid or username)
2. External Network: Choose the external network (`Your instructor will provide you with the name of the external network`. Simply, choosing this network as your "external" network means your router will have an interface on this network much like your home router connects to your Internet Service Provider's network).
3. Add a second interface to this router on your ``ssoid-test-subnet``:
   * IP Address: `192.168.1.1` (this will be the gateway for all instances launched in your ssoid-test-subnet)

### Lab Task 2-3: Create a SSH Key Pair and download to save in your .ssh directory

If you don't already have a Key Pair setup, create a SSH Key Pair and download to save in your .ssh directory. Use the below values/inputs [while following the instructions on how to create a key pair in OpenStack Dashboard here](../../tasks/openstack/create-key-pair.md).

1. Key Pair Name: `ssoid-key` (replace with your ssoid or username)

### Lab Task 2-4: Launch the Linux instance

With all the steps above, you're now ready to launch an Linux instance.

>Use the below values/inputs [while following the instructions on how to launch a linux instance in OpenStack Dashboard here](../../tasks/openstack/launch-ubuntu-instance.md).

1. Instance name: `server1`
2. Source Image: `Ubuntu-18-04` (no volumes)
3. Flavor: `m1.small`
4. Network: `ssoid-test` (you created this network earlier;)
5. Security Group: `Default` (no need to create one, this is already present. Every OpenStack project comes with a Default security group that blocks all incoming traffic to the instances in that group and allows all outgoing traffic.)
6. Key Pair: `ssoid-key` (you created this earlier with your ssoid or username)
7. **IMPORTANT** - Configuration: Use a cloud-init script to set a password for your Ubuntu instance.

### Lab Task 2-5: Access your instance through the browser using HTML 5 console (noVNC)

The launch [instance instructions](../../tasks/openstack/launch-ubuntu-instance.md#accessing-your-ubuntu-instance-through-the-browser-console) provides details on how to access your instance through the browser itself. Once at the console, you click in the console and then start typing. You can login with the username `ubuntu` and the password you set in the configuration script during launch!

### Lab Task 2-6: Cleanup cloud resources after you're done

It's always a good idea to delete/remove any **unwanted** cloud resources; as long as you're sure you don't need them. See [some guidelines how to clean up / delete cloud resources in OpenStack Dashboard here](../../tasks/openstack/clean-up-resources.md) if needed.
