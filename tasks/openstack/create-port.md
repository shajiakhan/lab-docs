# Create a port in an OpenStack network

1. Log in to the dashboard.
2. Select the appropriate project from the drop-down menu at the top left.
3. On the Project tab, click Networks category.
4. Click on the Network Name of the network in which the port has to be created.
5. Go to the Ports tab and click Create Port.
6. In the Create Port dialog box, specify the following values.
   * Name: Specify name to identify the port. It's usually better to name the port as "devicename-port" where "devicename" is the name of the device which will be attached to this port.
   * Enable Admin State: Leave checked.
   * Device ID: Device ID attached to the port. Leave blank if not currently known.
   * Device Owner: Device owner attached to the port. Leave blank if not currently known.
   * Specify IP address or subnet: If you don't need to specify a "static IP address", choose "Subnet" and then Select the subnet you wish to attach this port to. If you need to specify an address (typically used for static IP address assignments on instance ports), then select Fixed IP Address and then specify the IP address you need (for certain lab assignments, your instructor will provide you with the fixed IP address to use.)
   * MAC Address: Leave blank in most cases. Specify MAC address of the port. Leave blank if you don't need to have a specific MAC address.
   * Port Security: Leave checked (unless specifically needed to be turn off)
   * VNIC Type: Select the VNIC type that is bound to the neutron port. In most cases this should be set to **"Normal"**
7. Click Create Port.

The new port is now displayed in the Ports list.
