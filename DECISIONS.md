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
- Implementation outcomes, whether implementation has actually started, whether any implementation remains to be done under a fixed work item, and whether replacement work structure has been established when remaining implementation moves elsewhere are supplied by the surrounding workflow.
- Revising the scope of the same work item does not issue a new number.
- Determining whether something is still the same work item is not defined by this skill.

## Major finalization

- Assignments in unstarted open majors remain provisional.
- Provisional assignments may contain gaps in major numbers or minor letters while work is being split, combined, removed, or realigned.
- Superseded provisional structures and numbering are working state rather than numbering history and are replaced in the authoritative records.
- When the user instructs implementation to begin, first normalize that category's provisional assignments above the closed-through value from the latest work structure.
- Normalization removes avoidable major-number gaps, makes minor letters contiguous within each affected major, and applies freshly evaluated dependency and parallelism decisions from the surrounding workflow.
- The earliest resulting open major is eligible for finalization only after the preceding major in the same category is complete.
- Major `1` has no preceding-major prerequisite.
- A major satisfies the predecessor-completion condition when no implementation remains to be done under any work item fixed in that major.
- Successful implementation is not required for every fixed work item. No implementation remains when the work succeeded, when remaining implementation moved to replacement work after replanning, or when the work item was explicitly canceled or superseded before implementation began.
- If underlying work is still required, its replacement work structure must be established before the original fixed work item can be treated as having no remaining implementation.
- Disappearance from the active plan alone does not establish that no implementation remains.
- Replacement work may already have provisional work numbers in open majors while its structure is being established.
- The closed-through value records current numbering finalization and does not itself establish work completion.
- The implementation-start instruction then applies to the earliest resulting eligible open major and finalizes it.
- Finalization advances the category's closed-through value and fixes the major's membership for the pending implementation start.
- Finalization alone does not make the numbering irreversible.

## Reopening before implementation starts

- If implementation has not actually begun for any work item in the latest finalized major, the user may withdraw or revise the pending implementation and reopen that major.
- Reopening restores the category's previous closed-through value, or removes it when reopening major `1` and no earlier major is closed.
- Reopening returns that major's assignments to provisional state and allows normal provisional realignment again.
- The earlier instruction to begin implementation is not evidence that implementation actually started.
- Once implementation actually begins for any work item in a finalized major, preserve that major's membership and work numbers as irreversible history.
- Never roll the closed-through value back below a major whose implementation has actually started.

## Late discovery

- If an existing number is discovered before its major becomes irreversible through actual implementation, correct the proposed assignment.
- Once implementation actually starts in a finalized major, preserve its assigned numbers as history.
