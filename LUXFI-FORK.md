# LUXFI-FORK

This is a luxfi-maintained fork of [ethereum/go-verkle](https://github.com/ethereum/go-verkle).

## Pin

- Upstream tag: `v0.2.2`
- Upstream commit: `7dd8079b3a2d8bbf4fadf0d74bac51e8ad5c1c5c`
- License: MIT (see `LICENSE`)

## Why this fork exists

luxcpp/crypto's `verkle/` cpp body uses the deterministic Pedersen generator
table from go-verkle to build the C++ verkle commitment KAT suite. Pinning
to a luxfi-controlled mirror prevents upstream changes from breaking
deterministic builds.

`lux/crypto` (Go) imports this module via a `replace` directive so all luxfi
projects converge on a single canonical verkle implementation.

## Sync policy

- Track upstream tagged releases only. Never `master` HEAD.
- Pull tags into `sync/<tag>` branches.
- Re-run verkle KATs (lux/crypto and luxcpp/crypto/verkle) before merging
  to `master`.

## Maintainer

luxfi crypto team. Contact via the `luxfi/crypto` repo.
