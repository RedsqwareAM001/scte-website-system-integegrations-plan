[< Return to Home](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/)

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

## Systems Integration via Messaging Queue(s)
In the proposed microservices architecture, we can fullfill a user story by employing a single service or by uttilizing multiple services at the same time. When multiple services are in play, we can primarily perform a task by either:
* Rest Synchronous Model
   
   With rest synchronous model there are considerable problems like you might not able to respond in very short time as there could be huge amount of requests, and for each request you are making external call synchronously, it blocks current thread too until it get response from external service. There might be cases where external service is down. You are not sure on external dependency of messaging service. It might cause delay in response.

* Messaging based asynchronous model

  With messaging based asynchronous model, events pertaining to software system are pushed to queue/topic and, respond back to the users. That allows multiple receivers/services to process these messages asynchronously, which can signigicantly improve perfromance of the software system. If the messaging queue management system is run on multiple nodes, the intrgrations system become highly available, more fault tolerant and scalable ensuring seemless communication between services in the software system. Once message is pushed to the queue, the producer service/process can go back to serve user resulting in a non-blocking behaviour. Consumers/receivers can read messages from the queue and, process it asynchronously.

![Sync vs Async](https://www.oreilly.com/library/view/cloud-native-programming/9781787125988/assets/ee12981f-07fd-4efe-b986-a5914fb37798.png)
###### Diagram Credit: Cloud Native programming with Golang by Martin Helmich, Mina Andrawos, REST web services and asynchronous messaging. [Oreilly.com](https://www.oreilly.com/library/view/cloud-native-programming/9781787125988/043c95cd-6796-4123-969e-9b91b548aa9d.xhtml)

***

### Message Queues
A message queue provides an asynchronous communications protocol, a system that puts a message onto a message queue does not require an immediate response to continuing processing. Email is probably the best example of asynchronous messaging. When an email is sent can the sender continue processing other things without an immediate response from the receiver. This way of handling messages decouple the producer from the consumer. The producer and the consumer of the message do not need to interact with the message queue at the same time.

### A few use cases
* Sending user notification (via email/sms/push)
* Updating user status across the system upon completiting a certain course/certfication
* Aggregating and generating reports
* Tracking user transactions
* Tracking user activity
* Aggregating company specific data
* Media management
* Updating seach indexes in the software system

## Benefits of using message queues for Systems Integration
* __Decoupling__

   It’s extremely difficult to predict, at the start of a project, what the future needs of the project will be. By introducing a layer in between processes, message queues create an implicit, data-based interface that both processes implement. This allows you to extend and modify these processes independently, by simply ensuring they adhere to the same interface requirements.

* __Redundancy__

   Sometimes processes fail when processing data. Unless that data is persisted, it’s lost forever. Queues mitigate this by persisting data until it has been fully processed. The put-get-delete paradigm, which many message queues use, requires a process to explicitly indicate that it has finished processing a message before the message is removed from the queue, ensuring your data is kept safe until you’re done with it.

* __Scalability__

   Because message queues decouple your processes, it’s easy to scale up the rate with which messages are added to the queue or processed; simply add another process. No code needs to be changed, no configurations need to be tweaked. Scaling is as simple as adding more power.

* __Resiliency__

   When part of your architecture fails, it doesn’t need to take the entire system down with it. Message queues decouple processes, so if a process that is processing messages from the queue fails, messages can still be added to the queue to be processed when the system recovers. This ability to accept requests that will be retried or processed at a later date is often the difference between an inconvenienced customer and a frustrated customer.

* __Delivery Guarantees__

   The redundancy provided by message queues guarantees that a message will be processed eventually, so long as a process is reading the queue. On top of that, IronMQ provides an only-delivered-once guarantee. No matter how many processes are pulling data from the queue, each message will only be processed a single time. This is made possible because retrieving a message “reserves” that message, temporarily removing it from the queue. Unless the client specifically states that it’s finished with that message, the message will be placed back on the queue to be processed after a configurable amount of time.
* __Ordering Guarantees__

   In a lot of situations, the order with which data is processed is important. Message queues are inherently ordered, and capable of providing guarantees that data will be processed in a specific order. IronMQ guarantees that messages will be processed using FIFO (first in, first out), so the order in which messages are placed on a queue is the order in which they’ll be retrieved from it.
* __Buffering__

   In any non-trivial system, there are going to be components that require different processing times. For example, it takes less time to upload an image than it does to apply a filter to it. Message queues help these tasks operate at peak efficiency by offering a buffer layer–the process writing to the queue can write as fast as it’s able to, instead of being constrained by the readiness of the process reading from the queue. This buffer helps control and optimize the speed with which data flows through your system.
* __Understanding Data Flow__

   In a distributed system, getting an overall sense of how long user actions take to complete and why is a huge problem. Message queues, through the rate with which they are processed, help to easily identify under-performing processes or areas where the data flow is not optimal.
* __Asynchronous Communication__

   A lot of times, you don’t want to or need to process a message immediately. Message queues enable asynchronous processing, which allows you to put a message on the queue without processing it immediately.   For long-running API calls, SQL reporting queries, or any other operation that takes more than a second, consider using a queue.   Queue up as many messages as you like, then process them at your leisure.


## Popular Messaging Queue Solutions
* [IBM MQ](https://www.ibm.com/products/mq)
* [RabbitMQ](https://www.rabbitmq.com/)
* [AWS SQS](https://aws.amazon.com/sqs/)
* [ActiveMQ](http://activemq.apache.org/)
* [Apache Kafka](https://kafka.apache.org/)

## Message Queue Management System for SCTE Software System
For SCTE Software System, we highly recommend __AWS SQS__. Let's look at some of the factors we considered for choosing __AWS SQS__.
* Unmanaged Service, NO administrative overhead

   Unlike other populare messaging queues, SQS does not need an administration overhead. AWS manages all ongoing operations and underlying infrastructure needed to provide a highly available and scalable message queuing service. With SQS, there is no upfront cost, no need to acquire, install, and configure messaging software, and no time-consuming build-out and maintenance of supporting infrastructure. SQS queues are dynamically created and scale automatically so you can build and grow applications quickly and efficiently.

***

[< Return to Home](https://redsqwaream001.github.io/scte-website-system-integegrations-plan/)
