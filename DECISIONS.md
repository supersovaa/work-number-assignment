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
- Multiple future work items can be numbered in one pass.
- If no existing number for a category is found, start at `<category>1-A`.
- Existing numbers are discovered from repository-defined instructions or documentation rather than a fixed path.

## Scope boundaries

- The skill may use an inferred parallel structure.
- The method for inferring independence or parallelism is out of scope.
- Work decomposition, dependency discovery, and category definition are out of scope.
- Revising the scope of the same work item does not issue a new number.
- Determining whether something is still the same work item is not defined by this skill.

## Late discovery

- If an existing number is discovered after a new number was proposed, correct the new number when it has not yet been put into actual use.
- Once a number is already in active use, do not silently change it.
