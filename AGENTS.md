# AGENTS.md

## Supply-chain checks for AUR updates

The Brother packages here are based on several AUR packages and have no single
upstream repository. Before importing an update or pushing packaging changes:

- Review the AUR git history and diffs for each affected package, not just the
  latest snapshot. Treat unexplained changes to source URLs, checksums,
  patches or `prepare()` / `package()` logic as a red flag.
- Confirm every source URL points at Brother's official download host, not a
  fork, personal mirror or lookalike domain.
- Download sources independently and compare hashes with checksums published
  by upstream; do not trust the hashes in the AUR `PKGBUILD` alone.
- Inspect patches, launchers and any `.install` file for shell hooks, network
  access or unexpected executables.
- Never accept new AUR checksums without repeating the upstream verification.
- Record what was verified in the commit message.
