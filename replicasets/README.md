# ReplicaSet Examples

This directory contains various examples of Kubernetes ReplicaSets, each demonstrating different features and configurations. Below is a brief overview of each example:

## 01-basic-replicaset.yaml

This example defines a basic ReplicaSet that ensures a specified number of pod replicas are running at all times. It includes the pod template specification.

## 02-replicaset-with-labels.yaml

This ReplicaSet example includes labels for the pods, allowing for easier management and selection of pods. Labels are key-value pairs that can be used to organize and select resources.

## 03-replicaset-with-configmap.yaml

This example demonstrates how to utilize a ConfigMap to manage configuration data for the pods. ConfigMaps allow you to decouple configuration artifacts from image content to keep containerized applications portable.

## 04-replicaset-with-volume.yaml

This ReplicaSet mounts a volume to the pods, allowing for persistent storage. This is useful for applications that require data persistence beyond the lifecycle of individual pods.

## 05-replicaset-with-probes.yaml

This example includes readiness and liveness probes to monitor the health of the pods. Probes help ensure that your application is running smoothly and can automatically restart unhealthy pods.

## 06-replicaset-multiple-containers.yaml

This ReplicaSet runs multiple containers within each pod, showcasing how to manage multi-container applications. This is useful for applications that require tightly coupled components to run together.

## 07-replicaset-node-affinity.yaml

This example specifies node affinity rules, allowing pods to be scheduled on specific nodes based on labels. Node affinity is a way to constrain which nodes your pods are eligible to be scheduled based on labels on nodes.

## 08-replicaset-resource-requests-limits.yaml

This ReplicaSet specifies resource requests and limits for the pods, ensuring efficient resource allocation. This helps Kubernetes manage resources effectively and ensures that your applications have the necessary resources to run.

Each example can be applied to your Kubernetes cluster using `kubectl apply -f <filename>.yaml`. Be sure to review the individual README files for more detailed instructions and explanations for each specific example.
