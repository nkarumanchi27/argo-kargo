# argo-kargo
## Create a gke cluster with minimal cost
```
gcloud beta container --project "intense-elysium-446714-g4" clusters create "cluster-1" --zone "us-central1-c" --tier "standard" --no-enable-basic-auth --cluster-version "1.31.4-gke.1183000" --release-channel "regular" --machine-type "e2-small" --image-type "COS_CONTAINERD" --disk-type "pd-balanced" --disk-size "50" --metadata disable-legacy-endpoints=true --scopes "https://www.googleapis.com/auth/devstorage.read_only","https://www.googleapis.com/auth/logging.write","https://www.googleapis.com/auth/monitoring","https://www.googleapis.com/auth/servicecontrol","https://www.googleapis.com/auth/service.management.readonly","https://www.googleapis.com/auth/trace.append" --num-nodes "2" --logging=SYSTEM,WORKLOAD --monitoring=SYSTEM,STORAGE,POD,DEPLOYMENT,STATEFULSET,DAEMONSET,HPA,CADVISOR,KUBELET --enable-ip-alias --network "projects/intense-elysium-446714-g4/global/networks/default" --subnetwork "projects/intense-elysium-446714-g4/regions/us-central1/subnetworks/default" --no-enable-intra-node-visibility --default-max-pods-per-node "110" --enable-ip-access --security-posture=standard --workload-vulnerability-scanning=disabled --no-enable-master-authorized-networks --no-enable-google-cloud-access --addons HorizontalPodAutoscaling,HttpLoadBalancing,GcePersistentDiskCsiDriver --enable-autoupgrade --enable-autorepair --max-surge-upgrade 1 --max-unavailable-upgrade 0 --binauthz-evaluation-mode=DISABLED --enable-managed-prometheus --enable-shielded-nodes --node-locations "us-central1-c"
```

## install argocd
https://github.com/argoproj/argo-helm/tree/main/charts/argo-cd
https://github.com/argoproj/argo-cd
https://github.com/argoproj/argo-cd
https://www.arthurkoziel.com/setting-up-argocd-with-helm/

kubectl port-forward svc/argo-cd-argocd-server 8080:443

## Install grafana
https://grafana.com/docs/grafana/latest/setup-grafana/installation/helm/
https://github.com/grafana/helm-charts/tree/main/charts/grafana

## create a argocd application for a simple webapplication.
### create the application helm chart and install it through helm to test it first
'''
helm install my-nginx ./my-nginx --namespace nginx --create-namespace
helm upgrade my-nginx my-nginx -n nginx
helm history my-nginx -n nginx
helm package my-nginx


'''
### create an artifact out of te application helm chart and upload it to artifact hub
### create an argocd application to install the chart into gke

## install kargo
## tutorial on kargo

