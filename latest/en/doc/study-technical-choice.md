# Study technical choice

During this phase, you have to consult all technical expert : 

- Developer (language, framework, etc)
- Tech Lead
- Architect 
- VP engineering 
- DevOps
- Sys admin  
- Qa Team

![](https://images.ctfassets.net/82ripq7fjls2/2eVb2qmTZznSW5kMFI3f66/59e4f19a97c67fdad5d06ec90d18d0f6/2019_06_DevOps-Diagram.png?w=800&fit=fill&f=center&q=95&fm=webp)

## Architecture design

### Hexagonal Architecture

Layer's approach is very interesting to isolated responsibility in your application.
One most famous pattern in this category is Model View Controller aka MVC (input user, store data, etc.).
This Pattern is good, but it's not enough to isolated technical logic from business logic.

The idea of Hexagonal Architecture is to put inputs and outputs at the edges of our design. 
Business logic should not depend on whether we expose a REST or a GraphQL API, and it should not depend on where we get data from — a database, a microservice API exposed via gRPC or REST, or just a simple CSV file.
The pattern allows us to isolate the core logic of our application from outside concerns. Having our core logic isolated means we can easily change data source details without a significant impact or major code rewrites to the codebase.
One of the main advantages we also saw in having an app with clear boundaries is our testing strategy — the majority of our tests can verify our business logic without relying on protocols that can easily change.

![](https://static.packt-cdn.com/products/9781839211966/graphics/B15547_02_04.jpg)
![](https://miro.medium.com/max/1400/1*NfFzI7Z-E3ypn8ahESbDzw.png)

Pros : 
- Testability improvement
- Maintainability improvement
- Flexibility
- Application immune to technology evolution
- Delay technological decisions

Cons : 
- Complexity
- Build process performance
- Indirection and Mappings

### Event Driven

An event-driven architecture collects meaningful events, distributes them to the appropriate places, makes informed decisions, and takes effective action, all in real time. It allows you to provide the responsive experience your customers expect in a secure, reliable, scalable manner. From open source event streaming with Apache Kafka and Apache Pulsar to contextual and stream event processing, TIBCO has been at the forefront of event-driven thinking for many years, and we can help you take full advantage of the events that occur in your business everyday.

An extension is Event Sourcing, usually we have a storage system who record the latest state of an object. If we need to store
all change on object lifecycle we have to store all event that change object state.

![](https://hazelcast.com/wp-content/uploads/2021/12/20_EventDrivenArchitecture.png)

Pros :
- Better realtime user experiences
- Loose coupling between API producers and consumers
- Superior handling at scale
- Extensibility and resilience
- More consistent handling of concurrency
- Optimized network resource usage
- Mature tech

Cons :
- Increased complexity for API provider
- Ambiguity In API analytics
- Limited governance, standardization, and developer experience/support

### Microservice

By definition a microservice, it's an app with a dedicated database focus on limited business functionality.
We can use Hexagonal architecture or event driven in our microservice.
Microservice allow easily to scale on demand (up, down).
It's demand to be focus on communication between service (api), workflow rollback and security.

![](https://docs.oracle.com/fr/solutions/learn-architect-microservice/img/monolithic_vs_microservice.png)

Pros :
- Scaling up becomes easier
- Leads to Improved Fault Tolerance
- Ease of understanding of the codebase of the software system
- Gives you scope for experimenting with different technologies
- Independent Deployment of each module

Cons :
- Increased Complexity of Communication Between the Services
- Requires More Resources
- Global Testing and Debugging is Difficult
- Not Practical for Small Applications
- Relatively Complex Deployment

## Api communication

### REST

REST stands for REpresentational State Transfer and is an architectural style for network communication between applications, which relies on a stateless protocol (usually HTTP) for interaction.
In REST APIs, we use the HTTP verbs as actions, and the endpoints are the resources acted upon. 
We’ll be using the HTTP verbs for their semantic meaning:
- GET: retrieve resources 
- POST: create resources 
- PUT: update resources 
- PATCH: update resources
- DELETE: delete resources

![](https://www.redhat.com/architect/sites/architect/files/styles/embed_large/public/2020-09/Figure1_0.png?itok=yJKdvmYm)

Level of rest
- Level 1 – Resources
- Level 2 - HTTP Verbs 
- Level 3 - Hypermedia Controls (hateoas for business sem)

```json
{
  "booking": {
    "id": "KNDJT2A23A7703818",
    "links": [
      {
        "href": "/flights/booking/KNDJT2A23A7703818",
        "rel": "flights",
        "type" : "GET"
      },
      {
        "href": "/options/booking/KNDJT2A23A7703818",
        "rel": "options",
        "type" : "GET"
      },
      {
        "href": "/payment/booking/KNDJT2A23A7703818",
        "rel": "payment",
        "type" : "GET"
      }
    ]
  }
}
```

For documentation, you have to use a tools like OpenApi specification (Swagger)

![](https://octoperf.com/img/blog/jmeter-rest-api-testing/workspaces-api.png)

Pros :
- Fast development speed (CRUD)
- Better for Caching (HTTP)
- Manage File Upload (multiple type json, xml, binaire, json-hal)
- Restfull with hateoas for business semantic 

Cons :
- No standards
- Tied to HTTP (slow with TCP on HTTP1, waiting HTTP2/3)
- Bad for schema exposure (manually doc)

### GraphQl

At its core, GraphQL is a language for querying databases from client-side applications
A GraphQL server provides a client with a predefined schema – a model of the data that can be requested from the server. In other words, the schema serves as a middle ground between the client and the server while defining how to access the data.

Based on the graph data modeling with the schema at its core, GraphQL has three primary operations:

1. Query for reading data 
2. Mutation for writing data 
3. Subscription for automatically receiving real-time data over time.

![](https://i.imgur.com/z9VKnHs.png)
![](https://www.redhat.com/architect/sites/architect/files/styles/embed_large/public/2020-09/figure2.png?itok=tIx4bLW-)
![](https://content.altexsoft.com/media/2019/03/word-image-6.png)

Pros :
- Ecosystem (Apollo, Gateway, Microservice) 
- Good for select data properties with nested data
- Good fit for complex systems and microservices
- GraphQL for read but REST for writes.
- Fetching data with a single API call
- Validation and type checking out-of-the-box
- Good for schema exposure (auto generated doc)

Cons :
- Performance issues with complex queries
- Bad caching (create a unique hash id for CDN)
- Overkill for small applications
- File uploading
- Takes a while to understand

### RPC

Remote Procedure Call (RPC) is a protocol that provides the high-level communications paradigm used in the operating system. RPC presumes the existence of a low-level transport protocol, such as Transmission Control Protocol/Internet Protocol (TCP/IP) or User Datagram Protocol (UDP), for carrying the message data between communicating programs. RPC implements a logical client-to-server communications system designed specifically for the support of network applications.

It's existing multiple implementation : 
- xml-rpc (SOAP)
- json-rpc
- gRPC
- avroRpc

![](https://blog.logrocket.com/wp-content/uploads/2020/04/gRPC-server-1536x991.png)
![](https://www.oreilly.com/library/view/grpc-up-and/9781492058328/assets/grpc_0101.png) 

Pros :
- Perf with TCP (based on HTTP2)
- Good for managing action
- Good for type definition
- Good for schema exposure (auto doc)

Cons :
- Careful with volume payload 
- Highly coupled Front / Back (versioning)
- Overkill for small applications
- Not compliant on all browsers

### Sum up :  REST, GraphQL, gRPC

![](https://uploads-ssl.webflow.com/5eebed4f86986c7148161d11/5f7612fd3830fc0613bc2855_Copy-of-Sensedia-API-Days-Madrid-2019.png)
![](https://uploads-ssl.webflow.com/5eebed4f86986c7148161d11/5f7612fda96d09acb3def890_Copy-of-Sensedia-API-Days-Madrid-2019-1.png)

### Message broker

Message broker is a component used for applications to communicate with each other. It provides the exchange of information between applications by transmitting messages received from the producer to consumer.

- Producer: who create the message or event
- Consumer: receives messages from the queue and executes actions
- Exchange: forward messages to the required queues according to the specified rules

Storage : Kafka

Schema registry : Confluent, Apicurio

Message Schema : Asyncapi

Message format specification : https://github.com/cloudevents/spec

![](https://miro.medium.com/max/1302/0*p05ch77ERQOpj2GN.png)

Pros : 
- Scalable systems
- Loosely coupling application (microservice)
- Very high in terms of using resources more efficiently (async)

Cons : 
- Hard for Policy retry (define a unique id)
- Be careful when ordering on multiple consumer (example : bank account input)
- Bad for schema exposure (manually with tools)

## Database

- Hierarchical databases : Filesystems, DNS, LDAP directories
- Network databases : IDMS
- Relational databases : MySQL, MariaDB, PostgreSQL, SQLite
- NoSQL databases :
  - Key-value databases : Redis, memcached, etcd
  - Document databases : MongoDB, RethinkDB
  -	Graph databases : Neo4j, JanusGraph, Dgraph
  -	Column-family databases : Cassandra, HBase
  -	Time series databases : OpenTSDB, Prometheus, InfluxDB, TimescaleDB
- NeSQL databases : MemSQL, VoltDB, Spanner, Calvin, CockroachDB, FaunaDB, yugabyteDB
- Multi-model databases : ArangoDB, OrientDB, Couchbase

## Programming Languages

Firstly, you should ask a lot of questions : 

- What is the environment for the project (web, mobile, etc)?
- Any specific requirement of libraries, features, and tools for the programming language?
- What are some important constraints of this project? Time, budget, resources?
- What’s the performance consideration and is the languages suitable to accommodate this performance?
- What’s the security consideration and do we need to use any third-party tool?

For example, Object-oriented languages are the best suitable for web applications. For Android application, Java or Kotlin is good, for system programming middle level languages such as C can be used.

- Front End Development: JavaScript, HTML, and CSS
- Backend Development: Python, Java, C# or JavaScript
- 2D Game development: JavaScript or C#
- 3D Game Development: C# or C++
- Data Science/Machine Learning/Analytics: Python, R, Clojure, Julia
- Math & Scientific Computing: Matlab, FORTRAN, ALGOL, APL, Julia, R, C++
- Big Data: Java, Python, R, Scala, Clojure
- Operating Systems: C, C++
- Distributed System: C, Go, Rust


### Evaluation

|Criteria|Java|Php|Javascript|Python|Go|C#|
|:-----|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|
|Popularity|&#9733;&#9733;&#9733;|&#9733;&#9733;&#9733;|&#9733;&#9733;&#9733;|&#9733;&#9733;|&#9733;|&#9733;&#9733;|
|Easy of learning|&#9733;&#9733;|&#9733;&#9733;&#9733;|&#9733;&#9733;&#9733;|&#9733;|&#9733;&#9733;&#9733;|&#9733;&#9733;|
|Readability|&#9733;&#9733;&#9733;|&#9733;&#9733;&#9733;|&#9733;&#9733;|&#9733;|&#9733;&#9733;|&#9733;&#9733;&#9733;|
|Speed of development|&#9733;|&#9733;&#9733;&#9733;|&#9733;&#9733;&#9733;|&#9733;|&#9733;|&#9733;|
|Efficiency|&#9733;&#9733;|&#9733;&#9733;&#9733;|&#9733;&#9733;&#9733;|&#9733;&#9733;|&#9733;&#9733;|&#9733;&#9733;|
|Tools Support|&#9733;&#9733;&#9733;|&#9733;|&#9733;&#9733;&#9733;|&#9733;&#9733;|&#9733;&#9733;|&#9733;|
|Portability|&#9733;&#9733;&#9733;|&#9733;|&#9733;|&#9733;|&#9733;|&#9733;|

## Container and Orchestration

- Images
- Network
- Volume
- Autoscaling or number limit
- Canary testing with feature flipping

## Security

- Think who can attack and prepare backup (communication plan)
- Focus on data (public, private, secret)
- Focus on entry point (authentication and authorization)

## UI

State machine, Web components, Micro-Frontend, Story Book, Feature Fliping/Tours...
