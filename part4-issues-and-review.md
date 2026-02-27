# Part 4 – Issues, Coding Agent & Review

> **Navigation:** [Part 1 – Setup & Chat](part1-setup-and-chat.md) | [Part 2 – Custom Skills](part2-custom-skills.md) | [Part 3 – Custom Agents](part3-custom-agents.md) | Part 4

---

## Connecting Copilot to GitHub via MCP

**Goal:** Configure an MCP server so Copilot can interact with your GitHub repo — list issues, create new ones, and more.

### What is MCP?

MCP (Model Context Protocol) is an open standard that lets AI tools connect to external services. By adding the **GitHub MCP server**, you give Copilot the ability to read and write GitHub issues, pull requests, and other repo data directly from your IDE.

<details>
<summary><b>9. Add the GitHub MCP server</b></summary>

#### VS Code (recommended)

Use the built-in MCP management — no need to manually create files.

- [ ] Open the **Command Palette** (`Ctrl/Cmd + Shift + P`)
- [ ] Run **"MCP: Add Server"**
- [ ] Select **HTTP** as the server type
- [ ] Enter the URL: `https://api.githubcopilot.com/mcp/`
- [ ] Give it a name, e.g. `github`
- [ ] Choose **Workspace** to share via source control (make sure you're on your `copilot-hackathon` branch), or **User** for personal use
- [ ] VS Code will show a trust confirmation — accept it to start the server

You can verify it's running:
- [ ] Open the **Command Palette** and run **"MCP: List Servers"**
- [ ] The `github` server should appear and show as connected

> You can also browse and install MCP servers from the **Extensions** panel — type `@mcp` in the search bar to see available servers from the MCP registry.

#### JetBrains (IntelliJ, WebStorm, PyCharm, etc.)

- [ ] Open **Copilot Chat** and ensure you're in **Agent mode**
- [ ] Click the **MCP icon** in the chat window
- [ ] Find the **GitHub** server in the registry list and click **Install**
- [ ] Click **OK** to confirm

Alternatively, for manual setup: click the **Copilot icon** (bottom-right) → **Open Chat** → click the **tools icon** → **Add MCP Tools**, then edit the `mcp.json` file with:

```json
{
  "servers": {
    "github": {
      "url": "https://api.githubcopilot.com/mcp/"
    }
  }
}
```

#### Visual Studio (v17.14+)

- [ ] Open **View → GitHub Copilot Chat**
- [ ] Select **Agent** from the mode dropdown (bottom of the panel)
- [ ] Click the **tools icon** → click the **plus icon**
- [ ] In the "Configure MCP server" popup, set:
  - Server ID: `github`
  - Type: **HTTP/SSE**
  - URL: `https://api.githubcopilot.com/mcp/`
- [ ] Click **Save**

#### Other editors (Eclipse, Xcode)

These editors also support MCP servers via the Copilot Chat MCP icon. Look for the **MCP icon** in the chat window to browse the registry and install the GitHub server.

**Documentation:**
- [MCP servers in VS Code](https://code.visualstudio.com/docs/copilot/customization/mcp-servers) — full reference for VS Code MCP setup
- [Extending Copilot Chat with MCP](https://docs.github.com/en/copilot/how-tos/provide-context/use-mcp/extend-copilot-chat-with-mcp) — setup for all supported IDEs

</details>

---

## Working with Issues via MCP

**Goal:** Use Copilot's MCP connection to explore, understand, and create issues.

<details>
<summary><b>10. Explore and discuss issues (via MCP)</b></summary>

Now that the GitHub MCP server is configured:

- [ ] Use Copilot Chat to list or summarize issues in your repo.
  Examples:
  - "List open issues in this repo."
  - "Summarize issue #12."
  - "Suggest next steps for this bug."
  - "How could we improve code related to this issue?"

[Using GitHub Copilot in Issues](https://docs.github.com/en/copilot/how-tos/chat-with-copilot/chat-in-ide)

> **Copilot not finding your issues?** Click the **tools icon** (the wrench/hammer icon in the chat input bar) to open the tool selection dialog. Verify that the `github` server is listed, shows as **started**, and that its tools are checked. If the server is stopped, click it to start it. If tools are unchecked, enable them and retry your prompt.
> 
> For further troubleshooting, see [MCP servers in VS Code – troubleshooting](https://code.visualstudio.com/docs/copilot/customization/mcp-servers#_troubleshoot-and-debug-mcp-servers).
</details>

---

<details>
<summary><b>11. Analyze code relevant to an issue</b></summary>

- [ ] Pick an interesting issue.
- [ ] Ask Copilot to locate where in the code this occurs, or to explain related logic.

Examples:
> "Show me where this issue might occur in the code."
> "Explain how this module works."
> "What might cause this behavior?"
</details>

---

<details>
<summary><b>12. Generate a new issue</b></summary>

Once you've discussed a potential change, ask Copilot Chat to create a new issue.

- [ ] "Generate a new issue proposing a refactor of this method."
- [ ] "File an issue to add input validation."

Let Copilot generate the issue content directly.
</details>

---

<details>
<summary><b>13. Assign the new issue to Copilot Coding Agent</b></summary>

You can do this in two ways:

- [ ] In Copilot Chat, say **"Assign this issue to the Copilot Coding Agent."**
- [ ] **Or** on **GitHub.com** — open the issue — click **Assignees** — select **@copilot**.

Observe how the Coding Agent interprets and plans the task.

#### Verify the agent is running
- [ ] Go to the **Pull Requests** tab of your repository on GitHub.com — Copilot will have opened a **draft PR** on a branch named `copilot/...` within moments of being assigned.
- [ ] Open the draft PR and click **"View session log"** (or the agent activity link near the top of the PR) to watch the agent's live progress — you'll see it exploring code, running tests, and committing changes in real time.

#### Come back later
- [ ] Once the agent finishes it will mark you as a **reviewer** and you'll receive a notification. Come back, read the diff, and leave review comments if you want it to iterate.

> The agent works entirely in the background via GitHub Actions — you don't need to keep the page open.

[Tracking Copilot's sessions](https://docs.github.com/en/copilot/how-tos/use-copilot-agents/coding-agent/track-copilot-sessions) | [Copilot Coding Agent overview](https://docs.github.com/en/copilot/concepts/agents/coding-agent/about-coding-agent)
</details>

---

## Reviewing and Reflection

**Goal:** Use Copilot to review and reason about existing work.

<details>
<summary><b>14. Request a Copilot code review (on GitHub.com)</b></summary>

- [ ] Go to your repository on **GitHub.com**.
- [ ] Find an existing Pull Request (in your org's main project or your own branch).
- [ ] Assign **@copilot** as a reviewer.

Copilot will analyze the diff and comment directly on the PR.

> This action **updates the PR** with Copilot's review comments.
> *Alternative:* If you prefer, create a **duplicate PR** (from your hackathon branch) and assign Copilot there — this preserves the original untouched.

[Using Copilot for Pull Request reviews](https://docs.github.com/en/copilot/how-tos/use-copilot-agents/request-a-code-review/use-code-review)
</details>

---

## Share Your Insights

- What surprised you most about Copilot's behavior?
- Did different models produce noticeably different results?
- Which feature felt most natural or valuable?
- How could skills and agents improve your team's workflow?

---

## Completion Checklist

- [ ] 1 — Fork / create project branch
- [ ] 2 — Enable Copilot and Chat
- [ ] 3 — Explore Ask mode + models
- [ ] 4 — Generate `.github/copilot-instructions.md`
- [ ] 5 — Create explicit hello-ascii skill
- [ ] 6 — Create implicit greeting skill
- [ ] 7 — Build a code review agent
- [ ] 8 — Build a documentation agent
- [ ] BONUS — Create your own agent
- [ ] 9 — Add the GitHub MCP server
- [ ] 10–12 — Explore, analyze and generate issues
- [ ] 13 — Assign issues to Copilot Coding Agent
- [ ] 14 — Assign PR to Copilot for review
- [ ] Share insights

---

**Start over:** [Part 1 – Setup & Chat](part1-setup-and-chat.md)
