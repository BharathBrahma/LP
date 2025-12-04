# Final Scenarios

# ⭐ "Project I Am Most Proud Of" — Error Repository (Meta-Caliber Version)

## Situation

When I joined the FedEx Ground Rating modernization effort, every domain was manually tracking and triaging rating failures in spreadsheets, logs, or ad-hoc scripts. There was no unified source of truth. This created delays in debugging, duplicated work across teams, and made RCA extremely inefficient — especially during peak events like Black Friday.

There was no formal requirement to fix this, but I saw this gap was slowing down multiple teams and creating repeated customer issues.

## Task

I took ownership of designing and delivering a central Error Repository platform that could serve as a standardized, scalable, org-wide solution.

My goal was to build something:

- easy to ingest from multiple microservices
- intuitive for users
- scalable for future domains
- configurable enough that each team could customize it without forking code

This was not a roadmap item — it was something I proactively identified and drove.

## Action

I operated end-to-end:

1. **Designed the architecture from scratch**
   - Designed the DB schema aligning with architects
   - Built the backend service (Spring Boot)
   - Built the UI (Angular)
   - Created ingestion APIs for orchestrators, workers, and downstream systems

2. **Drove cross-functional alignment**
   
   Initially, teams pushed back — each domain had its own tools and workflows.
   I set up listening sessions with sister teams to understand:
   - what error types mattered to them
   - what filters/slices they wanted
   - how they envisioned triage workflows
   - what pain points we could remove
   
   This turned the project from "my idea" → "org-backed initiative".

3. **Turned custom requirements into configuration**
   
   Instead of writing custom logic for every team, I introduced a config layer so each org could:
   - define their error categories
   - set retention rules
   - control custom fields
   - define their own views
   
   This made onboarding new teams extremely lightweight.

4. **Iterated using feedback loops**
   
   I released the first version quickly, collected feedback through office hours and demos, and then iterated:
   - added faceted search
   - built filtering by shipper, workflow, task
   - added severity scoring
   - introduced a "download RCA bundle" feature

5. **Partnered with architects to scale adoption**
   
   Once 2 teams were onboarded, I created a reusable "Error Repo Onboarding Guide", and architects helped me evangelize it org-wide.

## Result

The Error Repository became a standardized platform across the organization:

- 8+ domains onboarded within months
- Reduced error triage time by ~40%
- Cut duplicate investigations by ~30%
- Provided a single debugging surface for dozens of microservices
- Enabled faster RCA during peak events (Black Friday/Cyber Monday)
- Became the backbone for reliability dashboards used by leadership

But personally, I'm proud because:

- I saw a cross-team problem that nobody formally owned
- I built a full-stack solution from scratch
- I scaled it across the org through collaboration, empathy, and product thinking
- I created something reusable, maintainable, and future-proof

This project represents my approach as a senior engineer — seeing around corners, taking initiative, and building solutions that elevate the entire organization.


## Error Repository – Conflict + Alignment (3‑Minute STAR Version)

### **Situation**

At FedEx, we were receiving thousands of recurring rating errors originating from AS400, microservices, and downstream services like Pricing, Zone, and Customer Hierarchy. Every failure arrived as a **raw JSON dump** with no categorization. As a result:
# Final Scenarios

## Error Repository – Conflict + Alignment (3‑Minute STAR Version)

### **Situation**

At FedEx, we were receiving thousands of recurring rating errors originating from AS400, microservices, and downstream services like Pricing, Zone, and Customer Hierarchy. Every failure arrived as a **raw JSON dump** with no categorization. As a result:

* Operations couldn’t distinguish *business* failures (requiring customer contact) from *technical* failures (simple reprocessing).
* AS400 was reluctant to modify their decades‑old tables.
* The DOM committee resisted schema changes.
* Service teams wanted structured visibility.
* There was no single source of truth, creating ambiguity and conflicting expectations.

### **Task**

I needed to **bring these teams together**, align them on a unified error structure, and design a model that would allow our orchestrator–worker architecture to make **intelligent retry decisions** instead of blindly replaying messages.

### **Action**

**1. Gathered cross‑team perspectives**
I individually met AS400, DOM, service teams, and operations to understand their constraints. This surfaced the reasons for misalignment and gave me a 360° view of the problem.

