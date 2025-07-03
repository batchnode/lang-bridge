# Lang Bridge 
### Dataset building framework for low resource languages.

Lang Bridge is a **framework and dataset-building method** for developing culturally accurate, linguistic tools , datasets etc for low-resource languages.

The core idea is simple but powerful:
- Words are mapped to unique internal values (vals).
- Phrases are mapped as sequences of those vals.
- This val-based system connects words and phrases into a scalable, structured dataset.

The Python script provided is a demonstration.  
The real value is the **data design and system structure**—a practical method for building efficient, culturally aligned datasets.

Originally developed for the Hmar language, Lang Bridge can be adapted for any language or dialect, especially low-resource languages where direct word-to-word translations often fail.

---

## Who This Is For

Lang Bridge is not a plug-and-play translator.  
It is a **framework for creators, dataset builders, and language developers.**

This system is useful if you:
- Want to simplify dataset creation for low-resource languages.
- Need a modular, scalable method to link words and phrases without complex linguistic rules.
- Care about building **culturally inclusive, context-aware datasets.**
- Are preparing structured data for LLMs without fine-tuning or heavy preprocessing.

---

## Why This Project Matters

Most translation tools break down in low-resource languages due to:
- Lack of structured datasets.
- Loss of meaning in direct, word-for-word translations.
- Ignoring cultural nuance and implied grammar.

Lang Bridge solves this by:
- Assigning each word a neutral internal key (val).
- Mapping full phrases via sequences of those keys.
- Quietly inserting missing grammar (like "is", "are", articles) at the phrase level.
- Producing culturally and grammatically correct translations by design.

The **val-mapping system is the core innovation:**
It builds datasets that are modular, scalable, and directly usable by LLMs without complex grammar parsing or linguistic engineering.

---

## Core Principles

- Words and phrases are fully linked through vals.
- Phrase-level mappings quietly handle grammatical corrections.
- The system is inherently **bi-directional**—it supports both source-to-English and English-to-source workflows using the same structure.
- Reverse translation is not a structural problem—**it only requires more data.**
- The focus is on **dataset creation and scalability, not just translation.**

---

## Key Use Cases

- Language Preservation: Build scalable datasets for underrepresented languages.
- Low-Resource Translation: Develop practical systems without large corpora.
- LLM Dataset Creation: Build structured, culturally coherent datasets ready for LLM workflows.
- Community Language Tools: Create phrasebooks, learning aids, or lightweight translation pipelines.

---

## How It Works

1. Words are mapped to vals in the word dataset.
2. Phrases are mapped as val sequences in the phrase dataset.
3. The system looks up user input, constructs the val sequence, and retrieves the correct phrase-level translation.
4. Missing grammar is handled at the phrase level—no linguistic rules are required.

This system:
- Preserves word-level translations.
- Provides culturally accurate phrase-level outputs.
- Builds connected datasets that can scale indefinitely.

---

## Project Structure

```
.
├── word_dataset.csv         # Maps each word to a unique val and literal English meaning
├── phrase_dataset.csv       # Maps sequences of vals to natural English phrases
├── translator.py            # Basic lookup demo (optional, not core)
└── README.md                # Documentation
```

---

## Dataset Format

### 1. word_dataset.csv

| val   | word   | literal_en |
|-------|--------|-------------|
| 11001 | iem    | what        |
| 11002 | i      | you         |
| 11003 | thaw   | do/doing    |

### 2. phrase_dataset.csv

| val_sequence       | phrase_source      | phrase_en               |
|--------------------|--------------------|-------------------------|
| 11001-11002-11003  | iem i thaw         | what are you doing?     |

---

## Example Output

```
Enter a phrase: iem i thaw?

Word-Level Lookup:
- iem → what (val: 11001)
- i → you (val: 11002)
- thaw → do/doing (val: 11003)

Constructed Value Sequence: 11001-11002-11003

Phrase-Level Lookup:
- Original Phrase: iem i thaw
- English Translation: what are you doing?
```

---

## Important Note

Lang Bridge is not a ready-to-use translator.  
It is a **dataset system and a modular translation framework.**

The Python script is just a demo.  
The key contribution is the **val-based linking system** that simplifies the creation of connected, culturally relevant datasets for low-resource languages.

What this system offers:
- A scalable, bi-directional dataset structure.
- A method to build modular, phrase-linked datasets for LLM input/output.
- A clean, adaptable way to build culturally correct translations without grammar engines or linguistic deep dives.

What it is not:
- A fully operational translator.
- A consumer-ready application.

---

## Tips for Modification and Extension

This system is deliberately simple and modular.  
Here’s how you can extend it:

### 1. Expand the Dataset
- Add new words and phrases to grow the dataset.
- Focus on cultural accuracy and community feedback.

### 2. Enable Reverse Translation
- Add English-to-val mappings to enable English-to-source translation.
- The system already supports this—**it just needs more data.**

### 3. Automate Dataset Growth
- Build a conversational logger to capture new phrases in real time.
- Use a lightweight LLM to suggest val mappings for new entries.

### 4. Fuzzy Matching
- Add typo tolerance using string similarity algorithms like Levenshtein distance.

### 5. Connect to LLM Pipelines
- Preprocess local language input to clean English for LLMs.
- Post-process model output back into the source language via the val mapping.

### 6. Build Interfaces
- Refine the CLI or build GUIs, mobile apps, or APIs.

### 7. Multi-Language Support
- Add datasets for other languages.
- Switch datasets dynamically using a language selector.

---

## Design Philosophy

Lang Bridge is based on one core belief:  
**The simplest path to low-resource language translation is a scalable, modular dataset—not complex grammar engines or large models.**

It’s a flexible system, not a fixed tool.

You are encouraged to:
- Build on it.
- Adapt it to your language.
- Extend it to your workflow.
- Treat it as a living, evolving system for building culturally relevant datasets.

---

## Roadmap

- [ ] Auto-add new words and phrases from conversations
- [ ] Fuzzy word matching and typo tolerance
- [ ] Mobile app or GUI for real-time use
- [ ] Multi-language dataset support
- [ ] Optional LLM assistance for phrase suggestions
- [ ] Bi-Directional Translation Support (English to Source Language)

---

## Why It’s Different

- Words and phrases are fully linked via vals.
- The system is **bi-directional by design**—it just needs more data to enable both flows.
- No grammar parsing required.
- No large linguistic datasets needed.
- No model fine-tuning necessary (but fully compatible if desired).
- Cultural and grammatical accuracy is embedded in the dataset itself.

Lang Bridge does not replace all machine translation systems.  
It is a **lean, modular, and scalable way to build culturally accurate datasets for low-resource languages.**

---

## Credits

Built by [dmuolhoi]  
Designed for Hmar, adaptable to any language.