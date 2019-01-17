## Context
The proposed SCTE software system will be a collection of [microservices.](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#microservice)
* A [microservice](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#microservice) can be a standalone [service](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#service) or a collection of services.
* Each [microservice](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#microservice) is developed to serve a specific [business unit](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#business-unit).
* [Business units](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#business-unit) are conceived from [user stories and use cases](https://signature1.basecamphq.com/projects/14315641/file/248138672/SCTE_WEBSITE_USER-STORIES_011219v03.xlsx).
* Each business unit can serve single or multiple [user stories](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#user-story) and [use cases](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#use-case).

## Microservices Integration
While the concept of [microservices](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#microservice), on an abstract level, strongly suggests autonomy and decoupling of services.  How we map each [microservice](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#microservice) determines how autonomous it will be. [Microservices](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#microservice) modeled by bounded contexts or business capabilities are more natural to the autonomy than the ones based on the technical abilities. Mapping services in vertical business slices with their own [databases](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#database) is only the beginning. We still need to integrate them in a way that creates a cohesive experience and share the data between those services. The myriad of interactions between individual services influence integration decisions. Below are the steps that we can take to create a cohesive [software system](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#software-system) with integrated [microservices](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#microservice).

### Loose Coupling and High Cohesion
To ensure autonomy and scale, individual services should be highly cohesive (grouping similar functionalities) and loosely [coupled](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#coupling). The loosely [coupled](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#coupling) systems share well-defined data in the form of messages, and that's all. Such services are not dependent on states, uptimes, performance levels, or technical implementations.
Some services might have a high contingency on other services resulting in back and forth network activity and inept communication. We can merge such services into a single cohesive [microservice](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#microservice). Services that depend too much on other services' data, implementations, and uptimes, could be a symptom of wrong or outdated business boundaries. Businesses always change, which is why we need to revisit boundary assumptions periodically. This ensures we aren't creating too fine-grained services, i.e. [nano-services](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#nano-service). These nano-services tend to have fragmented logic and poor performance. They add a lot of maintenance overhead. Horizontal services that are based on technical implementation rather than business boundaries fall into this pit. 

### Data Sharing between microservices
While [microservices](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#microservice) can always interface on the network layer to share and exchange data, we should use network interfacing only when it's absolutely necessary. [Microservices](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#microservice) can establish connections to [databases](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#database) on the local and remote infrastructure. [Microservice](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#microservice) have the context to process data coming from an external source. Each [microservice](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#microservice) may have its own local data storage system to persist and cache data and avoid continuous sync between [databases](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#database). With this approach, the [software system](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/Glossary#software-system) becomes more fault tolerant and efficient.

## Integration Examples

### Local Network Interface

![Exhibit A](https://s3.amazonaws.com/fallback-assets1/MicroserviceIntegrationExample1.png)

***

### Interfacing via API

![Exhibit B](https://s3.amazonaws.com/fallback-assets1/MicroserviceIntegrationExample2.png)

***

### Interfacing with Database
![Exhibit C](https://s3.amazonaws.com/fallback-assets1/MicroserviceIntegrationExample-Page-2.png)
