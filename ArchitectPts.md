## Architect Role Overview

In the architect role, on a day-to-day basis:
- I will be a part of architectural meetings/discussions with the other architects in our organization, and these meetings are about various topics of current interest.
- Work closely with business to understand the priorities or even help them with the priorities
- Interact with business architects to understand core business or features needed
- I have been extensively involved in migrating the on-prem apps to cloud-native micro-services and deploy them in IAAS infrastructure or PAAS infrastructure as needed.
- One of the key efforts I've been involved in since 2020-2021 is working on Ground Rating Modernization : I played a key role in architecting a highly decoupled orchestrator-worker pattern by leveraging Kafka queues and topics.

Understand the difference between pricing and rating.

### Responsibilities:

### Ground Rating Modernization (GRM) Infrastructure:

1. **Gateway**
    - Custom filters
    - Canary routes
    - Quarantining
    - Rate limiting
2. **Eureka**
    - Fault tolerance
3. **Adapter**
    - Upstream system: SAPI Details
    - A technical debt module: job is to transform the object into something that we created - RateEvent object
    - This rate event object is forwarded to a queue where the Orchestrator consumes from
    - Capability of Hold and Release:
        - A faster solution was to introduce a column in the database against the shipper number saying HOLD
        - A more robust scalable solution was built in a full stack manner to hold packages, partially release packages as per business needs
4. **Orchestrator**
    - Mapped Diagnostic Context establishment with Spring Aspect
    - Workflow, Workflow_def, Task, Task_def (Input keys, output keys)
    - Topics, queues, database tables for storing the workflow, task details
    - Each task and workflow have statuses like COM, ERR, INPRG, COMWR
5. **Workers**
   - Database Worker, PFI (Publish Invoice), Delivery Area Surcharges, General Ledger
   - Work asynchronously connected with queues and re-publish messages back to the orchestrator topic with a status
   - Based on status message , orchestrator would trigger the next task in the workflow
7. **Rating Engine**
   - Heart of the rating infrastructure
   - I have been involved in the complete design from the scratch and even today I work on it
   - REST Endpoint and easy to manage versions of it, highly scalable
   - Itenary manager : Aggregation, Computation and Disposition
   - Stations 
   - Third party Web Service calls : Dynamic fuel, eDD, Customer Account ( Cash status ), GRD, Location Information ( zipcode is pickup, delivery, postal delivery available)
   - Design of notifications : My contribution was adding something like notifications object to the response object - Now the notifications serve as different purposes -> notify the end users in the UI to display custom messages, notify the downstream systems with agreed upon notification codes which help them verify and tally out things for revenue, now the responses are relayed to one more team in data networks org via Kafka where this is stored in a Cassandra, and further used for data analysis to build dashboards. Instead of json paths , the critical information in the form of codes and plain text helped them to explore options, drove the retry mechanism when we were able to differentiate technical errors like network / service unavailability and others
8. Ground Rating Database
   - Formulas
   - Zones
11. Push-Pull architecture for pricing
    - SQL Triggers in Legacy application triggers an event
    - Based on the event, the data which is modified recently is pulled
    - Pulled data is published to a topic and consumed to udpate the pricing info
13. Role of Policy Grids for configurable rules
    - In the design decision with my previous background with jRules, after a few POC's I decided and pitched for usage of Policy Grid. This is the heart of the rules where we set it up for business to make it as intuitive as possible for business and reflect the changes right away. A few rules that I can quote are like which service allows what functionality like is signature allowed in this service, whats the weight limit, is there any zone specific rules
    - **JRules:** JRules provides a comprehensive set of features for authoring, managing, and executing business rules. It offers capabilities for rule modeling, decision tables, rule templates, rule validation, testing, and deployment.
    - **Policy Grid:** The features and functionality of a Policy Grid solution can vary widely depending on the specific implementation or product chosen. It may include features for defining, analyzing, and enforcing policies across different domains within an organization. This mainly is customizable for Organizations with well defined API's to interact. Scaling is easier in this case as this is an enterprise wide thing and can scale with growing rulesets and user base.
### CI/CD Configuration:

1. IAAS
2. PAAS

### Performance Improvement Approaches:

1. 2 Level Cache Implementation
2. Query optimization by removing JSON data
3. DB retrieval optimization by solving "Thundering herd problems"
4. Optimization of retry mechanism by inclusion of Technical Errors, Business Errors

### Future Enhancements I am Owning:

1. Orchestrator generic solution for multiple domains/organizations
2. Orchestrator mutable keys
3. Sharding of database to handle more load

### Additional Responsibilities:

1. Audit & Logging
2. Access controls
3. Performance monitoring
4. Error Repository Application
5. Compare tool development and enhancements
6. Behavior-driven development emphasis
7. Password Cipher jar creation
