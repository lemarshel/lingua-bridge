# Lingua Bridge — System Design & Vision

## The Vision

Lingua Bridge is an open-source platform that makes it possible to "hack" any language by learning its 4000 most frequent words through intelligently structured vocabulary pages and context texts. Free forever, community-driven, built one language at a time.

Each language gets a single, beautifully structured page with all ~4000 words — searchable, filterable, with language-specific organization (Chinese: morphemes and phonetic families; Arabic: root letters and Quranic filter; German: gender markers and compound decomposition). Alongside this, ~40 context texts each cover ~100 target words embedded in beginner-intermediate level surrounding language, so a learner can read and break down each text a few times and the words lock in naturally. The texts aren't 100 words long — they're as long as needed to naturally incorporate all target words in digestible context.

Most languages besides English lack quality, structured, free learning resources. Lingua Bridge fixes that.

The long-term vision extends beyond languages: Lingua Bridge is the first project in a broader mission to make world-class education free and open-source. Future projects include university-level course series (Physics in 100 Lessons, Psychology in 80 Lessons, Biology in 90 Lessons, etc.) built with professor-verified structures, AI-simplified explanations, PhD-level depth eased to understand, and extensive practice tasks — all free, all open-source, all in a single place.

### The Story

Founder: **Sultan Kulbassov** (GitHub: lemarshel, Telegram: @hinataace, Email: lemarshel@gmail.com)

I started learning Chinese on my own about three years ago, with big breaks in between. When I came back to it seriously, I realized something: the way most people learn languages is broken. Duolingo gamifies but stays shallow. Textbooks are scattered and boring. Anki is powerful but soulless. And none of them exploit the internal logic of the language itself.

Chinese taught me that languages are systems, not word lists. Every character is built from components. Every compound word is a logical combination of simpler morphemes. 电 (electricity) + 话 (speech) = 电话 (telephone). Once you see the system, you stop memorizing and start predicting. I realized that ~4000 carefully chosen, intelligently structured words cover roughly 95% of daily language use — and that the right structure makes learning those 4000 words dramatically faster.

Then I looked at Arabic and saw the same principle: three root letters generate dozens of related words. German compounds decompose into learnable pieces. Every language has its own internal logic that can be exploited for faster acquisition — but nobody was building tools that actually used these patterns.

So I built it myself. First for Chinese — decomposing every word into morphemes, grouping by phonetic components, clustering into balanced topics, writing context texts that naturally embed target vocabulary. The result was a system where reading 40 texts thoughtfully a few times genuinely locks in 4000 words. Then I decided to make it free and open-source for every language, because everyone deserves access to tools this good.

This took — and continues to take — enormous amounts of time, money, and energy. If this project helps you, please consider supporting it so more languages and educational projects can be built.

### Support the Project

This project is free and will remain free forever. If it helped you, consider supporting future development:

- GitHub: https://github.com/lemarshel/lingua-bridge (star, contribute, share)
- Contact: Sultan Kulbassov — Telegram: @hinataace · Email: lemarshel@gmail.com
- Donate: [placeholder for donation link — Ko-fi, GitHub Sponsors, or Buy Me a Coffee]

Every donation directly funds new languages, better features, and future open-source education projects.

---

## Architecture Overview

### Hosting Strategy

**Phase 1 (Now):** GitHub Pages — free, fast, global CDN.
- Each language = a set of static HTML/CSS/JS files
- No server, no database, no auth needed for core functionality
- User progress and customizations saved to browser localStorage
- Works offline after first load (PWA-ready)
- The immediate goal is to "hack" every language with the best possible free static tool

**Phase 2 (When funded/supported):** Add optional backend for:
- User accounts and cloud sync of progress
- Community contribution management
- Cross-device progress sync
- Potential: Supabase free tier or similar

**Phase 3 (Growth):** If funders or community support make it viable:
- Dedicated hosting for better performance
- Audio file CDN
- Real-time collaboration features
- ML personalization layer

### Core Principle: Static-First