**2. Proposed a Notification Code–based error model**
I designed:

* Notification codes at every key computation stage
* Metadata to indicate *where* and *why* the failure occurred
* Clear separation of business vs technical errors
* Routing logic for the orchestrator to determine the correct retry stage

Examples:

* If code = tech‑retry, retry from **Worker 2** instead of Worker 1
* If code = business error, operations contacts customer
* If code = technical failure, ops simply re‑submits after validating a few fields

**3. Negotiated schema changes with reluctant teams**
I worked with DOM to justify the schema update and partnered with AS400 to introduce notification codes in a **non‑breaking** way so their legacy table remained stable.

**4. Built the end‑to‑end system**
I implemented the backend, repository, Kafka→Cassandra ingestion, retry logic using Resilience4j, and the UI that operations used to triage errors.

### **Result**

The Error Repository became the **single source of truth** for rating failures.

* Retry success rate improved significantly as retries executed at the correct worker stage.
* Application load decreased due to intelligent routing.
* Operations gained clear visibility into business vs technical errors.
* Service teams could finally observe structured patterns instead of raw JSON.
* The approach was later adopted by sister teams.

Overall, I turned a multi‑team disagreement into a unified, scalable design that meaningfully reduced repetitive errors and operational overhead.

## Learned from Mistake – Storing Large JSON CLOBs (3-Minute STAR Version)

### **Situation**

Early in my FedEx tenure, I owned a service responsible for persisting rating events coming through Kafka and downstream systems. The original design stored the **entire 20–25KB JSON message** inside an Oracle CLOB column for every transaction. This looked convenient at first, but it became a scaling issue.

The database grew rapidly, queries slowed down, and downstream consumers struggled with huge payloads. Troubleshooting also became harder because the JSON wasn't normalized—every service handled it differently.

### **Task**

I needed to recognize where the design was breaking down and fix it in a way that both improved performance and maintained backward compatibility. More importantly, I needed to understand my own decision-making gap and prevent similar architectural mistakes.

### **Action**

**1. Analyzed the root problem**
I dug into the performance metrics and realized the real issue: I had optimized for convenience instead of scalability. Storing full JSON blobs:

* Increased I/O and storage costs
* Slowed down queries
* Made debugging inconsistent
* Made downstream processing expensive

**2. Designed a correct, long-term fix**
I normalized the schema and extracted only the necessary fields instead of the entire payload. I added metadata columns and references so debugging was easier and storage was efficient.

**3. Owned the mistake publicly**
I documented the original decision, its shortfalls, the new design, and what I learned. This transparency actually increased trust with my manager and peers.

### **Result**

* DB storage dropped significantly
* Query speeds improved
* Downstream systems became more stable
* The new schema became the standard for similar services

But the bigger win: I became far more deliberate about evaluating performance impact and long-term maintainability before accepting a “quick” design.

---

## Learned from Mistake – Communication & Follow-up Discipline (3-Minute STAR Version)

### **Situation**

At Microsoft, during my ramp-up, I struggled with one thing: **proactive communication**. I often assumed teams were busy and didn’t want to “disturb” people with follow-ups. That led to:

* Delays in getting requirements clarified
* Blockers going unaddressed
* My manager asking for updates I wasn’t prepared to give
* A perception issue during my performance review cycle

One specific incident stood out: My manager asked for a dependency status on a partner team. I had reached out once but never followed up aggressively. The partner had not responded, and I had no update. I ended up looking unprepared, and it hurt my credibility.

### **Task**

I needed to change how I approached communication—be proactive, consistent, and structured—and ensure no dependency, question, or task remained stuck because I stayed silent.

### **Action**

**1. Created a communication & follow-up template**
I built a simple internal system:

* Daily agenda outlining whom I need to reach out to
* Follow-up cadence (Day 1, Day 3, Day 5)
* Notes on dependencies, blockers, and clarifications
* A short update message for my manager summarizing progress

**2. Stopped assuming people were “too busy”**
I reframed my mindset: following up is not disturbing someone—it's how work gets unblocked.

**3. Proactively kept my manager in the loop**
Not for micromanagement, but so he always had:

