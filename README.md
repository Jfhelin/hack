# GitHub Copilot Hackathon

A hands-on hackathon guide for exploring GitHub Copilot's latest features — from chat modes and custom instructions to skills, agents, MCP integration, and AI-powered code reviews.

## How to use

This hackathon is designed to be run interactively. Work through the parts in order:

| Part | Topic | File |
|------|-------|------|
| 1 | Setup & Exploring Copilot Chat | [part1-setup-and-chat.md](part1-setup-and-chat.md) |
| 2 | Custom Copilot Skills | [part2-custom-skills.md](part2-custom-skills.md) |
| 3 | Custom Copilot Agents | [part3-custom-agents.md](part3-custom-agents.md) |
| 4 | MCP, Issues, Coding Agent & Review | [part4-issues-and-review.md](part4-issues-and-review.md) |

## Reference files

This repo includes reference implementations you can copy into your own projects:

```
.github/
├── skills/
│   ├── hello-ascii/SKILL.md    # Explicit skill — triggers on specific requests
│   └── greeting/SKILL.md       # Implicit skill — triggers on any greeting
└── agents/
    ├── code-reviewer.md         # Read-only code review agent
    └── doc-writer.md            # Documentation agent with edit access
```

## Prerequisites

- A GitHub account with Copilot access
- An IDE with the GitHub Copilot extension (VS Code recommended)
- A repository to experiment in
