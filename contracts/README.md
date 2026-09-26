# Contracts

Shared file formats for the WhyStrohm skills. Each skill stays in its own repo. They connect by
reading and writing the same files in a `brand/` folder in the user's project.

| File | Written by | Read by | Schema |
|---|---|---|---|
| `brand/voice-profile.json` | whystrohm-voice-extract | whystrohm-voice-scorer | `voice-profile.v1.schema.json` |

The canonical schemas live in [whystrohm/shotkit](https://github.com/whystrohm/shotkit/tree/main/contracts).
Every other repo keeps a byte-identical copy, and its CI fails if the copy drifts. To change a
schema, change it in Shotkit first, then copy it into each repo that uses it.

A new version of a schema gets a new file (`v2`). A skill that reads the file checks `contract`
and `version` before it trusts the rest.
