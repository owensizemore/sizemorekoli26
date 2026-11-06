---
theme: ./slidev-theme-cs390
title: GenAI-Powered Postsecondary Computer Science Education Tools A Systematic
  Literature Review
class: title-slide
---

# GenAI-Powered Postsecondary Computer Science Education Tools
## A Systematic Literature Review

<div class="authors">
  <div class="author">
    <div class="author-name"><strong>Owen Sizemore</strong></div>
    <div class="author-photo-wrap">
      <div class="author-photo wide-shot">
        <img src="/authors/owen.jpg" alt="Owen Sizemore" />
      </div>
      <div class="author-badge">
        <img src="/logos-square/duke.png" alt="Duke" />
      </div>
    </div>
  </div>
  <div class="author">
    <div class="author-name">Seth Bernstein</div>
    <div class="author-photo-wrap">
      <div class="author-photo">
        <img src="/authors/seth.png" alt="Seth Bernstein" />
      </div>
      <div class="author-badge">
        <img src="/logos-square/michigan.png" alt="Michigan" />
      </div>
    </div>
  </div>
  <div class="author">
    <div class="author-name">Audrey Ostrom</div>
    <div class="author-photo-wrap">
      <div class="author-photo">
        <img src="/authors/audrey.png" alt="Audrey Ostrom" />
      </div>
      <div class="author-badge badge-ucsc">
        <img src="/logos-square/santacruz.jpg" alt="UCSC" />
      </div>
    </div>
  </div>
  <div class="author">
    <div class="author-name">Thomas Rexin</div>
    <div class="author-photo-wrap">
      <div class="author-photo">
        <img src="/authors/thomas.jpg" alt="Thomas Rexin" />
      </div>
      <div class="author-badge badge-ncstate">
        <img src="/logos-square/ncstate.png" alt="NC State" />
      </div>
    </div>
  </div>
  <div class="author">
    <div class="author-name">Kristin Stephens-Martinez</div>
    <div class="author-photo-wrap">
      <div class="author-photo">
        <img src="/authors/kristin.jpg" alt="Kristin Stephens-Martinez" />
      </div>
      <div class="author-badge">
        <img src="/logos-square/duke.png" alt="Duke" />
      </div>
    </div>
  </div>
</div>

<style>
.authors {
  display: grid;
  grid-template-columns: repeat(5, max-content);
  justify-content: center;
  column-gap: 3.5rem;
  margin-top: 1.5rem;
  margin-left: -2.5rem;
  margin-right: -2.5rem;
  align-items: start;
}
.author {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.55rem;
}
.author-name {
  font-size: 0.9rem;
  font-weight: 500;
  line-height: 1.2;
  text-align: center;
  white-space: nowrap;
}
.author-photo-wrap {
  position: relative;
  width: 6rem;
  height: 6rem;
  flex-shrink: 0;
}
.author-photo {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  overflow: hidden;
}
.author-photo img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center 22%;
}
.author-photo.wide-shot img {
  object-position: center 12%;
  transform: scale(1.65);
  transform-origin: center 18%;
}
.author-badge {
  position: absolute;
  right: -0.15rem;
  bottom: -0.15rem;
  width: 2.05rem;
  height: 2.05rem;
  border-radius: 50%;
  overflow: hidden;
  border: 2.5px solid #fff;
  background: #fff;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.28);
}
.author-badge img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.author-badge.badge-ucsc img {
  transform: scale(1.22);
}
.author-badge.badge-ncstate {
  background: #cc0000;
}
.author-badge.badge-ncstate img {
  object-fit: contain;
  transform: scale(1.28);
}
</style>

---

# How do we regulate GenAI use in postsecondary CSEd?

<SpectrumArrow />

---

# What does this look like?
- Course interventions to learn how to use GenAI
- Student reflections to encourage thoughtful GenAI use
- <span v-mark.underline.green="5">Custom tools with guardrails to mitigate irresponsible GenAI use</span>

---
layout: center
---

<img src="/misc/umbrella2.png" alt="GenAI-Powered Postsecondary CSEd Tools umbrella term" style="max-height: 85vh; width: auto; padding: 7rem 7rem;" />

---
class: tool-flow-slide
---

<h1 class="tool-flow-title">Tool Paradigms</h1>

