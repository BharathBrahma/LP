# Have you ever had difficult/challenging situation in your previous job
Perf Improvements
- issue identified in L4 after L3 functional testing
- Not meeting the SLA ( REST API and the Async rating )
- As the lead on the team I was tasked with finding out the places that needs improvememnts
  - Low hanging fruits
  - Caching and cache-hit ratio, ttl etc
  - Database query optimization
  - Connection pooling to separate read and write requests
  - Infrastructure sizing based on the above results in L4. Warming up the containers, and adding more the fleet with beefed up ones
 


Situation:
In a previous role, I was responsible for maintaining and optimizing a critical system that processed a large volume of data transactions. As our user base grew, I noticed that the system was starting to experience significant performance bottlenecks, particularly during peak usage times. This issue posed a threat to our ability to meet service level agreements (SLAs) and risked causing user dissatisfaction.

Task:
I was tasked with identifying and resolving the root causes of these performance issues to ensure the system could handle the increased load and continue meeting SLAs without compromising user experience.

Action:
To tackle this challenge, I initiated a cross-functional effort, collaborating closely with database administrators, software developers, and infrastructure teams. My first step was to conduct a comprehensive analysis of the system’s architecture to identify the root causes of the performance bottlenecks. Through this analysis, I discovered that the inefficiencies stemmed primarily from outdated database queries and a lack of effective caching mechanisms.

I then led the implementation of a two-level caching system, which significantly reduced the load on the database by caching frequently accessed data. Additionally, I optimized the database retrieval process by addressing the 'thundering herd' problem, a situation where multiple processes simultaneously accessed the same data, overwhelming the system. I also introduced a sharding strategy to the database, partitioning it based on specific customer groups. This not only improved performance but also ensured the system could scale efficiently as the user base continued to grow.

Throughout this process, I prioritized collaboration by maintaining open communication channels with the various teams involved, ensuring that the changes were understood and smoothly integrated into the existing system. I also focused on building fast by rolling out the most impactful improvements in stages, minimizing disruption to users.

Cross functional collaborations : \
- Worked with architects on the to analyze the queries, and I led a workshop (which is 2 hrs of un-inturrupted meetings for 1 week) to create materialized views for the expensive queries of calculating zones, base rates for package
- Worked with the redis team to understand the amount of storage that can be granted for this application ID , then implemented a hybrid approach which is 2 level caching with caffiene and redis for faster data retrieval and lesser queries
- ** mention this in other point - Revisted caching, how effective it is at peak time, cache hit ratio, how effectively are we mapping cached data and created views which are only a subset of data to be stored
- Separated the reads and writes as there was a process that was hydrating the data as the application read the data, so worked with DBA's to separate the traffic and helped with bottleneck of connections at the DB
- Too much data was being stored , so devised a plan for purging the data which effectively copies over the data to a hard drive or cold storage for audit purposes
  
Result:
As a result of these actions, I successfully resolved the immediate performance issues and positioned the system for long-term success. The system's improved efficiency allowed us to meet our SLAs consistently, even during peak usage times. These optimizations led to increased user satisfaction and confidence in our platform, as the system was now more robust and capable of handling the demands of a growing user base.

# Have you had any competing priorities
# Most difficult project or task
# Something you are proud of
Situation:
In my previous role, I was leading the development of a critical Orchestrator solution intended for deployment across multiple domains within our organization. Concurrently, I was also managing the enhancement of an internal Compare Tool used for analyzing and comparing large datasets. Both projects were crucial to the organization’s strategic goals, and each had tight deadlines. The Orchestrator project, in particular, faced significant infrastructure challenges, including the need to scale our Kafka cluster, develop effective criteria for scaling AWS Lambda functions, increase the number of connections our Oracle cluster could handle, and add nodes to the Redis cluster. These infrastructure delays posed a risk to the project timeline.

Task:
I was tasked with ensuring the timely delivery of both the Orchestrator solution and the Compare Tool enhancements, despite the infrastructure challenges. This required careful prioritization, effective management of resources, and close coordination with various teams to address the delays and keep both projects on track.

Action:
To handle the competing priorities and infrastructure delays, I first developed a detailed project plan that highlighted the critical infrastructure tasks for the Orchestrator project. Recognizing that these delays could impact the overall timeline, I prioritized addressing the infrastructure issues to ensure the system's stability and scalability.

