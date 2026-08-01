Using the entire conversation above as the source material, produce a comprehensive, implementation-oriented plan for the hackathon system we have been designing.

Do not merely summarize the conversation.

Harvest the ideas, decisions, corrections, constraints, terminology, system components, proposed workflows, sequencing, uncertainties and unresolved design questions from the full conversation. Synthesize them into a coherent operating plan that David and Carlan could use to prepare for and run the hackathon.

The document must preserve the distinction between ideas that were firmly agreed, ideas that were suggested but not settled, and assumptions that still need validation.

## Core concept

The system listens to historical and live human and machine-generated streams, discovers valuable opportunities hidden within them, and turns selected opportunities into useful artifacts.

The two initial evidence sources are:

1. **Captain’s Log**

   * Ingests conversations and spoken stream-of-consciousness recordings from Plaud, Omi, Whisper Flow or similar sources.
   * Tags and structures those recordings using ontologies.
   * Contains personal discussions, project ideas, feature ideas, problems, health reflections, work discussions and other human context.
   * Represents what people were thinking, discussing, wanting, struggling with or imagining.

2. **Angel Eye**

   * Records Claude Code and Codex sessions.
   * Captures session transcripts and relevant lifecycle hooks, including session start, session end, turn start, turn end, tool calls, skill calls and other development events.
   * Represents what actually happened during implementation, including successes, failures, decisions, debugging, changes and development history.

The system between and around these sources should not be presented merely as a technical router. The router is infrastructure. The meaningful product is an **opportunity discovery and opportunity-realisation engine**.

Its broad proposition is:

> People and organisations are already producing valuable traces through conversations, journals, chat channels, development sessions and operational histories. This system listens to those traces, discovers unmet needs and valuable opportunities, helps people choose which opportunities matter, and then transforms selected opportunities into tangible outputs.

For the hackathon, the tangible output will primarily be small, useful micro-applications created for participants from short interviews.

## Required document purpose

Create a detailed plan that answers:

* What exactly are we building?
* What is the smallest convincing version that can work during the hackathon?
* What must exist before the hackathon starts?
* What happens during the hackathon?
* What happens in each participant pipeline?
* What skills, prompts, plugins, handovers, schemas, artifacts and interfaces are required?
* What decisions are made by AI?
* What decisions require human judgement?
* What information moves between phases?
* How do Captain’s Log and Angel Eye contribute differently?
* How do we preserve lineage from interview to opportunity to requirements to application to marketing?
* How do we run several participant pipelines in parallel without losing context?
* How do we demonstrate both personal value and universal applicability?
* How do we keep the scope achievable?

## Important architectural principles

Apply the following principles throughout the plan.

### 1. Single Responsibility Principle for skills

Do not create large skills with menus of unrelated capabilities.

Each transformation or responsibility should normally be represented by a separate, focused skill.

For example, generating interview questions, normalising transcripts, extracting facts, generating candidate opportunities, framing jobs to be done, scoring opportunities and creating requirements are separate responsibilities and should generally be separate skills.

Skills may be bundled inside a plugin, but each skill must remain independently understandable, testable, replaceable and callable.

### 2. Plugin containing a catalogue of skills

Design a plugin that contains the individual skills required by the workflow.

The plugin must include a clear table of contents or manifest describing:

* skill name
* single responsibility
* expected input
* expected output
* prerequisites
* phase in which it is used
* whether it is mandatory or optional
* next likely skill or skills
* validation criteria
* failure or fallback behaviour

The orchestration layer or Claude Code session should be able to inspect this catalogue and determine which skill should run next.

### 3. Separate participant lineages

Treat each selected person or participant as an isolated but structurally identical lineage.

The likely hackathon scope is:

* one combined David and Carlan pipeline
* four additional participant pipelines
* five pipelines in total

Each pipeline should preserve its own:

* source interview
* transcript
* evidence
* fact sheet
* candidate opportunities
* selected opportunity
* jobs-to-be-done framing
* value analysis
* requirements
* design decisions
* repository
* coding sessions
* Angel Eye records
* handover packages
* application
* documentation
* marketing or presentation artifact
* final outcome

