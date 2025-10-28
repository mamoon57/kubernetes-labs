# 03 - Secret environment example

What: Shows storing credentials in Secret and injecting as env vars.

Why: Keep credentials out of YAML and images.

How:

1. Replace stringData with safer creation method: kubectl create secret generic db-credentials --from-literal=DB_USER=... --from-literal=DB_PASS=...
2. kubectl apply -f 03-secret-env-deployment.yaml
3. Inspect secrets carefully; avoid committing real secrets to git.
