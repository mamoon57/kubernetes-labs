# 08 - Multi-container pod (main, sidecar) + initContainer

What: initContainer prepares something before app starts. Sidecar provides logging/auxiliary functions. Shared emptyDir demonstrates IPC/shared files.

Why: Common microservice pattern (logging, proxy, syncing).

How:
kubectl apply -f 08-multi-container-sidecar-init-deployment.yaml
