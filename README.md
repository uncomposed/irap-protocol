# Idea Rendering Attestation Protocol

IRAP is a Git-native, forge-agnostic protocol for identifying an exact state of an evolving idea, linking independently published renderings to that state, and recording attributable signed judgments about those renderings.

This repository is the canonical idea history for IRAP. A branch is an editing convenience; an IRAP state is always an exact Git commit. The public registry at [ideas.proximitytoprogress.com](https://ideas.proximitytoprogress.com/) indexes those states and federates announcements, but it is not the source of canonical authority.

## Repository map

- `SPEC.yaml` — protocol definition
- `product.md` — reference product definition
- `acceptance.md` — normative acceptance criteria
- `.idea/manifest.yaml` — durable idea identity and Git metadata
- `.idea/verifiers.yaml` — historical verifier keys
- `.idea/verification-policy.yaml` — claim recognition policy
- `examples/` — illustrative records plus signed author-bootstrap attestations for immutable reference deployments
- `source/irap-v0.1.zip` — recovered source package preserved byte-for-byte

## Trust boundaries

- Git commit identity establishes the idea state.
- Artifact digests establish exact rendering bytes or a recursively identifying manifest.
- Ed25519 signatures establish who issued an attestation.
- The policy at the referenced commit determines whether a valid attestation is recognized.
- ActivityPub transports announcements; it does not establish truth or verification.

The initial eligible verifier is the protocol author. A recognized author attestation is attributable bootstrap evidence, not independent review. Independent verifier identities can be added in later commits without changing how historical attestations are evaluated.

Signed bootstrap statements are preserved beneath `examples/`. Their target remains the original protocol commit named inside each attestation; storing the records in later commits does not change that historical target.

## Current public implementation

The reference registry is available at [ideas.proximitytoprogress.com](https://ideas.proximitytoprogress.com/). Its implementation is maintained separately at `uncomposed/irap-registry` so protocol authority, software execution, and verification evidence remain distinct.

## Status

IRAP 0.1 is a draft. See `acceptance.md` for falsification tests and `PROVENANCE.md` for the origin of the recovered definition.
