# 05 - NFS PV/PVC with Deployment

What: Static NFS PV + PVC + Deployment that mounts NFS (ReadWriteMany).

Why: Shared storage across pods/nodes (logs, shared datasets).

How:

1. Replace <NFS_SERVER> and path.
2. kubectl apply -f 05-nfs-pv-pvc-deployment.yaml
3. Check files written under /mnt/nfs in pods.

Note: For production use, secure NFS and consider dynamic provisioners or managed file services.
