### Project title:

* Cost modelling and estimation of cloud-native applications

### Project category

* Data Science (research and development)

### Key skill

* Strong cloud computing and machine learning background

### Relation with modules

🏁 To undertake this project, you should have completed one or more of the following modules.

[Cloud computing](https://www.bbk.ac.uk/courses/modules/buci/BUCI029H7#content), [Analytical Foundations of Data Science](https://www.bbk.ac.uk/courses/modules/buci/BUCI091H7#content), [Applied Machine Learning](https://www.bbk.ac.uk/courses/modules/buci/BUCI077H7#content), [Neural Networks and Deep Learning](https://www.bbk.ac.uk/courses/modules/coiy/COIY065H7#content), [Statistical Learning](https://www.bbk.ac.uk/courses/modules/emms/EMMS022H7#content), [Principles of Programming](https://www.bbk.ac.uk/courses/modules/buci/BUCI063H7#content)

### Required background

*	Knowledge of machine learning methods for modelling time series datasets.
*	Knowledge of programming with `Python` for collecting and cleaning data.
*	Understanding or willigness to learn the use of `Kubernetes` for deployment.
*	Knowledge or willingness to learn developing APIs using `Python`,  `Node.js`, `Go` or similar frameworks.
*	Fundamental understanding or willingness to learn and apply software development methods, including object-oriented programming.
*	Knowledge of libraries such as `Scikit-learn`, `Keras`, `Pyspark`, `Torch` and others for data modelling.
*	Fundamental understanding or willingness to learn and use monitoring services such as `Prometheus` [4] and visualization services such as `Graffana` [3].
*	Willingness to work with industry-standard benchmarks and workloads for relational [6] or non-relational databases [7].

### Dataset

* The dataset will be generated during experimental analysis using industry-based benchmarks as in [6] and [7] - instructions will be provided.

### Project idea

Cost modelling of cloud workloads aims to create computational models to estimate and forecast cloud resource burst for cloud native applications. 

Achieving accurate cost modeling, especially in Kubernetes deployed cloud workloads is challenging for several reasons:

1. Complex Pricing Models: Cloud service providers have complex pricing structures that can vary by instance type, usage duration, bandwidth, and additional services like storage and data transfer.
2. Dynamic Workloads: Cloud-native applications often experience variable workloads. Predicting these fluctuations accurately is complex, as they depend on many unpredictable factors, such as user behavior.
3. Multi-Tenancy and Shared Resources: Kubernetes often runs containers from different applications and environments on the same physical resources, which complicates cost management.
4. Complex Pricing Structures: Complex pricing includes various factors such as compute, storage, and network usage. Mapping this pricing to the dynamically changing resource usage within Kubernetes is non-trivial.
5. Granularity of Services: Kubernetes supports microservices architectures, which means an application can be split into many small services, each potentially scaling independently and incurring costs.
6. Overhead Costs: Kubernetes itself requires compute resources to run its management components, and understanding the cost of this overhead is essential for accurate budgeting.
7. Lack of Visibility: Traditional monitoring tools may not provide the visibility needed to understand costs at the container, pod, or service level within a Kubernetes cluster.

🎯 The project aims to develop a microservice back-end service to collect and analyse workload data to predict cloud costs for Kubernetes deployed applications.

The core project features include:

1. Explore and understand different cloud cost models in AWS and GCP.
2. Use seed applications that will run on a Kubernetes cluster.
3. Develop deployment pipelines to deploy and run the applications, to monitor and explore cost metrics in relation to resource usage.
4. Model the behaviour of applications based on cost metrics for forecasting costs and making recommendations.
5. Develop a use case and present an experimental analysis.

*🔍 Other features could also be identified and proposed by the student.*

### Support and resources

*	Access to the Google Cloud Platform or Amazon Web Services.
*	Programming seed repositories and other resources to start your developments.
*	Development support and advice by expert data scientists.

### Project learning outcomes and skills

*	You will learn how to build modern AI-based solutions for solving real-world problems.
*	You will learn how to use popular machine-learning and time series analysis methods for close to real-time data analysis.
*	You will develop skills in using and integrating monitoring systems for real-time data analysis.
*	You will have the opportunity to work towards an academic publication in case results showcase an improvement of the literature.

### Difficulty level

*	**3/5**

>This project includes data-science-related developments. The project implementation will be organized into features - **not all features need to be developed for this project**.

### Resources:

1. [Kubernetes](https://kubernetes.io) and [Kubernetes API](https://kubernetes.io/docs/concepts/overview/kubernetes-api/)
2. [Prometheus monitoging system](https://prometheus.io)
3. [Grafana labs](https://www.investopedia.com/terms/a/autoregressive-integrated-moving-average-arima.asp)
4. [Prometheus monitoging system](https://prometheus.io)
5. [Grafana labs](https://www.youtube.com/watch?v=ocPOHZJ21jE)
6. [TPC-C benchmark](https://www.tpc.org/tpcc/)
7. [YCSB benchmark](https://github.com/brianfrankcooper/YCSB)

