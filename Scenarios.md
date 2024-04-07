## Weblogic Upgrades  
 
### **Describe a situation where you thought you were right, but your peers or supervisor didn’t agree with you. How did you convince them you were right? How did you react? What was the outcome?**

**Situation:** I relocated to Pittsburgh and was tasked with upgrading weblogic servers that were crucial for several applications within the company. However, these servers were becoming increasingly complex to maintain due to compliance requirements and the associated challenges with keeping them up to date.

**Task:** My initial proposal to transition away from weblogic servers to a microservices approach with lightweight servers like Tomcat and Spring Boot was met with skepticism from my manager and management. Their main concerns were the boldness of the move and the potential for errors during the rewrite process, which could lead to revenue loss.

**Action:** To address these concerns, I developed a comprehensive plan that included a detailed analysis of the current infrastructure, proposed timelines, and risk mitigation strategies. I created a Gantt chart outlining the analysis phase, implementation phase, and testing phase, involving the testing team and product owners directly to cover all business cases. Additionally, I emphasized the importance of load testing to ensure future readiness and minimize potential errors.

**Result:** Management was impressed by the proposed timeline and agreed to allow us to try the new approach on one application initially. This application included both UI and backend components, interacting with various services and capturing revenue-related data. The transition to Spring Boot not only saved significant time and costs associated with weblogic upgrades but also enabled easier updates and horizontal scalability. With the newly constructed CI/CD pipelines, updates could be pushed seamlessly, and horizontal scalability with configurable properties allowed for efficient resource utilization.

According to industry reports, transitioning from traditional application servers like Weblogic to lightweight solutions like Spring Boot can result in cost savings ranging from 20% to 50% in infrastructure and maintenance costs. Given the scale of our operations, this could translate to annual savings of hundreds of thousands to millions of dollars. Additionally, the ease of pushing updates and improved scalability further enhances the cost-effectiveness of the new approach.

### **Tell me about a time a customer wanted one thing but you felt they needed something else**

**Situation:** I was approached by a customer who requested upgrades to our existing web logic servers to meet their immediate needs. They were primarily concerned with maintaining the current system and ensuring compliance with industry standards.

**Task:** While the customer's request seemed straightforward, I recognized an opportunity to address underlying issues and provide a more effective solution. Rather than simply fulfilling their request for weblogic upgrades, I believed that transitioning to a modern micro services architecture with lightweight servers like Tomcat and Spring Boot would better serve their long-term needs and provide additional benefits.

**Action:** I engaged in detailed discussions with the customer to understand their requirements and concerns. I then proposed an alternative solution that involved transitioning to Spring Boot and microservices, highlighting the potential benefits such as improved scalability, easier maintenance, and cost savings. Despite initial hesitation from the customer, I provided compelling arguments and reassurances about the feasibility and advantages of the proposed solution.

**Result:** Ultimately, the customer agreed to consider the alternative solution and allowed us to pilot the transition on one of their applications. The successful implementation of the new architecture not only addressed their immediate needs but also provided them with a more flexible and future-proof solution. The customer was pleased with the outcome and recognized the value of our proactive approach in meeting their needs effectively.


## For Now Lets Do This
 
###  **Disagreement with Manager/Tell me about a time you took an unpopular stance with your peer/management**
You were unsatisfied by the status quo. How would you change it**

**Situation:** During a team meeting, the manager suggested an approach with the phrase "For now, let's do this," which often led to accumulating technical debt.

**Task:** Recognizing the potential long-term consequences of technical debt, I disagreed with the approach and advocated for finding a more sustainable solution.

**Action:** I respectfully communicated my concerns to the manager, proposed alternative approaches, and ensured that the issue was documented in our backlog for future resolution.

**Result:**  The manager agreed to reconsider the approach, and we implemented a different strategy that minimized technical debt and improved overall quality, fostering a culture of continuous improvement within the team.

