# Part 2 – Custom Copilot Skills

> **Navigation:** [Part 1 – Setup & Chat](part1-setup-and-chat.md) | Part 2 | [Part 3 – Custom Agents](part3-custom-agents.md) | [Part 4 – Issues & Review](part4-issues-and-review.md)

---

## Writing Custom Skills

**Goal:** Extend Copilot's capabilities by writing custom skills that teach it new behaviors.

### What are Copilot Skills?

Skills are folders of instructions and resources that Copilot can load to improve how it responds to specific tasks. Each skill lives in `.github/skills/<skill-name>/` and contains a `SKILL.md` file with instructions.

Key points:
- Skills are automatically loaded by Copilot when it determines they are **relevant** to the user's prompt.
- They work in **Agent mode** in VS Code, the **Copilot Coding Agent**, and **GitHub Copilot CLI**.
- You can also place personal (cross-project) skills in `~/.copilot/skills/<skill-name>/SKILL.md`.

**Documentation:**
[About agent skills](https://docs.github.com/en/copilot/concepts/agents/about-agent-skills)

---

### Exercise A: Create an explicit "Hello ASCII" skill

In this exercise, you'll create a skill that displays "Hello" in ASCII art. You'll need to **explicitly ask** Copilot to use it by referencing it directly.

<details>
<summary><b>5. Create the hello-ascii skill</b></summary>

#### Step 1 — Create the skill folder

> Make sure you're on your `copilot-hackathon` branch before creating these files.

- [ ] In your repo, create the directory: `.github/skills/hello-ascii/`

#### Step 2 — Write the SKILL.md

- [ ] Create `.github/skills/hello-ascii/SKILL.md` with the following content:

```markdown
# Hello ASCII

Display a "Hello" message using ASCII art.

## When to use

When the user explicitly asks to "show hello in ASCII art", "use the hello skill",
or "display an ASCII hello".

## Instructions

Respond with the following ASCII art:

    _   _      _ _
   | | | | ___| | | ___
   | |_| |/ _ \ | |/ _ \
   |  _  |  __/ | | (_) |
   |_| |_|\___|_|_|\___/

Always display the ASCII art exactly as shown. Do not modify or substitute it.
```

#### Step 3 — Test it

- [ ] Open **Copilot Chat** in your IDE (make sure you're in **Agent mode**).
- [ ] Type: **"Show hello in ASCII art"** or **"Use the hello-ascii skill"**.
- [ ] Verify Copilot responds with the ASCII art from your skill.

> If Copilot doesn't pick it up, try reloading your IDE window or starting a new chat session.

</details>

---

### Exercise B: Extend to trigger implicitly on any greeting

Now you'll create a second version of the skill with a **broader description** so that Copilot automatically loads it whenever you simply greet it — no explicit reference needed.

<details>
<summary><b>6. Create the greeting skill</b></summary>

#### Step 1 — Create a new skill folder

> Make sure you're on your `copilot-hackathon` branch before creating these files.

- [ ] Create the directory: `.github/skills/greeting/`

#### Step 2 — Write the SKILL.md

- [ ] Create `.github/skills/greeting/SKILL.md` with the following content:

```markdown
# Greeting

Respond to user greetings with a friendly ASCII art hello.

## When to use

When the user greets you. This includes any of the following:
- "hello", "hi", "hey", "howdy"
- "good morning", "good afternoon", "good evening"
- "greetings", "what's up", "yo"
- Swedish greetings: "hej", "tjena", "hallå", "god morgon", "god kväll"
- Any other conversational greeting or salutation in any language

## Instructions

When a greeting is detected, respond with this ASCII art:

    _   _      _ _       _
   | | | | ___| | | ___ | |
   | |_| |/ _ \ | |/ _ \| |
   |  _  |  __/ | | (_) |_|
   |_| |_|\___|_|_|\___/(_)

Follow the ASCII art with a brief, friendly response. Keep it short and warm.
```

#### Step 3 — Test the implicit trigger

- [ ] Open a **new Copilot Chat session** (Agent mode).
- [ ] Type just: **"Hi"** or **"Good morning"**.
- [ ] Observe whether Copilot responds with the ASCII art greeting — without you mentioning the skill at all.

#### Step 4 — Compare the two versions

- [ ] Try the same greetings with only the `hello-ascii` skill present (rename or delete the `greeting` folder temporarily).
- [ ] Notice how the **broader description** in the greeting skill makes Copilot load it automatically, while the narrower `hello-ascii` version requires explicit references.

> This demonstrates how the **description and "When to use" section** in a skill controls when Copilot decides to load it. Broader descriptions mean more implicit activation.

</details>

---

### Key Takeaways

| Aspect | hello-ascii (explicit) | greeting (implicit) |
|--------|----------------------|---------------------|
| **Trigger** | User must reference it directly | Any greeting triggers it |
| **"When to use"** | Narrow — specific phrases only | Broad — many greeting patterns |
| **Behavior** | Predictable, controlled | Automatic, seamless |
| **Use case** | Specialized tools | Ambient behaviors |

Both approaches are valid — choose based on whether you want **control** or **convenience**.

> **Reference implementations** of both skills are available in this repo under [`.github/skills/`](https://github.com/Jfhelin/hack/tree/main/.github/skills).

---

### Why Skills? Real-world uses for your team

The ASCII art exercises above are intentionally simple — but skills really shine when they encode **team-specific knowledge** that Copilot wouldn't otherwise have. The community `github/awesome-copilot` repository contains hundreds of real skills, and they follow consistent patterns. Consider skills that:

- **Generate conventional commit messages** — a skill like `conventional-commit` that guides Copilot to produce standardized commit messages following the Conventional Commits specification, with type, scope, and description, every time.
- **Plan and validate deployments** — skills like `devops-rollout-plan` or `azure-deployment-preflight` encode your rollout process: preflight checks, step-by-step deployment, verification signals, and rollback procedures.
- **Automate and document GitHub Actions workflows** — a skill like `create-github-action-workflow-specification` captures your CI/CD pipeline structure so Copilot can generate, document, or troubleshoot workflows consistently.
- **Generate tests across languages** — skills like `polyglot-test-agent` teach Copilot to generate comprehensive unit tests for any language in your stack, following your project's testing conventions.
- **Document and onboard** — skills like `architecture-blueprint-generator` or `folder-structure-blueprint-generator` produce standardized architectural documentation from your codebase, giving new developers (and Copilot) a fast path to understanding how the project is structured.

Skills turn Copilot from a general-purpose assistant into one that understands **your** team's way of working. They're version-controlled alongside your code, reviewed in PRs, and shared automatically with everyone on the project.

> Browse the full community skill library at [github/awesome-copilot](https://github.com/github/awesome-copilot/tree/main/skills) for ready-to-use examples you can copy or adapt.

---

### Documentation & Resources

**Getting started:**
- [About agent skills](https://docs.github.com/en/copilot/concepts/agents/about-agent-skills) — overview of what skills are and how Copilot selects them
- [Adding custom instructions for GitHub Copilot](https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions) — broader context on customizing Copilot behavior

**Technical reference:**
- [Creating agent skills](https://docs.github.com/en/copilot/how-tos/use-copilot-agents/coding-agent/create-skills) — file structure, SKILL.md format, and configuration details
- [Custom agents in VS Code](https://code.visualstudio.com/docs/copilot/customization/custom-agents) — how skills, agents, and MCP tools fit together in VS Code

**Community & examples:**
- [awesome-copilot](https://github.com/github/awesome-copilot) — curated collection of community skills, agents, and extensions

---

**Next up:** [Part 3 – Custom Agents](part3-custom-agents.md) *(continues at step 7)*
