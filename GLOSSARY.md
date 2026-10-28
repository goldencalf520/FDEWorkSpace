# FDE Workbench

This glossary defines the language used to describe an enterprise delivery engagement from initial evidence through an accepted software product.

## Participants

**FDE (Forward Deployed Engineer)**:
The solution-provider engineer accountable for turning an enterprise's needs into a deployable and accepted solution. The FDE is the workbench's primary day-to-day user.
_Avoid_: Implementation engineer, enterprise user

**Enterprise Participant**:
A customer-side person who provides evidence, clarifies needs, or confirms and reviews delivery outcomes without operating the full workbench day to day.
_Avoid_: Workbench user, interviewee

## Delivery

**Delivery Engagement**:
The body of work through which an FDE team turns one enterprise's evidence and needs into an accepted software product.
_Avoid_: Project, case, workspace

**Delivery Chain**:
The traceable progression from enterprise evidence through findings, business processes, solution design, prototype, implementation, verification, and review.
_Avoid_: Pipeline, workflow

**Delivery Area**:
A non-linear cluster of related delivery work that can be entered, revisited, or skipped when an engagement already has suitable inputs.
_Avoid_: Mandatory stage, wizard step, phase

**Entry Package**:
A set of existing materials, such as organized requirements and partial software, supplied to begin work in a later delivery area without repeating earlier work.
_Avoid_: Source evidence, verified conclusion

**Entry Mode**:
The declared starting condition of a delivery engagement: discovery from enterprise evidence, requirements from an organized brief, or takeover of an existing software product.
_Avoid_: Skipped steps, project type

**Supplied Baseline**:
An imported set of requirements, decisions, or software accepted as a starting point without being treated as enterprise-confirmed or verified.
_Avoid_: Verified conclusion, source evidence

**Engagement Boundary**:
The isolation boundary around one delivery engagement's participants, evidence, decisions, artifacts, software, tests, and reviews.
_Avoid_: Enterprise boundary, department boundary

**Reuse Policy**:
An FDE-organization rule that determines which delivery outcomes may be reused within one enterprise or across enterprises without requiring item-by-item approval.
_Avoid_: Project permission, enterprise consent

**Reusable Delivery Asset**:
A policy-compliant abstraction, such as an industry process pattern, solution profile, or aggregated performance result, that may inform another engagement without exposing protected source material.
_Avoid_: Raw recording, source code, enterprise identity

**Cross-Enterprise Override**:
An audited FDE decision, supported by applicable data rights, that permits specifically scoped source material to cross an enterprise boundary despite the default reuse policy.
_Avoid_: Automatic reuse, project sharing

**Affected Outcome**:
A downstream delivery outcome that must be re-examined because one of its supporting upstream outcomes changed.
_Avoid_: Failed outcome, deleted outcome

## Product Operation

**Workbench Desktop**:
The Windows or macOS application through which an FDE performs the full delivery engagement workflow and controls local execution capabilities.
_Avoid_: Enterprise portal, execution node

**Enterprise Portal**:
The browser-based participation surface through which enterprise participants confirm, comment, review, and accept scoped delivery outcomes without operating the full workbench.
_Avoid_: Workbench desktop, public share link

**Control Plane**:
The deployable service that coordinates shared engagement state, versions, relationships, policies, and audit history without requiring custody of every sensitive artifact.
_Avoid_: Execution node, source-code host

**Execution Node**:
An authorized Windows, macOS, or server environment that runs local models, coding agents, browsers, builds, and tests near the artifacts and credentials they require.
_Avoid_: Agent, control plane

**Content Location Policy**:
A rule declaring where a class of recordings, code, business data, credentials, and execution evidence may be stored and processed.
_Avoid_: Retention policy, file path

**Audit Event**:
An attributable record of a security- or delivery-significant action such as viewing, exporting, confirming, executing an agent, using a credential, accepting risk, or overriding reuse policy.
_Avoid_: Activity notification, debug log

**Audit Tombstone**:
A content-free retained record that a governed object existed and was deleted, preserving the accountable deletion event without retaining the deleted source or personal information.
_Avoid_: Archived content, soft deletion

**Capability Permission**:
An authorization to perform a specific action on a declared scope or object class, independent of a user's broad role label.
_Avoid_: Project membership, job title

**External Access Grant**:
A revocable, expiring, identity-verified authorization for an enterprise participant to view or act on a narrowly scoped portal outcome.
_Avoid_: Public share link, project membership