Do not merge participant data in ways that make attribution unclear.

A separate portfolio-level process may analyse common themes across participants, but this must remain distinct from each individual participant’s lineage.

### 4. Explicit phase boundaries and handovers

Use major phase boundaries rather than trying to complete the entire workflow inside one endlessly growing Claude Code session.

The provisional phase structure is:

1. Discover
2. Evaluate and select
3. Define and design
4. Build
5. Analyse the build
6. Productise and present

Reconsider these names if a better structure emerges, but preserve the underlying concept.

At each major boundary, create a structured handover package.

David already has handover skills intended to open a new Claude Code session while carrying forward the relevant information from the previous session.

Define:

* when each handover occurs
* what the handover contains
* what should not be carried forward
* how the new session verifies the handover
* how missing or contradictory data is handled
* how the new session identifies the next skills to call
* how lineage and identifiers are preserved

The likely operating pattern is several vertically stacked or adjacent terminal sessions per participant, with continuity maintained through handover artifacts rather than relying on one enormous context window.

### 5. Human decision gates

The AI should expand, structure and evaluate possibilities, but humans must choose which opportunities are worth building.

A critical missing stage identified in the conversation is the opportunity-selection funnel.

The system must not move directly from interview to application build.

The process should be:

* collect rich but constrained interviews
* extract factual evidence
* generate multiple candidate opportunities
* present those opportunities in a fast, understandable form
* rank or shortlist them
* allow David, Carlan and ideally the interview participant to choose what feels most useful
* only then generate detailed requirements and begin implementation

### 6. Evidence before invention

The system should distinguish:

* what the participant explicitly said
* what can reasonably be inferred
* what the AI proposed
* what was selected by humans
* what was later discovered during development

Every opportunity and requirement should be traceable back to evidence.

Avoid presenting AI speculation as participant fact.

### 7. Captain’s Log and Angel Eye have different roles

Maintain this distinction:

* **Captain’s Log tells us what might be valuable to build and why.**
* **Angel Eye tells us what actually happened while it was being built.**

Captain’s Log is primarily an upstream source for discovery, needs, context, desires, frictions and opportunity generation.

Angel Eye is primarily a downstream source for implementation history, development evidence, lessons, technical narrative, failures, successes, documentation and marketing proof.

The broader routing architecture may eventually interrogate either source at any stage, but the hackathon plan should use the simplest clear division that can be demonstrated reliably.

## Required sections

Produce the final plan with the following major sections.

### 1. Executive overview

Explain the concept in plain language.

Describe:

* the problem
* the insight
* the proposed system
* why it matters
* the hackathon demonstration
* why the idea is useful beyond this specific event

Include a concise project thesis and a concise demonstration promise.

### 2. Product framing

Define the product at several levels:

* the broad universal concept
* the hackathon-specific implementation
* the internal David and Carlan use case
* the participant-facing experience
* the technical orchestration layer
* the evidence and lineage layer

Clarify what the product is not.

In particular, explain why it should not be pitched merely as a router, project-management tool, prompt chain or code generator.

Propose a strong working category or category description such as:

* opportunity discovery engine
* continuous opportunity listener
* trace-to-value engine
* opportunity-realisation engine
* another more accurate term derived from the discussion

Do not force a final product name unless the conversation supports one.

### 3. Hackathon story and demonstration arc

Design a compelling beginning-to-end demonstration.

The conversation proposed that the very first interview should be between David and Carlan, and that the first application or artifact may help create the pitch, presentation or North Star for the hackathon itself.

Explain how the demonstration could show:

1. David and Carlan being interviewed by their own system.
2. Their discussion being ingested into Captain’s Log.
3. Candidate opportunities being extracted.
4. One opportunity being selected.
5. A tangible artifact or application being generated.
6. Additional attendees being interviewed.
7. Opportunities being generated for those attendees.
8. Several participant applications being built.
9. Angel Eye recording how those applications were built.
10. Marketing pages, presentation artifacts, origin stories and value propositions being generated from both the human interview evidence and the coding evidence.
11. A portfolio-level view showing all participant pipelines and common themes.
12. Public repositories and deployable outcomes being shown at the end.

