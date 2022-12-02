# K8S-Website

small K8S website project

-  deployment (3 replicas + Website on nginx container)
-  service

<details>
 <summary>You will need 🗒️</summary>

### [x] KUBECTL

The Kubernetes command-line tool, kubectl, allows you to run commands against Kubernetes clusters. You can use kubectl to deploy applications, inspect and manage cluster resources, and view logs. For more information including a complete list of kubectl operations, see the kubectl reference documentation.

kubectl is installable on a variety of Linux platforms, macOS and Windows. Find your preferred operating system below.

-  [Install kubectl on Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux)
-  [Install kubectl on macOS](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos)
-  [Install kubectl on Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl-windows)

### [x] DOCKER

Docker is an open platform for developing, shipping, and running applications.

-  [Install Docker on Linux](https://docs.docker.com/desktop/install/linux-install/)
-  [Install Docker on macOS](https://docs.docker.com/desktop/install/mac-install/)
-  [Install Docker on Windows](https://docs.docker.com/desktop/install/windows-install/)

Quick Docker setup:

1. Click on the setting icon in DOCKER <img width="44" alt="Screenshot 2022-12-02 at 14 19 57" src="https://user-images.githubusercontent.com/94550034/205302086-76b6c0fa-6b8f-4405-9768-d8b6c1cf0cf3.png">
2. Click on KUBERNETES category on the left <img width="162" alt="Screenshot 2022-12-02 at 14 20 19" src="https://user-images.githubusercontent.com/94550034/205302361-7434b0da-1df6-4e6c-b672-39a08248cf63.png">
3. Activate KUBERNETES <img width="446" alt="Screenshot 2022-12-02 at 14 20 28" src="https://user-images.githubusercontent.com/94550034/205302450-7246009a-06ea-40df-8673-f0080b6f1fad.png">
 

</details>
<details>

 <summary>Automation 🤖 copy & paste easy deploy 👍</summary>

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

</detils>
