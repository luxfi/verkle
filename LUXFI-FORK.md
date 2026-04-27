# LUXFI-FORK

This is a luxfi-maintained fork of [ethereum/go-verkle](https://github.com/ethereum/go-verkle).

## Pin

* Upstream tag: `v0.2.2`
* Commit SHA: `7dd8079b3a2d8bbf4fadf0d74bac51e8ad5c1c5c`
* License: Unlicense (public domain, see `LICENSE`)

## Why this fork exists

go-verkle is the canonical Verkle tree implementation for Ethereum's
state-tree migration. luxfi consumes it for:

* `luxcpp/crypto/verkle/` — first-party C++ port (LP-137 sibling #104) needs
  the `DeterministicGenerator` table and KAT vectors
* `lux/crypto` Go layer — replaces `github.com/ethereum/go-verkle` via go.mod
  replace directive

Owning the fork pins the deterministic-generator table and Pedersen commit
constants so upstream restructures (e.g. between EIP-6800 revisions) cannot
silently break already-committed Verkle proofs.

## Sync policy

* Track upstream tagged releases only.
* Pull tags into `sync/<tag>` branches. Re-run Verkle KATs in
  luxcpp/crypto/verkle and lux/crypto Go tests. Merge to `master` only when
  the deterministic generator table is byte-identical OR audited.
* Generator-table changes are a hard stop — they re-key existing commitments.

## Maintainer

luxfi crypto team. Contact via the `luxfi/crypto` repo.
