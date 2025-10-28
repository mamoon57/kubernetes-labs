# 09 - Node affinity and tolerations

What: Forces pods on nodes labeled as workers and tolerates taints with key `dedicated=batch`.

Why: Place workloads on specific node pools (e.g., GPU, spot, dedicated nodes).

How:

- Ensure nodes have `node-role.kubernetes.io/worker=true` label or change to match your labels.
- kubectl apply -f 09-node-affinity-tolerations-deployment.yaml
