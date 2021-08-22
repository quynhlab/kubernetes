## Set up NFS Server

```
sudo yum install nfs-utils -y
sudo mkdir -p /mnt/k8sMount
whoami
sudo chown -R centos:centos /mnt/k8sMount/

sudo systemctl restart nfs-server

sudo vi /etc/exports

/mnt/k8sMount     <Worker1 IP>(rw,sync,no_root_squash,no_subtree_check)
/mnt/k8sMount     <Worker2 IP>(rw,sync,no_root_squash,no_subtree_check)

sudo exportfs -ra
```
## SSH to worker-nodes and follow the steps

```
sudo yum install nfs-utils -y

sudo mkdir -p /mnt/k8sWMount
sudo chown -R centos:centos /mnt/k8sWMount

sudo mount -t nfs 167.254.204.123:/mnt/k8sMount/ /mnt/k8sWMount/

df -h
```
 
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