The platform must work as pure static files. No user should ever need an account to learn. The backend is a future enhancement, not a requirement. This means:
- All word data embedded in the HTML/JS files
- All interactivity runs client-side
- localStorage for progress tracking
- Export/import JSON for backup and migration

---

## Project Structure

```
lingua-bridge/
├── index.html                    ← Landing page: vision, language selector, story, donate
├── STATUS.md                     ← Current progress and where we stopped
├── CONTRIBUTING.md               ← How to contribute (for devs and non-devs)
│
├── docs/
│   ├── SYSTEM_DESIGN.md          ← This document
│   ├── LANGUAGE_TEMPLATE.md      ← Guide: how to build a new language module
│   ├── ROADMAP.md                ← Public roadmap with milestones
│   └── system_discovery_report.md
│
├── shared/                       ← Shared across all languages
│   ├── css/
│   │   └── lingua-bridge.css     ← Global styles, responsive, dark/light mode
│   ├── js/
│   │   ├── tracker.js            ← Learning event tracker (language-agnostic)
│   │   ├── search.js             ← Universal search/filter engine
│   │   ├── audio.js              ← Audio playback controller
│   │   ├── customize.js          ← User page customization (layout, preferences)
│   │   ├── suggest.js            ← In-app suggestion/feedback button
│   │   └── progress.js           ← Progress tracking, streaks, export/import
│   ├── components/
│   │   ├── word-card.js          ← Reusable word detail popup/tooltip
│   │   ├── nav.js                ← Shared navigation header
│   │   ├── footer.js             ← Shared footer with story + donate
│   │   └── feedback-modal.js     ← Suggestion submission form
│   └── data/
│       └── languages.json        ← Registry of all available languages + metadata
│
├── chinese/                      ← Chinese language module
│   ├── index.html                ← Main vocabulary page (all 4000+ words, single page)
│   ├── texts/                    ← Context texts (each covers ~100 target words)
│   │   ├── index.html            ← Text browser/reader
│   │   └── texts.json            ← Text data
│   ├── mindmap/                  ← Interactive morpheme mindmap
│   │   └── index.html
│   ├── data/
│   │   ├── words.json            ← All word data
│   │   ├── topics.json           ← Topic clusters (40 × 100 words)
│   │   └── morphemes.json        ← Morpheme hub data
│   └── js/
│       ├── hanzi-writer.js       ← Stroke order practice (Chinese-specific)
│       ├── pinyin-filter.js      ← Pinyin search/filter
│       └── morpheme-groups.js    ← Phonetic component grouping
│
├── arabic/                       ← Arabic language module (future)
│   ├── index.html
│   ├── texts/
│   ├── data/
│   └── js/
│       ├── root-system.js        ← 3-letter root analysis and grouping
│       ├── quran-filter.js       ← Quranic vs modern vocabulary filter
│       └── rtl-layout.js         ← Right-to-left layout handling
│
├── german/                       ← German language module (future)
│   ├── index.html
│   ├── texts/
│   ├── data/
│   └── js/
│       ├── gender-marker.js      ← Der/Die/Das color coding
│       ├── compound-splitter.js  ← Compound word decomposition
│       └── case-system.js        ← Case marking visualization
│
└── [language]/                   ← Template for any new language
    ├── index.html
    ├── texts/
    ├── data/
    └── js/
```

---

## Language Module Specification

Every language module follows the same skeleton but with unique internals.

### Universal Requirements (every language must have):

1. **~4000 most frequent words** with:
   - Word in target language
   - Romanization/transliteration (if non-Latin script)
   - English translation
   - One natural example sentence with translation
   - Audio pronunciation (TTS or recorded — can be added progressively)
   - Part of speech tag
   - Frequency rank

2. **~40 context texts** (number may grow):
   - 40 texts × 100 target words each (4000 total)
   - 1000–1200 words per text (target 1000), beginner-level scaffolding with target words embedded
   - Target words highlighted/bolded in the text
   - Full translation available (toggleable)
   - Romanization available (toggleable, for non-Latin scripts)
   - A learner reads and breaks down each text a few times and the words lock in

