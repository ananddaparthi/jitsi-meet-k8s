This will deploy each container to separate pod.

Create a namespace to deploy jitsi to:

`kubectl create namespace jitsi`

Add the secret with secret values (replace `...` with some random strings):

`kubectl create secret generic jitsi-config -n jitsi --from-literal=JICOFO_COMPONENT_SECRET=... --from-literal=JICOFO_AUTH_PASSWORD=... --from-literal=JVB_AUTH_PASSWORD=... `

Deploy the Prosody Pod:

`kubectl create -f prosody-deploy.yaml`

Deploy the Prosody Service and notedown the ClusterIP:

`kubectl create -f prosody-service.yaml`

Add PROSODY service LoadBalancer to JICOFO, JVB and WEB deployment files and deploy rest of the services.

`kubectl create -f prosody-deploy.yaml`
`kubectl create -f prosody-service.yaml`

`kubectl create -f jicofo-deploy.yaml`

`kubectl create -f web-deploy.yaml`
`kubectl create -f web-service.yaml`

You can use "https" service port to access jitsi.

TO DO:
`Scale JVB`
`Nginx ingress for web service`
