# system-design-Handbook

## CAP Theorem 
(Consistency, Availability, Partition Tolerance)

The CAP theorem states that a distributed database system can only guarantee two out of the following three properties at a given time:

- ##### Consistency (C)
Every read receives the most recent write or an error, ensuring data uniformity across all nodes.

- ##### Availability (A)
Every request (read or write) receives a response, even if it might not reflect the most recent write.

- ##### Partition Tolerance (P)
The system continues to operate even if network partitions (communication breakdowns) occur between nodes.

#### Key Insights on CAP Theorem in Databases

##### Partition Tolerance Is Mandatory ? ( BACK UP )

Imagine a distributed system as a network of computers working together. Sometimes, parts of this network might get disconnected, like a power outage affecting a few computers. This is called a network partition.

A reliable distributed system must be able to function correctly even when such partitions happen. This means it needs to be Partition Tolerant. It's like having a backup plan in case of a power outage – the system keeps working, even if some parts are down.

thats why Partition Tolerance is mandatory for a distributed system to be reliable.

now partition Tolerance is essential, in the event of a network partition or failure , the system must choose between: Consistency  & Availability

Consistency (C): Ensuring that all nodes have up-to-date, uniform data, even if it means some requests might fail.
Availability (A): Ensuring that every request is served, even if the data served is not the latest.




## Client-Server Architecture

### Client:
For example, your phone acts as the client. When you search for something on YouTube or a web browser and click on it, this sends a request to the server.

### Server:
The server is the system behind the application that processes incoming requests. It doesn't know what the client wants until it receives the request. Once the request arrives, the server responds accordingly.

### Advantages of Client-Server Networks:
Centralized Data: All data is stored on the server, making it easy to manage.
Security: Resources and access are centrally controlled, improving security.
Performance: The server enables faster sharing of resources, enhancing overall system performance.
Scalability: You can easily add new features (nodes) to the network or application at any time.

### Disadvantages of Client-Server Networks:
Traffic Congestion: When many clients send requests at once, the server can become overloaded.
Server Downtime: If the server is down, client requests cannot be fulfilled.
Resource Availability: Sometimes, resources exist on the server but are not available on the client.

## Microservice Architecture

Microservices perform specific business functions. Each microservice can be developed, deployed, and scaled independently. They can be written in various programming languages and frameworks, functioning as self-contained mini-applications.


### example ( payment app )

User authentication and authorization

Payment Gateway Microservice

Transaction Management Microservice

Wallet Microservice

Notification Microservice

Reward and Cashback Microservice

Merchant Management Microservice

Customer Support Microservice


#### How Microservices Work?

Service Interaction: Microservices interact via APIs, facilitating standardized information exchange and integration.

Feature-Oriented Design: Applications are divided into specific features, such as user authentication or product management, allowing for specialized and focused development.

Technology Agnosticism: Different technologies can be used for each service, enabling teams to choose the best tools for their specific needs.


### Main Components of Microservices Architecture

#### Microservices:

Represent specific business functions or features, each focusing on a distinct capability.

#### API Gateway:

Manages requests, handles authentication, and routes requests to the appropriate microservices.

#### Service Registry:

Tracks the addresses of all microservices, enabling dynamic discovery and communication among services.

#### Load Balancer:

Distributes incoming traffic across multiple services to prevent any single microservice from being overwhelmed.

#### containerization:

Tools like Docker encapsulate microservices and their dependencies.
Orchestration tools like Kubernetes manage deployment, scaling, and monitoring.

#### Message Broker:
Facilitates communication between microservices, ensuring reliable message exchange.

#### Database:
Each microservice typically has its own database, promoting data autonomy and allowing for independent management and scaling.

#### Caching:
Frequently accessed data is stored in a cache close to the microservice, improving performance by reducing repetitive queries.

#### Fault Tolerance:
Ensures the system maintains overall functionality even when individual services fail.

## microserivce vs monlithic 

### microserivce

- Decomposed into small, independent services.

- Small,cross-functional teams for each microservice.

- Independent scaling of individual services.

- Independent deployment of services.

- Faster development and deployment cycles.