Scaling the Kafka Cluster:
I coordinated with the DevOps team to expand the Kafka cluster, ensuring it could handle the increased message throughput required by the Orchestrator. This involved carefully planning the addition of brokers to the cluster and optimizing configurations to avoid performance bottlenecks.

Developing Criteria for Scaling Lambda Functions:
I worked closely with the cloud architecture team to develop a set of effective criteria for auto-scaling AWS Lambda functions based on workload. This included setting up triggers based on request rates, execution duration, and error rates to ensure the system could dynamically adjust to varying loads without manual intervention.

Increasing Oracle Cluster Connections:
To address the limitations in the Oracle cluster, I collaborated with the database administration team to increase the number of concurrent connections the cluster could handle. This required both hardware upgrades and optimization of the connection pooling strategy to ensure the database could support the growing demands of the Orchestrator.

Adding Nodes to Redis Cluster:
I also led the effort to add additional nodes to the Redis cluster, ensuring that the in-memory data store could handle the increased data load. This included reconfiguring the cluster to ensure even distribution of data across nodes and optimizing the replication process for high availability.

In parallel, I continued to manage the Compare Tool enhancements by breaking down the project into manageable phases. I prioritized the most critical features and performance optimizations, ensuring steady progress without compromising the quality of the Orchestrator project.

I maintained regular communication with all stakeholders, holding daily stand-ups and weekly review meetings to track progress, address issues as they arose, and adjust timelines when necessary. This proactive approach allowed me to manage the infrastructure delays effectively while keeping both projects aligned with the organization’s goals.

Result:
Despite the infrastructure challenges, I successfully delivered the Orchestrator solution on time. The system was robust, scalable, and met all the deployment requirements across multiple domains. The infrastructure enhancements, including the scaled Kafka cluster, optimized Lambda scaling criteria, increased Oracle connections, and expanded Redis cluster, ensured the system’s stability and future-proofed it for growing demands.

Simultaneously, the Compare Tool enhancements were completed without delays, leading to significant improvements in tool performance and user satisfaction. This experience demonstrated my ability to effectively manage competing priorities and infrastructure challenges, ensuring successful project delivery while maintaining a focus on collaboration, quality, and long-term scalability.
# Tell me about a time when you led the team for some task (or took extra responsibilities. he tried to see if I led anyone)                                               Situation:
In my previous role, I was tasked with leading the adoption of ephemeral environments within our development pipeline. This initiative aimed to enhance our on-demand testing capabilities and accelerate the software development lifecycle by integrating tools like Terraform and cloud infrastructure management. The project was crucial for improving efficiency but posed significant challenges, particularly for the junior developers on the team who were unfamiliar with the new technologies and methodologies involved.

Task:
As the project lead, my primary responsibility was to ensure the successful implementation of ephemeral environments while also mentoring the junior developers. I needed to guide them through the complexities of infrastructure automation, cloud orchestration, and the integration of ephemeral environments into our existing workflow.

Action:
To manage the adoption process effectively, I started by setting up a series of workshops to introduce the team to the concept of ephemeral environments, the benefits they bring, and the specific tools we would be using, such as Terraform for infrastructure as code (IaC). These sessions were designed to build a strong foundational understanding, especially for the junior developers who were new to these technologies.

Recognizing the steep learning curve, I implemented a mentoring system where I paired junior developers with more experienced team members. This approach allowed for hands-on learning through pair programming, where juniors could actively participate in the setup and deployment of ephemeral environments while receiving guidance and feedback in real time.

I led from the front by taking charge of the most complex tasks, such as integrating Terraform with our cloud infrastructure to automate the creation and destruction of environments. I demonstrated the process of writing modular and reusable Terraform scripts, explaining the best practices for managing state, variables, and resource configurations. Throughout this process, I made sure to involve the junior developers, walking them through each step and encouraging them to contribute to the scripts and deployment processes.

Additionally, I organized regular code reviews and knowledge-sharing sessions where team members, including juniors, could present their work, discuss challenges, and share solutions. This not only helped in building their confidence but also fostered a collaborative learning environment.

When we faced challenges, such as configuring the scaling criteria for ephemeral environments or dealing with cloud resource limitations, I took the lead in troubleshooting and problem-solving sessions. I encouraged the juniors to actively participate, guiding them through the process of identifying issues, exploring solutions, and implementing fixes.

