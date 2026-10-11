# Security policy

## Reporting a vulnerability

Please email **security@relaymsg.app** and don't open a public issue. Include:

- what's affected: this Android client (with the commit or build you tested),
  the relay server, or the protocol;
- the steps to reproduce it, and what an attacker could do with it;
- any proof-of-concept code or logs (with nobody else's data in them).

We'll acknowledge your report, keep you updated while we fix it, and credit you
when the fix ships unless you'd rather we didn't. Please give us a reasonable
time to release a fix before you publish anything.

## Scope

In scope:

- this Android client;
- the relay server and the production service at `api.relaymsg.app`, and the
  iPhone app (see the [Relay repository](https://github.com/CoderDude1232/Relay));
- the wire protocol and the cryptography it uses.

A difference between this client and the iPhone app that weakens security,
such as a skipped check or a weaker parameter, counts as a vulnerability.

Out of scope: denial of service or load testing against the production service,
social engineering, physical attacks, and issues in third-party services
(Google, Cloudflare, Supabase) that aren't caused by how Relay uses them.

## Testing safely

Test against your own accounts, or better, a relay you run yourself (see the
Relay repository's `server/README.md`). Don't access or change other people's
data, create accounts in bulk, or degrade the service for others. Research done
in good faith within these rules is welcome, and we won't pursue it.

## Supported versions

Relay for Android hasn't been released. Fixes go into `main`.
