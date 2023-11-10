### Project title:

* Multi-cloud deployer in Kubernetes

### Project category

* Software Engineering (development)

### Key skill

* Strong programming background in building APIs and knowledge of cloud computing

### Relation with modules

🏁 To undertake this project, you should have completed one or more of the following modules.

[Cloud computing](https://www.bbk.ac.uk/courses/modules/buci/BUCI029H7#content), [Software design and programming](https://www.bbk.ac.uk/courses/modules/coiy/COIY062H7#content), [Programming in Java](https://www.bbk.ac.uk/courses/modules/buci/BUCI033S7#content), [Software design and programming](https://www.bbk.ac.uk/courses/modules/coiy/COIY062H7#content), [Internet and web technologies](https://www.bbk.ac.uk/courses/modules/buci/BUCI063H7#content)

### Required background

*	Knowledge or willingness to learn developing APIs using `Node.js`, `Go` or similar frameworks.
*	Knowledge or willingness to learn infrastructure as a code (IaC) tool such as `Terraform` [4].
*	Fundamental knowledge of cloud computing and command line interfaces (Linux).
*	Understanding of REST APIs and use of `Docker` and `GitHub`.
*	Knowledge or willingness to learn orchestration frameworks and `Kubernetes`.

### Project idea

Kubernetes (K8s) is an open-source platform that automates deploying, scaling, and operating application containers. This project aims to develop an API service that facilitates deploying and managing containerized applications across multiple cloud environments using Kubernetes. This multi-cloud API would serve as an intermediary layer interacting with different Kubernetes clusters, possibly across various cloud providers such as AWS and GCP. 

The service would abstract the complexity of dealing with individual clusters, offering a uniform interface to manage deployments in a multi-cloud setting. Key features include:

* The ability to manage resources, monitor the health of deployments and perform automatic rebalancing, e.g. for locality cases and fault tolerance operations for scaling. 
* The ability to move containers from one cluster to another in response to load changes or infrastructure outages, ensuring high availability and efficient resource utilization across clouds.

🎯 The project aims to develop a tool (API-based) to optimize container orchestration in multi-cloud Kubernetes environments using the latest IaC solutions.

The core implementation tasks include:

1. Deployment of Kubernetes clusters in various providers and exploration of Kubernetes API.

2. Developing a custom API to interact with Kubernetes API. 

3. Develop a set of experiments to demonstrate scaling, rebalancing, locality and migration scenarios.

4. Deploying prototype applications using different resources and testing on various demands.

5. Develop a custom dashboard using existing tools for monitoring and alerting.

6. Develop documentation and critical analysis through comparisons.

*🔍 Other features could also be identified and proposed by the student.*

### Video description

Watch the following project description video.

* {Link to be provided soon}

### Support and resources

*	Access to the Google Cloud Platform or Amazon Web Services.
*	Programming seed repositories and other resources to start your developments.
*	Development support and advice by expert data scientists.

### Project learning outcomes and skills

*	You will learn how to integrate custom software with `Kubernetes` and build microservices.
*	You will learn how to use popular cloud platforms to deploy software and customise `Kubernetes`.
*	You will develop skills in REST API development using `Node.js` and `Go`.
*	You will learn how to use modern DevOps pipelines for software development.

### Difficulty level

*	**4.5/5**

>This is a challenging project with data-science-related developments. The project implementation will be organized into features - **not all features need to be developed for this project**.

### Resources:

1. [Kubernetes](https://kubernetes.io) and [Kubernetes API](https://kubernetes.io/docs/concepts/overview/kubernetes-api/)
2. [Prometheus monitoging system](https://prometheus.io)
3. [Grafana labs](https://www.youtube.com/watch?v=ocPOHZJ21jE)
4. [Terraform documentation](https://developer.hashicorp.com/terraform?product_intent=terraform)
5. Terraform, [Deploy federated multi-cloud Kubernetes clusters](https://developer.hashicorp.com/terraform/tutorials/networking/multicloud-kubernetes)
