# 10 - Resource requests and limits

What: Shows CPU/memory requests and limits.

Why: Helps scheduler place pods and prevents noisy neighbors.

How:

- Tune requests/limits for your app.
- Consider cluster LimitRanges and QoS classes.
- kubectl apply -f 10-resources-limits-deployment.yaml
