# Q-MATH fork of core_affinity

`carlosfundora/core_affinity_rs`, branch `qmath`, is the Carlos-owned fork of
[`Elzair/core_affinity_rs`](https://github.com/Elzair/core_affinity_rs)
(crate `core_affinity`), forked on 2026-11-05 at upstream `master`
`90aa48cab703f748bd58d63fa41755be4228609e` (crate version 0.8.3, plus the
upstream SPDX license-metadata merge).

Q-MATH consumes it as the submodule `hardware/core_affinity`. Like the Rayon
fork it is held only by the canonical checkout (`update = none`) and is
ignored for Q-MATH status (`ignore = dirty`): changes inside the checkout are
committed and pushed here, while a moved gitlink still shows in Q-MATH.

## Rules

- `upstream` is fetch-only (`git remote set-url --push upstream DISABLED-fetch-only`).
  Nothing is ever pushed to `Elzair/core_affinity_rs`.
- Q-MATH changes are commits on `qmath` on top of the recorded upstream base.
  This file is the first such commit; it changes no code.

## Reapplying on a newer upstream

```sh
git fetch upstream
git format-patch --zero-commit --no-signature -o qmath-patches 90aa48cab703f748bd58d63fa41755be4228609e..qmath
git switch -c qmath-next <new-upstream-commit>
git am --3way qmath-patches/*.patch
cargo test
```

Then requalify the Q-MATH consumers, push `qmath` to `origin`, and advance the
Q-MATH `hardware/core_affinity` gitlink.
