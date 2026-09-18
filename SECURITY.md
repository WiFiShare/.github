# Security policy

WiFiShare is in early development. No data is being collected yet and no app has
been released. Reports are still welcome: it is cheaper to fix a design problem
now than after the first dump is published.

## Reporting a vulnerability

Use GitHub private vulnerability reporting on the repository that is affected:

1. Go to that repository on github.com.
2. Open the `Security` tab.
3. Choose `Report a vulnerability`.

That opens a private advisory visible only to you and the organization owners.
Do not open a public issue and do not send a pull request that demonstrates the
problem, because both are public the moment they are created.

If you are unsure which repository is affected, report it on
[spec](https://github.com/WiFiShare/spec/security), since that is where the data
model and the privacy filter rules are defined.

Please include what you would want to receive yourself: the affected repository
and revision, what an attacker can do, and the steps to reproduce it. A proof of
concept helps. If the finding involves real Wi-Fi networks or real locations,
describe the class of problem and leave the identifying details out of the
report, or say that you can supply them separately.

## What is in scope

| Area | Examples |
| --- | --- |
| `api` | Anonymous ingest, area lookups, dump export, authentication of owner verification, anything that lets one client learn about another |
| `android`, `ios` | Data left on the device, data sent that the privacy rules do not allow, permission misuse, anything that identifies the person running the app |
| Dump pipeline | The weekly commit and monthly release, anything that publishes more than the filter allows, anything that lets a removal be undone |

Failures of the three privacy rules are in scope and treated as security
problems, not as feature requests:

1. Collect only what helps someone connect.
2. Publish less than is collected.
3. Keep nothing that ties an observation to a person.

Concretely, a way to make the system collect a network whose SSID ends in
`_nomap` or `_optout`, to collect a private password-protected network its owner
has not shared, to publish a community-found network's BSSID, to publish a
community-found network at a finer precision than a geohash-7 cell, or to link
observations back to a person, is a vulnerability. Report it privately.

## What is not in scope

- Reports about one specific Wi-Fi network's privacy. If a network of yours
  should not be in the data, that is the opt-out path, not a vulnerability:
  rename the network so its SSID ends in `_nomap` or `_optout`, use the app's
  one-tap removal once an app is released, or open a `Network problem` issue on
  the [data](https://github.com/WiFiShare/data) repository. Do not include a
  BSSID or a password in a public issue.
- Wrong, stale or unusable data in the dump. That is also a `Network problem`
  issue.
- Findings against third-party services the project happens to use, unless the
  problem is in how WiFiShare configures them.
- Automated scanner output with no described impact.

## What to expect

There is no bug bounty. The project has no funding and does not pay for reports,
and it will not offer swag instead. What you get is a reply, credit in the
advisory if you want it, and a fix.

The project is run by volunteers, so no response time is promised. Please allow
a reasonable period for a fix before publishing, and tell us if you have a
disclosure deadline so we can plan around it. Fixed issues are published as
GitHub security advisories on the affected repository.