Result:
As a result of these efforts, the team successfully adopted ephemeral environments, significantly improving our on-demand testing capabilities and reducing the time required to spin up and tear down test environments. The junior developers not only gained proficiency in Terraform and cloud infrastructure management but also developed a deeper understanding of DevOps practices and infrastructure automation.

Their growth was evident in their ability to take on more complex tasks independently as the project progressed. The successful adoption of ephemeral environments led to increased productivity across the development pipeline, and the juniors I mentored were well-prepared to contribute to future infrastructure and DevOps initiatives.

This experience underscored the importance of hands-on leadership and the value of coaching in driving both project success and team development. By leading from the front and fostering a culture of continuous learning, I was able to guide the team through a significant technological shift while ensuring the professional growth of my colleagues.

# Tell me about a time when you work together with other teams                                                                                                             
# Tell me about a time you made a mistake.
Situation:
In a previous role, I was working on a project that involved managing a large volume of JSON data within our database. We were using traditional relational tables to store this JSON data due to its flexibility and ease of querying. As the volume of requests grew exponentially, I noticed that the database was becoming increasingly strained, leading to performance issues. To address this, I decided to optimize the table design by compressing columns and adding appropriate indexes. Confident in the changes, I moved forward without conducting thorough load testing, believing the optimizations would be sufficient.

Task:
My task was to find a sustainable solution to manage the increasing volume of JSON data efficiently while ensuring the database remained performant and scalable. However, by underestimating the scale of the data and skipping extensive load testing, I made a critical mistake that led to further performance degradation and exceeded the database's size expectations. This mistake caused delays in data processing and impacted the user experience.

Action:
When the performance issues became apparent, I realized that my initial approach had not adequately addressed the scalability challenges. I immediately took responsibility for the oversight and initiated a deeper analysis of the situation. Through this analysis, I identified that the current database structure was not well-suited to handle the rapidly growing JSON data.

To rectify the mistake, I led an effort to re-architect the data storage solution. Recognizing the limitations of our existing approach, I proposed moving the JSON data to a separate object storage solution that was better equipped to handle large, unstructured data. Additionally, I explored alternative database solutions and decided to adopt a wide columnar database specifically designed to manage large volumes of JSON data more efficiently.

I also implemented a rigorous testing framework that included extensive load testing to simulate peak conditions and ensure the new solution could handle the expected data volumes. This testing phase involved setting up a staging environment that closely mirrored production, allowing us to identify and address any potential issues before deployment.

Result:
The new approach to storing JSON data in an object storage solution, combined with the use of a wide columnar database, significantly improved the system’s performance and scalability. The performance degradation issues were resolved, and the database size was managed more effectively, preventing the system from being overwhelmed by the growing volume of requests.

However, this experience was a valuable lesson in the importance of thorough testing and the need to fully understand the implications of system changes. By learning from this mistake, I was able to implement a more robust solution that not only met the immediate needs but also positioned the system for future growth.

In the end, the new architecture led to improved data processing times, better resource utilization, and enhanced system stability. The lesson learned from this experience also influenced my approach to future projects, where I placed a greater emphasis on comprehensive testing and validation, ensuring that similar mistakes were not repeated.

# What product that you led are you most proud of and why?   

# Tell me about a time you convinced someone to change their mind.   

## Situation
After relocating to Pittsburgh, I was tasked with upgrading the WebLogic servers that were crucial for several applications within the company. However, maintaining these servers was becoming increasingly complex due to compliance requirements and the challenges of keeping them up to date. The complexity of managing WebLogic led to increased maintenance costs and potential risks, prompting me to explore more modern solutions.

## Task
I proposed transitioning from WebLogic servers to a microservices architecture using lightweight servers such as Tomcat and Spring Boot. This approach promised greater flexibility, easier maintenance, and improved scalability. However, my proposal was met with skepticism from my manager and management, who were concerned about the boldness of the move and the potential for errors during the rewrite process, which could negatively impact revenue.

## Action
To address these concerns and build confidence in my proposed approach, I developed a comprehensive plan that included the following components:

### Risk Analysis
- **Technical Risks:** Identified potential technical risks such as integration challenges with existing systems, performance bottlenecks, and compatibility issues with third-party services.
- **Business Risks:** Assessed business risks, including potential downtime during the transition, the impact on revenue-generating services, and compliance with industry standards.
- Developed mitigation strategies for each risk, including extensive testing, phased rollouts, and fallback options to minimize disruption.

