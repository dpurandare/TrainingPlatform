<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>

# I want to build a corporate training agent for, uh, Jade Business Services. Where, uh, everything needs to be prompt-oriented. I need to build training videos, technical training videos, as well as domain training videos. Uh, so technical training videos will be for all data and AI concepts. And, uh, so and for domain training videos it has to be all for energy and utility concepts. I really do not want to spend time in actually adding more just prompts. Help me how do I go about, uh, doing it.

You can treat this as a “training factory” powered by one master prompt system, instead of manually writing new prompts for every course or video.[^1_1][^1_2]

Below is a concrete way to do it for JBS.

***

## 1. Decide the core architecture

Think in terms of three layers, all prompt-driven:[^1_3][^1_1]

- **Instruction layer (system prompts):**
One master “JBS Training Agent” spec that defines tone, audience (JBS roles), formats (video script, quiz, case study), and guardrails (no hallucinated client names, etc.).[^1_4][^1_1]
- **Content layer (retrieval):**
Plug in:
    - JBS internal docs, proposals, solution decks.
    - Public energy \& utilities references you trust (NERC, FERC, ISO/RTO docs, OEM docs etc.).
    - Standard data/AI concepts (your existing decks, blogs, notebooks).
Use retrieval so the agent *pulls* content instead of you re‑prompting it each time.[^1_5][^1_6]
- **Experience layer (LMS/portal):**
Where employees:
    - Select learning path (role + level).
    - Watch AI-generated videos.
    - Take quizzes, get completion tracking and certificates.[^1_7][^1_8][^1_9]

This lets you change behavior by editing one or two root prompts + a few templates, not hundreds of ad-hoc prompts.[^1_1][^1_4]

***

## 2. Define reusable prompt templates (not ad-hoc prompts)

Create 5–7 reusable “prompt patterns” that your agent uses under the hood.[^1_1][^1_5] For example:

1. **Curriculum designer prompt**
Input: role, level, topic (e.g., “Data engineer, intermediate, ‘Time-series forecasting for wind/solar’”).
Output: modular outline (modules, lessons, duration, outcomes, pre-reqs).[^1_10][^1_8]
2. **Lesson blueprint prompt**
Input: lesson name + outline.
Output:
    - Key concepts (bullets)
    - 1–2 JBS-context examples (using genericized client stories)
    - 3–5 quiz questions
    - 1 hands-on task.[^1_10][^1_11][^1_6]
3. **Video script prompt**
Input: lesson blueprint.
Output:
    - Narration script (short sentences, spoken style)
    - On-screen text cues
    - Visual suggestions (simple diagrams, charts).[^1_5][^1_4]
4. **Assessment prompt**
Input: module outline + Bloom level (remember, apply, evaluate).
Output: mix of MCQs, scenario questions, small case studies.[^1_7][^1_5]
5. **Localization/simplification prompt**
Take a technical script and rewrite into:
    - “New joiner” version
    - “Leadership summary” version.[^1_7][^1_6]

These templates live once in your “training agent” and are reused programmatically; you don’t hand‑craft new prompts every time.[^1_1][^1_4]

***

## 3. Use AI video tools to produce videos at scale

You don’t need to record everything yourself—use an AI video platform that supports training/eLearning.[^1_12][^1_13][^1_9]

For JBS use-case:

- **Platforms to shortlist**
    - Synthesia – very enterprise-friendly, strong LMS integrations, many training templates.[^1_12][^1_9]
    - Colossyan – strong on interactive training (branching, quizzes) and SCORM export.[^1_9]
    - HeyGen – good avatars and languages, better if you care about marketing-style videos too.[^1_13][^1_9]
- **Minimal workflow**

1. JBS Training Agent outputs a video script + screen text.
2. You paste into Synthesia/Colossyan/HeyGen template.
3. Choose avatar, brand colors, logo, export.
4. Upload to LMS or SharePoint/Zoho-integrated portal.[^1_12][^1_9]

This turns “write script + shoot + edit” into “approve script + click generate”, which is where you save time.[^1_5][^1_6][^1_13]

***

## 4. Design the technical curriculum (Data \& AI)

Have the agent generate and maintain a standard technical track library.[^1_8][^1_10]

Example structure (each becomes a module with 2–3 lessons):

- Data foundations for JBS
- SQL + data modeling for analytics
- ETL/ELT and lakehouse concepts (Databricks, Synapse, BigQuery)
- Machine learning fundamentals
- MLOps basics
- GenAI for JBS (RAG, agents, evaluation, prompt patterns).[^1_4][^1_1][^1_14]

For each module, you run:

1. “Curriculum designer prompt” → outline.
2. “Lesson blueprint prompt” → lesson breakdown.
3. “Video script prompt” → script.

You review/trim only once per module; the template remains the same across everything.[^1_4][^1_5]

***

## 5. Design the energy \& utilities domain curriculum

Anchor this tightly to your JBS positioning (renewables, utilities, grid, forecasting).[^1_15][^1_10][^1_11]

Sample domain tracks:

- **Energy basics**
    - Market structure (gen, transmission, distribution, retailers).
    - Regulated vs deregulated markets (US, India examples but anonymized).[^1_10][^1_11]
- **Renewable energy \& forecasting**
    - Solar, wind, hybrid plants.
    - Time-series forecasting for load and generation.[^1_10][^1_11]
- **Grid \& smart grid**
    - SCADA, AMI, EMS/DMS basics.
    - Smart metering, demand response, flexibility.[^1_10][^1_11]
- **AI in utilities**
    - Predictive maintenance.
    - Outage prediction.
    - Loss reduction, theft analytics (generic).[^1_8][^1_11]

Use the same three-step pipeline (outline → blueprint → script). For domain accuracy, the agent should always pull from a vetted energy/utility knowledge base when answering.[^1_10][^1_8][^1_11]

***

## 6. Make it adaptive and role-based

Use your LMS/CRM data to let the agent personalize paths.[^1_7][^1_14][^1_5]

- Role-based entry prompts:
    - “New data engineer on utilities projects.”
    - “Project manager moving from generic analytics to energy.”
- Agent outputs:
    - Recommended modules and order.
    - Estimated hours.
    - Pre-assessment quiz to skip basics if they pass.[^1_7][^1_5]

This reduces “prompting overhead” for you; the employee just selects role and the agent picks the right template and content.[^1_14][^1_7]

***

## 7. Governance: don’t let it drift

To avoid chaos:

- **Content source control:**
Only specific folders/SharePoint libraries and documents are used for retrieval.[^1_5][^1_6]
- **Versioning:**
Each module has a version (v1, v1.1 etc.). Agent can only update content via a “revision prompt” that logs what changed and why.[^1_4][^1_5]
- **Quality checks:**
Simple checklist for reviewers:
    - Is the domain technically correct?
    - Any client-identifiable detail?
    - Level appropriate for audience?[^1_5][^1_6]

***

## 8. A simple starting blueprint for you

If you want a minimal “Phase 1” that you and one ops person can execute in 2–4 weeks:

