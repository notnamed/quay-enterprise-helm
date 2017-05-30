# quay-enterprise-helm
A Helm chart to deploy Quay Enterprise; designed for use with Tectonic

## Setup

1. Grab your pull token in JSON form from https://account.coreos.com/ and save it to `config.json`
2. Deploy the Helm chart:

`helm install ./quay-enterprise-helm --set "secret=$(cat ./config.json | base64 -i -w 0)"`

3. Monitor the status of your deployment (the Quay image will take about 5 minutes to pull):

`kubectl get po,svc,rs,storageclasses,pv,pvc --namespace quay-enterprise`

4. If deploying on AWS, grab your ELB hostname using:

`kubectl describe svc quay-enterprise --namespace quay-enterprise | grep Ingress`

5. Navigate to your new service and configure Quay per the setup docs: http://coreos.com/quay-enterprise/docs/latest/tectonic/