### Implementation Plan
- **Gantt Chart Overview:**
  - **Analysis Phase (2 weeks):** Detailed assessment of the current WebLogic infrastructure, including dependencies and compliance requirements.
  - **Pilot Rewrite and Testing Setup (5 weeks):**
    - Selection of an initial application to rewrite using Spring Boot and deploy on Tomcat.
    - Setup of a parallel testing environment to validate the new architecture.
    - Collaboration with testing teams to ensure comprehensive coverage of business cases, with a focus on revenue-related functionalities.
  - **Full Implementation and Rollout (4 weeks):**
    - Gradual migration of other applications, ensuring continuous monitoring and real-time adjustments.
    - Development of CI/CD pipelines to facilitate seamless updates and enhance scalability.

### Agile Approach
- Proposed managing the transition using an Agile methodology, organizing the project into sprints that allowed for flexibility and rapid iteration.
- **Sprint Planning:** Broke down the migration into 2-week sprints, each focusing on specific components of the transition, such as the initial pilot rewrite, testing, and full rollout.
- **Daily Stand-Ups:** Led daily stand-ups to track progress, address blockers, and ensure alignment among all team members.
- **Sprint Reviews:** Conducted reviews at the end of each sprint to gather feedback, assess outcomes, and make necessary adjustments for the next sprint.

### Contingency Planning
- Developed a robust contingency plan, including a rollback strategy for each stage of the migration. This involved maintaining the existing WebLogic servers in parallel until the new microservices-based system was fully validated.
- Set clear criteria for rolling back the transition if critical issues were encountered, ensuring that we could revert to the previous setup with minimal disruption.

### Load Testing and Performance Validation
- Emphasized the importance of load testing to ensure that the new architecture could handle peak traffic and was future-ready.
- Configured the testing environment to simulate real-world conditions, working closely with product owners and testers to validate performance under various scenarios.
- This rigorous testing phase helped to build confidence in the new system's reliability and scalability.

## Result
Management was impressed by the thoroughness of my plan and the comprehensive approach to risk mitigation and testing. They agreed to allow us to pilot the new approach on one application initially. This application included both UI and backend components and interacted with various services, including those capturing revenue-related data.

The transition to Spring Boot and Tomcat was executed successfully, with the following key outcomes:

- **Cost Savings:** The new architecture resulted in significant reductions in the time and costs associated with WebLogic upgrades. The ease of maintenance and the ability to push updates seamlessly through the new CI/CD pipelines translated into further savings.
- **Scalability:** The system's horizontal scalability was enhanced, allowing for efficient resource utilization through configurable properties.
- **Efficiency:** The modern microservices approach enabled quicker updates and more straightforward management of the infrastructure, aligning with our goal of future-proofing our systems.
- **Risk Mitigation:** The comprehensive testing and contingency planning ensured that the transition was smooth, with no significant disruptions to revenue-generating services.

According to industry reports, transitioning from traditional application servers like WebLogic to lightweight solutions like Spring Boot can result in cost savings ranging from 20% to 50% in infrastructure and maintenance costs. Given the scale of our operations, this could translate to annual savings of hundreds of thousands to millions of dollars.

This successful pilot led to broader adoption of the microservices strategy across other applications within the company, validating my approach and highlighting the benefits of embracing modern, scalable solutions.

# Can you give me an example of how you manage conflict? 
Situation:
In my previous role, I was involved in a project where the goal was to implement a new Orchestrator solution for multiple domains within our organization. This solution was highly decoupled and configurable, designed to be a plug-and-play mechanism for different departments. However, during the project's critical phase, there was a significant conflict between the development team and the operations team regarding the approach to be taken for database partitioning. The development team favored a more aggressive sharding approach to handle increased load, while the operations team was concerned about the potential risks and long-term maintenance challenges associated with this method.

Task:
As the lead on the project, it was my responsibility to manage this conflict, ensuring that both teams’ concerns were addressed while keeping the project on track. I needed to find a resolution that would not only meet the technical requirements but also align with the broader organizational goals of scalability and maintainability.

Action:
To address the conflict, I first initiated a series of meetings with both teams to fully understand their perspectives. I made it a priority to listen actively to each team's concerns and validate their points of view. I then facilitated a joint discussion where I encouraged both teams to openly share their thoughts and proposed a solution that would balance the immediate need for performance with the long-term operational considerations.