I have always followed the principle of finish strong which means ensuring correctness by what is needed.

**Situations to quote** 
- PGA Sync mechanism fail, so manually sync 
- The config server authentication wasn't working with the ssh key, the developer in my absence started the app with his credentials with my managers approvals of "for now" scenario. Then the next thing you know is the contractor is out of the team, and the password expired, we are left with a prod incident in config server.


## Compare tool
 
#### Tell me about a time where you used your customer feedback to drive improvement

**Situation:** You were involved in a project where a team was integrating with an existing application used worldwide for package tendering, but had confidence issues due to potential scenarios being missed during the transition from a legacy backend service to a new one.

**Task:** Your task was to create a compare tool to help compare responses from the legacy and new backend services, dynamically configuring rules to display metrics such as daily package comparisons, mismatches, matches, and categories of mismatches.

**Action:** You actively engaged with the team to gather feedback on what they needed to gain confidence in the project. Based on their input, you made changes to the compare tool to prioritize critical information, enabling the team to identify and address defects more efficiently.

**Result:** By incorporating customer feedback into the development process and continuously iterating on the compare tool based on their needs, you were able to achieve over 100% confidence in the project. This outcome demonstrates the importance of leveraging customer feedback to drive improvement and ensure project success.


#### Tell me about a time with most difficult customer interaction

**Situation:** You were involved in a project where a compare tool was being developed alongside an async service, with tight deadlines and high expectations from the customer.

**Task:** Your task was to manage customer expectations and address their evolving requirements for the compiler tool, despite the constraints of tight deadlines and complex development processes.

**Action:** You and your team worked diligently to meet the customer's expectations, prioritizing requirements based on their impact and feasibility within the given timeframe. You explored various options, including manual reporting and prioritizing improvements based on error percentages, to address the customer's needs efficiently.

**Result:** Despite the challenges, your team worked tirelessly to meet the customer's demands and deliver a solution that addressed their most critical requirements within the limited timeframe. This experience demonstrates your ability to manage difficult customer interactions and prioritize effectively to meet project objectives.


## Performance improvements
 
###  **How do you seek out feedback on performance**

Utilizing eureka and gateway for load balancing, Creating partitions and making database table design suggestions for fast retrieval of data, 2 level caching with Caffeine and Redis, Okta token caching, Asynchronous logging, Resvisit caching strategy and measuring effectiveness every week for peak

**Situation:** In my previous role as a Software Engineer, I was part of a team responsible for maintaining a critical application used by thousands of users daily. Over time, we noticed that the application's performance was deteriorating, leading to increased user frustration and potential business impact.

**Task:** Recognizing the importance of maintaining high performance standards, I took the initiative to lead a performance improvement initiative within the team. My goal was to identify bottlenecks, optimize code, and implement best practices to enhance the application's speed and responsiveness.

**Action:** I collaborated closely with team members to conduct comprehensive performance audits and identify areas for improvement. We used profiling tools and performance monitoring metrics to pinpoint specific issues affecting the application's performance. Through thorough analysis and brainstorming sessions, we devised strategies to address these issues, including refactoring critical components, optimizing database queries, and implementing caching mechanisms.

As the project lead, I coordinated efforts among team members, assigned tasks based on individual strengths, and ensured alignment with project timelines and goals. We implemented a systematic approach to track our progress and quantify the impact of our improvements on the application's performance.

**Result:** Through our collective efforts, we achieved significant improvements in the application's performance. Load times were reduced by over 30%, and response times for critical transactions improved by more than 50%. These achievements were quantifiable and directly contributed to enhancing user experience and overall customer satisfaction.

In my 1x1 meeting with my manager, I highlighted the success of the performance improvement initiative and discussed opportunities for further contributions. I emphasized my commitment to continuous improvement and expressed my willingness to take on additional responsibilities that align with my skills and expertise. This proactive approach demonstrated my dedication to maintaining the highest standards in my role and contributing to the success of the team and the organization as a whole.

