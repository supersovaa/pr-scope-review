---
name: pr-scope-review
description: Review a pull request without letting related pre-existing problems expand its scope; classify required fixes as current-PR, separate-PR, or follow-up work, and identify prerequisite dependencies without taking over PR execution.
---

# PR Scope Review

Use this skill when reviewing a pull request and related existing problems may tempt the review to expand the PR beyond its purpose.

It is especially useful for documentation changes, but applies to pull request review in general.

## Core rule

Judge a proposed fix by whether it is required for the current PR to fulfill its purpose.

Do not include a fix in the current PR merely because:

- it is closely related;
- it is nearby in the same document or code;
- it concerns the same concept;
- it would be convenient to fix at the same time.

Keep the current PR limited to changes required for its stated purpose and internal correctness.

## Classify review findings

For every finding that requires a change, classify it as one of:

- `Fix in current PR`
- `Fix in separate PR`
- `Record as follow-up`

Use `Fix in current PR` only when the fix is required for the current PR to fulfill its purpose or remain internally correct.

Use `Fix in separate PR` when the issue is outside the current PR's purpose and a concrete independent fix already exists or can be cleanly separated as a coherent change.

Use `Record as follow-up` when the issue is outside the current PR's purpose and no separate fix needs to be created as part of the current review.

Make the classification explicit in the review result.

## Remove scope creep already present

Apply the same boundary to changes that are already in the PR.

If a change is not required for the PR's purpose, classify it as out of scope and require the current PR not to include it, even if it is small, relevant, or already implemented.

Preserve useful work by classifying it for a separate PR when appropriate instead of leaving it mixed into the current PR.

## Separate PRs

A separate PR should have one coherent purpose of its own.

Multiple out-of-scope fixes may share a separate PR only when they can naturally be explained as one change with one purpose.

Do not group unrelated fixes merely because they were discovered during the same review.

Apply this skill recursively when reviewing a separate PR. If that PR contains another independent change, classify that change separately again.

## Prerequisite PRs

When an out-of-scope fix is a prerequisite cleanup or correction that should be applied before the current PR can be accepted, classify it as `Fix in separate PR` and record the dependency explicitly.

Continue the current review cycle through its full effective review scope after discovering the prerequisite. Do not stop the review merely because a prerequisite PR is needed.

The current PR must not be accepted until the prerequisite PR has been merged, the current PR has been updated to the latest base, and any required re-review has been completed.

Creating, editing, completing, or merging the separate PR, and updating the current branch, are responsibilities of the surrounding workflow rather than this skill.

Dependency on the current work is not by itself a reason to keep both changes in one PR.

If an out-of-scope issue does not affect the current PR's validity, record or classify it without blocking acceptance of the current PR.

## Do not widen the search

Review enough surrounding context to determine whether the current PR is correct.

This rule does not narrow the review scope required to judge the current PR's correctness. Continue through the full effective review scope, including required canonical sources and relevant comparisons, even after finding an out-of-scope or prerequisite issue.

When an unrelated or out-of-scope existing problem is discovered, do not use that problem as a reason to broaden the review into a larger audit.

Record the problem as follow-up work when appropriate, then continue reviewing the current PR against its own purpose.

## Review output

For each finding that requires a change, state:

1. the problem;
2. why it matters to the reviewed change;
3. one of `Fix in current PR`, `Fix in separate PR`, or `Record as follow-up`.

When a separate PR is a prerequisite, state the dependency and the acceptance condition explicitly. Complete the current review cycle before reporting, but do not accept the current PR until the prerequisite has been merged, the current PR has been updated to the latest base, and any required re-review has been completed.
