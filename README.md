# Kubernetes Manifests
Stores manifests for OneSky Kubernetes cluster

# Kubernetes Glossaries
- `Pod`
  - 1 or more containers that must live and die together on the same host
  - Shares a network (can call each other through localhost:port)
  - E.g.
    - Single container pod
      - Import
    - Multiple container pod
      - Apache + Datadog agent for Apache

- `Replication Controller`
  - Ensure a certain number of `Pods` is running at all times

- `Service`
  - TCP / UDP Proxy to `Pod`
  - Can contain 1 or more type of `Pods`
  - Select by `Label`


# Best Practices
- ***If*** a `Service` is needed, ***always*** create the `Service` before creating `Pod` or `Replication Controller`
  - Allow others to discover your app even if it is down
  - Once `Pod` is available others can immediately connect to your app
  - Also allow self discovering infra like Cassandra, Redis, etc

# Config files
- use tools/templater.sh to generate real kubernetes config yml files
- {{ENV}} - the namespace of prod, stag, dev environment
  - the service address (service.{{ENV}}.svc.cluster.local) will follow this convertion 