3. **Main vocabulary page (single page, all words loaded):**
   - All ~4000 words displayed in a clean, searchable, filterable list
   - Language-specific grouping and filtering (see table below)
   - Search by target language, romanization, and English — must be instant (<50ms)
   - Hover/click for word details (example sentence, audio, language-specific features)
   - Progress tracking via localStorage (checkboxes: unseen → familiar → learned)
   - Works on mobile and desktop
   - Loads all words on single page — no pagination

4. **Responsive design**: Must work perfectly on phone, tablet, desktop
5. **Fast loading**: Target < 3 seconds on 3G for initial load
6. **Offline-capable**: Works after first load without internet (PWA-ready)

### Language-Specific Features:

| Language | Script | Direction | POS Categories | Unique Features |
|----------|--------|-----------|---------------|----------------|
| Chinese (Mandarin) | Hanzi | LTR | noun, verb, adjective, adverb, conjunction, preposition, particle, measure word, auxiliary verb, pronoun, numeral, interjection | Stroke order practice (Hanzi Writer), pinyin filter, morpheme/phonetic component grouping, tone color coding, radical index, interactive morpheme mindmap |
| Arabic | Arabic | RTL | noun, verb, particle (3 divisions only) | 3-letter root system grouping, Quranic vs modern filter, verb form (وزن) patterns, harakat toggle |
| Japanese | Kanji + Kana | LTR | noun, verb, i-adjective, na-adjective, adverb, particle, counter | Kanji stroke order, hiragana/katakana toggle, JLPT level filter, on'yomi/kun'yomi readings, furigana toggle |
| Korean | Hangul + Hanja | LTR | noun, verb, adjective, adverb, particle, counter | Hangul component breakdown, TOPIK level filter, honorific markers, Sino-Korean vs native grouping |
| German | Latin | LTR | noun (with gender), verb, adjective, adverb, conjunction, preposition | Gender color coding (der/die/das), compound decomposition, case visualization, plural patterns, separable prefix markers |
| French | Latin | LTR | noun (with gender), verb, adjective, adverb, conjunction, preposition | Gender marking, verb conjugation group, liaison indicators, formal/informal register |
| Spanish | Latin | LTR | noun (with gender), verb, adjective, adverb, conjunction, preposition | Gender marking, verb group (ar/er/ir), subjunctive flag, regional variants (Spain vs LatAm) |
| Russian | Cyrillic | LTR | noun, verb, adjective, adverb, conjunction, preposition, particle | Case declension patterns, aspect pairs (perfective/imperfective), stress marking, gender |
| Hindi | Devanagari | LTR | noun (with gender), verb, adjective, adverb, postposition | Gender system, postposition grouping, formal/informal register, Sanskrit vs Perso-Arabic origin |
| Portuguese | Latin | LTR | noun (with gender), verb, adjective, adverb | Gender marking, verb conjugation, Brazilian vs European variants |
| Italian | Latin | LTR | noun (with gender), verb, adjective, adverb | Gender marking, verb conjugation group |
| Turkish | Latin | LTR | noun, verb, adjective, adverb, postposition | Vowel harmony visualization, agglutination breakdown, suffix chain decomposition |
| Dutch | Latin | LTR | noun (with gender de/het), verb, adjective, adverb | Gender marking, separable verbs, compound decomposition |
| Swedish | Latin | LTR | noun (en/ett gender), verb, adjective, adverb | Gender marking, compound decomposition |
| Polish | Latin | LTR | noun, verb, adjective, adverb, conjunction, preposition | Case system (7 cases), aspect pairs, gender (3 genders) |
| Thai | Thai script | LTR | noun, verb, adjective, classifier | Tone marking, classifier grouping, no spaces helper |
| Vietnamese | Latin + diacritics | LTR | noun, verb, adjective, classifier | Tone marking, Sino-Vietnamese vs native grouping, classifier system |
| Indonesian/Malay | Latin | LTR | noun, verb, adjective, adverb | Affix system (me-, ber-, di-, ke-an), root word grouping |
| Greek | Greek | LTR | noun (with gender), verb, adjective, adverb | Gender and case marking, verb aspect |
| Czech | Latin | LTR | noun, verb, adjective, adverb | Case system (7 cases), aspect pairs, gender |
| Romanian | Latin | LTR | noun (with gender), verb, adjective, adverb | Gender marking, definite article suffix |
| Hungarian | Latin | LTR | noun, verb, adjective, adverb | Vowel harmony, agglutination breakdown, case suffixes |
| Finnish | Latin | LTR | noun, verb, adjective, adverb | 15 cases, vowel harmony, consonant gradation |
| Hebrew | Hebrew | RTL | noun (with gender), verb, adjective | Root system (like Arabic), verb binyanim patterns |
| Persian (Farsi) | Arabic | RTL | noun, verb, adjective, adverb, preposition | Ezafe construction, compound verbs, Arabic loanword roots |
| Swahili | Latin | LTR | noun (with class), verb, adjective, adverb | Noun class system (18 classes), verb morphology breakdown, prefix/suffix chain |
| Ukrainian | Cyrillic | LTR | noun, verb, adjective, adverb | Case system, aspect pairs, gender, comparison with Russian toggle |
| Danish | Latin | LTR | noun (en/et gender), verb, adjective, adverb | Gender marking, compound decomposition |
| Norwegian | Latin | LTR | noun (en/ei/et gender), verb, adjective, adverb | Gender marking, Bokmål vs Nynorsk toggle |
| Tagalog | Latin | LTR | noun, verb, adjective, adverb | Focus/voice system, affix grouping (mag-, -um-, -in) |