Specifically, I proposed a phased approach to the database partitioning. We would implement a less aggressive sharding strategy initially, which would address the immediate performance issues without introducing significant operational risks. At the same time, I committed to developing detailed documentation and creating a robust testing environment that would allow the operations team to gradually adopt more advanced sharding techniques as they became more comfortable with the approach.

By focusing on collaboration and building for the future, I was able to get both teams to agree on this compromise. I also ensured that clear communication channels were established, so that any future concerns could be addressed promptly, avoiding similar conflicts down the line.

Result:
The phased approach was successfully implemented, leading to significant performance improvements without compromising the system's maintainability. The operations team appreciated the gradual transition and the attention given to their concerns, while the development team was satisfied with the performance gains achieved. The project was completed on time, and the Orchestrator solution was rolled out smoothly across multiple domains, demonstrating scalability and flexibility as intended.

This experience reinforced my belief in the importance of addressing conflicts head-on, ensuring that all stakeholders feel heard and respected. By fostering collaboration and focusing on long-term goals, I was able to turn a potentially disruptive conflict into a productive dialogue that benefited the entire project.

Sharding details :
The team proposed to shard by shipperId, zone ID, Location ID \
Also proposed hybrid approach where compound shard key with shipperId_zone  \
But the complexity in shard key design with hybrid approach, maintainability like adding nodes and the uncertainity behind uneven distribution of data on different shards if sharded by what the team propsed , DBA was'nt giving a buy-in 
Leaving the ego aside , working for the company's best - combinedly both the teams decided to agree on sharing on request id and pre-compute the shardId that the query should be fired to. The DBA team decided to go with 3 shards to start with, and the queries were made configurable to pre-compute it based on a hash function. Further partitioning the tables with shipped date , helped to custom create the queries and improved peformance

# Give me an example of how you negotiated between two teams.                                                                                                              
# How do you handle promoting someone as a manager?                                                                                                                        
# How do you communicate technical project needs with non-technical teams? [Answer]                                                                                        
# Why are you interested in this role at Meta?                                                                                                                             
# What do you think about Meta values, and how do you put these values into your work life?                                                                                
# Tell me about a time when you had to work on something you were passionate about.                                                                                      

## Situation
In my previous role, I was given the opportunity to develop an Orchestrator worker pattern from scratch, a project I was particularly passionate about. The Orchestrator was intended to manage complex workflows across multiple domains, requiring a highly efficient and scalable system. Given my interest in designing robust architectures and optimizing system performance, this project was a perfect fit for me.

## Task
My task was to design and implement a scalable Orchestrator worker pattern that could handle a high volume of tasks efficiently. Additionally, I was responsible for ensuring that the system could manage peak loads without performance degradation. The success of this project was critical to the company's ability to automate and streamline operations across different business units.

## Action
Driven by my passion for system design and performance optimization, I took the following steps to ensure the success of the project:

### Research and Design
- I began by researching best practices for worker pattern architectures, focusing on scalability, fault tolerance, and efficiency. I explored various design patterns, ultimately choosing a highly decoupled approach that allowed each worker to operate independently while being coordinated by a central Orchestrator.
- I designed the system to leverage message queues for task distribution, ensuring that workers could scale horizontally based on the workload. This approach allowed for dynamic scaling, with workers being added or removed as needed without impacting overall performance.

### Development and Implementation
- I led the development effort, working closely with a team of developers to build the Orchestrator worker pattern from the ground up. I implemented the core functionality, including task scheduling, load balancing, and error handling mechanisms.
- Recognizing the importance of performance, I integrated caching mechanisms and optimized database interactions to minimize latency and ensure that the system could handle high throughput.

### Performance Improvements
- Once the initial version was in place, I focused on fine-tuning the system's performance. I conducted extensive load testing to identify bottlenecks and optimize the system's response under peak conditions.
- I introduced a two-level caching system and optimized database retrieval processes to address performance issues, particularly under heavy load conditions. This included solving "thundering herd" problems, where multiple processes would simultaneously request the same data, overwhelming the system.

### Iterative Refinement
- I applied an Agile approach to the project, breaking down the development into sprints that allowed for continuous iteration and improvement. Each sprint focused on specific aspects of the Orchestrator, such as improving fault tolerance, enhancing logging mechanisms, or further optimizing performance.
- I conducted regular code reviews and performance assessments, working with the team to implement enhancements and refine the system based on real-world testing.

