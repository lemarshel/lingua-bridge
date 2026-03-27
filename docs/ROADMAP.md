# Lingua Bridge — Public Roadmap

## Current Focus: Chinese (Mandarin)

### Completed
- 5361 words processed (morphemes, POS, examples, pinyin, Russian translations)
- 40 topics × 100 words, HSK-balanced distribution
- Learner event tracker (7/7 audit pass)
- Text number filtering on vocabulary page (texts 1–40)
- 8 data quality audits passed
- Full morpheme analysis (1806 hubs, 11 semantic categories)

### In Progress
- Production-quality vocabulary page
- Interactive morpheme mindmap
- 40 context texts (manually curated popular story retellings, 1000-1200 words each, interlinear word-by-word display, built-in Fibonacci-interval spaced repetition cameos, three audio modes + tap-any-word + tap-any-sentence with speed control, 40-50 minute session design)

### Planned
- Stroke order practice (Hanzi Writer integration)
- Audio pronunciation for all words
- Landing page with project story

## The 40 Texts Pipeline (per language)

Creating the 40 texts for each language follows this pipeline:

1. **Word selection & distribution** — divide 4000 most frequent words into 40 groups of 100, balanced by difficulty
2. **Cameo schedule computation** — calculate the Fibonacci-interval reappearance schedule for all 4000 words across all 40 texts
3. **Story selection** — choose 40 popular stories/narratives that naturally accommodate each group's vocabulary domains
4. **Writing** — write/adapt each story using only beginner-level scaffolding + 100 target words + required cameo words
5. **Validation** — automated script checks: all 100 target words present, all required cameo words present, scaffolding words are beginner-level only, word count in range 1000-1200
6. **Interlinear formatting** — word segmentation, alignment, romanization, translation mapping
7. **Audio generation** — TTS for all words and full text, speed variants
8. **Native speaker review** — verify naturalness, correct errors, improve flow (community contribution)
9. **Publication** — deploy to the language's texts page

Estimated effort per language: 40-80 hours for steps 1-7 (can be parallelized). Step 8 is ongoing community effort.

## Next Language: Arabic

### Planned
- Top 4000 frequency words with root letter analysis
- Quranic vs modern classification
- 3-category POS (noun/verb/particle)
- RTL layout
- Context texts

## Platform Features (After Chinese is complete)
- Shared component library
- Language contribution template
- Community suggestion system
- PWA/offline support
- User customization

## Future Languages (in rough priority order)
Arabic → German → Japanese → Spanish → French → Korean → Russian → Portuguese → Italian → Turkish → Hindi → Dutch → Swedish → Polish → Thai → Vietnamese → Indonesian → Greek → Czech → Romanian → Hungarian → Finnish → Hebrew → Persian → Swahili → Ukrainian → Danish → Norwegian → Tagalog

## Beyond Languages (Long-term Vision)
- Physics in 100 Lessons
- Psychology in 80 Lessons
- Biology in 90 Lessons
- (Professor-verified, AI-simplified, PhD-depth, free, open-source)
