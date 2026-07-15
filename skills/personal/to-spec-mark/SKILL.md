---
name: to-spec-mark
description: Synthesize settled context into Mark-style project specifications, proposed revisions, or gap reports without unauthorized writes or work breakdown. Use when Mark asks to turn a clarified conversation, notes, project controls, or source evidence into a new specification or revision; when a canonical specification location must be proposed or checked; or when unsettled context should be routed to generic grilling before specification drafting.
---

# To Spec Mark

## Operating Contract

Produce one of three outputs:

- a conversation-only draft specification;
- a conversation-only proposed revision to an existing canonical specification; or
- a focused gap report when important decisions are not settled.

Act as a strict synthesizer. Do not conduct a full interview inside this skill. If context is unsettled, route to generic `grilling` with a compact specification-focused steering brief. Do not persist drafts, edit project controls, create work breakdown, create tickets or tracker/YAML/Plane artifacts, access external services, or execute the specified work unless Mark separately authorizes that exact action.

Keep ordinary use lean. Do not load validation fixtures, long examples, or implementation notes unless implementing, validating, debugging, or resolving an ambiguity in this skill.

## Workflow

1. Identify whether Mark is asking for a new specification, an existing-spec revision, or readiness/gap analysis.
2. Read only the local context needed for the request: user-supplied context, named project controls, named source files, and any existing canonical specification being revised.
3. Decide whether the outcome is sufficiently settled for a conversation-only draft or revision.
4. If not settled, return a gap report or route to generic `grilling`.
5. If settled, produce a draft or proposed revision with status, scope, source summary, verification, and authorization gates.
6. If persistence is desired, include a `Persistence Request` that asks for content approval and the named write authorization in one user-facing pass.

## Required Draft Shape

Every draft or revision must include:

- `Spec Status and Permissions`;
- purpose;
- project boundary;
- outcome definition;
- work type: `code`, `non-code`, or `coherent mixed`;
- in scope and out of scope;
- deliverables;
- constraints and prohibited actions;
- verification criteria;
- approval gates;
- known gaps;
- deferred downstream work; and
- source summary.

Use these status fields for persisted or persistence-intended specifications:

```text
Specification Status: draft | specification-approved
Canonical Specification Location: <location>
Persistence Status: conversation-only | conversation-only; persistence desired but not authorized | authorized-to-persist | persisted
Execution Status: not-authorized
```

For code specs, add expected behavior, likely affected area, proposed verification steps, test/check command if known, unknown technical assumptions, and human review check.

For non-code specs, add expected output, approved sources, prohibited sources/actions, completion test, human review check, and fact/inference/provenance rule.

For coherent mixed specs, include shared outcome, code deliverable, non-code deliverable, separate verification for each deliverable, and why splitting would be artificial or harmful. Route independently completable or separately approved work back to `grilling` for separation.

## Existing-Spec Revisions

Prefer revising an existing canonical specification when new settled context changes the same outcome. Propose a new specification only when the outcome is meaningfully separate.

For material revisions, show the proposed change or section-level delta, identify changed or superseded assumptions, and ask Mark to approve the revised content and authorize writing the named file in the same pass. Clerical fixes and non-substantive formatting do not require reapproval.

## Persistence Request

When persistence is desired, include:

- intended Canonical Specification Location;
- whether `AGENTS.md` confirms this location;
- proposed `AGENTS.md` Specification Contract text if missing;
- why this location belongs there; and
- exact approval and write authorization needed before writing.

Ask for approval and write authorization together: approve this content and authorize this named file write. Do not insert an extra generic persistence step. Authorization must name the specific file action and exclusions, and it must not imply work breakdown, tracker creation, implementation, external access, or execution.

## Gap Reports And Grilling

Return a gap report when important decisions block drafting or persistence. Include blocking gaps, why each blocks progress, non-blocking uncertainties only when they affect later work breakdown, one recommended next grilling decision, and clear permission status.

When routing to `grilling`, provide a compact steering brief covering outcome, boundary, scope, sources, constraints, verification, approval/write target, and explicit non-authorization. Avoid work breakdown unless it is needed to clarify the specification boundary.

## Provenance

Every draft includes a short `Source Summary`. Simple drafts may say `User-supplied conversation only`.

Use concise inline provenance labels when claims affect scope, decisions, gaps, verification, current rules, or revisions. Broad labels are enough for simple cases: note-backed fact, project-control fact, Mark-supplied update, user-supplied conversation, and agent inference.

Use detailed states only when they matter: suggestion, Mark-confirmed decision, reported execution result, paused item, unresolved gap, superseded assumption, and agent inference. Do not turn unresolved suggestions or inherited assumptions into requirements without Mark confirmation. Do not over-annotate every claim when source roles are obvious.

## Simplification

When Mark indicates that a category is small, low-risk, or not worth taxonomy, choose a simple adequate default, label the simplification, and preserve approval, write, and execution gates.

Treat empty capacity as empty, reserved, or out of scope unless Mark assigns a purpose. Use `paused item` only when the distinction matters.

## Maintenance Sources

For ordinary use, rely on this `SKILL.md`. For maintenance, implementation review, validation, or ambiguity resolution, read the relevant approved sources:

- `/home/mark/Documents/Obsidian Vaults/Agent Wiki/plans/To-Spec-Mark Agent Behaviour Specification.md`
- `/home/mark/Documents/Obsidian Vaults/Agent Wiki/plans/To-Spec-Mark SKILL Implementation Specification.md`
- `/home/mark/Documents/Obsidian Vaults/Agent Wiki/plans/To-Spec-Mark Validation Fixtures Specification.md`
- `/home/mark/Documents/Obsidian Vaults/Agent Wiki/plans/Matt Pocock Workflow Adoption Plan.md`

Current source files must be re-read before implementation changes because they may change. Relevant sources include Matt's current `to-spec`, Matt setup/local tracker/domain docs, Mark's `new-agentic-folder`, and active schema/templates/naming references.
