# system-design-Handbook

#

# CAP Theorem
- [Key Insights on CAP Theorem](#key-insights-on-cap-theorem-in-databases)

# Performance vs Scalability
- [Performance](#performance)
- [Scalability](#scalability)
- [Trade-off](#trade-off)
- [Latency](#Latency)
- [Throughput](#Throughput)

# 


# Consistency in Distributed Systems
- [Strong Consistency](#strong-consistency)
- [Eventual Consistency](#eventual-consistency)
- [Causal Consistency](#causal-consistency)
- [Weak Consistency](#weak-consistency)

# Availability Patterns
- [Active-Active Pattern](#active-active-pattern)
- [Active-Passive Pattern](#active-passive-pattern)
- [Failover Pattern](#failover-pattern)
- [Replication Pattern](#replication-pattern)
- [Sharding Pattern](#sharding-pattern)
- [Load Balancing Pattern](#load-balancing-pattern)

# CDN
- [How CDNs Reduce Latency and Balance Network Loads](#how-cdns-reduce-latency-and-balance-network-loads)
- [Pull CDN](#pull-cdn)
- [Push CDN](#push-cdn)

# DNS
- [How It Works](#how-it-works)
- [Benefits of DNS](#benefits-of-dns)

#

![system-design_page-0001 (1)](https://github.com/user-attachments/assets/2619371b-b8ea-4521-9cc6-ef24b106de21)

#

## CAP Theorem 
(Consistency, Availability, Partition Tolerance)

The CAP theorem states that a distributed database system can only guarantee two out of the following three properties at a given time

- ##### Consistency (C)
Every read receives the most recent write or an error, ensuring data uniformity across all nodes.

- ##### Availability (A)
Every request (read or write) receives a response, even if it might not reflect the most recent write.

- ##### Partition Tolerance (P)
The system continues to operate even if network partitions (communication breakdowns) occur between nodes.


#

#### Key Insights on CAP Theorem in Databases

##### Partition Tolerance Is Mandatory ? ( BACK UP )

Imagine a distributed system as a network of computers working together. Sometimes, parts of this network might get disconnected, like a power outage affecting a few computers. This is called a network partition.

A reliable distributed system must be able to function correctly even when such partitions happen. This means it needs to be Partition Tolerant. It's like having a backup plan in case of a power outage – the system keeps working, even if some parts are down.

thats why Partition Tolerance is mandatory for a distributed system to be reliable.

now partition Tolerance is essential, in the event of a network partition or failure , the system must choose between: Consistency  & Availability

Consistency (C): Ensuring that all nodes have up-to-date, uniform data, even if it means some requests might fail.

Availability (A): Ensuring that every request is served, even if the data served is not the latest.

but right now consistancy also used in ACID properties so how it differ from cap ?

so in cap theoram consistency => uniformity It ensures that all clients see the most recent state of the system (after a write operation has completed) or indicate an error if the state is not up to date.

on other hand consistency in ACID  properties in any database, consistency refers to the correctness of the database state after a each action is executed.



### Consistency & partition tolerance
when a value is written to one node, the value will be updated in all the other nodes. 
 CP systems may compromise on availability that means some data might not be accessible in the event of a network partition.


### Consistency & availability
prioritize a constant view of the data and ensure the availability is high under normal operating conditions. 
This means that every request made in the system must return either a successful or a failed response.


### Availability & partition tolerance
aims to process queries and provide the most recent available version of information, 
even if it cannot ensure it is completely up-to-date due to network partitioning

# 

## Performance vs Scalability
 
### Performance 

how well a system executes tasks or processes within a given timeframe. 
It encompasses factors like speed, responsiveness, throughput, and resource utilization.


#### Performance Optimization Techniques:

1. Code optimization is best for algorithm-heavy applications because it reduces execution time and minimizes resource consumption.
    However, the downside is that it makes the code more complex and increases development time.
   

2. Caching means storing frequently used data in memory for quick access. It helps decrease the load on the backend and reduces query response time.
   However, it requires additional memory and also increases system complexity

3. Load balancing spreads work evenly across multiple servers. It helps prevent server overload and improves system reliability.
   However, a disadvantage is that it can be expensive to implement and adds network complexity.

4. Parallelism and Concurrency running multiple tasks simultaneously to utilize multiple CPU cores and reduce processing time.

5. Database Optimization Improving database performance through smart design and querying to enhance data retrieval speed and reduce database load.
but increase schema complexity, needing periodic maintenance.

6. Multi-level Caching significantly reduce latency and improve user experience by reducing backend load.

7. Resource Pooling reusing resources instead of creating new ones each time
 reduce creation overhead and improve system efficiency by managing resource consumption.


 
#### Which Technique is Best for Which Situation?

1. Small, computational app → Code Optimization
2. Content-heavy website → Multi-level Caching
3. High-traffic platform → Load Balancing
4. Data processing task → Parallelism
5. Large database system → Database Optimization
6. Resource-intensive application → Resource Pooling


### Scalability:
 system's ability to handle increasing amounts of work or users without compromising performance.

- example to choose between performance & scalability

 Imagine you're building a website. You need to decide whether to focus on making it super fast (performance) or able to handle many visitors at once (scalability).
 
 consider e-commerce startup ( grocery delivery app ) might initially prioritize performance to provide a smooth shopping experience for its customers. 
 As the business grows and attracts more visitors, they may need to shift their focus towards scalability to handle increased traffic and prevent website crashes.



- Fast Website: If you need your website to load quickly for every visitor, prioritize performance.
  For example, a news website with breaking news would benefit from fast load times.
 
- Many Visitors: If you expect a lot of traffic, like a popular online store during a sale, scalability is crucial. 
 The website should be able to handle a sudden surge in visitors without crashing.

#### trade off

 Sometimes, improving performance can make it harder to scale

Find the Right Balance: Aim for a solution that meets your needs without sacrificing too much on either side.

#
 
###  Latency
 it represents  time delay between a request and a response.
- Measuring Unit: Millisecond (ms).
- Represents: How quickly a single request is processed.
- Affecting Factors: Network distance, congestion, processing delays.
- Impact on performance: High latency can lead to a slow and interrupted network experience (e.g., lag in video calls).
- Measure: Latency is a measure of time.
- Importance: Critical for real-time applications like online meeting apps.
- Example: The time it takes for a website to load after you click a link.

#### Latency Types

- Network Latency :
Time for data to travel network infrastructure

- Processing Latency :
Time taken by devices to process incoming data

- Transmission Latency :
Time to push data onto the network medium

- Propagation Latency :
Physical time signal takes to travel

- Strategies to Reduce Latency

Content Delivery Networks (CDNs),
Optimized routing,
Hardware upgrades

# 
  

### throughput 

- repesent How much data is been transferred over a network in a period of time.
- Measuring Unit: Bits per second (bps), Megabits per second (Mbps).
- Represents: How much data is being transferred over a network in a period of time.
- Affecting Factors: Network bandwidth, congestion, packet loss, network topology.
- Impact on performance: Low throughput can lead to slow and inefficient data transfer (e.g., slow file downloads).
- Measure: Throughput is a measure of data transfer.
- Importance: Important for data-intensive applications like file transfer apps.
- Example: The amount of data (in Mbps) that can be downloaded per second from a server.


# 


## consistency in distributed system : 

A distributed system replicates data across multiple servers to achieve improved fault tolerance, scalability, and reliability. Consistency refers to a set of techniques for data storage and management in a distributed system, which can impact the scalability and reliability of the system

### Strong Consistency (Data Uniformity)

Strong consistency is a consistency model in distributed systems that ensures when a write operation is performed on one server, all subsequent read operations on any other server will immediately return the most recently written data.

- Example: Instagram Post

Consider an example with an Instagram post. When a user creates a post on one server, the data is instantly and synchronously replicated to all other servers. Any user attempting to view the post on a different server will see the exact same, most up-to-date version of the post.

- workflow to achieve strong consistency in data replication :

 - The client (or server) executes a write operation against the primary database instance.
 - The primary instance propagates the written data to the replica instances.
 - The replica instances send an acknowledgment signal to the primary instance.
 - The primary instance sends an acknowledgment signal to the client.

- Use Cases:
File Systems
Relational Databases
Financial Services (trading platform,banking)

#

### Eventual Consistency
When a write operation is executed on a server, the immediate subsequent read operations on other servers do not necessarily return the latest written data. 
This pattern typically replicates the data asynchronously across multiple servers.

The eventual consistency pattern is highly available and has low latency, but the disadvantages are that the data can be inconsistent, and there is a chance of data loss or conflicts.

 Workflow to attain eventual consistency in data replication:

- The client executes a write operation against the primary database instance.
- The primary instance sends an acknowledgment signal to the client.
- The primary instance eventually propagates the written data to the replica instances.
  
Use Cases:
URL Shortener
Domain Name System (DNS)


#


### Weak consistency 

is a consistency model where a write operation to a system may not be immediately visible to all subsequent read operations. While this can lead to data inconsistency, it often offers high availability and low latency.

Use Cases:

- Video Games: To ensure smooth gameplay, video game servers often use weak consistency.
 Client-side predictions and server reconciliation are used to handle potential inconsistencies.

- Live Streaming: In live streaming, it's often more important to deliver content quickly than to ensure absolute consistency.
 Weak consistency allows for faster delivery, even at the cost of potential slight delays or inconsistencies.

#

### Causal consistency :  
ensures that related events (cause and effect) are observed in the correct order by all systems. 
However, unrelated events can be observed in any order.
To achieve causal consistency, systems often use a technique called vector clocks. Vector clocks help track the causal relationships between events.

- example 
Think of a comment thread on a social media platform like Reddit. Replies to a specific comment must be seen in the order they were posted. This ensures that the conversation flows logically. However, different comment threads can be displayed in any order, as they are not directly related.

# 


## Availability Patterns  


#### Active-Active Pattern

The active-active pattern is a modern distributed system architecture where multiple application instances are operational simultaneously, serving user requests. 
This pattern ensures high scalability, fault tolerance, and optimal resource utilization. Seamless horizontal scaling supports high-performance requirements.

- Example
  
E-Commerce Platform: Consider an e-commerce website during a Black Friday sale. To handle a surge in user traffic:
Multiple server instances (A, B, C) operate in parallel, distributing incoming user requests via a load balancer.
If one instance fails (e.g., Server B), traffic is dynamically rerouted to Servers A and C without downtime.

# 

#### Active-Passive Pattern

The active-passive pattern prioritizes simplicity and resource efficiency. In this model, one primary instance handles all traffic, while secondary instances remain on standby, 
ready to take over in case of failure. While not as scalable as active-active, it ensures predictable failover with minimal infrastructure costs.

- example :
  
Imagine a customer is chatting with a support agent. Server A (active) handles:
The customer-agent conversation in real time,Storing the chat history in a database.
Server B (passive):
Regularly replicates the chat history from the database.Monitors Server A’s status via heartbeat signals.

If Server A fails, Server B:
Takes over the chat sessions with the most recent replicated state.
Ensures the conversation continues without requiring the customer to reconnect.

# 

#### Failover Pattern

The failover pattern is an essential high-availability strategy in distributed system design. It ensures uninterrupted service during system failures by 
seamlessly transitioning operations to a backup system. Failover is critical for minimizing downtime and ensuring service reliability in mission-critical applications.

- example :
An online payment gateway (Stripe) processes millions of transactions daily.

 -- Setup:
Primary Server: Handles transaction processing.
Backup Server: Stays in sync with the primary server, replicating state and transaction logs.

 -- Process:
Heartbeat monitoring continuously checks the primary server's health.
If the primary server fails, the backup server immediately takes over, ensuring customers can still make payments.
Outcome: Minimal downtime, no transaction loss, and uninterrupted user experience.

# 


#### Replication Pattern

The replication pattern ensures data availability and fault tolerance by maintaining multiple copies of data across different nodes or locations. I
t is fundamental in distributed systems, allowing systems to handle high availability, scalability, and disaster recovery requirements.

- Replication Approaches

 - Synchronous Replication:

Data is immediately written to all replicas, ensuring consistency.
Higher latency due to waiting for confirmation from all nodes.
Example: Financial trading systems where data accuracy is critical.

 - Asynchronous Replication:

Data is written to the primary node first, then asynchronously to replicas.
Offers better performance with potential short-term inconsistencies.
Example: Social media platforms like Instagram, where eventual consistency is accept

Example : 

A cloud storage service (e.g., Google Drive) replicates user files to multiple data centers worldwide.

Setup:
Synchronous replication for files within the same region (ensures immediate consistency).
Asynchronous replication for files across continents (reduces latency).

Process:
A user uploads a document in New York.
The file is immediately replicated to nearby data centers (synchronous).
The file is later replicated to a European data center (asynchronous) for disaster recovery.
Outcome: The user's file is always accessible, even during regional outages.

#

#### Sharding Pattern

Sharding is a powerful data partitioning technique that divides a large dataset into smaller, more manageable segments (called shards). 
Each shard is stored and processed independently, enabling systems to scale horizontally and handle massive amounts of data more efficiently.

**Sharding Strategie**

- Range-Based Sharding: Data is split based on value ranges.
Example: A user database sharded by age group (e.g., 0–18, 19–35, 36–60).

- Hash-Based Sharding: A hash function distributes data evenly across shards.
Example: User IDs are hashed to determine the shard for storing user profiles.

- Directory-Based Sharding: A lookup table maintains data location.
Example: A central directory maps customer IDs to the specific shard storing their orders.

- Geographical Sharding: Data is partitioned based on geographic regions.
Example: A logistics platform stores orders in regional shards (e.g., US, Europe, Asia).


##### Partitioning Techniques:

- Horizontal Partitioning: Splits rows into different shards.
Example: A product catalog divides rows of products alphabetically (A–M in one shard, N–Z in another).
- Vertical Partitioning: Splits columns across databases.
Example: User profile data (e.g., names and emails) in one shard and activity logs in another.
- Functional Partitioning: Groups data by functionality.
Example: Orders and payments data are stored in separate shards.

**Example**
 A global social media platform like Instagram stores user posts in a sharded database to handle billions of records.

Setup:

Hash-based sharding with the user ID as the shard key.
Each shard stores posts for a subset of users.

Process:

A user's post is routed to the correct shard using a hash of their user ID.
Queries for user posts are sent directly to the corresponding shard, minimizing latency.
Outcome: Scalable infrastructure capable of handling millions of concurrent users.


**Choose sharding when**

Your application manages massive datasets (e.g., analytics platforms, social networks).
Horizontal scaling of databases is a priority.


# 


#### Load Balancing Pattern
Load balancing is an architectural strategy that distributes incoming traffic or computational workloads across multiple servers or resources. It ensures optimal resource utilization, system reliability, and scalability.

##### Load Balancer Types:

- Hardware Load Balancers: High-performance physical devices (e.g., F5).
- Software Load Balancers: Solutions like Nginx or HAProxy.
- Cloud-Native Load Balancers: Services like AWS Elastic Load Balancer or Azure Load Balancer.
- Application-Level Load Balancers: Focus on routing based on application-specific criteria.

Example: 
An e-commerce website like Amazon experiences high traffic spikes during sales.

Setup:
Load balancer distributes user requests across multiple servers.
Uses a weighted round-robin algorithm to allocate more traffic to powerful servers.

Process:
User requests for product pages are routed evenly.
Health checks detect server failures, rerouting traffic to healthy servers.
Outcome: A seamless shopping experience even during peak traffic.


**Choose load balancing when**

Your application requires high availability and performance under variable workloads.
Traffic needs to be distributed across multiple servers.


# 

## System availability in Numbers 

Availability: The percentage of time a system or service is operational.

Downtime: The time when a system is unavailable or not functioning.

![availabel](https://github.com/user-attachments/assets/eddd432b-e0f0-497d-8661-efc507514dde)

One Nine (90%): The system is operational 90% of the time, resulting in significant downtime (36.5 days/year).

Two Nines (99%): System downtime drops to 3.65 days annually, improving reliability.

Three Nines (99.9%): Only 8 hours of downtime per year, making the system far more reliable
example : SaaS tools

Four Nines (99.99%): Downtime is reduced to less than an hour per year (52 minutes)
example : Netflix, YouTube

Five Nines (99.999%): Extremely reliable with only 5 minutes of downtime annually
example : trading platforms, banking systems hospital monitoring systems

Six Nines (99.9999%): Near-perfect availability with a mere 32 seconds per year
highly complex & costly ( defence eqipments ) 

# 

## CDN 

A CDN (Content Delivery Network) enhances website performance and ensures content is delivered quickly and efficiently to users worldwide.

Think of the internet as a giant library with books (web content) stored in various locations:

- **Origin Servers**: are like the main library where the original copies of all books are kept. Any new book is added or updated here.
  
- **Edge Servers** are smaller libraries located in different cities. They store copies of the most popular books from the main library. When you need a book, you visit the closest smaller library instead of traveling all the way to the main one, saving time and effort. Similarly, when you access a website, the CDN directs your request to the nearest edge server to ensure faster content delivery.
  
- **DNS Servers** act as the librarians who know the exact location of every book. They guide you to the nearest library (edge server) that has the book you’re looking for.
  

##### HOW CDNs reduce latency and balance network loads:

**Reducing Latency**

Geographic Distribution: CDNs have servers located all around the world. When you request a webpage, the CDN directs you to the nearest server, reducing the distance the data has to travel.
Caching: CDNs store copies of popular content on these servers. So, if many people are requesting the same page, the CDN can quickly serve it from the local server, instead of fetching it from the origin server, which can be far away.

**Balancing Network Loads**

**Load Balancing**: CDNs distribute the traffic across multiple servers. This prevents any single server from becoming overloaded.
**Dynamic Routing**: CDNs intelligently route traffic to the least busy server, ensuring optimal performance.

# 

#### Pull CDN 

Imagine you're in a library. When you ask the librarian for a book, they go to the shelves to fetch it for you. If many people request the same book, the librarian might keep a copy on their desk for quicker access.

A Pull CDN works similarly. When a user requests a webpage or a file, the CDN server checks if it has a copy. If not, it fetches the content from the origin server and stores it locally for future requests. This ensures that the content is always up-to-date.

ideal for websites with dynamic content, such as news websites or e-commerce stores.

#### Push CDN 

In this scenario, the librarian pre-selects popular books and places them on the shelves, ready to be borrowed.

A Push CDN works in a similar way. The content owner proactively uploads the content to the CDN network. The CDN then distributes the content to its servers around the world. This can be faster for initial requests, but it requires more manual effort to keep the content up-to-date.

better suited for static content, such as images, videos, or downloadable files.


#

### DNS 

translates website names into addresses, making the internet a more user-friendly place.

Imagine the internet as a giant city.

Every building (website) has a unique address (IP address), but these addresses are just long strings of numbers, hard to remember.
DNS is like the city's phonebook. It translates easy-to-remember names (domain names) like "google.com" into the actual building addresses (IP addresses) that computers understand.

 **how it works**:

- You want to visit a website, so you type "google.com" into your web browser.
- Your browser doesn't understand names, so it asks a special helper called a DNS server to look it up.
- The DNS server, like a librarian looking through a phonebook, searches for "google.com" and finds its actual address (IP address).
- With the address in hand, your browser can now connect to the website and show you google.com.


**Benefits of DNS**:

- Makes the internet easier to use by remembering names instead of numbers.
- Speeds things up by caching addresses so you don't have to look them up every time.
- Keeps things organized by assigning addresses in a hierarchical way.

more info on https://www.cloudflare.com/learning/dns/what-is-dns/

#


## Event-Driven Architecture

**Concepts**

 - Event Broker : -
An event broker acts as middleware (software, appliance, or SaaS) that routes events between systems using the publish-subscribe messaging pattern. Applications connect to the broker, which accepts events from publishers and delivers them to subscribers. Effective system design and governance ensure events are delivered where needed, with tools like event portals facilitating design, documentation, and governance.

#

 -  Event Portal
   
 adoption of event-driven architecture by enabling the design, documentation, and management of events and applications.

#

 - Topics
   
 hierarchical metadata strings describing the content of events. 

 - Publishers: Send an event once to a specific topic.
 - Subscribers: Register for relevant topics or groups of topics using wildcards.
  This ensures filtering is done by subscriptions, not business logic, and events are efficiently distributed to recipients.

#

- Event Mesh
  
An event mesh is a dynamic infrastructure layer composed of interconnected event brokers. It distributes events among decoupled applications, regardless of their deployment location (on-premises, cloud, or IoT). The mesh dynamically routes events by sharing consumer topic subscriptions across the network, ensuring seamless communication.

#

- Deferred Execution
  
When an event is published, the publisher does not wait for an immediate response. Instead, the event broker persists the event until consumers process it. This deferred execution creates cascades of events, each functionally and temporally independent, but occurring in a sequence.

#

 - Eventual Consistency
 
 events are processed asynchronously, systems cannot guarantee immediate synchronization across stateful entities (e.g., databases, ERPs). However, eventual consistency ensures that, over time, all systems will converge to the correct state.

#

 - Choreography
   
In event-driven systems, coordination among services is achieved through choreography rather than orchestration. Services autonomously respond to incoming events and generate new events, resulting in a “dance” of coordinated actions. This eliminates a single point of failure or bottleneck, as seen in orchestration-based systems.

#

- CQRS (Command Query Responsibility Segregation)
  
CQRS separates the responsibilities of commands (actions like insert/update) from queries (retrieving data). This is particularly useful for scaling, as query operations often outnumber commands. In event-driven architecture, topics contain the action verb, allowing dedicated query services to process relevant topics independently and efficiently.

#

**How EDA Works**

Event Generation: When an event occurs (e.g., a customer places an order), a system generates an event message.   

Event Brokering: The event message is sent to an event broker, which acts as a central hub for distributing events. ( message queue , kafka , rabbit MQ )  

Event Consumption: Interested systems and applications subscribe to specific event topics. When a relevant event is published, the broker delivers it to the subscribers.  

Event Processing: Subscribers process the event and take appropriate actions, such as updating a database, sending a notification, or triggering a workflow


#

## reverse proxy 

reverse proxy is a type of physical or virtual network device, software, or cloud service that plays a crucial role in managing, scaling and securing traffic. It deploys in front of applications, intercepting requests from clients. 

**function** :  direct client requests to the appropriate backend application server

#### operates in three primary stages:

**Origin Server Connection**: The reverse proxy, which acts as a middleman, forwards the client connection request to the application, establishing a connection between the client and the application instance serving the request.

**TCP Three-Way Handshake**: A connection to the reverse proxy is established after a TCP connection protocol is satisfied. In addition, the SSL handshake is followed if the request is an HTTP/S request.

**Connection Request Collection**: The reverse proxy receives incoming requests from clients at the network’s edge.

**example** :
Imagine you're ordering food from a restaurant called "Pizza Palace." Instead of going directly to the kitchen to place your order, you tell a waiter.

waiter
   - Takes your order: You tell the waiter what you want, like a large pepperoni pizza.
   - Checks your order: The waiter ensures your request is clear and valid (e.g., you're not asking for something the restaurant doesn't offer).
   - Passes it to the kitchen: Once everything looks good, the waiter tells the kitchen staff what to make.
   - Delivers the food: When the kitchen finishes your pizza, the waiter brings it to your table.
  
**Instead of users directly contacting the web server (the "kitchen"), they go through a reverse proxy (the "waiter").
The reverse proxy adds safety, checks requests, forwards them to the server, and sends back the response to the user.**
       
#

## Load balancing

 distributing incoming network traffic or application requests across multiple servers or resources to ensure no single server becomes overwhelmed. It optimizes resource use, maximizes throughput, minimizes response time, and ensures high availability and reliability.

implemented at :

Network Level: Distributes traffic at the TCP/UDP level.
Application Level: Distributes traffic based on specific application logic, like HTTP headers or cookies.

**Challenges:**

1) single point of failure : If the load balancer itself fails, the entire system might become unavailable unless there is redundancy.
   
2) latency issue : load balancer adds significant latency to requests, it can degrade the user experience.
   
3) limited scalabilty : poorly designed load balancing solutions might not scale effectively with growing traffic demands.


#### TYPES :

1) Hardware Load Balancers : High performance
Example: F5 Big-IP series, Citrix ADC (NetScaler).

2) Software Load Balancers : flexible 
Examples: HAProxy, NGINX, Apache Traffic Server.

3) Network Load Balancers (NLB) : Operates at Layer 4 (Transport Layer) of the OSI model.
Distributes traffic based on TCP/UDP protocols without inspecting the payload.

4) Application Load Balancers (ALB):Operates at Layer 7 (Application Layer).
Routes requests based on content, such as HTTP headers, paths, or hostnames.

5) . Global Load Balancers: Distributes traffic across multiple geographical regions.
Example: Cloudflare / Serving users with low latency worldwide.

#### TCP load balancer ( network load balancer ) 

known as a Layer 4 Load Balancer, operates at the transport layer (Layer 4) of the OSI model. It is specifically designed to distribute network traffic based on the transport-layer information in the TCP/IP protocol, such as IP addresses and port numbers. 

The main purpose of a TCP load balancer is to distribute incoming traffic evenly across backend servers to optimize resource utilization and ensure availability. uses conncetion based algo round robin & least conncetions 

In multi-region deployments, TCP load balancers can direct traffic to the nearest data center or server, reducing latency and improving user experience.

TCP load balancers can offer session affinity by sticking connections to specific servers based on client information like IP.

**example**
Imagine a busy airport.
 - Passengers (clients): They want to board a flight (access a service).
 - Gates (servers): Where passengers board the flights.
 - Airport Operations (TCP Load Balancer): Doesn't care about your destination
 -  (application data): Just needs to get you to a gate.

 - Next available gate (Round Robin)
 - Gate with fewest passengers (Least Connections)
 - Your assigned gate for this flight (Session Persistence)
 - Hides specific gate locations: You only see the general boarding area.
 - Monitors gate status: If a gate is experiencing delays, they'll redirect passengers.

   #

### Application Load Balancer : 

An Application Load Balancer (ALB) is a specialized type of load balancer operating at the application layer (Layer 7) of the OSI model. Unlike traditional load balancers that work at the transport layer (Layer 4), ALBs provide intelligent traffic management by evaluating the content of incoming requests and routing them based on application-layer information like HTTP headers, paths, cookies, and query strings. This makes ALBs particularly suitable for modern web applications, microservices, and container-based architectures.

 **example**
 
 - Imagine a busy airport with many airlines and flights.
 - Passengers (Clients): Want to reach their destination (access an application).
 - Gates (Servers): Where passengers board their flights (where applications run).
   
 - Airport Operations (Application Load Balancer):
  - Doesn't just send you to any gate: Checks your flight number (host header), destination (path), and even your boarding pass details (cookies) to route you correctly.
  - Handles security checks: Manages security screenings and baggage checks (SSL/TLS termination).
  - Deals with special flights: Accommodates flights with unique needs, like those for groups or cargo (microservices).
  - Monitors gate status: If a gate is delayed, they reroute passengers (health checks).

# 

### Pass-Through Load Balancer

known as  load 4 balancer 
distributes incoming traffic directly to backend servers without modifying them.

**example** : 

Imagine you're at a busy restaurant. Instead of waiting for one waiter to take your order, serve your food, and bring back your payment, a host simply guides you to an available table where you interact directly with the server. That's essentially how a pass-through load balancer works.

**how it works**

Traffic Arrives: When a customer (your computer) wants to access a website or service (like a restaurant), their request (your order) goes to the load balancer (the host).

Choosing the Right Server: The load balancer, using a smart system, decides which server (table) is best suited to handle the request. This ensures no single server gets overwhelmed.

Direct Connection: The load balancer then smoothly connects the customer directly to the chosen server.

Direct Communication: The customer interacts directly with the server, and the server sends the response directly back to the customer, bypassing the load balancer.

**When to Use Pass-Through Load Balancers:**

 - High-speed needs: Perfect for services that require super-fast speeds, like streaming videos or online games.
 - Low latency: Ideal for situations where every millisecond counts, such as financial trading platforms.
 - example : streaming platofrm

#

## Load Balancing Algorithms

**Static Load Balancing Algorithms:**

Static load balancing algorithms distribute workloads based on predetermined rules, without adapting to real-time system variations. Tasks or resources are assigned to servers in a fixed manner, ensuring simplicity but lacking the flexibility to respond to dynamic changes in resource utilization or server availability.

# 

### Round Robin Load Balancing Algorithm: 

The Round Robin algorithm is one of the most straightforward static load balancing techniques. Requests are distributed sequentially across servers in a circular fashion, ensuring each server is assigned a task in turn. While easy to implement, the algorithm does not account for server load, leading to potential imbalances when servers have unequal capacities or varying workloads.

**How It Works**
- Requests are assigned to servers in a cyclic order.
- Once the last server is assigned, the next request is routed back to the first server.
- This process continues in a loop, distributing tasks evenly without considering individual server conditions.


#

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



#

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


#


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































