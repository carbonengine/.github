# Contributing to the Carbon Development Platform

Welcome, and thanks for considering a contribution to the Carbon Development Platform, the technology behind EVE Online and EVE Frontier. We're open-sourcing it piece by piece, so this guide will keep evolving. Use your best judgement, and feel free to suggest changes to it in a PR.

## TL;DR

- Read the repo's README first for build and setup steps. Not every repo is buildable *yet* (see Developer environment).
- Bug fixes and small improvements are welcome. For anything large, open an issue first (see What we accept).
- Keep commits small and scoped. (~300 lines is a good target for a fast review, but not a hard rule, larger is fine if the change is atomic.)
- On your first PR the CLA bot posts a link to sign. Sign once and it covers every carbonengine repo.
- Builds run on our internal CI, a maintainer usually kicks it off after an initial review, and you'll see status checks on your PR.

This is the canonical contribution guide for every repo under https://github.com/carbonengine. Individual repos may add a local CONTRIBUTING.md that extends this one for component-specific details (build commands, test runner, extra labels). A repo-local file should be short and link back here.

*A note on terms: throughout this guide, **"maintainers"** means the FC engineers who own a given repository (its code owners). You can reach them through that repo's maintainers team.*

## What we accept (scope)

Carbon Engine backs live games, and we steer its direction. Contributions are genuinely welcome, within that reality:

- **Welcome:** bug fixes, small improvements, documentation, and fixes to things that are clearly broken.
- **Discuss first:** anything large or structural (new features, refactors, API changes). Open an issue before you write the code, so we can tell you whether it fits our development plans before you invest time.
- **What to expect:** the roadmap is largely driven by our needs and the games we ship. A well-made contribution can still be declined if it doesn't fit that direction. If we close something as `out-of-scope`, please understand that it's not a comment on the quality of your work and we truly appreciate your contributions regardless.

### Ground rules

- Open an issue for any large or structural change before starting. Discuss it openly.
- Be welcoming, kind, inclusive, and professional.

## Code of conduct

