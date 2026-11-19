# agents

This repository is the shared Claude Code and Codex plugin catalog. It stores marketplace metadata and a README index, not copies of the tools or their skills.

Read `.agents/rules/catalog.md` before changing catalog entries.

## Catalogs

- `.claude-plugin/marketplace.json` is the Claude Code marketplace.
- `.agents/plugins/marketplace.json` is the Codex marketplace.
- `README.md` groups the available plugins and documents client installation.
- `CHANGELOG.md` records catalog releases; there is no package or build artifact.

## Verification

Parse both JSON documents, check unique plugin names and source paths, compare shared entries, and reconcile README counts. Check added entries against the tool repository's actual manifests and release before publishing this catalog.

The tag pipeline renders the version and license badges. There is no application test suite or Makefile.
