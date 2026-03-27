# Lingua Bridge

**Lingua Bridge** is a free, open-source, multilingual language-learning platform built to make serious language acquisition simpler, deeper, and more scalable.

The project starts from one core belief:

> **You can hack any language with 40 well-designed texts.**

Instead of relying on shallow gamification, disconnected flashcards, or bloated textbooks, Lingua Bridge is built around a structured system:
- a carefully chosen core vocabulary
- powerful interactive language tools
- story-based acquisition
- learner progress tracking
- reusable architecture for many languages

Chinese is the first major implementation. Other languages will follow through the same platform structure.

---

## Mission

Lingua Bridge exists to build a **unified open-source platform for learning many languages** through the same strong method.

The long-term aim is:

- make high-quality language learning free
- make the system reusable across many languages
- preserve deep, structured learning instead of shallow engagement tricks
- support both desktop and future mobile learning
- eventually expand beyond languages into other open educational systems

This is meant to be a real platform, not a one-language side project.

---

## Core Method — “All of a Language in 40 Texts”

The foundation of Lingua Bridge is the **40-text method**.

### The basic idea

- Start with roughly **4000 of the most useful words**
- Divide them into **40 groups of 100 words**
- Build **40 strong texts**, each centered around one 100-word cluster
- Use only controlled beginner-level helper language to make the text understandable
- Let the learner acquire vocabulary through repeated, meaningful context

### Why this works

Most everyday language use is concentrated in a relatively small high-frequency core. Instead of making learners study that core through isolated cards, Lingua Bridge teaches it through readable, memorable texts.

Each text is designed to function as a complete study unit:
1. first supported reading
2. second pass with less support
3. audio-based reinforcement
4. repeated reappearance of words over time

This combines:
- contextual acquisition
- structured repetition
- readability
- long-form immersion
- active review without destroying flow

---

## Study Experience

A full Lingua Bridge language module is designed to include:

- a **vocabulary page**
- a **story/text reader**
- a **morpheme / word-family explorer**
- a **learner tracker**
- a **dashboard / study hub**
- export and personalization tools
- language-specific UI rules where needed

The goal is not one study mode. The goal is a connected learning environment.

---

## Platform Architecture

Lingua Bridge is designed as a **static-first platform**.

### Current architectural principles

- pure HTML / CSS / JavaScript
- GitHub Pages friendly
- no build step required for the basic version
- no mandatory account system
- localStorage-based learner state
- shared reusable components
- separate language modules under one platform shell

### Intended structure

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
│   ├── index.html
│   ├── vocabulary.html
│   ├── mindmap.html
│   ├── stories.html
│   ├── data/
│   ├── js/
│   ├── css/
│   └── assets/
├── arabic/
├── japanese/
├── korean/
├── italian/
├── dutch/
└── docs/