---
name: work-number-assignment
description: Assign repository-defined work numbers such as T1-A to upcoming implementation work, finalize the earliest eligible open major when the user instructs implementation to begin, and allow that finalization to be reopened until implementation actually starts. Use repository-defined categories, a per-category closed-through major, predecessor-completion gating, parallel-stage grouping, and the next major for replanned work while preserving numbering history once implementation has begun.
---

# Work Number Assignment

Use this skill when assigning work numbers to upcoming implementation work, when the user instructs implementation of a major to begin, or when the user withdraws or revises that pending implementation before it actually starts.

## Number format

Use:

```text
<category><major>-<minor>
```

Example:

```text
T1-A
T1-B
T2-A
```

## Repository-defined categories

The repository defines the available category prefixes and what each category means.

Use only repository-defined category meanings.

Discover category definitions and work-number records from repository instructions or documentation without assuming a fixed filename or path.

## Closed-through major

Record the highest currently finalized major for each category in the repository's authoritative work-number records.

Use the same source of truth that records work-number assignments.

Example:

```text
T: closed through 3
D: closed through 5
```

Every major at or below that value is closed to newly assigned work while it remains finalized.

The closed-through value may advance when a major is finalized.
It may roll back only when reopening the latest finalized major before implementation has actually started in that major.
Never roll it back below a major whose implementation has actually started.

Already assigned work numbers remain valid identifiers after their major becomes closed.

Keep assignments in unstarted open majors provisional.
Provisional assignments may contain gaps in major numbers or minor letters while work is being split, combined, removed, or realigned.

When the user instructs implementation of a major to begin, first normalize that category's provisional assignments above the closed-through value from the latest work structure.
Remove avoidable gaps in major numbers, assign minor letters contiguously within each affected major, and use dependency and parallelism decisions freshly evaluated by the surrounding workflow from the latest repository state to move dependent work to later open majors under the normal numbering rules.

The earliest resulting open major is eligible for finalization only when the preceding major in the same category is complete.
Major `1` has no preceding-major prerequisite.
Treat a major as complete for this predecessor condition when no implementation remains to be done under any work item fixed in that major.

Judge this from the repository's recorded work state, not from whether every fixed work item completed implementation successfully.
For example, no implementation remains under a fixed work item when its implementation completed successfully, when a failed attempt has been replanned so any remaining implementation belongs to replacement work, or when the work item was explicitly canceled or superseded before implementation began.
The predecessor-completion condition tracks remaining implementation work.
A completed implementation satisfies that condition while merge prerequisites govern its later incorporation.
If underlying work is still required, its replacement work structure must be established before treating the original fixed work item as having no remaining implementation.
Do not infer that no implementation remains merely because an item disappeared from the active plan.
Replacement work may already have provisional work numbers in open majors while its structure is being established.
Do not infer major completion from the closed-through value; closed-through records current numbering finalization, not work completion.

Then apply the implementation-start instruction to the earliest resulting eligible open major and finalize it.
Advance the category's closed-through value to that major.
Finalization fixes the major's membership for the pending implementation start, but remains reversible until implementation actually begins.

## Reopening before implementation starts

If implementation has not actually begun for any work item in the latest finalized major, the user may withdraw or revise the pending implementation and reopen that major.

When reopening:

- restore the category's closed-through value to its previous value, or remove it when reopening major `1` and no earlier major is closed;
- return the reopened major's assignments to provisional state;
- apply the normal provisional realignment and normalization rules to later work as needed.

Do not treat the earlier instruction to begin implementation as proof that implementation actually started.

Once implementation actually begins for any work item in a finalized major, preserve that major's membership and work numbers as irreversible history.
Do not reopen or renumber that major afterward.

## Major numbers

Major numbers are independent within each category.

Start from `1` when the category has no existing work number.

Work items that can proceed in parallel may share the same open major number.

When assigning numbers to multiple plans added together within the same category, each plan that depends on another plan in that same addition uses a later major number than that dependency.

Assign major numbers from implementation dependency and parallelism.
Merge prerequisites govern incorporation order.

Work that belongs to a later non-parallel stage uses a later major number.

New work receives a major above the category's closed-through value.

An existing open future major may receive another work item when the surrounding workflow already determines that they belong to the same parallel stage.

## Minor numbers

Within the same major number, distinguish work items with uppercase letters in order:

```text
A
B
C
...
```

Assign multiple upcoming work items together when needed.

## Existing assignments

Use repository work-number records as the source for existing assignments.

When an existing assignment is discovered before its major becomes irreversible through actual implementation, align the proposal with the recorded numbering.

Assignments in open majors and reopened unstarted majors may be realigned.
Superseded provisional splits, combinations, removals, and numbering are working state rather than work-number history, so update the authoritative records to the current provisional structure instead of preserving the superseded state.
Gaps in provisional major numbers or minor letters are allowed until finalization.
Once implementation actually starts in a finalized major, preserve its work numbers as history and reconcile later assignments around the recorded state.

## Replanning

When an implementation attempt in major `N` requires replanning, preserve the old work number with its earlier plan or attempt history.

Begin numbering replanned work at major `N+1`.

For replanned work placed in `N+1`, assign the next available minor letter.
For example, if `T4-A` already exists, assign the replanned work `T4-B`.

The surrounding planning workflow decides whether replanning also requires splitting or combining work.
After that work structure is decided, apply the major-number and minor-number rules starting from `N+1`.

The insertion may leave existing future plans semantically misaligned with their major numbers or dependencies.
Handle that downstream plan-number realignment in a separate follow-up pull request.

## Scope revisions

Keep the existing work number when the same viable work item receives an ordinary scope revision.

Use the replanning rule when the current implementation boundary is replaced by a new plan.

The surrounding planning context determines whether the revised plan still represents the same viable work item or a replacement.

## Responsibility boundary

This skill assigns work numbers, finalizes or reopens majors when permitted, and preserves numbering history once implementation begins.

The surrounding workflow supplies decisions about:

- work independence;
- parallelism;
- decomposition;
- splitting and combining work;
- dependencies;
- category definitions;
- implementation outcomes;
- whether implementation has actually started;
- whether any implementation remains to be done under a fixed work item;
- whether replacement work structure has been established when remaining implementation moves out of the fixed work item;
- merge prerequisites and whether their conditions are currently satisfied;
- the user's instruction to start, withdraw, or revise implementation of a major;
- the plan changes that trigger replanning.

## Output

Return assigned work numbers clearly and associate each number with its corresponding work item when multiple items are numbered.

When numbering changes create downstream inconsistencies in existing plans, also identify the need for a separate plan-number realignment pull request.