**Redacted View**:
A role-appropriate representation that preserves permitted meaning while withholding protected recordings, code, business data, credentials, or review content.
_Avoid_: Deleted source, anonymized dataset

**Edit Conflict**:
A detected attempt to change an outcome whose confirmed base version changed concurrently and therefore requires an explicit merge or selection.
_Avoid_: Last-write-wins update, review disagreement

**Engagement Export**:
A permission-filtered, portable representation of an engagement's evidence index, process models, solution, prototype, development baseline, tasks, tests, and reviews in open formats where practical.
_Avoid_: Database backup, unrestricted archive

**Tamper-Evident Audit Log**:
An append-only, verifiable, searchable, and exportable sequence of audit events in which privileged administrators cannot alter sensitive actions without detection.
_Avoid_: Application log, mutable activity feed

**Extension Adapter**:
A versioned integration with an external meeting, model, agent, source-control, knowledge, API, or test service that declares its capabilities, permissions, data destinations, and compatibility.
_Avoid_: Unrestricted plugin, embedded credential

**Extension Permission Manifest**:
The reviewable declaration of sensitive capabilities and data access required by an extension adapter before it may be installed or executed.
_Avoid_: Terms of service, runtime log

**Verified Adapter**:
An extension adapter that has passed declared capability, compatibility, permission, failure, and recovery tests against a specific external platform version.
_Avoid_: Installed adapter, theoretical integration

**Routing Eligibility**:
The current ability of a model or agent platform to receive a task after evaluating installation, authorization, region, data policy, budget, health, and task-type verification.
_Avoid_: Model popularity, configured provider

**Update Channel**:
An administrator-controlled stream of signed desktop and execution-node releases with explicit rollout timing and compatibility requirements.
_Avoid_: Package mirror, automatic restart

**Execution Resource Policy**:
The limits and scheduling preferences applied to an execution node according to CPU, GPU, memory, storage, power, network, and user activity.
_Avoid_: Agent budget, operating-system priority

**Recovery Profile**:
The declared backup, encryption, restore-testing, and recovery objectives for a class of control-plane or locally retained content.
_Avoid_: Retention policy, content location policy

**Telemetry Policy**:
The organization-controlled declaration of product performance, crash, and usage information that may leave an environment, excluding business content by default.
_Avoid_: Audit policy, unrestricted analytics

**FDE Organization**:
The commercial and administrative tenant whose delivery team manages users, enterprises, engagements, policies, adapters, credentials, and execution budgets.
_Avoid_: Enterprise participant, single project

**Managed Usage**:
Model, agent, or third-party execution purchased through platform-provided capacity and attributed to its organization, engagement, task, and provider.
_Avoid_: Customer-owned credential, subscription seat

**Customer-Owned Usage**:
Model, agent, or third-party execution authorized through credentials and commercial relationships supplied by the customer organization.
_Avoid_: Managed usage, free execution

**Engagement Overview**:
The project-centered view of current delivery state, provenance, risks, affected outcomes, and next actions across all delivery areas.
_Avoid_: Module dashboard, activity feed

**Attention Queue**:
The unified, responsibility-aware collection of findings, questions, confirmations, affected outcomes, failed runs, budget alerts, test gaps, and acceptance work that currently require action.
_Avoid_: Notification inbox, metric dashboard

**Guidance Mode**:
An interaction density that presents the same engagement state as a stepwise path for less experienced users without creating a separate workflow or data model.
_Avoid_: Simplified project type, tutorial

**Traceability Inspector**:
A contextual view available from any delivery outcome that exposes its sources, confirmation state, version, dependencies, and affected downstream outcomes.
_Avoid_: Audit report, properties panel

**Supported Capacity Envelope**:
The publicly tested organization, engagement, recording, domain-object, codebase, and agent-concurrency scale within which the product claims its performance and reliability targets.
_Avoid_: Theoretical maximum, business limit

**Long-Running Operation**:
An upload, transcription, indexing, agent, build, or test execution whose duration requires truthful progress, budget visibility, pause, retry, and recovery behavior.
_Avoid_: Background spinner, synchronous request

**Operation Checkpoint**:
A durable, idempotent recovery point from which a long-running operation can resume without repeating confirmed work or corrupting state.
_Avoid_: Progress percentage, debug snapshot

