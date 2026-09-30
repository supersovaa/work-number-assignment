---
name: work-number-assignment
description: Assign repository-defined work numbers such as T1-A to upcoming work items. Use repository-defined categories, a per-category closed-through major, parallel-stage grouping, and later numbering for replanned work while preserving prior numbering history.
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

Discover category definitions and work-number records from repository instructions or documentation.

## Closed-through major

Record the highest closed major for each category.

Example:

```text
T: closed through 3
D: closed through 5
```

A closed-through value is monotonic.
Every major at or below that value is closed to newly assigned work.

Already assigned work numbers remain valid identifiers after their major becomes closed.

When implementation begins for work in major `N`, advance that category's closed-through value to at least `N`.

This closes the membership of that major when implementation starts, while preserving all work that was already assigned to it.

## Major numbers

Major numbers are independent within each category.

Start from `1` when the category has no existing work number.

Work items that can proceed in parallel may share the same open major number.

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

## Replanning

When an implementation attempt requires replanning, preserve the old work number with its earlier plan or attempt history.

Assign the replanned work a later major number above the original major and above the category's closed-through value.

The surrounding planning workflow decides whether replanning also requires splitting or combining work.
After that work structure is decided, apply the normal major/minor rules.

A shifted work number can invalidate the ordering or numbering of already planned future work.
Handle that broader plan-number realignment in a separate follow-up pull request so the replanning change and the downstream reorganization remain distinct.

## Scope revisions

Keep the existing work number when the same viable work item receives an ordinary scope revision.

Use the replanning rule when the current implementation boundary is replaced by a new plan.

The surrounding planning context determines whether the revised plan still represents the same viable work item or a replacement.

## Responsibility boundary

This skill assigns and closes work numbers from an available work structure.

The surrounding workflow supplies decisions about:

- work independence;
- parallelism;
- decomposition;
- splitting and combining work;
- dependencies;
- category definitions;
- when implementation has begun;
- the plan changes that trigger replanning.

## Output

Return assigned work numbers clearly and associate each number with its corresponding work item when multiple items are numbered.

When numbering changes create downstream inconsistencies in existing plans, also identify the need for a separate plan-number realignment pull request.
