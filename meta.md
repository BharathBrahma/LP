# Have you ever had difficult/challenging situation in your previous job
Situation:
In a previous role, I was responsible for maintaining and optimizing a critical system that processed a large volume of data transactions. As our user base grew, I noticed that the system was starting to experience significant performance bottlenecks, particularly during peak usage times. This issue posed a threat to our ability to meet service level agreements (SLAs) and risked causing user dissatisfaction.

Task:
I was tasked with identifying and resolving the root causes of these performance issues to ensure the system could handle the increased load and continue meeting SLAs without compromising user experience.

Action:
To tackle this challenge, I initiated a cross-functional effort, collaborating closely with database administrators, software developers, and infrastructure teams. My first step was to conduct a comprehensive analysis of the system’s architecture to identify the root causes of the performance bottlenecks. Through this analysis, I discovered that the inefficiencies stemmed primarily from outdated database queries and a lack of effective caching mechanisms.

I then led the implementation of a two-level caching system, which significantly reduced the load on the database by caching frequently accessed data. Additionally, I optimized the database retrieval process by addressing the 'thundering herd' problem, a situation where multiple processes simultaneously accessed the same data, overwhelming the system. I also introduced a sharding strategy to the database, partitioning it based on specific customer groups. This not only improved performance but also ensured the system could scale efficiently as the user base continued to grow.

Throughout this process, I prioritized collaboration by maintaining open communication channels with the various teams involved, ensuring that the changes were understood and smoothly integrated into the existing system. I also focused on building fast by rolling out the most impactful improvements in stages, minimizing disruption to users.

Result:
As a result of these actions, I successfully resolved the immediate performance issues and positioned the system for long-term success. The system's improved efficiency allowed us to meet our SLAs consistently, even during peak usage times. These optimizations led to increased user satisfaction and confidence in our platform, as the system was now more robust and capable of handling the demands of a growing user base.

# Have you had any competing priorities
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
# Tell me about a time when you led the team for some task (or took extra responsibilities. he tried to see if I led anyone)                                               
# Tell me about a time when you work together with other teams                                                                                                             
# Tell me about a time you made a mistake. [Answer]                                                                                                                        
# What product that you led are you most proud of and why? [Answer]                                                                                                        
# Tell me about a time you convinced someone to change their mind. [Answer]       

# Can you give me an example of how you manage conflict? [Answer]
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

# Give me an example of how you negotiated between two teams.                                                                                                              
# How do you handle promoting someone as a manager?                                                                                                                        
# How do you communicate technical project needs with non-technical teams? [Answer]                                                                                        
# Why are you interested in this role at Meta?                                                                                                                             
# What do you think about Meta values, and how do you put these values into your work life?                                                                                
# Tell me about a time when you had to work on something you were passionate about.                                                                                        
                                                                                                                                                                           
