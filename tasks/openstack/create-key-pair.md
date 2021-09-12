# Create a new Key Pair or import a Key Pair in OpenStack Horizon Dashboard

When working with OpenStack, you will often need to use key based authentication. Keys are used for things such connecting to instances via SSH using key-based authentication, obtaining instance passwords (if any are set), sending authenticated API requests, etc.

You can either create a new key pair or import your own existing (SSH or X.509 based) public key(s).

You should have at least one key pair for every OpenStack project you have access to. **Also, you should never share your private keys with others**.

## Add a SSH key pair

Create at least one key pair for each project. Create a Key Pair through the dashboard and download and save to your .ssh directory (if you don't know what .ssh directory is, [see this first](../../concepts/general/ssh-directory.md)). Be sure to set appropriate file permissions.

1. Log in to the dashboard.
2. Be sure you have selected the appropriate project from the drop down menu at the top left.
3. On the Project tab, open the Compute tab.
4. Click the Key Pairs tab, which shows the key pairs that are available for this project.
5. Click Create Key Pair.
6. In the Create Key Pair dialog box, enter a name (best to use all lower case and no spaces) for your key pair.
7. If available, under Key Type, choose ``SSH Keys``
8. Click Create Key Pair.
9. The private key will be downloaded automatically.  **Warning: This will be the only time you will have the ability to download the private key. ALSO, BE SURE to save the key (it will be a .pem file) into your .ssh directory.**
10. **Be sure to set properfile permissions on the private key file, (so that only you can read and write to the file)**

> To set permissions, open Terminal on Mac/Linux or Git Bash on Windows and navigate to the .ssh directory and run the following command:
>> `chmod 0400 yourPrivateKeyName.pem` (specify your keyname of course)
>

## Import a key pair (i.e. upload your existing PUBLIC key)

1. Log in to the dashboard.
2. Select the appropriate project from the drop down menu at the top left.
3. On the Project tab, open the Compute tab.
Click the Key Pairs tab, which shows the key pairs that are available for this project.
4. Click Import Key Pair.
5. In the Import Key Pair dialog box, enter the name of your key pair, copy the **public** key into the Public Key box, and then click Import Key Pair. (In Windows, open the public key file, typically with extension ``.pub``, in an editor such as Notepad and select all, copy, and paste in the Public Key box. Windows, MAC, and Linux users can also simply "cat" the public key from the terminal/powershell and copy/paste.) **Be sure not to copy paste your private key!**
6. The OpenStack Compute database registers the public key of the key pair.
7. If successful, the Dashboard lists the key pair on the Key Pairs tab.
