### Project title:

* Migrating cloud-native application states

### Project category

* Software Engineering (development)

### Key skill

* Strong programming background in building APIs and knowledge of cloud computing

### Relation with modules

🏁 To undertake this project, you should have completed one or more of the following modules.

[Cloud computing](https://www.bbk.ac.uk/courses/modules/buci/BUCI029H7#content), [Software design and programming](https://www.bbk.ac.uk/courses/modules/coiy/COIY062H7#content), [Programming in Java](https://www.bbk.ac.uk/courses/modules/buci/BUCI033S7#content), [Software design and programming](https://www.bbk.ac.uk/courses/modules/coiy/COIY062H7#content), [Internet and web technologies](https://www.bbk.ac.uk/courses/modules/buci/BUCI063H7#content)

### Required background

*	Strong knowledge or willingness to learn using command line interfaces.
*	Knowledge or willingness to learn developing APIs using `Node.js`, `Go` or similar frameworks.
*	Knowledge or willingness to learn infrastructure as a code tool such as `Terraform` [5].
*	Knowledge or willingness to learn orchestration frameworks and `Kubernetes`.
*	Willingness to dive into `CRIU (Checkpoint/Restore In Userspace)` [1]

### Project idea

Container migration is increasingly essential due to the need for high availability, fault tolerance and seamless scaling across cloud environments. This involves developing a software tool to explore and facilitate container migration within Kubernetes environments, explicitly targeting stateless and stateful applications. 

The key objectives of this project are:

1. **Enhance fault tolerance**: By enabling containers to move across different hosts or environments, the system's overall resilience against failures can be improved.
2. **Speed up deployment**: Container migration can reduce the time it takes to deploy applications by moving containers to where they are needed most.

The key challenge is:

- **Challenging stateful application migration**: Migrating stateful applications—which maintain data state across sessions—is complex because it ensures data integrity and consistency before, during, and after migration.

The software will be designed to test and measure:

- **Downtimes**: The periods when the service is unavailable during the migration process.
- **Deployment Latencies**: The delays in getting a container fully operational in a new location can vary depending on the complexity and type of the application.

The research component of the project will delve into different migration scenarios:

- **Cold Migration**: Where the container is stopped before being moved.
- **Live Migration**: Where the container is moved while it is still running, aiming for zero downtime.
- **Warm Migration**: Where the container is paused, transferred, and then resumed, aiming to minimize downtime.
- **Application-Level Migration**: The application within a container is transferred to a new container instance without moving the original container itself.

The project will build upon the CRIU tool. CRIU (Checkpoint/Restore In Userspace) is an open-source software tool for the Linux operating system that enables freezing a running application (or part of it) and checkpointing its state to disk as a collection of files. Then, the application can be restored from its checkpointed state on the same or a different host.

The study, aims to utilize two different scenarios:

- **Stateless Application Migration**: Stateless apps do not retain data or session information between requests. Migration is generally straightforward because any application instance can handle the request; there's no need to consider data consistency or user session data during the migration.
- **Stateful Application Migration**: Stateful apps maintain data or state across sessions and requests. Migration must include transferring this state information to the new environment to ensure continuity and data integrity, making the process more complex and sensitive to handle.

This study will aim to produce actionable insights into the optimal strategies for container migration tailored to various application types and workload demands within Kubernetes ecosystems.

The core implementation features include:

1. Deployment of Kubernetes clusters and exploration of Kubernetes API.

2. Developing a custom API to interact with Kubernetes API and integration with CRIU. 

3. Develop a set of experiments to demonstrate migrations of basic stateless and stateful applications.
   * Stateless: Migration of APIs / Statefull: Migration of a shopping cart

4. Deploying prototype applications using different resources and testing on various demands.

5. Develop experimental analysis to demonstrate combinations of downtimes and latencies to various migration scenarios (cold/live/warm and application-level).

6. Develop documentation and critical analysis through comparisons.

### Video description

Watch the following project description video.

* {Link to be provided soon}

### Support and resources

*	Access to the Google Cloud Platform or Amazon Web Services.
*	Programming seed repositories and other resources to start your developments.
*	Development support and advice by expert data scientists.

### Project learning outcomes and skills

*	You will learn how to integrate custom software with `Kubernetes` and build microservices.
*	You will learn how to use and customize state-of-the-art software tools such as CRIU.
*	You will learn how to use popular cloud platforms to deploy software and customise `Kubernetes`.
*	You will develop skills in REST API development using `Node.js` and `Go`.
*	You will learn how to use modern DevOps pipelines for software development.

### Difficulty level

*	**5/5** - *My most challenging project*

>This is a challenging project with data-science-related developments. The project implementation will be organized into features - **not all features need to be developed for this project**.

### Resources:

1. [Checkpoint/Restore In Userspace (CRIU)](Checkpoint/Restore In Userspace (CRIU))
2. [CRIU GitHub project](https://github.com/checkpoint-restore/criu)
3. [Article on CRIU - Checkpoint/Restore in user space by RedHat](https://access.redhat.com/articles/2455211)
4. [Checkpoint and Restore in Kubernetes with CRIU | Talks at DeepSource](https://www.youtube.com/watch?v=JEcLoJjH3Ls)
5. [Terraform documentation](https://developer.hashicorp.com/terraform?product_intent=terraform)
