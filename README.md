# pr-scope-review

`pr-scope-review` is a lightweight ChatGPT-oriented skill for keeping pull request review aligned with the PR's actual purpose.

It is aimed especially at documentation PRs, where review often uncovers nearby or related pre-existing problems that are tempting to fix at the same time.

## Core rule

A related problem belongs in the current PR only when fixing it is required for the current PR to fulfill its purpose or remain internally correct.

Related, nearby, convenient, or conceptually similar work is not automatically in scope.

## Review classifications

Every finding that requires a change is classified as one of:

- `Fix in current PR`
- `Fix in separate PR`
- `Record as follow-up`

This makes the scope decision explicit instead of leaving it implicit in the review text.

## Scope creep already in the PR

The same rule applies to changes that have already been added.

If an existing change is outside the PR's purpose, the review requires it to be removed from the current PR. If it already forms a useful independent change, the review classifies it for a separate PR.

## Separate PRs

Separate fixes are grouped only when they share one coherent purpose.

A separate PR is reviewed under the same rule, so splitting one PR does not simply move the same scope creep into another PR.

## Prerequisite fixes

Sometimes review finds an existing problem that should be corrected before the current PR.

In that case, the review records the separate PR as a prerequisite acceptance condition. The current review cycle still continues through its full effective scope instead of stopping at the first prerequisite finding.

The current PR is not accepted until the prerequisite PR is merged, the current PR is updated to the latest base, and any required re-review is complete. Creating, merging, and updating PRs remain responsibilities of the surrounding workflow.

If the out-of-scope issue does not affect the current PR's validity, it does not block acceptance of the current PR.

## Review breadth

Discovering an out-of-scope problem does not justify expanding the review into a broader audit.

This does not narrow the scope needed to judge the current PR correctly. The reviewer still completes the effective review scope, including required canonical sources and relevant comparisons, records unrelated problems when useful, and keeps the review focused on the PR's purpose.
