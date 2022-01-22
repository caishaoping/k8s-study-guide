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
# PVC (Persistent Volumes and Claims)
# PV (Persistent Volume)
# Dynamic Provisioning
# Rook for Storage Orchestration
# Secrets
## Using Secrets via Environment Variables
## Mounting Secrets as Volumes
# ConfigMaps
## Portable Data
## Using ConfigMaps


