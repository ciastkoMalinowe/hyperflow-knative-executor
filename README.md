# hyperflow-knative-executor
Hyperflow (https://github.com/hyperflow-wms/hyperflow) executor running on Knative. Exemplary image executes Montage (https://github.com/hyperflow-wms/montage2-workflow).

### Setup
To start a cluster with Knative setup your credentials (it may vary depending on a platform) and run _create_cluster.sh_ script. Once ready, configure DNS with  
```kubectl patch configmap config-domain --namespace knative-serving --patch '{"data": {"example.com": null, "<your-external-ip>.xip.io": ""}}'```.  
You can fetch external ip with `kubectl get svc istio-ingressgateway -n istio-system`.  

Deploy executor with:  
`kubectl apply --filename service.yaml`.  
You can use  `kubectl logs <pod-name> user-container` to obtain logs
and `kubectl get pods` to list all pods.

Service URL can be found using `kubectl get ksvc hyperflow-executor`.
