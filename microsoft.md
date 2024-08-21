## Biggest achievement or achievement you are proud of
  ### Compare tool
  -  leadership
  -  design decisions
  -  inclusivity
  -  the cross-functional collaboration
  -  technical challenges and edge
      - Rate limiting
      - Redis Streams
      - Orchestration
      - High level compares
      - Low level compares with customized rules which are configurable
      - Cron job for creating materialized views for UI
      - Intuitive UI to look at the difference and drill down on what is the difference
  -  who are the stake holders
  -  result of the tool
  ### Error Repository application
  - As a snr full stack developer, developed the backend-front end from the scratch
  - cross functional collaboration to setup the kafka cluster needed
  - Worked with architect to present it to higher management
  - Collaborated with other teams to showcase and be open for constructive feedback
  - Based on feedback prioritized and added functionalities
    - Storing header information
    - Adding retries based on parameters
    - Differentiate techinical errors and business errors
    - Automated replays in terms of network glitch
    - Authorization with OAuth 2.0
   - Result - Used as a repo for the org under my director and sister teams
## Dealing with Ambiguity
  ### GRM VB2 Orchestration
  - Problem Solving: I faced a situation where we had to work with incomplete or not-finalized responses from web services.

  - Decision Making: Despite the lack of finalized responses, we had to adhere to tight timelines. As the lead, I decided to advance development in parallel with waiting for the final responses. This involved developing the workers' framework, creating orchestrator tasks and workflows, and stubbing responses while anticipating potential changes.

  - Adaptability: I prepared the team for inevitable changes by fostering a flexible mindset. We planned for iterations to incorporate changes and ensured that the team had the capacity to handle and test changes as they came in.

  - Critical Thinking: I proactively anticipated potential impacts of changes on our system and devised strategies to accommodate them without disrupting overall progress.

  - Communication Skills: I maintained constant communication with product owners from dependent teams to stay updated on their progress. I ensured that any minor developments were communicated effectively and monitored deviations from the established contract, evaluating the impact on our system and downstream processes on a bi-weekly basis.

  - Resilience: I demonstrated resilience by managing ongoing changes and keeping the team focused and motivated despite the evolving requirements.

  - Prioritization: I prioritized tasks based on their impact and urgency, ensuring that critical components were addressed promptly while managing other aspects of the project in parallel.

  - Collaboration: I fostered collaboration within the team and with external stakeholders, ensuring that everyone was aligned and working towards common goals despite the uncertainties.

## Innovation/Thought process

Situation: As a principal engineer on the team, I was tasked with reducing the errors, replays, rebills and re-rates requests that were coming in as a part of production support. There was a process where every day we would get to know the errors occurred while ledgering , and invoicing once the package is rated. A lot scenarios where the customer was billed wrong due to errors in WS calls, data hydration etc. 

Task : My task was to target to reduce the number of errors by atleast 30 - 40% by the end of the PI

Action : My initial thought process was to understand the scale of errors, categorize the errors and get an idea of why or where majority of the errors are happening. I took help from a Data team , set up kafka queues to relay our rating information to them, where they would aggregate and create a dashbboard. \
But the dashboard wasnt really helping with drilling down unless we could categorize effectively. Now I took the initiative to work with a DOM committe that approves requests for changing/modifying json schema to add a new list and named it notifications. My thought process was to add notification in each stage of calculation with a notification code, description. Like it would say base charge was this, discount retrived was this, customer is not billed etc. Based on the notification codes, the dashboard looked much better and the errors were categorized. 

Result: Worked on the highest errors first, implemented resilience4j and circuit breaker pattern to retry rating when WS fails instead of wrong data, and I was able to lead the effort of moving these changes phase by phase to production. Definitely reduced the number of times we were paged and results were quantify able to the management.

## Peak Preparedness

- Spin up VMs and Lambda functions well in advance to avoid the cold start ( triggered based on requests/sec, cpu usage ) Warm them up, have it ready
- Database sizing
- Logs folder and splunk monitoring
- alert revisit
- cache hit ratio revisitt
- opportunities for fine tuning the objects
- dashboards for management (fine tune to show YoY progress)
