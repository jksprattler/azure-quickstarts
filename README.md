# Azure CLI and PowerShell commands

## Create a VM:
```
az vm create --resource-group testdummy2-rg --name demovm2 --image win2019datacenter --admin-username demousr --admin-password AzurePortal@123
```
```
New-AzVm -ResourceGroupName testdummy2-rg -Name demovm3 -Location EastUS -Image win2019datacenter
```

## Create and Add data disks:
$resourcegroup = 'testdummy2-rg'
$machinename = 'demovm2'
$location = 'East US'
$storageType = 'Standard_LRS'
$dataDiskName = 'newdisk01'
$dataDiskSize = 20
 
$datadiskConfig = New-AzDiskConfig -SkuName $storageType -Location $location -CreateOption Empty -DiskSizeGB $dataDiskSize
$dataDisk01 = New-AzDisk -DiskName $dataDiskName -Disk $datadiskConfig -ResourceGroupName $resourcegroup
$vm = Get-AzVM -Name $machinename -ResourceGroupName $resourcegroup
$vm = Add-AzVMDataDisk -VM $vm -Name $dataDiskName -CreateOption Attach -ManagedDiskId $dataDisk01.Id -Lun 1
 
Update-AzVM -VM $vm -ResourceGroupName $resourcegroup
