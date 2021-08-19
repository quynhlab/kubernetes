## Follow the steps for NFS provision:
## Run the RBAC policy on k8s cluster:
```
kubectl apply -f rbac.yaml
```
## Create a Storage Class called "managed-nfs-storage" as default:
```
kubectl apply -f default-sc.yaml

kubectl get storageclass
```
## Modify the NFS Server IP Address and NFS PATH and run below cmd:
```
kubectl apply -f deployment.yaml
kubectl get pod
```
## Test dynamic pv are creating or not
```
kubectl apply -f pvc.yaml
```
