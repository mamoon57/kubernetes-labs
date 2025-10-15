# ReplicaSet mini project — multi-volume example

This single-file Kubernetes mini project demonstrates a ReplicaSet that uses:

- emptyDir (ephemeral pod-local storage)
- NFS (shared ReadWriteMany static PV + PVC)
- Cloud-backed PVC (dynamic provisioning via StorageClass)

It also shows running multiple containers in the same Pod, each using a different volume, and selecting specific node(s) for scheduling.

Quick notes (easy English)

- Namespace: replicaset-demo — the resources live here.
- StorageClass: `cloud-storage` — placeholder for cloud dynamic provisioning. Replace `provisioner` and `parameters` with your cloud's CSI driver (AWS/GCP/Azure).
- NFS PV: `nfs-pv` — static PV. Replace `<NFS_SERVER_IP_OR_HOSTNAME>` and `/export/path` with your NFS server details.
- PVCs:
  - `nfs-pvc` binds to the static NFS PV.
  - `cloud-pvc` requests a cloud-backed PV via StorageClass.
- ReplicaSet: `multi-vol-replicaset`
  - Runs 2 replicas (adjust `replicas` if needed).
  - Uses `nodeSelector: node-role.kubernetes.io/worker: "true"` to pick nodes. Change this to match your node labels (for example `kubernetes.io/hostname: my-node`).
  - 3 containers:
    - `web-emptydir` (nginx) — serves content from an emptyDir (ephemeral).
    - `worker-nfs` (busybox) — writes to NFS (shared storage).
    - `sidecar-cloud` (busybox) — writes to cloud-backed PVC.

How to use

1. Edit the YAML file:

   - Fill NFS server/path.
   - Update StorageClass provisioner if using the included StorageClass, or remove the StorageClass object and set `cloud-pvc` storageClassName to one that exists in your cluster.
   - Update nodeSelector to match a real node label in your cluster.
2. Apply the file:
   kubectl apply -f multi-vol-replicaset.yaml
3. Check resources:
   kubectl get ns,rs,pv,pvc -n replicaset-demo
   kubectl get pods -n replicaset-demo
4. Inspect a pod:
   POD=$(kubectl get pod -n replicaset-demo -l app=multi-vol -o jsonpath='{.items[0].metadata.name}')
   kubectl describe pod $POD -n replicaset-demo
   kubectl exec -it $POD -n replicaset-demo -- ls -la /mnt/nfs /data /usr/share/nginx/html
5. Logs:
   kubectl logs -n replicaset-demo $POD -c web-emptydir
   kubectl logs -n replicaset-demo $POD -c worker-nfs
   kubectl logs -n replicaset-demo $POD -c sidecar-cloud

Real-work tips

- Use proper StorageClass settings for your cloud provider (CSI drivers).
- For shared storage prefer ReadWriteMany-capable backends (NFS, CephFS, certain cloud file services).
- Use nodeAffinity if you need more complex scheduling (preferred/required).
- Add readiness/liveness probes, securityContext, resource limits and requests, and RBAC where appropriate.
- Do not keep plaintext secrets in manifests — use Secrets for credentials.

If you want, I can:

- adjust the manifest for a specific cloud provider (AWS/GCP/Azure),
- convert the static NFS PV to a dynamic provisioner (if your environment supports it),
- change nodeSelector to nodeAffinity with examples.

# ReplicaSet mini project — multi-volume example

This single-file Kubernetes mini project demonstrates a ReplicaSet that uses:
- emptyDir (ephemeral pod-local storage)
- NFS (shared ReadWriteMany static PV + PVC)
- Cloud-backed PVC (dynamic provisioning via StorageClass)

It also shows running multiple containers in the same Pod, each using a different volume, and selecting specific node(s) for scheduling.

Quick notes (easy English)
- Namespace: replicaset-demo — the resources live here.
- StorageClass: `cloud-storage` — placeholder for cloud dynamic provisioning. Replace `provisioner` and `parameters` with your cloud's CSI driver (AWS/GCP/Azure).
- NFS PV: `nfs-pv` — static PV. Replace `<NFS_SERVER_IP_OR_HOSTNAME>` and `/export/path` with your NFS server details.
- PVCs:
  - `nfs-pvc` binds to the static NFS PV.
  - `cloud-pvc` requests a cloud-backed PV via StorageClass.
- ReplicaSet: `multi-vol-replicaset`
  - Runs 2 replicas (adjust `replicas` if needed).
  - Uses `nodeSelector: node-role.kubernetes.io/worker: "true"` to pick nodes. Change this to match your node labels (for example `kubernetes.io/hostname: my-node`).
  - 3 containers:
    - `web-emptydir` (nginx) — serves content from an emptyDir (ephemeral).
    - `worker-nfs` (busybox) — writes to NFS (shared storage).
    - `sidecar-cloud` (busybox) — writes to cloud-backed PVC.

How to use
1. Edit the YAML file:
   - Fill NFS server/path.
   - Update StorageClass provisioner if using the included StorageClass, or remove the StorageClass object and set `cloud-pvc` storageClassName to one that exists in your cluster.
   - Update nodeSelector to match a real node label in your cluster.

2. Apply the file:
   kubectl apply -f multi-vol-replicaset.yaml

3. Check resources:
   kubectl get ns,rs,pv,pvc -n replicaset-demo
   kubectl get pods -n replicaset-demo

4. Inspect a pod:
   POD=$(kubectl get pod -n replicaset-demo -l app=multi-vol -o jsonpath='{.items[0].metadata.name}')
   kubectl describe pod $POD -n replicaset-demo
   kubectl exec -it $POD -n replicaset-demo -- ls -la /mnt/nfs /data /usr/share/nginx/html

5. Logs:
   kubectl logs -n replicaset-demo $POD -c web-emptydir
   kubectl logs -n replicaset-demo $POD -c worker-nfs
   kubectl logs -n replicaset-demo $POD -c sidecar-cloud
