# Launch an Ubuntu instance

The steps below apply for most use cases. Your instructor will provide specific guidance if needed.

## Prerequisites before launching any instances

You should have already:

1. [Created a network, a subnet](create-network.md) within that network, and a [router](create-router.md) connected to that network (in most use cases) which also connects to an external network
2. Created a [Key Pair](create-key-pair.md)
3. Configured a security group for this instance as needed unless the default security group works for your use case

## Launch Ubuntu instance with a dynamic IP address

1. Navigate to Project -> Compute -> Instances
2. Click Launch Instance
3. In the Launch Instance wizard window you will enter a series of inputs and move to the next step by clicking Next and then finish the wizard by clicking Launch.
   * Instance Name: provide a name. Best to keep it all lower case and no spaces. This will become the "hostname" of the instance you're launching.
   * Description: optional, for your reference
   * Availability Zone: leave default, i.e. no change
   * Instance Count: 1
   * Click Next
   * On the Source tab:
      * Select Boot Source: Image
      * Create New Voume: No
      * Scroll down to see list of Ubuntu Images available. Click on the Up Arrow next to the one you wish to use (e.g., `Ubuntu-18-04` signifying Ubuntu 18.04 LTS edition)
      * Click Next
   * On the Flavor tab:
      * Select flavor `m1.small` (click Up Arrow next to it) unless specified otherwise by your instructor. This flavor will allot 1 virtual CPU, 1GB RAM, and 10GB of hard disk space to your instance.
      * Click Next
   * On the Networks tab:
      * Select the network you are launching this instance on; from the "Available" section and move it to the Allocated section by clicking on the Up Arrow next to your network (e.g., ssoid-net)
   * On the Network Ports tab:
      * Skip this section (in most cases, unless you need it)
   * On the Security Groups tab:
      * Select the security group you created or choose Default if your instructor did not specify any requirements. The "Default" security group will likely already be selected under "Allocated". If you need a different security group, click on the Down Arrow next to Default to remove it from Allocated section and assign a different one. If another security group is not present in the list, you'll have to cancel wizard, create it first, and then start launch instance wizard again.
   * On the Key Pair tab:
      * Select the Key Pair you created and move to Allocated by clicking on the Up Arrow.
   * **Optional**: Configuration tab
      * If you need to set a password for the default user then add the following cloud-init script in the "Customization Script" box:

         ```yaml
         #cloud-config
         password: mypassword #replace "mypassword" with your password
         chpasswd: { expire: False}
         ```

      > ***Note***: the above practice is not recommended and should be used if you are only going to access your instance through the HTML 5 console. For demo and lab assignments, it's fine to do so.

   * Skip through the next sections: Server Groups, Scheduler Hints, and Metadata; unless specified otherwise by your instructor, by clicking next.

4. Click Launch Instance to start the instance creation process.

You can view the instance launch progress through the Project -> Compute -> Instances page. A couple minutes later, if instance status shows "Running" then everything worked.

## Accessing your Ubuntu instance through the browser console

There are a few ways to get to the console. Here are two and we recommend the second one:

### Connecting to console from the Instances page

1. On the Instances page, click on the drop down under Actions. Choose Console;
2. The Ubuntu console should appear within your browser.
3. Click on "Click here to show only console" to open the console in a full window. You can also open that link in a new window (Shift + click the link or right click and choose Open in New Tab/Window)

### Connecting through the Network Topology page (Preferred)

1. Go to the Network Topology and left click/hover on the instance icon (choose the Normal View (click button) if you don't see the instance names on icons). Then click on "View Console".

### Login (from console)

Username: `ubuntu`

Password: (the one you set in your Customization Script during instance launch)

   >***This will be your administrative (sudo) password.***

## Retrieving administrative password for the instance if needed

If you set a password, you can retrieve the current administrative password for an instance after launch if needed.

1. On the Instances page, click on the drop down under Actions. Choose **Retrieve Password**.
2. On the Retrieve Password window, click on browse to find your private key (from the same Key Pair you used to launch the instance). Note the private key is not sent to the server but only used in your browser.
3. Click on Decrypt Password.
4. The password should now show in the Password field at the bottom left.

> **Note:** if an encrypted password is not displayed on the Retrieve Password window then it means that there was no password set during launch or after launch. In this case, there is no way to retrieve the password for Windows instances. You will have to launch a new instance and delete the one without the password. For Linux instances, however, you should still be able to connect to the Linux instances using your key (via SSH, if floating IP is configured).
