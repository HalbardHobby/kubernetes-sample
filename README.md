# Kubernetes Beginner Project

This repository contains a simple kubernetes project with multiple pods and a load balancer based on NGINX.

## Pieces of the project

### Deployments
Deployments are the basic unit of kubernetes, within them you can find how each component is defined and configured. In this example there are three deployments as follow: 

- [Main deployment](bookie_deployment.yaml)
- [NGINX load balancer](nginx_deployment.yaml)
- [Postgres database](postgres_deployment.yaml)

### Services
Services define the way each pod is exposed, either to other services within the cluster or to an external network. These are as follow:

- [Database service](postres_service.yaml)
- [Main Service](bookie_service.yaml)
- [Load balancer and external service](nginx_service.yaml)

### Secrets
There are times when a service needs to ofuscate information that could be sensitive. Kubernetes offers a _secret_ object that allows for this information to be stored without being shared. Normally this information would be excluded from the version control.

- [Database secret](postgres_secret.yaml)

### Configurations
As the name implies, this components give a better control when configuring services, allowing for more readable and better configured environments. in this example, the database and load balancer were configured to allow a correct function of the application.

- [Database configuration](postgres_config.yaml)
- [Load balancer configuration](nginx_config.yaml)

## Deploying the project

In this example ``Minikube`` was used to provide a local cluster in which to deploy the application, to install it just follow the [instructions](https://minikube.sigs.k8s.io/docs/start/).

Once installed and started, it is possible to begin with the deployment. It is important to take into account the existing dependencies between components in order to avoid errors. In this case, the order to follow is the following:

1. Secrets & Configurations
2. Database deployment & service
3. Main deployment & service
4. Load balancer deployment
5. Load balancer service

Finally, to access the service you can use the command ``minikube service nginx-service``

## Author

**Alejandro Espinosa**