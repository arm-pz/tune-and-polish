# tune-and-polish

Tune a skill's trigger and boundaries with Tune-Skill, then audit its discoverability and polish it with Findable-Polish. Use when the user wants to fix a skill that isn't triggering correctly or overlaps with siblings, and also wants its repo description, README, and site page polished for discovery — in one pass.

## Usage

```text
/tune-and-polish findable
/tune-and-polish ~/.qoder/skills/wordsmith/SKILL.md
Fix my skill's triggering and polish its discovery surfaces.
```

## Workflow

1. **Tune-Skill** fine-tunes description, commands, and sibling boundaries
2. **Findable-Polish** audits discoverability and generates polished alternatives
3. Returns tune changes + discovery alternatives + recommended actions

## Dependencies

Requires `tune-skill` and `findable-polish` (which needs `findable` + `wordsmith`) to be installed.

## License

MIT © Abdul Rahman P Z
