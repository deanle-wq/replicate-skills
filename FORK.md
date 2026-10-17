# replicate-skills

Personal fork of [morluto/rea](https://github.com/morluto/rea). Everything
outside `.agents/skills/replicate/` is upstream REA.

## What's ours

- `.agents/skills/replicate/` is the `replicate` skill: the feature-replication
  workflow plus the Field notes we add as we use it.
- This file.

## How it's wired

Claude Code loads both skills straight from this checkout through symlinks, so
edits apply on the next Claude session:

- `~/.claude/skills/replicate` -> `.agents/skills/replicate`
- `~/.claude/skills/reverse-engineer-anything` -> `.agents/skills/reverse-engineer-anything`

The REA tools themselves come from the `rea-agents` npm package, registered as
the `rea` MCP server (`claude mcp list`).

Because the symlinks point at the working tree, keep the branch that has
`replicate` checked out (merge it into `main`).

## Pull upstream updates

```bash
git fetch upstream
git merge upstream/main
```

Then bump the MCP server to the new release, matching the version in
`package.json`:

```bash
claude mcp remove --scope user rea
claude mcp add --scope user rea -- npx -y rea-agents@<version> mcp
```
