# cadvisor-daemonset

This is a daemonset for cadvisor which exposes a web interface every node.  Metrics are updated every second and are available progamatically via the [cadvisor API](https://github.com/google/cadvisor/blob/master/docs/api.md).

To apply, just use `kubectl apply -f https://raw.githubusercontent.com/integrii/cadvisor-daemonset/master/cadvisor-daemonset.yaml` or download the YAML and apply it yourself.

![cadvisor web](https://github.com/integrii/cadvisor-daemonset/blob/master/cadvisor-web.png?raw=true)

