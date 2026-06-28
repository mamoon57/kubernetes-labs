# ReplicaSet examples

Different RS configs I tried while learning — labels, configmaps, volumes, probes, multi-container, affinity, resource limits.

| file | point |
|------|-------|
| 01-basic-replicaset.yaml | simplest rs |
| 02-replicaset-with-labels.yaml | selector labels |
| 03-replicaset-with-configmap.yaml | config from cm |
| 04-replicaset-with-volume.yaml | emptyDir / pvc |
| 05-replicaset-with-probes.yaml | liveness + readiness |
| 06-replicaset-multiple-containers.yaml | two containers one pod |
| 07-replicaset-node-affinity.yaml | schedule on specific nodes |
| 08-replicaset-resource-requests-limits.yaml | requests/limits |

`kubectl apply -f <file>`. In prod you'd use Deployments not bare RS but the concepts are the same.
