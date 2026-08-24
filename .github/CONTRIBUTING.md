# Contributing

Build, format, and release rules for CleanroomMC projects live in
[CleanroomMC/Convention](https://github.com/CleanroomMC/Convention).

In short:

- Default branch is `master`.
- Squash-merges only.
- Pull request title is a [Conventional Commit](https://www.conventionalcommits.org). It becomes the commit on `master`.
- Run `./gradlew spotlessApply` before you push. Formatting is not a review topic.
- Do not vendor a copy of a convention file. Change it in the [Convention Repository](https://github.com/CleanroomMC/Convention) and bump the plugin.

Security reports: see [SECURITY.md](SECURITY.md).
