# TrainingPlatform

A small repo for the corporate training agent materials.

Current contents: PerplexityCommunication.md

I split the your conversation with Perplexity into 4 different parts so that we can digest the info properly. 

## Approach

The conversation across Parts 1–4 with Perplexity gives a good picture of _what_ we want to build, but it jumps too quickly into specific tools and prompts before we have a solid foundation. We need to go stepwise:

### Step 1 — Define business requirements (technology-agnostic)

Capture **what** the system must do without committing to any specific tool, LLM, or vendor yet. Technology and architecture constraints can be recorded as preferences or constraints only if there is a genuine business reason for them.

- Who are the users? Define all personas: content owners, instructional designers, video producers, graphic designers, learners, managers, admins.
- What training domains must be supported? (Data & AI concepts, Energy & Utilities domain — and can others be added later?)
- What output formats are required? (video scripts, slide decks, infographics, quiz/assessment items, research briefs)
- What does the content lifecycle look like? (intake → research → draft → review → approve → publish → retire)
- What are the governance constraints? (accuracy checklist, no client-identifiable information, version control, source restrictions)
- What are the non-functional requirements? (scalability, editorial quality, turnaround time SLA, portability away from any single vendor, cost envelope)
- What integrations are expected? (LMS, storage, communication tools, PM/task tool)

### Step 2 — Identify gaps and define development priorities

Review the requirements against what is already known and flag anything that is unclear, contested, or not yet decided.

- Which features are MVP vs. future phases? For example: basic video-script generation is MVP; adaptive learning paths based on CRM data is a future enhancement.
- Where are there open questions? (Which LMS? Which storage layer? Who owns content approval?)
- Rank features by business value and technical risk to define a priority-ordered backlog.
- Define acceptance criteria for each priority feature so the team knows when something is "done".
- Identify dependency chains — for example, the RAG knowledge base must exist before research automation can work.

### Step 3 — Research tools and technology

Only after requirements and priorities are clear, explore how different tools could satisfy each feature. Evaluate options against consistent criteria:

- **Cost-effectiveness**: licensing, API call costs at scale, free-tier limits.
- **Stickiness / lock-in risk**: how hard is it to swap one LLM or workflow tool for another? Prefer interfaces that abstract the model from the application logic.
- **Portability**: can prompts, content and workflows be exported and moved? Avoid proprietary formats where possible.
- **Integration breadth**: does the tool connect natively to the other components in our stack?
- **Maturity and support**: is the product stable enough for production use at JBS?

Areas to research specifically: LLM options (Gemini, Claude, OpenAI — cost, context window, rate limits), orchestration tools (n8n vs. alternatives), RAG/retrieval frameworks, AI video platforms, presentation generators, LMS options, and infographic tools. Build a short comparison matrix and run a time-boxed POC for shortlisted combinations before committing.

### Step 4 — Finalise the tech stack and overall architecture

With research complete, make firm decisions and document them as Architecture Decision Records (ADRs) so the rationale is preserved.

- Select the LLM(s) and the abstraction layer that will sit between the application and the model providers.
- Choose the orchestration tool and confirm it can handle the full workflow: trigger → research → brief → parallel asset generation → approval routing → publish → logging.
- Define the retrieval/RAG architecture: indexing strategy, chunking, embedding model, vector store, curated source list.
- Confirm storage layer (Drive/SharePoint folder structure, naming conventions, metadata schema).
- Confirm the LMS and how modules will be imported/published (API, SCORM, CSV, or manual).
- Produce a high-level system diagram showing all components and the data flows between them.

### Step 5 — Define metadata, data sources, integrations, data flows and processes

Nail down the details that make the system work as a coherent whole rather than a collection of disconnected scripts.

- **Content taxonomy**: define the controlled vocabulary for domain, audience role, seniority level, format, tech stack tags, and content version.
- **Topic record schema**: every training request should have a well-defined record (title, domain, audience, level, formats, status, timestamps, asset links).
- **Source document strategy**: which internal documents feed the RAG index? Which external sites are trusted and curators? How are they refreshed?
- **API and integration contracts**: define the payload shape for each tool integration (LLM request/response, LMS publish, storage write, notification).
- **Content lifecycle state machine**: map every possible status transition, who triggers it, and what automation fires at each step.
- **Prompt library governance**: where do prompts live (version-controlled repo), how are they named, and how are changes reviewed?

### Step 6 — Finalise security, users, groups, authentication, authorisation and access metrics

- Define all roles and map them to permissions (e.g., a Learner can read published modules; a Content Owner can approve; an Admin can edit templates).
- Choose an auth provider and SSO strategy appropriate for JBS.
- Define API key management: how are credentials stored, rotated, and audited? No keys in code.
- Scope the RAG retrieval: ensure the agent can only access documents appropriate for the query context (no leakage of confidential client data into public-facing content).
- Define audit logging: every content generation event, approval action, and publish event should be logged with who, what, and when.
- Agree on access metrics to track: active users, content generated per role, approval turnaround times.

### Step 7 — Finalise architecture documentation, design documentation and user documentation

Before the build begins in earnest, ensure the team has everything they need to work independently.

- **Architecture documentation**: finalised system diagram, component descriptions, ADRs, data flow diagrams, integration specs.
- **Design documentation**: UI/UX wireframes or mockups for any input forms or dashboards; prompt template specifications; workflow diagrams for each n8n (or equivalent) flow.
- **User documentation**: user guides per persona (how a Training Lead submits a topic; how a Reviewer approves assets; how a Learner navigates the LMS); admin guide for managing templates and sources.

### Step 8 — Define the build and deployment process

Set up the engineering pipeline before writing production code.

- Define the repository structure: source code, prompt library, n8n workflow exports, infrastructure-as-code, documentation — all in one repo with clear folder conventions.
- Set up environments: development, staging/UAT, and production. Each should mirror the others.
- Define the CI/CD pipeline: automated linting, prompt format validation, integration tests, and deployment steps.
- Define the monitoring and alerting strategy: workflow success/failure rates, LLM API errors, latency, cost tracking.
- Document the runbook for common operational tasks (adding a new trusted source, updating a prompt, rotating API keys).

### Step 9 — Incremental: code, test, deploy

Build in short cycles, delivering working functionality at the end of each sprint.

- Start with the thinnest possible slice that delivers real value: the topic intake form → research node → master content brief saved to storage.
- Expand one feature at a time: add video script generation, then slide generation, then infographic, then quiz — each verified end-to-end before the next is started.
- Write tests alongside the code: unit tests for utility functions, schema validation for prompt outputs, integration tests for each workflow node, and UAT sign-off with a real content owner before marking a feature done.
- Collect feedback after each deployment and feed it back into the prompt library and workflow design immediately — do not batch it up.
- Track velocity and quality metrics (modules generated, review pass rate, learner ratings) from the first release and use them to prioritise the next sprint.

