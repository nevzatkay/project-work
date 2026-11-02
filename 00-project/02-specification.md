project_outline
[[00-project/01-project-outline]]
Board-game rules companion with source references
Author: Nevzat Kayıkçı
Neptun: JWM27Z
Supervisor: Sári Dávid
Project ID: 2026-SD-02

1. Actors and access
Role	Needs and access
Player	Select a rules collection, ask questions, inspect sources and save personal questions or notes
Collection maintainer	Upload permitted documents, assign edition/expansion metadata and review processing results
Evaluator	Run the documented evaluation against checked questions and source labels
One person may hold several roles. Questions, personal notes and corrections belong to their user or isolated local profile. The deployment and identity mechanism will be decided during design. AI suggestions never grant access or change source documents automatically.

2. Use cases
UC1: Upload and prepare a rulebook
Precondition: The maintainer has permission to use the document.
Flow: Upload a text-based PDF or Markdown file; identify game, edition and expansion if applicable; extract structure; review section/page mappings and cross-references; build the index; activate the validated version.
Errors: Reject unsupported or unreadable files with an explanation. Processing failure leaves the previous active index available.
Result: A versioned, searchable document with verifiable source locators.
UC2: Select rules and ask a question
Flow: Select game, edition and expansions; optionally enable explicitly labelled house rules; enter a situational question; retrieve evidence within that selection; generate a grounded response.
Alternative: If a missing detail could change the answer, ask a targeted clarification and search again after the reply.
Result: An answer with evidence, a clarification request or an explicit unresolved response.
UC3: Inspect an answer and its references
Flow: Read the selected edition, answer and source excerpts; open a reference to the original PDF page or Markdown section with surrounding context.
Errors: Conflicting sources trigger clarification or an unresolved indication. Missing evidence must not produce an asserted ruling.
Result: The player can check whether each cited rule supports the explanation.
UC4: Save questions, notes and corrections
Flow: Save a question and its answer with source versions; add or edit personal notes; flag an incorrect answer with a reason; record a user correction separately from the generated answer.
Errors: AI failure must not delete the question, notes or previously saved answers.
Result: Persistent personal history with clear provenance and feedback.
UC5: Replace a document or rebuild its index
Flow: Create an immutable new document version; validate extraction and index; activate it; retain historical references and flag answers affected by changed source versions as historical or requiring review.
Errors: Failed rebuilds leave the prior working version intact. Do not silently point old citations to new content.
Result: Current answers and historical evidence remain distinguishable.
UC6: Evaluate retrieval and answers
Flow: Run a frozen checked dataset against the retrieval alternatives and baseline/enhanced pipelines; record retrieved sections, answers, citations, clarification/abstention outcomes, latency and errors; score and compare results.
Result: Reproducible measurements with documented limitations.
3. Functional requirements
ID	Requirement	Acceptance criterion
FR1	Import text-based PDF and Markdown	Valid examples of both formats persist with source content and metadata; unsupported files return an actionable error
FR2	Preserve document structure	Every indexed section has a document-version-bound stable ID and a source locator; headings, parent sections and explicit references are retained
FR3	Select applicable rules	The interface shows game, edition and expansions; retrieval and related-section expansion cannot leave that selected collection
FR4	Implement hybrid retrieval	Keyword and semantic candidates are fused, deduplicated, applicability-filtered and reranked using a documented method
FR5	Follow cross-references	Explicit references retrieve applicable related sections with a documented depth/budget and cycle protection
FR6	Ground LLM responses	The model receives retrieved excerpts and citation IDs; answers distinguish supported claims, assumptions and uncertainty
FR7	Clarify missing information	Checked ambiguous questions trigger requests for decision-relevant details rather than invented circumstances
FR8	Handle insufficient or conflicting evidence	Unsupported questions yield an explicit unresolved response; conflicts trigger clarification or remain unresolved
FR9	Show verifiable references	Selecting a citation opens the original version's page or section and surrounding context
FR10	Save questions and personal notes	Saved questions, answers and editable notes survive reload and restart within the deployment's persistence model
FR11	Record incorrect-answer feedback	A flag stores the answer ID, reason and optional correction without overwriting the original answer
FR12	Label house rules	User-defined rules remain visibly separate from official rules and apply only when explicitly selected
FR13	Preserve answer provenance	Every saved answer retains selected rules, immutable source version IDs, citations and generation configuration
FR14	Manage replacement and reindexing	Version changes mark affected previous answers as historical/requiring review; index rebuilds preserve valid locators and never relabel obsolete evidence as current
FR15	Support reproducible evaluation	A documented command runs the checked dataset and exports per-question results, configuration, errors and aggregate metrics
All FR1–FR15 are required. Multilingual questions, advanced tables and shared session collections are optional extensions.

