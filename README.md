# system-design-Handbook



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



































![system-design_page-0001 (1)](https://github.com/user-attachments/assets/2619371b-b8ea-4521-9cc6-ef24b106de21)



