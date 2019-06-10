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



## Readings
- [X] [DDD & Event Driven Systems in Java](https://developer.ibm.com/tutorials/reactive-in-practice-8/)
- [ ] [Modelling Reactive Systems with Event Storming and Domain-Driven Design](https://blog.redelastic.com/corporate-arts-crafts-modelling-reactive-systems-with-event-storming-73c6236f5dd7)

## Courses
- [ ] [Cognitive Class - Reactive Architecture: Domain Driven Design](https://cognitiveclass.ai/courses/reactive-architecture-ddd/)
- [ ] [Cognitive Class - Reactive Architecture: Introduction to Reactive Systems](https://cognitiveclass.ai/courses/reactive-architecture-introduction/)
- [ ] [Cognitive Class - Reactive Architecture: Advanced](https://cognitiveclass.ai/learn/reactive-architecture-advanced/)


## Books
- [ ] Event Storming by Alberto Brandolini
- [ ] Domain-Driven Design Distilled by Vaughn Vernon
- [ ] Domain-Driven Design: Tackling Complexity in the Heart of Software by Eric Evans

## Resources
- [Github - awesome-ddd](https://github.com/heynickc/awesome-ddd)
