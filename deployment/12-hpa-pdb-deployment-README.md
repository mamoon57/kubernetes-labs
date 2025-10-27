# 12 - HPA and PodDisruptionBudget

What: Horizontal Pod Autoscaler (HPA) + PDB for `autoscale-app`.

Why: HPA auto-scales based on CPU; PDB prevents too many pods being evicted during maintenance.

How:

- Ensure metrics-server is installed for CPU-based HPA.
- kubectl apply -f 12-hpa-pdb-deployment.yaml
- kubectl get hpa -n deploy-examples
