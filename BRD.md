# Business Requirements Document (BRD)
## JBS Enterprise Training Content System

| Field | Detail |
|---|---|
| **Document version** | 0.1 – Draft |
| **Date** | March 5, 2026 |
| **Organisation** | Jade Business Services (JBS) |
| **Prepared by** | [PLACEHOLDER – Author name] |
| **Reviewed by** | [PLACEHOLDER – Reviewer name(s)] |
| **Status** | Draft – pending stakeholder review |

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Business Context & Problem Statement](#2-business-context--problem-statement)
3. [Objectives & Success Criteria](#3-objectives--success-criteria)
4. [Scope](#4-scope)
5. [Stakeholders & User Roles](#5-stakeholders--user-roles)
6. [Functional Requirements](#6-functional-requirements)
7. [Content Domain Requirements](#7-content-domain-requirements)
8. [Inputs & Outputs](#8-inputs--outputs)
9. [Data & Metadata Requirements](#9-data--metadata-requirements)
10. [Content Lifecycle & Workflow Requirements](#10-content-lifecycle--workflow-requirements)
11. [Governance & Compliance Requirements](#11-governance--compliance-requirements)
12. [Non-Functional Requirements](#12-non-functional-requirements)
13. [Reporting & Analytics Requirements](#13-reporting--analytics-requirements)
14. [Enterprise Scope – Future Phases](#14-enterprise-scope--future-phases)
15. [Constraints & Assumptions](#15-constraints--assumptions)
16. [Open Questions & Decisions Required](#16-open-questions--decisions-required)
17. [Glossary](#17-glossary)

---

## 1. Executive Summary

Jade Business Services (JBS) requires a **corporate training content system** that allows the organisation to produce high-quality, consistent training materials at scale without requiring significant manual effort for each new topic. The system must support two content domains — **Data & AI** (technical concepts) and **Energy & Utilities** (industry domain) — and must generate all key training asset types from a single topic request. In a later phase, the same platform must extend to support other business functions (HR, Marketing, Sales) under a unified enterprise framework.

---

## 2. Business Context & Problem Statement

### 2.1 Organisation Background

JBS is a Data & AI solutions company specialising in the Energy & Utilities industry. Its workforce includes data engineers, data scientists, analytics engineers, solution architects, project managers, and business stakeholders at client organisations. JBS regularly needs to train internal staff and, at times, client personnel on both technical Data & AI concepts and industry-specific Energy & Utilities concepts.

### 2.2 Current Situation

- Training content is created manually and inconsistently.
- Creating a new training module requires significant time investment from subject matter experts and content teams.
- There is no reusable, standardised process for content creation.
- Different formats (videos, slide decks, infographics, assessments) each require separate, disconnected efforts.
- There is no organised learning pathway mapped to employee roles and seniority levels.
- There is no mechanism to keep content current as domains evolve.

### 2.3 Problem Statement

JBS lacks a systematic, scalable way to produce training content. The effort required to create each new topic from scratch is unsustainable. The organisation needs a system where a single **topic request** drives the creation of all required training assets in a consistent, high-quality, and auditable manner, with minimal manual intervention per topic.

---

## 3. Objectives & Success Criteria

### 3.1 Business Objectives

1. Dramatically reduce the time and effort required to produce a complete set of training assets for any given topic.
2. Ensure consistency in structure, tone, depth, and quality across all training content.
3. Build a library of modular, versioned training content covering both technical and domain knowledge areas relevant to JBS.
4. Make training content discoverable and consumable by JBS employees according to their role, level, and learning goals.
5. Establish governance so that content remains accurate, current, and free from confidential or client-identifiable information.
6. Lay the foundation for a broader enterprise content automation capability across HR, Marketing, and Sales.

### 3.2 Success Criteria

| Criterion | Measure |
|---|---|
| Content creation speed | Time from topic request to first complete draft asset set |
| Content quality | Reviewer pass rate on first submission (target: [PLACEHOLDER]%) |
| Content coverage | Number of modules published across both domains within 6 months |
| Learner adoption | Percentage of JBS staff who complete at least one module within 3 months of launch |
| Learner satisfaction | Average module feedback rating (target: [PLACEHOLDER] out of 5) |
| Governance compliance | Percentage of published modules with completed review checklist |

---

## 4. Scope

### 4.1 In Scope – Phase 1

- Enterprise Training Content System for JBS internal use.
- Two content domains: Data & AI (technical), Energy & Utilities (domain).
- Five output asset types per topic: research brief, content brief, video script, slide deck outline, infographic specification, and assessment items.
- End-to-end content lifecycle: intake → research → drafting → review → approval → publishing → archiving.
- Role-based content discoverability and learning pathways.
- Content versioning and governance.
- Analytics on content creation and learner engagement.

### 4.2 Out of Scope – Phase 1

- Actual video production (assumed to be performed by a Video Producer using the generated script as input).
- Actual graphic design (assumed to be performed by a Designer using the generated specification as input).
- Learner personalisation based on real-time behavioural data (deferred to a later phase).
- Integration with client-facing training portals (JBS-internal only in Phase 1).
- HR, Marketing, and Sales functions (see Section 14).

---

## 5. Stakeholders & User Roles

| Role | Description | Responsibilities in this system |
|---|---|---|
| **Training Lead / Content Owner** | Owns the training function; commissions and approves content | Submit topic requests; approve or reject generated assets; publish modules |
| **Subject Matter Expert (SME)** | Deep domain knowledge in Data & AI or Energy & Utilities | Review research briefs and content briefs for accuracy; provide corrections |
| **Instructional Designer** | Expertise in learning design and pedagogy | Review asset structure; ensure learning objectives are measurable; ensure content level matches audience |
| **Video Producer** | Creates training videos | Receives the video script and visual asset list; produces the final video externally |
| **Graphic / Deck Designer** | Creates visual assets and slide decks | Receives the slide deck outline and infographic specification; produces final visual assets externally |
| **Learner** | JBS employee consuming training content | Discovers, takes, and rates training modules |
| **Manager** | Team lead or department head | Assigns modules to team members; monitors completion; views team-level progress |
| **Administrator** | System administrator | Manages content taxonomy, user access, knowledge source lists, and system configuration |
| **Executive / Sponsor** | Senior leadership | Receives high-level reporting on content output, learner adoption, and ROI |

---

## 6. Functional Requirements

### FR-1: Topic Intake & Classification

| ID | Requirement |
|---|---|
| FR-1.1 | The system shall provide a structured intake form for submitting a new training topic request. |
| FR-1.2 | The intake form shall capture: topic title, content domain (Data & AI / Energy & Utilities / both), target audience role, target seniority level, required output formats, and any additional context notes. |
| FR-1.3 | The system shall automatically classify the submitted topic into an appropriate learning path and module type based on the provided metadata. |
| FR-1.4 | The system shall allow the submitter to override the auto-classified learning path and module type. |
| FR-1.5 | The intake process shall be triggerable via a web form, and optionally via a messaging platform command. |

### FR-2: Research & Knowledge Compilation

| ID | Requirement |
|---|---|
| FR-2.1 | For each topic request, the system shall compile a structured research brief covering: key concepts and definitions, current methods and approaches, industry applications (specifically Energy & Utilities), 3–5 real-world examples, common challenges and solutions, and future trends. |
| FR-2.2 | The research brief shall include source citations for all material included. |
| FR-2.3 | The system shall draw on JBS internal content (proposals, case studies, slide decks) as a knowledge source. |
| FR-2.4 | The system shall draw on approved external knowledge sources. The list of approved sources shall be curated and maintained by the Administrator. |
| FR-2.5 | The research brief shall be stored against the topic record and available for human review before downstream asset generation proceeds. |
| FR-2.6 | The system shall not incorporate content from sources outside the approved list without human approval. |

### FR-3: Master Content Brief Generation

| ID | Requirement |
|---|---|
| FR-3.1 | The system shall generate a Master Content Brief from the research brief and topic metadata. |
| FR-3.2 | The Master Content Brief shall include: a one-sentence core message, 3–5 measurable learning objectives, target audience description, seniority level, prerequisite knowledge, narrative arc (hook, context, solution, applications, call-to-action), JBS-relevant context, key terms with definitions, and suggested visual opportunities. |
| FR-3.3 | The Master Content Brief shall be stored against the topic record and available for review. |
| FR-3.4 | The Instructional Designer and Training Lead shall be able to edit the Master Content Brief before downstream assets are generated. |

### FR-4: Training Asset Generation

| ID | Requirement |
|---|---|
| FR-4.1 | The system shall generate a **Video Script** from the approved Master Content Brief. The script shall be structured by scenes with timestamps, narration text (in spoken style), on-screen text cues, visual direction notes, and a list of visual assets required. |
| FR-4.2 | The system shall generate a **Slide Deck Outline** from the approved Master Content Brief. The outline shall contain 10–15 slides with a title, key bullet points (maximum 5 per slide), and a description of the required visual for each slide. |
| FR-4.3 | The system shall generate an **Infographic Specification** from the approved Master Content Brief. The specification shall include a title, a hero statistic, 5–7 supporting statistics with context, an optional process flow, an optional comparison table, and layout and icon suggestions. |
| FR-4.4 | The system shall generate **Assessment Items** from the approved Master Content Brief. Each set shall contain 5–10 questions, including multiple-choice and scenario-based items, along with correct answers and rationale. |
| FR-4.5 | All generated assets shall be labelled as version V1 at creation. |
| FR-4.6 | The system shall support regeneration of individual assets without requiring regeneration of all assets for the same topic. |
| FR-4.7 | The system shall support simplified content variants: a "new joiner" version (simplified language) and an "executive summary" version (condensed) of any generated asset, on request. |

### FR-5: Content Review & Approval

| ID | Requirement |
|---|---|
| FR-5.1 | Once assets are generated, the system shall automatically notify the designated Content Owner and Instructional Designer that content is ready for review. |
| FR-5.2 | Reviewers shall be able to view all assets for a topic in a single consolidated location. |
| FR-5.3 | Reviewers shall be able to approve or reject each asset individually, with the ability to add comments. |
| FR-5.4 | Rejected assets shall be returned to a "Revision Required" state, with comments visible to the originator. |
| FR-5.5 | The system shall track the full approval history of each asset (who reviewed, what decision, when). |
| FR-5.6 | All assets for a topic must be individually approved before the topic can be published. |

### FR-6: Publishing & Content Discovery

| ID | Requirement |
|---|---|
| FR-6.1 | Approved modules shall be publishable to a learning portal or LMS where they are accessible to Learners. |
| FR-6.2 | Each published module shall be tagged with: domain, audience role, seniority level, sub-topic, and any prerequisite modules. |
| FR-6.3 | Learners shall be able to search and filter the content catalogue by domain, role, level, and keyword. |
| FR-6.4 | The system shall present role-appropriate learning paths: given a Learner's role and level, the system shall recommend a sequenced set of modules. |
| FR-6.5 | Learners shall be able to take assessments and record completion within the portal. |
| FR-6.6 | Managers shall be able to assign specific modules or learning paths to their team members. |
| FR-6.7 | Managers shall be able to view completion status and assessment scores for their team. |
| FR-6.8 | The system shall support completion certificates for learners who finish a module or learning path. |

### FR-7: Content Versioning & Revision

| ID | Requirement |
|---|---|
| FR-7.1 | Every published module shall carry a version number (e.g., v1.0, v1.1, v2.0). |
| FR-7.2 | When a module is revised, the previous version shall be retained and accessible for audit purposes. |
| FR-7.3 | A revision record shall capture: what changed, why it changed, who made the change, and when. |
| FR-7.4 | The system shall support retirement/archiving of outdated modules, with learners notified if a module they have completed has been superseded. |

---

## 7. Content Domain Requirements

### 7.1 Technical Domain: Data & AI

The system shall support content creation across the following subject areas (non-exhaustive; full curriculum to be defined separately):

| Track | Example Topics |
|---|---|
| Data Foundations | Data literacy, data types, data quality, data governance basics |
| Data Modelling & Analytics | Dimensional modelling, SQL for analytics, analytical thinking |
| Data Engineering | Batch and streaming pipelines, data lakes, lakehouses, ETL/ELT patterns |
| Machine Learning | Supervised/unsupervised learning, model evaluation, feature engineering |
| MLOps & Model Lifecycle | Model deployment, monitoring, retraining, experiment tracking |
| Generative AI | Large language models, retrieval-augmented generation, AI agents, prompt design, evaluation |

### 7.2 Domain Track: Energy & Utilities

The system shall support content creation across the following subject areas (non-exhaustive):

| Track | Example Topics |
|---|---|
| Energy Market Fundamentals | Market structure (generation, transmission, distribution, retail), regulated vs deregulated markets |
| Renewable Energy | Solar, wind, hybrid plants, energy storage basics |
| Forecasting in Energy | Load forecasting, generation forecasting, time-series methods |
| Grid & Smart Grid | Grid topology, SCADA, AMI, EMS/DMS, smart metering, demand response, flexibility markets |
| AI Applications in Utilities | Predictive maintenance, outage prediction, loss reduction, energy theft analytics |

### 7.3 Audience Levels

All topics shall support content calibrated to three depth levels:

| Level | Description |
|---|---|
| **Beginner** | No prior knowledge assumed. Focus on concepts, definitions, and context. |
| **Intermediate** | Foundational knowledge assumed. Focus on methods, patterns, and applications. |
| **Advanced** | Practitioner-level knowledge assumed. Focus on design decisions, trade-offs, and nuanced cases. |

---

## 8. Inputs & Outputs

### 8.1 System Inputs

| Input | Source | Description |
|---|---|---|
| Topic request | Training Lead / SME via intake form | Topic title, domain, audience, level, formats |
| JBS internal content | Internal document repository | Proposals, case studies, past training decks, internal blogs and whitepapers |
| Approved external knowledge sources | Maintained by Administrator | Curated list of trusted publications, research bodies, and industry sources for each domain |
| Reviewer feedback | Content Owner / Instructional Designer / SME | Approval decisions and comments on draft assets |

### 8.2 System Outputs

| Output | Description | Consumed by |
|---|---|---|
| **Research Brief** | Structured summary of the topic with citations; covers definitions, methods, applications, examples, challenges, trends | SME and Instructional Designer for review |
| **Master Content Brief** | Structured content plan: core message, learning objectives, audience, narrative arc, key terms, visual opportunities | Instructional Designer, downstream asset generation |
| **Video Script** | Scene-by-scene script with timestamps, narration, on-screen text, visual cues, and a list of required visual assets | Video Producer |
| **Slide Deck Outline** | 10–15 slide structure with titles, key bullets (max 5 per slide), visual descriptions, and design notes | Graphic/Deck Designer |
| **Infographic Specification** | Title, statistics, process flow, comparison tables, layout and icon guidance | Graphic Designer |
| **Assessment Items** | 5–10 questions (MCQ and scenario-based) with correct answers and rationale | Training Lead, LMS import |
| **Published Module Record** | All assets linked from one topic record; tagged and discoverable in the portal | Learners, Managers |
| **Completion Record** | Learner's completion status, assessment score, and feedback per module | Managers, Training Lead, Executives |
| **Analytics Reports** | Content creation metrics; learner engagement metrics; feedback scores | Training Lead, Executives |

---

## 9. Data & Metadata Requirements

### 9.1 Topic Record

Every training topic shall be represented as a record with the following fields:

| Field | Type | Description |
|---|---|---|
| `topic_id` | Unique identifier | System-generated |
| `title` | Text | Short, descriptive title of the topic |
| `domain` | Enum | Data & AI / Energy & Utilities / Both |
| `sub_domain` | Text | More specific subject area within the domain |
| `audience_role` | Enum / multi-select | Target job role(s) (e.g., Data Engineer, Project Manager) |
| `seniority_level` | Enum | Beginner / Intermediate / Advanced |
| `content_formats` | Multi-select | Video Script / Slide Deck / Infographic / Assessment |
| `learning_path` | Text | Assigned learning path name |
| `module_type` | Enum | Introduction / Concept Explainer / Deep-Dive / Case Study |
| `status` | Enum | Requested / Research Complete / Brief Complete / Assets Generated / In Review / Approved / Published / Archived |
| `version` | Text | e.g., v1.0 |
| `requestor` | User reference | Who submitted the request |
| `reviewer(s)` | User reference(s) | Assigned reviewers |
| `created_at` | Timestamp | |
| `last_modified_at` | Timestamp | |
| `approved_at` | Timestamp | |
| `published_at` | Timestamp | |
| `prerequisite_modules` | Reference list | Other module topic_ids that should be completed first |
| `tags` | Free text / controlled vocabulary | Additional searchable keywords |
| `feedback_rating_avg` | Decimal | Average learner rating (populated post-publication) |
| `completion_count` | Integer | Number of learners who have completed the module |

### 9.2 Asset Record

Each generated asset (Research Brief, Content Brief, Video Script, Slide Deck Outline, Infographic Spec, Assessment Items) shall have:

| Field | Type | Description |
|---|---|---|
| `asset_id` | Unique identifier | System-generated |
| `topic_id` | Reference | Parent topic record |
| `asset_type` | Enum | Research Brief / Content Brief / Video Script / Slide Deck / Infographic / Assessment |
| `version` | Text | e.g., v1.0 |
| `content` | Document / file reference | Location of the asset content |
| `status` | Enum | Draft / In Review / Revision Required / Approved |
| `reviewer` | User reference | Who reviewed this asset |
| `review_comments` | Text | Free text comments from reviewer |
| `reviewed_at` | Timestamp | |
| `created_at` | Timestamp | |

### 9.3 Knowledge Source Registry

The list of approved knowledge sources shall be a maintained registry with:

| Field | Description |
|---|---|
| `source_id` | Unique identifier |
| `name` | Human-readable name |
| `domain` | Applicable domain (Data & AI / Energy & Utilities / General) |
| `description` | What this source provides |
| `status` | Active / Inactive |
| `added_by` | Administrator who approved it |
| `last_reviewed` | Date the source was last validated |

### 9.4 Learner Record

| Field | Description |
|---|---|
| `learner_id` | Unique identifier (linked to organisational identity) |
| `name` | Full name |
| `role` | Job role |
| `seniority_level` | Current level |
| `department` | Department / team |
| `manager_id` | Reference to manager's record |
| `modules_assigned` | List of assigned module topic_ids |
| `modules_completed` | List of completed module topic_ids with completion date |
| `assessment_scores` | Per-module score |
| `feedback_given` | Per-module rating and optional comment |

---

## 10. Content Lifecycle & Workflow Requirements

### 10.1 Content Lifecycle States

```
Requested → Research Complete → Brief Complete → Assets Generated
    → In Review → [Revision Required → Assets Generated (loop)]
    → Approved → Published → Archived
```

### 10.2 State Transition Rules

| From | To | Triggered by | Condition |
|---|---|---|---|
| — | Requested | Training Lead submits intake form | Valid intake form submitted |
| Requested | Research Complete | System | Research brief successfully generated |
| Research Complete | Brief Complete | System | Master Content Brief successfully generated |
| Brief Complete | Assets Generated | System | All requested asset types generated |
| Assets Generated | In Review | System | Automatic; reviewers notified |
| In Review | Revision Required | Reviewer | Any asset rejected with comment |
| In Review | Approved | Reviewer | All assets individually approved |
| Revision Required | Assets Generated | System | Revised assets regenerated |
| Approved | Published | Training Lead | Manual publish action |
| Published | Archived | Administrator / Training Lead | Module retired |

### 10.3 Notification Requirements

| Event | Who is notified |
|---|---|
| New topic request submitted | Training Lead (confirmation) |
| Assets ready for review | Assigned reviewers (Content Owner, Instructional Designer) |
| Asset rejected | Topic requestor |
| All assets approved | Training Lead |
| Module published | All eligible learners (based on role/level tags) |
| Assigned module | Learner (when Manager assigns a module) |
| Module updated / superseded | Learners who have completed the previous version |

---

## 11. Governance & Compliance Requirements

### 11.1 Content Accuracy

| ID | Requirement |
|---|---|
| GR-1 | Every module must pass a reviewer quality checklist before it can be marked as Approved. |
| GR-2 | The quality checklist shall include, at minimum: (a) Is the domain content technically accurate? (b) Is the difficulty level appropriate for the stated audience? (c) Are there any client-identifiable or confidential details that must not appear? (d) Are all statistics either cited or clearly labelled as illustrative examples? |

### 11.2 Confidentiality & Data Privacy

| ID | Requirement |
|---|---|
| GR-3 | No real client names, project names, or client-identifiable data shall appear in any published training asset. |
| GR-4 | All case study examples in training content must be genericised or anonymised. |
| GR-5 | [PLACEHOLDER – Data privacy obligations applicable to employee personal data held in learner records (e.g., GDPR, applicable local law) to be confirmed with legal/compliance.] |

### 11.3 Knowledge Source Control

| ID | Requirement |
|---|---|
| GR-6 | Only sources on the approved Knowledge Source Registry may be used to ground generated content. |
| GR-7 | The Administrator shall review and update the Knowledge Source Registry at a minimum of [PLACEHOLDER – frequency, e.g., quarterly]. |
| GR-8 | Any request to add a new source to the registry shall be subject to Administrator approval. |

### 11.4 Audit Trail

| ID | Requirement |
|---|---|
| GR-9 | All content generation events shall be logged with: who triggered the action, what was generated, and the timestamp. |
| GR-10 | All review and approval decisions shall be logged. |
| GR-11 | All publish and archive events shall be logged. |
| GR-12 | Audit logs shall be retained for a minimum of [PLACEHOLDER – period, e.g., 2 years]. |

---

## 12. Non-Functional Requirements

| ID | Category | Requirement |
|---|---|---|
| NFR-1 | Scalability | The system shall support concurrent processing of multiple topic requests without degradation of output quality. |
| NFR-2 | Consistency | All generated assets shall follow standard templates and structures defined in the system's content templates. Content structure must not vary between topics. |
| NFR-3 | Portability | The system architecture must not create hard dependencies on any single vendor's proprietary formats. Content must be exportable in standard formats (text, markdown, PDF, CSV). |
| NFR-4 | Extensibility | The system must be designed to add new content domains, new output asset types, and new enterprise functions (HR, Marketing, Sales) without fundamentally redesigning the core platform. |
| NFR-5 | Turnaround | A full set of draft assets for a new topic shall be available for review within [PLACEHOLDER – e.g., 30 minutes] of an intake submission. |
| NFR-6 | Availability | The system shall be available during JBS business hours with a minimum uptime of [PLACEHOLDER – e.g., 99%]. |
| NFR-7 | Usability | Non-technical users (Training Lead, SME, Instructional Designer) shall be able to use the intake form and review interface without developer assistance. |
| NFR-8 | Maintainability | Content templates must be updatable by an Administrator without requiring code changes or developer involvement. |
| NFR-9 | Cost | [PLACEHOLDER – Budget envelope for infrastructure and tooling to be defined.] |

---

## 13. Reporting & Analytics Requirements

### 13.1 Content Creation Metrics

| Metric | Description |
|---|---|
| Topics requested (period) | Number of new topic requests per week/month |
| Time to first draft | Elapsed time from topic request submission to completion of first asset generation |
| Review cycle time | Elapsed time from assets generated to all assets approved |
| First-pass approval rate | Percentage of topics where all assets are approved without revision |
| Modules published (period) | Number of modules reaching Published status per period |
| Modules per domain | Count of published modules by domain and sub-domain |

### 13.2 Learner Engagement Metrics

| Metric | Description |
|---|---|
| Module views | Number of times each module has been accessed |
| Module completion rate | Percentage of learners who started a module and completed it |
| Assessment pass rate | Percentage of learners who passed the assessment on first attempt |
| Average feedback rating | Average learner rating per module and across the full catalogue |
| Learning path completion | Percentage of assigned learning paths completed by target learners |

### 13.3 Reporting Audiences

| Audience | Report Type |
|---|---|
| Training Lead | Content creation pipeline status; module quality and engagement summary |
| Manager | Team completion dashboard; individual learner progress |
| Executive / Sponsor | High-level summary: content produced, learner adoption, training ROI (indicative) |
| Administrator | System usage logs; governance compliance rate; knowledge source health |

---

## 14. Enterprise Scope – Future Phases

The enterprise vision is for the training content system to be the first pillar of a broader **enterprise-wide content and workflow automation framework**. The same core approach — intake request → research/context gathering → draft output → review → approve → publish — shall underpin multiple business functions. Requirements for these functions are **out of scope for Phase 1** but must be considered in the architecture so that Phase 1 does not create barriers to extension.

### 14.1 HR Administration Agent (Future Phase)

| Function | High-Level Business Need |
|---|---|
| Employee onboarding | Generate role-specific onboarding packs, checklists, and documentation |
| Policy Q&A | Allow employees to ask HR policy questions and receive accurate, cited responses |
| Document generation | Auto-draft standard HR documents (offer letters, confirmation letters, etc.) |
| Ticket triage | Route HR queries to the correct person or process |

### 14.2 Marketing Content Agent (Future Phase)

| Function | High-Level Business Need |
|---|---|
| Campaign content | Generate campaign briefs, blog posts, and social content for JBS marketing |
| Persona-based content | Tailor content to defined buyer or audience personas |
| Training content repurposing | Adapt internal training material into external-facing thought leadership content |

### 14.3 Sales Outreach Agent (Future Phase)

| Function | High-Level Business Need |
|---|---|
| Lead research | Compile background research on target accounts and contacts |
| Outreach sequences | Generate multi-step, personalised outreach messages |
| CRM documentation | Auto-draft follow-up summaries and log activities in the CRM |

### 14.4 Shared Enterprise Requirements

Regardless of the function, the enterprise framework shall share:

- A common intake and workflow pattern.
- A single knowledge and content repository with function-appropriate access scoping.
- Unified role-based access control across all agents.
- A single governance and audit trail framework.
- Shared analytics and reporting infrastructure.

---

## 15. Constraints & Assumptions

### 15.1 Constraints

| ID | Constraint |
|---|---|
| C-1 | JBS does not want to manually author new content prompts for every new training topic. The system must be template-driven. |
| C-2 | Training content must not include real client names, project-specific financial data, or any information that would identify a JBS client. |
| C-3 | The system must support both Data & AI topics and Energy & Utilities topics with the same structural framework. |
| C-4 | [PLACEHOLDER – Any regulatory or legal constraints applicable to JBS's industry.] |
| C-5 | [PLACEHOLDER – Budget constraints.] |

### 15.2 Assumptions

| ID | Assumption |
|---|---|
| A-1 | JBS has an existing repository of internal documents (proposals, decks, case studies) that can serve as a knowledge base for grounding content. |
| A-2 | Actual video production and graphical design will remain human-in-the-loop activities using the system's generated scripts and specifications as inputs. |
| A-3 | The Training Lead will own and manage the approval workflow. |
| A-4 | JBS will designate an Administrator responsible for maintaining the Knowledge Source Registry and system configuration. |
| A-5 | The learning portal / LMS to be used for learner access will be determined during the technology selection phase. |
| A-6 | All JBS employees targeted by training have internet access and can access a web-based portal. |

---

## 16. Open Questions & Decisions Required

| # | Question | Owner | Target Date |
|---|---|---|---|
| OQ-1 | Which LMS or learning portal will be used? Criteria should include SCORM support, SSO integration, completion tracking, and cost. | Training Lead / IT | [PLACEHOLDER] |
| OQ-2 | What is the full list of audience roles for whom learning paths need to be defined? | Training Lead / HR | [PLACEHOLDER] |
| OQ-3 | What are the JBS competency frameworks (if any) to which learning objectives should be mapped? | HR / Training Lead | [PLACEHOLDER] |
| OQ-4 | What storage platform will be used as the document repository? (internal SharePoint, Google Drive, etc.) | IT | [PLACEHOLDER] |
| OQ-5 | What is the policy for handling training content sourced from external bodies? Is there a copyright / attribution requirement? | Legal / Compliance | [PLACEHOLDER] |
| OQ-6 | What are the data retention and privacy requirements for learner records under applicable law? | Legal / Compliance | [PLACEHOLDER] |
| OQ-7 | What integration exists or is required with the HR system to keep learner roles and seniority levels current? | HR / IT | [PLACEHOLDER] |
| OQ-8 | What is the target turnaround time SLA for draft asset generation? | Training Lead / Sponsor | [PLACEHOLDER] |
| OQ-9 | Should training content be accessible to JBS clients, or is it strictly internal in Phase 1? | Executive / Training Lead | [PLACEHOLDER] |
| OQ-10 | Who has authority to retire / archive a module? Training Lead only, or also Administrators? | Training Lead | [PLACEHOLDER] |

---

## 17. Glossary

| Term | Definition |
|---|---|
| **Asset** | A discrete output document generated for a training topic (e.g., Video Script, Slide Deck Outline). |
| **Assessment Item** | A test question (multiple-choice or scenario-based) used to evaluate learner understanding. |
| **Content Brief / Master Content Brief** | A structured planning document that defines the core message, learning objectives, narrative arc, and key elements of a training module, used as the basis for generating all other assets. |
| **Content Domain** | A broad knowledge area: either "Data & AI" (technical) or "Energy & Utilities" (industry domain). |
| **Infographic Specification** | A structured blueprint describing the content, statistics, layout, and icon suggestions for a visual infographic asset. |
| **JBS** | Jade Business Services – the organisation commissioning this system. |
| **Knowledge Source Registry** | The curated list of internal and external sources approved for use in generating training content. |
| **Learning Path** | An ordered sequence of modules recommended for a specific audience role and level. |
| **LMS** | Learning Management System – the platform on which published training modules are hosted and consumed by Learners. |
| **Module** | A complete, publishable unit of training content on a single topic, comprising all approved assets and associated metadata. |
| **Research Brief** | A structured summary of a topic compiled from approved knowledge sources, including key concepts, methods, applications, examples, challenges, and trends with citations. |
| **Slide Deck Outline** | A structured document describing the content, structure, and visual requirements for a presentation. |
| **SME** | Subject Matter Expert – a person with deep knowledge in a relevant domain who reviews content for accuracy. |
| **Topic Record** | The master data record representing a training topic throughout its lifecycle from request to archive. |
| **Video Script** | A scene-by-scene script for a training video, including narration, on-screen text, timestamps, and visual direction notes. |
