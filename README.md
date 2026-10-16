# resolc-releases

Byte-identical copies of [resolc](https://github.com/paritytech/revive) release binaries, the
Solidity compiler for PolkaVM built by Parity Technologies. pezkuwi-DKS CI downloads resolc from
here so its builds do not depend on another organisation keeping a release URL alive.

We host the bytes; we do not build them. Every binary here is downloaded from the upstream
release named below and is accepted only if its sha256 matches the `checksums.txt` that upstream
published with that release. That file is kept unchanged under `<version>/checksums.txt`, and the
consumer pins the same hash again, so a substituted binary fails on both sides.

| Release | Upstream | Upstream tag commit | Mirrored assets |
| --- | --- | --- | --- |
| v1.0.0 | [paritytech/revive v1.0.0](https://github.com/paritytech/revive/releases/tag/v1.0.0) | `a0a1e11453983b0ab5a8bfe93a9881eb4167a211` | `resolc-x86_64-unknown-linux-musl` |

## Adding a release

1. Download the asset and `checksums.txt` from the upstream release.
2. `sha256sum -c --ignore-missing checksums.txt` must pass.
3. Commit `checksums.txt` under `<version>/` through a pull request, then create the release
   `v<version>` here with the same asset name.
4. Update `resolc-version` and `resolc-sha256` in pezkuwi-DKS
   `.github/actions/install-solidity/action.yml`.

## License

resolc is dual-licensed under Apache-2.0 and MIT by its authors; both license texts are included
here unchanged. This repository adds no code.