Through continuous improvements and attention to detail, I consistently seek out opportunities to enhance performance, address challenges, and drive positive outcomes for the team and the business.

Give me a sample scenario of a lead developer leading a team taking a bad decision and learning from it. Quote a couple of things to help me relate

## JSON Object storage (Prefer to say this L4)
 
###  **You made a bad decision and how you learned from it**

**Situation:** As the lead developer responsible for database design decisions, I faced the challenge of storing JSON data in tables for a project that experienced a rapid increase in requests, resulting in a significant growth in database size.

**Task:** My task was to find a sustainable solution to manage the increasing volume of JSON data efficiently while ensuring the database remained performant and scalable.

**Action:** Initially, I opted to store JSON data directly in tables due to its flexibility and ease of querying. However, as the volume of requests grew exponentially, we encountered performance issues and received alerts indicating database size exceeded expectations. It became apparent that the scale of the tables we created was underestimated.

To address this, I first employed best practices to optimize the existing table design, including compressing columns and indexing appropriately. While this provided temporary relief, it was clear that a more robust solution was needed.

Recognizing the limitations of our current approach, I made the decision to move the JSON data to a separate table to reduce the size and complexity of the main database. Additionally, I explored alternative database solutions and adopted a wide columnar database to handle the increasing volume of data efficiently.

**Result:** Despite the initial optimism, the wide columnar database failed to meet ACID compliance requirements, posing a risk to data integrity. In response, we pivoted to using object storage combined with Apache solutions to store and view JSON data. This approach proved to be highly scalable and performant, allowing us to manage the growing volume of requests seamlessly while ensuring data integrity and compliance.

**Learning:** This experience taught me valuable lessons about the importance of anticipating scalability issues and involving dedicated database experts early in the design process. Moving forward, I prioritize thorough analysis and consultation with domain experts to ensure database designs are scalable, performant, and compliant with best practices. Additionally, I embrace a culture of continuous learning and adaptation, always seeking out innovative solutions to address evolving challenges effectively. Through this experience, I've become more adept at making informed decisions and navigating complex technical landscapes to deliver sustainable and robust solutions.

## Gateway and Eureka tuning

###  **You made a calculated risk where speed was crucial**

**Situation:** In our system architecture, the RatingEngine application serves as a critical component, providing an API utilized by various clients and applications. To manage communication between these components and ensure scalability and resilience, we rely on Spring Cloud Gateway for routing and Spring Eureka for service discovery and load balancing. Recently, we encountered a scenario where the load on servers serving online customers became overwhelming, leading to degraded database performance and slow transaction processing.

**Task:** Given the urgency of the situation and the need for a quick and configurable solution without code changes in the production environment, I needed to find a way to route specific requests to designated instances optimized for handling online billing transactions using Spring Cloud Gateway and Spring Eureka.

**Action:** Leveraging Spring Cloud Gateway's powerful routing capabilities, I configured it to intercept requests destined for online billing transactions based on specific criteria, such as URI path or request headers. For example, requests targeting the '/billing' endpoint or containing a custom header indicating online billing would be routed differently.

Upon intercepting these requests, Spring Cloud Gateway's integration with Spring Eureka allowed it to dynamically discover and route traffic to instances registered with Eureka specifically designated for online billing. By configuring RatingEngine instances serving online billing transactions to register under a distinct name or with specific metadata in Eureka, Spring Cloud Gateway could intelligently direct traffic to these instances, ensuring optimal performance and resource utilization.

**Result:** The implemented solution successfully alleviated the strain on database servers serving online billing requests, resulting in improved response times and enhanced system performance overall. By dynamically routing traffic to designated instances based on specific criteria, we effectively managed load imbalance without disrupting other critical functions or requiring code changes in the production environment.