* Visibility into what I was driving
* Awareness of blockers
* Context for escalations

### **Result**

* My dependencies started moving faster because I followed up reliably
* Partners appreciated clear, crisp messages instead of one-off pings
* My manager had full visibility and explicitly called out the improvement in my mid-cycle
* I felt more confident and in control instead of reactive

Most importantly, I fundamentally shifted from a "hesitant communicator" to someone who **proactively drives clarity and momentum**, which directly improved my execution velocity.

## Driving Results Under Ambiguity – NSP Subscription Cleanup (3-Minute STAR Version)

### **Situation**

While working on the Network Security Perimeter (NSP) initiative at Microsoft, I deployed updated infrastructure across 30+ partner subscriptions using our standard weekly production pipeline. After deployment, I discovered that **seven or more partner environments still had non-compliant resources**.

A deeper investigation revealed the root issues:

* Many resources were **never part of automated weekly pipelines**.
* Several had been **manually created months or years earlier** and completely forgotten.
* Some existed in **6–8 regions** for audit or historical reasons but were not being used.
* No single team claimed ownership.

These unknown resources were invisible tech debt but posed a real **security compliance risk**, and we were on a strict deadline.

### **Task**

I needed to:

* Identify what each orphaned resource was,
* Determine whether it should be **deleted or integrated** into our automated pipelines,
* Work with multiple partner teams—many initially unresponsive—to get clarity,
* And ensure **full NSP compliance** across every subscription before the security deadline.

### **Action**

**1. Created clarity out of ambiguity**
I built a subscription-wide matrix capturing:

* Resource type
* Region
* Usage history
* Pipeline participation
* Ownership
* Delete-or-retain decisions

This gave teams and leadership their first structured view of the problem.

**2. Opened communication loops with each partner**
I reached out individually to owners of each resource, asking:

* Do you still need this?
* Can it be deleted?
* If needed, should it be built through the pipeline?

Most partners initially deprioritized the task since it wasn't blocking them. I persisted with follow-ups, short syncs, and clear context-setting about compliance deadlines.

**3. Framed the problem in terms of risk and cost**
I highlighted:

* Security exposure from unmanaged resources,
* Pipeline inconsistencies,
* Unnecessary multi-region VM costs.

This reframing shifted teams from hesitation to partnership.

**4. Executed cleanup and automation**
I collaborated with each team to:

* Delete stale resources,
* Remove unused multi-region VMs,
* Standardize what remained,
* Move necessary items into automated deployment pipelines,
* Ensure everything integrated cleanly with NSP.

### **Result**

Within a few weeks:

* All subscriptions became fully **NSP compliant ahead of deadline**.
* We significantly **reduced cost** by removing unused multi-region VMs.
* Security exposure from untracked resources dropped to zero.
* Automated pipelines became the single source of truth.
* Partner teams appreciated the new visibility into their infra.

This was a strong example of me taking ownership in ambiguity and driving cross-team alignment and security compliance.

---

## Learned From Mistake – Hesitant Follow-Up & Communication Cadence (3-Minute STAR Version)

### **Situation**

During the same NSP effort, I had to coordinate with several partner teams to validate whether their orphaned resources should be deleted or built through automated pipelines.

At the time, I hesitated to follow up frequently because I assumed:

* People were too busy,
* They would reply when they got time,
* I shouldn't "bother" anyone.

Because of this, several key decisions remained unresolved. When my manager asked for updates, I didn't have clear answers, and it affected my credibility.

### **Task**

I needed to fix two things:

1. **Resolve the open dependency decisions quickly**, so I could unblock NSP compliance.
2. **Address my communication approach**, which was slowing my progress and causing last‑minute workload spikes.

### **Action**

**1. Owned the mistake**
I was transparent with my manager about what happened—that I hesitated to follow up and it created gaps. He encouraged me to build a proactive communication system.

**2. Built a structured follow‑up methodology**
I created a daily system:

* A dependency & follow-up tracker,
* Cadence: Day 1 → Day 3 → Day 5 reminders,
* Clear owner tagging,
* Decision logs,
* Short progress updates to my manager (not for micromanagement but visibility).

**3. Changed my mindset**
I reframed follow-ups as part of my job:

