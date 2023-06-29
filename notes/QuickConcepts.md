# Quick Concepts

Some quick concepts to become familiar with:
    Node - The server, computer, or VM with is running Kubernetes
    Container - Running docker images
    Pod - An encapsulation of a container,
          1 app per pod,
          given IP addresses for Kubernetes internal network,
          ephemeral
    Service - Mapping of an ephemeral ip of a pod to a static ip of a service
              Service is also a load-balancer for nodes
    External Service - Web app to access an external service
    Ingres - DNS for services and external services,
             Possibly some port MUX/DMUX???
    ConfigMap - Yaml file,
                External config of entire application such as URLs,
                URLs can be used as inter pod communication,
                Passed to the application pod so it can function
    Secrets - Yaml file,
              Config map but used for confidential data,
              Base 64 encoded
    Volumes - Used as persistent storage for pods because they are ephemeral,
              Attaches physical storage or remote storage to pods

Replicate everything to have High Availability

Have another node which shares the same services of the original node

    Deployment - Blueprint for pods to ensure replication,
                 We create deployments to create pods
                
Databases are harder to replicate since we cannot have data inconsistencies

Databases can't be replicated by deployments because of this

    StatefulSet - A deployment tool for databases,
                  Difficult to use
                  DBs are often hosted outside of clusters