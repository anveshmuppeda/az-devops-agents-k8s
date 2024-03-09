# Installation of Sysbox  

Installation is easily done via a daemonset called "sysbox-deploy-k8s", which installs the Sysbox and CRI-O binaries onto the desired K8s nodes and performs all associated config.  

Steps:  

```bash
kubectl label nodes <node-name> sysbox-install=yes
kubectl apply -f https://raw.githubusercontent.com/nestybox/sysbox/master/sysbox-k8s-manifests/sysbox-install.yaml
```  
NOTE: the above step will restart the Kubelet on all nodes where Sysbox is being installed, causing all pods on the node to be stopped and re-created. Depending on the number of pods, this process can take anywhere from 30 secs to 2 minutes. Wait for this process to complete before proceeding.  

Once Sysbox installation completes, you can proceed to deploy pods with Sysbox as shown in section Pod Deployment.  

### Additional notes:  

Sysbox can be installed in all or some of the Kubernetes cluster worker nodes, according to your needs.  

Installing Sysbox on a node does not imply all pods on the node are deployed with Sysbox. You can choose which pods use Sysbox via the pod's spec (see Pod Deployment below). Pods that don't use Sysbox continue to use the default low-level runtime (i.e., the OCI runc) or any other runtime you choose.  

Pods deployed with Sysbox are managed via K8s just like any other pods; they can live side-by-side with non Sysbox pods and can communicate with them according to your K8s networking policy.  