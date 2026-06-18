# promptSkill

A curated skills library for Claude Code (Claude desktop app and CLI) — TDD, systematic debugging, collaborative planning, and proven development workflows. Skills auto-trigger at the right moments so you don't have to remember to use them.

## Quick Install (Claude Code)

```bash
/plugin install https://github.com/peterpitt/promptSkill
```

That's it. Restart your session. The skills activate automatically.

## What You Get

Skills activate automatically when relevant. You don't invoke them manually.

| Skill | Auto-triggers when |
|-------|--------------------|
| **brainstorming** | You mention building, adding, or changing a feature |
| **writing-plans** | You have an approved design and need an implementation plan |
| **subagent-driven-development** | You have a plan and want fast parallel execution |
| **executing-plans** | You have a plan to execute step-by-step with checkpoints |
| **test-driven-development** | Implementing any feature, fix, or behavior change |
| **systematic-debugging** | Any bug, test failure, or unexpected behavior |
| **verification-before-completion** | Before claiming work is done or fixed |
| **requesting-code-review** | After completing tasks or before merging |
| **receiving-code-review** | When receiving and implementing review feedback |
| **using-git-worktrees** | Before starting isolated feature work |
| **finishing-a-development-branch** | When all tasks are done and you need to merge/PR |
| **dispatching-parallel-agents** | When 2+ independent tasks can run concurrently |
| **writing-skills** | When creating or editing skills |

## The Workflow

```
User: "Let's build X"
  → brainstorming   (clarify intent, propose approaches, write spec)
  → writing-plans   (break spec into bite-sized TDD tasks)
  → subagent-driven-development  (fresh agent per task, review after each)
  → finishing-a-development-branch  (verify, merge or PR)
```

## Extending — Add Your Own Skills

Skills are just markdown files. Create a new one in `skills/`:

```
skills/
└── my-skill/
    └── SKILL.md       ← required
```

**Minimal SKILL.md template:**

```markdown
---
name: my-skill
description: Use when <exact trigger condition> — one sentence, specific
---

# My Skill Title

## When to Use

- Condition A
- Condition B

## The Process

1. Step one
2. Step two
3. Step three

## Key Rules

- Rule 1
- Rule 2
```

**Frontmatter rules:**
- `name` — must match the directory name
- `description` — this is what the agent reads to decide whether to invoke the skill; be specific about trigger conditions

After adding a skill, reload your Claude Code session and it will auto-discover the new skill.

## Updating

```bash
/plugin update promptSkill
```

Or reinstall:

```bash
/plugin install https://github.com/peterpitt/promptSkill
```

## File Structure

```
promptSkill/
├── .claude-plugin/
│   ├── plugin.json         Plugin metadata
│   └── marketplace.json    Marketplace registration
├── hooks/
│   ├── hooks.json          Session-start hook config
│   ├── run-hook.cmd        Windows/Unix polyglot dispatcher
│   └── session-start       Bootstrap injection script
└── skills/
    ├── using-superpowers/  Bootstrap — loaded at every session start
    │   ├── SKILL.md
    │   └── references/
    │       └── claude-code-tools.md
    ├── brainstorming/
    ├── test-driven-development/
    ├── systematic-debugging/
    ├── writing-plans/
    ├── subagent-driven-development/
    ├── executing-plans/
    ├── finishing-a-development-branch/
    ├── requesting-code-review/
    ├── receiving-code-review/
    ├── using-git-worktrees/
    ├── verification-before-completion/
    ├── dispatching-parallel-agents/
    └── writing-skills/
```

## License

MIT