Make the presentation feel like a closed loop:

> We captured conversations, discovered opportunities, selected meaningful ideas, built real things, observed how they were built, and transformed the complete lineage into applications, documentation and stories.

### 4. Scope definition

Define:

* minimum viable hackathon scope
* target scope
* stretch scope
* explicitly excluded scope

Use five pipelines as the current target:

* David and Carlan
* participant 2
* participant 3
* participant 4
* participant 5

Discuss whether five applications must all be fully finished or whether graded completion is more realistic.

Recommend an achievable success definition, such as:

* five interviews completed
* five fact sheets produced
* five opportunity sets produced
* five human selections made
* five requirements packages produced
* three to five runnable applications
* all pipelines documented
* at least one polished end-to-end demonstration
* one portfolio presentation site

Do not quietly assume that ten complete polished applications are achievable. Explain the trade-offs.

### 5. Pre-hackathon validation and simulation

A major concern is whether short interviews will contain enough useful information to generate opportunities worth building.

Create a validation phase to run before the hackathon.

This should include:

* one synthetic interview
* one real rehearsal interview between David and Carlan
* possibly one external test interview
* transcript ingestion
* fact sheet generation
* candidate opportunity generation
* jobs-to-be-done cards
* ranking and human review
* requirements generation for at least one selected idea
* optionally a complete test build

Explain the key diagnostic rule raised in the conversation:

> If the opportunity cards are weak, do not immediately adjust the scoring system. First inspect whether the interview questions and source evidence were good enough.

Define what success looks like for the rehearsal.

Create a test matrix covering:

* rich interview
* vague interview
* overly solution-led interview
* contradictory interview
* participant with several unrelated interests
* participant with no clear app idea
* participant describing a problem but not a solution
* participant requesting something too large for the hackathon

### 6. Interview design

Design a short, high-yield interview structure appropriate for use with Plaud or Omi at a hackathon.

The interview must be limited enough to conduct repeatedly but rich enough to discover useful opportunities.

Do not assume that asking “What app do you want?” is sufficient.

The interview should uncover:

* who the person is in this context
* what they are trying to accomplish
* what currently frustrates them
* what they repeatedly do manually
* what information or decisions slow them down
* what they wish existed
* what a useful outcome would look like
* who else is affected
* what constraints matter
* what could realistically be demonstrated today
* what they would be excited to try immediately

Provide:

* a recommended primary interview format
* exact suggested questions
* optional probing questions
* a maximum duration
* interviewer guidance
* stopping rules
* how to avoid leading the participant
* how to separate problem discovery from solution requests
* how to capture consent for public use of interviews, repositories and demonstrations
* how to handle private or sensitive content
* how to label every recording immediately

Consider whether interviews should be:

* one continuous recording per participant
* several short recordings per participant
* a combination of core interview plus follow-up clips

Make a recommendation and explain why.

### 7. Ingestion and identity model

Define how every artifact is identified.

Create a simple naming and identifier convention for:

* event or hackathon
* participant
* interview
* recording segment
* transcript
* fact sheet
* opportunity
* selected opportunity
* requirement package
* handover
* Claude Code session
* Angel Eye session
* repository
* application build
* presentation or marketing artifact

Identifiers should be:

* unique
* human-readable
* sortable
* easy to use in filenames
* safe for Git repositories
* preserved across Captain’s Log, Claude Code, Angel Eye, GitHub and Vercel

Use ordinal labels where useful, but do not rely only on ambiguous labels such as “project 1” without a participant or event identifier.

Propose a directory and metadata structure.

### 8. Fact sheet generation

Define a dedicated fact-sheet skill.

The fact sheet must remain primarily factual.

It should include:

* participant summary
* relevant background
* goals
* current behaviours
* frustrations
* repeated tasks
* constraints
* tools currently used
* direct evidence excerpts or references
* unresolved ambiguities
* explicit requests
* inferred needs, clearly marked as inferences
* privacy or publication restrictions
* potential opportunity territories without prematurely selecting a solution

Explain how the fact sheet differs from:

* a transcript summary
* an opportunity card
* a requirements document
* a marketing persona

