# Flusso con creazione namespace e checkout git automatici

`helm plugin install https://github.com/thomastaylor312/helm-namespace`  

`helm plugin install https://github.com/aslafy-z/helm-git.git`  

`helm repo add mycharts git+https://github.com/ccangemi-redhat/demo-deploy@/`  

`helm namespace install example-app mycharts/example-app -n demo-deploy`  


# Flusso standard

Creazione namespace:  
`oc new-project <namespace>`

`oc project <namespace>`  

Checkout git in locale.  

`helm install example-app example-app/ -n demo-deploy`