4. Data model and source identity
Entity	Minimum information
Game / rules selection	Game ID, edition, selected expansions and explicit house-rule selection
Document version	Immutable version ID, content hash, title, edition, expansion applicability, original file, usage conditions and active/historical status
Section	Stable ID within a document version, heading path, parent ID, text, original locator and outgoing cross-references
Index build	Build ID, document-version set, parser/chunking/embedding configuration and activation status
Question / answer	User/profile, question, clarification history, selection snapshot, answer/status, model/prompt configuration, citations and timestamp
Citation	Exact document version, section ID, excerpt span and original context locator
Note / feedback	Owner/profile, linked question or answer, text, correction if supplied and timestamp
PDF locators retain physical page index and printed page label when reliably available. Markdown uses section IDs and source line/span information; it must not invent page numbers. Reindexing the same immutable source keeps section identity stable. Changed source text creates a new document version; mappings between versions are explicit, never silent.

5. Processing and retrieval design
Validate input and usage metadata; preserve original bytes as an immutable version.
Extract text, page boundaries, headings and section hierarchy. Review ambiguous structure or unresolved references.
Map explicit references to section IDs. Keep unresolved targets visible rather than guessing links.
Produce section-aware chunks with parent metadata and exact source spans. Split long sections with documented overlap, preserving identity.
Generate keyword and semantic candidates within the allowed rules collection.
Fuse candidate rankings, deduplicate, enforce edition/expansion/house-rule applicability and rerank.
Expand explicit related-section references within the same allowed collection, deduplicate and enforce the context budget.
Supply evidence to the LLM, request clarification where needed and generate an answer with source IDs or an unresolved response.
Validate citation membership and locators before display. Invalid references trigger an error or unresolved response, not fabricated references.
The student will implement structure mapping, candidate fusion, applicability filtering and reference resolution. Search libraries and existing models may support these components. Initial fusion may use reciprocal rank fusion; its parameters and any reranking rules will be justified and evaluated before being fixed. No backend, model or hosting provider is assumed to have been selected yet.

Behavioural constraints
Documents are untrusted data and cannot override application instructions or invoke tools.
Personal notes do not become official rules or searchable house rules without explicit user action.
Source conflicts cannot be resolved by silently preferring a newer file or an expansion. Use explicit applicability evidence, seek clarification or report unresolved conflict.
A valid citation identifier proves that a source exists, not that it supports the associated claim.
Generated explanations assist players; the application does not enforce moves or act as an automated adjudicator.
AI requests and persistence transactions are separated so timeouts cannot discard saved work.
6. User interface
Collection view: upload, processing status, game, edition, expansions, document versions and usage information.
Question view: visible rules selection, situational question and clarification exchange.
Answer view: explanation or unresolved status, supporting excerpts and original-context links.
History view: saved questions, personal notes, corrections and historical-version labels.
Feedback action: flag an incorrect answer and optionally explain the problem.
The interface must be usable on a phone without horizontal scrolling for core workflows. The source viewer may support zooming for original PDF pages.

