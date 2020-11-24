# mongoEKS
 A kubernetes cluster deployed with Terraform that uses a mongoDB backend database.

 This kubernetes cluster contains two kinds of pods, a frontend application and a backend database.
 The front end is served by an nginx web server and the backend is a mongodb database connected to mongo express.

 The credentials for the database are stored in the secret.yaml file for kubernetes. The values are passed into the mongodb and mongo express deployment files. This allows the admin to keep the credentials out of the deployment file and safe.

 The configmap.yaml file is used to connect the services together. It maps the adstract urls for each service and kubernetes takes care of the networking for each individual pod and its ip address. This way if a pod is destroyed and replaced, the networking doesn't have to be redone. This helps a lot because with kubernetes, everytime you update a pod you don't need to map the new ip address.

The service for the front end includes a load balancer created on AWS that helps route the traffic to the front end applications. 