Provide a proposed fact-sheet schema.

### 9. Opportunity generation

Define how one interview becomes several candidate opportunities.

The system should generate a broad enough search space without overwhelming the human reviewers.

Discuss a likely output such as:

* five leading contenders
* five runners-up
* optional discarded or out-of-scope ideas stored separately

Each candidate should be expressed as an independently understandable opportunity, not as a vague feature list.

Define a dedicated skill or set of skills for:

* extracting opportunity territories
* generating candidate ideas
* deduplicating similar ideas
* checking evidence support
* identifying scope risks
* creating opportunity cards

### 10. Opportunity cards and jobs to be done

Create a standard opportunity-card format.

At minimum, each card should include a jobs-to-be-done framing.

A possible structure is:

* opportunity title
* participant
* source evidence
* situation
* struggle or friction
* job to be done
* desired outcome
* proposed intervention
* why it matters
* immediate user value
* expected demonstration value
* effort estimate
* feasibility
* confidence
* evidence quality
* privacy concerns
* dependencies
* risks
* what can be built today
* what would remain after the hackathon

Use a jobs-to-be-done statement such as:

> When [situation], I want to [motivation or job], so I can [desired outcome].

Do not force every opportunity into an unnatural formula. Allow additional explanatory text.

The card must be readable quickly by:

* David
* Carlan
* the interview participant
* another judge or observer with no prior context

### 11. Ranking, shortlist and human selection

Design a transparent ranking system.

Possible criteria include:

* user value
* strength of evidence
* hackathon feasibility
* time to first useful result
* demonstration clarity
* emotional resonance
* originality
* reusability
* technical risk
* dependency risk
* privacy risk
* likelihood the participant will actually try it

Do not let a weighted score silently make the final decision.

The score should organise attention, not replace judgement.

Define:

* automatic disqualification rules
* top contender selection
* runners-up
* participant feedback
* David and Carlan review
* final selection record
* reason for selection
* reason other ideas were not selected

Explain whether the system should select one idea per participant or allow a small combined application containing two tightly related jobs.

### 12. Value analysis frameworks

The conversation proposed jobs to be done, customer journey analysis, lean canvas and value proposition analysis.

Determine where each framework belongs in the flow.

Do not run every framework merely because it exists.

Recommend which are:

* mandatory before build
* optional before build
* better run in parallel with requirements
* better generated after the application exists
* useful only for presentation and marketing

The likely design should distinguish:

* evidence framing
* opportunity selection
* product definition
* business or value analysis
* marketing narrative

Explain whether customer journey, lean canvas and value proposition canvas should happen:

* before selection
* after selection but before build
* in parallel with application development
* after build using both interview and Angel Eye evidence

Provide a reasoned recommendation.

### 13. Technology-agnostic requirements package

Define a skill that transforms the selected opportunity into a strong, implementation-ready but technology-agnostic requirements package.

This package should include:

* problem statement
* user and context
* job to be done
* desired outcome
* success criteria
* primary user journey
* functional requirements
* non-functional requirements
* constraints
* assumptions
* data requirements
* inputs and outputs
* states and edge cases
* acceptance criteria
* minimum useful version
* exclusions
* future opportunities
* evidence mapping
* unanswered questions
* decision log

It should be strong enough that a later build phase can combine it with an implementation stack without having to reinterpret the original interview.

Clearly separate:

* participant requirements
* AI recommendations
* hackathon compromises
* technical decisions

### 14. AppyTron build preparation

The current likely build stack is AppyTron, an Electron application boilerplate.

Create a preparation process in which a focused skill studies the AppyTron boilerplate before the hackathon and records:

* architecture
* repository structure
* standard commands
* development workflow
* packaging workflow
* reusable UI components
* state management patterns
* data storage options
* common gotchas
* known build failures
* naming conventions
* testing approach
* how new applications should be created from the boilerplate
* how repositories should be initialised
* how applications should be made visually coherent
* what can safely be generated automatically
* what requires human inspection

This knowledge should become a focused AppyTron implementation skill or a small collection of focused skills, not an oversized generic app-building skill.

### 15. Skill and plugin architecture

