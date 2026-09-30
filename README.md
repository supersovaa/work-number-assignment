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

Within each category:

- numbering starts at major `1` when no prior numbers are found;
- work that can proceed in parallel shares the same open major number;
- parallel work items are distinguished with `A`, `B`, `C`, ...;
- later non-parallel stages use later major numbers;
- completed major numbers remain closed as history;
- newly discovered work uses an open current major or a later major;
- multiple future work items may be numbered together;
- an ordinary scope revision to the same viable work item keeps the existing number;
- implementation work that requires replanning or decomposition keeps the original number as history and starts replacement work at least one major later.

When implementation cannot complete within the current work boundary, the skill first sends the remaining work back for decomposition consideration.
After the replacement work structure is decided, numbering follows the usual parallel and dependency rules.

For example, a failed `T3-A` attempt may produce parallel replacement items `T4-A` and `T4-B`, followed by dependent `T5-A`.

The skill uses repository instructions or documentation to find category definitions, recorded work numbers, and completion state.
It does not require a fixed file or path.

## Deliberate non-goals

The surrounding workflow determines independence, parallelism, work decomposition, dependency discovery, and category definitions.

This skill assigns work numbers from that available work structure and preserves numbering history.

## Name

`work-number-assignment` is only a packaging name for this draft.
The behavior does not depend on the final published skill name.
