# Work Number Assignment

A lightweight skill for assigning repository-defined work numbers such as `T1-A`.

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

Each category records a monotonic closed-through major, for example:

```text
T: closed through 3
```

When implementation begins for work in a major, that major becomes closed to newly assigned work.
Already assigned work numbers in that major remain valid.

Within each category:

- numbering starts at major `1` when no prior numbers are found;
- parallel work may share the same open major;
- parallel items use `A`, `B`, `C`, ...;
- later non-parallel stages use later majors;
- new work uses a major above the closed-through value;
- ordinary scope revisions keep the same number while the work item remains viable;
- replanned work preserves the old number as history and receives a later major.

Work decomposition remains a planning decision.
If another planning rule calls for splitting or combining work during replanning, numbering is applied after that structure is decided.

Renumbering replanned work can make existing future plans inconsistent.
That broader plan-number realignment is handled in a separate follow-up pull request.

The skill uses repository instructions or documentation to find category definitions, work-number records, and the closed-through values.
It does not require a fixed file or path.

## Deliberate non-goals

The surrounding workflow determines independence, parallelism, decomposition, dependencies, category definitions, and the plan changes that require replanning.

This skill assigns work numbers, closes majors when implementation begins, and preserves numbering history.

## Name

`work-number-assignment` is only a packaging name for this draft.
The behavior does not depend on the final published skill name.