7. Evaluation
Dataset and comparisons
Create a manually checked question-answer-source dataset for a few selected games. Record the applicable edition/expansions, expected answer or clarification/abstention, and all required evidence sections. Include single-section questions, multi-section questions, expansion differences, wrong-edition distractors, missing situational details, conflicts and unanswerable cases. Document reviewer identity and limitations. Use development and held-out subsets, preventing near-duplicate questions from crossing the split.

Compare keyword-only, semantic-only and hybrid retrieval at the same candidate/evidence budget and with the same applicability constraints. Compare a basic fixed-size chunk RAG baseline with an enhanced pipeline using section hierarchy and explicit cross-references. Keep the document corpus, test questions, model, prompt policy and shared generation settings consistent. Freeze chunk sizes, retrieval budgets, reranking rules and test protocol before the final run. Report configurations and service/model versions so reruns are as reproducible as the services permit.

Metric	Operational definition
Retrieval recall@k	Fraction of required gold evidence units covered by the top-k retrieved passages, mapped to original source spans
Complete evidence retrieval	Fraction of answerable multi-rule questions for which every required evidence unit is retrieved within the fixed budget
Answer correctness	Manually checked correctness against the applicable rules and labelled question circumstances
Citation validity	Automatic checks that each cited version/section/span exists and belongs to the selected collection
Citation correctness and coverage	Manual checks of whether citations support each claim and whether substantive rule claims have supporting citations
Incorrect-edition retrieval	Rate of retrieved evidence and final answers/citations using versions outside the selected collection, reported separately
Unanswerable-question handling	Correct abstentions among unanswerable cases, unsupported answers on those cases, and unnecessary abstentions on answerable cases
Clarification handling	Whether cases with missing details elicit the necessary question before a ruling
Latency	Retrieval and end-to-end response time, including median, p95 and failures/timeouts under documented conditions
Score multi-rule and expansion cases separately. Map evidence to source spans to avoid rewarding one chunking method merely for using larger chunks. Report failure examples and trade-offs, not just aggregate scores. Zero cross-edition leakage and valid source resolution are design acceptance goals; benchmark accuracy and latency thresholds will be agreed after the pilot, not invented as achieved results.

8. Non-functional requirements
Requirement	Verification
Responsive interface	Complete selection, question, citation and history workflows on phone and desktop viewport sizes
Persistent storage	Restart/reload tests preserve documents, questions and notes
Failure resilience	Simulate unavailable AI and failed imports/rebuilds; existing data and prior usable index remain accessible
Source security	Test embedded prompt-injection text, invalid citations and attempts to access a different rules collection
Secret protection	Keep credentials on the server, exclude secrets from Git and avoid exposing them in browser requests or errors
Maintainability	Separate application/UI, persistence, document processing, retrieval and AI adapters
Reproducibility	Document setup, dependencies, permitted samples, evaluation command and configuration
User control	Allow editing notes and recording corrections without rewriting historical AI outputs
9. Risks and open design decisions
Risk or decision	Planned response
Rulebook usage restrictions	Check each selected document's conditions; distribute only permitted sample content
Complex layouts or extraction mistakes	Start with text-based documents; inspect structure and page/section mapping
Multiple rules needed for one question	Preserve hierarchy and follow cross-references; measure complete evidence retrieval
Edition or expansion confusion	Explicit selection, applicability filtering and adversarial separation tests
Plausible but unsupported explanations	Ground responses, request missing details, allow abstention and manually assess citation support
Hosted model cost or unavailability	Compare suitable providers/local options during design; expose failures without losing saved work
Excessive scope	Limit initial games; retain required versioning, evidence and evaluation features before optional extensions
Model and retrieval choices	Justify chunking, fusion, reranking, model and hosting in the technical proposal
The assigned requirements in 2026-SD-02.md are authoritative. This specification describes planned work rather than completed implementation or benchmark results.
