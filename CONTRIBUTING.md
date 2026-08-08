# Contributing to OpenPowertrain

## Project status

OpenPowertrain is still fully experimental and pre-alpha. APIs, module boundaries and even some engineering assumptions
can change without notice. Contributions are welcome, but keep that instability in mind. It's worth checking open issues
or discussions before putting real time into a change.

## Before you start

For anything that isn't trivial, open an issue or a discussion first. Small stuff like typos, docs or obvious bugs can
go straight to a pull request.

## Branching model

The project follows the classic Git branching model, often called GitFlow.

**main** always reflects the latest released version. It only receives merges from `release/*` or `hotfix/*` branches,
and every merge into `main` gets tagged (`vX.Y.Z`).

**develop** is the integration branch for ongoing work. All feature branches merge here first.

**feature/<short-description>** branches off `develop` and merges back into `develop` through a PR.

**release/<version>** branches off `develop` when preparing a release. Only bug fixes and release-prep changes
(changelog, version bump) happen here, and it merges into both `main` (tagged) and back into `develop`.

**hotfix/<short-description>** branches off `main` for urgent fixes to a released version, and merges into both `main`
(tagged) and `develop`.

While the project is pre-release (no `v1.0.0` yet) most work happens directly against `develop` through `feature/*`
branches. `release/*` and `hotfix/*` only come into play once there's a first tagged version.

## Developer Certificate of Origin (DCO)

Every commit needs to be signed off to certify you have the right to submit the contribution under the project's license
(Apache 2.0):

```bash
git commit -s -m "your commit message"
```

That adds a `Signed-off-by` trailer with your name and email. PRs with unsigned commits won't get merged.

### DCO alone doesn't prove authorship. Commit signing does.

The `Signed-off-by` trailer is a legal certification, not cryptographic proof. Nothing technically stops someone from
typing another person's name and email into a signed-off commit. That's a known and accepted limitation of the DCO model
(it's the same one the Linux kernel uses). It answers the licensing question, not the "who actually wrote this"
question.

To close that gap, commits should also be cryptographically signed, either with GPG or SSH. GitHub verifies SSH-signed
commits against the public key registered on your account, and it's been natively supported since Git 2.34, so you don't
need a separate GPG key if you already use SSH to push:

```bash
git config --global gpg.format ssh
git config --global user.signingkey ~/.ssh/id_ed25519.pub
git config --global commit.gpgsign true
```

Once that's configured, every commit is both signed off (the legal certification) and cryptographically signed (proof of
who actually wrote it) automatically. DCO and signing solve two different problems, and neither replaces the other.

This isn't enforced at the branch protection level yet, to keep the barrier low while the project is solo and early
stage. Once there's more than one regular contributor, `main` and `develop` will require verified signatures through
GitHub branch protection rules.

## AI-generated code

There are two reasons contributions here shouldn't be AI-generated.

The first is the point of the project itself. OpenPowertrain exists partly as a way to actually learn Go and powertrain
engineering by building something real. Code that was generated rather than written and understood defeats that, both
for whoever submitted it and for anyone reading it later to learn from.

The second connects directly to the DCO section above. Signing off on a commit certifies you created the contribution
and have the right to license it under Apache 2.0. That's a hard thing to honestly certify about code an AI wrote for
you, since there's no reliable way to know it's free of memorized copyrighted or proprietary training data, and in some
jurisdictions AI output isn't even considered a copyrightable work without meaningful human authorship, which raises the
question of who's actually certifying what. A number of established projects, including GCC, QEMU, Git and NetBSD, have
adopted similar restrictions for this exact reason, and it's worth reading their reasoning if you want the full
background.

In practice: use whatever tools help you learn, debug or research, an AI explaining a concept or pointing you toward a
bug is fine. What you submit should be code you wrote and understand well enough to explain and defend during review.
Pull requests that read like unreviewed AI output get rejected regardless of whether a tool was involved. This is
enforced on trust rather than any detection tool, so it only works if contributors take the DCO sign-off seriously.

## Coding conventions

Go code needs to pass `gofmt` and `go vet` before review. Favor small, composable packages (`engine/`, `physics/`,
`simulation/` and so on) that can each be used independently of any front end. Public APIs need godoc comments, and
anything modeling a non-obvious physical or mathematical relationship needs a comment citing the source, something like
"Otto cycle efficiency, Brunetti Vol. 1". Keep CGO out of the core simulation packages so they stay portable and
importable in server-side contexts. Anything that needs CGO, like GUI code or hardware drivers, stays isolated in its
own package.

## Pull requests

Fork and branch off `develop`, following the branching model above. Keep PRs focused on one logical change. Include or
update tests for anything touching `engine/`, `physics/`, `simulation/` or `vehicle/`. Reference the related issue in
the PR description.

## Reporting issues

Use GitHub Issues. For bugs, include your Go version, OS and minimal reproduction steps. For proposals, explain the
engineering motivation and point to a reference if there's one that applies.

## Conduct

Be respectful and professional in every project space. A formal Code of Conduct will get added as the contributor base
grows.

## License of contributions

By contributing, you agree your contributions are licensed under the project's Apache License 2.0 for code, or CC BY 4.0
for documentation, consistent with the DCO sign-off above.

## A note on the future

If OpenPowertrain ever moves past the experimental phase and gets accepted into, or adopts, an existing open source
foundation's governance model, contribution requirements (like a formal contributor agreement replacing the DCO) might
get updated to match that foundation's process. This document will be revised if and when that happens.
