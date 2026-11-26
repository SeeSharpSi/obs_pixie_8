---
subject: openshift
tags:
 - gtri
 - openshift
tech:
 - openshift
type: reference
topic: tech
---

# todo
- [ ] look into `= this.subject`
- [ ] look into certs
# links
* [Main Site](https://www.redhat.com/en/technologies/cloud-computing/openshift)
* [Getting Started](https://access.redhat.com/documentation/en-us/red_hat_container_development_kit/2.3/html/getting_started_guide/index)
* [ISD Console](https://console-openshift-console.apps.isdosdev.isdos.core.gtri.org/)
* [Using OpenShift Container Platform](https://access.redhat.com/documentation/en-us/red_hat_container_development_kit/2.3/html/getting_started_guide/using_openshift_container_platform#doc-wrapper)
* [Docker Images](https://catalog.redhat.com/software/containers/search)
* [Create App w/ GUI](https://access.redhat.com/documentation/en-us/openshift_container_platform/4.10/html/getting_started/openshift-web-console)

# certs

# cli commands
taken from [manual section 7.2](https://access.redhat.com/documentation/en-us/red_hat_container_development_kit/2.3/html/getting_started_guide/using_openshift_container_platform#working_with_openshift_templates)
`oc get templates -n openshift`
`oc get templates -o json -n openshift [name] > [name].json`
`oc create -f [name].json -n [namespace]` 
	you must change the value of `namespace` in the .json file
`oc create -f [name].json`
`oc process --parameters [name]`
`oc process [name] -v SOURCE_REPOSITORY_URL=[github_url] | oc create -f -`
`oc help`