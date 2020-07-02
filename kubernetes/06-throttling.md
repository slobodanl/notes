_Written by: Reza Shams Amiri_
# Throttling

## CPU units ([ref][ACRTCAPK])
The CPU resource is measured in CPU units. One CPU, in Kubernetes, is equivalent to:

1 AWS vCPU
1 GCP Core
1 Azure vCore

Fractional values are allowed. A Container that requests 0.5 CPU is guaranteed half as much CPU as a Container that requests 1 CPU. You can use the suffix m to mean milli. For example 100m CPU, 100 milliCPU, and 0.1 CPU are all the same. Precision finer than 1m is not allowed.

## References
1. [Assign CPU Resources to Containers and Pods | Kubernetes][ACRTCAPK]

* * *
Creation date: _2020-07-02_

[ACRTCAPK]: https://kubernetes.io/docs/tasks/configure-pod-container/assign-cpu-resource/