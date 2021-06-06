# Run Multiple instance of same distro in WSL2
Often it might be required that you have to run several instances of the same distro to keep things more organized in WSL. Here is method to do that. 


You might want to start with fresh install of your baseline distro. For our example we will user Ubunutu 20.04 LTS. IF you already have it installed you can reset it to clean state by following the below steps.
1. Open “Settings”
1. Click on “Apps”
1. Click on “Apps & features”
1. Select Linux Distro Name — e.g., Ubuntu 20.04 LTS
1. Click on “Advanced Options” link
1. Click on “Reset” button to reset your Linux Distro (e.g., Ubuntu 20.04 LTS) to initial install state. Please note that everything will be deleted.
1. When the reset is completed, start your Linux Distro (e.g., Ubuntu 20.04 LTS) then setup your Linux Distro by entering username and password.
1. Run ```sudo apt-get update``` (for Ubuntu 20.04 LTS) to retrieves information about what packages can be installed, including what updates to currently installed packages packages are available, from Internet sources.
1. Run ```sudo apt-get upgrade``` (for Ubuntu 20.04 LTS) to install available upgrades of all packages currently installed on the system from Internet sources.
1. IF you want you also apply the changes described in my other repo for making life easier with WSL2. 

## Export the linux Distro in WSL2
Next create an export image of your Linux Distro. This image will be used to create the multiple instances of same Linux Distro.
 1. Open a new command prompt or a new Powershell.
 1. Run the command  ``` wsl --list```  to view a list of Windows Subsystem for Linux Distributions installed on your computer. For example on my computer, it would be “Ubuntu-20.04”.
 1. Run the command ``` wsl — export <DistributionName> <FileName>```  in mycase  ```wsl — export Ubuntu-20.04 rootfs.tar.gz``` to export your Linux distros to a TAR file. This will create a file entitled "rootfs.tar.gz" on your computer in the current path.
 1. Copy the newly created file named “roofts.tar.gz” to your desired directory. For example on my computer, I have copied the file to c:\linux\ubuntu-20.04.clean directory.
 
 ## Use the wsldl tool to run mutliple instances of same distro
 We need to download, install and configure WSLDL. WSLDL is an open-source Advanced WSL Distribution Launcher / Installer that can be used to configure and launch a same Linux Distro as a different Linux instances.
1. Download “Launcher.exe” from How to [Install](https://wsldl-pg.github.io/docs/How-to-Install/) and save the file to your desired directory. I saved the file to c:\linux\ubuntu-20.04.second directory. For documentation on wsdl check here [Wsldl official documentation](https://wsldl-pg.github.io/docs/How-to-Install/) 
1. Copy the roofts.tar.gz to the direcotry c:\linux\ubuntu-20.04.second 
3. Rename the file “Launcher.exe” to your desired Linux Distro name “Ubuntu-20.04.second.exe”  in my case
4. To install WSLDL, just double click on the Ubuntu-20.04.second.exe. Installaition starts and vhdx file is created. 
5. Delete copied “rootfs.tar.gz” after the installation is completed.
6. To configure WSLDL to default to your username when you run your Linux Distro on WSL, run the command ``` Ubuntu-20.04.second config --default-user <username> ``` in my case ``` Ubuntu-20.04.second config --default-user chcoders ```.
7. To run a newly installed Linux Distro on WSL, just run the command ``` Ubuntu-20.04.second.exe ``` in c:\linux\ubuntu-20.04.second directory from command prompt or Powershell.
8. Since the launcher has the default icon if you want you could get the correct icon from the link here (https://github.com/yuk7/wsldl/tree/main/res) and change the icon to appropriate Linux Distro.
9. You can repeat the steps in the subsection as many times as you want with ubuntu-20.04.third and so on to create as many distros as you want.



