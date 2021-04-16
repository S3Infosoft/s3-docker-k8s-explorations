#Installation of Three Applications on a Single Kubernetes Cluster#

The applications we are going to install :

1. OpenKM
2. Sentrifugo
3. OSTicket

OpenKM :

        OpenKM is a Free/Libre document management system that provides a web interface for managing nonspecific files. 
        OpenKM includes a content repository, Lucene indexing, and jBPM workflow. 
        The OpenKM system was developed using open technology.
        
Sentrifugo :

        Sentrifugo is a FREE and powerful Human Resource Management System that can be easily configured to meet your organizational needs.
        
OSTicket :

        osTicket is an attractive alternative to higher-cost and complex customer support systems; simple, lightweight, reliable, open source,
        web-based and easy to setup and use. The best part is, it's completely free.
        
        
STEPS TO FOLLOW :

1. Download all the three .YAML files from the GitHub Repository.
2. Go to your browser and typw www.kubesail.com.
3. Open your free account on the platform and login with your credentials.
4. Once you get logged in, Click on Clusters and add a cluster.
5. Copy the given command by KubeSail and paste it onto your Windows Powershell.
6. It will ask to give a name to your cluster and then take few time to create your cluster.
7. Once created you will see your cluster into the cluster section.
8. Now, click on Apps section at the top and click New App.
9. Now when you have to click on edit YAML file and copy the content of the file you downloaded before and paste it there.
10. Click on Save and give it some time.
11. Once Created you will see a message notifying about your successfull deployment.
12. You can check it by typing the following command in shell :
      
      kubectl get deployments
      
      and to see the created pods 
      
      kubectl get pods
     
13. Now you have to check the running status of the deployment.
14. After that click on Network beside status and check the SERVICES tab.
15. Click on services.
16. After clicking the service, click on create Service.
17. A service will be created.
18. Now click on Ingress and click on create Ingress.
19. It will create the Ingress Service and give you the public address to access your application.
20. Now click on the link and it will open your application.
