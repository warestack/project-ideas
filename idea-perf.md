### Project title:

* Performance modelling of cloud workloads

### Project category

* Data Science (research and development)

### Key skill

* Strong machine learning background

### Relation with modules

🏁 To undertake this project, you should have completed one or more of the following modules.

[Analytical Foundations of Data Science](https://www.bbk.ac.uk/courses/modules/buci/BUCI091H7#content), [Applied Machine Learning](https://www.bbk.ac.uk/courses/modules/buci/BUCI077H7#content), [Neural Networks and Deep Learning](https://www.bbk.ac.uk/courses/modules/coiy/COIY065H7#content), [Statistical Learning](https://www.bbk.ac.uk/courses/modules/emms/EMMS022H7#content), [Principles of Programming](https://www.bbk.ac.uk/courses/modules/buci/BUCI063H7#content)

### Required background

*	Knowledge of machine learning methods such as  `Convolutional Neural Network (CNN)`, `Recurrent Neural Network (RNN)` or similar methods.
*	Knowledge of programming with `Python` for collecting and cleaning data.
*	Fundamental understanding or willingness to learn and apply software development methods, including object-oriented programming.
*	Knowledge of libraries such as `Scikit-learn`, `Keras`, `Pyspark`, `Torch` and others for data modelling.
*	Fundamental understanding or willingness to learn time series data analysis such as `Dynamic time warping` [1], `ARIMA` [2] and others.
*	Fundamental understanding or willingness to learn and use monitoring services such as `Prometheus` [3] and visualization services such as `Graffana` [4].
*	Willingness to work with industry-standard benchmarks and workloads for relational [9] or non-relational databases [10].

### Dataset

* The dataset will be generated during experimental analysis using industry-based benchmarks as in [9] and [10] - instructions will be provided.

### Project idea

Performance modelling of cloud workloads aims to create computational models to estimate and forecast behavior and performance of cloud applications. Examples of such applications include:

* Resource usage to identify resource starvation scenarios for scaling.

* Reads, writes, or updates of transactional systems like an e-shop and its databases. 

* HTTP traffic of web servers for estimating traffic spikes or identifying abnormal executions

* HTTP traffic for security aspects such as identifying DDoS attacks. 

🎯 The project aims to conduct experimental analysis of cloud applications and workloads through the development of real-time modeling.

The core implementation features include:

1. Deployment of a seed application and its associated databases. This is called a template of an application.
2. Deployment of benchmarks to emulate usage in periodic/non-periodic workloads and data collection. 
3. Modelling datasets with various methods, including proactive and reactive real-time signal analysis.
4. Develop a custom dashboard using existing tools for monitoring and alerting.
5. Develop documentation and critical analysis through comparisons.

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

>This is a data-science-related development project. The project implementation will be organized into features - **not all features need to be developed for this project**.

### Resources:

1. [Databricks article: Understanding Dynamic Time Warping](https://docs.github.com/en/codespaces/overview)
2. [Autoregressive Integrated Moving Average (ARIMA) Prediction Model](https://www.investopedia.com/terms/a/autoregressive-integrated-moving-average-arima.asp)
3. [Prometheus monitoging system](https://prometheus.io)
4. [Grafana labs](https://www.youtube.com/watch?v=ocPOHZJ21jE)
5. S. Chouliaras and S. Sotiriadis, [Real-Time Anomaly Detection of NoSQL Systems Based on Resource Usage Monitoring](https://ieeexplore.ieee.org/abstract/document/8930068) in *IEEE Transactions on Industrial Informatics*, vol. 16, no. 9, pp. 6042-6049, Sept. 2020, doi: 10.1109/TII.2019.2958606.
6. S. Chouliaras and S. Sotiriadis, [Towards constrained optimization of cloud applications: A hybrid approach](https://www.sciencedirect.com/science/article/pii/S0167739X23003539),
   *Future Generation Computer Systems*, 2023, doi: 10.1016/j.future.2023.09.024
7. S. Chouliaras and S. Sotiriadis, [An adaptive auto-scaling framework for cloud resource provisioning](https://www.sciencedirect.com/science/article/pii/S0167739X23002005),
   Future Generation Computer Systems, Volume 148, 2023, Pages 173-183, ISSN 0167-739X,
    doi: 10.1016/j.future.2023.05.017
8. A. Bhattacharyya, S. A. J. Jandaghi, S. Sotiriadis and C. Amza, [Semantic Aware Online Detection of Resource Anomalies on the Cloud](https://www.eecg.toronto.edu/~amza/papers/cloudcom.pdf) *2016 IEEE International Conference on Cloud Computing Technology and Science (CloudCom)*, Luxembourg, Luxembourg, 2016, pp. 134-143, doi: 10.1109/CloudCom.2016.0035
9. [TPC-C benchmark](https://www.tpc.org/tpcc/)
10. [YCSB benchmark](https://github.com/brianfrankcooper/YCSB)

