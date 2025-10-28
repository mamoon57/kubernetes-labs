
# 02 - ConfigMap environment example

What: Uses a ConfigMap to inject environment variables into pods.

Why: Separate configuration from images; change config without rebuilding image.

How:

1. Edit values in ConfigMap if needed.
2. kubectl apply -f 02-configmap-env-deployment.yaml
3. kubectl logs -n deploy-examples deploy/configmap-deployment

Tip: Use configMapKeyRef to map single keys or mount as files with volumeMount.