**Offline Event Queue**:
The ordered set of locally authorized draft changes retained while disconnected and submitted only after permissions are revalidated and version conflicts are resolved.
_Avoid_: Confirmed engagement history, synchronization cache

**Execution Capability**:
A governed Skill, MCP server, model, agent, adapter, or tool that may be selected to perform declared work in one or more delivery areas.
_Avoid_: Delivery area, feature flag, installed application

**Capability Registry**:
The authoritative catalog of execution capabilities and their availability, selection state, health, version, permissions, data destinations, and supported delivery uses.
_Avoid_: Plugin list, stage configuration

**Capability Use Record**:
An attributable record of which execution capability and version actually acted on which scoped inputs and produced which outputs.
_Avoid_: Available capability, generic activity log

**Capability Selection**:
The declared choice of an eligible execution capability for a delivery use, distinct from both its general availability and evidence that it actually ran.
_Avoid_: Installed capability, capability use record

**Capability Fallback Rule**:
A predeclared, policy-compliant condition under which an unavailable selected capability may be replaced by a named eligible alternative without a new selection decision.
_Avoid_: Silent substitution, routing recommendation

**Capability Trust Level**:
An organization-governed classification of an execution capability as built-in, publisher-verified, organization-verified, or unverified that constrains its permitted data, credentials, and external effects.
_Avoid_: Capability health, user rating

**Capability Dependency**:
A model, MCP server, runtime, account, credential, network condition, or other prerequisite that must be eligible and healthy before an execution capability can run.
_Avoid_: Capability permission, task dependency

**Capability Version Lock**:
The association between a delivery outcome and the exact execution-capability versions that produced it, retained until an accountable upgrade decision is made.
_Avoid_: Latest installed version, dependency lockfile

**Experimental Capability**:
An execution capability whose declaration, trust, compatibility, or organization verification is incomplete and whose data access and external effects are therefore restricted.
_Avoid_: Failed capability, beta product feature

**Organization Capability Catalog**:
The organization-private collection of reusable, versioned execution capabilities that retain their publisher, trust level, permission declaration, compatibility, and withdrawal state.
_Avoid_: Public marketplace, installed capability

**Capability Invocation Chain**:
The expandable record of the top-level capability and every nested Skill, MCP server, model, adapter, or external service that participated in one execution.
_Avoid_: Capability dependency, flat activity log

**Capability Trust Invalidation**:
The withdrawal of a capability's eligibility after a security finding or material change to its permissions, data destinations, dependencies, or external effects.
_Avoid_: Health-check failure, version upgrade

## Domain Knowledge And Process

**Domain Knowledge Source**:
A provenance-bearing, versioned, access-controlled body of reference material uploaded or connected for continued parsing and indexing within an allowed knowledge scope.
_Avoid_: Enterprise fact, source evidence

**Knowledge Scope**:
The reuse and access boundary of a domain knowledge source: product-wide, FDE-organization, enterprise, or delivery-engagement.
_Avoid_: Folder, document tag

**Knowledge Publication State**:
The declared readiness of a domain knowledge source as uploaded, parsed, indexed, reviewed, or published.
_Avoid_: Upload progress, model confidence

**Indexed Fragment**:
A retrievable portion of a domain knowledge source that retains its source identity, version, scope, permissions, and usage restrictions.
_Avoid_: Anonymous embedding, generated answer

**Knowledge Conflict**:
Two or more attributable domain knowledge sources that make incompatible claims for an overlapping context and therefore require an explicit applicability decision.
_Avoid_: Model error, merged answer

**Domain Pattern**:
A reusable industry process, constraint, or solution pattern derived from domain knowledge sources and presented as a reference hypothesis rather than a fact about an enterprise.
_Avoid_: Enterprise requirement, verified conclusion

**Match Candidate**:
A domain pattern proposed for one interview finding, pain, process step, or constraint together with its matching rationale, confidence, and alternatives.
_Avoid_: Automatic decision, industry classification

**Current-State Process**:
An enterprise-specific representation of how work currently proceeds, including its triggers, outcomes, roles, steps, systems, data, rules, permissions, judgment points, and exceptions.
_Avoid_: Industry pattern, target process

**Process Model**:
The structured source of truth for a business process from which swimlanes, flowcharts, BPMN views, and textual views may be rendered.
_Avoid_: Diagram image, canvas file

