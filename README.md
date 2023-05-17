# assignment
Run a Production grade Wordpress app on Kubernetes using Aws cloud 

## step1 --Set up an Amazon EKS Cluster:
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


## Step --2 Connect to the Kubernetes Cluster

1. Install the `kubectl` command-line tool by following the instructions in the Kubernetes documentation: https://kubernetes.io/docs/tasks/tools/

2. Configure `kubectl` to connect to your EKS cluster by running the following command: `aws eks update-kubeconfig --name <your-cluster-name>`
   
3. Verify Cluster Connectivity: Run the following command to verify that `kubectl` is properly configured and can connect to your EKS cluster:
  `kubectl get nodes`

## Step3 --Create PersistentVolumeClaims and PersistentVolumes

## Create PersistentVolumeClaims
To request storage resources for your WordPress application, you can create PersistentVolumeClaims (PVCs) in your Kubernetes cluster. PVCs define the storage requirements, such as storage class, access mode, and size.

1. Create a new file named `pvc.yaml` in a text editor.

2. Copy and paste the following YAML configuration into the `pvc.yaml` file:

   ```yaml
   apiVersion: v1
   kind: PersistentVolumeClaim
   metadata:
     name: wordpress-pvc
   spec:
     accessModes:
       - ReadWriteOnce
     resources:
       requests:
         storage: 5Gi
     storageClassName: <your-storage-class>

3. Replace <your-storage-class> with the name of the storage class you want to use. You can find the available storage classes in your cluster by running the command: kubectl get storageclasses,Save the pvc.yaml file.
   
4. Apply the PVC configuration by running the following command: `kubectl apply -f pvc.yaml`

   ## Creating PersistentVolumes (PVs)

To provide persistent storage for your applications in Kubernetes, you can create PersistentVolumes (PVs) by following these steps:

1. Create a new file named `pv.yaml` in a text editor.

2. Copy and paste the following YAML configuration into the `pv.yaml` file:

3. Replace <your-storage-class> with the same storage class used in the PVC you created earlier.Adjust the storage value as per your storage requirements.
Save the pv.yaml file.
   
4. Open a terminal or command prompt and navigate to the directory where the pv.yaml file is saved.
Apply the PV configuration by running the following command:`kubectl apply -f pv.yaml`
   
   
## Docker file 
1: Create a new directory for your project and navigate to it. `mkdir my-project`
   `cd my-project`
   
2: Step 2: Create a file named Dockerfile in the project directory and open it in a text editor.`touch Dockerfile`
   
3: Copy and paste the code into the Dockerfile. Code is in **Docker data file**
 

4: Create an Nginx configuration file named nginx.conf in the project directory and open it in a text editor.
`touch nginx.conf`
   
5: Copy and paste your desired Nginx configuration into the nginx.conf file. This should include the necessary proxying directives for passing requests to WordPress.
Add your Nginx configuration here **Copy the configuration from configuration file on github** Save the Dockerfile and nginx.conf files.

6: Build the Docker image using the following command:
`docker build -t my-wordpress` .
Replace my-wordpress with the desired name for your Docker image.

7: Run the Docker container based on the image you built:
`docker run -p 80:80 my-wordpress`
This will map port 80 of the container to port 80 of the host machine, allowing you to access your WordPress site.


## Deploying WordPress using Helm

To deploy WordPress using Helm, follow these steps:

1. Install Helm on your local machine by following the official Helm documentation. Helm is a package manager for Kubernetes that simplifies the deployment of applications.

2. Add the WordPress Helm repository. Replace `<repository-url>` with the actual URL of the repository. You can use the official WordPress Helm repository or any other trusted repository.

   ```shell
   helm repo add my-repo <repository-url>
   
3. Deploy WordPress using the Helm chart. Replace <my-release> with the desired name for your release.
   
   ```shell
   helm install <my-release> my-repo/wordpress -f values.yaml
   
4. Wait for the deployment to complete. You can check the status using the following command:
   
   ```shell
   helm status <my-release>
   
5. To clean up the deployment, delete the Helm release
   ```shell
   helm delete my-release
 Wait for the release to be deleted.
   

   

   
   
   
   
   
   
   
   
   
   
   
   
   
   
