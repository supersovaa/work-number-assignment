---
name: work-number-assignment
description: Assign repository-defined work numbers such as T1-A to upcoming work items. Use repository-defined categories and recorded work numbers, group parallel work under the same major number, distinguish concurrent items with minor letters, and preserve an existing number when only the scope of the same work item is revised. Do not define how parallelism or work independence must be inferred.
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

Do not invent category meanings in this skill.

When the user asks for future work numbers in a category, such as `T`, use that repository-defined category.

Discover category definitions and the repository's work-number records from repository instructions or documentation. Do not require a fixed filename or path.

## Major numbers

Major numbers are independent within each category.

Start from `1` when no existing work number for that category is found.

Work items that can proceed in parallel use the same major number.

Work that belongs to a later non-parallel stage uses a later major number.

This skill may rely on an inferred parallel structure, but it does not define or validate the method used to infer work independence or parallelism.

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

Use the repository's defined work-number records to determine existing numbers.

Normally continue from the existing numbering for the category.

If no existing number is found, start from:

```text
<category>1-A
```

If an existing number is discovered after a new number was proposed, correct the new number when it has not yet been put into actual use.

If the proposed number is already in active use, do not silently renumber it.

## Scope revisions

If the scope of the same work item is revised, keep its existing work number.

Do not issue a new work number merely because the work item's scope changed.

Whether two descriptions still represent the same work item is outside this skill's decision procedure.

## Out of scope

This skill does not define or validate:

- how work independence is determined;
- how parallelism is inferred;
- how work is decomposed;
- whether two work items should be split or combined;
- how dependencies are discovered;
- how categories are chosen or defined.

Those decisions may come from repository conventions, the surrounding workflow, the user, or another skill.

## Output

Return the assigned work numbers clearly and associate each number with its corresponding work item when multiple items are numbered.