<div class="tool-flow">

```mermaid
%%{init: {"flowchart": {"nodeSpacing": 10, "rankSpacing": 4, "padding": 8, "htmlLabels": true, "useMaxWidth": true}, "themeVariables": {"fontSize": "22px"}}}%%
flowchart LR
    subgraph c1[" "]
      direction TB
      SP["<img src='/public/icons/person.png' width='72' height='72' style='width:72px;height:72px;object-fit:contain;aspect-ratio:1/1' /> <strong>Student prompt</strong>"]
      CTX["<img src='/public/icons/text.png' width='72' height='72' style='width:72px;height:72px;object-fit:contain;aspect-ratio:1/1' />Context"]
    end
    subgraph c2[" "]
      direction TB
      IC["<img src='/public/icons/filter.png' width='72' height='72' style='width:72px;height:72px;object-fit:contain;aspect-ratio:1/1' />Input filtering"]
      SYS["<img src='/public/icons/guide.png' width='72' height='72' style='width:72px;height:72px;object-fit:contain;aspect-ratio:1/1' /> <strong>System prompts</strong>"]
      KB["<img src='/public/icons/database.png' width='72' height='72' style='width:72px;height:72px;object-fit:contain;aspect-ratio:1/1' />Knowledge base"]
    end
    subgraph c3[" "]
      LLM["<img src='/public/icons/chatgpt.png' width='72' height='72' style='width:72px;height:72px;object-fit:contain;aspect-ratio:1/1' /> <strong>LLM Endpoint</strong>"]
    end
    subgraph c4[" "]
      RC["<img src='/public/icons/checks.png' width='72' height='72' style='width:72px;height:72px;object-fit:contain;aspect-ratio:1/1' />Response checks"]
    end
    subgraph c5[" "]
      OUT["<img src='/public/icons/reply.png' width='72' height='72' style='width:72px;height:72px;object-fit:contain;aspect-ratio:1/1' /> <strong>Response to student</strong>"]
    end

    SP --> IC
    CTX --> IC

    IC --> LLM
    SYS --> LLM
    KB --> LLM

    LLM --> RC
    RC --> OUT

    classDef col1 fill:#e3efff,stroke:#6ea8dc,color:#000,stroke-width:1px
    classDef col1Bold fill:#e3efff,stroke:#3d7ab8,color:#000,stroke-width:12px,font-weight:bold
    classDef col2 fill:#e2f4e8,stroke:#6bb57c,color:#000,stroke-width:1px
    classDef col2Bold fill:#e2f4e8,stroke:#2e7d3a,color:#000,stroke-width:12px,font-weight:bold
    classDef col3 fill:#fff3cd,stroke:#d4b44a,color:#000,stroke-width:1px
    classDef col3Bold fill:#fff3cd,stroke:#b89620,color:#000,stroke-width:12px,font-weight:bold
    classDef col4 fill:#eee5ff,stroke:#a78bdb,color:#000,stroke-width:1px
    classDef col5 fill:#ddf5f2,stroke:#5aaaa0,color:#000,stroke-width:1px
    classDef col5Bold fill:#ddf5f2,stroke:#2d8a80,color:#000,stroke-width:12px,font-weight:bold
    class SP col1Bold
    class CTX col1
    class IC,KB col2
    class SYS col2Bold
    class LLM col3Bold
    class RC col4
    class OUT col5Bold
    style c1 fill:none,stroke:none,color:transparent
    style c2 fill:none,stroke:none,color:transparent
    style c3 fill:none,stroke:none,color:transparent
    style c4 fill:none,stroke:none,color:transparent
    style c5 fill:none,stroke:none,color:transparent
```

</div>

<style>
.tool-flow-title {
  position: absolute;
  top: 2rem;
  right: 4rem;
  margin: 0;
  text-align: right;
  z-index: 5;
  pointer-events: none;
}
.tool-flow {
  box-sizing: border-box;
  width: 100%;
  padding: 0 1rem;
  margin: 0 auto;
}
.tool-flow :deep(.mermaid) {
  display: block;
  width: 100%;
}
.mermaid img {
  width: 72px !important;
  height: 72px !important;
  max-width: 72px !important;
  object-fit: contain !important;
  aspect-ratio: 1 / 1;
}
</style>

