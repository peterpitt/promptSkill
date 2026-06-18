---
name: using-superpowers
description: Use when starting any conversation - establishes how to find and use skills, requiring skill invocation before ANY response including clarifying questions
---

<SUBAGENT-STOP>
If you were dispatched as a subagent to execute a specific task, skip this skill.
</SUBAGENT-STOP>

<EXTREMELY-IMPORTANT>
If you think there is even a 1% chance a skill might apply to what you are doing, you ABSOLUTELY MUST invoke the skill.

IF A SKILL APPLIES TO YOUR TASK, YOU DO NOT HAVE A CHOICE. YOU MUST USE IT.

This is not negotiable. This is not optional. You cannot rationalize your way out of this.
</EXTREMELY-IMPORTANT>

## Instruction Priority

1. **User's explicit instructions** (CLAUDE.md, direct requests) — highest priority
2. **Skills** — override default system behavior
3. **Default system prompt** — lowest priority

## Skills Catalog

Check this catalog before EVERY response. If any skill matches, invoke it first.

| Skill | Invoke when |
|-------|-------------|
| `brainstorming` | User wants to build, add, or change features — before ANY code is written |
| `writing-plans` | You have an approved spec/design and need to create an implementation plan |
| `subagent-driven-development` | You have a written plan and want to execute it with fresh subagents per task |
| `executing-plans` | You have a written plan to execute without subagent dispatch |
| `test-driven-development` | Implementing any feature, bugfix, or behavior change |
| `systematic-debugging` | Any bug, test failure, unexpected behavior, or build error |
| `verification-before-completion` | Before claiming work is done, fixed, or passing — always |
| `requesting-code-review` | After completing tasks, before merging, or after major features |
| `receiving-code-review` | When receiving code review feedback before implementing suggestions |
| `using-git-worktrees` | Before starting feature work that needs isolation |
| `finishing-a-development-branch` | When all tasks complete and you need to merge/PR/cleanup |
| `dispatching-parallel-agents` | When you have 2+ independent tasks that can run concurrently |
| `writing-skills` | When creating or editing skills |

## How to Access Skills

**In Claude Code:** Use the `Skill` tool. When you invoke a skill, its content is loaded — follow it directly.

**Never read skill files manually with file tools** — always use the `Skill` tool.

## The Rule

**Invoke relevant skills BEFORE any response or action.** Even a 1% chance a skill might apply means invoke it.

```
User message received
  → Check Skills Catalog above
  → Any match? → Invoke the skill → Announce "Using [skill] to [purpose]"
               → Create todos for checklist items
               → Follow skill exactly
  → No match? → Respond normally
```

## Skill Priority

When multiple skills apply:
1. **Process skills first** (`brainstorming`, `systematic-debugging`) — determine HOW to approach
2. **Implementation skills second** — guide execution

"Let's build X" → `brainstorming` first, then implementation skills.
"Fix this bug" → `systematic-debugging` first, then fix.

## Skill Types

**Rigid** (`test-driven-development`, `systematic-debugging`, `verification-before-completion`): Follow exactly. No adaptation.

**Flexible** (planning, review skills): Adapt principles to context.

## Red Flags — You Are Rationalizing

| Thought | Reality |
|---------|---------|
| "This is just a simple question" | Questions are tasks. Check catalog. |
| "I need more context first" | Skill check comes BEFORE clarifying questions. |
| "This doesn't need a formal skill" | If a skill exists for it, use it. |
| "I remember this skill" | Skills evolve. Load current version. |
| "The skill is overkill" | Simple things become complex. Use it. |
| "I'll just do this one thing first" | Check BEFORE doing anything. |
| "I know what that means" | Knowing the concept ≠ using the skill. |

## User Instructions

Instructions say WHAT, not HOW. "Add X" or "Fix Y" doesn't mean skip workflows.
