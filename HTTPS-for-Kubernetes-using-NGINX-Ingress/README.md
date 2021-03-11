1. Create a namespace :
   
   kubectl create namespace cert-manager

2. Install cert-manager :

   kubectl apply --validate=false -f cert_mgr_name
   
3. Create a certificate issuer :

   kubectl apply -f cert.yaml
   
4. Update ingress configuration :
   
   kubectl apply -f ingress.yaml

5. Check the Certificate :

   kubectl describe certificate

   