---
autoClicks: false
---

# Research Questions
1. <span class="hl-blue"><strong>RQ1 (Approaches & motivations)</strong></span>: What approaches are currently used to build GenAI-powered postsecondary CSEd tools, and how are they motivated?
2. <span class="hl-pink"><strong>RQ2 (Educational framings)</strong></span>: What educational theories and framings inform the development of GenAI-powered postsecondary CSEd tools?
3. <span class="hl-green"><strong>RQ3 (Evaluations)</strong></span>: What methods are used to empirically evaluate the effects of GenAI-powered postsecondary CSEd tools?

<style>
.slidev-layout > ol > li {
  margin-bottom: 1rem;
}
</style>

---

## Literature Review Methodology
<p class="text-center">(Kitchenham & Charters, PRISMA)</p>

<div class="w-full flex justify-center">

```mermaid {scale: 0.85}
%%{init: {"flowchart": {"wrappingWidth": 640, "minNodeWidth": 640, "rankSpacing": 24, "padding": 10, "useMaxWidth": false, "htmlLabels": true}}}%%
flowchart TD
    A[Create IC/EC based on seed papers] --> B["Search digital libraries (<strong>n=1,834</strong>)"]
    B --> C["Apply IC/EC to titles/abstracts (<strong>n=117</strong>)"]
    C --> D[Develop codebook with paper sample, calculate IRR]
    D --> E["Apply IC/EC to full papers (<strong>n=72</strong>)"]
```

</div>

---

## Codebook Categories

<div class="card-grid">

  <div class="info-card card-blue">
    <span class="rq-label">RQ1</span>
    <h3>Problem Space</h3>
    <p>Why is the tool being built?</p>
  </div>

  <div class="info-card card-blue">
    <span class="rq-label">RQ1</span>
    <h3>Pedagogical Features</h3>
    <p>How does the tool support learning?</p>
  </div>

  <div class="info-card card-blue">
    <span class="rq-label">RQ1</span>
    <h3>Delivery Method</h3>
    <p>How do students access the tool?</p>
  </div>

  <div class="info-card card-pink">
    <span class="rq-label">RQ2</span>
    <h3>Educational Framings</h3>
    <p>What research is the tool based on?</p>
  </div>

  <div class="info-card card-green">
    <span class="rq-label">RQ3</span>
    <h3>Evaluation Goals</h3>
    <p>What do the authors want to understand about the tool?</p>
  </div>

  <div class="info-card card-green">
    <span class="rq-label">RQ3</span>
    <h3>Evaluation Methods</h3>
    <p>How are the tools empirically evaluated?</p>
  </div>

</div>

<style>
.card-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  grid-template-rows: repeat(2, minmax(0, 1fr));
  gap: 12px;
  height: 290px;
  margin-top: 16px;
}

.info-card {
  position: relative;
  box-sizing: border-box;
  min-height: 0;
  padding: 16px;
  border-radius: 12px;
  color: #263238;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.rq-label {
  position: absolute;
  top: 0.4rem;
  left: 0.55rem;
  font-size: 0.9rem;
  font-weight: 700;
  letter-spacing: 0.02em;
  line-height: 1;
  opacity: 0.7;
}

.info-card h3 {
  margin: 0 0 8px;
  font-size: 1.15rem;
  font-weight: 600;
  text-align: center;
}

.info-card p {
  margin: 0;
  font-size: 0.95rem;
  line-height: 1.4;
  text-align: center;
}

