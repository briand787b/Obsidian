# Kubectl
Kubectl always talks to the API server, never the resources directly

## Viewing Objects
Minimal details: `kubectl get <object-type>`
More details: `kubectl get -o wide <object-tpe>`
Full description: `kubectl describe <object-type> <object-id>`