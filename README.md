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
- work that can proceed in parallel shares the same major number;
- parallel work items are distinguished with `A`, `B`, `C`, ...;
- later non-parallel stages use later major numbers;
- multiple future work items may be numbered together;
- a scope revision to the same work item keeps the existing number.

The skill uses repository instructions or documentation to find category definitions and recorded work numbers. It does not require a fixed file or path.

## Deliberate non-goals

The skill does not prescribe how to determine independence, parallelism, work decomposition, dependency discovery, or category definitions.

Its responsibility is limited to assigning work numbers from the available work structure and repository conventions.

## Name

`work-number-assignment` is only a packaging name for this draft. The behavior does not depend on the final published skill name.