.card-blue   { background: #e3efff; }
.card-green  { background: #e2f4e8; }
.card-yellow { background: #fff3cd; }
.card-purple { background: #eee5ff; }
.card-pink   { background: #ffe5ec; }
.card-teal   { background: #ddf5f2; }
</style>

---
autoClicks: false
---

# Motivations for building tools <span class="rq-title rq1">(RQ1)</span>

- Provide personalized, context-aware support
- Unrestricted GenAI use can lead to overreliance
- Lack of scalable help-seeking in classrooms

---
autoClicks: false
---

# Tool features and approaches <span class="rq-title rq1">(RQ1)</span>

<div>

**Features**

</div>

- Scaffold feedback so the tool doesn’t give away answers
- Curated practice/problem sets
- Ground responses in curated learning material

**Delivery method**
- Mostly standalone web apps

---
autoClicks: false
---

# Educational Framings <span class="rq-title rq2">(RQ2)</span>

- Most frequent mentions:
    - Scaffolding
    - Cognitive Load Theory
    - Metacognition
    - Self-regulated learning
- Connection between framings and tool features still unclear

---
autoClicks: false
---

# Evaluation Goals <span class="rq-title rq3">(RQ3)</span>

- Understand student perceptions
- Understand usage patterns
- Measure student impact
    - Pre-/post-test performance
    - Affective state (self-efficacy, nervousness, etc.)

---
autoClicks: false
---

# Evaluation Methods <span class="rq-title rq3">(RQ3)</span>

- Post-surveys (and less common pre-surveys)
- Usage data analysis
- Think-alouds/other lab studies

---

# Recommendations

<div class="rec-grid">

  <div class="info-card card-teal" v-click.fade-in>
    <ph-question class="rec-icon" />
    <h3>Start with the problem, not the tool</h3>
  </div>

  <div class="info-card card-orange" v-click.fade-in>
    <ph-lego class="rec-icon" />
    <h3>Build on what the field already knows</h3>
  </div>

  <div class="info-card card-yellow" v-click.fade-in>
    <ph-magnifying-glass class="rec-icon" />
    <h3>Investigate<br>the gaps</h3>
  </div>

  <div class="info-card card-purple" v-click.fade-in>
    <ph-arrows-split class="rec-icon" />
    <h3>Consider that students have alternatives</h3>
  </div>

</div>

<style>
.rec-grid {
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));
  gap: 12px;
  height: 255px;
  margin-top: 16px;
}
.info-card {
  box-sizing: border-box;
  min-height: 0;
  padding: 56px 16px 16px;
  border-radius: 12px;
  color: #263238;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  text-align: center;
}
.info-card h3 {
  margin: 0;
  font-size: 1.05rem;
  font-weight: 600;
  line-height: 1.35;
  text-align: center;
}
.rec-icon {
  width: 2.75rem;
  height: 2.75rem;
  margin-bottom: 0.85rem;
  flex-shrink: 0;
}
.card-teal   { background: #ddf5f2; }
.card-orange { background: #ffe8d6; }
.card-yellow { background: #fff3cd; }
.card-purple { background: #eee5ff; }
.rec-grid :deep(.slidev-vclick-target) {
  transition: opacity 0.45s ease !important;
}
</style>

---
layout: two-cols-header
autoClicks: false
---

# Summary

::left::

<div class="summary-bullets">

- Custom tools are one of many instructional strategies to regulate GenAI
- Tools use <span class="hl-blue">pedagogical features</span> to support learning
- Work is informed by <br><span class="hl-pink">educational framings</span>
- <span class="hl-green">Evaluations</span> adopt many goals and methods
- Consider the problem at hand, prior research, and student alternatives when making the decision to develop a tool

</div>

::right::

<div class="qr-panel">
  <p class="qr-caption">GenAI-Powered Postsecondary Computer Science Education Tools: A Systematic Literature Review</p>
  <img class="qr-code" src="/misc/qrcode.png" alt="QR code for the paper" />
  <p class="qr-email"><a href="mailto:owen.sizemore@duke.edu">owen.sizemore@duke.edu</a></p>
  <p class="qr-email"><a href="https://duke.is/sizemore-kc26-genai">duke.is/sizemore-kc26-genai</a></p>
</div>

<style>
.summary-bullets {
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.summary-bullets ul {
  margin: 0;
}
.summary-bullets li {
  margin-bottom: 0.9rem;
}
.qr-panel {
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.qr-caption {
  margin: 0;
  padding: 0 1.5rem 1.25rem;
  text-align: center;
  font-size: inherit;
  line-height: 1.35;
}
.qr-code {
  width: 11rem;
  height: 11rem;
  object-fit: contain;
  border: 2px solid #263238;
  border-radius: 8px;
}
.qr-email {
  margin: 0.85rem 0 0;
  text-align: center;
  font-size: 1.05rem;
}
.qr-email a {
  color: inherit;
  text-decoration: underline;
}
</style>