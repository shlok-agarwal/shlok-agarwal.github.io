---
layout: post
title: "Personalized Modular Claude Code Configuration for Engineers"
date: 2026-01-19
categories: [AI, tools]
tags: [AI, Claude, workflow]
excerpt: "Context engineering techniques for getting better results from LLMs like Claude Code. A modular .claude configuration that anyone can customize."
---

# Personalized Modular Claude Code Configuration for Engineers

I remember when long conversations with LLMs would gradually degrade as the output becoming less accurate, the suggestions less relevant. At those times, I would either switch to another platform or give up on the question entirely. Then I came across [Ashley Ha's blog post](https://medium.com/@ashleyha/i-mastered-the-claude-code-workflow-145d25e502cf) that put all of this in "context" (pun intended). I recommend reading her post first, as it goes into more detail than I will here.

What I was missing was the concept of **context engineering**. Once your context exceeds roughly 60%, LLM responses start losing sight of your initial requirements. The model becomes overloaded with conflicting information and accumulated session data, diluting its understanding of what actually matters.

Different LLMs handle this differently. ChatGPT uses a rolling context window where recent exchanges may cause it to forget earlier conversation which sometimes is helpful but sometimes not. With Claude Code, which I consider the best coding agent available, you need to be more deliberate. Code files are long, and the context window fills up quickly. Monitoring context usage and clearing or compacting it before moving forward is essential.

## What is Context Engineering?

Context engineering, a term coined by [Dexter Horthy](https://github.com/dexhorthy), is the practice of deliberately managing what information you feed to an LLM and when. As Ashley Ha puts it: *"It's really not about having more context, it's about having the right context at the right time."*

The key insight is counterintuitive: the more you allocate into the context window, the worse the outcomes—both in quality and unexpected behavior. This holds true regardless of which LLM you're using.

## The 60% Rule and Four-Phase Workflow

Ashley Ha's workflow, which I've been using for over a month now, centers on two principles:

1. **Never exceed 60% context** — check frequently with `/context` and clear when needed
2. **Split work into four phases** — Research → Plan → Implement → Validate

### The Four Phases

**Research**: Understand existing code without writing any. Spawn agents to investigate different aspects in parallel. Save findings to a `thoughts/` directory. Clear context.

**Plan**: Create a detailed implementation strategy through approximately 5 iterations. Each iteration addresses clarifying questions, design tradeoffs, and edge cases. Clear context.

**Implement**: Execute one phase at a time. Run verification, pause for manual testing. This prevents cascading failures from undetected Phase 1 errors.

**Validate**: Systematically verify the entire implementation. Review commits, run comprehensive checks, generate reports.

The critical insight here: **one phase at a time equals continuous validation equals fewer surprises.**

## Making It Your Own: A Modular Configuration

After using this workflow extensively, I built a modular `.claude` configuration that anyone can customize. The design philosophy is simple: generic commands and agents that work out of the box, with a `personal/` folder for project-specific customization.

### Directory Structure

```
.claude/
├── commands/           # Slash command definitions
├── agents/             # Agent definitions
├── reference/          # Shared reference docs
├── settings.json       # Global settings
└── personal/           # YOUR PROJECT-SPECIFIC CONFIG (gitignored)
    ├── config.yaml              # Workspace paths and commands
    ├── build-instructions.md    # Build procedures
    ├── coding-preferences.md    # Code style guidelines
    ├── project-context.md       # Project-specific context
    └── thoughts/                # Your research and plans
```

### Available Commands

| Command | Description |
|---------|-------------|
| `/create_plan` | Create detailed implementation plans through interactive research |
| `/implement_plan` | Implement approved plans with verification |
| `/validate_plan` | Validate implementation against plan |
| `/research_codebase` | Document codebase with thoughts directory for context |
| `/create_handoff` | Create handoff document for session transfer |
| `/resume_handoff` | Resume work from a previous handoff |

### Self-Discovery

When personal configuration files are missing, the commands automatically discover your build system by looking for CMakeLists.txt, package.json, Makefile, or Cargo.toml. This means you can start using the workflow immediately and add customization incrementally.

## Practical Tips

**Research never gets skipped** — Even when I think I know the codebase, parallel agents discover overlooked patterns and edge cases that would have caused problems later.

**Plan iteration pays dividends** — Spending 30-45 minutes on five planning iterations prevents hours of implementation backtracking.

**Be ruthless with context** — When hitting 60%, immediately save findings to files rather than keeping everything in memory. The `thoughts/` directory becomes your external brain.

**Manual testing complements automation** — Automated tests catch code issues; manual testing reveals UX problems, performance bottlenecks, and real-world edge cases that tests miss.

**Plans are living documents** — Update your plan file when Phase 2 discoveries affect Phase 3 specifications.

## A Word of Caution

This workflow has two practical limitations:

1. **Speed**: Multiple agents spawned means simple tasks take longer. For trivial changes, skip phases or use Claude directly.

2. **Usage limits**: Claude Pro barely supports this workflow—you'll hit limits with 1-2 feature implementations. Claude Max is recommended if you can afford it.

Writing detailed prompts before diving into code is also a good practice that this workflow enforces. It forces you to plan before you start coding, something many engineers are accustomed to doing anyway but often skip under time pressure.

## Getting Started

Clone the repository and start using it immediately. The commands work out of the box with self-discovery. Then, bit by bit, customize the agents and commands to your workflow. Create the `personal/` folder and add your build instructions, coding preferences, and project context.

The configuration is designed to be portable—the `personal/` folder is gitignored to keep project-specific customizations local while sharing the generic infrastructure.

## Acknowledgments

Thanks to [Dexter Horthy](https://github.com/dexhorthy) for coining the term "context engineering" and to [Ashley Ha](https://medium.com/@ashleyha/i-mastered-the-claude-code-workflow-145d25e502cf) for writing a detailed blog explaining the workflow that inspired this configuration. The commands and agents were originally inspired by [HumanLayer](https://github.com/humanlayer/humanlayer) and then modified for my workflow as a robotics controls engineer working with C++ and Python.

---

*The `.claude` configuration is available in my [github repository](https://github.com/shlok-agarwal/.claude). Feel free to clone it and make it your own.*