Produce a complete proposed catalogue of individual skills.

Organise them by phase.

Potential areas include, but are not limited to:

#### Interview preparation

* interview-guide-generator
* interviewer-brief-generator
* consent-and-publication-check

#### Ingestion

* recording-identity-validator
* transcript-normaliser
* speaker-separation-validator
* Captain’s Log retrieval skill

#### Evidence

* interview-fact-extractor
* fact-sheet-builder
* ambiguity-detector
* evidence-reference-builder

#### Opportunity discovery

* opportunity-territory-extractor
* candidate-opportunity-generator
* opportunity-deduplicator
* jobs-to-be-done-framer
* opportunity-card-builder
* opportunity-scope-checker
* opportunity-ranker
* shortlist-builder

#### Human decision support

* participant-review-pack-builder
* selection-record-builder

#### Product definition

* customer-journey-builder
* value-proposition-analyser
* lean-canvas-builder
* requirements-builder
* acceptance-criteria-builder
* requirements-validator

#### Handover

* discovery-to-design-handover
* design-to-build-handover
* build-to-productisation-handover
* handover-validator

#### AppyTron development

* AppyTron-boilerplate-inspector
* repository-bootstrapper
* implementation-plan-builder
* micro-app-builder
* build-validator
* UX-polish-reviewer
* application-documentation-builder

#### Angel Eye

* Angel-Eye-project-session-locator
* coding-lineage-extractor
* implementation-decision-extractor
* build-failure-and-recovery-analyser
* technical-origin-story-builder
* development-summary-builder

#### Productisation and presentation

* origin-story-builder
* marketing-message-builder
* participant-project-page-builder
* portfolio-site-builder
* pitch-deck-content-builder
* final-demo-script-builder
* repository-readme-builder
* public-documentation-sanitiser

This list is illustrative. Refine, merge or split items according to the Single Responsibility Principle.

For every proposed skill, include:

* purpose
* exact responsibility
* inputs
* outputs
* caller
* phase
* dependencies
* success criteria
* likely test
* whether it should be built before the hackathon, during the hackathon or treated as a stretch capability

### 16. Prompt architecture

Identify the prompts required in addition to reusable skills.

Distinguish:

* bootstrap prompts
* orchestration prompts
* per-participant prompts
* build prompts
* recovery prompts
* review prompts
* presentation prompts

Do not write every final prompt in full unless useful.

For each prompt, state:

* its purpose
* when it is used
* what context it receives
* which skills it may call
* what it must produce
* what it must not do
* how it determines completion

Include a bootstrap prompt for Claude Code that:

* understands how to access Captain’s Log through MCP
* understands how to access Angel Eye through MCP
* checks whether those interfaces are available
* inspects their available tools and schemas rather than assuming them
* creates only the missing adapter or interface work that is genuinely required
* avoids rebuilding existing functionality
* establishes project identifiers and lineage rules
* loads the plugin manifest
* understands phase boundaries and handover rules

### 17. MCP integration

Define the required MCP interactions at a conceptual level.

For Captain’s Log, likely capabilities include:

* list recordings or conversations
* retrieve transcript
* retrieve tags and ontology metadata
* retrieve speaker and time metadata
* search by participant, date, event or identifier
* attach or write derived artifacts if supported

For Angel Eye, likely capabilities include:

* list development projects
* list sessions by project
* retrieve session transcript
* retrieve hook events
* retrieve tool and skill calls
* retrieve timestamps and outcomes
* retrieve handover boundaries
* search for failures, decisions or changes

Do not invent concrete tool names that have not been confirmed.

Specify an adapter-discovery process.

Identify the minimum MCP capabilities needed for the hackathon and which richer capabilities can be deferred.

### 18. Per-participant session flow

Describe the complete lifecycle for one participant.

It should likely include:

