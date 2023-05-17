# assignment
Run a Production grade Wordpress app on Kubernetes using Aws cloud 

step1 
Set up an Amazon EKS Cluster:
. Log in to the AWS Management Console: https://console.aws.amazon.com/
. Navigate to the Amazon EKS service by searching for "EKS" in the search bar and selecting "Amazon Elastic Kubernetes Service (EKS)".
. Click on "Create cluster" to start the cluster creation process.
. Select the "Amazon EKS" cluster type and click on "Next".
. Configure the cluster details:

Enter a unique name for your cluster in the "Cluster name" field.
Choose the desired Kubernetes version.
Select the VPC and subnets where you want to launch your cluster.
Choose the appropriate security group settings.

Select the "Create a new IAM role" option.
Provide a unique name for the service role that will be created to manage your cluster.
. Configure the logging and monitoring settings according to your preference.
. Review the cluster configuration and click on "Create" to initiate the cluster creation process.
. Wait for the cluster to be created. This may take several minutes.
. Once the cluster is created, you can click on "View cluster" to access the cluster details.