- Easier to adopt new technologies for specific services.

- Easier maintenance of smaller, focused codebases.

### monlithic 

- Single, tightly integrated codebase.

- Larger, centralized development team.

- Scaling involves replicating the entire application.

- The whole application is deployed as a single unit.

- Resources are allocated based on the overall application’s needs.

- Limited flexibility due to a common technology stack.

- Maintenance can be complex for a large, monolithic codebase.

#### How to move from monolithic to microservices?


1) ##### Identify Components :-

- Analyze the monolithic application to identify its components.

- Determine which parts can be transitioned into independent microservices.



2) ##### Break Down Business Functions:-

- Decompose the monolith into specific business functions, such as user management, payment processing, or notifications.

- Focus on separating areas with minimal dependencies first.


3) ##### Implement the Strangler Pattern

- Gradually replace parts of the monolithic application with microservices.

- Route traffic to the new microservices while keeping the remaining monolith operational until full migration is complete.


4) ##### Establish Clear APIs and Contracts

- Define well-documented and standardized APIs for each microservice.

- Ensure these APIs facilitate seamless communication between services.

5) ##### Create CI/CD Pipelines

- Set up continuous integration and continuous deployment pipelines.

- Automate testing and deployment processes to enable faster and more reliable releases.


6) ##### Introduce Service Discovery

- Implement mechanisms for dynamic service discovery, allowing microservices to locate and communicate with each other.

- Use tools like Consul, Eureka, or Kubernetes for service discovery.


7) ##### Manage Cross-Cutting Concerns

- Ensure consistent handling of security, authentication, logging, monitoring, and other cross-cutting concerns across all microservices.

- Use shared libraries or middleware to standardize these practices.


8) ##### Take an Iterative Approach

- Start small and expand gradually.

- Continuously refine and improve your microservices architecture based on feedback, performance metrics, and changing business requirements.


## Design Patterns of Microservices

### API Gateway Pattern

The API Gateway serves as a single point of entry for all client requests and provides several essential functions. 
It simplifies communication between clients (e.g., devices or applications) and the underlying microservices by hiding the complexities of multiple services behind a unified interface. Additionally, it handles tasks like authentication, logging, and rate limiting, making it a crucial component of microservices architecture.

#### Characteristics of an API Gateway

##### 1) Routing and Load Balancing:

An API Gateway distributes incoming requests across multiple service instances, enabling load balancing. This ensures high reliability and scalability.

##### 2) Protocol Translation:

It can convert HTTP request messages into other formats (e.g., gRPC) to communicate with backend services that use different protocols.

##### 3) Request Transformation:

API Gateways can transform requests and responses according to the specific requirements of the backend services.

##### 4) Caching:

By caching frequently accessed data, API Gateways can reduce latency and improve response times. Stored data can be retrieved and served to clients without hitting the backend services repeatedly.



### Benefits of Using an API Gateway in Microservices

##### Centralized Management:
Simplifies the management of multiple microservices by consolidating tasks like logging, monitoring, and authentication.

##### Scalability:
Enhances scalability by distributing requests across multiple service instances efficiently.

##### Caching:
Improves performance by reducing the load on backend services through effective caching mechanisms.

##### Improved Security:
Provides an additional layer of security by enforcing authentication, authorization, and rate limiting at the gateway level.

### API Gateway Patterns 

#### 1) Gateway Aggregation
The practice of combining or consolidating multiple APIs into a single interface or endpoint.

Example:
Imagine you want to buy shoes from Nike. To integrate various functionalities like:

- New product listings
- Payment processing
- Order tracking
- User authentication

You can aggregate APIs from different providers (e.g., Product Catalog API, Payment Gateway API, Shipping and Logistics API, and User Authentication API) into a single interface within your e-commerce platform.

Instead of directly interacting with each provider's API separately, this approach offers a unified and seamless experience.

##### Advantages:

- Simplifies client integration.
- Minimizes network round-trips, improving performance.
- Reduces backend load.






























![system-design_page-0001 (1)](https://github.com/user-attachments/assets/2619371b-b8ea-4521-9cc6-ef24b106de21)



