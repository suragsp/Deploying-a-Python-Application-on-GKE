# Deploying-a-Python-Application-on-GKE
I will be using Powershell and VScode.
Step 1. Install Google Cloud SDK: Download and install the Google Cloud SDK.
Step 2. Initialize Google Cloud SDK: Open PowerShell and run:(Note: I am in the same folder in which i will be making and maintaining all my files.)
        gcloud init
Step 3.  Configure Gcloud (In case you follow stepl 2 yoiu will be able to login already if not use "gcloud auth login")
<h1>Let us set our project now.</h1> gcloud config set project YOUR_PROJECT_ID 

Note: use "gcloud projects list to get all the project list(If you don't have a GCloud made you can follow <a href="https://github.com/suragsp/Microservice-GCP">Click for how to make the Gcloud</a>)

![image](https://github.com/suragsp/Deploying-a-Python-Application-on-GKE/assets/104720115/4932721e-e90c-450b-a4a1-67a7ddee483b)

![image](https://github.com/suragsp/Deploying-a-Python-Application-on-GKE/assets/104720115/d42ae2aa-6a7a-4043-944f-db76c496ba6e)

Step 4: Create a GKE Cluster
You would need to install Kubernates API if not Installed - https://console.cloud.google.com/apis/library/container.googleapis.com
<h1>Check if account logged in and the account you have the actual project are the same </h1>

![image](https://github.com/suragsp/Deploying-a-Python-Application-on-GKE/assets/104720115/0ea3cbfa-928e-4f02-a5f9-06b2c9d87740)

Use Command - gcloud container clusters create my-gke-cluster --zone us-central1-a --num-nodes 3 --machine-type e2-medium --disk-size 10GB

![image](https://github.com/suragsp/Deploying-a-Python-Application-on-GKE/assets/104720115/d6273c72-bae2-480a-acb1-6d16eb10408d)












