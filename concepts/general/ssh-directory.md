# Finding the .ssh directory or creating one if needed to save key files

When working in cloud environments (e.g., launching a Linux instance in AWS) users often have to download the private key of the key pair they generate when using a cloud service. Typically, users have only one chance to download and save the private key file to their local computer. This tutorial provides some tips on where to save those keys.

**When creating or downloading keys, you should store them in the .ssh directory.** The ``.ssh`` directory (folder) is a hidden directory (the ``.`` before name implies a directory is hidden). The .ssh directory is typically found in the user's home directory.

> On Linux: ``/home/your_username/.ssh``
> On MacOS: ``/Users/your_username/.ssh``
> On Windows: ``C:\Users\your_username\.ssh``

The .ssh directory is used to hold SSH keys (and other types of keys and some other types of files such as known_hosts etc.).

See some tips below if you are not sure how to save key files to this directory.

## Linux Users

Linux users will have the .ssh directory in their home directory:

> /home/your_username/.ssh

Just be sure to download or move the .pem private key file to your .ssh directory and set the appropriate file permissions (e.g., `chmod 400 yourPrivateKey.pem`).

## MacOS Users

Mac users will have their .ssh directory under their home directory:

> /Users/your_username/.ssh

Just be sure to download or move the .pem private key file to your .ssh directory and set the appropriate file permissions (e.g., `chmod 400 yourPrivateKey.pem`).

If going through Finder, please ensure hidden file view is enabled: ``Shift + Command + .`` (press Shift key plus Command key plus the **.**  ((period)) key) while in Finder.

If hidden view is enabled and you still cannot locate the .ssh directory under your home directory, you could simply create one and set proper permissions on the directory.

Open Terminal and issue the following commands:
> ``mkdir ~/.ssh`` (create directory .ssh in home folder, the ~ is path to your home directory /Users/your_username)
> ``chmod 700 ~/.ssh`` (set full read/write/execute permissions for yourself and deny any permissions to all others)

Continue by storing keys in this folder from now on and be sure to set proper permissions on the key itself (as shown above)

## Windows Users

Windows users can check if the .ssh directory is already present. If yes, save the keys there. If directory is not present, simply create the directory. See tips below on how to check whether .ssh is alredy present. If it is not present, then see how to create the .ssh directory either through the terminal or through File Explorer.

### Windows 10: Checking if the .ssh directory is present

Open PowerShell or CMD (press Windows key and type in ``powershell`` or ``cmd`` and then choose the program from the list to open). Type in the following at the > prompt to list the contents of the .ssh directory:

``dir 'C:\Users\your_username\.ssh'`` (replace your_username with your username of course)

If directory is present, you should see a listing of contents.

If you get an error message, .ssh directory is not present. See how to create one below.

### Windows 10: Create the .ssh directory (IF NOT PRESENT) from PowerShell

**The .ssh directory is within your home directory. Create the directory if it doesn't exist.** In Windows, the .ssh directory should typically be in "C:\Users\your_username\.ssh" (replace your_username with your username of course).

``mkdir -Path 'C:\Users\your_username\.ssh'`` (the . before ssh tells that this is a "hidden" directory. Be sure to replace your_username with your actual username).

Continue with your work by saving your key file(s) in this directory from now on.

### Windows 10: Create the .ssh directory (IF NOT PRESENT) from File Explorer (alternative to creating it from PowerShell)

1. Navigate to your home directory ("C:\Users\your_username\").
2. Right click to make a New Folder.
3. Hidden folder names are preceded by a ``.``. To create a hidden .ssh folder, in the folder name of new folder, type in "``.ssh.``" (notice the period at the end too. The ending period is a way to specify directory names that are hidden while creating them in File Explorer and when you don't have hidden items viewable in File Explorer.)

Continue with your work by saving your key file(s) in this directory from now on. Also, it will be useful to enable hidden item view in File Explorer for future. See below.

#### Enable hidden item view in File Explorer

The .ssh directory is a hidden directory and may not be visible through File Explorer by default. If you do not see the .ssh directory in your home directory as above, you can enable "Hidden Items" from View tab in File Explorer. Just check the box next to "Hidden items" under View Tab -> Show/Hide.

You can also do so through Folder Options -> View -> Advanced Settings -> Hidden Files and Folders -> Show hidden files, folders, and drives.
