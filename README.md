# Helm deploy

## Automatic namespace creation and git checkout workflow

### Setup:
`helm plugin install https://gitlab.consulting.redhat.com/ccangemi/helm-namespace`  

`helm plugin install https://gitlab.consulting.redhat.com/ccangemi/helm-git`  

`helm repo add mycharts git+https://github.com/ccangemi-redhat/demo-deploy@infrastracture`  

### Run

`helm namespace install example-app mycharts/example-app -n <namespace>`  

## Manual flow

Namespace creation:  
`oc new-project <namespace>`

Git checkout.  

`helm install example-app example-app/ -n <namespace>`

# Binary build

## Prerequisite

* maven >= 3.6
* [oc client](https://docs.openshift.com/container-platform/4.4/cli_reference/openshift_cli/getting-started-cli.html)
## Build the app

From the project root

```cd web-app```

Build the app:

```mvn clean package -Dappversion=1.0```

Then go back to the project root

# Deploy the app

Make sure you're in the project:  

```oc project demo-deploy```

Start the binary build:

```oc start-build helloapp --from-file target/ROOT.war --follow;```

Wait for the pod with the app to be available (```oc get pods```).

Now from the route created by OpenShift you can reach the application deployed (the application is published on the root path)
