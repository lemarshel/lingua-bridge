# Project Plan — Lingua Bridge

## Goal

Build **Lingua Bridge** as the main open-source platform for multilingual language learning: a static-first website that explains the method, links all language modules, provides shared architecture, and eventually supports both web and mobile learning. Chinese is the first major implementation, while other language modules will plug into the same platform structure. :contentReference[oaicite:0]{index=0} :contentReference[oaicite:1]{index=1}

## Core Mission

Lingua Bridge is meant to be more than one language website.

Its mission is to create a **free, open-source system** that can teach many languages through the same structured method:

- high-utility vocabulary first
- fixed curriculum structure
- rich story-based acquisition
- learner-state tracking
- reusable language modules
- later expansion to mobile apps for Android and iPhone :contentReference[oaicite:2]{index=2}

## Core Method

The entire platform is built around one central idea:

> **All of a language in 40 texts.**

### Required curriculum structure

1. Select roughly **4000 of the most useful words** for a language.  
2. Divide them into **40 groups of 100 words**.  
3. Build **40 strong texts**, each centered around one target group.  
4. Keep support vocabulary controlled and beginner-friendly.  
5. Make the learner acquire words through repeated meaningful context, not isolated drills. :contentReference[oaicite:3]{index=3} :contentReference[oaicite:4]{index=4}

### Story specification

The platform method already assumes:

- each text should embed about **100 target words**
- texts should be around a full study session, not tiny fragments
- words should reappear later in a spaced pattern
- audio, display modes, and layered support are part of the intended experience
- stories should be real narratives, not dull textbook filler :contentReference[oaicite:5]{index=5}

## Platform Scope

Lingua Bridge should serve as:

- the **main landing page**
- the **methodology hub**
- the **language selector**
- the **shared architecture repo**
- the **public project face**
- the **home for platform documentation and roadmap** :contentReference[oaicite:6]{index=6} :contentReference[oaicite:7]{index=7}

## Architecture Direction

### Platform principles

Lingua Bridge is planned as a **static-first** system:

- pure HTML / CSS / JavaScript
- GitHub Pages friendly
- no mandatory backend
- no required account system
- localStorage for learner state
- shared reusable components
- language modules under a common platform shell :contentReference[oaicite:8]{index=8} :contentReference[oaicite:9]{index=9}

### Language module structure

The intended module pattern is:

```text
lingua-bridge/
├── index.html
├── README.md
├── PLAN.md
├── shared/
│   ├── js/
│   ├── css/
│   └── assets/
├── chinese/
├── arabic/
├── japanese/
├── korean/
├── italian/
├── dutch/
└── docs/

Major Add on:
## General Language-Building Method

Lingua Bridge follows a general language-building workflow that can be reused across different target languages.

### G-Step 1 — Build the Core Word Base

The first stage is to create the main word foundation for a language.

#### 1.1 Official level-based sources when available
If a language already has an official or widely accepted level structure, that structure is used as the starting point. This applies to languages such as Chinese or Japanese, where official or semi-official graded word systems already exist. In such cases, the platform uses approximately **4000–5000 words** from those level-based sources as the initial core.

#### 1.2 Custom level structure when no official list exists
If no official level list exists, a structured word base is built manually from strong, reputable sources chosen specifically for that language. In this case, the platform uses a clean multi-level split. One standard model is:

- **Level 1:** 500  
- **Level 2:** 700  
- **Level 3:** 800  
- **Level 4:** 900  
- **Level 5:** 1000  
- **Level 6:** 1100  

This produces a total of **5000 words**.

The exact level distribution may differ by language, but at this stage the goal is to create a strong, practical, approximately graded vocabulary foundation. Meanings at this point may still be partly approximate unless the source already provides official English definitions.

### G-Step 2 — Refine, Structure, and Prepare the Language System

Once the initial word base exists, the next stage is to transform it into a usable structured learning system.

#### 2.1 Grouping, filtering, search, and audio
Words are first divided approximately into useful internal structures such as phonetic groups, root families, morphemes, or similar language-specific clusters. Filters are added to the target-language words themselves, along with search tools and audio playback for pronunciation and study support.

#### 2.2 Manual quality checking in batches
The words are then reviewed carefully in batches of around **100 words at a time**. This includes:
- checking translations into **English** and **Russian** first
- correcting spelling
- adding example sentences
- translating those examples into multiple learner languages
- assigning the correct **part of speech**

For languages that already have strong official graded sources, the next step may be less important. For languages without such official grading, it becomes essential.

#### 2.3 Final level assignment
After the meanings, spelling, examples, and POS structure are cleaned up, the words are assigned to their final levels. A common 5000-word split is:

- **Level 1:** 500  
- **Level 2:** 700  
- **Level 3:** 800  
- **Level 4:** 900  
- **Level 5:** 1000  
- **Level 6:** 1100  

At this point the system should contain much more precise translations and cleaner level divisions.

#### 2.4 Divide the full word base into 40 study batches
Once the words are stable, they are divided evenly into **40 batches of 100 words** each. These batches are built using level distribution logic, so each text receives a balanced mixture from the correct difficulty ranges.

#### 2.5 Dictionary / test / flashcard readiness
At this stage the word base is already mature enough to function as:
- a strong searchable dictionary
- an Anki-style study base
- a testing system
- or another structured vocabulary tool

#### 2.6 Turn the batches into story-based learning texts
This is where the core method becomes most important.

Each 100-word batch is placed into a carefully written retelling of a famous story or another strong narrative format. The target batch words are embedded into context, while easier helper words — usually around Level 1–2 — are used to support comprehension. Stories are chosen and arranged so that easier texts come first and more challenging texts appear later.

The texts build upward. Words learned in earlier texts are reused and spread into later texts, so the learner gradually reaches a harder and denser 40th text without constantly resetting difficulty.

#### 2.7 Apply long-term memory repetition logic
A repetition formula is then applied to determine after how many days words should reappear in later texts to move them toward long-term memory. These repetitions are spread **forward into later texts**, never backward.

#### 2.8 Provide the 100-word list after each text
After a text is completed, the exact target list of **100 words** used in that text is shown clearly for review and study.

#### 2.9 Add audio and supporting study layers
At this stage the audio layer is added:
- word audio
- sentence audio
- reading support
- structural divisions and study aids linked to the text

This is the stage where the language is effectively “hacked” through **40 texts built from 40 structured story-based batches**.

##### 2.9.1 Harder-first sequencing inside texts
Within a text, harder words should preferably appear earlier, when the learner’s mind is fresher, while easier words can appear later.

##### 2.9.2 Different style from text to text
Each text should have its own style of telling so the learner does not feel like they are reading the same material again and again.

##### 2.9.3 Style preference and branching story paths
Users should be able to like or dislike the style of a text. This allows the system to detect which styles they respond to best. In the long term, that makes it possible to generate or prepare multiple story paths for the same 100-word batch.

For example:
- first pass: 1 story for each batch = 40 stories
- later passes: additional different stories for the same batches
- users choose styles they prefer
- the most liked styles receive more future versions

This means the system can eventually grow from a single 40-story path into many parallel paths while still preserving the same batch-based vocabulary structure.

### G-Step 3 — Expansion

After the core system is stable, the next stage includes broader improvements such as:

- improving design
- adding alphabet learning through a custom method
- building a dedicated app
- expanding interface languages
- improving personalization and style selection
- extending the same method across more languages