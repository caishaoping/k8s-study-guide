# Intro
## Pod, container, and Volume
  1. A Pod can be associated to one or more volumes;
  2. The same volume can be associated to multipe containers in the same Pod;
  3. The same volume can be associated to multiple Pods;
## Pods' access mode
  1. ReadWriteOnce, RW by a single node
  2. ReadOnlyMany,  RO by multiple nodes
  3. ReadWriteMany, RW by many nodes.

# Spec
    volumeMounts:  
    \- mountPath: /path  
       name: path-volume  
    volumes:  
    \- name: volume-name  
             emptyDir: {}  
          
# Volume Types
## Cloud volumes
    1. GCEpersistentDisk
    1. awsElasticBlockStore (EBS)
    1. azureDisk, azureFile
    
## Local volumes
    1. emptyDir, erased as the Pod dies
    1. hostPath
    
## Network volumes for multiple readers scenarios
    1. NFS (Netowrk File System)
    1. iSCSI (Internet Small Computer System Interfaces)

## Cluster volumes for multiple writer needs
    1. rbd for block storage
    1. CephFS and GlusterFS

## Others
    1. csi
    1. gitRepo
    1. local
    1. secret
    1. vsphereVolume
    1. etc

# Shared Volumes
# PV and PVC (Persistent Volumes and Claims)
    - PV: Storage abstraction, can retain data longer than Pods exist
    - PVC: defined in Pods to associalte with PV
    - StorageClass: define backend storage, type and size
## Persistent Storage phases
    - Provision
    - Bind
    - Use
    - Release
    - Reclaim:  Retain, Delete, and Recycle(to be deprecated)
    
## PV (Persistent Volume)
    - kind: PersistentVolume
    - Spec: capacity, accessmodes, hostpath
    - not a namespace object

## PVC (Persistent Volume Claim)
  ### manifest a claim
   - kind: PersistentVolumeClaim
    - spec: accessModes, resources
    - a namespace object
  ### pods to use the claim
    - volumes:  name, persistenVolumeClaim
    
# Dynamic Provisioning
    - No need to create volumes in the first place, instead, request storage from an exterior, pre-configured source.
    - kind: StorageClass
    - AWS and GCE are common choices for dynamic storage, other options are: Ceph cluster, iSCSI
    - apiVersion: storage.k8s.io/v1
    - provisioner: kubernetes.io/gce-pd
    
# Rook for Storage Orchestration
    - a project allows orchestration of storage using multiple storage providers
    - uses custom resource definition (CRD) and a custom operatior to provision storage
    - supported storage providers: Ceph, Cassandra, Network File System (NFS)
    
# Secrets
    - base64-encoded(default) or encrypted via Secret API resource
    - kubectl commands to create or get or delete secrets,  create/get/delete
    - EncryptionConfigration with key and proper identity
    - flag of --encryption-provider-config 

## Using Secrets via Environment Variables
    - yaml snippet
    ...
    spec:
      containers:
      - image: mysql:5.5
        name: dbpod
        env:
        - name: MYSQL_ROOT_PASSWORD
          valueFrom:
              secretKeyRef:
                  name: mysql
                  key: password 
      - environment variables stored in tempfs, a temporay memory-based file systems          
## Mounting Secrets as Volumes
    - yaml snippet
    ...
    spec:
      containers:
      - image: busybox
        command:
          - sleep
          - "3600"
        volumeMounts:
        - mountPath: /mysqlpassword
          name: mysql
      name: busy
    volumes:
      - name: mysql
          secret:
              secretName: mysql
    - to view the secret: kubectl exec -ti busybox -- cat /mysqlpassword/password

# ConfigMaps

## Portable Data

## Using ConfigMaps