> “I am unblocking the team. Following up is not bothering someone.”

**4. Applied it immediately**
Using this structure, I re‑engaged all partner teams, scheduled syncs, made decisions on each resource, and closed everything before the deadline.

### **Result**

* The NSP milestone was delivered on time.
* Dependencies started moving faster due to structured follow‑ups.
* Partner teams appreciated the clear, predictable communication.
* My manager explicitly acknowledged the improvement in my visibility and responsiveness.
* This permanently changed how I operate—I now maintain a predictable communication rhythm and proactively drive clarity.

This experience helped me evolve from a hesitant communicator into someone who drives alignment and momentum across teams.

## Embracing Ambiguity – Fabric Migration Exploration (3-Minute STAR Version)

### **Situation**

When I joined Microsoft, our organization received a mandate to explore migrating our data platform to Microsoft Fabric. Fabric was still in early preview—documentation was incomplete, behavior was inconsistent, and the team only had surface-level exposure. Because I was new and had fresh bandwidth, my manager asked me to **deep-dive Fabric** and bring clarity on what the real migration effort would look like.

There were no requirements, no defined scope, and no success criteria. The only instruction was: *"Explore Fabric and tell us what moving our workloads actually means."*

### **Task**

My responsibility was to take this completely ambiguous problem and:

* Understand practical paths for moving data into Fabric,
* Identify hidden constraints and blockers,
* Run experiments to capture real metrics instead of assumptions,
* Convert those findings into actionable insights,
* And help the team estimate realistic timelines and semester plans.

### **Action**

**1. Explored migration paths through hands-on experimentation**
I tested multiple approaches of copying data into OneLake—direct copy, Fabric pipelines, and transfers under different networking setups. I validated how Fabric behaves under:

* RBAC restrictions,
* VNET configurations,
* NAT gateway constraints,
* and different authentication flows.

Every experiment produced logs, metrics, and failure patterns that helped us understand Fabric’s real-world behavior.

**2. Iterated with senior and principal engineers**
I shared early results with leads, which prompted deeper exploration:

* "What if the customer uses a locked-down VNET?"
* "What happens under NAT?"
* "What if authentication changes?"

Each prompt drove new experiments. I repeatedly returned with concrete answers instead of theoretical assumptions.

**3. Structured the ambiguity**
I created:

* A comparison matrix of migration approaches,
* A constraints & blockers log,
* A networking conditions checklist,
* A mapping of operational behaviors,
* And detailed notes on what breaks vs succeeds.

This became the team’s **first grounded, structured understanding** of Fabric migration.

**4. Enabled semester & roadmap planning**
My findings helped principals and PMs:

* Break the work into fine-grained engineering stories,
* Identify gaps and required features,
* Understand cross-team dependencies,
* Realistically estimate timelines,
* And shape the upcoming semester roadmap.

It became clear from my work that migration isn't simply "moving data from A to B"—it involves deep networking, security, and infra considerations.

### **Result**

My research became the **baseline blueprint** for all Fabric migration planning in our team. It provided clarity, helped uncover future engineering scenarios, enabled realistic semester planning, and ensured the wider team wouldn't be starting blindly.

This reinforced my strength in taking an undefined, ambiguous space and turning it into structured, actionable clarity for the entire team.

## Communication & Innovation – Driving AI Adoption with Microsoft Roo (3-Minute STAR Version)

### **Situation**

When Microsoft Copilot and internal AI tooling were gaining momentum, our leadership encouraged engineers to explore whether AI could *realistically* improve productivity. In my team, everyone was busy with existing network isolation work, and no one had bandwidth to evaluate AI tools in depth.

Because I was new and curious, one of the senior engineers introduced me to **Microsoft Roo**, an AI assistant in VS Code. My manager asked me to explore it—not with an expectation to produce anything—but simply to answer one question:

> **“Is AI actually useful for our team’s work, or is it not worth investing in?”**

There was no pressure to produce a deliverable. The task was intentionally ambiguous—**just explore and see if it’s valuable.**

### **Task**

My goal was straightforward but open-ended:

* Experiment with Roo,
* Understand whether it could help with our complex network isolation tasks,
* And provide an honest, evidence-based recommendation to the team: **“Should we adopt this or not?”**

