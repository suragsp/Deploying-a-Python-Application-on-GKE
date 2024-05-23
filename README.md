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



Part 2
1. gcloud auth login
2. gcloud config set project YOUR_PROJECT_ID
3. gcloud container clusters create my-gke-cluster \
    --zone us-central1-a \
    --num-nodes 3 \
    --machine-type e2-medium \
    --disk-size 10GB
   
![image](https://github.com/suragsp/Deploying-a-Python-Application-on-GKE/assets/104720115/b45d8fca-65d8-40c1-80ab-b7ad95ddc9c0)

<h2>CLUSTER_NAME: my-gke-cluster
ZONE: us-central1-a (or choose a different zone close to your region)
NUM_NODES: 3</h2>.

![image](https://github.com/suragsp/Deploying-a-Python-Application-on-GKE/assets/104720115/2600eb24-4343-4bf3-89c7-1ccc4d85326e)

4. gcloud container clusters get-credentials my-gke-cluster --zone us-central1-a

   ![image](https://github.com/suragsp/Deploying-a-Python-Application-on-GKE/assets/104720115/16cef155-56f8-46bf-ac7e-e96fc2909f67)

5. kubectl create secret docker-registry gcr-json-key \
    --docker-server=gcr.io \
    --docker-username=_json_key \
    --docker-password="$(cat /home/suragsp/cloudstorageuploader-c9d203ce6c6e.json)" \
    --docker-email=your-email@example.com


   ![image](https://github.com/suragsp/Deploying-a-Python-Application-on-GKE/assets/104720115/45a29d3b-0fe2-4da7-9d9a-23d187fec94c)

6. docker build -t gcr.io/cloudstorageuploader/app:latest .


![image](https://github.com/suragsp/Deploying-a-Python-Application-on-GKE/assets/104720115/4ce391a5-af5e-40bb-b82e-1ec4bfc82dc6)

7. docker push gcr.io/cloudstorageuploader/app:latest


![image](https://github.com/suragsp/Deploying-a-Python-Application-on-GKE/assets/104720115/5547980c-5bef-4871-a534-c6b2f249de7f)

8. kubectl apply -f deployment.yaml


   ![image](https://github.com/suragsp/Deploying-a-Python-Application-on-GKE/assets/104720115/59b41b0d-7fae-45d3-84bc-8c307d9aa198)

9. kubectl expose deployment my-python-app --type=LoadBalancer --port 80 --target-port 5000

![image](https://github.com/suragsp/Deploying-a-Python-Application-on-GKE/assets/104720115/94dae0d7-5b42-4ca6-bca4-4fddc9d792ad)

10. kubectl get deployments

![image](https://github.com/suragsp/Deploying-a-Python-Application-on-GKE/assets/104720115/70c9dc10-26ef-4d6b-91f8-1268320caeb4)

11. kubectl get services

![image](https://github.com/suragsp/Deploying-a-Python-Application-on-GKE/assets/104720115/4188a585-fa5f-41dc-a568-e5a343c3f70a)

12. 



















