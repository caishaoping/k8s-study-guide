1. Kubernetes networking: 

Containers within a Pod use networking to communicate via loopback,  all containers in a Pod share the same IP assigned to Pod
Different Pods communicate via Cluster netowking, no NAT required
Application running in a Pod can be reachable from outside your cluster via Service recoures,  exposing application to the service
Services can be used for consumption inside your cluster throubh publishing services