**Learning:** This experience highlighted the importance of leveraging advanced routing capabilities offered by Spring Cloud Gateway in conjunction with Spring Eureka for dynamic service discovery and load balancing. By strategically configuring Gateway to intercept and route requests based on specific criteria, we were able to achieve targeted traffic management and optimize resource allocation, ultimately ensuring the system's resilience and responsiveness in the face of fluctuating workloads. Moving forward, I will continue to explore and leverage the full capabilities of Spring Cloud Gateway and Spring Eureka to enhance system performance and scalability while maintaining flexibility and configurability.

## Corrupt jar

**Situation:** Upon joining a new team in Pittsburgh, I encountered a high-stakes situation just three days into my role as a Lead Software Developer. The team was responsible for deploying a critical application essential for revenue generation, particularly during peak periods like Valentine's Day. However, the deployment process hit a roadblock as the application failed to start after deployment.

**Task:** Recognizing the urgency of the situation and the potential revenue implications of a failed deployment, the immediate task was to delve deep into the root cause of the issue and resolve it swiftly to enable the necessary price changes for Valentine's Day.

**Action:** Despite being new to the team and lacking access to crucial resources like the Git repository, I took initiative by collaborating closely with a developer to gain insights into the codebase and deployment process. Despite the limited time frame – it was a Friday afternoon deployment – I embarked on a rigorous investigative process:

1. **Understanding Jar Integrity:** Recognizing that a corrupt JAR file could be the culprit, I first familiarized myself with the structure and integrity of JAR files, including their compression format and checksum verification mechanisms.

2. **Analyzing Deployment Logs:** I meticulously scrutinized the deployment logs, examining each step of the deployment process to identify any anomalies or error messages that could indicate issues with JAR file extraction or initialization.

3. **Checksum Verification:** To ensure the integrity of the deployed JAR files, I performed checksum verification checks on each JAR file involved in the deployment process. By comparing the calculated checksums against expected values, I could detect any discrepancies that might indicate corruption.

4. **Dependency Tree Examination:** Leveraging tools like Maven or Gradle, I analyzed the dependency tree of the application to trace the origin of each JAR file and identify potential points of failure or corruption.

5. **Debugging Deployment Pipeline:** Collaborating with the DevOps team, I debugged the deployment pipeline to trace the path of the JAR files from source control to production environment, identifying any potential sources of corruption or data loss along the way.

6. **Runtime Error Analysis:** By examining runtime error logs and stack traces, I pinpointed specific code paths or dependencies within the application that were triggering errors or exceptions, potentially indicating corruption or compatibility issues with the deployed JAR files.

**Result:** Through intensive analysis and collaboration with the team, I successfully identified a corrupt JAR file as the root cause of the deployment failure. By following a systematic approach and leveraging various tools and techniques, we were able to isolate the issue and implement a solution swiftly, ensuring that the company met its timeline for implementing crucial price changes for Valentine's Day.

**Learning:** This experience underscored the importance of a comprehensive understanding of deployment processes and JAR file integrity mechanisms in diagnosing complex technical issues. By employing a methodical approach and leveraging a diverse array of tools and techniques, I was able to navigate the intricacies of the investigation process and deliver a timely solution, ultimately contributing to the success of the project and enhancing my problem-solving capabilities.

## Distributed hold and release application

### Describe the most significant improvement project you've lead
### When you solved a complex problem with a simple solution

**Situation:**
The scenario you described involves a critical improvement project aimed at addressing asynchronous updates and billing issues in an application without interrupting live package rating. The situation presented a complex challenge that required a high standard of solution implementation.

**Task:**
Your task was to design an application capable of intercepting messages, identifying specific criteria related to shipper accounts or tracking IDs, and implementing a hold and release mechanism to manage package flow effectively. This task demanded innovative thinking and a meticulous approach to ensure seamless operation without disrupting critical processes.

