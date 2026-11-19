# Catalog entries

- Keep Claude Code and Codex entries aligned on plugin name, source URL and plugin root. Preserve channel-specific fields and intentional Codex-only entries.
- Tool plugins use a `git-subdir` source rooted at the tool repository's `.agents` directory. The central catalog holds no copied skills.
- Derive descriptions and licenses from the tool's current public manifest. Do not promise capabilities absent from that tool.
- Keep the README index and plugin counts synchronized with both catalogs. Registering a marketplace does not install its plugins.
- Publish a tool's agent surface before publishing a catalog entry that depends on it.
