# Finding the .ssh directory or creating one if needed

**When creating or downloading keys, you should store them in the .ssh directory.** The .ssh directory (folder) is a hidden directory (the . before name implies a directory is hidden) typically found in the user's home directory.

On Linux/MAC: ``/home/your_username/.ssh``
On Windows: ``C:\Users\your_username\\.ssh``

The .ssh directory is used to hold SSH keys (and other types of keys and some other types of files such as known_hosts etc.).

See some tips below if you are not sure how to save key files to this directory.

## MAC/Linux Users

MAC and Linux users will have the .ssh directory in their home directory (typically /home/your_username/.ssh). Just be sure to download the .pem private key file to your .ssh directory and set the appropriate file permissions (see above).

Windows users can check if the directory is already present. If yes, simply save the keys there. If directory is not present simply create the directory.

### Windows 10: Checking if the .ssh directory is present

Open PowerShell or CMD (press Windows key and type in powershell or cmd and then choose the program from the list to open). Type in the following at the > prompt to list the contents of the .ssh directory:

``dir 'C:\Users\your_username\.ssh'`` (replace your_username with your username of course)

If directory is present, you should see a listing of contents. But, if you don't see it when viewed through File Explorer, see below.

If you get an error message, .ssh directory is not present. See how to create one below.

### Windows 10: Create the .ssh directory (IF NOT PRESENT) from PowerShell

**The .ssh directory is within your home directory. Create the directory if it doesn't exist.** In Windows, the .ssh directory should typically be in "C:\Users\your_username\\.ssh" (replace your_username with your username of course).

``mkdir -Path 'C:\Users\your_username\.ssh'`` (the . before ssh tells that this is a "hidden" directory.)

### Windows 10: Create the .ssh directory (IF NOT PRESENT) from File Explorer

Navigate to your home directory ("C:\Users\your_username\"). Right click to make a New Folder. Hidden folder names are preceded by a ``.``. To create hidden .ssh folder, in the folder name type in "``.ssh.``" (notice the period at the end too. The ending period is a way to specify directory names that are hidden while creating them in File Explorer and when you don't have hidden items viewable in File Explorer.)

#### Enable hidden item view in File Explorer

The .ssh directory is a hidden directory and may not be visible through File Explorer by default. If you do not see the .ssh directory in your home directory as above, you can enable "Hidden Items" from view settings or you may have to enable the view setting in folder options.
