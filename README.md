# Weather App - Deployment Guide

This guide provides step-by-step instructions to set up and deploy the Weather App using Vagrant, VirtualBox, Ansible, and Jenkins.
## Visulaiztion 
![Image](https://github.com/user-attachments/assets/2fa87466-645d-4056-84d4-31c65b34fbb7)

## Prerequisites

Ensure you have the following installed on your machine:
- [Vagrant](https://www.vagrantup.com/downloads)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
- [Jenkins](https://www.jenkins.io/download/)
- GitHub account with repository access

## Installation and Setup

### Step 1: Install Vagrant
Download and install Vagrant from [here](https://www.vagrantup.com/downloads).

### Step 2: Install VirtualBox
Download and install VirtualBox from [here](https://www.virtualbox.org/wiki/Downloads).

### Step 3: Get the Vagrantfile
Clone the repository and navigate to the directory:
```sh
 git clone https://github.com/youssefmoghazy/Weather_App.git
 cd Weather_App
```
Ensure the `Vagrantfile` is present in the directory.

### Step 4: Install Ansible
Install Ansible on your local machine:
```sh
 sudo apt update && sudo apt install ansible -y  # Ubuntu/Debian
```

### Step 5: Update Inventory File
Modify the `inventory` file to include the correct paths to the private keys:
```plaintext
./.vagrant/machines/m02/virtualbox/private_key
./.vagrant/machines/m01/virtualbox/private_key
```

### Step 6: Verify Connection
Run the following command to test the connection to the VMs:
```sh
 ansible all -m ping -i inventory
```

### Step 7: Clone Repository & Copy Private Keys
Clone the repository again and place the private key files in the same directory.
```sh
 git clone https://github.com/youssefmoghazy/Weather_App.git
 cp <private_key_files_paths> Weather_App/privatefiles
```

### Step 8: Push to GitHub
Push the updated repo to GitHub:
```sh
 git add .
 git commit -m "Added private keys for Jenkins"
 git push origin main
```

### Step 9: Configure Jenkins
1. Set up Jenkins and install necessary plugins (Git, Ansible, Pipeline, etc.).
2. Add GitHub credentials to Jenkins.
3. Create a new pipeline job.
4. Select "Pipeline script from SCM" and provide the GitHub repository URL.
5. Save and build the pipeline.

### Step 10: Provide Credentials
Provide the required credentials in Jenkins to enable GitHub access.

### Step 11: Configure Jenkins for CI/CD:
   - Set up a Jenkins pipeline to automate the deployment.
   - Add the repository URL and credentials to Jenkins.
   - Enable GitHub webhooks to trigger Jenkins builds on code changes.

### Step 12: Access the Application:
   - The application should now be accessible at `http://192.168.56.15:5000/` or `http://192.168.56.14:5000/`.

![Weather App Screenshot](https://github.com/user-attachments/assets/ef75a7b7-78e5-446f-be78-e9cfa1cd5509)


## Done 🎉
The pipeline should now be set up and running successfully!


