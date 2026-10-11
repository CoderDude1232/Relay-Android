# Contributing to Relay for Android

Thanks for your interest in Relay. Bug reports, fixes and improvements are all
welcome.

## Before you start

- **Security issues** go to security@relaymsg.app, never a public issue. See
  [SECURITY.md](SECURITY.md).
- **Bugs:** open an issue with your Android version and device, the commit you
  built, what you did, what you expected and what happened.
- **Features and larger changes:** open an issue to discuss them first, so
  nobody spends time on something that won't fit.

## Making a change

1. Fork the repository and create a branch from `main`.
2. Set up the build as described in the [README](README.md#building).
3. Keep the change focused: one fix or feature per pull request.
4. Match the style of the surrounding code, and add or update tests
   (`./gradlew test`). Anything that touches the wire or the crypto should be
   checked against the golden vectors from `tools/genvectors`.
5. Open a pull request that explains what changed and why, and how you tested
   it.

## Ground rules

- **Interoperability comes first.** This client must match the protocol and
  the iPhone app byte for byte. Protocol changes start in the
  [Relay repository](https://github.com/CoderDude1232/Relay) (`proto/` and
  `server/README.md`); `schema/` here is only ever a copy.
- **Privacy is a requirement.** Don't add analytics, tracking, advertising or
  third-party SDKs beyond Firebase Cloud Messaging for push, and don't log
  identifiers, IP addresses or message metadata.
- **Cryptography changes need review.** Anything touching keys, sessions,
  storage encryption or authentication gets extra scrutiny; explain the threat
  model in the pull request.
- **No secrets.** Never commit keys, tokens, keystores, `google-services.json`
  or server addresses.

## License

By contributing, you agree that your contributions are licensed under the
[GNU Affero General Public License v3.0](LICENSE), the same license as the rest
of Relay.