---

## The 40 Texts System — "All of [Language] in 40 Texts"

### Theoretical Foundation

This system is a practical implementation of Stephen Krashen's Comprehensible Input Hypothesis (i+1): optimal language acquisition occurs when the learner is exposed to input that is mostly understood, with a small amount of new material that becomes understandable through context. Each text is deliberately constructed so that ~90% of the language is already known (beginner-level scaffolding words), and the ~100 target words are the "+1" — new but guessable from the surrounding context. The learner never feels lost, and the new words click into place naturally through meaningful exposure rather than rote memorization.

### Core Concept

4000 most frequent words ÷ 40 texts = 100 target words per text. Anyone who thoughtfully breaks down and internalizes these 40 texts essentially knows the language at a conversational level. Each text is designed as a 40-50 minute study session — one text per day, 40 days, language hacked.

### Text Specifications

**Length:** 1000-1200 words per text in the target language (not counting interlinear translations). Minimum 800, maximum 1200. The target is 1000.

**Scaffolding ratio:** 10:1 — approximately 10 scaffolding words for every 1 target word. This gives each new word enough breathing room to be properly contextualized within natural, flowing prose. The story never feels rushed or forced.

**Session design:** Each text targets a 40-50 minute study session, naturally structured as:
- First read-through with full interlinear support (target language + romanization + translation visible): ~20 minutes
- Second read-through with translations hidden (testing recall, only target language + romanization): ~15 minutes
- Audio shadowing practice on difficult sentences and passages: ~10-15 minutes
- A learner who wants to split the session can take a break after the first read-through and return later for the review passes.

**Completion timeline:**
- 1 text per day = 40 days to complete all texts
- 1 text every 2-3 days (deeper study) = 80-120 days (~3-4 months)
- Either pace is sufficient for conversational fluency in the target language

### Design Principles

1. **100 target words per text, carefully selected and evenly distributed from the 4000 most frequent words.** Distribution is layered by difficulty level — each text contains a balanced mix of intermediate and advanced target words, never all easy or all hard.

