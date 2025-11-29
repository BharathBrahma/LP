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
