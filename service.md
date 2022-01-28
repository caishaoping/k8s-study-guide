# Overview
  - Types of services: internal, external, a headless service ( no fixed IP nor load-balancing)
  - Usages: load-banlancing, matching a label query, the possible session affinity via IP
  - Keys: connect Pods together, provide access outside of the cluster.
  - Label: labels associated with Pods can be used by Service to determine route traffic to which Pods.  

# Expose an application
  - create deployment
    
      vagrant@master-1:~$ kubectl create deployment nginx --image=nginx
      deployment.apps/nginx created
    
  - Expose service
    
      vagrant@master-1:~$ kubectl expose deployment/nginx --port=80 --type=NodePort
      service/nginx exposed
      vagrant@master-1:~$ kubectl get svc
      NAME         TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE
      kubernetes   ClusterIP   10.96.0.1        <none>        443/TCP        41d
      nginx        NodePort    10.109.142.213   <none>        80:31942/TCP   4s
  - View service
      
      vagrant@master-1:~$ kubectl get svc nginx -o yaml
      apiVersion: v1
      kind: Service
      metadata:
        creationTimestamp: "2022-01-28T03:05:24Z"
        labels:
          app: nginx
        name: nginx
        namespace: default
        resourceVersion: "127299"
        uid: 91e380c1-1625-4b94-ad99-2ddf1d6754dd
      spec:
        clusterIP: 10.109.142.213
        clusterIPs:
        - 10.109.142.213
        externalTrafficPolicy: Cluster
        internalTrafficPolicy: Cluster
        ipFamilies:
        - IPv4
        ipFamilyPolicy: SingleStack
        ports:
        - nodePort: 31942
          port: 80
          protocol: TCP
          targetPort: 80
        selector:
          app: nginx
        sessionAffinity: None
        type: NodePort
      status:
        loadBalancer: {}
      vagrant@master-1:~$


# Service types
  - ClusterIP: default and only provides access internally
  - NodePort: great for debugging
  - LoadBalancer: pass requests to a cloud provider
  - ExternalName: newer service, no selectors, no defined ports, no defined endpoints. Redirection at DNS level. 

# Start a local proxy
  - kubectl proxy


# Use the cluster DNS
## CoreDNS
  - default as of v1.13
  - great flexibility
  - kube-dns
  - in-tree plugins provide common functionality
  - common plugins provides metrics for consumption by Prometheus, error logging, health reporting, and TLS, to configure certificates        for TLS and gRPC servers
 ## Verify DNS setup works properly
  1. run a pod with shell and network tools in the cluster
  2. create a service to connect to the pod
  3. exec in it to do a DNS lookup
## Troubleshooting of DNS
   - nslookup
   - dig
   - nc
   - wireshaark
   - check /etc/resolv.conf file
   - 
    
    



