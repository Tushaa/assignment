# assignment
Run a Production grade Wordpress app on Kubernetes using Aws cloud 

step1 --
Set up an Amazon EKS Cluster:
1. Log in to the AWS Management Console: https://console.aws.amazon.com/

2. Navigate to the Amazon EKS service by searching for "EKS" in the search bar and selecting "Amazon Elastic Kubernetes Service (EKS)".

3. Click on "Create cluster" to start the cluster creation process.

4. Select the "Amazon EKS" cluster type and click on "Next".

5. Configure the cluster details:
   - Enter a unique name for your cluster in the "Cluster name" field.
   - Choose the desired Kubernetes version.
   - Select the VPC and subnets where you want to launch your cluster.
   - Choose the appropriate security group settings.

6. Configure the authentication and access control:
   - Select the "Create a new IAM role" option.
   - Provide a unique name for the service role that will be created to manage your cluster.

7. Configure the logging and monitoring settings according to your preference.

8. Review the cluster configuration and click on "Create" to initiate the cluster creation process.

9. Wait for the cluster to be created. This may take several minutes.

10. Once the cluster is created, you can click on "View cluster" to access the cluster details.