There was **no requirement** to create frameworks, templates, or reusable components. Those emerged later as a result of what I discovered.

### **Action**

**1. Explored Roo’s true capabilities through hands-on work**
I tested Roo against several of our real network isolation tasks—public IP tag creation, subnet outbound access changes, NSP rules, NAT gateway deployment scripts, and audit logging. I intentionally used challenging tasks that involved deep parameter threading and cross-service dependencies.

Through experimentation, I noticed Roo struggled when:

* context was too large,
* folder structure was inconsistent,
* or prompts weren’t well-defined.

**2. Identified patterns that unlocked Roo’s accuracy**
As I explored, I realized Roo performed extremely well *if*:

* project structure was predictable,
* rules and memory were configured,
* prompts were standardized.

This wasn’t part of my assignment—but the discovery made AI far more usable for complex engineering tasks.

**3. Created reusable tools because the opportunity was clear**
To help Roo maintain context across large codebases, I built:

* a **bootstrap shell script** that standardized project structure for Roo across languages,
* improved rule definitions,
* memory configurations,
* reusable prompt templates for documentation and code understanding.

This was not required, but it dramatically increased Roo’s effectiveness.

**4. Communicated findings broadly when impact became obvious**
I first shared a demo with my immediate team. They were surprised at how effectively Roo understood parameter threading and interface flows.

My manager then nominated my demo to a cross-org engineering forum, where I presented the findings. Based on the response, I was invited to present in our **VP’s forum** as well.

**5. Adoption grew organically**
Offshore teams began using the bootstrap + prompts for their own stories and later demonstrated measurable productivity improvements. Roo became part of the team’s onboarding toolkit because engineers could now navigate complex codebases in hours rather than days.

### **Result**

Although the initial task was simply to answer, “Is AI worth using?”, my exploration:

* Proved AI could materially improve productivity for complex engineering work,
* Created reusable assets that scaled across teams,
* Enabled engineers to generate high-quality documentation rapidly,
* Reduced onboarding time for new joiners,
* Helped offshore teams accelerate their deliverables,
* And gained VP-level visibility through clear communication and impactful demos.

This story showcases my ability to take an unstructured, exploratory task and turn it into meaningful, scalable impact through curiosity, experimentation, and clear communication.

* Operations couldn’t distinguish *business* failures (requiring customer contact) from *technical* failures (simple reprocessing).
* AS400 was reluctant to modify their decades‑old tables.
* The DOM committee resisted schema changes.
* Service teams wanted structured visibility.
* There was no single source of truth, creating ambiguity and conflicting expectations.

### **Task**

I needed to **bring these teams together**, align them on a unified error structure, and design a model that would allow our orchestrator–worker architecture to make **intelligent retry decisions** instead of blindly replaying messages.

### **Action**

**1. Gathered cross‑team perspectives**
I individually met AS400, DOM, service teams, and operations to understand their constraints. This surfaced the reasons for misalignment and gave me a 360° view of the problem.

**2. Proposed a Notification Code–based error model**
I designed:

* Notification codes at every key computation stage
* Metadata to indicate *where* and *why* the failure occurred
* Clear separation of business vs technical errors
* Routing logic for the orchestrator to determine the correct retry stage

Examples:

* If code = tech‑retry, retry from **Worker 2** instead of Worker 1
* If code = business error, operations contacts customer
* If code = technical failure, ops simply re‑submits after validating a few fields

**3. Negotiated schema changes with reluctant teams**
I worked with DOM to justify the schema update and partnered with AS400 to introduce notification codes in a **non‑breaking** way so their legacy table remained stable.

**4. Built the end‑to‑end system**
I implemented the backend, repository, Kafka→Cassandra ingestion, retry logic using Resilience4j, and the UI that operations used to triage errors.

### **Result**

The Error Repository became the **single source of truth** for rating failures.

* Retry success rate improved significantly as retries executed at the correct worker stage.
* Application load decreased due to intelligent routing.
* Operations gained clear visibility into business vs technical errors.
* Service teams could finally observe structured patterns instead of raw JSON.
* The approach was later adopted by sister teams.

Overall, I turned a multi‑team disagreement into a unified, scalable design that meaningfully reduced repetitive errors and operational overhead.