2. **The 40 texts are retellings or adaptations of popular, well-known stories** — folk tales, classic literature, famous narratives, historical events, modern stories, and culturally significant tales from around the world and from the target language's own culture. Popular stories have built-in emotional hooks, cultural resonance, and narrative tension that keeps learners engaged and motivated to finish.

   The story selection spans diverse settings and registers to ensure target vocabulary from every domain has a natural home:
   - Action/adventure stories (action verbs, physical world vocabulary)
   - Emotional/relationship stories (feelings, personality, social vocabulary)
   - Professional/business narratives (work, money, formal vocabulary)
   - Nature/travel stories (environment, geography, descriptive vocabulary)
   - Daily life stories (food, home, routine vocabulary)
   - Mystery/detective stories (logical reasoning, investigative vocabulary)
   - Historical/cultural stories (society, government, cultural vocabulary)
   - Philosophy/wisdom tales (abstract concepts, thinking vocabulary)
   - Comedy/humor (informal register, colloquial expressions)
   - Family/childhood stories (relationships, emotions, growing up)

3. **Context is built exclusively with beginner-level words** (HSK 1-2 for Chinese, A1-A2 for European languages) as the surrounding scaffolding. Target words are embedded so their meaning is guessable from context. The 10:1 ratio ensures the story flows naturally — the narrative comes first, the vocabulary serves the story.

4. **Helper words from the beginner level rotate across texts.** No text overuses the same basic connector words or sentence patterns. This gives the learner varied exposure to foundational grammar and vocabulary even in the scaffolding language. Helper word rotation is carefully designed so the learner sees common words used in many different contexts across the 40 texts.

5. **Built-in Spaced Repetition Across Texts (Forward-Only):**

   Each target word has one "home" text where it is formally introduced and highlighted. That word then reappears as an unhighlighted cameo in later texts at expanding intervals, following a Fibonacci-inspired spacing formula:

   **A word introduced in Text N reappears as a cameo in texts: N+1, N+3, N+7, N+15, N+30** (capped at Text 40).

   Examples:
   - Word from Text 1 → cameos in texts 2, 4, 8, 16, 31
   - Word from Text 5 → cameos in texts 6, 8, 12, 20, 35
   - Word from Text 20 → cameos in texts 21, 23, 27, 35
   - Word from Text 35 → cameos in texts 36, 38

   Rules:
   - **Forward-only**: cameos never appear in earlier texts than the home text. The learner never needs to go back.
   - Words from later texts naturally get fewer cameo repetitions (fewer texts remaining) — this is acceptable because by text 30+ the learner's retention and pattern recognition are significantly stronger.
   - Cameo appearances are NOT highlighted — they blend into the text naturally. The learner encounters them as "oh I know this word" moments, reinforcing retention unconsciously.
   - Each word is calculated to appear approximately 4-6 total times across the 40 texts (including the home text).
   - This creates an analog spaced repetition system baked into the content itself — no app, no algorithm, no flashcards needed. The spacing is built into the stories.

6. **The quality bar is non-negotiable.** These are not textbook exercises or auto-generated filler. Every text must be a genuinely enjoyable story that someone would want to read even if they weren't studying the language.

### Interlinear Display Format

Every text is displayed with word-by-word translations directly underneath, so the eye never needs to search for a meaning:

**For Chinese:**
```
我     昨天      去了     一家     新     开的      餐厅
wǒ     zuótiān   qùle    yījiā    xīn    kāide     cāntīng
I      yesterday went to  a       new    opened    restaurant
```

Rules:
- Multi-character words are grouped as single units (电话 stays together as one column, never split into 电 and 话)
- Pinyin sits directly under the characters
- English/Russian translation sits under the pinyin
- Words separated by 2+ spaces for visual clarity
- Tone colors applied to pinyin matching the hsk-base vocabulary page color scheme
- Target words (the 100 being taught in this text) are visually distinguished — bold, highlighted background, or distinct color
- Scaffolding words (HSK 1-2 helper words) are displayed normally, not highlighted
- Cameo words from previous texts are not highlighted — they appear as regular text

**For other languages (e.g., German):**
```
Ich     bin      gestern     in      ein      neues      Restaurant     gegangen
I       am       yesterday   in      a        new        restaurant     gone (went)
```

Same principles: word on top, translation directly below, target words highlighted, 2+ spaces between words. For RTL languages (Arabic, Hebrew, Persian): interlinear format reads right-to-left with translations below in the user's chosen interface language.

### Audio System

