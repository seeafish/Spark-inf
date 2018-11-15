Spark Infrastructure Code
=========================

These Azure Resource Manager (ARM) templates will deploy the infrastructure for the Spark application.

The templates all have a matching params file, which overrides the defaults in the templates.

How to
------
Using Azure CLI

`az group deployment create -g [resource group name] -n [name of deployment] --template-file [path] --parameter @[path]`

Running Order
-------------

All templates should be run in the same Resource Group.

1. Vnet
2. Keyvault
3. StorageAccount
4. Database
5. App
6. FrontEnd

Current issues
--------------
Due to time constraints, the following issues exist with the infrastructure as it stands.

* The Azure Diagnostics isn't reporting memory metrics. It has a somewhat convoluted XML confiuguration. It can easily be replaced with OMS, or even NewRelic.
* NSGs only at the VM level. Ideally should have some subnet level NSGs or, better still, ASGs.
* App layer LB has a Public IP; it's meant to be a private LB.
