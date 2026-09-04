# Contributing to CleanroomMC

Thank you for contributing to our project!

Build, format, and release rules are enforced by [CleanroomMC/Convention](https://github.com/CleanroomMC/Convention).

## Ground Rules

- Default branch is `master`.
- Squash merges only. The pull request title becomes the commit on `master`.
- Do not vendor or hand-edit convention files (`LICENSE`, `HEADER`,
  `checkstyle.xml`, `formatj.toml`, `cliff.toml`, `.editorconfig`,
  `.gitattributes`, `.gitignore`). Change them in the Convention repository
  and bump the plugin version instead.
- Security reports are not regular issues. See [SECURITY.md](SECURITY.md).

## Language

Use US English everywhere: prose, code, identifiers, comments, and Javadoc.
- US spelling
- Write clearly and concisely
- Prefer the imperative present tense for commits: add, not added/adds
- Identifiers and file names stay in English. Prefer full words over abbreviations: `configuration` over `cfg`, `message` over `msg`

## Commits and Pull Requests

Commits and pull request titles must be [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/).
CI and the changelog read it literally.

Format: `type(scope): description`, for example `fix(loader): handle missing mod`.

- Common types: `feat`, `fix`, `perf`, `refactor`, `docs`, `test`, `build`, `ci`.
  - `chore` and `style` are hidden from the changelog, so prefer a visible type for user-facing changes.
- `pack:` is the multi-change squash type (for example `pack(loader): 1.2.0`). Its body lines can carry nested conventional commits.
- Keep the scope short or omit it.
- Mark breaking changes with `!`: `feat(api)!: drop legacy hook`, and explain the break plus the migration in the body or footer.
- Link issues with `Fixes #123` or `Closes owner/repo#123` so the changelog attributes them.
- One logical change per pull request, do not mix different content together. Keep it focused and ready for review; draft pull requests are skipped by CI until marked ready.
- Co-authors belong in `Co-authored-by:` footers, not in the title.

## Codestyle

Formatting is automated and is not a review topic. Run before you push:

```shell
./gradlew check
./gradlew formatJavaApply clearSkiesApply
```

- `check` runs formatting checks, Checkstyle, `checkLicense`, and tests. Preferably even `build`.
- Every `.java` file starts with the `HEADER` block comment. `HEADER` should match the `LICENSE`,
- Java 25 by default. Files are UTF-8 with LF endings, 4 spaces, max line length 160.
  - See `.editorconfig` and `formatj.toml`.
- Nullness annotations come from `org.jspecify.annotations` only.
- Assertions use AssertJ (`org.assertj.core.api.Assertions`) only.
  - JUnit assertions, Hamcrest and several others are rejected by Checkstyle.
- Public API needs Javadoc. Checkstyle warnings on `JavadocMethod`, `SummaryJavadoc`, and clause order are review signals, do not add empty or filler Javadoc to silence them.
- Add or update tests for behavior changes.