**Three playback modes for the full text:**
1. **Full speed** — native speaker reading at natural pace
2. **Slow speed** — same reading with deliberate pauses between sentences
3. **Sentence-by-sentence** — tap/click to advance to the next sentence. Ideal for shadowing practice (speaking along with the audio to internalize pronunciation, rhythm, and intonation).

**Interactive audio at word and sentence level:**
4. **Tap any individual word** → hear that word spoken in isolation, clearly and at comfortable speed. Works on any word in the text — both target words and scaffolding words.
5. **Tap any sentence** → hear the full sentence spoken, with a speed control slider (0.5x, 0.75x, 1x, 1.25x) so the learner can find their comfortable pace for shadowing and comprehension.
6. Speed preference saved to localStorage, persists across texts and sessions.

Audio sources: TTS-generated initially for all words and sentences. Native speaker recordings added progressively when available through community contributions. Per-word audio is shared with the vocabulary page (same pronunciation files).

### Display Modes (toggleable by user)

1. **Full interlinear** (default for first read) — target language + romanization + translation all visible
2. **Target + romanization only** — translations hidden. For second read-through to test meaning recall.
3. **Target language only** — romanization and translations both hidden. For advanced reading fluency practice.
4. **Translation only** — target language hidden. Challenge: can you reconstruct the original from the translation?

Each layer toggles independently via buttons. For Chinese: separate toggles for pinyin and translation. Preferences saved to localStorage.

### Vocabulary Checklist Per Text

Each text includes a word checklist at the bottom:
- All 100 target words listed with three-state checkboxes: unseen → familiar → learned
- Progress bar: X/100 words mastered for this text
- Global progress bar: X/4000 words mastered across all 40 texts
- All progress saved to localStorage
- Words in the checklist are tappable to hear pronunciation
- Checklist sortable: by order of appearance in text, alphabetical, or by mastery state

### The Methodology — Why This Works

Traditional language learning fails because it treats vocabulary as isolated items to be memorized. Flashcards, word lists, and textbook vocabulary sections all share the same flaw: words learned in isolation don't stick, and even when they do, learners can't use them naturally in context.

The 40 Texts system works because it exploits how the brain actually acquires language:

1. **Context over isolation.** Every word is encountered inside a meaningful story, surrounded by comprehensible language. The brain doesn't memorize a definition — it absorbs a usage pattern. When you later need the word, you don't recall a flashcard; you recall a scene from a story.

2. **Emotion drives retention.** Popular stories create emotional engagement — suspense, humor, surprise, empathy. Emotional arousal significantly enhances memory formation. A word learned during an exciting plot twist sticks better than the same word on a flashcard.

