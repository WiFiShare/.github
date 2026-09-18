# WiFiShare

An open platform for sharing Wi-Fi access: people and venues share free or open
Wi-Fi so others can find and join it.

## Status

Early development, started September 2026. No data is being collected yet and no
app has been released. Everything here is scaffolding and specification.

## Privacy rules

Three rules decide what the software may do. They come before features.

1. Collect only what helps someone connect.
2. Publish less than is collected.
3. Keep nothing that ties an observation to a person.

There are no accounts, no device IDs and no advertising IDs for contributors.

Networks whose SSID ends in `_nomap` or `_optout` are never collected. Private
password-protected networks are not collected unless their owner shares them
deliberately. In the Android app, contributing is off until the person turns it on.

## Repositories

| Repo | Purpose | License |
| --- | --- | --- |
| [api](https://github.com/WiFiShare/api) | Django backend: anonymous ingest, area lookups, dump export | AGPL-3.0 |
| [android](https://github.com/WiFiShare/android) | Kotlin app that scans, shares and joins | MPL-2.0 |
| [ios](https://github.com/WiFiShare/ios) | Swift app that finds and joins | MPL-2.0 |
| [spec](https://github.com/WiFiShare/spec) | Data model, JSON Schemas, OpenAPI, privacy filter rules, test fixtures | Apache-2.0 |
| [data](https://github.com/WiFiShare/data) | Weekly public dump | ODbL-1.0 |
| [wifishare.github.io](https://github.com/WiFiShare/wifishare.github.io) | Website | MIT for code, CC-BY-4.0 for text |
| [.github](https://github.com/WiFiShare/.github) | This org profile and the shared community files | — |

## Phases

| Phase | Work | State |
| --- | --- | --- |
| P0 | Foundations | Current |
| P1 | Data pipeline and API | Planned |
| P2 | Android app | Planned |
| P3 | iOS app | Planned |
| P4 | Venue sharing and public beta | Targeted around April 2027 |

## Contributing

Work is tracked in the repository it affects, so open or pick up an issue there.
Read [CONTRIBUTING.md](https://github.com/WiFiShare/.github/blob/main/CONTRIBUTING.md)
first: it explains what a privacy-filter change must bring with it, and where
each component's build instructions live.

## Opting a network out

Two ways, and neither needs an account:

- Rename the network so its SSID ends in `_nomap` or `_optout`. Networks with
  those suffixes are never collected.
- Once an app is released, use its one-tap removal for a network you own.

If a network is already in the published data and should not be, open a
`Network problem` issue on the [data](https://github.com/WiFiShare/data) repo,
without a BSSID or a password.

## Security

Report a vulnerability with GitHub private vulnerability reporting on the
affected repository. Details and scope are in
[SECURITY.md](https://github.com/WiFiShare/.github/blob/main/SECURITY.md).
There is no bug bounty. A report about one specific Wi-Fi network's privacy is
not a vulnerability report: use the opt-out path above.

## Licenses

Each repository carries its own license, listed in the table above. In short:
the backend is AGPL-3.0, the apps are MPL-2.0, the specification is Apache-2.0,
the published data is ODbL-1.0, and the website is MIT for code with CC-BY-4.0
for text. Contributions are licensed under the license of the repository they
land in.
