# Work Number Assignment

A lightweight skill for deciding when implementation work needs a numbered series, selecting or creating that series, retiring completed series, and assigning repository-defined work numbers such as `T1-A`.

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

Before numbering work, choose among an independent unnumbered one-off, a task in an existing active category, and a new category with a distinct multi-stage completion target. One-off changes can use a single PR and verification record; a more involved standalone task can use an unnumbered persistent plan. More specific repository planning requirements still apply.

A category is `active` while it accepts new numbered work and `retired` after its completion target has concluded and remaining work is resolved. Record retirement with the existing category definition and preserve all historical assignments. Existing categories without an explicit state remain active until classified. Work on a previously completed feature is classified from its current objective, not its old work number.

Each category records the highest currently finalized major in the same authoritative records as the work-number assignments:

```text
T: closed through 3
```

Assignments in unstarted open majors remain provisional.
Provisional assignments may contain gaps in major numbers or minor letters while work is being split, combined, removed, or realigned.
Superseded provisional structures and numbering are working state rather than numbering history, so the authoritative records are updated to the current provisional state instead of retaining the superseded state.

When the user instructs implementation to begin, first normalize that category's provisional assignments above the closed-through value from the latest work structure.
Remove avoidable gaps in major numbers, assign minor letters contiguously within each affected major, and use freshly evaluated implementation-dependency and parallelism decisions from the surrounding workflow to place dependent work in later open majors.

The next open major can be finalized only after the preceding major in the same category is complete.
Major `1` has no preceding-major prerequisite.
A major satisfies this predecessor-completion condition when no implementation remains to be done under any work item fixed in that major.
This is not the same as requiring every fixed work item to complete implementation successfully.
Implementation may be exhausted because it succeeded, because a failed attempt was replanned and remaining implementation moved to replacement work, or because the fixed work item was explicitly canceled or superseded before implementation began.
If underlying work is still required, its replacement work structure must already be established.
Disappearance from the active plan alone is not enough to show that no implementation remains.
Replacement work may already have provisional work numbers in open majors before those majors are finalized.
The closed-through value does not itself mean work completion.

Then finalize the earliest resulting eligible open major and advance the category's closed-through value to that major.
Finalization fixes membership for the pending implementation start, but it is not yet irreversible.

If implementation has not actually begun for any work item in the latest finalized major, the user may withdraw or revise the pending implementation and reopen that major.
Reopening restores the previous closed-through value, returns that major's assignments to provisional state, and allows normal realignment again.
The earlier instruction to begin implementation does not by itself prove that implementation actually started.

Once implementation actually begins for any work item in a finalized major, that major's membership and work numbers become irreversible history.
The closed-through value must never be rolled back below a major whose implementation has actually started.

An implementation dependency means that one work item requires another work item's established result before implementation can begin.

Within each category:

- numbering starts at major `1` when no prior numbers are found;
- parallel work may share the same open major;
- parallel items use `A`, `B`, `C`, ...;
- within the same category, plans added together use later majors when one has an implementation dependency on another plan in that same addition;
- later non-parallel stages use later majors;
- new work uses a major above the closed-through value;
- ordinary scope revisions keep the same number while the work item remains viable;
- replanning an active attempt preserves the old number as history and starts at the next major in that active series; later changes to completed features are classified as new work.

For example, replanning work in `T3` uses `T4`.
If `T4-A` already exists, the replanned work uses the next free minor such as `T4-B`.

Work decomposition remains a planning decision.
If another planning rule calls for splitting or combining work, numbering is applied after that structure is decided.

The insertion may leave existing future plans semantically misaligned with their major numbers or dependencies.
That downstream plan-number realignment is handled in a separate follow-up pull request.

## Deliberate non-goals

The surrounding workflow determines independence, parallelism, decomposition, implementation dependencies, the work's completion target, implementation outcomes, whether implementation has actually started, whether any implementation remains under a fixed work item, whether replacement work structure has been established when remaining implementation moves elsewhere, and the plan changes that require replanning.

This skill selects numbered or unnumbered tracking, assigns or retires work-number series, finalizes and reopens majors under the established conditions, and preserves numbering history once implementation begins.

## Installation

Install this repository's `SKILL.md` as the `work-number-assignment` skill using the target agent's skill loader. Make the working repository's category definitions and work-number records available to the agent through its ordinary repository access.
