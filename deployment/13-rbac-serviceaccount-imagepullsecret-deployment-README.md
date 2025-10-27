# 13 - ServiceAccount, imagePullSecret, and RBAC

What: Use ServiceAccount for pods, imagePullSecrets for private registries, role+binding to grant limited permissions.

Why: Least privilege and private image access.

How:

1. Create image pull secret with kubectl create secret docker-registry.
2. kubectl apply -f 13-rbac-serviceaccount-imagepullsecret-deployment.yaml