**Target-State Process**:
The desired enterprise process after an accepted solution changes the current-state process.
_Avoid_: Current-state process, industry pattern

**Transformation Gap**:
An explicit addition, removal, automation, or change required to move from a current-state process to a target-state process.
_Avoid_: Pain, implementation task

**Exceptional Path**:
A formally modeled process path for failure, return, cancellation, timeout, insufficient permission, human fallback, or unavailable dependency.
_Avoid_: Edge note, out-of-scope case

**Clarification Question**:
A question generated from a specific missing or conflicting process detail, prioritized by its effect on downstream delivery outcomes and tracked through answer and confirmation.
_Avoid_: General chat message, suggestion

**Process Version**:
An immutable version of a current-state or target-state process that can be confirmed and compared with later versions at the affected-element level.
_Avoid_: Latest diagram, document revision

**Attached Discussion**:
A communication thread bound to a specific finding, process element, rule, or gap and carrying its participants, status, owner, due date, and resolution.
_Avoid_: General chat, meeting transcript

**Accepted Delivery Risk**:
A named FDE's decision to continue work despite an unresolved or unconfirmed dependency while preserving that dependency's effect on downstream outcomes.
_Avoid_: Confirmation, ignored warning

## Solution And Development

**Prototype Library**:
A separately governed catalog of versioned prototype patterns and related design assets that the workbench may search and import without treating the catalog as engagement-owned content.
_Avoid_: Workbench project, copied template folder

**Prototype Candidate**:
A prototype-library result presented with its stable identity, version, preview, provenance, usage rights, applicable capabilities, matching rationale, alternatives, and import path.
_Avoid_: Selected prototype, search result thumbnail

**Prototype Library Contract**:
The versioned boundary through which the workbench searches, resolves, checks rights, imports, and reports outcomes without depending on the prototype library's internal storage model.
_Avoid_: Shared database, template folder

**Prototype Search Context**:
The explicitly selected business, role, channel, design, image, and technical constraints disclosed to a prototype library for one search.
_Avoid_: Entire engagement, raw interview archive

**Prototype Feedback Envelope**:
The policy-filtered template identity, usage classification, and permitted outcome signals returned to a prototype library without automatically disclosing enterprise source material.
_Avoid_: Engagement export, analytics event

**Reference Capture**:
An attributable, time-stamped capture of an authorized website, application, image, recording, or exported design used for study without becoming an owned prototype pattern.
_Avoid_: Prototype template, copied product

**Design Interpretation**:
A traceable account of the structure, interaction ideas, visual principles, and constraints inferred from one or more reference captures before creating a new design.
_Avoid_: Source copy, final prototype

**Design Usage Rights**:
The declared permissions and restrictions governing whether a prototype candidate or reference capture may be viewed, analyzed, modified, shared, or used commercially.
_Avoid_: Access permission, source provenance

**Design Conversion Mode**:
The declared transformation intent for reference material: interpret its principles into a new design, reproduce it under sufficient rights, or migrate an owned product into a new design system and technology stack.
_Avoid_: Similarity score, export format

**Imported Prototype Branch**:
An engagement-owned prototype lineage created from a selected candidate and its recorded source version, which upstream library changes cannot overwrite automatically.
_Avoid_: Library template, synchronized copy

**Design Import Review**:
An explicit comparison and selective merge of changes from a linked design-authoring artifact into a new prototype version.
_Avoid_: Live synchronization, automatic overwrite

**Design Merge Conflict**:
A material disagreement between imported design changes and confirmed business, process, requirement, or prototype outcomes that requires an accountable resolution.
_Avoid_: Visual diff, automatic merge failure

**Reference Capture Scope**:
The declared pages, user paths, devices, and interface states that a reference-capture operation may observe.
_Avoid_: Entire website, crawl limit

**Design Asset Rights Status**:
The known, restricted, or unresolved right to reproduce a font, image, icon, video, brand element, or other asset in a generated delivery outcome.
_Avoid_: File availability, access permission

**Design System Profile**:
The versioned project or enterprise selection of design tokens, components, brand rules, supported states, and substitution rules used to shape prototype and interface outcomes.
_Avoid_: Style guide document, prototype pattern

**Design QA Result**:
An evidence-backed evaluation of prototype coverage, design-system consistency, responsive behavior, accessibility, and design-source compliance that does not substitute for running or testing generated code.
_Avoid_: Technical acceptance, visual opinion

