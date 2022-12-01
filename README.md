# K8S-Website
 small K8S website project

- deployment 3 replicas + Website on nginx container
- service 

<details>
 <summary>Automation 🤖</summary>
 
```bash
{
    # Clone this repo to get the manifests
    git clone --depth 1 https://github.com/lgp00/K8S-Website.git

    ### DEPLOYMENT ###
    kubectl apply -f K8S-Website/Deployment/websiteDeployment.yaml

    ### SERVICE ###
    kubectl apply -f K8S-Website/Service/websiteService.yaml

    # Wait for pod to be running
    echo "Waiting up to 10 for website deploy to be running..."
    kubectl wait --for=condition=available deployment website --timeout=10s

    echo -e "\n\nAutomation complete! \n"
}
```
