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
    echo " you can now access the website at http://localhost:(nodeport/TCP)" 
    kubectl describe svc website |grep nodeport -i | grep /TCP

    echo -e "\n\nAutomation complete! \n"

    echo -e "to find the home local network ip address of the node, run the following command: \n Linux \n ifconfig | grep 'inet' | grep -v 127.0.0.1 \n Windows \n ipconfig \n"
}

```
