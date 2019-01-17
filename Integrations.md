## Context
The proposed SCTE software system will be a collection of microservices.
* A microservice can be a standalone service or a collection of services.
* Each microservice is developed to serve a specific business unit.
* Business units are conceived from user stories and use cases.
* Each business unit can serve single or multiple user stories and use cases.

## Microservices Integration
While the concept of microservices, on an abstract level, strongly suggests autonomy and decoupling of services.  How we map each microservice determines how autonomous it will be. Microservices modeled by bounded contexts or business capabilities are more natural to the autonomy than the ones based on the technical abilities. Mapping services in vertical business slices with their own databases is only the beginning. We still need to integrate them in a way that creates a cohesive experience and share the data between those services. The myriad of interactions between individual services influence integration decisions. Below are the steps that we can take to create a cohesive software system with integrated microservices.

### Loose Coupling and High Cohesion
To ensure autonomy and scale, individual services should be highly cohesive (grouping similar functionalities) and loosely coupled. The loosely coupled systems share well-defined data in the form of messages, and that's all. Such services are not dependent on states, uptimes, performance levels, or technical implementations.
Some services might have a high contingency on other services resulting in back and forth network activity and inept communication. We can merge such services into a single cohesive microservice. Services that depend too much on other services' data, implementations, and uptimes, could be a symptom of wrong or outdated business boundaries. Businesses always change, which is why we need to revisit boundary assumptions periodically. This ensures we aren't creating too fine-grained services, i.e. nano-services. These nano-services tend to have fragmented logic and poor performance. They add a lot of maintenance overhead. Horizontal services that are based on technical implementation rather than business boundaries fall into this pit. 

### Data Sharing between microservices
While microservices can always interface on the network layer to share and exchange data, we should use network interfacing only when it's absolutely necessary. Microservices can establish connections to databases on the local and remote infrastructure. Microservice have the context to process data coming from an external source. Each microservice may have its own local data storage system to persist and cache data and avoid continuous sync between databases. With this approach, the software system becomes more fault tolerant and efficient.

