# Welcome to Azure DevOps Self-Hosted Agents Helm Chart  

## Install Helm chart  
Use the below command to install the respective agents in kuberenetes cluster.  
```bash
helm install az-selfhosted-agents ./az-selfhosted-agents \
    --set windows.enabled=false \
    --set linux.enabled=false \
    --set dind.enabled=true \
    --create-namespace -n az-devops
```  

## Uninstall the Helm chart
Use the below command to uninstall the respective agents in kuberenetes cluster.  
```bash
helm uninstall az-selfhosted-agents -n az-devops
```  