# 06 - Cloud-backed PVC via StorageClass

What: StorageClass + PVC that dynamically provisions cloud block storage; Deployment mounts it.

Why: Persistent storage for databases or stateful apps.

How:

- Replace provisioner with your cloud CSI driver.
- kubectl apply -f 06-cloud-pvc-storageclass-deployment.yaml

Tip: Use ReadWriteMany only if your storage supports it.