### Collaboration and Knowledge Sharing
- Throughout the project, I collaborated closely with other teams, including DevOps and infrastructure, to ensure seamless integration of the Orchestrator with existing systems. I also organized knowledge-sharing sessions to bring the team up to speed on the architectural decisions and performance optimization strategies.

## Result
The Orchestrator worker pattern was successfully developed and deployed, resulting in a highly efficient and scalable system that exceeded performance expectations. The system was able to handle peak loads smoothly, with performance improvements that significantly reduced processing times and increased overall throughput.

- **Scalability:** The system's ability to scale horizontally allowed it to manage a growing volume of tasks without degradation in performance, aligning with the company's long-term goals of automation and efficiency.
- **Performance:** The performance optimizations, including caching and database improvements, resulted in a more responsive system that could handle high volumes of transactions with minimal latency.
- **Passion and Impact:** This project not only fulfilled my passion for system design and optimization but also had a significant positive impact on the company's operations. The success of the Orchestrator worker pattern became a cornerstone of our automation strategy, leading to widespread adoption across various business units.

This experience reinforced my belief in the importance of pursuing projects that align with my passions, as it drives me to deliver innovative and high-quality solutions that make a meaningful impact.

# TODO

## Context setting about current project

## Questions
- How do you deal with teammate when you do not get a response from  and you need something
"When a teammate is unresponsive, I start by assessing the situation to understand if there might be any reasons for their lack of response, such as a heavy workload or personal issues. I then follow up politely, clearly stating what I need, why it’s important, and when I need it by. I make sure to use the appropriate communication channels, and if necessary, I escalate my follow-up gradually.

If the issue is urgent, I emphasize the impact of not getting a response and set a clear deadline. I also offer to help if they’re overwhelmed or suggest alternative solutions to move the project forward.

If multiple follow-ups don’t work and the situation is critical, I escalate the issue to management, focusing on finding a constructive solution rather than placing blame. After the situation is resolved, I reflect on the experience to improve my communication practices in the future."

This framework demonstrates that you handle unresponsiveness with professionalism, empathy, and a focus on collaboration, ensuring that the team’s goals are met while maintaining positive working relationships.
- How to deal with management changes
  - Ack the change
  - Adapt quickly
  - Align with new goals
  - Lead by example
"Management changes can be challenging, but I see them as opportunities for growth and improvement. When a new manager or director comes on board, I start by gathering information about their goals, priorities, and leadership style. This helps me align my team’s objectives with the new direction.

I maintain open communication with my team, ensuring they are informed and feel supported during the transition. I’m also flexible in adapting to any new processes or cultural shifts introduced by the new management.

To ensure my team remains productive and motivated, I lead by example, providing stability and promoting a growth mindset. I also believe in offering constructive feedback to the new management if necessary, always advocating for my team’s needs.

Finally, I reflect on the transition to learn from the experience and continuously improve my leadership approach, preparing for any future changes that may come."
- Explain about a complex problem that you have solved at your workplace

## Interviewing.io Questions 
#### A story about a project they are proud of that had a large impact on their org.
- “What project are you most proud of and why?”
  - **Error Repository**, Hold And Release App, Compare tool app
    - Org level impact
    - Motivation: solve a common problem and make difference
    - Proactive: Meet with stake holders to see what I can do better, brainstorm on the features, how generic can it be made
    - Perseverance: To meet deadline, need to get all the pawns in place. DB provisioning, Queue provisioning, Features, Stories
    - Empathy: Open for constructive critisism and understanding the problem or concern from their point of view

- “Tell me about a recent day working that was really great and/or fun.”
  - For great, I would like to quote **Compare tool app** and how it helped making decisions for management to push code to prod and get rid of old infrastructure
    
####  A story about a change they proactively suggested and drove that had an impact on their entire org. Usually requiring two or more teams to work on. 
- “Tell me about a time when you wanted to change something that was outside of your regular scope of work.”
  - JDK Upgrades to Weblogic servers
     - Emphasize on the Org level impact
     - The convincing part
     - The Planning part
      
- “Tell me about a time you had to make a fast decision and live with the results.”
    - Suggestion of Hold And Release methodology
      - It was a feature that was required once all the adapter, orchestrator was in place
      - It needed to be quick and efficient
      - This needed to be done by business without any technical knowledge
      - Living with it as its working for our stakeholders well and they control it
        
