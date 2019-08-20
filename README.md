export KUBECONFIG=kubeconfig.txt

### before connecting CVO Workspace with K8s Cluster

kubectl get sc

kubectl get pv

kubectl get pods --all-namespaces

### After K8S with connected with CVO in OCCM

mac$ kubectl get sc

mac$ kubectl get pv

mac$ kubectl create -f NKSDemoPVCforNAS.yaml

mac$ kubectl get pvc

mac$ kubectl create -f NKSDemo_mynginx.yaml
deployment.apps "my-nginx” created

mac$ kubectl get pods

mac$ kubectl expose deployment my-nginx --type=LoadBalancer --name=my-service
service "my-service” exposed

mac$ kubectl describe service my-service

mac$ kubectl get pods


mac$ kubectl exec -it my-nginx-b7b56756c-qdrhr sh
# cd /usr/share/nginx/html

# mount | grep trident
172.23.1.254:/netyrsrzfh_trident_default_persistent_volume_claim_nas_8b126 on /usr/share/nginx/html type nfs4 (rw,relatime,vers=4.1,rsize=65536,wsize=65536,namlen=255,hard,proto=tcp,timeo=600,retrans=2,sec=sys,clientaddr=172.23.1.226,local_lock=none,addr=172.23.1.254)

# echo "<h1>the quick brown fox jumps over the lazy dog on host $HOSTNAME </h1>" > index.html

mac$ kubectl get pods
