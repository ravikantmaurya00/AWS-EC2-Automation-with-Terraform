# AWS-EC2-Automation-with-Terraform
This repository contains Terraform scripts to automate the provisioning of AWS EC2 instances. It simplifies infrastructure management by enabling declarative configuration, ensuring consistency, and reducing manual effort.
## Automating AWS EC2 Provisioning with Terraform
- **Step 1:-**  Login to your AWS Management Console. 
- **Step 2:-** Create a EC2 Instance .
  
  ![](https://github.com/ravikantmaurya00/AWS-EC2-Automation-with-Terraform/blob/main/ScreenShot/ec2%20instance.png)
  
- **Step 3:-** Then Select  the instance and click on connect.
  
  ![](https://github.com/ravikantmaurya00/AWS-EC2-Automation-with-Terraform/blob/main/ScreenShot/ec2%20connect.png.png)

  ![](https://github.com/ravikantmaurya00/AWS-EC2-Automation-with-Terraform/blob/main/ScreenShot/ubuntu%20basic%20command.png)

  ![](https://github.com/ravikantmaurya00/AWS-EC2-Automation-with-Terraform/blob/main/ScreenShot/ubuntu.png)
  
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
       ![](https://github.com/ravikantmaurya00/AWS-EC2-Automation-with-Terraform/blob/main/ScreenShot/install%20terraform.png)
          
- **Step 5:-** **Configuring Terraform for AWS**
  
  Terraform requires AWS credentials to interact with your AWS environment. 
  You can configure AWS credentials in two ways:
  - **Using AWS CLI**
     - Install AWS CLI:
       ```
       sudo apt install awscli  # Linux
       brew install awscli       # macOS
       ```
       
       ![](https://github.com/ravikantmaurya00/AWS-EC2-Automation-with-Terraform/blob/main/ScreenShot/install%20awscli.png)
       
    - Configure AWS:
      ```
      aws configure
      ```
      Provide your AWS Access Key ,Secret Key ,Region and Output format.
      - How to get AWS Access Key and Secret Key
        - **Step 1:-** In AWS Search Bar  search for IAM( **Identity and  Access Management**).
          
          ![](https://github.com/ravikantmaurya00/AWS-EC2-Automation-with-Terraform/blob/main/ScreenShot/10.png)
          
        - **Step 2:-** In left Panel click on **users** and then on Create a new User.
        - **Step 3:-** Name yor IAM User and  then click on next.
          
          ![](https://github.com/ravikantmaurya00/AWS-EC2-Automation-with-Terraform/blob/main/ScreenShot/11.png)

           ![](https://github.com/ravikantmaurya00/AWS-EC2-Automation-with-Terraform/blob/main/ScreenShot/12.png)
          
        - **Step 4:-**  Then again click on Create user and your User is created.
          
          ![](https://github.com/ravikantmaurya00/AWS-EC2-Automation-with-Terraform/blob/main/ScreenShot/13.png)
          
        - **Step 5:-**  Select your user and click on Create A new **Access Key**.
          
           ![](https://github.com/ravikantmaurya00/AWS-EC2-Automation-with-Terraform/blob/main/ScreenShot/14.png)
          
        - **Step 6:-**  Then select **Command Line Interface (CLI)**. And  check the  recommendation and then click on next.
          
          ![](https://github.com/ravikantmaurya00/AWS-EC2-Automation-with-Terraform/blob/main/ScreenShot/15.png)
          
        - **Step 7:-** Then Write the description for creating the **Access Key**. And click on Create Access Key.
        - **Step 8:-** And then your Access Key is created Save your Secret Key and download your **csv.file**.
          
          ![](https://github.com/ravikantmaurya00/AWS-EC2-Automation-with-Terraform/blob/main/ScreenShot/16.png)
          
  - **Manually Adding AWS Credentials***
    Store credentials in `~/.aws/credentials`:
    ```
    [default]
    aws_access_key_id = YOUR_ACCESS_KEY
    aws_secret_access_key = YOUR_SECRET_KEY
    region = eu-west-2
     ```
- **Step 6:-** **Writing the Terraform Configuration File**
  
  Now, create a working directory for Terraform:
  ```
  mkdir terraform-ec2 && cd terraform-ec2
  ```
  - **Create a file named main.tf**
    ```
    nano main.tf
    ```
  -**Add the following configuration:**
    ```
    provider "aws" {
    profile = "default"
    region  = "eu-west-2"
    }

    resource "aws_instance" "UGO_Server" {
    ami           = "ami-0cbf43fd299e3a464"
    instance_type = "t2.micro"

    tags = {
        Name = "MyNCAAInstance"
    }
    }
    ```
    
    ![](https://github.com/ravikantmaurya00/AWS-EC2-Automation-with-Terraform/blob/main/ScreenShot/main%20file.png)
  
    Then Press **CTRL + X**, then **Y**, and hit **Enter** to save and exit.
- **Step 7:-** **Initializing and Applying Terraform**
  
  Before deploying, we need to initialize Terraform:
  ```
  terraform init
  ```
  This downloads the necessary provider plugins.
  
  ![](https://github.com/ravikantmaurya00/AWS-EC2-Automation-with-Terraform/blob/main/ScreenShot/terraform%20initialised.png)
  
  - **Check the Execution Plan**
    ```
    terraform plan
    ```
    This shows what Terraform will create.
    
    ![](https://github.com/ravikantmaurya00/AWS-EC2-Automation-with-Terraform/blob/main/ScreenShot/terrform%20plan.png)
    
    ![](https://github.com/ravikantmaurya00/AWS-EC2-Automation-with-Terraform/blob/main/ScreenShot/terraform%20plan1.png)
    
  - **Apply the Configuration**
    
    Now, deploy your EC2 instance:
    ```
    terraform apply -auto-approve
    ```
    This provisions the EC2 instance in AWS.
    
    ![](https://github.com/ravikantmaurya00/AWS-EC2-Automation-with-Terraform/blob/main/ScreenShot/configuration%20terraform.png)
    
- **Step 8:-** **Confirming the Deployment**
  - Step 1:- Go to the AWS Console
  - Step 2:- Navigate to EC2 → Instances
  - Step 3:- Verify that your instance is running 🎉
    
    ![](https://github.com/ravikantmaurya00/AWS-EC2-Automation-with-Terraform/blob/main/ScreenShot/cofirming%20deployment.png)
    
    ![](https://github.com/ravikantmaurya00/AWS-EC2-Automation-with-Terraform/blob/main/ScreenShot/confirming%20deployment%201.png)
    
- **Step 9:-** **Destroying the Infrastructure**
  
  When you're done, clean up resources to avoid unnecessary charges:
  ```
  terraform destroy -auto-approve
  ```
  This safely removes all provisioned resources.
  
  ![](https://github.com/ravikantmaurya00/AWS-EC2-Automation-with-Terraform/blob/main/ScreenShot/destroying%20terrform.png)

## 💡 Key Takeaways
  - Terraform simplifies cloud provisioning with Infrastructure as Code (IaC).
  - You can automate AWS EC2 deployment in a few lines of code.
  - Terraform ensures repeatability, scalability, and consistency in cloud infrastructure.
  - Cleanup is easy using terraform destroy, preventing resource waste.
    

    
    
  
