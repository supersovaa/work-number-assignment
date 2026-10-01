# Work Number Assignment

A lightweight skill for assigning repository-defined work numbers such as `T1-A` to implementation work.

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

As part of the planning change that sends work in a major into implementation, that major becomes closed to newly assigned work.
Already assigned work numbers in that major remain valid.

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

The surrounding workflow determines independence, parallelism, decomposition, dependencies, category definitions, and the plan changes that require replanning.

This skill assigns work numbers, records closed majors as part of implementation planning, and preserves numbering history.

## Name

`work-number-assignment` is only a packaging name for this draft.
The behavior does not depend on the final published skill name.
