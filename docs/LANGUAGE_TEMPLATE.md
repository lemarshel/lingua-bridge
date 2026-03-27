# How to Build a New Language Module for Lingua Bridge

This guide walks you through adding a new language to the platform.

## Prerequisites
- A frequency-ranked word list of ~4000-5000 words for the target language
- Basic understanding of the language's grammar categories (POS)
- Knowledge of any unique structural features (root systems, gender, cases, tones, etc.)

## Step-by-Step

### 1. Create the folder structure
```
lingua-bridge/[language-code]/
├── index.html
├── texts/
│   ├── index.html
│   └── texts.json
├── data/
│   ├── words.json
│   └── topics.json
└── js/
    └── [language-specific scripts]
```

### 2. Build words.json
Source a frequency word list. For each word provide:
- `id`: unique ID (w0001, w0002...)
- `word`: the word in target language script
- `romanization`: transliteration if non-Latin script (pinyin, romaji, etc.)
- `english`: English translation
- `pos`: part of speech
- `frequency_rank`: position in frequency list
- `example`: one natural example sentence with romanization and English translation
- `language_specific`: object with whatever is unique to this language

### 3. Divide into topics
- Select the top 4000 most frequent/useful words
- Create 40 topics of exactly 100 words each
- Distribute words evenly across difficulty levels (if the language has proficiency levels like HSK/JLPT/DELF)
- Keep semantically related words and word families together where possible
- Each topic should be a practical real-life theme

### 4. Build the main page (index.html)
- Copy the template from an existing language module
- Adapt filters and groupings for this language's unique features
- Ensure all 4000 words load on a single page
- Implement language-specific features (see the table in SYSTEM_DESIGN.md)

### 5. Write context texts
- Each text covers ~100 target words from one topic
- Surrounding language should be beginner-intermediate level
- Target words naturally embedded in context — not forced
- Texts should be interesting and varied (narrative, dialogue, article, diary, etc.)
- Bold/highlight all target words
- Provide full translation and romanization (toggleable)

### 6. Register the language
Add an entry to `shared/data/languages.json` with the language metadata.

### 7. Submit a PR
Follow CONTRIBUTING.md for PR guidelines.

## Quality Checklist
- [ ] 4000 words with complete data (no empty fields)
- [ ] Every word has a natural example sentence
- [ ] POS tags are correct (spot-check at least 50 random words)
- [ ] 40 topics × 100 words, no duplicates, no orphans
- [ ] Main page loads in < 3 seconds
- [ ] Search works for target language, romanization, and English
- [ ] Responsive on mobile
- [ ] Language-specific features implemented
- [ ] Registered in languages.json
