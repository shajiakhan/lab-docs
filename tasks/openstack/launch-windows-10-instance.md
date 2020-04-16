# Launch an Windows 10 instance in OpenStack

The steps below apply for most use cases. Your instructor will provide specific guidance if needed.

## Prerequisites before launching any instances

You should have already:

1. [Created a network, a subnet](create-network.md) within that network, and a [router](create-router.md) connected to that network (in most use cases) which also connects to an external network
2. Created a [Key Pair](create-key-pair.md)
3. Configured a security group for this instance as needed unless the default security group works for your use case

## Launch Windows 10 instance with a dynamic IP address

Log in to the OpenStack dashboard. Be sure you have selected the appropriate project from the drop down menu at the top left.

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
      * Scroll down to see list of Windows Images available. Click on the Up Arrow next to the one you wish to use (e.g., `Win-10-Pro`)
      * Click Next
   * On the Flavor tab:
      * Select flavor `m1.medium` (click Up Arrow next to it) unless specified otherwise by your instructor. This flavor will allot 1 virtual CPU, 4GB RAM, and 30GB of hard disk space to your instance.
      * Click Next
   * On the Networks tab:
      * Select the network you are launching this instance on from the "Available" section and move it to the Allocated section by clicking on the Up Arrow next to your network (e.g., `ssoid-lab6`)
   * On the Network Ports tab:
      * Skip this section (in most cases, unless you need it)
   * On the Security Groups tab:
      * Select the security group you created or choose `Default` if your instructor did not specify any requirements. The "Default" security group will likely already be selected under "Allocated". If you need a different security group, click on the Down Arrow next to Default to remove it from Allocated section and assign a different one. If another security group is not present in the list, you'll have to cancel wizard, create it first, and then start launch instance wizard again.
   * On the Key Pair tab:
      * Select the Key Pair you created and move to Allocated by clicking on the Up Arrow.
   * Skip through the next sections: Configurations, Server Groups, and Scheduler Hints unless specified otherwise by your instructor, by clicking next.
   * On the Metadata tab:
      * Under the Available Metadata (left side): Type in ``admin_pass`` in the **Custom** field. Click on the **+** sign to move the custom metadata field to the Existing Metadata section (right side).
      * Then, type in the Administrator password you wish to use on your Windows Server instance. *You will use this password to login to the server*. **Be sure to choose a strong password following Windows requirements**
4. Click Launch Instance to start the instance creation process.

You can view the instance launch progress through the Project -> Compute -> Instances page. If instance status shows "Running" then everything worked.

> **Note: as there are certain initialization scripts that must run before the instance allows you to login, please wait at least 10 to 15 minutes before attempting to login. Just to be safe.**

## Accessing your Windows 10 instance through the browser console

There are a few ways to get to the console. Here are two and we recommend the second one:

### Connecting to console from the Instances page

1. On the Instances page, click on the drop down under Actions. Choose Console;
2. The Windows 10 screen should appear within your browser.
3. Click on "Click here to show only console" to open the console in a full window. You can also open that link in a new window (Shift + click the link or right click and choose Open in New Tab/Window)

### Connecting through the Network Topology page (Preferred)

1. Go to the Network Topology and left click/hover on the instance icon (choose the Normal View (click button) if you don't see the instance names on icons). Then click on "View Console".

### First time login (once on Windows Console)

1. Because you're accessing the virtual machine console through the browser (!), you don't have access to features such as copy/paste from your computer into the virtual machine (instance) console.
2. To login, left click anywhere in the Windows screen **Or** click the button at the top right of the console that says "Send CtrlAltDel". Doing so will send the special Ctrl + Alt + Del key combination to the virtual machine.
3. Login with the password you set in the "admin_pass" metadata key during instance launch. Change your password if you're prompted to do so. *Choose a strong password following Windows requirements*. Leave the username unchanged (use whatever appears by default) the first time you're logging in.

   >***The newly changed password will then be your administrative password.***

## Retrieving administrative password for the instance if needed

You can retrieve the current administrative password for an instance after launch if needed.

1. On the Instances page, click on the drop down under Actions. Choose **Retrieve Password**.
2. On the Retrieve Password window, click on browse to find your private key (from the same Key Pair you used to launch the instance). Note the private key is not sent to the server but only used in your browser.
3. Click on Decrypt Password.
4. The password should now show in the Password field at the bottom left.

> **Note:** if an encrypted password is not displayed on the Retrieve Password window then it means that there was no password set during launch or after launch. In this case, there is no way to retrieve the password for Windows instances. You will have to launch a new instance and delete the one without the password. (For Linux instances, however, you should still be able to connect to the Linux instances using your key (via SSH)).