**Prototype Pattern**:
A reusable interaction, screen, or business-flow reference used to shape a target prototype without prescribing its implementation architecture.
_Avoid_: Code starter, solution profile

**Prototype Skeleton**:
A low-fidelity representation of information architecture, role-specific paths, and interactions used to confirm structure before visual refinement.
_Avoid_: Final design, code starter

**Prototype Version**:
A confirmed delivery record that binds an immutable set of screens, actions, fields, states, role variants, source relationships, and linked authoring-artifact versions to the outcomes it represents.
_Avoid_: Latest mockup, development baseline

**Prototype Acceptance**:
An accountable conclusion that a prototype version adequately represents the intended business coverage, role paths, states, interactions, and usability for its declared scope.
_Avoid_: Technical acceptance, visual approval

**Prototype Coverage Gap**:
A target process element or acceptance criterion without a corresponding prototype representation, or a prototype element without an attributable business source.
_Avoid_: Visual defect, feature request

**Mock Dataset**:
A synthetic, internally consistent set of related business records and state transitions used to exercise normal, boundary, and exceptional prototype paths without exposing real enterprise data.
_Avoid_: Anonymized production dump, placeholder text

**Code Starter**:
A versioned code asset capable of creating or extending a repository for a declared solution profile.
_Avoid_: Prototype pattern, example screenshot

**Generated Code Candidate**:
Source code derived from a confirmed prototype or design reference that remains subject to the development baseline, technical review, testing, and acceptance before it can be treated as delivered software.
_Avoid_: Editable prototype, production-ready code

**Prototype Adoption Signal**:
An attributable observation that a prototype candidate was selected, modified, rejected, confirmed, or associated with a later outcome, with evidentiary weight appropriate to the type of observation.
_Avoid_: Popularity count, experience weight

**Current-State Model**:
An FDE-corrected representation of the capabilities, user flows, and data flows observable in an existing software product.
_Avoid_: Target prototype, desired solution

**Development Baseline**:
The FDE-confirmed definition of what development will deliver and how completion will be judged, including scope, target flows, acceptance criteria, key data, external interfaces, and explicit exclusions.
_Avoid_: Requirements document, supplied baseline

**Deployable Subsystem**:
A part of the delivered product that can be released independently and can therefore have its own compatible technology choices.
_Avoid_: Module, feature

**Solution Profile**:
A reusable, validated combination of technology choices for a deployable subsystem.
_Avoid_: Framework, unrestricted component list

**Custom Solution Configuration**:
A user-assembled combination of technology choices whose compatibility and risks are evaluated for the engagement but which is not implicitly treated as a validated solution profile.
_Avoid_: Solution profile, unsupported solution

**Technology Bill Of Materials**:
The versioned set of frameworks, databases, middleware, identity, storage, messaging, external services, and deployment dependencies selected for a delivered product.
_Avoid_: Package lockfile, technology wishlist

**Decision Recommendation**:
An explainable set of ranked solution candidates with their fit, gaps, cost, risks, constraints, and rejected alternatives retained for an accountable selection.
_Avoid_: Automatic best choice, model answer

**Third-Party Service Candidate**:
An external API or service evaluated for a declared need across coverage, capability, cost, reliability, compliance, data residency, lock-in, and exit options.
_Avoid_: Approved integration, API key

**Credential Grant**:
A least-privilege, task-scoped authorization made available to an agent without exposing its underlying secret in ordinary conversation, screenshots, prompts, or logs.
_Avoid_: Shared API key, environment dump

**Development Task Graph**:
A dependency graph of development tasks whose nodes declare inputs, outputs, owned code scope, interface contracts, acceptance criteria, and prohibited changes.
_Avoid_: Flat task list, prompt queue

**Engineering Workflow Pack**:
A version-locked, replaceable collection of engineering Skills and conventions that turns a development baseline into specifications, tracked tasks, implementation work, and review evidence.
_Avoid_: Mandatory vendor workflow, orchestration backend

**Issue Tracker Projection**:
An externally synchronized view of development specifications, tasks, dependencies, reviews, and status that remains subordinate to the workbench development record.
_Avoid_: Development source of truth, engagement history

**Orchestration Backend**:
An explicitly selected execution capability that places and supervises agent work while leaving task meaning, permissions, evidence, and acceptance under workbench authority.
_Avoid_: Engineering workflow pack, development source of truth