1. Create participant identity.
2. Record interview.
3. Ingest into Captain’s Log.
4. Validate transcript and speaker separation.
5. Generate fact sheet.
6. Generate candidate opportunities.
7. Create opportunity cards.
8. Rank and shortlist.
9. Review with participant and humans.
10. Record final selection.
11. Generate value analysis where appropriate.
12. Generate technology-agnostic requirements.
13. Validate requirements.
14. Create discovery-to-build handover.
15. Open new Claude Code build session.
16. Combine requirements with AppyTron implementation knowledge.
17. Create repository.
18. Build the application.
19. Test and polish it.
20. Record all development through Angel Eye.
21. Create build-to-productisation handover.
22. Read Angel Eye development evidence.
23. Generate documentation, origin story and marketing.
24. Create a participant project page.
25. Deploy or package the result.
26. Present it to the participant.
27. Capture participant reaction or feedback.
28. Update the final project narrative.

For each step, state:

* responsible actor
* skill or prompt
* input
* output
* human checkpoint
* likely failure
* fallback

### 19. Parallel execution model

Explain how five participant pipelines can run concurrently.

The conversation proposed creating five Claude Code sessions early and progressing each participant through similar phase boundaries.

Create an execution model covering:

* one silo per participant
* maximum number of simultaneous coding sessions
* use of multiple machines
* suggested work-in-progress limit
* how David and Carlan divide responsibilities
* when to pause a pipeline
* how to prioritise the strongest candidates
* how to prevent one difficult build from consuming the whole event
* how to recover from a failed coding session
* how to use handovers to reopen work elsewhere
* how to see pipeline status at a glance

Include a simple state model such as:

* interview pending
* transcript ready
* facts ready
* opportunities ready
* awaiting selection
* requirements ready
* build queued
* building
* validation
* productisation
* complete
* blocked
* abandoned

### 20. Control-plane or dashboard requirements

The conversation referenced a model-controller-view style visualisation and a dashboard-like view of participant pipelines.

Define the minimum control-plane interface.

It may show:

* participant
* current phase
* current Claude Code session
* selected opportunity
* repository
* latest handover
* Captain’s Log source
* Angel Eye source
* blockers
* application status
* deployment status
* next action
* completed skills
* queued skills

Explain what must be available for the hackathon and what can remain a conceptual mock-up.

Do not let dashboard development consume time needed for the actual opportunity-to-application pipeline.

### 21. Repository and public documentation strategy

The plan is to create a GitHub organisation and public repositories.

Define:

* GitHub organisation preparation
* repository naming convention
* one repository per participant project
* whether the portfolio site has its own repository
* whether the plugin has its own repository
* where shared schemas and skills live
* README requirements
* documentation requirements
* licence considerations
* public versus private information
* handling participant consent
* removal or redaction of sensitive interview content
* preserving evidence without publishing private transcripts
* release and tagging strategy
* issue and project-board usage, if any

Each participant repository may contain:

* application source
* sanitised interview summary
* fact sheet
* selected opportunity card
* requirements
* decision record
* development summary
* screenshots
* usage instructions
* origin story
* generated marketing page
* relevant handover artifacts
* link to deployed site or packaged application

Recommend what should and should not be public.

### 22. Application output strategy

The expected tangible output may include:

* a runnable AppyTron Electron application
* a simple web demonstration
* a Vercel-hosted participant project page
* a static HTML artifact
* a portfolio site containing all projects
* documentation and GitHub repositories

Clarify the difference between:

* the micro-app itself
* the marketing or presentation page for the micro-app
* the portfolio-level hackathon site
* the pitch deck or final presentation

Recommend the smallest useful deployment strategy.

### 23. Angel Eye post-build analysis

Define the downstream process that reads coding sessions after the application has been built.

This process should discover:

* what was built
* why technical decisions were made
* where the build diverged from requirements
* failures and recoveries
* tools and skills used
* implementation milestones
* evidence of effort or complexity
* unresolved limitations
* notable moments suitable for the origin story
* technical lessons
* future improvements

The output should support:

* documentation
* README files
* case-study narrative
* marketing claims
* project timeline
* final presentation
* comparison between intent and implementation

Do not use Angel Eye merely to produce a generic coding summary.

### 24. Origin story and marketing synthesis

Create a process that combines:

* participant interview evidence
* selected opportunity
* jobs-to-be-done framing
* value analysis
* requirements
* application screenshots or outputs
* Angel Eye coding evidence
* participant reaction

