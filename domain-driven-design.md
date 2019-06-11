## Motivation
- Developers are too wrapped up with technology and trying to solve problems using technology rather than careful design and thought
- Database is given too much priority, solutions are centered around database and data model rather than business processes and operations
- Differences between mental model that the business owns and the software that developers deliver because developers dont give enough consideration to naming objects and operations
- Housing busness logic in interface or persistence components or persistence operations between business logic
- Locking database queries
- Wrong abstractions to address current and imagined future needs, over-generalizing solutions

## Spaces

**Problem Space**

* perfrom high-level strategic analysis and design within constrains for a given project.
* discuss project drivers, goals and risks
* Context Maps work very well in problem space discussions

**Solution Space**

* implement the solution that problem space discussions identify as *Core Domain*

## Strategic Design
- **Bounded Context** 
- segregate domain models and create ubiquitous language
- Semantic contextual boundary (problem space to solution space) within which each component of the software model has a specific meaning, plays a specfic role and performs specific things
- Core Domain
- Subdomains
- Context Mapping - integrate multiple bounded contexts, define relationships and technical mechanisms

## Tactical Design

## Glossary
- Bounded Context
- Domain Activities
  - Command
    - A command can be accepted/acknowledged or rejected; don’t consider commands to have a response
  - Query
    - A Query is a synchronous call and expected to respond immediately with the result
  - Event
 - Aggregate
  - Various pieces of data associated with an aggregate root
  - Aggregates are always wroken upon in context of aggregate root
 - Aggregate roots
  - An entity that will be retrieved based on a lookup ID
  - Commands will be directed to the aggregate root and events emitted by the aggregate root
  - The aggregate root can also subscribe to events from other aggregate roots
  - form a consistency and transactional boundary around aggregates
 
- Event Sourcing
Event sourcing is based around logical operations (compared to physical operations), similar to bookkeeping in an accounting context. In an event-sourced system we maintain state by collecting events about a specific entity, persisting those events to a journal, and then providing a read model about that entity in order to extract relevant knowledge based on the events. The read model is simply a summation of events about an aggregate root from the beginning of time until the read is executed.

Data is not modified or deleted. New events are recorded in a journal (similar to a ledger in accounting), and the current values of entities can be read by summing all events.

**Steps**

1. A command is received by an entity.
1. The entity checks to see if the command can be applied
1. If the command can be applied:
   1. The entity creates an event
   1. The entity changes state based on the event details
   1. The entity persists the event
   1. The entity publishes the event to a topic
1. If the command cannot be applied:
   1. The entity creates a failure event
   1. The entity publishes the failure event to a channel
   
**Aspects of an Entity**
- API
- State
- Behavior

**Types**
- Command type
- Event type
- State type

## Domain-Driven Architecture Diagrams

**System Context Diagram**
- high level overview of users, use-cases, internal systems, external dependencies
- reinforce our shared model by using ubiquitous language to list users, names of systems, and interactions

**Bounded Context Map**
- upstream/downstream relationships among bounded contexts
- team relationships, communication patterns, integration strategies, and cross-team dependencies
- marking Anti-Corruption layers (ACL)

**Bounded Context Deployables**
- services in a bounded context, interactions, technology choices etc

**Business Use Cases**
- end-to-end business use case as events flow through different bounded contexts

**Domain Concept**
- business rules, policies and workflows

## Maintaining coceptual integrity of the domain model
- an agile process that emphasizes frequent feedback from users and domain experts,
- the availability of real domain experts and a creative collaboration with them,
- a single and shared version of the model (in the application and test code) precisely defined in terms of the Ubiquitous Language, and
- an open and transparent environment that promotes learning and exploration.

## Readings
- [X] [DDD & Event Driven Systems in Java](https://developer.ibm.com/tutorials/reactive-in-practice-8/)
- [X] [Domain-Driven Architecture Diagrams](https://medium.com/nick-tune-tech-strategy-blog/domain-driven-architecture-diagrams-139a75acb578)
- [ ] [Modelling Reactive Systems with Event Storming and Domain-Driven Design](https://blog.redelastic.com/corporate-arts-crafts-modelling-reactive-systems-with-event-storming-73c6236f5dd7)

## Courses
- [ ] [Cognitive Class - Reactive Architecture: Domain Driven Design](https://cognitiveclass.ai/courses/reactive-architecture-ddd/)
- [ ] [Cognitive Class - Reactive Architecture: Introduction to Reactive Systems](https://cognitiveclass.ai/courses/reactive-architecture-introduction/)
- [ ] [Cognitive Class - Reactive Architecture: Advanced](https://cognitiveclass.ai/learn/reactive-architecture-advanced/)


## Books
- [ ] Event Storming by Alberto Brandolini
- [ ] Domain-Driven Design Distilled by Vaughn Vernon
- [ ] Domain-Driven Design: Tackling Complexity in the Heart of Software by Eric Evans
- [ ] Patterns, Principles, and Practices of Domain-Driven Design by Scott Millett

## Resources
- [DDD Community](http://dddcommunity.org/)
- [Github - awesome-ddd](https://github.com/heynickc/awesome-ddd)
- [InfoQ - DDD Content](https://www.infoq.com/domaindrivendesign/)