**Connection Task**:
A development task whose bounded responsibility is to configure, implement, or verify an external service, protocol, credential grant, MCP server, or execution environment.
_Avoid_: General development task, unrestricted production access

**Agent Placement**:
The accountable selection of an execution node for an agent task after evaluating content location, code, credentials, required capabilities, health, capacity, and cost in that order.
_Avoid_: Cheapest-model routing, orchestration backend selection

**Decision Gate**:
A durable, authorized choice that blocks a high-risk task transition or external effect until one declared option is resolved.
_Avoid_: Worker question, notification, automatic approval

**Unverifiable Run State**:
An agent-run state in which the authoritative execution node cannot currently prove whether the attempt is live or exited, and which therefore cannot be treated as either failure or completion.
_Avoid_: Failed run, timed-out run

**Agent Work Contract**:
The bounded responsibility assigned to an agent for one task, including the permitted workspace, required outputs, acceptance criteria, budget, and stop conditions.
_Avoid_: General instruction, agent role name

**Concurrency Limit**:
The maximum number of agents permitted to run simultaneously, distinct from the smaller number that current task dependencies may make useful.
_Avoid_: Required agent count, speed setting

**Execution Budget**:
The approved limits for cost, tokens, elapsed time, retries, and concurrency applied to an agent run.
_Avoid_: Cost estimate, unlimited retry policy

**Integration Agent**:
An agent responsible for ordering, merging, and verifying isolated changes against shared contracts without owning the underlying feature requirements.
_Avoid_: Implementation agent, final test agent

**Verification Agent**:
An agent independent of the implementation task that evaluates its code, tests, and acceptance evidence.
_Avoid_: Implementation self-check, final test agent

**Agent Run Record**:
A resumable record of an agent's input versions, model, platform, tool activity, code changes, tests, costs, checkpoints, and failure state.
_Avoid_: Chat transcript, completion message

**Acceptance Test Matrix**:
The mapping from every development-baseline acceptance criterion to an automated test, a named manual test with evidence, or an explicit not-applicable decision.
_Avoid_: Test-file list, coverage percentage

**Test Coverage Gap**:
An acceptance criterion that lacks an adequate test mapping or execution result.
_Avoid_: Failed test, unimplemented feature

**Flaky Test Result**:
A test result whose outcome changes across equivalent executions and therefore cannot be treated as a stable pass merely because a retry succeeded.
_Avoid_: Passed test, transient note

**Technical Acceptance**:
An evidence-backed conclusion that the declared technical acceptance criteria passed in a reproducible test environment.
_Avoid_: Business acceptance, release approval

**Business Acceptance**:
A named FDE or enterprise decision that the verified product satisfies the intended business outcome.
_Avoid_: Technical acceptance, jury score

**Review Snapshot**:
The locked set of baseline, prototype, code, test, and business-acceptance versions evaluated by a jury.
_Avoid_: Latest project state, live workspace

**Review Dimension**:
A named evaluation perspective with declared evidence, rubric, weight, minimum score, and optional veto conditions.
_Avoid_: Generic prompt, reviewer role

**Unscored Dimension**:
A review dimension for which required evidence is unavailable and which therefore cannot honestly receive a numeric score.
_Avoid_: Zero score, inferred score

**Score Disagreement**:
A material difference between jury evaluations that requires comparison of evidence and assumptions rather than automatic averaging.
_Avoid_: Low average, failed dimension

**Improvement Item**:
An evidence-linked corrective action with impact, owner, priority, acceptance criteria, and the earliest delivery area that must be revisited.
_Avoid_: General recommendation, reviewer comment

**Engagement History**:
The versioned record of evidence, confirmations, processes, solutions, prototypes, implementation, tests, reviews, and their relationships throughout a delivery engagement.
_Avoid_: Current project state, activity feed

**Current Engagement View**:
The latest valid projection of an engagement history after accounting for superseded, affected, withdrawn, and deleted outcomes.
_Avoid_: Mutable source of truth, latest file

**Outcome Signal**:
An attributable observation about a delivered solution after or during delivery, such as acceptance, actual use, business effect, defect rate, maintenance cost, schedule, or budget variance.
_Avoid_: Jury opinion, model confidence

**Experience Weight**:
A context-specific influence derived from positive and negative outcome signals, applicability, recency, and evidence quality that changes the ranking of a reusable delivery asset.
_Avoid_: Global quality score, popularity count

