# aci-flp-labs
This is a set of scripts and tools use to generate a docker image that will have the aci-flp-labs binary used to evaluate your AKS troubleshooting skill.

It uses the shc_script_converter.sh (build using the following tool https://github.com/neurobin/shc) to abstract the lab scripts on binary format and then the use the Dockerfile to pack everyting on a Ubuntu container with az cli and kubectl.

Any time the labs script require an update the github actions can be use to trigger a new build and push of the updated image. This will take care of building a new script binary as well as new docker image that will get pushed to the corresponding registry. The actions will get triggered any time a new release gets published.

Here is the general usage for the image and aci-flp-labs tool:

Run in docker: `docker run -it typeoneg/aci-flp-labs:latest`

aci-flp-labs tool usage:
```
$ aci-flp-labs -h
aci-flp-labs usage: aci-flp-labs -l <LAB#> -u <USER_ALIAS> [-v|--validate] [-r|--region] [-h|--help] [--version]


Here is the list of current labs available:

*************************************************************************************
CORE LABS:
* 1. ACI deployment failure configuration
* 2. ACI deployment authorization failed
* 3. ACI connection issue between 2 container groups V1
* 4. ACI deployment failed netwwork configuration V1
* 5. ACI deployment failed with Log analytics
* 6. ACI container create failure with Azure File mount
* 7. ACI deployment failure with Storage account
* 8. ACI container create image pull failure V1Extra Labs:

EXTRA LABS:
* 9.  ACI deployment failure on pre-existing vnet
* 10. ACI container continuous restart issue
* 11. ACI connection issue to container
* 12. ACI deployment failed netwwork configuration V2
* 13. ACI connection issue between 2 container groups V2
* 14. ACI container create image pull failure V2

*************************************************************************************

"-l|--lab" Lab scenario to deploy (3 possible options)
"-r|--region" region to create the resources
"--version" print version of aci-flp-labs
"-h|--help" help info
```
