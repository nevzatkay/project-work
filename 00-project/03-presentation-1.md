---
project_outline: "[[00-project/01-project-outline]]"
---

<!-- 5xl -->
# Board-game rules companion with source references

A mobile-friendly assistant for situational rules questions

Author: Nevzat Kayıkçı  
Neptun: JWM27Z  
Supervisor: Sári Dávid  
Project ID: 2026-SD-02

---

## Problem
- A game situation may require several rules together.
- Finding the relevant sections interrupts play.
- Editions and expansions can change the answer.
- Players need explanations they can verify.

**How can we answer rules questions with evidence from the correct rulebook?**

---

## Proposed idea
- Select a game, edition and expansions.
- Ask a question about the current situation.
- Retrieve relevant rulebook excerpts.
- Use an LLM to explain them with source references.

**Ask for missing details; report when evidence is insufficient.**

---

## Target users and scope
**Users:** players and game-session organisers.

**In scope**
- A few selected games, text-based PDF and Markdown.
- Saved questions, personal notes and answer feedback.
- Visible editions and clearly labelled house rules.

**Out of scope:** a game engine, computer opponent or automated adjudication.

---

## User journey 1: prepare the rules
1. Upload a rulebook with permission to use it.
2. Identify the game, edition and expansion.
3. Process pages, sections and cross-references.
4. Select the applicable rules collection.

**Search stays within that collection.**

---

## User journey 2: ask and clarify
1. Describe the game situation.
2. The system searches for relevant rules.
3. It asks for details that could change the answer.
4. It explains the answer using retrieved evidence.

**Insufficient or conflicting evidence may leave the question unresolved.**

---

## User journey 3: check and save
1. Read the answer and supporting excerpts.
2. Open a reference in its original context.
3. Save the question and add personal notes.
4. Flag an incorrect answer or record a correction.

**Saved answers retain the document versions used.**

---

## Retrieval approach
- Combine keyword and semantic search candidates.
- Filter by edition and expansion applicability.
- Rerank evidence using documented rules.
- Follow explicit references to related sections.

Section structure helps connect rules spread across the book.

---

## Main comparison
| Approach | Evidence retrieval |
| --- | --- |
| Basic RAG baseline | Fixed-size text chunks |
| Enhanced approach | Section hierarchy and cross-references |

Also compare keyword, semantic and hybrid search.

**Use the same checked questions and consistent comparison settings.**

---

## What will be measured?
- Retrieval recall and complete evidence for multi-rule questions.
- Answer correctness and whether citations support claims.
- Incorrect-edition retrieval and answers.
- Appropriate clarification and abstention.
- Response time, including slow or failed requests.

**A citation that exists is not automatically evidence for a claim.**

---

## Reliability and version handling
- Show the selected edition and supporting evidence.
- Keep old references tied to their original versions.
- Mark outdated answers when documents change.
- Preserve saved work if an AI service fails.
- Treat document text as data; keep credentials server-side.

---

## Expected deliverable and success
- A responsive web application with persistent storage.
- A documented processing and retrieval pipeline.
- A checked question-answer-source dataset.
- A reproducible baseline comparison and limitations report.

**Success means traceable answers and honest uncertainty, supported by evaluation.**

---

## Next steps
1. Confirm the initial games and document usage conditions.
2. Define source identifiers, versioning and the data model.
3. Prototype upload, retrieval and source viewing.
4. Prepare the technical proposal and evaluation dataset.
5. Implement and compare the two pipelines.

**Thank you. Questions?**
