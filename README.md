# cadvisor-daemonset

This is a daemonset for cadvisor which exposes a [cAdvisor](https://github.com/google/cadvisor) web interface on every node on port 8080.  You can change the port to anything you like in the kubernetes yaml.  Metrics are updated by cAdvisor every second and are available programmatically via the [cadvisor API](https://github.com/google/cadvisor/blob/master/docs/api.md).

To apply, just use `kubectl apply -f https://raw.githubusercontent.com/integrii/cadvisor-daemonset/master/cadvisor-daemonset.yaml` or you can download the YAML and apply it yourself with `kubectl apply -f`.

This kind of daemonset is a great way for anyone to get up to the second metrics off of their pods.

![cadvisor web](https://github.com/integrii/cadvisor-daemonset/blob/master/cadvisor-web.png?raw=true)

