# tune-and-polish

**Fix skill triggers and polish discoverability in one pass.**

When a skill isn't triggering correctly or overlaps with siblings, and you also want its public surfaces (repo description, README, site page) polished for discovery, tune-and-polish handles both. It runs Tune-Skill to diagnose trigger/boundary/handoff issues and make minimal validated edits, then passes the result to Findable-Polish to audit discoverability gaps and generate improved alternatives. You get a skill that fires correctly and is easy to find.

## Usage

```text
/tune-and-polish findable
/tune-and-polish ~/.qoder/skills/wordsmith/SKILL.md
Fix my skill's triggering and polish its discovery surfaces.
```

## When to use

- You want both trigger fixes AND better discoverability in one pass
- A skill isn't triggering when it should *and* its listing needs the same attention
- Two skills claim the same request *and* you want the public copy updated after the split
- Someone says "this skill doesn't work and nobody finds it"
- You're preparing a skill for publication and want it tight

## What it produces

- Trigger/boundary/handoff audit from Tune-Skill
- Minimal validated edits to SKILL.md
- check_skill.py validation (FAIL/WARN/PASS)
- Discoverability audit from Findable-Polish
- Polished alternatives for descriptions, README, site page

## Install

```bash
npx skills add arm-pz/tune-and-polish
```

## Dependencies

Requires `tune-skill` and `findable-polish` (which needs `findable` + `wordsmith`) to be installed.

## Not for

- Creating skills from scratch → use [draft-skill](https://github.com/arm-pz/draft-skill)
- Just tuning without polishing → use [tune-skill](https://github.com/arm-pz/tune-skill) alone
- Just polishing without tuning → use [findable-polish](https://github.com/arm-pz/findable-polish) alone

## Related

- **[tune-skill](https://github.com/arm-pz/tune-skill)** — Fix triggers and boundaries (phase 1)
- **[findable-polish](https://github.com/arm-pz/findable-polish)** — Audit and polish discoverability (phase 2)
- **[skill-launch](https://github.com/arm-pz/skill-launch)** — Full pipeline for new skills (includes these two)

## License

MIT © Abdul Rahman P Z
