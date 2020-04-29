# ARMVMDeploy
ARM template deployment via powershell of a Windows VM 


Powershell deployment script
===============================
$resourceGroupName = Read-Host -Prompt "Enter the Resource Group name"
$location = Read-Host -Prompt "Enter the location (i.e. centralus)"
$templateUri = "C:\Users\USER\Downloads\azure-vm\deployment\azuredeploy.json"
New-AzResourceGroupDeployment -ResourceGroupName $resourceGroupName -TemplateUri $templateUri -Location $location   



Running the Powershell deployment script:
=========================================
PS C:\Users\USER> cd .\Downloads\
PS C:\Users\USER\Downloads> cd .\azure-vm\
PS C:\Users\USER\Downloads\azure-vm> dir


    Directory: C:\Users\USER\Downloads\azure-vm


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----       28/04/2020     14:38                .vscode
d-----       28/04/2020     15:14                deployment


PS C:\Users\USER\Downloads\azure-vm> cd  .\deployment\
PS C:\Users\USER\Downloads\azure-vm\deployment> dir


    Directory: C:\Users\USER\Downloads\azure-vm\deployment


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       28/04/2020     14:38           9233 azuredeploy.json
-a----       28/04/2020     14:39            282 azuredeploy.parameters.json
-a----       28/04/2020     15:27            340 azureps.ps1
-a----       28/04/2020     14:39            282 metadata.json


PS C:\Users\USER\Downloads\azure-vm\deployment> .\azureps.ps1
Enter the Resource Group name: VirtualMachineResourceGroup
Enter the location (i.e. centralus): uksouth
New-AzResourceGroupDeployment : The term 'New-AzResourceGroupDeployment' is not recognized as the name of a cmdlet, function, script file, or operable program.
Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At C:\Users\USER\Downloads\azure-vm\deployment\azureps.ps1:4 char:1
+ New-AzResourceGroupDeployment -ResourceGroupName $resourceGroupName - ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (New-AzResourceGroupDeployment:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
==============
Nb: need to install powershell azure components
PS C:\Users\USER\Downloads\azure-vm\deployment> install-module -name Az -AllowClobber -Scope CurrentUser

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program
Files\PackageManagement\ProviderAssemblies' or 'C:\Users\USER\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by
running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its InstallationPolicy value by running the Set-PSRepository
cmdlet. Are you sure you want to install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y


PS C:\Users\USER\Downloads\azure-vm\deployment> ./azureps
Enter the Resource Group name: VirtualMachineResourceGroup
Enter the location (i.e. centralus): uksouth

cmdlet New-AzResourceGroupDeployment at command pipeline position 1
Supply values for the following parameters:
(Type !? for Help.)
adminUsername: destro
adminPassword: ********************


DeploymentName          : azuredeploy
ResourceGroupName       : VirtualMachineResourceGroup
ProvisioningState       : Succeeded
Timestamp               : 29/04/2020 09:25:59
Mode                    : Incremental
TemplateLink            :
Parameters              :
                          Name                Type                       Value
                          ==================  =========================  ==========
                          adminUsername       String                     destro
                          adminPassword       SecureString
                          dnsLabelPrefix      String                     vm-4rmu4l25pke5s
                          windowsOSVersion    String                     2019-Datacenter
                          departmentName      String                     MyDepartment
                          applicationName     String                     MyApp
                          createdBy           String                     MyName
                          vmSize              String                     Standard_D2_V3
                          location            String                     uksouth

Outputs                 :
DeploymentDebugLogLevel :



