# Work Number Assignment

A lightweight skill for assigning repository-defined work numbers such as `T1-A` and finalizing the earliest eligible unclosed major when the user starts implementation.

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

Each category records a monotonic closed-through major in the same authoritative records as the work-number assignments:

```text
T: closed through 3
```

Assignments in unstarted majors remain provisional.
Provisional assignments may contain gaps in major numbers or minor letters while work is being split, combined, removed, or realigned.
Superseded provisional structures and numbering are working state rather than numbering history, so the authoritative records are updated to the current provisional state instead of retaining the superseded state.

When the user instructs implementation to begin, first normalize that category's provisional assignments above the closed-through value from the latest work structure.
Remove avoidable gaps in major numbers, assign minor letters contiguously within each affected major, and use freshly evaluated dependency and parallelism decisions from the surrounding workflow to place dependent work in later open majors.

The next open major can be finalized only after the preceding major in the same category is complete.
Major `1` has no preceding-major prerequisite.
A major satisfies this predecessor-completion condition only when every work item fixed in that major has either completed implementation successfully or, after a failed implementation attempt, completed the replanning needed to establish its replacement work structure.
Replacement work may already have provisional work numbers in open majors before those majors are finalized.
The closed-through value does not itself mean work completion.

Then finalize the earliest resulting eligible open major and advance the category's closed-through value to that major.
Closing the major fixes its membership and puts its work numbers into active use before implementation begins.

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

The surrounding workflow determines independence, parallelism, decomposition, dependencies, category definitions, implementation outcomes, whether failed work has completed replanning and established its replacement work structure, and the plan changes that require replanning.

This skill assigns work numbers, finalizes a major on the user's implementation-start signal, records closed majors, and preserves finalized numbering history.

## Name

`work-number-assignment` is only a packaging name for this draft.
The behavior does not depend on the final published skill name.
