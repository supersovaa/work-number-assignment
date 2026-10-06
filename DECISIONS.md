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

- Assignments in unstarted majors remain provisional.
- Provisional assignments may contain gaps in major numbers or minor letters while work is being split, combined, removed, or realigned.
- Superseded provisional structures and numbering are working state rather than numbering history and are replaced in the authoritative records.
- When the user instructs implementation to begin, first normalize that category's provisional assignments above the closed-through value from the latest work structure.
- Normalization removes avoidable major-number gaps, makes minor letters contiguous within each affected major, and applies freshly evaluated dependency and parallelism decisions from the surrounding workflow.
- For ordinary progression, the earliest resulting open major is eligible for finalization only after the preceding major in the same category is implementation-complete.
- Major `1` has no preceding-major prerequisite.
- A major is implementation-complete when its implementation succeeds.
- If a major fails and requires replacement work, it becomes implementation-complete only when the replacement plan, or the final plan in a replacement chain, completes successfully.
- The closed-through value records numbering finalization and does not itself establish implementation completion.
- Replacement work needed to complete a failed preceding major is recovery work and may be finalized while that predecessor remains implementation-incomplete.
- Recovery work is normalized with the other provisional assignments before finalization so current dependency and parallelism decisions determine the recovery major's membership.
- The implementation-start instruction then applies to the earliest resulting eligible open major and finalizes it.
- Closing the major advances the category's closed-through value and puts its work numbers into active use.

## Late discovery

- If an existing number is discovered while its major is still open, correct the proposed assignment.
- Once a major is closed for implementation, preserve its assigned numbers as history.