See the [Carbon Code of Conduct](https://github.com/carbonengine/.github/blob/main/CODE_OF_CONDUCT.md). Reports of unacceptable behaviour can be sent confidentially to opensource@fenris.com.

## Not interested in any of this, I just have a question!

Please open an issue on the relevant repo if you have a question. Questions are more than welcome, and we are working towards setting up public questions spaces, but we're not all the way there yet. We're working towards enabling GitHub Discussions and creating a dedicated Discord server. Until then, if you still need help, either open an issue or email us at opensource@fenris.com.

## Developer environment

Carbon can't be built as a single package yet. It's currently a set of independent repos, each built and tested on its own, so there is no single set of build instructions. Each repo's README is the source of truth for its build and testing instructions.

A note on the current state: not every repo can be built from an external checkout yet. Some depend on proprietary third-party SDKs we can't distribute, and some rely on internal libraries or changes that aren't public yet. We're still working through things, and this will improve over time. If a repo you want to work on isn't buildable yet, its README should say so. Open an issue if anything is unclear or if you think the README has wrong or outdated information.

Generally, the minimum required development environment is:

- Git with SSH access to GitHub. Clone with `--recurse-submodules` (dependencies come in as submodules).
- CMake 3.31 or newer.
- A C++17 capable compiler. Take note that on Windows we are primarily testing with the v141 toolset. The exact toolset version varies by component, which should be mentioned in the relevant component's README.

Dependencies are handled through vcpkg: each repo vendors it as a submodule wired to the Carbon vcpkg registry, and the build pulls the public third-party packages it needs. Anything that can't be distributed, like proprietary SDKs or internal libraries, should be called out in that repo's README.

## How to contribute

1. Check existing issues, or open a new one to discuss a bug, idea, or doc improvement. For anything large, see "What we accept" above and open an issue first.
2. Fork the repo you want to change (https://github.com/carbonengine/*).
3. Create a descriptively named branch off the default branch (usually `main`).
4. Work in small, scoped commits. (Docs-only edits can be any size.)
5. Sign our CLA. On your first PR the CLA bot posts a link. You sign once, and it covers all future contributions to every carbonengine repo. The bot blocks merge until your signature is on file.
   - Contributing on your personal time, no employer claim to your code: sign the **ICLA** (Individual CLA).
   - Your employment contract gives your employer ownership of code you write (most full-time contracts do, even off-hours): your employer signs the **CCLA** (Corporate CLA) once, and you must be listed under it.
6. Open a pull request against the matching `main` branch.

## Reporting a bug

If you find a security vulnerability, **do not file a public issue**. See our [Security Policy](https://github.com/carbonengine/.github/blob/main/SECURITY.md) for the disclosure process.

A good litmus test to determine if you are dealing with a security issue, ask:

- Can I disable something for other people?
- Can I access something that I shouldn't have access to?

If you find yourself answering "yes" to either of these, then you are most likely dealing with a security vulnerability. However, it is very possible that even if you answer "no" to both questions, you may still be dealing with a security vulnerability, so if you're unsure just email us at opensource@fenris.com.

For any other bug, please create an issue using the [Bug Report](https://github.com/carbonengine/.github/blob/main/.github/ISSUE_TEMPLATE/bug_report.yml) template. Please search existing issues before filing a new one and include repro steps and system info when reporting bugs.

## AI assistance

AI tools are welcome here, we use them too when it makes sense. What matters to us isn't whether you used AI, it's whether the contribution is something you understand and can stand behind. Three principles (that we as FC abide by as well) guide how we'd like you to use AI when contributing.

### 1. Be accountable

You're responsible for what you submit, whatever tools you used to produce it. If a change is broken, you'll be asked to fix it. If an AI output doesn't meet your own standard, or you can't understand or explain it, please don't put it in a contribution.

### 2. Apply scrutiny

AI tools make mistakes: errors, hallucinations, and confident-sounding nonsense. Treat their output as a draft to check, not an answer to trust. Before you submit, make sure:

- it builds, and the tests run and pass
- you've read and understood every change, and can explain why it's there
- any APIs, functions, or facts it relied on are real and behave the way the code assumes
- it actually solves the problem, not just something that looks like it does

### 3. Be transparent

If AI generated or significantly assisted part of your contribution, tell us. The PR template has a field for it. Honest disclosure is never held against you, it just helps reviewers give your work the right kind of attention.

This is the same bar we hold ourselves to, and we value a few good contributions over a flood of unverified output. Note that AI-generated security reports are not accepted unless a human has verified the issue and can reproduce it from a clean clone (see [SECURITY.md](https://github.com/carbonengine/.github/blob/main/SECURITY.md)).

## Pull requests

To have your contribution considered:

1. Follow the PR template.
2. Follow the repo's formatter/linter config where it provides one (see Quality standards).
3. Each PR should be one logical change.
4. Update docs and CHANGELOG.md where relevant (skip if the repo has no CHANGELOG yet).

Note: builds and tests run on FC's internal CI. Status is posted back to your PR as commit status checks. On most repos a maintainer triggers the build after an initial review. If your PR sits with no status for more than a few working days, comment on the PR (the maintainers are subscribed and will be notified), or @-mention the maintainers team shown in its reviewers.

### Git commits

Follow the seven rules from Chris Beams' guide ([cbea.ms/git-commit](https://cbea.ms/git-commit)):

1. Separate subject from body with a blank line.
2. Limit the subject line to 50 characters.
3. Capitalize the subject line.
4. Don't end the subject line with a period.
5. Use the imperative mood ("Add", "Fix", "Remove").
6. Wrap the body at 72 characters.
7. Use the body to explain what and why, not how.

**Good**

```
Fix crash when no render target is bound

When the debug scene flag is enabled `activeRT` may be unset, leading
to a segfault in Resolve(). This adds a null-check and a unit test.
```

**Bad**

```
fixed crash when no render target is bound. added some checks and tests
```

### Quality standards

**Coding standards**

Coding conventions (header self-containment, namespace hierarchy, naming, and API documentation) live in the [Carbon coding guidelines](https://carbonengine.github.io/documentation/), please follow those. Where a repo has a formatter or linter config (for example `.clang-format` for C++), that config is the source of truth for formatting.

**Testing**

Test commands and frameworks vary by component; the repo's README should list the exact steps. As a rule of thumb: add at least one regression test when you fix a bug or add a feature, run the component's tests locally before marking your PR ready for review, and update performance or visual tests if applicable.

**Documentation**

Update inline API comments and docstrings when you change behaviour. Add or edit files under `docs/` for design notes. Pure documentation improvements are always welcome, no code required.

### Issue and PR labels

These are the common labels. Individual repos may add component-specific ones.

**Issue labels**

| Label | Meaning |
| --- | --- |
| `bug` | Confirmed bugs, or reports likely to be bugs |
| `enhancement` | A small improvement we'd accept |
| `documentation` | Documentation issues or changes |
| `good first issue` | Small, self-contained tasks suitable for newcomers (applied by maintainers) |
| `help wanted` | Something we'd welcome a contributor picking up |
| `question` | A question that should move to email rather than stay an issue |
| `duplicate` | Duplicate of another issue |
| `invalid` | Not a valid issue (for example, user error) |
| `out-of-scope` | A valid request that doesn't fit the project's direction |

**Pull requests**

We rely on GitHub's built-in PR states rather than manual status labels. Open a draft PR while it's still in progress, and mark it ready for review when it's done. Review status (review requested, changes requested, approved) is tracked by GitHub directly.

## Licensing

Each repository states its own license in its root, and the choice is made per repo. By contributing to a repository you agree to license your work under that repository's license and confirm you have the right to do so (including any employer approval). Third-party code or assets must keep their original license headers and be compatible with the repository's license.

## Response expectations

We aim to acknowledge new issues and PRs as soon as we reasonably can. We're early in the open-source roll-out, so some things may be slower for now while we settle the public process. If a PR has been quiet for more than a few working days, comment on the PR (the maintainers are subscribed), or @-mention the maintainers team shown in its reviewers.

## Need help?

- **Issues:** bug reports.
- **Email:** opensource@fenris.com for private matters.
- **Security:** see [SECURITY.md](https://github.com/carbonengine/.github/blob/main/SECURITY.md).

*These guidelines will grow as more of the engine becomes public. Thank you for helping us build an awesome open-source engine!*