The marketing or presentation page should be able to tell:

* who the person was
* what they described
* what friction or opportunity was discovered
* why this particular idea was selected
* what was built
* how it was built
* what changed during implementation
* why it matters
* how the person can use it
* what could come next

Ensure that claims are evidence-based.

### 25. Portfolio-level horizontal analysis

In addition to five individual lineages, define a separate portfolio analysis.

This process may ask:

* what themes occurred across participants?
* what common frictions appeared?
* what opportunity categories emerged?
* what types of micro-app were most valuable?
* what interview questions produced the strongest evidence?
* what skills were used most?
* where did builds fail?
* what did the applications have in common?
* what does this reveal about the broader product?
* how could this help people elsewhere in Chiang Mai?
* what other domains could use the same approach?

Keep this analysis separate from individual selection decisions.

### 26. Broader use cases

Demonstrate the universal value of the system with a concise but varied set of examples.

Possible sources include:

* Slack channels
* team chat
* personal journals
* founder notes
* customer interviews
* support conversations
* community discussions
* development logs
* chef or kitchen logs
* healthcare operations
* city-service discussions
* education
* local businesses
* creative work
* research notebooks
* field-service histories

For each example, show:

* source trace
* opportunity discovered
* possible output

Do not turn this section into an enormous speculative catalogue.

### 27. Risk register

Identify risks including:

* interviews too shallow
* poor transcription
* speaker confusion
* weak opportunity generation
* ideas too large
* participant selects an infeasible idea
* repetitive or generic apps
* AppyTron boilerplate failure
* too many parallel coding sessions
* context loss between sessions
* MCP tools unavailable
* Angel Eye data incomplete
* privacy or consent failures
* public repository leakage
* build succeeds but UX is poor
* marketing is generated before enough evidence exists
* deployment failures
* hackathon time pressure
* pitch becomes too technical
* dashboard consumes too much effort
* overreliance on autonomous loops

For each risk, include:

* likelihood
* impact
* warning signs
* mitigation
* fallback

### 28. Quality gates

Define quality gates for:

* interview
* transcript
* fact sheet
* opportunity cards
* selection
* requirements
* handover
* build
* UX
* documentation
* public release
* final presentation

A pipeline should not automatically advance simply because a file exists.

Define what “good enough to proceed” means at each gate.

### 29. Time-boxed operating plan

Create a realistic schedule divided into:

* work to complete before the hackathon
* pre-session work immediately before the hackathon starts
* early hackathon
* middle build period
* late productisation period
* final presentation preparation

Do not assume exact event hours unless they were stated.

Use relative time blocks where necessary.

Clearly mark the critical path.

Identify work that can happen in parallel.

### 30. Roles and responsibilities

Propose a practical division of labour between David, Carlan and the AI agents.

Reflect the conversation:

* Carlan may conduct or help conduct participant interviews.
* David may prepare prompts, AppyTron workflows, Claude Code sessions, repositories and build infrastructure.
* Both may review and select opportunities.
* AI systems perform structured extraction, generation, transformation and build work.
* Participants should ideally help choose the opportunity and react to the result.

Recommend who owns:

* interview quality
* consent
* opportunity selection
* technical feasibility decisions
* repository management
* build monitoring
* UX review
* documentation
* pitch narrative
* final demonstration

### 31. Pre-hackathon deliverables checklist

Provide a concrete checklist covering items such as:

* GitHub organisation
* repository templates
* plugin skeleton
* skill manifest
* required skills implemented
* required prompts drafted
* Captain’s Log MCP verified
* Angel Eye MCP verified
* AppyTron boilerplate tested
* handover mechanism tested
* interview guide tested
* consent wording prepared
* synthetic interview prepared
* rehearsal completed
* opportunity-card template approved
* requirements template approved
* participant identifier system approved
* deployment accounts ready
* Vercel project or portfolio shell ready
* multiple machines ready
* Claude Code sessions and credentials ready
* fallback static-site generator ready
* final demo structure prepared

Separate mandatory preparation from optional preparation.

### 32. Day-of operating checklist

Create a sequential checklist that David and Carlan can follow without rereading the full plan.

It should cover:

