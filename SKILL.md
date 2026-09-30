---
name: work-number-assignment
description: Assign repository-defined work numbers such as T1-A to upcoming work items. Use repository-defined categories and recorded work numbers, group parallel work under the same open major number, keep completed major numbers closed, distinguish concurrent items with minor letters, preserve an existing number for ordinary scope revision, and move replanned implementation work to a later major after reconsidering decomposition.
---

# Work Number Assignment

Assign work numbers to upcoming work items.

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

Use the repository-defined meaning of each category.

When the user asks for future work numbers in a category, such as `T`, use that repository-defined category.

Discover category definitions and the repository's work-number records from repository instructions or documentation.

## Major numbers

Major numbers are independent within each category.

Start from `1` when no existing work number for that category is found.

Work items that can proceed in parallel use the same open major number.

Work that belongs to a later non-parallel stage uses a later major number.

Treat a major number as closed once the repository records its work as completed or otherwise records that stage as complete.
Preserve closed major numbers as history and assign newly discovered work to a later major number.

This skill may rely on an inferred parallel structure; the surrounding workflow supplies the method used to infer work independence or parallelism.

## Minor numbers

Within the same major number, distinguish work items with uppercase letters in order:

```text
A
B
C
...
```

Assign multiple upcoming work items together when needed.

Example:

```text
T1-A
T1-B
T2-A
```

## Existing work numbers

Use the repository's defined work-number records, including completion state when available, to determine existing numbers.

Continue within an existing major only while that major is still open and the new work belongs to the same parallel stage.
Otherwise, use the next suitable later major number.

If no existing number is found, start from:

```text
<category>1-A
```

If an existing number is discovered after a new number was proposed, correct the new number when it has not yet been put into actual use.

If the proposed number is already in active use, preserve it and assign subsequent work around the recorded state.

## Replanned implementation work

When implementation cannot complete within the current work item's boundary, reconsider whether the remaining work should be decomposed before assigning replacement numbers.

Preserve the original work number as the record of that attempt.
Assign replacement work starting at least one major later than the original work, using the next available later major when necessary.

After decomposition is decided, apply the normal major/minor rules to the replacement items according to their parallel and dependency structure.

Example:

```text
T3-A   original attempt
T4-A   first replacement item
T4-B   parallel replacement item
T5-A   dependent replacement item
```

## Scope revisions

If the scope of the same work item is revised while the work item remains viable, keep its existing work number.

When implementation failure leads to replanning or decomposition, use the replanned implementation rule instead.

Whether two descriptions still represent the same work item comes from the surrounding planning context.

## Out of scope

This skill assigns numbers from an available work structure.
The surrounding workflow determines:

- how work independence is determined;
- how parallelism is inferred;
- how work is decomposed;
- whether two work items should be split or combined;
- how dependencies are discovered;
- how categories are chosen or defined.

## Output

Return the assigned work numbers clearly and associate each number with its corresponding work item when multiple items are numbered.
