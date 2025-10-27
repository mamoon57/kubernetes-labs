# 14 - NetworkPolicy example

What: Deployment + NetworkPolicy that only allows ingress on port 80 from pods labeled `role=frontend`.

Why: Restrict traffic flow between pods for security.

How:

- Requires CNI plugin that enforces NetworkPolicy (Calico, Cilium, etc).
- kubectl apply -f 14-networkpolicy-deployment.yaml
