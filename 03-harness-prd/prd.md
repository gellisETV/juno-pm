# Harness Sketch

Describe Juno's role and task: Juno AI - takes multiple artifacts (reports / research / user stories etc...) and evaluates what should be prototyped

_Rough first pass, Module 3 Lab 1. Not the AI PRD._

## 01 · Context
The raw artifact stream (Raw Signals.md) containing multi-channel inputs (Productboard CSV exports, customer interviews, support tickets, executive emails, sales CRM call notes, and engineering Slack threads). It also reads the active skill.md definitions and product parameters.

Deliberately left out: Live production database credentials, unverified third-party web scrapers, and raw company financial ledgers, preventing the model from hallucinating enterprise valuation metrics.

Data Hygiene & Boundaries: The context window expects clean text-based inputs. If data exceeds safety token limits or contains corrupted formatting, the harness must automatically truncate or request a summarized text stream, explicitly flagging truncated rows in the citation log.

Ambiguity Handling: If a raw signal lacks specific context (e.g., unstructured single-word complaints), Juno must categorize it under an "Unclassified Friction Pool" rather than forcing a high-priority mapping, explicitly noting the ambiguity in the citation block.

## 02 · Tools
Parse and cluster unstructured text artifacts.

Execute deterministic prioritization frameworks (Value vs. Impact matrices and MoSCoW scoping).

Generate structured markdown outputs, PR/FAQ product narratives, and structural ASCII text wireframes.

Emergency Break Conditions: The loop halts immediately and hands back to the human PM if:

Direct contradictions arise between critical artifacts (e.g., executive mandate conflicts directly with technical safety limits).

Zero valid source citations can be mapped to a high-priority feature request.

Wireframe.cc Integration: Generate structural component placement specs (JSON or layout coordinates) that map directly into Wireframe.cc’s block primitives or render an interactive low-fi wireframe viewport via external tool invocation.

Deliberately left out: Full graphic design rendering in Figma or Canva.

## 03 · Loop
A single-pass chain-of-thought execution loop for synthesis, followed by an iterative feedback check with the human PM.

Stop condition: Stops automatically once all eight standard output sections (Executive Summary, Traceable Insights, Value vs. Impact Matrix, PR/FAQ, MoSCoW Scope, Text Wireframes, Risk Analysis, and Actionable Next Steps) are fully populated.

Wireframe Generation Loop: Automatically triggers after the MoSCoW scope is finalized. If the wireframe layout exceeds standard single-viewport limits or fails structural validation, it makes one automated correction pass before handing off to the PM.

## 04 · Memory
The structured markdown report, updated skill parameters, and traceable citation logs persist within the session workspace and notebook context.

What expires: Transient raw prompt scaffolding and intermediate reasoning tokens are discarded. Only the human PM has write permissions to permanently update the system prompt or skill definition.

Audit Persistence: Each generated report must be timestamped and version-locked (e.g., v1-output-YYYY-MM-DD). Historical runs cannot be silently overwritten, ensuring the CPO can track how product recommendations evolve as raw signals shift.

## 05 · Permissions
Ingest raw text data, cross-reference sources, draft specifications, and structure ideas into standard templates.

Tiered safeguards: Because it cannot push code or modify live task trackers, its potential blast radius is low. However, high-impact decisions (such as pausing executive AI initiatives or committing to enterprise delivery dates like the Okta SSO deadline) require explicit human-in-the-loop sign-off.

Binding Commitment Restrictions: Juno is strictly forbidden from outputting definitive external delivery dates or financial commitments in the "Actionable Next Steps" or "PR/FAQ" sections; all timelines must be flagged as Proposed Estimates requiring Engineering sign-off.

Wireframe Generation Limits: Juno is permitted to generate structural wireframe mockups and component maps autonomously for top-ranked features, but cannot publish public links or push layouts directly to production design files without human approval.

## 06 · Verification
Every synthesized insight must clear a strict verification check: it must contain an explicit bulleted citation pointing to the exact document and paragraph/row (e.g., Artifact 1 [Paragraph 1]).

Failure handling: If an insight lacks a verifiable trace or relies on unbacked assumptions, the output is rejected or flagged for manual review before the CPO or engineering lead ever sees it.

Citation Cross-Reference Rule: The verification check must validate that the cited row or paragraph index physically exists within the ingested Raw Signals.md file bounds. If an index is out of bounds or non-existent, the verification check fails and triggers an automated re-synthesis pass.

Wireframe-to-Spec Consistency Check: Before presenting the wireframe to the PM, the harness verifies that every interactive element or state shown in the layout maps directly back to a "Must Have" requirement in the MoSCoW scope. If a phantom component appears, the output is rejected.
