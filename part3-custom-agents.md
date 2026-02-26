# Part 3 – Custom Copilot Agents

> **Navigation:** [Part 1 – Setup & Chat](part1-setup-and-chat.md) | [Part 2 – Custom Skills](part2-custom-skills.md) | Part 3 | [Part 4 – Issues & Review](part4-issues-and-review.md)

---

## Building Custom Agents

**Goal:** Create a custom Copilot agent — a specialized persona with its own behavior, tool access, and instructions.

### What are Custom Agents?

Custom agents are specialized versions of Copilot tailored to specific workflows. Unlike skills (which are auto-loaded based on relevance), agents are **manually selected** by the user from a dropdown menu in Copilot Chat or on GitHub.com.

Agents are defined as Markdown files with YAML frontmatter, placed in `.github/agents/`.

### How to think about Skills vs Agents

The simplest way to understand the difference:

- A **skill** is **knowledge** — it teaches Copilot *how to do something*. Think of it like a reference card or a runbook. Copilot picks it up automatically whenever it's relevant, regardless of which "mode" you're in. A skill about your CI pipeline helps whether you're debugging, writing code, or planning a release.

- An **agent** is a **persona** — it changes *who you're talking to*. When you select an agent, you're switching Copilot's entire personality, focus, and toolset. A code reviewer agent thinks differently than a documentation agent, even when looking at the same code.

Put another way: skills add to what Copilot knows, agents change how Copilot behaves. You can combine both — an agent can pick up skills, giving you a specialized persona that also has access to your team's domain knowledge.

| | Skills | Agents |
|---|--------|--------|
| **Concept** | Knowledge — *how to do a task* | Persona — *who is helping you* |
| **Analogy** | A reference card anyone can pick up | A specialist you bring into the room |
| **Invocation** | Automatic (Copilot loads when relevant) | Manual (you select from a dropdown) |
| **Effect** | Adds knowledge to the current session | Changes behavior, tone, and focus |
| **Tool control** | Inherits from context | Can restrict via `tools` property |
| **Structure** | Folder with `SKILL.md` | Single `.md` file with YAML frontmatter |
| **Location** | `.github/skills/<name>/SKILL.md` | `.github/agents/<name>.md` |
| **MCP servers** | No MCP config | Can configure MCP servers |
| **Combined** | Available to any agent automatically | Can leverage any skill in the repo |

**Documentation:**
[About custom agents](https://docs.github.com/en/copilot/concepts/agents/coding-agent/about-custom-agents)

---

### Exercise A: Create a code review agent

<details>
<summary><b>7. Build a code review agent</b></summary>

#### Step 1 — Create the agents directory

> Make sure you're on your `copilot-hackathon` branch before creating these files.

- [ ] In your repo, create the directory: `.github/agents/`

#### Step 2 — Define the agent

- [ ] Create `.github/agents/code-reviewer.md` — copy the content from the reference file in this repo: [`.github/agents/code-reviewer.md`](https://github.com/Jfhelin/hack/blob/main/.github/agents/code-reviewer.md)

Key things to notice in the file:
- `tools: ["read", "search"]` — this agent can **only** read and search, it cannot edit files
- The prompt defines a review process and explicitly tells the agent not to modify anything
- The `description` field is what Copilot shows in the agent dropdown

#### Step 3 — Test the agent

- [ ] Open **Copilot Chat** in your IDE.
- [ ] Look for the agent dropdown (model/agent selector) and select **"Code Reviewer"**.
- [ ] Ask it to review a file in your project.
- [ ] Notice how it only uses `read` and `search` — it cannot edit files.

</details>

---

### Exercise B: Create a documentation agent

<details>
<summary><b>8. Build a documentation agent</b></summary>

#### Step 1 — Define the agent

> Make sure you're on your `copilot-hackathon` branch before creating this file.

- [ ] Create `.github/agents/doc-writer.md` — copy the content from the reference file in this repo: [`.github/agents/doc-writer.md`](https://github.com/Jfhelin/hack/blob/main/.github/agents/doc-writer.md)

Key things to notice:
- `tools: ["read", "search", "edit"]` — unlike the reviewer, this agent **can** modify files
- The prompt focuses on documentation, not code logic
- Compare the tool lists between the two agents — this is how you shape what an agent can do

#### Step 2 — Test it

- [ ] Select the **"Doc Writer"** agent in Copilot Chat.
- [ ] Ask it to document a function or module in your project.
- [ ] Notice it has `edit` access — it can create and modify documentation files.

</details>

---

### Key Takeaways

- Agents give you **persona-based control** — you define what the agent can do, what tools it has, and how it behaves.
- The `tools` property is powerful — restricting tools shapes the agent's capabilities (e.g., a reviewer that can read but not edit).
- Agents can be shared across an organization or enterprise by placing them in a `.github-private` repository (see [docs](https://docs.github.com/en/copilot/concepts/agents/coding-agent/about-custom-agents#where-you-can-configure-custom-agents)).
- Combine agents with skills for maximum effect: agents define *who* is helping, skills define *what* they know.

---

**Next up:** [Part 4 – Issues, Coding Agent & Review](part4-issues-and-review.md) *(continues at step 9)*
