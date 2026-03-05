# Business Requirements Document (BRD)
## JBS Enterprise Content Platform — Generic (Domain-Configurable)

| Field | Detail |
|---|---|
| **Document version** | 0.1 – Draft |
| **Date** | March 5, 2026 |
| **Organisation** | Jade Business Services (JBS) |
| **Prepared by** | [PLACEHOLDER – Author name] |
| **Reviewed by** | [PLACEHOLDER – Reviewer name(s)] |
| **Status** | Draft – pending stakeholder review |

---

## ⚡ Core Premise — Read This First

> **This document describes a single, domain-configurable platform — not three separate systems.**

The JBS Enterprise Content Platform is architected as **one shared platform** that powers multiple business functions through configurable **Domain Profiles**. A Domain Profile is a named configuration of the platform's capabilities tailored to a specific business use case: vocabulary, content templates, knowledge sources, workflow rules, governance checklists, audience definitions, and distribution channels all vary by profile. The underlying platform — intake, research, generation, review, approval, publishing, consumption tracking, and analytics — is built once and shared.

**Three Domain Profiles are defined in this document:**

| Profile name | Business function | Primary output |
|---|---|---|
| **Training** | Corporate learning & development | Training modules, video scripts, assessments |
| **Marketing** | Content marketing & campaigns | Campaign assets, blogs, decks, social content |
| **HR Induction** | Employee onboarding & HR communications | Induction packs, policy guides, onboarding checklists |

Additional Domain Profiles can be added in the future (e.g., Sales Outreach, Client Enablement, Regulatory Compliance) without rebuilding the platform. This is an explicit design goal.

The table below illustrates how the same platform capability maps to different domain-specific language:

| Platform capability | Training profile | Marketing profile | HR Induction profile |
|---|---|---|---|
| Content request intake | Topic request | Campaign brief | Onboarding request |
| Audience definition | Learner role & level | Buyer persona | Employee type & join date |
| Knowledge grounding | Course knowledge base | Brand & product content | HR policies & handbook |
| Research output | Research brief | Market & competitor brief | Policy summary |
| Structured plan | Master content brief | Campaign content plan | Induction content plan |
| Generated assets | Video script, slides, infographic, quiz | Blog post, social copy, deck, email sequence | Welcome pack, checklist, FAQ, policy doc |
| Review & approval | Instructional review | Brand & legal review | HR & compliance review |
| Distribution channel | LMS / learning portal | CMS / email / social | HR portal / email |
| Consumption signal | Module completion | Content engagement | Induction milestone |
| Governance rule | Domain accuracy + confidentiality | Brand compliance + legal | Policy accuracy + legal compliance |

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Business Context & Problem Statement](#2-business-context--problem-statement)
3. [Objectives & Success Criteria](#3-objectives--success-criteria)
4. [Scope](#4-scope)
5. [Platform Concepts & Terminology](#5-platform-concepts--terminology)
6. [Stakeholders & User Roles](#6-stakeholders--user-roles)
7. [Platform-Level Functional Requirements](#7-platform-level-functional-requirements)
   - FR-1: Domain Profile Configuration
   - FR-2: Content Request Intake
   - FR-3: Research & Knowledge Grounding
   - FR-4: Structured Content Planning
   - FR-5: Asset Generation
   - FR-6: Review & Approval
   - FR-7: Publishing & Distribution
   - FR-8: Consumption & Engagement Tracking
   - FR-9: Content Versioning & Lifecycle
   - FR-10: User Management & Access Control
8. [Domain Profile Requirements](#8-domain-profile-requirements)
   - 8.1 Training Profile
   - 8.2 Marketing Profile
   - 8.3 HR Induction Profile
9. [Inputs & Outputs](#9-inputs--outputs)
10. [Data & Metadata Requirements](#10-data--metadata-requirements)
11. [Content Lifecycle & Workflow Requirements](#11-content-lifecycle--workflow-requirements)
12. [Governance & Compliance Requirements](#12-governance--compliance-requirements)
13. [Non-Functional Requirements](#13-non-functional-requirements)
14. [Reporting & Analytics Requirements](#14-reporting--analytics-requirements)
15. [Future Domain Profiles](#15-future-domain-profiles)
16. [Constraints & Assumptions](#16-constraints--assumptions)
17. [Open Questions & Decisions Required](#17-open-questions--decisions-required)
18. [Glossary](#18-glossary)

---

## 1. Executive Summary

JBS requires a scalable, AI-assisted content platform that reduces the manual effort of producing high-quality content across multiple business functions. Rather than building isolated tools for each function, JBS will build **one Enterprise Content Platform** with a configurable Domain Profile architecture. The same core workflow — request, research, plan, generate, review, approve, publish, track — underpins every function. Domain Profiles configure that workflow for a specific business context.

Phase 1 will implement the platform core and three Domain Profiles: Training, Marketing, and HR Induction. Future phases will add additional profiles (e.g., Sales Outreach, Client Enablement) using the same shared infrastructure, governance framework, and analytics layer.

---

## 2. Business Context & Problem Statement

### 2.1 Organisation Background

Jade Business Services (JBS) is a Data & AI solutions company specialising in the Energy & Utilities industry. JBS requires a continuous supply of high-quality content across several business functions:

- **Training & Learning Development:** Technical (Data & AI) and domain (Energy & Utilities) training for internal staff and, potentially, client personnel.
- **Marketing:** Thought leadership, campaign content, and sales-enabling material for the Data & AI and Energy & Utilities market.
- **HR Induction:** Structured onboarding content for new employees, covering company policies, role expectations, tools, and culture.

### 2.2 Current Situation

Across all three functions, JBS faces the same root problem expressed in different contexts:

- Content is created manually and inconsistently, with no reusable process.
- Subject matter experts and content leads spend disproportionate time on production rather than on review and quality.
- Different formats (videos, decks, written articles, checklists) require disconnected, ad-hoc effort each time.
- There is no organised system for managing content through a lifecycle from request to retirement.
- There is no analytics visibility into how content is consumed or whether it achieves its purpose.

### 2.3 Problem Statement

JBS lacks a systematic, scalable way to produce, govern, distribute, and measure the effectiveness of content across its business functions. Each function reinvents the same process independently. The organisation needs a **single configurable platform** where a content request in any domain drives a consistent, high-quality, auditable content production and distribution workflow with minimal manual overhead per item.

---

## 3. Objectives & Success Criteria

### 3.1 Business Objectives

1. Build one shared platform that serves Training, Marketing, and HR Induction content needs, eliminating duplication of infrastructure and process.
2. Dramatically reduce the time and effort required to produce a complete set of content assets for any given request in any domain.
3. Ensure structural consistency and quality across all content, regardless of domain.
4. Make content discoverable and consumable by the right audience at the right time, in the right channel.
5. Establish governance so content is accurate, current, compliant, and free from confidential or sensitive information leakage.
6. Provide visibility into content production performance and consumption effectiveness across all domains.
7. Design the platform to be extensible: new Domain Profiles must be addable without rebuilding core capabilities.

### 3.2 Success Criteria

| Criterion | Measure |
|---|---|
| Content production speed | Time from content request to first complete draft asset set, per domain |
| Content quality | First-submission review pass rate per domain (target: [PLACEHOLDER]%) |
| Platform reuse | Percentage of total content produced across all domains vs. domain-specific tooling |
| Audience adoption | Percentage of target audience who consume at least one piece of content within [PLACEHOLDER] of publication |
| Audience satisfaction | Average content feedback rating per domain (target: [PLACEHOLDER] out of 5) |
| Governance compliance | Percentage of published content items with completed domain governance checklist |
| Extensibility | Time required to configure and launch a new Domain Profile (target: [PLACEHOLDER]) |

---

## 4. Scope

### 4.1 In Scope — Phase 1

- Design and implementation of the platform core (all domain-agnostic capabilities).
- Configuration and launch of three Domain Profiles: Training, Marketing, HR Induction.
- End-to-end content lifecycle per profile: intake → research → planning → generation → review → approval → publishing → tracking → archiving.
- Role-based access control across all profiles, with full separation of content and permissions between domains.
- Configurable governance checklists per domain.
- Analytics covering both content production metrics and audience consumption metrics across all profiles.

### 4.2 Out of Scope — Phase 1

- Actual video production (the platform generates scripts; production is performed externally by a video producer).
- Actual graphic design execution (the platform generates specifications; design is performed externally).
- Real-time personalisation based on live behavioural signals (deferred to a future phase).
- External client-facing portals (JBS-internal content distribution only in Phase 1 unless explicitly stated per profile).
- Additional Domain Profiles beyond the three defined here (see Section 15).

---

## 5. Platform Concepts & Terminology

These terms are used throughout the document to describe platform-level concepts that apply regardless of domain.

| Term | Definition |
|---|---|
| **Domain Profile** | A named configuration of the platform that tailors all capabilities — vocabulary, templates, workflows, governance rules, audience definitions, distribution channels — to a specific business function. |
| **Content Request** | The intake event that initiates a new content production workflow. Contains the topic or brief, the target audience, the required formats, and any domain-specific metadata. |
| **Knowledge Base** | The curated set of internal and external sources approved for grounding generated content within a given Domain Profile. Each profile has its own Knowledge Base configuration. |
| **Content Plan** | The structured document generated after research that defines the core message, objectives, audience details, narrative structure, key concepts, and visual requirements. It is the master blueprint from which all content assets are generated. |
| **Content Asset** | A discrete output document generated for a content request (e.g., a video script, a blog post, an induction checklist). Each request may produce multiple assets. |
| **Asset Type** | The format of a content asset. Asset types are configured per Domain Profile (e.g., the Training profile uses "Video Script"; the Marketing profile uses "Blog Post"). |
| **Content Item** | A fully approved and published collection of all assets associated with a single content request, together with its metadata. Equivalent to a "module" in Training, a "campaign asset set" in Marketing, or an "induction pack" in HR. |
| **Audience Group** | A defined target audience configuration within a Domain Profile (e.g., "Intermediate Data Engineer" in Training; "CTO persona" in Marketing; "Graduate joiner" in HR Induction). |
| **Governance Checklist** | A domain-specific set of quality and compliance checks that must be completed by a reviewer before a content item can be approved for publishing. |
| **Distribution Channel** | The platform or mechanism through which a published content item is delivered to its intended audience. Configured per Domain Profile (e.g., LMS for Training, CMS for Marketing, HR portal for Induction). |
| **Consumption Signal** | An event indicating that an audience member has engaged with a content item (e.g., module completed, article read, induction task acknowledged). |
| **Content Lifecycle** | The sequence of states a content item passes through from request to archive, with defined rules for transitions between states. |

---

## 6. Stakeholders & User Roles

### 6.1 Platform-Level Roles

These roles exist at the platform level and operate across all Domain Profiles.

| Role | Description |
|---|---|
| **Platform Administrator** | Configures Domain Profiles, manages the Knowledge Base registry, controls user access and role assignments, monitors platform health and usage. |
| **Executive / Sponsor** | Receives cross-domain high-level reporting on content production volume, audience adoption, and business impact. |

### 6.2 Domain-Level Roles

Each Domain Profile configures the following role types with domain-specific naming. The platform enforces strict separation: a user with a role in one profile cannot access content or configuration of another profile unless explicitly granted.

| Platform role | Training profile | Marketing profile | HR Induction profile |
|---|---|---|---|
| **Content Requester** | Training Lead / SME | Marketing Manager / Campaign Owner | HR Manager / HRBP |
| **Content Reviewer** | Instructional Designer + SME | Brand Manager + Legal Reviewer | HR Policy Owner + Legal/Compliance |
| **Content Approver** | Training Lead | Head of Marketing | HR Director |
| **Content Producer** | Video Producer / Designer | Copywriter / Designer | HR Content Specialist |
| **Content Consumer** | Learner | Website visitor / prospect / internal reader | New employee |
| **Consumer Manager** | People Manager (assigns modules) | [Not applicable in Phase 1] | Line Manager (tracks induction progress) |
| **Domain Administrator** | Training Administrator | Marketing Administrator | HR Administrator |

---

## 7. Platform-Level Functional Requirements

These requirements apply to all Domain Profiles. Domain-specific elaborations are in Section 8.

---

### FR-1: Domain Profile Configuration

| ID | Requirement |
|---|---|
| FR-1.1 | The platform shall support the creation and management of Domain Profiles without requiring code changes. Profile configuration shall be data-driven. |
| FR-1.2 | Each Domain Profile shall independently configure: profile name and description; audience group definitions; content request metadata fields; Knowledge Base sources; content template set (asset types and structures); workflow steps and assignees; governance checklist items; distribution channels; and notification templates. |
| FR-1.3 | A Domain Profile shall be activatable and deactivatable by the Platform Administrator without affecting other active profiles. |
| FR-1.4 | Changes to a Domain Profile configuration shall be versioned and auditable. |
| FR-1.5 | The platform shall support at least [PLACEHOLDER — number] concurrent active Domain Profiles. |

---

### FR-2: Content Request Intake

| ID | Requirement |
|---|---|
| FR-2.1 | The platform shall provide a structured intake form for each Domain Profile. The fields presented shall be configurable per profile. |
| FR-2.2 | All intake forms shall capture, at minimum: a title or subject, the target audience group, the required asset types, and any free-text context or brief. Additional domain-specific fields are configured per profile (see Section 8). |
| FR-2.3 | The platform shall validate that all required fields are completed before accepting a content request. |
| FR-2.4 | On submission, the platform shall auto-classify the request into a content category, content type, and audience level based on the intake metadata. The requester shall be able to override the auto-classification. |
| FR-2.5 | The intake interface shall be accessible via a web form. Optionally, intake shall also be triggerable via a messaging platform command, configurable per Domain Profile. |
| FR-2.6 | Each accepted content request shall result in a Content Record being created and assigned a unique identifier. |
| FR-2.7 | The requester shall receive confirmation of submission with the assigned Content Record ID. |

---

### FR-3: Research & Knowledge Grounding

| ID | Requirement |
|---|---|
| FR-3.1 | For each content request, the platform shall compile a structured Research Output using the Knowledge Base configured for the active Domain Profile. |
| FR-3.2 | The Research Output structure shall be configurable per Domain Profile. It shall include, at minimum: key concepts and definitions, relevant examples, common challenges, and current trends. |
| FR-3.3 | The Research Output shall include source citations for all material drawn from the Knowledge Base. |
| FR-3.4 | The platform shall draw from JBS internal content (proposals, policies, brand assets, etc.) and from approved external sources, as configured per Domain Profile. |
| FR-3.5 | The platform shall not use sources outside the profile's approved Knowledge Base without explicit human approval. |
| FR-3.6 | The Research Output shall be stored against the Content Record and shall be available for human review before subsequent steps proceed. |
| FR-3.7 | A reviewer shall be able to flag the Research Output as insufficient, triggering a re-research step before the Content Plan is generated. |

---

### FR-4: Structured Content Planning

| ID | Requirement |
|---|---|
| FR-4.1 | The platform shall generate a Content Plan from the Research Output and content request metadata. |
| FR-4.2 | The Content Plan structure shall be configurable per Domain Profile. It shall include, at minimum: a core message, audience and level description, content objectives, a narrative or structural arc, key concepts or messages, and an indication of the assets to be produced. |
| FR-4.3 | The Content Plan shall be stored against the Content Record and shall be available for review and editing by the Content Reviewer or Approver before asset generation proceeds. |
| FR-4.4 | The platform shall support manual editing of the Content Plan. Edits shall be tracked with the editor's identity and timestamp. |
| FR-4.5 | Asset generation shall not proceed until the Content Plan has been reviewed and accepted (explicitly or implicitly by timeout, configurable per profile). |

---

### FR-5: Asset Generation

| ID | Requirement |
|---|---|
| FR-5.1 | The platform shall generate all asset types requested in the intake form from the approved Content Plan. |
| FR-5.2 | Asset types and their output structure (template) shall be fully configurable per Domain Profile. |
| FR-5.3 | All generated assets shall be labelled as version V1 at creation and stored against the Content Record. |
| FR-5.4 | The platform shall support generation of a simplified variant of any asset for a different audience level (e.g., a simplified "executive summary" or "new joiner" version), on request. |
| FR-5.5 | The platform shall support regeneration of an individual asset without needing to regenerate all other assets for the same Content Record. |
| FR-5.6 | Asset generation shall be performed in parallel where asset types are independent of one another. |
| FR-5.7 | The platform shall present a list of supplementary materials required to produce final deliverables from the generated assets (e.g., a list of required visual assets for a video script). |

---

### FR-6: Review & Approval

| ID | Requirement |
|---|---|
| FR-6.1 | On asset generation, the platform shall automatically notify the assigned reviewers for the Domain Profile that content is ready for review. |
| FR-6.2 | Reviewers shall be able to view all assets for a Content Record in a single consolidated view. |
| FR-6.3 | Reviewers shall be able to apply the domain-configured Governance Checklist to each asset and record pass/fail against each checklist item. |
| FR-6.4 | Reviewers shall be able to approve or reject each asset individually, with mandatory comments on rejection. |
| FR-6.5 | Approved and rejected assets shall be clearly distinguished in the interface. |
| FR-6.6 | Rejected assets shall trigger a Revision Required state for that asset only. Other approved assets for the same Content Record shall not be affected. |
| FR-6.7 | The platform shall track the full review history of every asset: who reviewed, what decision, what checklist responses, what comments, and when. |
| FR-6.8 | All assets for a Content Record must reach Approved status before the Content Record can be published. |
| FR-6.9 | The platform shall support escalation of a review decision to the Content Approver role when a reviewer and requester cannot agree. |

---

### FR-7: Publishing & Distribution

| ID | Requirement |
|---|---|
| FR-7.1 | Once all assets are approved, the Content Approver shall be able to publish the Content Record to the distribution channel(s) configured for the Domain Profile. |
| FR-7.2 | Distribution channel configuration shall be per Domain Profile (e.g., LMS for Training; CMS for Marketing; HR portal for Induction). |
| FR-7.3 | On publishing, the platform shall write the content item metadata to the configured distribution channel(s), including all audience tags, prerequisites, and version information. |
| FR-7.4 | The platform shall support scheduling of a publish action for a future date and time, per Domain Profile. |
| FR-7.5 | The platform shall notify the target audience group (or a subset) when a new content item is published, using the notification template configured for the Domain Profile. |
| FR-7.6 | The platform shall support targeting of a published content item to specific audience groups, preventing access by other audience groups or profiles. |
| FR-7.7 | For Domain Profiles where audience managers can assign content, the platform shall support assigning a content item to specific audience members and tracking acknowledgement or completion. |

---

### FR-8: Consumption & Engagement Tracking

| ID | Requirement |
|---|---|
| FR-8.1 | The platform shall record consumption signals from each active distribution channel. The definition of a consumption signal shall be configurable per Domain Profile. |
| FR-8.2 | The platform shall record, at minimum, for each audience member and content item: whether the item was accessed, whether the consumption signal was triggered, when, and any feedback provided. |
| FR-8.3 | Where assessment items are part of a content item, the platform shall record attempt count, score, and pass/fail status per audience member. |
| FR-8.4 | The platform shall support audience members providing a rating (numeric) and optional free-text feedback on any content item. |
| FR-8.5 | Audience managers shall be able to view consumption status for their assigned audience members. |

---

### FR-9: Content Versioning & Lifecycle

| ID | Requirement |
|---|---|
| FR-9.1 | Every published content item shall carry a version number (e.g., v1.0, v1.1, v2.0). |
| FR-9.2 | When a content item is revised, the previous version shall be retained and accessible for audit purposes. |
| FR-9.3 | A revision record shall capture what changed, the reason for the change, who made the change, and when. |
| FR-9.4 | The platform shall support archiving of outdated content items. Archived items shall no longer appear in the active catalogue but shall remain accessible for audit. |
| FR-9.5 | Audience members who have completed or consumed a content item that has subsequently been revised or archived shall be notified according to the notification rules configured for the Domain Profile. |
| FR-9.6 | The platform shall support setting a scheduled review date for each published content item. The Domain Administrator shall be alerted when a review date is reached. |

---

### FR-10: User Management & Access Control

| ID | Requirement |
|---|---|
| FR-10.1 | The platform shall enforce role-based access control. A user's permissions within the platform shall be determined by their assigned role(s). |
| FR-10.2 | Users may hold roles in multiple Domain Profiles, but content and configuration of one profile shall not be accessible to users acting in the context of a different profile unless explicitly granted. |
| FR-10.3 | The Platform Administrator shall be able to create, modify, and deactivate user accounts and role assignments without developer involvement. |
| FR-10.4 | The platform shall support single sign-on (SSO) integration with JBS's identity provider. |
| FR-10.5 | All user access events (login, content access, admin actions) shall be logged for audit purposes. |
| FR-10.6 | API access to the platform (for integration with distribution channels and other systems) shall be secured with managed credentials that are independently rotatable without affecting user access. |

---

## 8. Domain Profile Requirements

This section defines the specific configuration requirements for each of the three initial Domain Profiles. These requirements configure the platform capabilities defined in Section 7 — they do not define new platform capabilities.

---

### 8.1 Training Profile

**Purpose:** Produce modular training content covering two knowledge domains — Data & AI (technical) and Energy & Utilities (industry) — for internal JBS staff across multiple roles and seniority levels.

#### Audience Groups

| Audience group | Description |
|---|---|
| Data Engineer – Beginner/Intermediate/Advanced | Technical staff building data pipelines and infrastructure |
| Data Scientist – Beginner/Intermediate/Advanced | Technical staff building and deploying models |
| Analytics Engineer – Beginner/Intermediate/Advanced | Technical staff bridging data engineering and business analytics |
| Solution Architect – Intermediate/Advanced | Staff designing end-to-end Data & AI solutions |
| Project Manager | Staff managing delivery of Data & AI projects |
| Business Stakeholder | Client-side or internal non-technical stakeholders |

#### Content Request Intake Fields (Training-specific)

In addition to the platform-standard fields, a Training content request shall capture:
- Knowledge domain: Data & AI / Energy & Utilities / Both
- Sub-domain / topic area (from a controlled list maintained by the Training Administrator)
- Module type: Introduction / Concept Explainer / Deep Dive / Case Study
- Prerequisite modules (optional)
- Desired module duration (indicative)

#### Knowledge Base Sources (Training-specific)

The Training Knowledge Base shall include, at minimum:
- JBS internal content: proposals, solution decks, case studies, internal blogs, and past training materials
- **Data & AI sources:** peer-reviewed and practitioner publications covering machine learning, data engineering, MLOps, generative AI, and related fields
- **Energy & Utilities sources:** publications from major energy research bodies (e.g., NREL, IEA, IEEE Power & Energy Society), industry news, and regulatory/standards bodies (e.g., NERC, FERC)
- The Training Administrator shall maintain and update the approved source list

#### Asset Types (Training-specific)

| Asset type | Description |
|---|---|
| Research Brief | Structured topic summary with citations: key concepts, methods, applications, examples, challenges, trends |
| Master Content Brief | Core message, learning objectives, audience, prerequisites, narrative arc, JBS context, key terms, visual opportunities |
| Video Script | Scene-by-scene script with timestamps, narration (spoken style), on-screen text, visual direction, and a list of required visual assets |
| Slide Deck Outline | 10–15 slide structure with title, key bullets (max 5 per slide), visual description per slide, and design notes |
| Infographic Specification | Title, hero statistic, 5–7 supporting stats, optional process flow, optional comparison table, layout and icon guide |
| Assessment Items | 5–10 questions (MCQ and scenario-based) with correct answers and rationale |
| Simplified Variant | "New joiner" or "Leadership summary" version of any asset above, on request |

#### Governance Checklist (Training-specific)

Reviewers shall confirm:
- [ ] Domain content is technically accurate for the stated level
- [ ] Learning objectives are measurable and appropriate for the audience
- [ ] Content difficulty level matches the declared audience level and prerequisites
- [ ] No real client names, project-specific financials, or client-identifiable information is present
- [ ] All statistics are cited or clearly labelled as illustrative
- [ ] JBS brand voice is maintained
- [ ] Content is consistent with existing modules in the same learning path

#### Distribution Channel (Training-specific)

Published training modules shall be distributed to the JBS Learning Management System (LMS) or learning portal. The platform shall write module metadata (title, domain, audience role, level, prerequisites, asset links) to the LMS on publish.

#### Consumption Signal (Training-specific)

A consumption signal is recorded when a learner completes a module (watches the video or reads the content) and, where applicable, submits the assessment. Assessment scores and pass/fail status shall be recorded.

#### Learning Path Requirements (Training-specific)

- The Training Profile shall support the definition of ordered learning paths linking multiple modules for a given audience group.
- The system shall recommend a relevant learning path to a learner based on their declared role and level.
- Learners shall be able to take a pre-assessment to skip modules covering knowledge they can demonstrate.
- Managers shall be able to assign specific modules or full learning paths to individual team members and track completion.

---

### 8.2 Marketing Profile

**Purpose:** Produce and distribute marketing and thought leadership content aligned to JBS's positioning in Data & AI for Energy & Utilities.

#### Audience Groups

| Audience group | Description |
|---|---|
| Technical buyer (CTO / Head of Data) | Technical decision-makers at target organisations |
| Business buyer (COO / Head of Operations) | Business decision-makers at target organisations |
| Internal JBS staff | Sales, pre-sales, and delivery staff who need enablement content |
| Industry community | General public / LinkedIn / conference audience |

#### Content Request Intake Fields (Marketing-specific)

In addition to platform-standard fields:
- Campaign or initiative name
- Content objective: Awareness / Consideration / Enablement / Retention
- Target buyer persona
- Key message or point of view (free text)
- Publishing channel(s): Website / LinkedIn / Email / Event / Internal
- Deadline or campaign date

#### Knowledge Base Sources (Marketing-specific)

The Marketing Knowledge Base shall include:
- JBS brand and messaging guidelines
- JBS service and solution descriptions
- Past JBS publications, case studies, and thought leadership (anonymised)
- Competitor and market landscape references (approved by Marketing Administrator)
- Industry analyst reports relevant to Data & AI and Energy & Utilities

#### Asset Types (Marketing-specific)

| Asset type | Description |
|---|---|
| Market Research Summary | Structured summary of market context, audience pain points, competitor landscape, and trends |
| Campaign Content Plan | Core message, audience, objectives, narrative arc, key proof points, and asset list |
| Blog Post / Article | Structured long-form written content with headline, subheadings, body, and call-to-action |
| Social Media Copy | Platform-specific short-form copy variants (LinkedIn, Twitter/X) derived from the article |
| Presentation Deck Outline | 10–15 slide structure for event or sales enablement presentations |
| Email Copy | Subject line, preview text, and body copy for a campaign email |
| Infographic Specification | Data-driven visual content blueprint (stats, process, comparison, layout) |
| Simplified Variant | An "executive summary" or "plain language" version of any asset above, on request |

#### Governance Checklist (Marketing-specific)

Reviewers shall confirm:
- [ ] Content is factually accurate and does not make unsubstantiated claims
- [ ] Content is consistent with JBS brand voice and messaging guidelines
- [ ] No client-confidential information, project-specific financials, or identifiable client detail is present
- [ ] Legal review has been completed for any claims, statistics, or competitive references
- [ ] Content is appropriate for the declared publishing channel
- [ ] Calls to action are correct and links are valid

#### Distribution Channel (Marketing-specific)

Published marketing content shall be distributed to the configured publishing channel(s) declared in the content request (website CMS, email platform, social scheduling tool, or internal file share for enablement content).

#### Consumption Signal (Marketing-specific)

Consumption signals shall be defined per channel:
- Website: page views, estimated read time, downloads
- Email: open rate, click rate
- Social: impressions, engagement (likes, shares, comments)
- Internal: access confirmation

---

### 8.3 HR Induction Profile

**Purpose:** Produce structured, accurate, and compliant onboarding and induction content for new JBS employees.

#### Audience Groups

| Audience group | Description |
|---|---|
| Graduate / Entry-level joiner | New employees joining in a first professional role |
| Experienced hire | New employees joining with prior experience |
| Contractor / Consultant | Non-permanent staff requiring a subset of induction content |
| Internal transfer | Existing JBS staff moving to a new role or team |

#### Content Request Intake Fields (HR Induction-specific)

In addition to platform-standard fields:
- Induction content type: Company / Role / Policy / Tools & Systems / Culture / Compliance
- Department or team
- Relevant policies or documents that must be covered
- Acknowledgement required: Yes / No (determines whether a completion signal needs to be recorded)
- Effective date (required for policy-based content)

#### Knowledge Base Sources (HR Induction-specific)

The HR Induction Knowledge Base shall include:
- Current JBS HR policies and employee handbook (maintained by HR)
- Organisational structure and role descriptions
- Tools and systems guides (IT onboarding documentation)
- Legal and compliance obligations applicable to JBS employees (maintained by HR/Legal)
- Culture and values documentation

All HR Induction Knowledge Base sources shall be reviewed and re-approved by the HR Administrator at a minimum of every [PLACEHOLDER — e.g., 6 months] to ensure currency.

#### Asset Types (HR Induction-specific)

| Asset type | Description |
|---|---|
| Policy Summary | Plain-language summary of a policy or set of policies with key obligations highlighted |
| Welcome Pack | Narrative introduction to the company, team, culture, and first-week expectations |
| Structured Checklist | Step-by-step onboarding checklist with tasks, responsible parties, and deadlines |
| FAQ Document | Answers to commonly asked questions for a given audience group or topic |
| Process Walkthrough | Step-by-step guide for completing a key process (e.g., expenses, leave requests) |
| Compliance Acknowledgement | A document the employee reads and acknowledges, creating an audit record |

#### Governance Checklist (HR Induction-specific)

Reviewers shall confirm:
- [ ] Content accurately reflects current HR policies and is consistent with the approved source documents
- [ ] Content complies with all applicable employment law and compliance obligations
- [ ] Language is plain, clear, and accessible to the declared audience group
- [ ] Any obligations requiring legal review have been reviewed and signed off
- [ ] Effective date and version are clearly stated on policy-related content
- [ ] Where acknowledgement is required, the acknowledgement mechanism is correctly configured

#### Distribution Channel (HR Induction-specific)

Published induction content shall be distributed to the JBS HR portal or intranet. Where acknowledgement is required, the platform shall record the employee's acknowledgement event with timestamp, forming part of the HR compliance record.

#### Consumption Signal (HR Induction-specific)

- For informational content: access/read confirmation.
- For compliance content: explicit acknowledgement by the employee (recorded as a compliance event).
- For checklists: task-by-task completion, with optional sign-off by the line manager.

---

## 9. Inputs & Outputs

### 9.1 Platform Inputs

| Input | Source | Description |
|---|---|---|
| Content request | Domain requester via intake form | Topic/brief, audience, level, asset types, domain-specific fields |
| JBS internal content | Internal document repository | Primary internal knowledge source; scope and access configurable per Domain Profile |
| Approved external sources | Knowledge Base Registry, per Domain Profile | Curated list of trusted external publications and resources per domain |
| Reviewer feedback | Domain reviewers | Governance checklist responses, approve/reject decisions, comments |
| Audience profile data | HR system / user profile | Role, level, team, and manager, used for audience targeting and consumption tracking |
| Consumption signals | Distribution channels | Completion, engagement, and acknowledgement events from the channel the content is consumed in |

### 9.2 Platform Outputs

| Output | Description | Consumed by |
|---|---|---|
| **Research Output** | Structured summary of the topic with citations, drawn from the profile's Knowledge Base | Domain Reviewer / SME for accuracy check |
| **Content Plan** | Structured planning document: objectives, audience, narrative, key messages, asset list | Domain Reviewer; input to asset generation |
| **Generated Assets** | One or more assets per content request, per profile-configured asset types | Content Producers (for final production); end audiences (once published) |
| **Published Content Item** | Approved content item pushed to distribution channel(s) with metadata and audience tags | End audience (Learners, Readers, New Employees) |
| **Consumption Record** | Per-audience-member record of access, completion, score, and feedback | Audience managers; Analytics |
| **Analytics Reports** | Production metrics and consumption metrics per Domain Profile and cross-profile | Domain Administrators, Platform Administrator, Executives |
| **Audit Log** | Full record of all platform actions: requests, generation events, review decisions, publish events, access events | Platform Administrator; Legal/Compliance |

---

## 10. Data & Metadata Requirements

### 10.1 Content Record

Every content request shall be represented as a record with the following fields. Domain-specific additional fields are added by Domain Profile configuration.

| Field | Type | Description |
|---|---|---|
| `content_id` | Unique identifier | System-generated |
| `domain_profile` | Reference | Which Domain Profile this record belongs to |
| `title` | Text | Short descriptive title |
| `content_category` | Text | Profile-configured category (e.g., sub-domain in Training; campaign type in Marketing) |
| `content_type` | Enum | Profile-configured type (e.g., module type in Training; content format in Marketing) |
| `audience_group` | Reference | Target audience group from the profile's audience group list |
| `audience_level` | Enum | Complexity or seniority level (if applicable to the profile) |
| `asset_types_requested` | Multi-select | Asset types to be generated for this request |
| `status` | Enum | Requested / Research Complete / Plan Complete / Assets Generated / In Review / Revision Required / Approved / Published / Archived |
| `version` | Text | e.g., v1.0 |
| `requestor` | User reference | Who submitted the request |
| `reviewer(s)` | User reference(s) | Assigned reviewers |
| `approver` | User reference | Assigned approver |
| `scheduled_review_date` | Date | When the content item should be reviewed for continued accuracy |
| `prerequisite_content` | Reference list | Other content IDs that should be consumed first (if applicable) |
| `tags` | Multi-select / free text | Searchable keywords |
| `created_at` | Timestamp | |
| `last_modified_at` | Timestamp | |
| `approved_at` | Timestamp | |
| `published_at` | Timestamp | |
| `archived_at` | Timestamp | |
| `feedback_rating_avg` | Decimal | Average audience rating (populated post-publication) |
| `consumption_count` | Integer | Number of audience members who triggered the consumption signal |

### 10.2 Asset Record

| Field | Type | Description |
|---|---|---|
| `asset_id` | Unique identifier | System-generated |
| `content_id` | Reference | Parent Content Record |
| `asset_type` | Enum | Profile-configured asset type |
| `version` | Text | e.g., v1.0 |
| `content_location` | File reference | Storage location of the asset content |
| `status` | Enum | Draft / In Review / Revision Required / Approved |
| `governance_checklist_response` | Structured data | Reviewer's pass/fail responses per checklist item |
| `reviewer` | User reference | Who reviewed this asset |
| `review_comments` | Text | Free text comments from reviewer |
| `reviewed_at` | Timestamp | |
| `created_at` | Timestamp | |

### 10.3 Knowledge Base Registry

| Field | Description |
|---|---|
| `source_id` | Unique identifier |
| `domain_profile` | Which profile(s) this source is approved for |
| `name` | Human-readable name |
| `description` | What this source provides |
| `source_type` | Internal / External |
| `status` | Active / Inactive |
| `approved_by` | Administrator who added/approved this source |
| `last_reviewed` | Date the source was last validated for accuracy and continued relevance |
| `next_review_due` | Date by which this source must be re-validated |

### 10.4 Audience Member Record

| Field | Description |
|---|---|
| `member_id` | Unique identifier (linked to organisational identity / HR system) |
| `name` | Full name |
| `domain_profile_access` | List of Domain Profiles the member is enrolled in |
| `audience_group` | Assigned audience group per profile |
| `manager_id` | Reference to line manager's record |
| `content_assigned` | List of content IDs assigned to this member |
| `content_consumed` | List of content IDs for which the consumption signal has been recorded, with date |
| `assessment_results` | Per-content assessment scores (where applicable) |
| `feedback_given` | Per-content rating and optional comment |
| `acknowledgements` | List of compliance acknowledgement records (HR Profile) |

### 10.5 Domain Profile Configuration Record

| Field | Description |
|---|---|
| `profile_id` | Unique identifier |
| `profile_name` | Human-readable name (e.g., "Training", "Marketing", "HR Induction") |
| `status` | Active / Inactive |
| `intake_fields` | Configuration of custom intake form fields |
| `audience_groups` | List of defined audience groups |
| `knowledge_base_sources` | List of approved Knowledge Base source IDs |
| `asset_types` | List of configured asset types and their output template specifications |
| `workflow_steps` | Ordered list of workflow steps with assigned roles |
| `governance_checklist` | List of checklist items with pass/fail type |
| `distribution_channels` | Configuration of publish targets |
| `notification_templates` | Notification content per workflow event |
| `consumption_signal_definition` | What constitutes a consumption signal for this profile |
| `version` | Configuration version |
| `last_modified_by` | Administrator who last edited the configuration |
| `last_modified_at` | Timestamp |

---

## 11. Content Lifecycle & Workflow Requirements

### 11.1 Universal Content Lifecycle States

The following lifecycle states apply to all Domain Profiles. State transition rules and notification events may vary per profile configuration.

```
Requested
  → Research Complete
    → Plan Complete
      → Assets Generated
        → In Review
          → Revision Required (→ Assets Generated, loops until no rejections remain)
          → Approved
            → Published
              → Archived
```

### 11.2 State Transition Rules

| From | To | Triggered by | Condition |
|---|---|---|---|
| — | Requested | Requester submits intake form | Valid intake form submitted |
| Requested | Research Complete | System | Research Output successfully generated |
| Research Complete | Plan Complete | System | Content Plan successfully generated |
| Plan Complete | Assets Generated | System | All requested asset types generated |
| Assets Generated | In Review | System | Automatic; reviewers notified |
| In Review | Revision Required | Reviewer | Any asset rejected with comment |
| In Review | Approved | Reviewer + Approver | All assets individually approved and Governance Checklist completed |
| Revision Required | Assets Generated | System | Revised asset(s) regenerated |
| Approved | Published | Content Approver | Manual publish action, immediately or on scheduled date |
| Published | Archived | Domain Administrator or Content Approver | Manual archive action |

### 11.3 Notification Requirements

| Event | Recipient |
|---|---|
| Content request submitted | Requester (confirmation) |
| Research Output ready | Content Reviewer (optional, configurable per profile) |
| Assets ready for review | Assigned reviewers |
| Asset rejected | Requester |
| All assets approved | Requester + Content Approver |
| Content item published | Target audience group (per profile notification template) |
| Content item assigned | Specific audience member (if assignment model is used) |
| Content item revised / superseded | Audience members who consumed the previous version |
| Scheduled review date reached | Domain Administrator |

---

## 12. Governance & Compliance Requirements

### 12.1 Governance Checklist

| ID | Requirement |
|---|---|
| GR-1 | Every content item must have a completed Governance Checklist before it can reach Approved status. |
| GR-2 | The Governance Checklist shall be configurable per Domain Profile. It shall be defined and maintained by the Domain Administrator in consultation with Legal/Compliance where required. |
| GR-3 | The platform shall record each reviewer's responses to every checklist item, with timestamp. |

### 12.2 Confidentiality

| ID | Requirement |
|---|---|
| GR-4 | No real client names, project-specific financials, or client-identifiable information shall appear in any published content item. This applies to all Domain Profiles. |
| GR-5 | The Governance Checklist for every Domain Profile shall include a confidentiality check item. |

### 12.3 Data Privacy

| ID | Requirement |
|---|---|
| GR-6 | The platform shall handle personal data (audience member records, consumption records, HR acknowledgement records) in compliance with applicable data privacy law. [PLACEHOLDER – specific regulations to be confirmed with Legal/Compliance.] |
| GR-7 | Audience member personal data shall not be shared across Domain Profiles without explicit authorisation. |

### 12.4 Knowledge Source Control

| ID | Requirement |
|---|---|
| GR-8 | Only sources on the profile's approved Knowledge Base Registry shall be used to ground generated content. |
| GR-9 | The Domain Administrator shall review and re-validate Knowledge Base sources on the schedule defined in the registry configuration. |
| GR-10 | Requests to add new sources shall require Domain Administrator approval. |

### 12.5 Audit Trail

| ID | Requirement |
|---|---|
| GR-11 | All content generation, review, approval, publish, archive, and access events shall be logged with user identity, action, and timestamp. |
| GR-12 | For HR Induction acknowledgement events, the compliance record shall be tamper-evident and retained for at least [PLACEHOLDER — e.g., duration of employment + 2 years]. |
| GR-13 | Audit logs shall be retained for a minimum of [PLACEHOLDER — e.g., 2 years] across all Domain Profiles. |

---

## 13. Non-Functional Requirements

| ID | Category | Requirement |
|---|---|---|
| NFR-1 | Extensibility | Adding a new Domain Profile must not require changes to the platform core. Profile configuration must be entirely data-driven. |
| NFR-2 | Scalability | The platform must support concurrent content requests across all active Domain Profiles without performance degradation. |
| NFR-3 | Consistency | All generated assets must conform to the template structure configured for their asset type in the active Domain Profile. |
| NFR-4 | Portability | The platform must not create hard dependencies on any single vendor's proprietary format. All content must be exportable in open/standard formats. |
| NFR-5 | Separation of concerns | Content, configuration, and consumption data for one Domain Profile must be fully isolated from other Domain Profiles at the data level. |
| NFR-6 | Turnaround | A full set of draft assets for a new content request must be available for review within [PLACEHOLDER] of intake submission. |
| NFR-7 | Availability | The platform must be available during JBS business hours with a minimum uptime of [PLACEHOLDER — e.g., 99%]. |
| NFR-8 | Usability | Non-technical users (requesters, reviewers, approvers, audience members) must be able to operate the platform without developer assistance. |
| NFR-9 | Maintainability | Domain Profile configuration, content templates, and Knowledge Base sources must be updatable by a Domain Administrator without code changes. |
| NFR-10 | Auditability | All platform actions must be logged and retrievable by the Platform Administrator. |
| NFR-11 | Cost | [PLACEHOLDER — Budget envelope for infrastructure and tooling to be confirmed.] |

---

## 14. Reporting & Analytics Requirements

### 14.1 Content Production Metrics (per Domain Profile and cross-profile)

| Metric | Description |
|---|---|
| Requests submitted (period) | Number of new content requests per profile per week/month |
| Time to first draft | Elapsed time from intake to completion of asset generation |
| Review cycle time | Elapsed time from assets generated to all assets approved |
| First-pass approval rate | Percentage of content items approved without revision, per profile |
| Content items published (period) | Number of published items per profile per period |
| Content items by category/type | Breakdown of published content by configurable taxonomy per profile |

### 14.2 Audience Consumption Metrics (per Domain Profile)

| Metric | Description |
|---|---|
| Content item access count | Number of times each item has been accessed |
| Consumption signal rate | Percentage of reached audience members who triggered the consumption signal |
| Assessment pass rate | Percentage of first-attempt passes (Training and HR Induction) |
| Completion / acknowledgement rate | Percentage of assigned audience who completed or acknowledged required content |
| Average feedback rating | Average rating per item and per profile |
| Content catalogue coverage | Percentage of defined audience groups with at least one relevant published item |

### 14.3 Reporting Audiences

| Audience | Report scope |
|---|---|
| Domain Administrator | Production pipeline and consumption summary for their profile |
| Audience Manager | Assigned audience members' consumption status and scores |
| Executive / Sponsor | Cross-profile summary: content volume, adoption rates, feedback, operational efficiency |
| Platform Administrator | Cross-profile system health, audit compliance rate, Knowledge Base currency |

---

## 15. Future Domain Profiles

The platform architecture is designed to accept additional Domain Profiles beyond the three defined here. The following are candidates for future phases. Business requirements for these profiles will be defined separately.

| Profile name | Business function | Primary output |
|---|---|---|
| Sales Outreach | AI-assisted outbound sales engagement | Prospecting research, outreach sequences, follow-up summaries |
| Client Enablement | Onboarding and enabling JBS clients to use JBS-delivered solutions | Client user guides, solution explainer packs, change management content |
| Regulatory & Compliance | Internal compliance training and documentation | Policy updates, compliance training modules, regulatory briefings |
| Partner Enablement | Equipping JBS channel partners | Partner-facing decks, co-marketing assets, technical briefs |

---

## 16. Constraints & Assumptions

### 16.1 Constraints

| ID | Constraint |
|---|---|
| C-1 | Adding a new Domain Profile must not require engineering changes to the platform core. |
| C-2 | Content produced by the platform must never contain real client names, project-specific financials, or client-identifiable information, regardless of Domain Profile. |
| C-3 | Content and data from one Domain Profile must not be visible or accessible to users operating in the context of a different Domain Profile. |
| C-4 | [PLACEHOLDER — Any regulatory or legal constraints applicable to JBS's industry or jurisdiction.] |
| C-5 | [PLACEHOLDER — Budget and resource constraints.] |

### 16.2 Assumptions

| ID | Assumption |
|---|---|
| A-1 | JBS has existing repositories of internal documents relevant to each Domain Profile (training materials, brand assets, HR policies) that can serve as initial Knowledge Base inputs. |
| A-2 | Actual video production, graphic design execution, and final copyediting remain human-in-the-loop activities that use platform-generated assets as inputs, not final deliverables. |
| A-3 | Each Domain Profile will have a designated Domain Administrator responsible for maintaining its configuration and Knowledge Base. |
| A-4 | The distribution channel for each Domain Profile (LMS, CMS, HR portal) will be determined during the technology selection phase. |
| A-5 | All JBS employees have access to a web-based interface and can access the platform via browser. |
| A-6 | The HR system or a manual profile management process will maintain current role and seniority data for all JBS employees. |

---

## 17. Open Questions & Decisions Required

| # | Question | Owner | Target date |
|---|---|---|---|
| OQ-1 | What is the chosen LMS / learning portal for the Training Profile? Criteria: SCORM support, SSO, completion tracking, cost. | IT / Training Lead | [PLACEHOLDER] |
| OQ-2 | What CMS or publishing platform will be used for the Marketing Profile? | IT / Marketing | [PLACEHOLDER] |
| OQ-3 | What HR portal or intranet platform will be used for the HR Induction Profile? | IT / HR | [PLACEHOLDER] |
| OQ-4 | What is the JBS identity provider / SSO system for platform authentication? | IT | [PLACEHOLDER] |
| OQ-5 | What is the internal document storage platform? (SharePoint, Google Drive, etc.) | IT | [PLACEHOLDER] |
| OQ-6 | What data privacy regulations apply to audience member records held by this platform? | Legal / Compliance | [PLACEHOLDER] |
| OQ-7 | What retention periods apply to audit logs, HR acknowledgement records, and content version history? | Legal / Compliance | [PLACEHOLDER] |
| OQ-8 | What is the target turnaround SLA for draft asset generation from intake? | Sponsor / Domain Leads | [PLACEHOLDER] |
| OQ-9 | Should Marketing Profile content be distributed externally in Phase 1 or remain internal-facing only? | Marketing / Sponsor | [PLACEHOLDER] |
| OQ-10 | What are the JBS competency frameworks (if any) that Training Profile learning objectives should align to? | HR / Training Lead | [PLACEHOLDER] |
| OQ-11 | What is the minimum viable number of Domain Profile configurations that must be supportable concurrently? | Platform Architect | [PLACEHOLDER] |
| OQ-12 | Should the platform support content co-authoring (multiple people editing a Content Plan simultaneously), or is sequential review sufficient for Phase 1? | Domain Leads | [PLACEHOLDER] |

---

## 18. Glossary

| Term | Definition |
|---|---|
| **Asset Type** | A configurable format category for a generated output (e.g., "Video Script", "Blog Post", "Policy Summary"). Asset types are defined per Domain Profile. |
| **Audience Group** | A named, defined target audience segment within a Domain Profile, used for content targeting and consumption tracking. |
| **Audience Manager** | A user who oversees a group of content consumers and can assign content and track consumption (e.g., a line manager or people manager). |
| **Compliance Acknowledgement** | A record that a specified audience member has read and accepted a specific content item, creating an auditable HR or legal record. |
| **Consumption Signal** | An event that records that an audience member has meaningfully engaged with a content item. Defined per Domain Profile (e.g., module completion, article read, checklist acknowledged). |
| **Content Item** | A fully approved and published set of assets associated with a single content request, together with all associated metadata. The equivalent terms per profile are: "module" (Training), "campaign asset set" (Marketing), "induction pack" (HR Induction). |
| **Content Plan** | A structured document generated after research that defines objectives, audience, narrative, key messages, and required assets. Serves as the blueprint for all asset generation. |
| **Content Record** | The master data record for a content request, tracking its state, metadata, assets, and history from intake to archive. |
| **Domain Administrator** | The user responsible for configuring and maintaining a specific Domain Profile, including Knowledge Base sources and governance checklists. |
| **Domain Profile** | A named, data-driven configuration of the platform that tailors all capabilities to a specific business function. The platform ships three initial profiles: Training, Marketing, HR Induction. |
| **Governance Checklist** | A domain-configured set of quality and compliance items that must be completed and passed by a reviewer before a content item can be approved. |
| **JBS** | Jade Business Services — the organisation commissioning this platform. |
| **Knowledge Base** | The curated set of internal and external sources approved for use in grounding generated content within a given Domain Profile. |
| **Knowledge Base Registry** | The managed list of all sources in the Knowledge Base, with approval status, review schedule, and currency status. |
| **Platform Administrator** | The user with cross-profile administrative access who manages Domain Profile configurations, user access, and system health. |
| **Research Output** | The structured document compiled from Knowledge Base sources as the first step of the content production workflow, before planning or asset generation. |
