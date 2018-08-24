# Kubernetes (K8s) and Sensu: Better Together :) 

# Cluster Startup

Similar patterns across any etcd-based backend (Sensu, K8s, etc)

* Needs to be ordered (one proposed leader, others join, they form quorum)
  * Can cause issues when automated as the first one to launch might not be the proposed leader
* etcd-operator in K8s can help manage all of that

* Proposed solution: Make Sensu aware that it is running within K8s
  * That way it can hit K8s APIs to see if I'm the first to boot up, for example
  * That's how Prometheus works within K8s

# How to monitor Pods?

* Typical model: sidecars within the Pod
* Or do we have Sensu get the Pod endpoints and just monitor those?
* Have Sensu run as the readiness probe
  * Can to more robust things than just checking if a port is up

# Monitoring Pods Alongside Bare Metal Powering Them

* Question: Separate backends for Pod(s) and baremetal?
* Answer: Probably not, as Sensu 2.0 has environments and orgs to keep those separate, yet view together if needed
