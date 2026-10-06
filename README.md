# Work Number Assignment

A lightweight skill for assigning repository-defined work numbers such as `T1-A`, finalizing the earliest eligible open major when the user starts implementation, and reopening that finalization while implementation has not actually started.

## Behavior

Work numbers use this form:

```text
<category><major>-<minor>
```

Example:

```text
T1-A
T1-B
T2-A
```

The repository defines category prefixes such as `T`.
The skill uses only repository-defined category meanings and discovers the work-number records through repository conventions without assuming a fixed file or path.

Each category records the highest currently finalized major in the same authoritative records as the work-number assignments:

```text
T: closed through 3
```

Assignments in unstarted open majors remain provisional.
Provisional assignments may contain gaps in major numbers or minor letters while work is being split, combined, removed, or realigned.
Superseded provisional structures and numbering are working state rather than numbering history, so the authoritative records are updated to the current provisional state instead of retaining the superseded state.

When the user instructs implementation to begin, first normalize that category's provisional assignments above the closed-through value from the latest work structure.
Remove avoidable gaps in major numbers, assign minor letters contiguously within each affected major, and use freshly evaluated dependency and parallelism decisions from the surrounding workflow to place dependent work in later open majors.

The next open major can be finalized only after the preceding major in the same category is complete.
Major `1` has no preceding-major prerequisite.
A major satisfies this predecessor-completion condition only when every work item whose numbering became irreversible in that major has either completed implementation successfully or, after a failed implementation attempt, completed the replanning needed to establish its replacement work structure.
Replacement work may already have provisional work numbers in open majors before those majors are finalized.
The closed-through value does not itself mean work completion.

Then finalize the earliest resulting eligible open major and advance the category's closed-through value to that major.
Finalization fixes membership for the pending implementation start, but it is not yet irreversible.

If implementation has not actually begun for any work item in the latest finalized major, the user may withdraw or revise the pending implementation and reopen that major.
Reopening restores the previous closed-through value, returns that major's assignments to provisional state, and allows normal realignment again.
The earlier instruction to begin implementation does not by itself prove that implementation actually started.

Once implementation actually begins for any work item in a finalized major, that major's membership and work numbers become irreversible history.
The closed-through value must never be rolled back below a major whose implementation has actually started.

Within each category:

- numbering starts at major `1` when no prior numbers are found;
- parallel work may share the same open major;
- parallel items use `A`, `B`, `C`, ...;
- within the same category, plans added together use later majors when one depends on another plan in that same addition;
- later non-parallel stages use later majors;
- new work uses a major above the closed-through value;
- ordinary scope revisions keep the same number while the work item remains viable;
- replanned work preserves the old number as history and starts at the next major.

For example, replanning work in `T3` uses `T4`.
If `T4-A` already exists, the replanned work uses the next free minor such as `T4-B`.

Work decomposition remains a planning decision.
If another planning rule calls for splitting or combining work, numbering is applied after that structure is decided.

The insertion may leave existing future plans semantically misaligned with their major numbers or dependencies.
That downstream plan-number realignment is handled in a separate follow-up pull request.

## Deliberate non-goals

The surrounding workflow determines independence, parallelism, decomposition, dependencies, category definitions, implementation outcomes, whether implementation has actually started, whether failed work has completed replanning and established its replacement work structure, and the plan changes that require replanning.

This skill assigns work numbers, finalizes a major on the user's implementation-start signal, allows that finalization to be reopened before actual implementation starts, records the current closed-through major, and preserves numbering history once implementation begins.

## Name

`work-number-assignment` is only a packaging name for this draft.
The behavior does not depend on the final published skill name.
