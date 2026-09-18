# Contributing to WiFiShare

WiFiShare is in early development. No data is being collected yet and no app has
been released, so most open work is specification, scaffolding and review rather
than feature work.

Please read the [Code of Conduct](CODE_OF_CONDUCT.md) before taking part.

## Picking up work

Issues live in the repository they affect, not in a central tracker. Start
there:

| Repo | What its issues cover |
| --- | --- |
| [spec](https://github.com/WiFiShare/spec) | Data model, JSON Schemas, OpenAPI, privacy filter rules, test fixtures |
| [api](https://github.com/WiFiShare/api) | Django backend: anonymous ingest, area lookups, dump export |
| [android](https://github.com/WiFiShare/android) | Kotlin app that scans, shares and joins |
| [ios](https://github.com/WiFiShare/ios) | Swift app that finds and joins |
| [data](https://github.com/WiFiShare/data) | The weekly public dump and problems in published data |
| [wifishare.github.io](https://github.com/WiFiShare/wifishare.github.io) | Website |

If the change you have in mind is not covered by an issue, open one in that
repository first and say what you intend to do. That avoids two people building
the same thing in different directions, which is easy to do while the data model
is still moving.

For anything that crosses repositories, open the issue on `spec`. The
specification is what the other repositories agree on, so a cross-cutting change
starts there.

## Privacy-filter changes need spec fixtures

The privacy filter decides what is collected and what is published. The three
rules it exists to enforce are:

1. Collect only what helps someone connect.
2. Publish less than is collected.
3. Keep nothing that ties an observation to a person.

A change to filter behaviour in any repository must come with test fixtures in
[spec](https://github.com/WiFiShare/spec) that demonstrate the new behaviour,
and the implementation must be tested against them. This applies to, among
others:

- the `_nomap` and `_optout` SSID suffixes, which are never collected
- whether a network is collected at all, including password-protected networks,
  which are excluded unless their owner shares them deliberately
- the precision of a published position, and which networks get an exact one
- whether a BSSID is published
- the mobile-network rule, which excludes networks seen more than 1 km apart

A pull request that changes any of this without fixtures will be asked for them
before review. The reason is simple: a privacy rule that is only described in
prose gets broken by the next refactor, and a broken filter publishes something
about somebody.

## Commits and pull requests

- One logical change per pull request. A refactor and a behaviour change in the
  same diff are hard to review and harder to revert.
- Write commit messages in the imperative mood, with a short subject line and a
  body that says why, not what. The diff already says what.
- Reference the issue the pull request closes.
- Say in the pull request description whether the change affects what is
  collected or what is published. If it does, link the fixtures.
- Keep the pull request template filled in. It exists so that reviewers do not
  have to ask the same three questions every time.
- Run each repository's tests and linters before pushing. The commands are in
  that repository's README.
- Expect review comments on anything that touches the data model, the filter or
  a platform permission. Those are the parts that are expensive to change later.

## Licensing of contributions

There is no CLA and the DCO is not required. No sign-off is needed on commits.

By opening a pull request you agree that your contribution is licensed under the
license of the repository it lands in: AGPL-3.0 for `api`, MPL-2.0 for `android`
and `ios`, Apache-2.0 for `spec`, ODbL-1.0 for `data`, and MIT for code with
CC-BY-4.0 for text on the website. Each repository carries its license text in
its `LICENSE` file.

Do not contribute code or data you do not have the right to relicense this way.
In particular, do not import network data from another database whose terms do
not allow it.

## Running each component

Build and run instructions belong with the code that changes, so they are in
each repository's README rather than duplicated here:

| Component | Where to look |
| --- | --- |
| Backend | [api/README.md](https://github.com/WiFiShare/api#readme) |
| Android app | [android/README.md](https://github.com/WiFiShare/android#readme) |
| iOS app | [ios/README.md](https://github.com/WiFiShare/ios#readme) |
| Specification and fixtures | [spec/README.md](https://github.com/WiFiShare/spec#readme) |
| Public dump layout | [data/README.md](https://github.com/WiFiShare/data#readme) |
| Website | [wifishare.github.io/README.md](https://github.com/WiFiShare/wifishare.github.io#readme) |

If a README's instructions do not work, that is a bug in that repository. Please
open an issue there.

## Reporting a vulnerability

Do not use a pull request or a public issue. See [SECURITY.md](SECURITY.md).
