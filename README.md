===
pv-pvc-nfs.yaml
---
Here's an example manifest file for creating a Persistent Volume and a Persistent Volume Claim that uses an NFS share as the storage backend. This will allow you to use the NFS share as a volume for pods in your Kubernetes cluster.

Here's what this manifest file does:

The PersistentVolume section creates a new Persistent Volume (PV) object named CORE-Kuber. The capacity field specifies the amount of storage to allocate, and the accessModes field specifies that the volume can be mounted by multiple pods simultaneously in read-write mode. The nfs field specifies the location of the NFS share, including the server hostname and the path to the share.

The PersistentVolumeClaim section creates a new Persistent Volume Claim (PVC) object named CORE-Kuber1. The accessModes field specifies that the PVC requires read-write access to the volume, and the resources field specifies the amount of storage to request. The selector field specifies that the PVC should be bound to a PV with the label type: nfs.

To use this manifest file, save it to a file (e.g. nfs-volume.yaml) and apply it to your Kubernetes cluster using the kubectl apply command:

kubectl apply -f nfs-volume.yaml

Once the PV and PVC are created, you can reference the PVC in your pod manifests to mount the NFS share as a volume.



===
mount-nfs2pod.yaml
---
In this example, the volumeMounts field specifies that the NFS volume should be mounted at the path /mnt/nfs within the container, and the volumes field specifies that the volume should be provided by the PVC named CORE-Kuber1.
