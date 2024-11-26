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
