## Learned from Mistake – Storing Large JSON CLOBs (3-Minute STAR Version)

### **Situation**

Early in my FedEx tenure, I owned a service responsible for persisting rating events coming through Kafka and downstream systems. The original design stored the **entire 20–25KB JSON message** inside an Oracle CLOB column for every transaction. This looked convenient at first, but it became a scaling issue.

The database grew rapidly, queries slowed down, and downstream consumers struggled with huge payloads. Troubleshooting also became harder because the JSON wasn't normalized—every service handled it differently.

### **Task**

I needed to recognize where the design was breaking down and fix it in a way that both improved performance and maintained backward compatibility. More importantly, I needed to understand my own decision-making gap and prevent similar architectural mistakes.

### **Action**

**1. Analyzed the root problem**
I dug into the performance metrics and realized the real issue: I had optimized for convenience instead of scalability. Storing full JSON blobs:

* Increased I/O and storage costs
* Slowed down queries
* Made debugging inconsistent
* Made downstream processing expensive

**2. Designed a correct, long-term fix**
I normalized the schema and extracted only the necessary fields instead of the entire payload. I added metadata columns and references so debugging was easier and storage was efficient.

**3. Owned the mistake publicly**
I documented the original decision, its shortfalls, the new design, and what I learned. This transparency actually increased trust with my manager and peers.

### **Result**

* DB storage dropped significantly
* Query speeds improved
* Downstream systems became more stable
* The new schema became the standard for similar services

But the bigger win: I became far more deliberate about evaluating performance impact and long-term maintainability before accepting a “quick” design.

---

## Learned from Mistake – Communication & Follow-up Discipline (3-Minute STAR Version)

### **Situation**

At Microsoft, during my ramp-up, I struggled with one thing: **proactive communication**. I often assumed teams were busy and didn’t want to “disturb” people with follow-ups. That led to:

* Delays in getting requirements clarified
* Blockers going unaddressed
* My manager asking for updates I wasn’t prepared to give
* A perception issue during my performance review cycle

One specific incident stood out: My manager asked for a dependency status on a partner team. I had reached out once but never followed up aggressively. The partner had not responded, and I had no update. I ended up looking unprepared, and it hurt my credibility.

### **Task**

I needed to change how I approached communication—be proactive, consistent, and structured—and ensure no dependency, question, or task remained stuck because I stayed silent.

### **Action**

**1. Created a communication & follow-up template**
I built a simple internal system:

* Daily agenda outlining whom I need to reach out to
* Follow-up cadence (Day 1, Day 3, Day 5)
* Notes on dependencies, blockers, and clarifications
* A short update message for my manager summarizing progress

**2. Stopped assuming people were “too busy”**
I reframed my mindset: following up is not disturbing someone—it's how work gets unblocked.

**3. Proactively kept my manager in the loop**
Not for micromanagement, but so he always had:

* Visibility into what I was driving
* Awareness of blockers
* Context for escalations

### **Result**

* My dependencies started moving faster because I followed up reliably
* Partners appreciated clear, crisp messages instead of one-off pings
* My manager had full visibility and explicitly called out the improvement in my mid-cycle
* I felt more confident and in control instead of reactive

Most importantly, I fundamentally shifted from a "hesitant communicator" to someone who **proactively drives clarity and momentum**, which directly improved my execution velocity.

## Driving Results Under Ambiguity – NSP Subscription Cleanup (3-Minute STAR Version)

### **Situation**

While working on the Network Security Perimeter (NSP) initiative at Microsoft, I deployed updated infrastructure across 30+ partner subscriptions using our standard weekly production pipeline. After deployment, I discovered that **seven or more partner environments still had non-compliant resources**.

A deeper investigation revealed the root issues:

* Many resources were **never part of automated weekly pipelines**.
* Several had been **manually created months or years earlier** and completely forgotten.
* Some existed in **6–8 regions** for audit or historical reasons but were not being used.
* No single team claimed ownership.

These unknown resources were invisible tech debt but posed a real **security compliance risk**, and we were on a strict deadline.

### **Task**

I needed to:

* Identify what each orphaned resource was,
* Determine whether it should be **deleted or integrated** into our automated pipelines,
* Work with multiple partner teams—many initially unresponsive—to get clarity,
* And ensure **full NSP compliance** across every subscription before the security deadline.

### **Action**

**1. Created clarity out of ambiguity**
I built a subscription-wide matrix capturing:

* Resource type
* Region
* Usage history
* Pipeline participation
* Ownership
* Delete-or-retain decisions

This gave teams and leadership their first structured view of the problem.

**2. Opened communication loops with each partner**
I reached out individually to owners of each resource, asking:

* Do you still need this?
* Can it be deleted?
* If needed, should it be built through the pipeline?

Most partners initially deprioritized the task since it wasn't blocking them. I persisted with follow-ups, short syncs, and clear context-setting about compliance deadlines.

**3. Framed the problem in terms of risk and cost**
I highlighted:

* Security exposure from unmanaged resources,
* Pipeline inconsistencies,
* Unnecessary multi-region VM costs.

This reframing shifted teams from hesitation to partnership.

**4. Executed cleanup and automation**
I collaborated with each team to:

* Delete stale resources,
* Remove unused multi-region VMs,
* Standardize what remained,
* Move necessary items into automated deployment pipelines,
* Ensure everything integrated cleanly with NSP.

### **Result**

Within a few weeks:

* All subscriptions became fully **NSP compliant ahead of deadline**.
* We significantly **reduced cost** by removing unused multi-region VMs.
* Security exposure from untracked resources dropped to zero.
* Automated pipelines became the single source of truth.
* Partner teams appreciated the new visibility into their infra.

This was a strong example of me taking ownership in ambiguity and driving cross-team alignment and security compliance.

---

## Learned From Mistake – Hesitant Follow-Up & Communication Cadence (3-Minute STAR Version)

### **Situation**

During the same NSP effort, I had to coordinate with several partner teams to validate whether their orphaned resources should be deleted or built through automated pipelines.

At the time, I hesitated to follow up frequently because I assumed:

* People were too busy,
* They would reply when they got time,
* I shouldn't "bother" anyone.

Because of this, several key decisions remained unresolved. When my manager asked for updates, I didn't have clear answers, and it affected my credibility.

### **Task**

I needed to fix two things:

1. **Resolve the open dependency decisions quickly**, so I could unblock NSP compliance.
2. **Address my communication approach**, which was slowing my progress and causing last‑minute workload spikes.

### **Action**

**1. Owned the mistake**
I was transparent with my manager about what happened—that I hesitated to follow up and it created gaps. He encouraged me to build a proactive communication system.

**2. Built a structured follow‑up methodology**
I created a daily system:

* A dependency & follow-up tracker,
* Cadence: Day 1 → Day 3 → Day 5 reminders,
* Clear owner tagging,
* Decision logs,
* Short progress updates to my manager (not for micromanagement but visibility).

**3. Changed my mindset**
I reframed follow-ups as part of my job:

> “I am unblocking the team. Following up is not bothering someone.”

**4. Applied it immediately**
Using this structure, I re‑engaged all partner teams, scheduled syncs, made decisions on each resource, and closed everything before the deadline.

### **Result**

* The NSP milestone was delivered on time.
* Dependencies started moving faster due to structured follow‑ups.
* Partner teams appreciated the clear, predictable communication.
* My manager explicitly acknowledged the improvement in my visibility and responsiveness.
* This permanently changed how I operate—I now maintain a predictable communication rhythm and proactively drive clarity.

This experience helped me evolve from a hesitant communicator into someone who drives alignment and momentum across teams.

## Embracing Ambiguity – Fabric Migration Exploration (3-Minute STAR Version)

### **Situation**

When I joined Microsoft, our organization received a mandate to explore migrating our data platform to Microsoft Fabric. Fabric was still in early preview—documentation was incomplete, behavior was inconsistent, and the team only had surface-level exposure. Because I was new and had fresh bandwidth, my manager asked me to **deep-dive Fabric** and bring clarity on what the real migration effort would look like.

There were no requirements, no defined scope, and no success criteria. The only instruction was: *"Explore Fabric and tell us what moving our workloads actually means."*

### **Task**

My responsibility was to take this completely ambiguous problem and:

