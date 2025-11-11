#### This project is for the Devops Bootcamp Exercise for 
#### "Container Orchestration with Kubernetes" 

10 - Container Orchestration with Kubernetes
Exercises for Module "Container Orchestration with Kubernetes"

Your bootcamp-java-mysql application (from Docker module exercises) is running with docker-compose on a server. This application is used often internally and by your company clients too. You noticed that the server isn’t very stable: Often a database container dies or the application itself, or docker daemon must be restarted. At this time people can’t access the app!

So when this happens, the users write you that the app is down and ask you to fix it. You ssh into the server, restart containers with docker-compose and containers start again.

But this is an annoying work, plus it doesn’t look good for your company that your clients often can’t access the app. So you want to make your application more reliable and highly available . You want to replicate both database and the app, so if one container goes down, there is always a backup. Also you don’t want to rely on a single server, but have multiple, in case 1 whole server goes down or gets rebooted etc.

So you look into different solutions and decide to use a container orchestration tool Kubernetes to solve the issue. For now you want to configure it and deploy your application manually, since it’s a new tool and want to try it out manually before automating.
EXERCISE 1: Create a Kubernetes cluster

    Create a Kubernetes cluster (Minikube or LKE)

EXERCISE 2: Deploy Mysql with 3 replicas

First of all, you want to deploy the mysql database.

    Deploy Mysql database with 3 replicas and volumes for data persistence

To simplify the process you can use Helm for that.
EXERCISE 3: Deploy your Java Application with 3 replicas

Now you want to

    deploy your Java application with 3 replicas.

With docker-compose, you were setting env_vars on server. In K8s there are own components for that, so

    create ConfigMap and Secret with the values and reference them in the application deployment config file.

EXERCISE 4: Deploy phpmyadmin

As a next step you

    deploy phpmyadmin to access Mysql UI.

For this deployment you just need 1 replica, since this is only for your own use, so it doesn’t have to be High Availability. A simple deployment.yaml file and internal service will be enough.

Now your application setup is running in the cluster, but you still need a proper way to access the application. Also, you don’t want users to access the application using the IP address and instead use a domain name. For that, you want to install Ingress controller in the cluster and configure ingress access for your application.
EXERCISE 5: Deploy Ingress Controller

    Deploy Ingress Controller in the cluster - using Helm

EXERCISE 6: Create Ingress rule

    Create Ingress rule for your application access

EXERCISE 7: Port-forward for phpmyadmin

However, you don’t want to expose the phpmyadmin for security reasons. So you configure port-forwarding for the service to access on localhost, whenever you need it.

    Configure port-forwarding for phpmyadmin

As the final step, you decide to create a helm chart for your Java application where all the configuration files are configurable. You can then tell developers how they can use it by setting all the chart values. This chart will be hosted in its own git repository.

EXERCISE 8: Create Helm Chart for Java App

    All config files: service, deployment, ingress, configMap, secret, will be part of the chart
    Create custom values file as an example for developers to use when deploying the application
    Deploy the java application using the chart with helmfile
    Host the chart in its own git repository

