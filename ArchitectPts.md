## Architect Role Overview

In the architect role, on a day-to-day basis, I will be a part of architectural meetings/discussions with the other architects in our organization, and these meetings are about various topics of current interest.

### Responsibilities:

1. Work closely with business to understand the priorities or even help them with the priorities.
2. Interact with business architects to understand core business or features needed.
3. Most of the applications in FedEx were/are in DB2 or iSeries, and there is a huge effort going on to modernize these applications. People have been around for like 30 years, and a lot of features are implemented in Cobol. Business team would help dig into existing stuff and come up with requirements.
4. I have been extensively involved in migrating the on-prem apps to cloud-native micro-services and deploy them in IAAS infrastructure or PAAS infrastructure as needed.
5. One of the key efforts I've been involved in since 2020-2021 is working on Ground Rating Modernization.
6. Understand the difference between pricing and rating.

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
5. Workers
6. Rating Engine
7. Data propagation
8. Push-Pull architecture for pricing
9. Role of Policy Grids for configurable rules

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
