# udacity-project4
Microservices project

Attempt #1. AWS Cloud 9
  Create environment, t2.micro (1 GiB RAM + 1 vCPU), Amazon Linux
  git clone
  Create python env
  make install
  Docker already installed
    Docker version 19.03.6-ce, build 369ce74
  Install hadolint via docker
    docker run --rm -i hadolint/hadolint < Dockerfile
    Replaced hadolint line in Makefile with the above
  make lint errors on app.py
    https://pastebin.pl/view/fa8b3925
  Install kubectl
    curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
    chmod +x ./kubectl
    sudo mv ./kubectl /usr/local/bin/kubectl
    kubectl version --client
      Client Version: version.Info{Major:"1", Minor:"19", GitVersion:"v1.19.0", GitCommit:"e19964183377d0ec2052d1f1fa930c4d7575bd50", GitTreeState:"clean", BuildDate:"2020-08-26T14:30:33Z", GoVersion:"go1.15", Compiler:"gc", Platform:"linux/amd64"}
  Install minikube
    curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
    chmod +x minikube
    sudo mkdir -p /usr/local/bin/
    sudo install minikube /usr/local/bin/
  Start minikube
    minikube start --driver=docker
    Fails, not enough vCPU's
      https://pastebin.pl/view/b3d73d98
      
Attempt #2. AWS Cloud 9
  Create environment, m5.large (8 GiB RAM + 2 vCPU), Amazon Linux
  git clone
  Create python env
  make install
  Docker already installed
    Docker version 19.03.6-ce, build 369ce74
  Install hadolint via docker
    docker run --rm -i hadolint/hadolint < Dockerfile
    Replaced hadolint line in Makefile with the above
  make lint errors on app.py
    https://pastebin.pl/view/fa8b3925
  Install kubectl
    curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
    chmod +x ./kubectl
    sudo mv ./kubectl /usr/local/bin/kubectl
    kubectl version --client
      Client Version: version.Info{Major:"1", Minor:"19", GitVersion:"v1.19.0", GitCommit:"e19964183377d0ec2052d1f1fa930c4d7575bd50", GitTreeState:"clean", BuildDate:"2020-08-26T14:30:33Z", GoVersion:"go1.15", Compiler:"gc", Platform:"linux/amd64"}
  Install minikube
    curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
    chmod +x minikube
    sudo mkdir -p /usr/local/bin/
    sudo install minikube /usr/local/bin/
  Start minikube
    minikube start --driver=docker
    Fails, "no space left on device"
      https://pastebin.pl/view/38e1d026
    Possible follow-up action > increase nvme partition size > https://stackoverflow.com/questions/52508038/how-to-increase-aws-ebs-nvme-size
      (.devops) ec2-user:~/environment/DevOps_Microservices/project-ml-microservice-kubernetes (master) $ sudo growpart /dev/nvme0n1 1
      NOCHANGE: disk=/dev/nvme0n1 partition=1: size=20967390, it cannot be grown

Attempt #3. AWS Cloud 9
  Create environment, m5.large (8 GiB RAM + 2 vCPU), Ubuntu Server 18.04 LTS
  git clone
  Create python env
  make install
  Docker already installed
    Docker version 19.03.12, build 48a66213fe
  Install hadolint via docker
    docker run --rm -i hadolint/hadolint < Dockerfile
    Replaced hadolint line in Makefile with the above
  make lint errors on app.py
    https://pastebin.pl/view/fa8b3925
  Install kubectl
    curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
    chmod +x ./kubectl
    sudo mv ./kubectl /usr/local/bin/kubectl
    kubectl version --client
      Client Version: version.Info{Major:"1", Minor:"19", GitVersion:"v1.19.0", GitCommit:"e19964183377d0ec2052d1f1fa930c4d7575bd50", GitTreeState:"clean", BuildDate:"2020-08-26T14:30:33Z", GoVersion:"go1.15", Compiler:"gc", Platform:"linux/amd64"}
  Install minikube
    curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
    chmod +x minikube
    sudo mkdir -p /usr/local/bin/
    sudo install minikube /usr/local/bin/
  Start minikube
    minikube start --driver=docker
    Fails, "no space left on device"
      https://pastebin.pl/view/69d885c4