3. **Comprehensible input (Krashen's i+1).** The scaffolding ratio ensures the learner is always operating in the optimal acquisition zone: understanding enough to follow the story, encountering just enough new material to grow. This is the most efficient zone for language acquisition — not too easy (boring, no growth), not too hard (frustrating, no comprehension).

4. **Built-in spaced repetition.** The Fibonacci-interval cameo system means every word reappears at mathematically optimal intervals across the 40 texts. The learner doesn't need a separate review system — the review is woven into the stories themselves.

5. **Multi-modal reinforcement.** Each word is encountered through reading (visual), listening (auditory), and shadowing (kinesthetic/motor). The interlinear format adds spatial association. Four channels of encoding for every single word.

6. **Progressive difficulty without overwhelm.** The 40-text sequence gradually shifts the balance: early texts have more scaffolding and simpler target words; later texts use previously learned words as scaffolding for harder new words. The learner's foundation grows with each text.

7. **Completion psychology.** 40 texts is a finite, achievable goal. Unlike open-ended study plans ("keep studying until you're fluent"), the learner can see the finish line from day one. Each completed text is tangible progress — 2.5% closer to "done." This dramatically reduces dropout rates.

The result: 40 stories, 40-50 minutes each, ~40 days. At the end, the learner has encountered the 4000 most frequent words in the language, each in rich context, each reinforced through spaced repetition, each anchored to memorable narratives. That's not a study plan — that's a language acquisition system.

---

## Main Landing Page (index.html)

### Layout:

**Header:** "Lingua Bridge" logo/title + language count + GitHub stars badge

**Hero section:**
- Headline: "Hack Any Language. 4000 Words. Free Forever."
- Subtitle: "Open-source language learning tools built for real fluency, not gamification."
- CTA: Language grid below

**Language grid:**
- Card per available language: flag + language name + word count + text count + status badge (Complete / In Progress / Coming Soon)
- Clicking card → that language's main page
- Sorted: Complete first, then In Progress, then Coming Soon

**The Story section:**
- The founder story (from above)
- What makes this different
- The broader vision (free education)

**How It Works section:**
- Step 1: Pick a language
- Step 2: Go through the 4000 most frequent words (structured by the language's internal logic)
- Step 3: Read the context texts (every target word in natural, digestible context)
- Step 4: Break down each text a few times — words lock in naturally
- Step 5: You've hacked the language

**Support section:**
- Why this is free
- How donations help
- Donation link + GitHub link + Contact: lemarshel@gmail.com

**Community section:**
- How to contribute
- "Help us add your language" CTA

**Footer:**
- GitHub link
- "Built with love and thousands of hours of work"

### Technical requirements:
- Pure HTML/CSS/JS, no framework
- Loads < 1 second
- Responsive (mobile-first)
- Reads from shared/data/languages.json for language grid
- SEO optimized: meta tags, Open Graph for social sharing

---

## Per-Language Main Page (e.g., chinese/index.html)

### Layout:

**Top navigation:**
- Back to Lingua Bridge home
- Language name + flag
- Search bar (always visible)
- Filter toggles (POS, level, text/topic number 1–40, language-specific)
- Progress summary (X learned / X total)
- Settings gear (customize layout, dark/light mode)
- "Suggest improvement" button

**Vision banner (collapsible, shown on first visit):**
- Brief Lingua Bridge story
- "Support this project" + donation link
- Dismissable, remembered in localStorage

**Word list (main content):**
- All ~4000 words loaded and displayed
- Grouped by language-specific logic
- Each word row: word, romanization, English, POS tag
- Click/hover expands: example sentence, audio, language-specific features
- Three-state checkbox: unchecked → familiar → learned

**Sidebar/bottom panel:**
- Quick stats: words learned, streak, session time
- Topic shortcuts
- Links to texts and mindmap (if available)
- Export/import progress

**Footer:**
- Short Lingua Bridge story
- Support/donate link
- GitHub + contact

### Technical requirements:
- Single HTML file with data embedded or loaded async from JSON
- Must handle 4000+ words without lag
- Virtual scrolling or smart rendering for mobile performance
- Instant search (<50ms) via pre-built index
- localStorage for all user state
- Service worker for offline capability

---

## User Customization System

**What users CAN customize (saved to localStorage):**
- Dark/light mode
- Font size for target language
- Which columns to show/hide
- Default filter settings
- Sort order
- Whether to show romanization by default
- Layout (compact vs spacious)

**What users CANNOT customize:**
- Word data, filter functionality, underlying structure
- To change functionality → suggestion button or GitHub PR

**Mechanics:**
- All preferences in localStorage
- "Reset to defaults" button
- "Export/import settings" for sharing configs

---

## Community Contribution System

### For non-technical users:
- Floating "Suggest" button on every page
- Modal: category dropdown (Bug / Word correction / Missing word / Feature idea / New language / Other), text area, optional email
- Submits to GitHub Issues API or Formspree
- No account needed

### For developers:
- CONTRIBUTING.md with clear instructions
- LANGUAGE_TEMPLATE.md for adding new languages
- GitHub issue templates
- PR review process (lemarshel reviews everything)

---

## Performance Budget

| Metric | Target |
|--------|--------|
| First paint | < 1s |
| Full word list interactive | < 3s |
| Search response | < 50ms |
| Total page weight | < 2MB |
| Word data JSON | < 500KB gzipped |
| Offline capable | Yes |
| Mobile | Full feature parity |

---

## Data Schemas

### words.json (per language)
```json
{
  "language": "chinese",
  "version": "1.0.0",
  "total_words": 4000,
  "words": [
    {
      "id": "w0001",
      "word": "电话",
      "romanization": "diànhuà",
      "english": "telephone",
      "pos": "noun",
      "frequency_rank": 245,
      "example": {
        "target": "我给你打电话。",
        "romanization": "Wǒ gěi nǐ dǎ diànhuà.",
        "english": "I'll give you a call."
      },
      "audio_url": "audio/w0001.mp3",
      "language_specific": {}
    }
  ]
}
```

The `language_specific` field holds whatever is unique to that language:
- Chinese: `morphemes`, `morpheme_meanings`, `radical`, `hsk_level`, `tone_pattern`, `phonetic_family`
- Arabic: `root_letters`, `verb_form`, `is_quranic`
- German: `gender`, `plural`, `compound_parts`, `separable_prefix`
- etc.

### topics.json (per language)
```json
{
  "language": "chinese",
  "total_topics": 40,
  "words_per_topic": 100,
  "topics": [
    {
      "id": "t01",
      "name": "Daily Routine",
      "name_target": "日常生活",
      "word_ids": ["w0001", "w0023"],
      "text_available": false
    }
  ]
}
```

### languages.json (shared registry)
```json
{
  "languages": [
    {
      "code": "zh",
      "name": "Chinese (Mandarin)",
      "native_name": "中文",
      "flag": "🇨🇳",
      "word_count": 4000,
      "text_count": 0,
      "status": "in_progress",
      "features": ["stroke_order", "morpheme_mindmap", "pinyin_filter", "tone_colors"],
      "script": "hanzi",
      "direction": "ltr",
      "contributors": ["lemarshel"]
    }
  ]
}
```

---

## Roadmap

### Phase A — Chinese Module (Current)
- [x] 5361 words with morphemes, POS, examples, pinyin, Russian
- [x] 40 topics × 100 words, HSK-balanced
- [x] Learner tracker with event logging (7/7 audit pass)
- [ ] Main vocabulary page (production quality, single page, all features)
- [ ] Stroke order practice integration
- [ ] Context texts (handpicked, not auto-generated)
- [ ] Interactive morpheme mindmap
- [ ] Audio pronunciation
- [ ] Landing page with story + donation

### Phase B — Arabic Module
- [ ] Source top 4000 frequency words
- [ ] 3-letter root analysis and grouping
- [ ] Quranic vs modern classification
- [ ] Noun/verb/particle POS tagging (3 categories only)
- [ ] Context texts
- [ ] RTL layout and Arabic typography
- [ ] Audio pronunciation

### Phase C — Platform Infrastructure
- [ ] Shared component library
- [ ] LANGUAGE_TEMPLATE.md
- [ ] Suggestion/feedback system
- [ ] User customization system
- [ ] PWA/offline support
- [ ] SEO optimization

### Phase D — Expand Languages
- [ ] German, Japanese, Korean, Spanish, French, Russian
- [ ] Community contributors for additional languages
- [ ] Donation system live

### Phase E — Beyond Languages
- [ ] Physics in 100 Lessons
- [ ] Psychology in 80 Lessons
- [ ] Biology in 90 Lessons
- [ ] Professor-verified, AI-simplified, PhD-level depth, free, open-source

---

## Technical Decisions

| Decision | Choice | Why |
|----------|--------|-----|
| Framework | None (vanilla HTML/JS) | Zero build step, GitHub Pages, fastest load, anyone can edit |
| CSS | Shared stylesheet + per-language overrides | Consistent, maintainable |
| Data | JSON embedded or async-loaded | No database, works offline |
| User state | localStorage | No auth needed, instant, private |
| Search | Pre-built inverted index in JS | Instant across 4000 words |
| Audio | MP3, lazy-loaded | Don't block page load |
| Rendering | Virtual scrolling | Smooth on mobile with 4000+ items |
| Hosting | GitHub Pages | Free, fast CDN, git-based deploy |
| Contributions | GitHub Issues + PRs + in-app suggestion | Low barrier + structured |
