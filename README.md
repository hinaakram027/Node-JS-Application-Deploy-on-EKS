# Installation Instructions

## Step 1: Create EC2 Instance
    
## Step 2: Install ```AWS CLI```, ```Kubectl```, ```EKSCTL```:
- ```AWS CLI``` - AWS CLI is a unified tool for managing AWS services from the command line.

```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"

apt install unzip

unzip awscliv2.zip
```

- ```Kubectl``` - kubectl is the command-line tool used to interact with Kubernetes clusters.
```
curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.19.6/2021-01-05/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin
kubectl version --short --client
```    
- ```EKSCTL``` - eksctl is a command-line tool for managing Amazon EKS (Elastic Kubernetes Service) clusters.
```
curl -LO "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_Linux_amd64.tar.gz"

tar -xzf eksctl_Linux_amd64.tar.gz

sudo mv eksctl /usr/local/bin/

eksctl version
```

## Step 3: AWS Configure - 
        ○ Access Key - Your_Access_Key
        ○ Access Secret Key - Your Access_secret_key
        
## Step 4: Create EKS Cluster -
- Create Cluster:
```
eksctl create cluster --name jenkins-project --region us-east-2 --node-type t3.medium --nodes-min 1 --nodes-max 2
```

- Get Eks Cluster:
```
eksctl get cluster --name jenkins-project --region us-east-2
```
- Update Kubeconfig file for  kubectl:
```
aws eks update-kubeconfig --name jenkins-project --region us-east-2
```
## Step 5: Install Java -
```
sudo apt update

sudo apt install fontconfig openjdk-21-jre

java -version
```
## Step 6: Install Jenkins on Ubuntu -
```
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
```
```
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
```
```
sudo apt update
```
```
sudo apt install jenkins
```
<img width="1360" height="674" alt="jenkins pipeline" src="https://github.com/user-attachments/assets/3b5858ed-a05b-4d18-8ff1-aa1957000fe4" />


