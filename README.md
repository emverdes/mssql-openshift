# Deployment of a MSSQL Server Database on Openshift

These are the objects needed to deploy a MSSQL Database to Openshift.
This deployment have been tested in **[Openshift Developer Sandbox](https://console.redhat.com/openshift/sandbox)**.

You need a Red Hat Developer account to deploy this instance.

When you login to your Openshift Server, create a project, e.g. "*mssql*"
```
$ oc new-project mssql
```
Create a secret with SA Password
```
$ oc create secret generic mssql --from-literal=MSSQL_SA_PASSWORD="MyP4$$w0rd"
```
You can also use the secret object yaml file.
```
$ oc apply -f mssqlpasswd.yml
```
Create private volume claim.
```
$ oc apply -f sqlpvc.yml
```
Create deployment
```
$ oc apply -f sqldeployment.yml
```
Create NodePort service.
```
$ oc apply -f sqlservice.yml
```