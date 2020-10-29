# Salesforce DX Project: Next Steps

Repository to replicate issues caused by "Protected" custom object in 2GP.

## How to replicate

Create a namespace, link it to your devhub and replace `namespace` values in `sfdx-project.json` and `config/project-scratch-def.json` files

Checkout code from master branch and reate a package by running below command

`sfdx force:package:create --name fmaObjectTest --packagetype Managed --path force-app`

Create first version of the package by running below command

`sfdx force:package:version:create --package fmaObjectTest --installationkeybypass --definitionfile config/project-scratch-def.json --codecoverage --wait 10`

Promote first version of the package

`sfdx force:package:version:promote --package FIRST_VERSION_ID_HERE --noprompt`

Install the package in an environment.

Checkout `second_version` branch and create second version of the package by running below command

`sfdx force:package:version:create --package fmaObjectTest --installationkeybypass --definitionfile config/project-scratch-def.json --codecoverage --wait 10`

At the time of writing second version is failing with below error,

`CostHub__c: Cannot modify managed object: entity=CustomEntityDefinition, component=01I0x000000YQBH, state=MANAGED_RELEASED, You can't reduce the visibility from Public to Protected for a released Custom Object.`
