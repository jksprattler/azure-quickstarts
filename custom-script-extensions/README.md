# Usage instructions for extensions

## Usage for install_web.sh
- This shell script will install a basic nginx web server on a Linux VM named "linuxvm" by calling out to the files stored in this github repo
- Run the following command from the Azure CLI
```
az vm extension set --resource-group testdummy2-rg --vm-name linuxvm --name customScript --publisher Microsoft.Azure.Extensions --settings customscript.json
```