**Retention Policy**:
An organization, enterprise, or engagement rule governing how long each class of sensitive source material, execution evidence, and reusable abstraction may be retained.
_Avoid_: Backup schedule, deletion request

## Knowledge And Trust

**Interview Template**:
A versioned, configurable arrangement of interview topics, questions, ordering, and completeness rules selected for an engagement context.
_Avoid_: Fixed interview stage, completed interview

**Source Evidence**:
Original material supplied or produced by enterprise participants, such as meeting speech, recordings, documents, and direct feedback.
_Avoid_: Requirement, truth

**Evidence Segment**:
An immutable, time-bounded portion of source evidence associated with its recorded speaker identity or an explicit unknown-speaker label.
_Avoid_: Finding, edited quote

**Source Transcript**:
The preserved machine transcription of source evidence before an FDE or enterprise participant corrects or interprets it.
_Avoid_: Confirmed transcript, meeting summary

**Correction Annotation**:
A traceable human correction attached to source evidence without replacing the original recording or source transcript.
_Avoid_: Transcript overwrite, AI inference

**Interview Finding**:
A structured statement extracted from an interview and linked to supporting evidence segments, such as an enterprise fact, pain, desired outcome, constraint, decision, commitment, disagreement, or open question.
_Avoid_: Meeting summary, transcript passage

**Unknown Speaker**:
An unresolved participant label retained when the system or FDE cannot reliably associate speech with a known enterprise participant.
_Avoid_: Guessed participant

**Recording Authorization**:
The recorded basis on which a meeting or uploaded recording may be captured and used, including its source, responsible uploader, capture time, participants, and consent state.
_Avoid_: File permission, upload completion

**Recognition Context Pack**:
Engagement-scoped background material supplied before analysis to improve recognition of enterprise names, people, products, terminology, abbreviations, and existing facts.
_Avoid_: Source evidence, global training data

**Finding Confidence**:
Separate indicators of transcription, speaker attribution, semantic extraction, and evidentiary support for one interview finding.
_Avoid_: Meeting accuracy score, truth probability

**Review Queue**:
The ordered collection of findings requiring human attention because of low confidence, conflicting evidence, or high consequence if wrong.
_Avoid_: Task backlog, notification list

**Correction Memory**:
A scoped memory of confirmed terminology or speaker corrections that may improve later analysis within an engagement, enterprise, or policy-approved anonymous industry context.
_Avoid_: Source evidence, unrestricted model training

**Enterprise Confirmation Pack**:
A focused set of material findings presented to enterprise participants for item-level confirmation, correction, or rejection without requiring review of an entire transcript.
_Avoid_: Meeting summary, final report

**Analysis Version**:
An immutable set of analysis results produced from a declared combination of source evidence, context, models, and analysis instructions.
_Avoid_: Latest result, overwritten analysis

**Delivery Report Version**:
An immutable, reviewable presentation of delivery conclusions that preserves its supporting evidence, confirmation state, unresolved items, and relationship to superseding versions.
_Avoid_: Live dashboard, generated prose

**AI Inference**:
A machine-generated interpretation derived from source evidence that has not yet been confirmed by an accountable person.
_Avoid_: Fact, confirmed requirement

**Critical Finding**:
A finding whose omission or misinterpretation could materially change delivery scope, architecture, compliance, acceptance, or a commercial decision.
_Avoid_: Interesting detail, transcript keyword

**FDE Confirmation**:
An explicit acceptance by an FDE that an inference is suitable for continued delivery work.
_Avoid_: Enterprise approval, verification

**Enterprise Confirmation**:
An explicit acceptance by an enterprise participant that a statement or outcome represents the enterprise's intent.
_Avoid_: FDE confirmation, verification

**Accountable Confirmation**:
A confirmation attributed to a named person who accepts responsibility for allowing the delivery engagement to proceed on that basis.
_Avoid_: Model confidence, anonymous approval

**Verified Conclusion**:
A conclusion supported by downstream test or delivery evidence, in addition to any human confirmation.
_Avoid_: AI inference, assumption

## Acceptance

**Demo Scenario**:
The declared audience, business story, product path, environment, integrations, presenters, and intended outcome of one customer demonstration.
_Avoid_: Demo script, sales opportunity

