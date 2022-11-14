on this page I will try to list the commands I may need someday

How to Delete Multiple Azure Resource Groups with Bash and Azure CLI via Azure Cloud Shell

Azure currently does not provide a way to delete multiple resource groups at once.

I tried this and it worked successfully

Assign a new tag named “Delete” to the resource groups you want to delete.

This script will loop through all resource groups that have the tag ‘delete’ and will prompt you to confirm the deletion. If you type ‘y’, then the resource group will be deleted. If you type ‘n’ that resource group will be skipped.

If you don’t want to be prompted for every resource group, then add a -y to the az group delete -n ${rg} command like so: az group delete -n ${rg} -y.

```
###### az group list --tag delete --query [].name -o tsv | xargs -otl az group delete --no-wait  -n
```

I found the code from this site

https://blog.jongallant.com/2020/05/azure-delete-multiple-resource-groups/