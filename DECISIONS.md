# Decided Specification

## Format

- Work number: `<category><major>-<minor>`
- Example: `T1-A`
- Category definitions belong to the repository.
- Major numbers are independent per category.
- Minor numbers use `A`, `B`, `C`, ... in order.

## Assignment model

- Parallel work uses the same major number.
- Parallel siblings use different minor letters.
- Within the same category, when multiple plans are added together, each plan that depends on another plan in that same addition uses a later major number than that dependency.
- Multiple future work items can be numbered in one pass.
- If no existing number for a category is found, start at `<category>1-A`.
- Existing numbers are discovered from repository-defined instructions or documentation rather than a fixed path.

## Scope boundaries

- The skill may use an inferred parallel structure.
- The method for inferring independence or parallelism is out of scope.
- Work decomposition, dependency discovery, and category definition are out of scope.
- Revising the scope of the same work item does not issue a new number.
- Determining whether something is still the same work item is not defined by this skill.

## Major finalization

- Assignments in an unstarted major remain provisional.
- Finalize majors strictly in ascending order within each category.
- A user implementation-start instruction triggers finalization only for the major exactly one greater than the category's closed-through value.
- When the user names a later major, keep it provisional and identify the next eligible major.
- Before closing that major, reconcile its assignments against dependency and parallelism decisions freshly evaluated by the surrounding workflow from the latest repository state.
- Work that depends on another item in the same major moves to a later open major under the normal numbering rules.
- After reconciliation, advance the category's closed-through value by exactly one to that major.
- Closing the major is the point at which its work numbers enter active use.

## Late discovery

- If an existing number is discovered while its major is still open, correct the proposed assignment.
- Once a major is closed for implementation, preserve its assigned numbers as history.