1. Pick 2 tracks:
    - “Data \& AI Foundations for Energy \& Utilities.”
    - “Energy \& Utility Domain 101 for JBS New Joiners.”[^1_10][^1_11]
2. Define the 5–7 reusable prompts (I can draft them if you like).
3. Feed in your existing slide decks, proposals, blogs as the initial corpus.
4. Choose one AI video tool (likely Synthesia or Colossyan).
5. Build 3 modules end-to-end (outline → script → video → quiz).
6. Release as “JBS Training Agent – Beta Academy” and gather feedback.

If you tell me:

- Which LLM stack you prefer (OpenAI/Azure/Open-source), and
- Which LMS/portal you want to use (Zoho Learn, custom, or others),

I can next write the concrete master system prompt for the JBS Training Agent plus the exact 5–7 reusable prompt templates you or your team can drop straight into your setup.
<span style="display:none">[^1_16][^1_17][^1_18][^1_19]</span>

<div align="center">⁂</div>

[^1_1]: https://www.emergentmind.com/topics/prompt-based-llm-generation

[^1_2]: https://www.perplexity.ai/search/8423236f-c1c6-4497-997a-371f489f6b05

[^1_3]: https://ieeexplore.ieee.org/document/11257597/

[^1_4]: https://www.leewayhertz.com/ai-agent-for-content-generation/

[^1_5]: https://digiqt.com/blog/ai-agents-in-corporate-training-for-workforce-training/

[^1_6]: https://www.akira.ai/ai-agents/content-creation-ai-agents

[^1_7]: https://elearningindustry.com/do-more-with-less-how-ai-agents-are-revolutionizing-corporate-training

[^1_8]: https://copextraining.com/courses/ai-application-for-utility

[^1_9]: https://www.voomo.ai/blog/heygen-vs-synthesia-comparison-ai-video-generators/

[^1_10]: https://upskilldevelopment.com/energy-data-analytics-and-digital-transformation-in-power-systems-training-course

[^1_11]: https://stratinstitute.com/training/ai-for-energy-utilities/

[^1_12]: https://www.synthesia.io/alternatives/synthesia-vs-colossyan

[^1_13]: https://willscott.me/2025/12/18/ai-video-platforms-for-business-a-comprehensive-2025-comparison/

[^1_14]: https://www.mindstudio.ai/blog/launch-ai-agent-training-program-team

[^1_15]: work.company_focus

[^1_16]: https://www.perplexity.ai/search/9895b19c-3c19-4f5c-a14d-ee6c0be1ba2d

[^1_17]: work.task_focus

[^1_18]: https://kodexolabs.com/ai-agents-content-generation-guide/

[^1_19]: https://www.reddit.com/r/aiagents/comments/1n7aq90/i_built_an_ai_agent_to_automate_my_mandatory/


---

# I have Veed.io and HeyGen for video creation, Pyxa.ai, Gemini Pro, Claude Pro, OpenAI Pro, Perplexity Pro for research and content, Gamma App, Notebooklm for ppt and infographics. I want to create a core system where I put the prompt for the topic, it does the deep research and creates a  script for the script for making videos, beautiful graphics, ppts and infographia. I need the following topics to be used to build. I need the best 5 to 7 reliable sites as inputs and prompts for building such a system. my preferred automation is n8n. if I can generate everything from claude Pro, gemini Pro, notebooklm, I would prefer that

Perfect! You already have a premium stack. Let me design a **single n8n automation workflow** that takes one topic prompt, researches it deeply, and outputs everything you need—script, video assets, PPT, and infographics—all orchestrated through Claude Pro, Gemini Pro, and NotebookLM.

***

## **Core n8n Workflow Architecture**

```
[Manual Trigger: Topic Input]
    ↓
[Perplexity API: Deep Research]
    ↓
[Claude Pro API: Generate Master Content Brief]
    ↓
    ├─→ [Gemini Pro API: Video Script + Visuals Plan]
    ├─→ [Claude Pro API: PPT Outline + Slide Content]
    └─→ [Gemini Pro API: Infographic Data Points]
    ↓
[Format & Store Outputs in Google Drive/SharePoint]
    ↓
[Trigger Notifications: Slack/Email with links]
```

You input **one topic**, the workflow does the rest, and outputs:

- Research brief (PDF)
- Video script with scene breakdowns
- PPT content (ready for Gamma)
- Infographic data (ready for Pyxa.ai or manual design)
- Visual asset suggestions

***

## **5–7 Reliable Input Sources (for Research Layer)**

These will be your **content knowledge base** that Perplexity/Claude/Gemini query:

### **Technical/Data \& AI Concepts:**

