# Relay — Android client

The Android client for Relay (Kotlin / Jetpack Compose). The relay server, the
iOS app and the protocol live in [Relay](https://github.com/CoderDude1232/Relay);
check it out next to this repo as `../Relay`.

**Status:** not started. The project brief, interop contract, platform mappings,
and staged build plan live in [`CLAUDE.md`](CLAUDE.md).

**How to work on it:** open a Claude Code session in this repo (separate from
the iOS/server session). The agent reads `CLAUDE.md`
automatically. First deliverable is `PROTOCOL.md` (the exact contract to match),
for owner review before Stage 1.

**Build tooling:** Android Studio + JDK 17 + Android SDK + emulator.

**Interop:** every stage must round-trip a message with the iOS client against the
live relay (`https://api.relaymsg.app`). The wire protocol is defined in
`proto/` and `server/README.md` in the Relay repo — those are authoritative.
`schema/` holds a copy of the protos the build generates code from.
