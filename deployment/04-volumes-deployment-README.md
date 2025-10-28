# 04 - Volumes (emptyDir, hostPath, PVC)

What: Demonstrates emptyDir (ephemeral), hostPath (node-local), and PVC mount in same pod.

Why: Useful when pods need transient scratch, node logs, and persistent app data.

Warnings:

- hostPath has security implications  use carefully.
- Ensure StorageClass `standard` exists or change it.

How:
kubectl apply -f 04-volumes-deployment.yaml
