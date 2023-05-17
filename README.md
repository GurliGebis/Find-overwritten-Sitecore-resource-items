# Find-overwritten-Sitecore-resource-items
- A Sitecore PowerShell Report for Sitecore IAR items, Items as Resources.
- A Content Editor warning for IAR items and IAR overridden, overwritten items in Sitecore PowerShell
- A overwritten resource item compare in the Report
- A overwritten resource item restore/delete in the Report

## PowerShell only
Certainly with Sitecore XM Cloud there is more resistance to extend the Sitecore CMS using c# code in a custom DLL. But with Sitecore PowerShell a lot can be done these tools are completely in Sitecore PowerShell and everything is in Sitecore items no files needed.

## For Sitecore 10.2, Sitecore 10.3+ and XM Cloud
IAR Sitecore items can be overwritten by a sql database item, With the Sitecore PowerShell report you can easy find the item and delete/restore the item as resource.

![Example](https://raw.githubusercontent.com/jbluemink/Find-overwritten-Sitecore-resource-items/main/find-overwritten-sitecore-resource-items.png)

![compare-Example](https://raw.githubusercontent.com/jbluemink/Find-overwritten-Sitecore-resource-items/main/iar-compare-report.png)

See blog [Items as resources by sitecore part 3](https://uxbee.nl/actueel/items-as-resources-by-sitecore-part-3)
See blog [Items as resources by Sitecore part 2: reports](https://uxbee.nl/actueel/items-as-resources-by-sitecore-part-2)
Based on the first version of this tool. See [gist](https://gist.github.com/jbluemink/ac0851a20a3e94a25a6d998dcd25f466)

## IAR Content Editor Warning for Sitecore 10.3+ or XM Cloud.
See blog : [Item as resources PowerShell Content Editor Warning](https://www.stockpick.nl/sitecore/item-as-resources-powershell-warning/)

![Example](https://raw.githubusercontent.com/jbluemink/Find-overwritten-Sitecore-resource-items/main/Overridden-item-as-resource-content-editor-warning.png)


## Download and Install the tool, Powershell Report
For just installing and use the tool the easy way is:
copy items.master.iaroverwrittenreport.dat  to \sitecore modules\items\master of your Sitecore CM instance.

## For using the Sitecore CLI and optional using Visual Studio to edit the module.json
### Install Sitecore Command Line Interface
See: [Install Sitecore Command Line Interface](https://doc.sitecore.com/xp/en/developers/103/developer-tools/install-sitecore-command-line-interface.html)

#cd {project folder}\
cd C:\projects\Find-overwritten-Sitecore-resource-items

dotnet new tool-manifest
dotnet nuget add source -n Sitecore https://sitecore.myget.org/F/sc-packages/api/v3/index.json \
dotnet tool install Sitecore.CLI --version 5.1.25

#dotnet sitecore init

dotnet sitecore login --authority https://id.{host}.local --cm https://cm.{host}.local --allow-write true

#push item to Sitecore\
dotnet sitecore ser push

#pull sitecore item to files\
dotnet sitecore ser pull


### Generate IAR .dat file
dotnet sitecore itemres create -o iaroverwrittenreport


