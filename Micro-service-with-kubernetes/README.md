1. git clone https://github.com/S3Infosoft/s3-docker-k8s-explorations/new/main/Micro-service-with-kubernetes
2. cd .\Micro-service-with-kubernetes
3. Execute into your CMD : docker build -t dockerid/filename
4. To check if the build is successful : docker images image_name
5. To run the image :

   docker run -p 8080:8080 image_name
  
6. Run the following command with the file name to deploy the created image into containers :
   
   kubectl create -f .\deployment.yml
   
7. kubectl get pods

8. kubectl port-forward docker_id 8080:8080

9. Now we have executed everything and now we should test the deployment onto the :

   http://127.0.0.1:8080/employee
 
10. This should show you the deployed micro service onto the Kubernetes.

   
