# Set up a linux VM on Windows

## Install Oracle VM VirtualBox

1. Go to https://www.virtualbox.org/, click Downloads, and download the installer for windows under "VirtualBox x.x.xx platform packages". At the time of this writing, the latest version is available [here](https://download.virtualbox.org/virtualbox/6.1.26/VirtualBox-6.1.26-145957-Win.exe).
1. Install VirtualBox using the downloaded installer.

## Get the VM Image

1. Go to [OSBoxes.org/ubuntu](https://www.osboxes.org/ubuntu/).
1. Download VirtualBox image for the "`Ubuntu 20.04.3 Focal Fossa`", or simply [click here](https://sourceforge.net/projects/osboxes/files/v/vb/55-U-u/20.04/20.04.3/Desktop/64bit.7z/download). Extract the file to a safe location, you can use [7-zip](https://www.7-zip.org) for extracting the `.7z` file.
1. You can also see the VM credentials in the "`Info`" tab. These are the details:
    - Username: `osboxes`
    - Password: `osboxes.org`
    - Guest Additions: Installed
    - Keyboard Layout: US (Qwerty)
    - VMware Compatibility: Version 10+

## Set up the Ubuntu VM

1. Open VirtualBox from start menu.
1. From to top menu, click on `Machine`, then select `New`.
1. Enter a name for your VM.
1. Leave the default value in `Machine Folder` as is.
1. Select the `Type` of VM as `Linux`.
1. Select the `Version` to `Ubuntu (64 bit)`.
1. Set the `Memory size` to `4096 MB` or above. If you do not see the option to select memory size, click on `Expert Mode` button at the bottom.
1. In the `Hard disk` section, select `Use an existinf virtual hard disk file` and open the extracted `.vdi` file using the open button at the right-bottom corner.
1. Click on `Create`.

#### Optional Optimizations:
1. Do not start the VM yet. Right clock the VM and open `Settings`.
1. Go to `System` > `Processor` settings and increase the Processors count to `2` or more.
1. Go to `System` > `Display` settings and increase the Video Memory to `64 MB` or more. Also enable `3D Acceleration`.
1. Go to `System` > `Network` > `Adapter 1` settings and set `Attached to` to `Bridged Adapter`.
1. Go to `Shared Folders` settings and click on the plus icon on the right to add a shared folder. Select any folder from your computer and give a desired `Folder Name`. Check the `Auto-mount` option, enter `/` as `Mount Point` and click `OK`.
1. Save all the settings by pressing `OK`.

#### Bug: Can not access shared folder

1. Re-install Guest Additions in the VM. When the VM is running and logged in, from the top-menu, click on `Devices` and then select `Insert Guest Additions CD Image` and follow the install instructions.
1. When the installation is complete, open another terminal and run this command: `sudo adduser osboxes vboxsf`.
1. Restart your VM.
1. If you still can not access the shared folder, shut down the VM and remove the shared folder from VM settings and add it again.

- Note: its a known bug in VirtualBox that `gedit` editor is unable to edit files in shared folders. So you can use `VS Code`.
 
<blockquote>
Congratulations! Your VM is now set up. Use the credentials above to log in.
</blockquote>