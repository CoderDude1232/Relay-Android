<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset=".github/assets/relay-logo-light-ink.png">
    <img src=".github/assets/relay-logo-dark-ink.png" alt="Relay" width="180">
  </picture>
</p>

<h3 align="center">Relay for Android</h3>

<p align="center">
  The Android client for Relay, an end-to-end encrypted messenger.<br>
  It speaks the same protocol as the iPhone app, byte for byte.
</p>

<p align="center">
  <a href="https://relaymsg.app"><b>Website</b></a> ·
  <a href="https://github.com/CoderDude1232/Relay"><b>Relay (server, iOS, protocol)</b></a> ·
  <a href="docs/PROTOCOL.md"><b>Interop contract</b></a> ·
  <a href="SECURITY.md"><b>Report a vulnerability</b></a>
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/-AGPL--3.0-C611D6?style=flat-square&logoColor=white&logo=gnu" alt="License: AGPL-3.0"></a>
  <img src="https://img.shields.io/badge/-Android%208.0+-C611D6?style=flat-square&logoColor=white&logo=android" alt="Android 8.0+">
  <img src="https://img.shields.io/badge/-Kotlin%20%C2%B7%20Compose-C611D6?style=flat-square&logoColor=white&logo=kotlin" alt="Kotlin and Jetpack Compose">
  <img src="https://img.shields.io/badge/-Signal%20Protocol%20+%20PQXDH-C611D6?style=flat-square&logoColor=white&logo=signal" alt="Encryption: Signal Protocol + PQXDH">
</p>

> [!NOTE]
> Relay for Android is in development and hasn't been released. Relay is
> available on iPhone today.

## Features

- 🔐 **Same encryption as iPhone.** libsignal 0.97.4 (the exact version the iOS
  app vendors): PQXDH, the Double Ratchet, sender keys and sealed sender.
- 💬 **Messaging.** One-to-one and group chats, reactions, replies, edits and
  unsend, voice notes, photos and files, polls, scheduled messages, live
  location and search.
- 📞 **Calls** over WebRTC, relayed through TURN.
- 🔒 **Encrypted storage.** SQLCipher, with its key wrapped by the Android
  Keystore.
- ☁️ **Encrypted backups** in the same format as the iPhone app.
- 🔍 **Blinded contact discovery**, matching the relay's OPRF exactly.

## What's in this repository

| Path | Contents |
|---|---|
| [`app/`](app) | The app: Jetpack Compose UI, calls, notifications. |
| [`core/`](core) | Messaging logic: envelopes, sessions, groups, backup. |
| [`crypto/`](crypto) | libsignal, attachment encryption, blinded discovery and device linking. |
| [`net/`](net) | REST and WebSocket clients, with `Relay-Sig` request signing. |
| [`storage/`](storage) | The SQLCipher database and Keystore-backed secrets. |
| [`proto/`](proto) | Generates Kotlin from [`schema/`](schema), a copy of the wire protocol from the Relay repo. |
| [`tools/genvectors`](tools/genvectors) | Generates test vectors from the Go relay, so the Kotlin code is checked against it. |
| [`docs/`](docs) | [`PROTOCOL.md`](docs/PROTOCOL.md): every endpoint, field and crypto parameter the client has to match. |

## Building

<details>
<summary><b>Android app</b>: Android Studio, JDK 17</summary>

Open the project in Android Studio, or build from the command line:

```sh
./gradlew assembleDebug
./gradlew test
```

Push notifications need a Firebase config in `app/google-services.json`
(not checked in); without it the app builds without push.

</details>

<details>
<summary><b>Test vectors</b>: Go, with the Relay repo checked out next to this one</summary>

```sh
git clone https://github.com/CoderDude1232/Relay ../Relay
cd tools/genvectors
go run . -kind=wire   > ../../proto/src/test/resources/golden/wire-vectors.json
go run . -kind=crypto > ../../crypto/src/test/resources/golden/crypto-vectors.json
```

</details>

## The protocol

The wire protocol is defined in the [Relay repository](https://github.com/CoderDude1232/Relay):
[`proto/`](https://github.com/CoderDude1232/Relay/tree/main/proto) and the API in
[`server/README.md`](https://github.com/CoderDude1232/Relay/blob/main/server/README.md).
`schema/` here is a copy; when the protocol changes there, copy both `.proto`
files over unchanged.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Please report security issues privately,
as described in [SECURITY.md](SECURITY.md).

## License

Copyright © 2026 the Relay authors.

Relay for Android is free software under the
[GNU Affero General Public License v3.0](LICENSE). It's built on
[libsignal](https://github.com/signalapp/libsignal), which is also AGPL-3.0.
Other components keep their own licenses.
