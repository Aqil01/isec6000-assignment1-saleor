# Building, Deploying, and Securing a Microservices E-commerce Application
## Create a Kubernetes Cluster on Google Kubernetes Engine
1)	Access the Google Cloud Console by signing in with your google account. You will have to add billing info and with that you get an initial amount that helps to play around with the GKE for a start.

2)	Then you can follow the steps below to **create a new project**:
       1) In the Google Cloud console, go to the Manage Resources page. Link: [Go to Manage Resources](https://console.cloud.google.com/cloud-resource-manager?walkthrough_id=resource-manager--create-project&start_index=1&_ga=2.210894805.1333585992.1693288858-1368561227.1693027365&_gac=1.54144346.1693027503.CjwKCAjwoqGnBhAcEiwAwK-OkdDkdFh8ORWsvhT0rYfi1Z1M_rtcCVCt1oi9nYEgsSw0TueDC7ddFhoCx90QAvD_BwE#step_index=1)
       2) Then click the **Create Project** button
       3) Create a new project named '**Saleor e-commerce**' in the New Project window.
       4) When you have finished entering new project information, click **Create**
          ![Create project image](https://github.com/Aqil01/isec6000-assignment1-saleor/blob/4bc9d6d94d8002986c8bd1c04afdabc239e63f11/asset/1-Create%20Project%20Image.png)
       5) Activate the Google Kubernetes Engine and Artifact Registry APIs.
       6) To launch the cloud shell, click the **Activate Cloud Shell** button, which is located next to the search toolbar in the upper-right corner of the console. Cloud Shell gives you command-line access to Google Cloud computing resources. Cloud Shell includes the Google Cloud CLI and the kubectl command-line tool. The gcloud CLI is the primary command-line interface for Google Cloud, while kubectl is the primary command-line interface for running commands against Kubernetes clusters. 
          You can then **Authorize Cloud Shell** if this is your first time using it
          ![Authorize Cloud Shell image](https://github.com/Aqil01/isec6000-assignment1-saleor/blob/4bc9d6d94d8002986c8bd1c04afdabc239e63f11/asset/2-Authorize%20Cloud%20Shell%20Image.png)
          The Cloud Shell session will appear in the bottom of the page.
          This shell is used to execute gcloud and kubectl commands. Set your default project in the Google Cloud CLI by running the following command:
          ```
          gcloud config set project saleor-e-commerce 
          ```
          ![gcloud default project configuration image](https://github.com/Aqil01/isec6000-assignment1-saleor/blob/4bc9d6d94d8002986c8bd1c04afdabc239e63f11/asset/3-gcloud%20default%20project%20configuration%20image.png)
          Choose a Default Compute Zone: The Compute Zone aids in providing a general idea of where the clusters and resources will be located physically.
          Run the following command in the cloud shell to set your default compute zone:
          ```
          cloud config set compute/zone us-central1-a 
          ```
          Note: You can change us-central1-a to any zone you want.

3)  Next to create a Kubernetes cluster, select **Kubernetes Engine** from the navigation menu followed by **Clusters**

4) Configure the cluster's settings, such as the name, location, and node pool configuration. Then click **Create** to provision your GKE cluster.
    ![Create cluster image](https://github.com/Aqil01/isec6000-assignment1-saleor/blob/4bc9d6d94d8002986c8bd1c04afdabc239e63f11/asset/4-create%20cluster%20image.png)

    The cluster '**isec6000-saleor-cluster**' is created now
    ![Cluster created image](https://github.com/Aqil01/isec6000-assignment1-saleor/blob/4bc9d6d94d8002986c8bd1c04afdabc239e63f11/asset/5-cluster%20created%20image.png)

## Install and configure kubectl to manage your Kubernetes cluster
1) After creating the GKE cluster, open the Cloud shell and type in the following command to configure kubectl to use the cluster you created:
          ```
          gcloud container clusters get-credentials isec6000-saleor-cluster --zone us-central1-a 
          ```
   ![Configure kubectl image](https://github.com/Aqil01/isec6000-assignment1-saleor/blob/4bc9d6d94d8002986c8bd1c04afdabc239e63f11/asset/6-configure%20kubectl%20image.png)

## Microservices Architecture and Deployment of Saleor e-commerce app
1) Install Docker following the [Docker Installation Guide](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository) to run the containerised saleor app.

2) To avoid the risks presented by running docker as root user, follow the steps in this link: [Docker post install steps](https://docs.docker.com/engine/install/linux-postinstall/)

3) Fork the [saleor-platform](https://github.com/saleor/saleor-platform) repository to your GitHub account. Then modify the **docker-compose.yaml** file to assign port 9002 for the Saleor Dashboard.
![Compose file edit image](https://github.com/Aqil01/isec6000-assignment1-saleor/blob/4bc9d6d94d8002986c8bd1c04afdabc239e63f11/asset/7-Compose%20file%20edit%20image.png)

4) Follow the steps in [saleor-platform](https://github.com/saleor/saleor-platform) repository to effectively run a Saleor stack enriched with sample data.

## Vulnerability Scanning
Use tools like trivy to scan the container images for vulnerability. You can install trivy by following the instructions on the following webpage: [Install trivy](https://aquasecurity.github.io/trivy/v0.27.1/getting-started/installation/)
