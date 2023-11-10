### Project title:

* Building a large language model deployment pipeline in Kubernetes

### Project category

* Software Engineering - Data science (development)

### Key skill

* Strong programming and machine learning background

### Relation with modules

🏁 To undertake this project, you should have completed one or more of the following modules.

[Cloud computing](https://www.bbk.ac.uk/courses/modules/buci/BUCI029H7#content),  [Neural Networks and Deep Learning](https://www.bbk.ac.uk/courses/modules/coiy/COIY065H7#content), [Software design and programming](https://www.bbk.ac.uk/courses/modules/coiy/COIY062H7#content), [Programming in Java](https://www.bbk.ac.uk/courses/modules/buci/BUCI033S7#content), [Software design and programming](https://www.bbk.ac.uk/courses/modules/coiy/COIY062H7#content), [Internet and web technologies](https://www.bbk.ac.uk/courses/modules/coiy/COIY063H7#content), [Applied Machine Learning](https://www.bbk.ac.uk/courses/modules/buci/BUCI077H7#content)

### Required background

*	Knowledge or willingness to learn deploying and building LLMs.
*	Fundamental knowledge of cloud computing and command line interfaces (Linux).
*	Understanding of `Kubernetes` for deployment.
*	Knowledge or willingness to learn libraries such as `Tensorflow`, `Torch` and others for data modelling.
*	Knowledge of `GitHub` and the `GitHub cli`.

### Project idea

Large language models (LLMs) like GPT-4 and its predecessors have become popular for their versatility and research breakthroughs.

LLMs' size and complexity introduce several challenges regarding real-world usage, including significant memory and computational requirements. LLMs' heavy size means they require specialized hardware (often high-end GPUs or TPUs) with significant memory to run efficiently. While LLMs can be fine-tuned on specific tasks or datasets, the process can be resource-intensive and tricky, given the size and complexity of the model.

🎯 The project aims to develop an open-source CI/CD deployment pipeline for LLM models such as Mistral, Llama and others on Kubernetes clusters in a shared environment (e.g. using multi-instance GPU capabilities). The pipeline will be developed as a Helm chart to templatize the Kubernetes manifests. 

The project use case includes the development of a seed application to highlight the deployment pipeline. The application will allow users to deploy a text file and query directly using the appropriate model.

The core solution is organised in features that include the following tasks:

1. Deploy the model and create a seed application on Kubernetes in a multi-instance GPU environment.

2. Develop the seed application.

3. Develop deployment pipelines using Helm charts.
4. Develop a use case and offer it as a service using a simple UI.

*🔍 Other features could also be identified and proposed by the student.*

### Support and resources

*	Access to GPU resources on Google Cloud Platform or Amazon Web Services.
*	Programming seed repositories and other resources to start your developments.
*	Development support and advice by expert developers.

### Project learning outcomes and skills

*	You will learn how to deploy LLMs on `Kubernetes` and build automated pipelines.
*	You will learn how to build use cases for LLMs.
*	You will learn how to use GPU processors for generative AI.
*	You will develop skills in REST API development using `Python` and associated libraries.

### Difficulty level

*	**4/5**

>  This project includes data-science-related developments including deployment of models in cloud providers. The project implementation will be organized into features - **not all features need to be developed for this project**.

### Resources:

1. [What is a large language model (LLM)?](https://www.elastic.co/what-is/large-language-models)
2. [Helm charts](https://helm.sh/docs/topics/charts/)
3. [Learning Helm](https://learning.oreilly.com/library/view/learning-helm/9781492083641/)
4. [Example of Mistral 7B (Huggingface)](https://huggingface.co/mistralai/Mistral-7B-Instruct-v0.1)
5. [Mistral AI documentation](https://docs.mistral.ai)
6. [LLama 2 research paper](https://arxiv.org/abs/2307.09288)