**Demo Readiness Template**:
A versioned set of required and optional readiness expectations that may be specialized by a demo scenario, organization, product, or execution capability.
_Avoid_: Static checklist, task list

**Demo Readiness Item**:
One accountable readiness expectation with an owner, due time, status, blocking severity, and completion evidence.
_Avoid_: Reminder, unchecked box

**Rehearsal Evidence**:
Attributable evidence of a timed demonstration rehearsal, including the scenario exercised, environment, result, failures, and unresolved risks.
_Avoid_: Presenter assurance, test result

**Demo Readiness Decision**:
The evidence-backed conclusion that a declared demo scenario is ready, blocked, or proceeding with specifically accepted non-blocking risks.
_Avoid_: Checklist percentage, calendar status

**Demo Dataset**:
A scenario-bound set of synthetic, redacted, or specifically approved real records prepared for a demonstration with declared validity and reset behavior.
_Avoid_: Test fixture, production copy

**Demo Snapshot**:
A locked, immutable combination of product version, demo dataset, accounts, configuration, integrations, presentation, and script from which a demonstration can be initialized and restored.
_Avoid_: Backup, release tag

**Demo Integration Mode**:
The declared operating context of an external dependency during a demo as simulated, provider sandbox, or live, with consequences appropriate to its real-world effects.
_Avoid_: Environment name, connection status

**Live Demo Action Allowlist**:
The narrowly declared external write operations and target objects permitted during a live-mode demonstration.
_Avoid_: Service permission, presenter role

**Demo Emergency Stop**:
An audited action that immediately blocks remaining live external writes and revokes applicable temporary authorizations without erasing evidence of the triggering condition.
_Avoid_: Application exit, demo reset

**Demo Mode**:
An isolated operating context that uses a demo snapshot, suppresses inappropriate internal information, and prevents demonstration activity from contaminating formal enterprise records.
_Avoid_: Presentation theme, test environment

**Readiness Invalidation**:
The withdrawal of previously satisfied readiness items when a material demo-snapshot or scenario dependency changes.
_Avoid_: Checklist reset, failed rehearsal

**Readiness Evidence Window**:
The period during which a readiness check remains sufficiently current to support a demo-readiness decision.
_Avoid_: Retention period, due date

**Demo Preparation Pack**:
A permission-safe, exportable assembly of the demo scenario, versions, responsibilities, readiness evidence, rehearsal results, accepted risks, fallback path, and operational contacts.
_Avoid_: Slide deck, credential bundle

**Demo Fallback Path**:
A rehearsed alternative that uses prepared offline, recorded, simulated, or static material when a required live dependency is unavailable.
_Avoid_: Improvisation, incident response plan

**Demo Audience View**:
A presentation-safe projection of one demo snapshot that exposes only the content appropriate to a declared audience.
_Avoid_: User role, redacted engagement export

**Demo Run**:
The attributable record of one rehearsal or customer demonstration against a demo snapshot, including its participants, actual versions, incidents, feedback, and follow-up actions.
_Avoid_: Demo snapshot, recording

**Demo Remediation Item**:
A problem discovered during a rehearsal or demo run that is linked to the affected readiness item or product outcome and requires ownership, correction, and re-verification.
_Avoid_: Feedback note, generic task

**Demo Feedback Record**:
A post-demo observation classified as attributable enterprise feedback, an FDE's contemporaneous note, or an FDE inference before it enters the delivery chain.
_Avoid_: Confirmed requirement, meeting summary

**Temporary Demo Resource**:
A demo-scoped account, authorization, dataset, or live-service permission with a declared expiry and post-demo reset, disablement, or deletion action.
_Avoid_: Permanent test account, credential

**Development Baseline Lead Time**:
The elapsed time from the first source evidence or entry-package import until an FDE confirms the development baseline.
_Avoid_: Total project duration, coding time

**FDE Review Time**:
The active time an FDE spends correcting and confirming extracted interview findings into usable delivery knowledge.
_Avoid_: Meeting duration, processing time

**Evidence-Backed Test Result**:
A test result linked to reproducible execution evidence, such as step screenshots, video, logs, or API and data assertions.
_Avoid_: Agent completion claim, test summary

**Blocking Failure**:
An outcome that rejects the release regardless of average score, including cross-enterprise data leakage, an undisclosed critical-finding omission, or a false claim that an unexecuted or failed test passed.
_Avoid_: Low score, improvement suggestion
