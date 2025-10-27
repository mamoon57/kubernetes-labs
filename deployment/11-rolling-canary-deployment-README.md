# 11 - Rolling + Canary pattern

What: Stable (blue) deployment + small canary; Service routes to both by `app:web` selector.

Why: Test a new version on a small percentage of traffic before full rollout.

How:

1. Apply file.
2. Monitor metrics and logs for canary.
3. If canary OK, scale stable down / update stable to new image or promote canary.

Tip: Use Ingress/service mesh for more precise traffic splitting.
