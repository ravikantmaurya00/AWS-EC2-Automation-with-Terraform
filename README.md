# AWS-EC2-Automation-with-Terraform
This repository contains Terraform scripts to automate the provisioning of AWS EC2 instances. It simplifies infrastructure management by enabling declarative configuration, ensuring consistency, and reducing manual effort.
## Automating AWS EC2 Provisioning with Terraform
- **Step 1:-**  Login to your AWS Management Console. 
- **Step 2:-** Create a EC2 Instance  .
- **Step 3:-** Then Select  the instance and click on connect.
- **Step 4:-** Then  **Install Terraform**.
    - **Windows**
      -  Download Terraform from the [Terraform website].
      -  Extract the .zip file and add it to your system’s PATH.
      -  Verify the installation: ` terraform --version`
    - **macOS(Using Homebrew)**
        ```
        brew tap hashicorp/tap
        brew install hashicorp/tap/terraform
        terraform --version
        ```
    - **Linux**
       ```
      sudo apt-get update && sudo apt-get install -y gnupg software-properties-common
      wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
      echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee 
         /etc/apt/sources.list.d/hashicorp.list
      sudo apt-get update && sudo apt-get install terraform
      terraform --version
       ```
          
- **Step 5:-** **Configuring Terraform for AWS**
  Terraform requires AWS credentials to interact with your AWS environment. 
  You can configure AWS credentials in two ways:
  - **Using AWS CLI**
     - Install AWS CLI:
       ```
       sudo apt install awscli  # Linux
       brew install awscli       # macOS
       ```
    - Configure AWS:
      ```
      aws configure
      ```
- **Step 1:-**
- **Step 1:-**
- **Step 1:-**
- **Step 1:-**
**Step 1:-**
**Step 1:-**