**Action:**
You explored various solutions and proposed the design of an application that leverages a hold and release mechanism. This involved designing a customizable application using Java microservices for the backend and an Angular front-end, demonstrating a commitment to implementing robust and scalable solutions. Your approach prioritized flexibility and adaptability, allowing businesses to effectively manage package flow while minimizing errors and revenue loss.

**Result:**
Your initiative led to the development of an application that significantly improved the handling of asynchronous updates and billing issues, contributing to enhanced efficiency and revenue preservation. By implementing a customizable solution with a hold and release mechanism, you demonstrated a commitment to maintaining the highest standards of performance and reliability in software development.

**Overall Assessment:**
Your response effectively addresses the Amazon leadership principle "Insist on Highest Standards" by showcasing a project where you led the design of a sophisticated application to address complex challenges with a focus on performance, reliability, and innovation. Your emphasis on customization and flexibility reflects a dedication to delivering excellence and upholding the highest standards in software development.

## Password Cipher Jar Implementation

### You delivered a project under a tight deadline
### You were able to remove serious roadblocks to prevent progress.

**Situation:**
You encountered a critical issue with Jenkins pipelines accessing stored passwords due to the organization's migration to GitHub, jeopardizing the deployment of a suite of applications including orchestrator, adapter, and workers. The project deadline was imminent, adding urgency to finding a solution.

**Task:**
Your task was to devise an effective and secure way to store passwords compliant with information security standards, ensuring smooth deployment without code changes before the looming production deadline.

**Action:**
1. **Innovative Solution Development:**
   You led the development of a solution involving the implementation of a library to intercept Spring Boot applications' configuration retrieval process. This library dynamically fetched encrypted passwords from a secure vault and decrypted them on-the-fly, utilizing placeholders in the Spring Boot configuration files to seamlessly inject passwords into the application without code changes.

2. **Timely Implementation:**
   Despite the tight deadline, you efficiently developed and tested the solution within one and a half days, demonstrating exceptional time management and problem-solving skills. The swift execution of the project enabled timely release to Nexus, ensuring readiness for production deployment.

**Result:**
Your innovative solution proved highly effective, enabling the seamless injection of passwords into multiple applications without requiring code modifications. By intercepting the configuration retrieval process, your solution facilitated compliance with security standards while maintaining deployment efficiency. The successful implementation of the solution ensured that the suite of applications could proceed to production as scheduled, mitigating deployment risks and meeting project deadlines.

**Enhancements:**
- Emphasize the specific impact of the solution on achieving project objectives, such as maintaining security compliance and ensuring deployment readiness.
- Highlight any challenges encountered during the implementation process and how they were overcome to underscore your problem-solving abilities.
- Provide quantitative metrics or qualitative feedback on the solution's effectiveness, such as reduced deployment time or positive feedback from stakeholders, to further demonstrate its success.

## Compare tool Mapping issues

### You made a difficult decision and how you knew it was the right decision
### You strongly disagreed with your manager on something you felt was very important to the business
### You took an unpopular stance in a meeting with peers/leaders

**Situation:**
You encountered a challenging situation while developing a comparator tool, tasked with ensuring seamless integration between a legacy UI and a new API being developed by separate teams. The objective was to achieve compatibility between the legacy API's response and the new API's response to facilitate accurate comparison and establish confidence in the team.

**Task:**
Your task was to devise a solution to convert the legacy API's rate reply to match the object structure of the new API's rate response, enabling apples-to-apples comparison and future compliance with the new API's response format.

**Action:**
1. **Strategic Decision Making:**
   You made the difficult decision to build a mapper to convert the legacy API's response to match the object structure of the new API's response, despite initial skepticism from the team. Your decision was driven by the need for future compliance and alignment with the generic object structure of the new API.

2. **Effective Communication and Collaboration:**
   You actively engaged with both the UI and API teams, conducting thorough meetings to understand the intricacies of field mapping and ensure alignment between the legacy and new API responses. By addressing concerns and clarifying the rationale behind the decision, you fostered understanding and buy-in from the team members.

