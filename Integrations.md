## Context
The proposed SCTE software system will be a collection of microservices.
* A microservice can be a standalone service or a collection of services.
* Each microservice is developed to serve a specific business unit.
* Business units are conceived from user stories and use cases.
* Each business unit can serve single or multiple user stories and use cases.

## Microservices Integration
While the concept of microservices, on an abstract level, strongly suggests autonomy and decoupling of services. We still need to integrate them in a way that creates a cohesive experience and share the data between those services. How we map each microservice determines how autonomous it will be. Microservices modeled by bounded contexts or business capabilities are more natural to the autonomy than the ones based on the technical abilities.

### Loose Coupling and High Cohesion
To ensure autonomy and scale, individual services should be highly cohesive (grouping similar functionalities) and loosely coupled. The loosely coupled systems share well-defined data in the form of messages, and that's all. Such services are not dependent on states, uptimes, performance levels, or technical implementations.