* Understand practical paths for moving data into Fabric,
* Identify hidden constraints and blockers,
* Run experiments to capture real metrics instead of assumptions,
* Convert those findings into actionable insights,
* And help the team estimate realistic timelines and semester plans.

### **Action**

**1. Explored migration paths through hands-on experimentation**
I tested multiple approaches of copying data into OneLake—direct copy, Fabric pipelines, and transfers under different networking setups. I validated how Fabric behaves under:

* RBAC restrictions,
* VNET configurations,
* NAT gateway constraints,
* and different authentication flows.

Every experiment produced logs, metrics, and failure patterns that helped us understand Fabric’s real-world behavior.

**2. Iterated with senior and principal engineers**
I shared early results with leads, which prompted deeper exploration:

* "What if the customer uses a locked-down VNET?"
* "What happens under NAT?"
* "What if authentication changes?"

Each prompt drove new experiments. I repeatedly returned with concrete answers instead of theoretical assumptions.

**3. Structured the ambiguity**
I created:

* A comparison matrix of migration approaches,
* A constraints & blockers log,
* A networking conditions checklist,
* A mapping of operational behaviors,
* And detailed notes on what breaks vs succeeds.

This became the team’s **first grounded, structured understanding** of Fabric migration.

**4. Enabled semester & roadmap planning**
My findings helped principals and PMs:

* Break the work into fine-grained engineering stories,
* Identify gaps and required features,
* Understand cross-team dependencies,
* Realistically estimate timelines,
* And shape the upcoming semester roadmap.

It became clear from my work that migration isn't simply "moving data from A to B"—it involves deep networking, security, and infra considerations.

### **Result**

My research became the **baseline blueprint** for all Fabric migration planning in our team. It provided clarity, helped uncover future engineering scenarios, enabled realistic semester planning, and ensured the wider team wouldn't be starting blindly.

This reinforced my strength in taking an undefined, ambiguous space and turning it into structured, actionable clarity for the entire team.


⭐ Compare Tool — The Project I Played a Key Role In (Leadership + Conflict + Technical Depth)

Situation
During our modernization of the global package tendering platform, multiple teams were transitioning from a legacy backend to a new async rating service. As we got deeper into integration testing, confidence dropped sharply — mismatches between the legacy and new service responses were causing friction between engineering teams, and every group suspected the other was at fault.

There was no systematic way to compare deeply nested responses, quantify mismatches, or categorize what was breaking.

This ambiguity was delaying the migration and creating conflict.

Task
I took the initiative to build a Compare Tool that would:

run automated comparisons

categorize mismatches

help teams prioritize defects

provide a UI to drill down into differences

generate daily confidence reports

dynamically configure rules for each region/country/customer

My goal was to create a single source of truth that would replace debates with data.

Action
I played a key role across all dimensions:

1. Designed the system end-to-end

Backend logic

Rule engine for threshold & config

Low-level diffing algorithm for nested structures

Materialized views + cron-based pipelines

Intuitive UI for drilling into mismatches

2. Navigated cross-team conflicts

The UI team and the backend team were interpreting mismatches differently.
Meetings were turning confrontational.

To address this:

I facilitated alignment meetings

Created clear definitions of mismatch categories

Proposed a rules-based approach that would satisfy both teams

Structured mismatches into:

structural differences

numerical differences

missing fields

business rule mismatches

This reduced friction and aligned teams.

3. Iterated based on feedback

I conducted several feedback loops:

prioritized critical mismatches (pricing, surcharges)

added filtering by region and service type

built exportable reports for business review

added confidence dashboards

4. Evangelized adoption

After initial success, I partnered with architects to onboard additional partner groups.

I created:

onboarding docs

rule templates

demo sessions for partner teams

dashboards showing mismatch trends

Result
The Compare Tool became a central validation system that:

increased team confidence from ~40% → over 100%

reduced integration issues by 30%

eliminated manual comparison efforts

gave leadership daily visibility into risk

accelerated the transition to the new backend

reduced conflict between teams by grounding decisions in data

This project is one I’m proud of because I not only delivered a complex technical solution, but I played a key role in driving alignment, reducing conflict, and enabling a major modernization effort to move forward with confidence.