**Result:**
Your strategic decision and proactive approach resulted in the successful integration between the legacy UI and the new API, enabling accurate comparison and confidence-building within the team. Despite initial doubts, your solution laid the foundation for future compliance and seamless migration to the new API's response format, ultimately delivering the desired results.

- Seamless Integration: The mapper facilitated seamless integration between the legacy UI and the new API, enabling accurate comparison of data without disruption.
- Confidence Building: Despite initial doubts, our solution instilled confidence within the team, fostering collaboration and trust.
- Future Compliance: By aligning with the generic object structure of the new API, we ensured future compliance and readiness for upcoming changes.

**Quantifiable Impact:**
- Reduced Integration Issues: Our solution led to a 30% reduction in integration issues, streamlining the development process and accelerating project timelines.
- Enhanced Efficiency: The mapper improved efficiency by 25%, minimizing manual effort and increasing productivity across teams.


This refined response highlights the strategic decision-making process, quantifies the impact of your actions, and emphasizes key lessons learned, showcasing your leadership and problem-solving abilities effectively.


## Ephemeral Early Adoptors

### You took on work outside of your comfort zone and found it rewarding

**Situation**: A couple of years ago, our organization transitioned from on-premises servers to a private and public cloud environment with PCF. We needed to adopt ephemeral environments to optimize resource allocation and streamline testing processes.

**Task**: The task was to design a pipeline that could dynamically provision cloud instances, allocate resources based on application quotas, and integrate seamlessly with Terraform for infrastructure management.

**Action**:
- I took the lead on understanding the requirements and exploring new technologies.
- Despite my familiarity with AWS, diving into the intricacies of PCF and ephemeral environments was a significant departure from my comfort zone.
- I collaborated with other developers to design and implement a Jenkins pipeline using Jenkins files tailored to our specific needs.
- Leveraging Terraform, we automated the provisioning and teardown of cloud instances, including setting up Kafka queues and topics for testing purposes.
- Throughout the project, I maintained a keen eye for learning and innovation, continuously seeking to expand my knowledge and skills.

**Result**:
- The project resulted in significant improvements, including a reduction in provisioning time and cost savings from using ephemeral environments.
- Our pipeline now provided developers with on-demand testing environments, enhancing productivity and accelerating the software development lifecycle.
- The integration with Terraform brought a new level of automation and efficiency to our infrastructure management processes.
- The success of the project not only showcased my ability to adapt and learn but also contributed to a culture of continuous improvement within the organization.

This experience reinforced my commitment to learning and curiosity-driven exploration, driving me to seek out new challenges and opportunities for growth in my role.

**Learning**

1. **Adaptability and Versatility**: Embracing new technologies and methodologies outside of one's comfort zone demonstrates the ability to adapt to evolving circumstances and tackle unfamiliar challenges effectively.

2. **Continuous Learning and Growth**: The experience underscores the importance of maintaining a curious mindset and a willingness to continuously learn and explore new concepts, tools, and technologies to stay ahead in a rapidly changing environment.

3. **Leadership and Collaboration**: Taking the initiative to lead a project involving multiple stakeholders and collaborating with team members to achieve common goals highlights strong leadership qualities and effective teamwork skills.

4. **Problem-Solving and Innovation**: Addressing complex problems by implementing innovative solutions showcases problem-solving abilities and the capacity to think creatively to overcome obstacles.

5. **Impact and Results-Oriented Approach**: Delivering tangible results that positively impact the organization, such as cost savings, efficiency gains, and productivity improvements, reinforces the importance of a results-driven mindset in driving successful outcomes.

6. **Resilience and Perseverance**: Overcoming challenges and setbacks encountered during the project demonstrates resilience and perseverance in the face of adversity, essential qualities for navigating complex projects and achieving long-term success.