#### A story about an ambiguous project that the candidate took ownership of and was able to drive consensus from stakeholders in their org. Usually requiring two or more teams to work on.
- “How do you decide what to work on next?”
  - Being in the principal role here at FedEx, I have been a part of design conversations for a while now
  - Being in this role has given me a breadth of view from an architects perspective and by leading a group of developers, deeveloper perspective
  - From the architect, I would only a one liner of what needs to be done, and why it would help
  - Then I would dig in deep, collaborate with on-site off-shore leads, may be whiteboard stuff, and lay out how it can be done
  - Once I discuss this with Architect, I go and articulate the how process, and assign the stories based on the strengths of devs including me
  - While developing there are more things that are usually discovered, it could be like adding an extra column in the db, it could be adding extra field in the json, or sometimes scrap the whole how as we got to know why it cant be done only after laying down a bit of implementation.
  - I maintain a list of things that are pending and would take a considerable amount of man-hours
  - Discuss this with Architect to see where we stand with future new features
  - Then once this list is compiled its the job of Product Owners to help me but my say has a good amount of weight as I have gotten into the weeds more
    
- “Tell me about a project or task that was ambiguous or underspecified.”
  - Underspecified : VB2 Implementation, Compare tool Implementation

#### A story about a project with many technical difficulties that were blocking many teams and how they overcame each blocker.

- “Tell me about a time when you needed to overcome external obstacles to complete” a task or project.
  - VB2 Infrastructure provisioning with deadline
  - Compare tool mapping issues with CRSV
    
- “Tell me about a time a project took longer as expected.”
   - VB2 timeline with workers ( explain with "I" as the POV )

#### A story about how they were able to work through a disagreement with two or more teams on the direction of a large project.
- “Tell me about a person or team who you found most challenging to work with.”
   - Compare tool mapping issues ( Conflict story , add more points to emphasize on empathy and perserverance )
- “Tell me about a time you disagreed with a coworker.”
   - Weblogic story if Compare tool was already mentioned
- “Tell me about a situation where two teams couldn’t agree on a path forward.”
   - DB sharding story ( Make it a bit more technical, add details on perseverance )

####  A story about a soft skill or technical skill they want to developer and the progress they have made to learn it. Usually a skill that will have the potential to affect two or more teams.

- “Describe a situation when you made a mistake, and what you learned from it.”
  - JSON Data in tables
    - why json was stored plain
    - explain why it was missed in lower levels ( quote urgency factor )
    - articulate what was the impact ( DB alerts, slowness in responses as it throttled the db, infrastructure isn't alike production, so cant load much )
    - what was the quickest fix I was able to make ( purge job to reclaim some space )
    - Hot fix in L4 to push the data to object store and retrieve while comparing ( Followed by immidiate request for BLOB storage in PROD )
    - Communicate it to mananger, and make sure he is able to answer the management for a missed deadline and how fast and efficient we are fixing
      
- “Tell me about some constructive feedback you received from a manager or a peer”
  - Networking with the architects beyond the Org
  - Know how the systems operate and gather information of best practices across
    
- “Tell me about a skill set that you observed in a peer or mentor that you want to develop in the next six months.”
   - Be here now during the meetings
   - Think from different POV's and for that gain domain knowledge of the systems involved
   - Always think from a perspective of generalization and robustness when designing interfaces
   - Be open minded and understand from where the other person is coming during the discussions

  "In the next six months, I want to focus on developing a few key skills that I’ve observed in a peer of mine. First, they have an incredible ability to be fully present during meetings. It sounds simple, but being fully engaged without distractions allows them to grasp the nuances of discussions and offer more thoughtful input. I’m working on improving that, to ensure I’m not just physically present but truly 'here' during critical conversations.

Another skill I admire is how they consistently think from different points of view. They do this by really digging into the domain knowledge of the systems we work on. I’ve realized that gaining a deeper understanding of the systems involved helps me see problems through the eyes of various stakeholders, making my contributions more valuable.

Additionally, they have this mindset of designing interfaces and solutions with generalization and robustness in mind. It’s something I’ve started adopting—thinking not just about solving the problem at hand, but also considering how flexible and resilient the solution will be in the future.

Lastly, I’ve noticed how open-minded they are in discussions. They make a conscious effort to understand where the other person is coming from, even if they initially disagree. I’m trying to be more mindful of that, especially during tough discussions, because it really helps in building a collaborative atmosphere."


                                                                                                                                                                        