1. **Papers with Code** ([https://paperswithcode.com](https://paperswithcode.com))
    - State-of-the-art ML/AI methods, benchmarks, reproducible research
2. **Google AI Research** ([https://research.google/pubs/](https://research.google/pubs/))
    - Foundational papers on transformers, GenAI, multimodal models
3. **Databricks Blog** ([https://www.databricks.com/blog](https://www.databricks.com/blog))
    - Lakehouse architecture, MLOps, enterprise AI patterns

### **Energy \& Utilities Domain:**

4. **NREL (National Renewable Energy Laboratory)** ([https://www.nrel.gov/research/publications.html](https://www.nrel.gov/research/publications.html))
    - Solar, wind, grid integration, forecasting research
5. **IEEE Xplore – Power \& Energy Society** ([https://ieeexplore.ieee.org/Xplore/home.jsp](https://ieeexplore.ieee.org/Xplore/home.jsp))
    - Peer-reviewed papers on smart grids, SCADA, AI in utilities
6. **IEA (International Energy Agency)** ([https://www.iea.org/reports](https://www.iea.org/reports))
    - Global energy trends, policy, renewables, data-driven insights
7. **Utility Dive** ([https://www.utilitydive.com](https://www.utilitydive.com))
    - Industry news, use cases, utility transformation trends

**Bonus:** Your own **JBS content library** (SharePoint/Drive folder with proposals, decks, case studies) should be the 8th "site"—Perplexity or Claude can retrieve from it if you set up RAG or upload context.

***

## **Detailed n8n Workflow Design**

### **Node 1: Manual Trigger (Webhook or Form)**

- **Input fields:**
    - `topic` (e.g., "Time-series forecasting for wind energy")
    - `audience` (e.g., "Data engineers at JBS")
    - `video_length` (e.g., "8–10 minutes")
    - `content_type` (checkboxes: Video, PPT, Infographic)

***

### **Node 2: Perplexity API – Deep Research**

**Purpose:** Get a comprehensive, cited research summary.

**n8n HTTP Request Node:**

- **Method:** POST
- **URL:** `https://api.perplexity.ai/chat/completions`
- **Headers:**

```
Authorization: Bearer YOUR_PERPLEXITY_API_KEY
Content-Type: application/json
```

- **Body (JSON):**

```json
{
  "model": "sonar-pro",
  "messages": [
    {
      "role": "system",
      "content": "You are a research assistant for Jade Business Services, a Data & AI firm specializing in Energy & Utilities. Provide detailed, cited research summaries using trusted sources."
    },
    {
      "role": "user",
      "content": "Research topic: {{$json.topic}}. Provide:\n1. Key concepts and definitions\n2. Current state-of-the-art methods\n3. Industry applications in energy/utilities\n4. 3–5 real-world examples\n5. Common challenges and solutions\n6. Future trends\n\nCite all sources."
    }
  ],
  "max_tokens": 4000,
  "temperature": 0.2
}
```


**Output:** Store `research_brief` (text with citations).

***

### **Node 3: Claude Pro API – Generate Master Content Brief**

**Purpose:** Synthesize Perplexity research into a structured brief for downstream generation.

**n8n HTTP Request Node:**

- **Method:** POST
- **URL:** `https://api.anthropic.com/v1/messages`
- **Headers:**

```
x-api-key: YOUR_CLAUDE_API_KEY
anthropic-version: 2023-06-01
Content-Type: application/json
```

- **Body (JSON):**

```json
{
  "model": "claude-3-7-sonnet-20250219",
  "max_tokens": 8000,
  "temperature": 0.3,
  "system": "You are a content strategist for Jade Business Services. Transform research into actionable content briefs for training videos, presentations, and infographics targeting data/AI professionals in energy & utilities.",
  "messages": [
    {
      "role": "user",
      "content": "Topic: {{$json.topic}}\nAudience: {{$json.audience}}\n\nResearch:\n{{$node["Perplexity Research"].json["choices"]["message"]["content"]}}\n\nGenerate a Master Content Brief with:\n\n## Core Message\n- One-sentence takeaway\n- 3 key learning objectives\n\n## Narrative Arc\n- Hook (problem/question)\n- Context (background)\n- Solution/Method\n- Application/Impact\n- Call-to-action\n\n## Technical Depth\n- Complexity level (beginner/intermediate/advanced)\n- Required prerequisites\n- Jargon to explain\n\n## JBS Context\n- How this relates to JBS services (Azure, GCP, Databricks, GenAI)\n- Client relevance (utilities, renewables)\n\n## Visual Opportunities\n- 5 key diagrams/charts needed\n- Data visualization suggestions"
    }
  ]
}
```


**Output:** Store `content_brief`.

***

### **Node 4A: Gemini Pro API – Video Script + Scene Plan**

**Purpose:** Generate detailed video script with narration, on-screen text, and visual cues.

**n8n HTTP Request Node:**

- **Method:** POST
- **URL:** `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash-exp:generateContent`
- **Headers:**

```
Content-Type: application/json
```

- **Query Parameters:**

```
key: YOUR_GEMINI_API_KEY
```

- **Body (JSON):**

```json
{
  "contents": [{
    "parts":[{
      "text": "You are a video scriptwriter for technical training content at Jade Business Services.\n\nContent Brief:\n{{$node["Claude Content Brief"].json["content"]["text"]}}\n\nTarget Length: {{$json.video_length}} minutes\n\nGenerate a complete video script in this format:\n\n## VIDEO SCRIPT: [Title]\n\n### Scene 1: Hook (0:00–0:30)\n**Narration:**\n[Spoken text, short sentences, conversational tone]\n\n**On-Screen Text:**\n[Key phrases to display]\n\n**Visuals:**\n[Description for video editor: charts, diagrams, b-roll suggestions]\n\n---\n\n### Scene 2: Context (0:30–2:00)\n...\n\n[Continue for 5–8 scenes covering the narrative arc]\n\n### Closing Scene: Call-to-Action\n**Narration:**\n[Wrap-up, next steps]\n\n**End Card:**\n- JBS logo\n- Contact: jade-biz.com\n- Next module link\n\n---\n\n## VISUAL ASSETS NEEDED:\n1. [List specific charts/diagrams to create]\n2. [Stock footage keywords]\n3. [Icon/graphic needs]\n\nMake it engaging, technically accurate, and brand-aligned for JBS."
    }]
  }],
  "generationConfig": {
    "temperature": 0.4,
    "maxOutputTokens": 8000
  }
}
```


**Output:** Store `video_script`.

***

### **Node 4B: Claude Pro API – PPT Outline + Slide Content**

**Purpose:** Generate complete slide deck content ready for Gamma App.

**n8n HTTP Request Node:**

- **Method:** POST
- **URL:** `https://api.anthropic.com/v1/messages`
- **Body (JSON):**

```json
{
  "model": "claude-3-7-sonnet-20250219",
  "max_tokens": 6000,
  "temperature": 0.3,
  "system": "You are a presentation designer for Jade Business Services. Create slide decks for technical training that are visually clean, data-driven, and brand-professional.",
  "messages": [
    {
      "role": "user",
      "content": "Content Brief:\n{{$node["Claude Content Brief"].json["content"]["text"]}}\n\nGenerate a complete slide deck outline in markdown format ready for Gamma App:\n\n# [Title Slide]\n**Title:** [Compelling title]\n**Subtitle:** [Context]\n**Presenter:** Jade Business Services – Data & AI for Energy & Utilities\n\n---\n\n# Slide 2: Agenda\n- [3–5 bullet points]\n\n---\n\n# Slide 3: [Section Title]\n## Key Point 1\n- [Supporting bullet]\n- [Supporting bullet]\n\n**Visual:** [Chart/diagram description]\n\n---\n\n[Continue for 8–12 slides]\n\n---\n\n# Final Slide: Key Takeaways\n1. [Takeaway 1]\n2. [Takeaway 2]\n3. [Takeaway 3]\n\n**Contact:** jade-biz.com\n\n---\n\n## DESIGN NOTES:\n- Use JBS brand colors (teal accent, dark/light neutrals)\n- Minimal text per slide (max 5 bullets)\n- One visual per slide where possible\n- Professional, modern layout"
    }
  ]
}
```


**Output:** Store `ppt_content` (markdown).

***

### **Node 4C: Gemini Pro API – Infographic Data Points**

**Purpose:** Extract key stats, comparisons, and visual data for infographic design.

**n8n HTTP Request Node:**

- **Body (JSON):**

```json
{
  "contents": [{
    "parts":[{
      "text": "Content Brief:\n{{$node["Claude Content Brief"].json["content"]["text"]}}\n\nExtract infographic-ready content:\n\n## Title\n[Catchy, short title]\n\n## Key Statistics (5–7)\n1. [Stat with context]: \"X% of utilities use AI for outage prediction\"\n2. ...\n\n## Process Flow / Timeline\n[If applicable: 3–5 step process]\n\n## Comparison Table\n| Method A | Method B | Method C |\n|----------|----------|----------|\n| [Feature]| [Feature]| [Feature]|\n\n## Visual Hierarchy\n- Hero stat: [Most important number]\n- Supporting stats: [3–4 secondary]\n\n## Design Suggestions\n- Layout: [Vertical/horizontal/circular]\n- Color coding: [Category-based colors]\n- Icons needed: [List 5–8 icons]\n\nFormat for Pyxa.ai or Canva input."
    }]
  }],
  "generationConfig": {
    "temperature": 0.3,
    "maxOutputTokens": 4000
  }
}
```


**Output:** Store `infographic_data`.

***

### **Node 5: Google Drive – Save All Outputs**

**n8n Google Drive Node (4 instances):**

1. **Research Brief (PDF):**
    - Folder: `JBS Training Content/Research Briefs`
    - File name: `{{$json.topic}}_research_{{$now}}.txt`
    - Content: `{{$node["Perplexity Research"].json}}`
2. **Video Script (Markdown):**
    - Folder: `JBS Training Content/Video Scripts`
    - File name: `{{$json.topic}}_script_{{$now}}.md`
    - Content: `{{$node["Gemini Video Script"].json}}`
3. **PPT Content (Markdown):**
    - Folder: `JBS Training Content/Presentations`
    - File name: `{{$json.topic}}_slides_{{$now}}.md`
    - Content: `{{$node["Claude PPT"].json}}`
4. **Infographic Data (JSON/Markdown):**
    - Folder: `JBS Training Content/Infographics`
    - File name: `{{$json.topic}}_infographic_{{$now}}.md`
    - Content: `{{$node["Gemini Infographic"].json}}`

***

### **Node 6: NotebookLM Integration (Optional Enhancement)**

**Manual step after automation:**

1. Upload the **Research Brief** PDF to NotebookLM.
2. Use NotebookLM's "Audio Overview" feature to generate a podcast-style discussion of the topic.
3. Download the audio and use as voice-over base or supplementary content.

**Future n8n automation:** NotebookLM doesn't have a public API yet, but you can use **Pyxa.ai API** (if available) or **Gamma App API** to auto-generate PPTs from the markdown.

***

### **Node 7: Slack/Email Notification**

**n8n Slack/Email Node:**

- **Message:**

```
✅ Training content generated for: {{$json.topic}}

📄 Research Brief: [Drive Link]
🎬 Video Script: [Drive Link]
📊 PPT Content: [Drive Link]
📈 Infographic Data: [Drive Link]

Next steps:
1. Review content in Drive
2. Import PPT markdown to Gamma App
3. Use video script in HeyGen/Veed.io
4. Design infographic in Pyxa.ai
```


***

## **Reusable Master Prompt Templates (for Manual Override)**

If you want to bypass n8n and run manually in Claude/Gemini/Perplexity, here are the **5 core prompts** you can reuse:

### **1. Deep Research Prompt (Perplexity Pro)**

```
Research topic: [TOPIC]

Provide a comprehensive research summary covering:
1. Key concepts and definitions
2. Current state-of-the-art methods
3. Industry applications in energy & utilities
4. 3–5 real-world examples with data
5. Common challenges and solutions
6. Future trends (2026–2030)

Use sources from:
- NREL, IEEE, IEA for energy/utilities
- Papers with Code, Google AI Research for AI/ML
- Databricks, vendor blogs for enterprise patterns

Cite all sources. Format for training content creation.
```


***

### **2. Master Content Brief Prompt (Claude Pro)**

```
You are a content strategist for Jade Business Services, a Data & AI firm specializing in Energy & Utilities.

Topic: [TOPIC]
Audience: [AUDIENCE]
Research: [PASTE PERPLEXITY OUTPUT]

Generate a Master Content Brief with:

## Core Message
- One-sentence takeaway
- 3 key learning objectives

## Narrative Arc
- Hook (problem/question)
- Context (background)
- Solution/Method
- Application/Impact in energy/utilities
- Call-to-action

## Technical Depth
- Complexity level
- Prerequisites
- Jargon to explain

## JBS Context
- Relation to JBS services (Azure, GCP, Databricks, GenAI)
- Client relevance (utilities, renewables, grid)

## Visual Opportunities
- 5 key diagrams/charts needed
- Data visualization types

Be specific and actionable.
```


***

### **3. Video Script Prompt (Gemini Pro)**

```
You are a video scriptwriter for technical training at Jade Business Services.

Content Brief: [PASTE CLAUDE OUTPUT]
Target Length: [X] minutes

Generate a complete video script:

Format:
### Scene [N]: [Title] (timestamp)
**Narration:** [Spoken text, short sentences, conversational]
**On-Screen Text:** [Key phrases]
**Visuals:** [Chart/diagram/b-roll description]

Structure:
- Scene 1: Hook (0:00–0:30)
- Scene 2–3: Context (0:30–2:00)
- Scene 4–6: Core Content (2:00–7:00)
- Scene 7: Application/Impact (7:00–8:30)
- Scene 8: Closing + CTA (8:30–9:00)

Include:
- Engaging narration (spoken style, not written)
- Clear visual cues for video editor
- JBS branding moments
- End card with jade-biz.com

List all visual assets needed at the end.
```


***

### **4. PPT Content Prompt (Claude Pro)**

```
You are a presentation designer for Jade Business Services.

Content Brief: [PASTE BRIEF]

Generate a complete slide deck in markdown (ready for Gamma App):

Format:
# [Slide Title]
- [Bullet point]
- [Bullet point]

**Visual:** [Chart/diagram description]

---

Requirements:
- 10–15 slides total
- Title slide with JBS branding
- Agenda slide
- 1 concept per slide
- Max 5 bullets per slide
- Visual suggestion for each slide
- Final slide: Key Takeaways + Contact

Design notes:
- JBS brand colors (teal accent, slate/white)
- Minimal text
- Data-driven where possible
- Professional, modern layout

Output clean markdown I can paste directly into Gamma.
```


***

### **5. Infographic Data Prompt (Gemini Pro)**

```
Content Brief: [PASTE BRIEF]

Extract infographic-ready content:

## Title
[Short, catchy]

## Key Statistics (5–7)
[Stat]: "Context"

## Process Flow (if applicable)
[3–5 step process with descriptions]

## Comparison Table
| Option A | Option B | Option C |
|----------|----------|----------|
| [Value]  | [Value]  | [Value]  |

## Visual Hierarchy
- Hero stat: [Most important number]
- Supporting stats: [3–4 secondary]

## Design Suggestions
- Layout type: [vertical/horizontal/circular]
- Color coding: [By category/value/type]
- Icons needed: [List 8–10]

Format for Pyxa.ai or Canva.
```


***

## **Quick Start: 3-Step MVP**

1. **This week:**
    - Build the n8n workflow above (start with just Perplexity → Claude → save to Drive).
    - Test with 2 topics: one technical (e.g., "RAG for utilities"), one domain (e.g., "Wind forecasting methods").
2. **Week 2:**
    - Add Gemini video script node.
    - Test script in HeyGen (paste script, pick avatar, generate).
    - Add Claude PPT node.
    - Test PPT markdown in Gamma App.
3. **Week 3:**
    - Add infographic node.
    - Build your first 2 complete courses end-to-end.
    - Share with JBS team for feedback.

***

**Want me to:**

1. Write the complete n8n workflow JSON you can import directly?
2. Draft the exact system prompts for Claude/Gemini tailored to JBS voice?
3. Design a simple "training request form" (Typeform/Airtable) that triggers this workflow?

Let me know and I'll build it out for you.

---

# can I use Google adk to build this system

Yes, you can absolutely use Google’s stack to build this, and it actually fits your “one core system, many outputs” idea very well.[^3_1][^3_2][^3_3]

I’ll map it concretely to what you want.

***

## 1. What “using Google” really means here

You have two main options:

- **Google AI Studio / Gemini API (aka Google AI SDK):**
Use Gemini models directly from your own app, n8n, or scripts to:
    - Do domain research (or co‑research with Perplexity).
    - Generate master briefs, scripts, PPT markdown, infographic specs.[^3_1][^3_2][^3_3]
- **Google Workspace + Apps Script + Gemini API:**
Use Apps Script to:
    - Read/write Docs, Slides, Sheets.
    - Call Gemini from Apps Script (with GeminiApp or direct HTTP).
    - Auto-fill Slides with content, create Docs with scripts, etc.[^3_4][^3_5][^3_6]

You can combine them: **n8n as the orchestrator, Gemini API as the brain, Google Workspace as the content store.**[^3_2][^3_4]

***

## 2. Using Gemini API as the core “content engine”

Google’s Gen AI SDK / Gemini API supports `generateContent` for text, structure, JSON, etc.[^3_2][^3_3]

In your case, one Gemini flow can:

1. Take the topic prompt.
2. Generate a **content brief** (learning objectives, audience, outline).
3. From the brief, generate:
    - **Video script** (scene-by-scene, with visual cues).
    - **Slide deck markdown/outline** for Gamma or Slides.
    - **Infographic JSON** (stats, tables, process flows, design hints).[^3_2]

You already use Gemini Pro; “Google AI SDK” is just how you call that same capability from code (n8n, Apps Script, or backend).[^3_2][^3_1]

***

## 3. Connecting Gemini to n8n

You can directly use Gemini in n8n via HTTP Request or Gemini nodes:

- Tutorials show step‑by‑step how to:
    - Create a Google AI Studio or Google Cloud project.
    - Get an API key.
    - Plug it into n8n as credentials.
    - Call the Gemini Chat/GenerateContent endpoint from workflows.[^3_7][^3_8][^3_9]

n8n flow pattern:

1. **Trigger:** Topic text (manual, webhook, or form).
2. **Node 1 (Gemini):** Generate “Master Content Brief.”
3. **Node 2 (Gemini):** From brief → video script.
4. **Node 3 (Gemini):** From brief → PPT outline/markdown.
5. **Node 4 (Gemini):** From brief → infographic specification (JSON).
6. **Node 5:** Save outputs to Google Drive/Sheets/Docs or send to Gamma/NotebookLM.

So yes, you can keep most generation purely in Gemini via the Google AI SDK, without needing another LLM if you don’t want.[^3_2][^3_3]

***

## 4. Using Apps Script + Gemini inside Workspace

If you prefer to live inside Google Docs/Slides instead of n8n for some pieces:

- Google’s codelab shows:
    - How to call Gemini from Apps Script (script.new).
    - How to use function calling to automate Workspace tasks.[^3_4]
- The GeminiApp library wraps the Gemini API nicely for Apps Script, enabling:
    - Multi-modal prompts.
    - Structured JSON output.
    - Token management/caching.[^3_5]

Example pattern:

- Apps Script bound to a Google Doc:
    - Reads your topic from a cell/paragraph.
    - Calls Gemini to generate a slide outline.
    - Auto-creates a Google Slides deck with title and bullet content.

This could sit alongside your n8n system, or you choose one as primary.

***

## 5. How to blend this with your existing tools

With Google as the “core engine,” you can still use everything else:

- **HeyGen / Veed.io:**
Paste the Gemini-generated script and visual cues into HeyGen to produce the actual video.
- **Gamma App:**
Paste the slide markdown from Gemini to instantly generate a polished deck.
- **NotebookLM:**
Upload the research + brief for “audio overview” or Q\&A on each module.
- **Pyxa.ai:**
Feed it the infographic JSON/outline from Gemini to create graphics.

So yes: **Google AI SDK (Gemini API) + n8n can be your main engine**, with Claude/Perplexity as optional “specialists” you call when needed; you don’t have to.[^3_2][^3_4][^3_3]

***

If you’d like, I can now give you:

- A concrete Gemini `generateContent` prompt template tailored to your JBS training use case, and
- A minimal n8n HTTP node config (body/headers) you can paste in to test the first “topic → master content brief” step.
<span style="display:none">[^3_10][^3_11][^3_12][^3_13][^3_14][^3_15]</span>

<div align="center">⁂</div>

[^3_1]: https://ai.google.dev/gemini-api/docs/ai-studio-quickstart

[^3_2]: https://docs.cloud.google.com/vertex-ai/generative-ai/docs/model-reference/inference

[^3_3]: https://ai.google.dev

[^3_4]: https://codelabs.developers.google.com/codelabs/gemini-workspace

[^3_5]: https://github.com/mhawksey/GeminiApp

[^3_6]: https://kartaca.com/en/no-code-no-problem-automating-google-workspace-with-gemini-and-apps-script/

[^3_7]: https://www.youtube.com/watch?v=nJuiFLfXr5g

[^3_8]: https://www.youtube.com/watch?v=ZIQuzDyuN34

[^3_9]: https://www.youtube.com/watch?v=rwuUF7CoKaI

[^3_10]: https://aistudio.google.com/case-studies/spline

[^3_11]: https://www.youtube.com/watch?v=JbwBuFYXl4E

[^3_12]: https://www.ctcd.edu/sites/myctcd/today/app.html?app=build-ai-first-apps-faster-with-google-ai-studio-698ca37f6f8fe

[^3_13]: https://dev.catalog.calpia.ca.gov/custom/assets/detail/index.html?app=build-ai-first-apps-faster-with-ai-google-studio-695e0497b92ce

[^3_14]: https://www.reddit.com/r/Bard/comments/1rc2793/google_ai_studio_is_set_to_be_powered_by/

[^3_15]: https://support.google.com/gemini/answer/15229592?hl=en


---

# concrete Gemini generateContent prompt template tailored to your JBS training use case, and

Here’s a concrete Gemini `generateContent` prompt template you can reuse as the **core JBS Training Generator** for any topic.

You’ll pass this as the `text` in `contents.parts` to Gemini (API, AI Studio, or wherever you call it).

***

## 1. Master prompt template (one-shot “all outputs”)

Use this when you want **research + brief + video script + slides + infographic spec** in one call.

```text
You are a senior instructional designer and AI/content strategist for 
Jade Business Services (JBS), a Data & AI solutions company specializing 
in the Energy & Utilities industry.

Your job is to take a single topic and generate all core training assets
for JBS employees and clients.

COMPANY CONTEXT (JBS)
- We build Data & AI solutions for Energy & Utilities (generation, T&D, 
  renewables, retail).
- Typical learners: data engineers, data scientists, analytics engineers, 
  solution architects, project managers, and business stakeholders at utilities.
- We work a lot with Azure, GCP, Databricks, and modern GenAI patterns 
  (RAG, agents, MLOps, lakehouse).

TASK
Given the topic and audience, produce ALL of the following, in order:

1) QUICK SUMMARY
- 2–3 sentences describing the topic at a high level.
- 3 bullet points: why this matters for JBS and Energy & Utilities.

2) MASTER CONTENT BRIEF
Structure as:

## Core Message
- One-sentence takeaway
- 3–5 learning objectives (clear, measurable)

## Audience & Level
- Target audience description
- Level: Beginner / Intermediate / Advanced
- Prerequisites (skills, tools, concepts)

## Narrative Arc
- Hook: 2–3 sentences posing the core problem or question
- Context: 4–6 sentences of background
- Solution / Methods: 5–8 bullet points
- Applications in Energy & Utilities: 5–8 bullet points
- Future trends (next 3–5 years): 3–5 bullet points

## JBS Angle
- How JBS might implement or sell this (Azure/GCP/Databricks/GenAI)
- Typical JBS-style use cases (keep client details generic)

## Key Terms to Explain
- 5–10 essential terms with one-line definitions

3) VIDEO TRAINING SCRIPT (8–10 minutes)
Write a complete video script with:

### Overall Instructions
- Spoken style: short sentences, natural tone, no long paragraphs.
- Assume voice-over with supporting visuals (screen, diagrams, charts).
- Audience: [AUDIENCE_PLACEHOLDER].

### Script Structure
Provide scenes in this exact format:

#### Scene 1 – Hook (0:00–0:45)
Narration:
[Write narration]

On-screen text:
- [Bullet phrase 1]
- [Bullet phrase 2]

Visuals:
- [Describe visuals: diagrams, charts, b-roll, etc.]

#### Scene 2 – Context (0:45–2:00)
Narration:
[...]

On-screen text:
- [...]

Visuals:
- [...]

[Continue scenes until ~8–10 minutes total:
- Concept explanation
- Step-by-step workflow or architecture
- Energy & Utilities use cases
- Common pitfalls
- Closing / call to action]

#### Final Scene – Call to Action
Narration:
[Summarize key points and next steps, mention JBS and jade-biz.com]

On-screen text:
- 3 key takeaways
- URL: jade-biz.com

Visual Assets Needed (list):
- [List all diagrams, charts, example dashboards, icons, etc.]

4) SLIDE DECK OUTLINE (for Gamma or Google Slides)
Output in clean markdown:

# Slide 1 – Title
Title: [Compelling title]
Subtitle: [Contextual subtitle]
Footer: Jade Business Services – Data & AI for Energy & Utilities

---
# Slide 2 – Agenda
- [Bullet 1]
- [Bullet 2]
- [Bullet 3]

---
# Slide 3 – Problem / Hook
Key points:
- [Bullet 1]
- [Bullet 2]
Visual:
- [Diagram or image description]

---
# Slide 4 – Core Concepts
Key points:
- [...]
Visual:
- [...]

[Continue until 10–15 slides, covering:
- Problem/context
- Core concepts
- Architecture / workflow
- Energy & Utilities use cases
- Example metrics
- Summary / next steps]

---
# Slide N – Key Takeaways
- [Takeaway 1]
- [Takeaway 2]
- [Takeaway 3]

Footer: jade-biz.com

Design notes (do NOT turn into slides):
- Use JBS brand feel: modern, clean, teal accent with dark/light neutrals.
- Max 5 bullets per slide.
- Prefer one visual (diagram/chart) per content slide.

5) INFOGRAPHIC SPEC (for Pyxa.ai or Canva)
Produce an infographic blueprint:

## Infographic Title
[Short, punchy title]

## Hero Statistic
- [One primary stat with short explanation]

## 5–7 Supporting Statistics
1. [Stat 1] – [1–2 sentence context]
2. [Stat 2] – [...]
3. [...]

## Process / Framework (if applicable)
List 3–7 steps with short descriptions.

## Comparison Section (if applicable)
Simple markdown table:
| Option A | Option B | Option C |
|---------|----------|----------|
| [...]   | [...]    | [...]    |

## Visual Layout Suggestions
- Layout type (vertical / horizontal / grid)
- Suggested sections (top / middle / bottom)
- Color-coding idea
- Icon suggestions (list 8–10 icon ideas)

GENERAL STYLE
- Assume everything is used for internal and client-facing training.
- Be technically accurate but accessible.
- Prefer concrete examples in Energy & Utilities (keep client names generic).
- Avoid hallucinating impossible numbers; if you need a statistic, label it as an illustrative example, not a real measured value.

INPUTS
Topic: {{TOPIC}}
Audience: {{AUDIENCE}}
Desired depth: {{LEVEL}} (Beginner / Intermediate / Advanced)

Now generate all sections in order, using clear headings so a workflow can parse them.
```

You would programmatically replace `{{TOPIC}}`, `{{AUDIENCE}}`, and `{{LEVEL}}` before sending the prompt.

***

## 2. Variant prompts for separate calls (if you want separate endpoints)

If you decide to break it into multiple steps, you can:

- Use the **same Master Content Brief section** as the first call.
- Then have smaller prompts like:


### A. “From brief → video script”

```text
You are a video scriptwriter for Jade Business Services.

Use this content brief to write the full video script:

[PASTE MASTER CONTENT BRIEF HERE]

Audience: {{AUDIENCE}}
Target length: {{LENGTH_MINUTES}} minutes

[Then reuse ONLY section 3) VIDEO TRAINING SCRIPT from the big prompt above]
```


### B. “From brief → slide deck”

```text
You are a presentation designer for Jade Business Services.

Use this content brief to create a slide deck outline in markdown:

[PASTE MASTER CONTENT BRIEF HERE]

[Then reuse ONLY section 4) SLIDE DECK OUTLINE from the big prompt]
```


### C. “From brief → infographic spec”

```text
You are an information designer for Jade Business Services.

Use this content brief to design an infographic blueprint:

[PASTE MASTER CONTENT BRIEF HERE]

[Then reuse ONLY section 5) INFOGRAPHIC SPEC from the big prompt]
```


***

If you tell me your preferred **default audience and level** (e.g., “Intermediate data engineer in Energy \& Utilities”), I can tighten this further into a shorter “production” prompt you can drop directly into your Gemini API calls.

---

# I want to be part of an holistic enterprise system. I need the entire support functions to be leveraging an enterprise wide agentic framework. my functions of enterprise content development for training, hr administration multiple functions, marketing content creation, sales outbound outreach to be part of the same architecture. I want a detailed scope of work which spells out the overall vision but defines the detailed scope for enterprise training as defined above for my development team. Make it as detailed as possible so I can share with them and they should get all the user stories, workflows.

Below is a **scope of work (SoW)** you can hand to your team that:

- States the **enterprise-wide agentic vision**, and
- Gives **very detailed scope, user stories, and workflows** for the **Enterprise Training Content System** as the first pillar.[^5_1][^5_2][^5_3]

***

## 1. Vision: JBS Holistic Agentic Enterprise

### 1.1 Vision Statement

Jade Business Services (JBS) will implement an **enterprise-wide agentic framework** where AI agents and humans collaborate across all support functions—Training, HR, Marketing, Sales, and Operations.[^5_1][^5_4][^5_5]

Key principles:

- **Shared architecture:** One common AI backbone (Gemini / Claude / OpenAI + RAG) serving all departments, not isolated tools.[^5_2][^5_6][^5_3]
- **Specialized agents:** Domain-specific agents (Training Agent, HR Agent, Marketing Agent, Sales Agent) built on the same platform, sharing data and patterns where appropriate.[^5_7][^5_3][^5_8]
- **Human-in-the-loop:** Humans act as “agent bosses”—reviewing, approving, and escalating, with clear audit trails.[^5_1][^5_4][^5_9]
- **Workflow orientation:** Agents own end-to-end workflows (e.g., “create training module”, “onboard employee”, “launch outbound campaign”), not just single prompts.[^5_6][^5_7][^5_10]
- **Observability and governance:** Central monitoring, usage analytics, and performance metrics for all agent actions.[^5_3][^5_8][^5_9]

***

## 2. Enterprise Agentic Architecture (High-Level Scope)

### 2.1 Core Platform Components

1. **LLM / Agent Layer**
    - Primary: **Gemini (Google AI SDK / Gemini Enterprise)** as default model.[^5_11][^5_12][^5_3]
    - Secondary: Claude, OpenAI, Perplexity for specialized tasks (e.g., research, long-context, reasoning).
    - Agent framework (e.g., Gemini Enterprise Agents, custom orchestration, or n8n-based agent flows).[^5_13][^5_3][^5_8]
2. **Orchestration Layer**
    - **n8n** as the primary workflow orchestrator for automation across tools (LLMs, CRM, HRIS, LMS, email, storage).[^5_6][^5_10]
    - Reusable “agentic workflow” templates: trigger → plan → call tools/APIs → generate content → route for approval → publish/log.[^5_6][^5_7]
3. **Knowledge \& Data Layer**
    - Central **RAG index**:
        - JBS internal content (SharePoint / Google Drive / Notion / Confluence).
        - Structured data from CRM, HRIS, LMS.
        - Curated external sources (NREL, IEEE, IEA, vendor docs) for Energy \& Utilities + Data/AI.[^5_14][^5_15][^5_7]
4. **Application Layer (Enterprise Functions)**
    - **Enterprise Training Agent** (Phase 1 – detailed below).
    - HR Admin Agent (policies, onboarding, FAQs, forms).
    - Marketing Content Agent (blogs, campaigns, assets).
    - Sales Outreach Agent (researched sequences, personalization, logging).[^5_5][^5_16][^5_10]
5. **Governance \& Measurement**
    - Role-based access, content approval workflows.
    - Metrics: time saved, cycle times, quality ratings, usage by function, error/issue logs.[^5_1][^5_9][^5_17]

***

## 3. Scope Focus: Enterprise Training Agent (Detailed)

### 3.1 Objectives

- Build a **central Enterprise Training Agent** that converts a single topic request into all necessary training assets:
    - Research brief
    - Master content brief
    - Video script for Veed/HeyGen
    - Slide deck outline (Gamma/Slides)
    - Infographic blueprint
    - Quiz/assessment questions
- Support **two learning domains**:
    - Technical: Data \& AI concepts.
    - Domain: Energy \& Utilities concepts.[^5_14][^5_15]

***

### 3.2 Users \& Roles

- **Content Owner (Training Lead / SME):** Requests new modules, approves final content.
- **Instructional Designer:** Fine-tunes outlines, ensures pedagogy and consistency.
- **Video Producer:** Uses scripts in Veed/HeyGen to generate videos.
- **Graphic/Deck Designer:** Uses slide outlines \& infographics in Gamma, Pyxa, Canva.
- **Learners:** JBS team members (Data engineers, DS, PMs, Sales, HR).
- **Admin:** Manages access, templates, taxonomies, and analytics.

***

### 3.3 Functional Scope (Training Agent)

**F1. Topic Intake \& Classification**

- Accept a topic + metadata:
    - Topic name.
    - Domain: Data/AI or Energy/Utilities (or both).
    - Target audience (role, seniority).
    - Level (Beginner / Intermediate / Advanced).
    - Desired formats (video, slides, infographic, quiz).
- Automatically classify into:
    - Learning path (e.g., “Technical Foundations”, “Utility Domain 101”, “Advanced Forecasting”).
    - Module type (intro/concept/deep-dive/case study).

**F2. Research \& Knowledge Grounding**

- Call Perplexity/Gemini/other to run **structured research** with curated sources.[^5_14][^5_15][^5_7]
- Pull from:
    - RAG index of JBS content.
    - External trusted sources (NREL, IEEE, IEA, Databricks, etc.).[^5_14][^5_15]
- Output: Research Brief (citations, key concepts, applications, challenges, trends).

**F3. Master Content Brief Generation**

- From research + topic metadata, generate a standard **Master Content Brief** including:
    - Core message \& learning objectives.
    - Audience details \& prerequisites.
    - Narrative arc (hook, context, solution, applications, CTA).
    - JBS angle (services, platforms, typical use cases).
    - Key terms to define.
    - Visual opportunities.[^5_5][^5_3]

**F4. Asset Generation**

From the Master Content Brief, generate:

- **Video Script (V1)**
    - Scene-based script with timestamps, narration, on-screen text, and visual cues.
    - List of visual assets needed (charts, diagrams, b-roll types).
- **Slide Deck Outline (V1)**
    - 10–15 slides in structured markdown.
    - Title, agenda, concept, architecture/workflow, use cases, summary.
    - Design notes for Gamma/Slides.
- **Infographic Spec (V1)**
    - Hero stat, 5–7 supporting stats, process flow, comparison table.
    - Layout and icon suggestions.
- **Assessment Items (V1)**
    - 5–10 questions per module (MCQs, scenario-based).
    - Answer key + rationale.

**F5. Workflow \& Approvals**

- Push all V1 outputs into storage (Drive/SharePoint) with structured naming.
- Create a review task for Content Owner \& Instructional Designer.
- Provide a summary email/Slack message with links and quick view.
- Track approval status (Draft → In Review → Approved → Published).

**F6. Publishing \& Integration**

- Once approved:
    - Publish metadata and links into LMS/knowledge portal (e.g., Zoho Learn, custom portal).
    - Tag modules by:
        - Role, seniority, domain, tech stack (Azure/GCP/Databricks), level.
    - Make content searchable from an internal “Learning Copilot” chat interface.

**F7. Analytics \& Feedback**

- Track:
    - Number of modules generated.
    - Time saved vs traditional creation.
    - Usage/consumption metrics from LMS.
    - Feedback rating per module (1–5) and free-text comments.
- Use analytics to improve templates and prompts iteratively.[^5_9][^5_3]

***

## 4. User Stories – Enterprise Training Agent

### 4.1 Topic Intake \& Planning

1. **As a Training Lead**, I want to submit a topic and target audience so that the system can generate appropriate training assets.
2. **As a SME**, I want to select a domain (Data/AI or Energy/Utilities) and level so that content depth matches learner needs.
3. **As a Training Lead**, I want the agent to suggest where the module fits in existing learning paths so that the curriculum remains coherent.

### 4.2 Research \& Grounding

4. **As a SME**, I want the agent to compile a research brief using curated internal and external sources so that I don’t have to manually research every new module.[^5_14][^5_15][^5_7]
5. **As a Content Owner**, I want citations included so I can validate the information and update sources if needed.[^5_15][^5_7]

### 4.3 Content Brief Creation

6. **As an Instructional Designer**, I want a consistent Master Content Brief structure so that all modules follow a similar pedagogical flow.
7. **As a Training Lead**, I want learning objectives auto-generated so I can quickly validate alignment with JBS competency frameworks.

### 4.4 Asset Generation

8. **As a Video Producer**, I want scene-based scripts with timestamps and visual cues so I can quickly create videos in HeyGen/Veed.io.
9. **As a Designer**, I want slide markdown with visuals descriptions so I can import into Gamma and finalize the deck.
10. **As a Designer**, I want an infographic blueprint with stats and layout suggestions so I can build visual assets in Pyxa/Canva.
11. **As a Training Lead**, I want auto-generated quiz questions so I can quickly add assessments to the LMS.

### 4.5 Workflow \& Approval

12. **As a Content Owner**, I want all assets from a topic stored and linked in one place so I can review them together.
13. **As a Reviewer**, I want to mark each asset as approved/rejected with comments so that iterations are tracked.
14. **As an Admin**, I want to track status of each module (draft/review/approved/published) so that nothing is lost or half-done.

### 4.6 Publishing \& Discovery

15. **As a Learner**, I want modules to be discoverable by role, topic, and level so that I can self-serve learning paths.
16. **As a Manager**, I want to assign modules to my team and track completion so that I can enforce required training.

### 4.7 Analytics \& Improvement

17. **As a Training Lead**, I want to see analytics on content creation speed and learner feedback so that I can refine the templates and prompts.
18. **As an Executive**, I want to view how training content correlates with project performance (optional later) so that we can justify investment in the agentic framework.

***

## 5. End-to-End Workflow (Training Agent) – As Implemented in n8n

### 5.1 Trigger

- Trigger types:
    - Manual form (Typeform/Airtable or simple internal form).
    - Slack slash command (`/new-training-topic`).
- Input fields:
    - Topic title.
    - Domain (Technical / Domain / Both).
    - Audience role \& level.
    - Formats required (Video, Slides, Infographic, Quiz).


### 5.2 Workflow Steps

1. **Node: “Create Topic Record”**
    - Create a record in a central “Training Topics” table (Airtable/Sheets/DB).
2. **Node: “Research” (Perplexity/Gemini)**
    - Build prompt using topic \& domain.
    - Save Research Brief in Drive/SharePoint.
3. **Node: “Master Content Brief” (Gemini/Claude)**
    - Use prompt template (like the one we designed) to generate Master Content Brief.
    - Save as markdown/Doc.
4. **Parallel Nodes – Asset Generation**
    - **Video Script Node**: generate video script \& visual asset list.
    - **Slides Node**: generate slide markdown.
    - **Infographic Node**: generate infographic blueprint.
    - **Quiz Node**: generate quiz questions \& answers.
5. **Node: “Aggregate \& Store Outputs”**
    - Create a folder for the topic.
    - Save each asset with consistent naming.
6. **Node: “Create Review Task”**
    - Create a task in your PM tool (Jira/ClickUp/Trello) for reviewers.
    - Attach links to assets and status field.
7. **Node: “Notify Reviewers”**
    - Slack/Email message to Training Lead + SME with summary and links.
8. **Node: “Approval Updates”**
    - When reviewers change status in PM tool, update the “Training Topics” table \& metadata.
9. **Node: “Publish to LMS/Portal”**
    - On approval, write module metadata \& links into LMS (via API or CSV/import).
10. **Node: “Log Analytics”**
    - Log key timestamps (topic submission, asset generation completion, approval date) for reporting.

***

## 6. How This Fits the Wider Agentic Enterprise

You want **one architecture** where the same principles apply to HR, Marketing, Sales.[^5_5][^5_7][^5_16]

Examples of parallel agents:

- **HR Admin Agent:** Onboarding/offboarding workflows, policy Q\&A, document generation (offer letters, confirmations), ticket triage.[^5_2][^5_18]
- **Marketing Content Agent:** Campaign briefs, persona-based content, repurposing training content into public-facing material.[^5_5][^5_10]
- **Sales Outreach Agent:** Lead research, multi-step outbound sequences, personalized messaging, CRM logging.[^5_6][^5_16][^5_10]

All built on:

- The same **LLM/agent stack** (Gemini/Claude/OpenAI).
- The same **n8n orchestration pattern** (trigger → research → brief → asset → approval → publish).
- The same **observability \& governance layer**.[^5_6][^5_3][^5_9]

***

If you want, I can next turn this into:

- A **one-page architecture diagram description** your devs can implement, and/or
- A **first backlog**: epics, stories, and milestones for Phase 1 (Training Agent) over 6–8 weeks.
<span style="display:none">[^5_19]</span>

<div align="center">⁂</div>

[^5_1]: https://www.salesforce.com/agentforce/agentic-enterprise/

[^5_2]: https://www.moveworks.com/us/en/resources/blog/what-is-agentic-framework

[^5_3]: https://intuitionlabs.ai/articles/gemini-enterprise-deployment-architecture-guide

[^5_4]: https://www.mckinsey.com/capabilities/people-and-organizational-performance/our-insights/the-future-of-work-is-agentic

[^5_5]: https://writer.com/guides/ai-use-cases/

[^5_6]: https://hightouch.com/blog/agentic-workflows

[^5_7]: https://www.ema.co/additional-blogs/addition-blogs/understanding-agentic-ai-and-its-role-in-enterprise-evolution

[^5_8]: https://cloud.google.com/gemini-enterprise/agents

[^5_9]: https://isg-one.com/articles/from-potential-to-performance--building-an-enterprise-measurement-framework-for-agentic-ai

[^5_10]: https://www.jadasquad.com/blogs/top-5-use-cases-for-agentic-workflows

[^5_11]: https://docs.cloud.google.com/vertex-ai/generative-ai/docs/model-reference/inference

[^5_12]: https://ai.google.dev

[^5_13]: https://smythos.com/developers/agent-integrations/gemini-ai-agent-builder-api/

[^5_14]: https://upskilldevelopment.com/energy-data-analytics-and-digital-transformation-in-power-systems-training-course

[^5_15]: https://copextraining.com/courses/ai-application-for-utility

[^5_16]: https://www.highspot.com/blog/agentic-workflows/

[^5_17]: https://www.bcg.com/publications/2025/how-agentic-ai-is-transforming-enterprise-platforms

[^5_18]: https://www.linkedin.com/pulse/agentic-ai-hr-transforming-workforce-2025-puneet-sachdev-rtsje

[^5_19]: https://www.linkedin.com/pulse/four-systems-agentic-enterprise-bob-vanstraelen-amrje