* opening systems
* checking devices
* starting Angel Eye
* creating participant records
* recording interviews
* ingesting interviews
* validating transcripts
* generating fact sheets
* generating opportunity cards
* reviewing and selecting
* creating handovers
* opening build sessions
* creating repositories
* monitoring parallel builds
* validating applications
* generating product pages
* collecting participant reactions
* preparing the portfolio
* rehearsing the final presentation

### 33. Final demonstration script

Provide a provisional presentation structure.

It should lead with the human insight, not the technical plumbing.

A likely structure:

1. People already produce valuable traces.
2. Most of those traces disappear into recordings, chats and development logs.
3. We listened to those traces.
4. We discovered opportunities nobody had formally requested.
5. Humans selected the ideas that mattered.
6. The system generated requirements and built tangible micro-apps.
7. Angel Eye captured how each application came into existence.
8. The system turned the complete lineage into documentation and stories.
9. Here are the participant outcomes.
10. Here is the broader implication for Chiang Mai and other communities.

Include suggestions for live demonstration versus prerecorded backup.

### 34. Success metrics

Define hackathon success metrics in categories:

* participant experience
* opportunity quality
* build completion
* usefulness
* system reliability
* evidence traceability
* speed
* presentation quality
* reuse potential
* technical learning

Include leading and lagging indicators.

Avoid vanity metrics.

### 35. Open questions and decisions required

End with a prioritised decision register.

Include unresolved questions such as:

* final number of participants
* interview duration
* one recording or multiple clips
* exact Captain’s Log MCP capabilities
* exact Angel Eye MCP capabilities
* whether the first David and Carlan output is a pitch deck, planning app or another North Star artifact
* which value frameworks are mandatory
* whether every project must use AppyTron
* whether static web apps are an acceptable fallback
* how many builds can run simultaneously
* which artifacts can be public
* what consent language is required
* what the control-plane view must contain
* whether the portfolio site is generated continuously or only near the end
* whether participant feedback is captured as another Captain’s Log event
* how much autonomous recovery the build agents should attempt

For each question, recommend:

* when it must be decided
* who should decide it
* the default choice if no decision is made

## Required diagrams and structured views

Include clear text-based diagrams where useful.

At minimum include:

1. The overall system flow.
2. The per-participant pipeline.
3. The phase and handover model.
4. The five-pipeline parallel execution model.
5. The Captain’s Log versus Angel Eye evidence flow.
6. The plugin and skill architecture.
7. The human decision gates.
8. The repository and artifact lineage.

Use Mermaid or ASCII, whichever is most readable.

## Required tables

Include tables for:

* phase overview
* skill catalogue
* prompt catalogue
* handover packages
* artifact schemas
* participant pipeline state
* risk register
* quality gates
* pre-hackathon checklist
* day-of checklist
* responsibilities
* success metrics
* decision register

## Writing requirements

The document must be detailed, concrete and operational.

It must not be a sales pitch disguised as a specification.

It must not reduce the discussion to a generic AI app generator.

It must preserve the insight that the system discovers opportunities from traces before anybody has necessarily issued a formal request.

Use consistent terminology throughout.

Where the conversation used several possible terms, select one working term and mention the alternatives once.

Clearly label:

* agreed decisions
* recommended decisions
* assumptions
* open questions
* stretch goals

Where the conversation contains tension or competing approaches, explain the trade-off and recommend a default.

Do not invent facts about Captain’s Log, Angel Eye, AppyTron, Plaud, Omi, MCP tools, repositories or the hackathon that were not established in the conversation.

Do not claim that integrations exist until they have been verified.

Do not omit minor operational details merely because they seem unimportant. Small details such as project naming, public repositories, session handovers, participant consent and the distinction between human and coding evidence are central to making the system work.

## Final output standard

The completed document should function simultaneously as:

* product concept document
* hackathon execution plan
* system architecture
* workflow specification
* skill and plugin design
* prompt inventory
* operational runbook
* risk plan
* demonstration plan
* preparation checklist

It should be detailed enough that the next step after reading it is to begin creating the plugin, individual skills, prompts, schemas, rehearsal data and repository structure.
