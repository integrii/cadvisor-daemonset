# cadvisor-daemonset

This is a daemonset for cadvisor which deploys a [cAdvisor](https://github.com/google/cadvisor) web interface to every node.  Metrics for pods are updated by cAdvisor every second and are available programmatically via the [cadvisor API](https://github.com/google/cadvisor/blob/master/docs/api.md).  This is a much higher metric frequency that normally available in Kubernetes.

This kind of daemonset is a great way to get up to the second metrics off of their pods.

#### `externalTrafficPolicy: Local`

The service configuration is set to use `externalTrafficPolicy: Local`, which means that queries sent to the cluster service (`cadvisor.kube-system.svc.cluster.local`) **ARE NOT** routed to other nodes.

All queries from pods or from external sources are handled by the cAdvisor daemonset pod running on the node handling the request.  Also, because cAdvisor is not cluster-aware, this means that you can not query statistics for pods from sources outside of the node running the pod.

This kind of setup is designred for a sidecar that fetches its own pod's metrics rapidly (once a second).  All the service has to do in this case is to query the cluster service and it will always hit the cAdvisor daemonset on its own node!

#### Installation

`kubectl apply -f https://raw.githubusercontent.com/integrii/cadvisor-daemonset/master/cadvisor-daemonset.yaml`  


![cadvisor web](https://github.com/integrii/cadvisor-daemonset/blob/master/cadvisor-web.png?raw=true)

