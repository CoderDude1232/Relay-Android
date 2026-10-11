# Wire schema

`relay.proto` and `content.proto` are copies of `proto/` in the Relay repo
(https://github.com/CoderDude1232/Relay), which is the source of truth for the
protocol: the relay server and the iOS app are built from it. Don't edit these
files here. When the schema changes there, copy both files over unchanged; the
`:proto` module generates Kotlin from them at build time.
