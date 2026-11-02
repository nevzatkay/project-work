---
project_outline: "[[00-project/01-project-outline]]"
---
# Board-game rules companion with source references
Neptun: JWM27Z  
Project ID: 2026-SD-02  
supervisor: Sári Dávid


This project proposes a mobile-friendly web application that helps players answer situational questions using the selected board game's rulebooks. Users choose a game, edition and applicable expansions, ask a question, and inspect an answer with precise references to the original rules. The application retrieves relevant excerpts before asking a large language model (LLM) to explain them. It asks for missing details and reports when the available sources cannot establish an answer. Users can save questions and personal notes and flag incorrect answers.
Objectives
- Primary objective: Build a usable rules companion that provides traceable, edition-appropriate answers grounded in retrieved rulebook excerpts.
- Target users: Board-game players, session organisers and users maintaining a small collection of rulebooks. The supervisor and examiners assess the implementation and evaluation.
- Research questions:
  - How do keyword, semantic and hybrid retrieval compare for situational rules questions?
  - Does section hierarchy and cross-reference retrieval improve evidence coverage compared with a basic fixed-chunk RAG baseline?
  - How reliably can the system keep editions separate, request missing details and abstain when evidence is insufficient?
- Measurable success criteria:
  - A responsive application supports a few selected games, persistent document/question storage, personal notes and feedback.
  - Text-based PDF and Markdown imports retain document versions, page locators where available, section identifiers and source context.
  - Search is restricted to the selected game, edition and applicable expansions. House rules are explicitly labelled.
  - Answers cite retrieved evidence. References open the original context, and previous answers retain their original document versions.
  - A manually checked question-answer-source dataset supports reproducible retrieval and answer evaluation.
  - Evaluation reports retrieval recall, complete evidence retrieval, answer correctness, citation support, incorrect-edition retrieval, unanswerable-question handling and latency.
  - Baseline and enhanced pipeline results are reported fairly, including failures and cases without improvement.
Scope
In scope
- A mobile-friendly web application with persistent rulebooks, questions, answers and personal notes.
- A small curated set of games with explicit edition and expansion metadata.
- Text-based PDF and Markdown processing with stable section identifiers, hierarchy and cross-references.
- Keyword and semantic candidate retrieval, candidate fusion, applicability filtering and justified reranking.
- Retrieval-augmented generation (RAG), which supplies source excerpts to the LLM before it answers.
- Clarification questions, source conflict handling and explicit abstention when evidence is insufficient.
- Verifiable references, original-context viewing, saved question history and incorrect-answer reports.
- Version-aware document replacement and index rebuilding.
- A reproducible evaluation comparing a fixed-chunk baseline with a structure-aware approach.
Out of scope
- A complete game engine, computer opponent or automated adjudication.
- Support for every board game or unrestricted web answers.
- Training a new language model.
- Mandatory support for scanned/image-only PDFs through OCR.
- Multilingual questions, complex table interpretation and shared session question collections in the initial version. These are optional extensions.
Research and evaluation plan
Check usage conditions before selecting or distributing rulebooks. Prepare a manually checked dataset covering direct lookups, questions requiring multiple sections, edition and expansion differences, missing situational details, conflicting evidence and unanswerable questions. Use a development subset to tune retrieval and a held-out subset for final evaluation. Record expected sources and acceptable clarification or abstention behaviour.

Compare keyword-only, semantic-only and hybrid retrieval under consistent collection filters and retrieval budgets. Compare a fixed-chunk RAG baseline against section-aware retrieval with cross-references while holding the generation model and other shared settings fixed. Measure whether citations actually support claims, separately from automatic checks that their locators exist. Choose the dataset size, games, model, chunking strategy and target thresholds during the technical proposal, then freeze the evaluation protocol before final testing.
Constraints and deliverables
Separate application, persistence and AI integration logic. Keep service credentials server-side. Treat uploaded documents as untrusted data, preserve saved work when AI services fail, and allow users to correct suggestions. Store code, setup instructions, permitted sample data and evaluation scripts in Git, excluding secrets and personal or production data.

Deliver a working application, documented processing/retrieval pipeline, reproducible evaluation and limitations report. This outline describes planned work. The assigned brief is 2026-SD-02.md; specific tools and providers will be justified during design.
