# Serverless Functions

## What is serverless?

* Serverless is a cloud computing application development and execution model that enables developers to build and run application code without provisioning or managing servers or backend infrastructure.
* Serverless lets developers put all their focus into writing the best front-end application code and business logic they can. All developers need to do is write their application code and deploy it to containers managed by a cloud service provider. The cloud provider handles the rest, provisioning the cloud infrastructure required to run the code and scaling the infrastructure up and down on demand as needed. The cloud provider is also responsible for all routine infrastructure management and maintenance such as operating system updates and patches, security management, capacity planning, system monitoring and more.
* 'Serverless' describes the developer’s experience with those servers—they are are invisible to the developer, who doesn't see them, manage them, or interact with them in any way.

## More than just FaaS

* Function-as-a-service, or FaaS, is a cloud computing service that enables developers to run code or containers in response to specific events or requests, without specifying or managing the infrastructure required to run to code.
* In addition to FaaS, these services include:
  * Serverless databases and storage: Databases (SQL and NoSQL) and storage (particularly object storage) are the foundation of the data layer
  * Event streaming and messaging
  * API gateways

## Serverless vs. PaaS, containers, and VMs

* Because serverless, platform as a service (PaaS), containers, and virtual machines (VMs) all play a critical role in the cloud application development and compute ecosystem, it’s useful to compare how serverless compares to the others across some key attributes.

  * Provisioning time
  * Administrative burden
  * Maintenance
  * Scaling
  * Capacity planning
  * Statelessness
  * High availability (HA) and disaster recovery (DR)
  * Resource utilization
  * Billing granularity and savings

## Serverless, Kubernetes and Knative

* Kubernetes is an open-source container orchestration platform that automates the deployment, management and scaling of containers. Serverless applications are often deployed in containers. But on its own, Kubernetes can't run serverless apps without specialized software that integrates Kubernetes with a specific cloud provider's serverless platform.
* Knative provides a serverless framework for Kubernetes. It’s an open-source extension to Kubernetes that enables any container to run as a serverless workload on any cloud platform that runs Kubernetes, whether the container is built around a serverless function or some other application code (e.g., microservices). Knative is transparent to developers—they just build a container as usual using Kubernetes, and Knative does the rest, running the container as a serverless workload.

## Pros of serverless

* Improved developer productivity
* Pay for execution only
* Develop in any language
* Streamlined development/DevOps cycles
* Cost-effective performance
* Usage visibility

I didn't see any cons in the article

## Things I want to know more about

* Real-world examples of how serverless can be a benefit for developers or companies.

Source: <https://www.ibm.com/topics/serverless>
