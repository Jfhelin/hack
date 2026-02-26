# Part 1 – Setup & Exploring Copilot Chat

> **Navigation:** Part 1 | [Part 2 – Custom Skills](part2-custom-skills.md) | [Part 3 – Custom Agents](part3-custom-agents.md) | [Part 4 – Issues & Review](part4-issues-and-review.md)

---

## Setup & Preparation

**Goal:** Get your environment and repository ready for Copilot experimentation.

<details>
<summary><b>1. Find or fork a project</b></summary>

- [ ] Pick a repository you're comfortable working in — any language works.
  You can:
  - Use an existing project you maintain.
  - Fork a public repo (e.g. from [GitHub Explore](https://github.com/explore)).

- [ ] Copy the markdown of the relevant part files into issues in your working repo so that you can modify them.

- [ ] Create a **new branch**, e.g. `copilot-hackathon`.
  Keep all experiments in this branch — do **not** modify your `main`.

> Copilot never commits code without your consent, but keep your hackathon work isolated.
</details>

---

<details>
<summary><b>2. Ensure GitHub Copilot is enabled</b></summary>

- [ ] Make sure the **GitHub Copilot** extension is installed and active in your IDE.
- [ ] Ensure you also have **Copilot Chat** available (and optionally **Copilot Edits/Agent** features if supported by your IDE).

**Documentation:**
- [Getting started with GitHub Copilot](https://docs.github.com/en/copilot/getting-started-with-github-copilot)
- [Setting up GitHub Copilot in VS Code](https://code.visualstudio.com/docs/copilot/setup)

> You don't need three separate installs — Copilot Chat and Edits are included in most IDE integrations.
> Just verify both completions and chat are visible in your IDE.
</details>

---

## Exploring Copilot Chat Modes

**Goal:** Learn how Copilot helps you explore, understand, and reason about your code.

<details>
<summary><b>3. Explore your code using Ask mode</b></summary>

Pick a file or function you don't know well and experiment freely with **Copilot Chat**.

Try questions like:
- [ ] "Explain what this function does, step by step."
- [ ] "Where is this class used?"
- [ ] "Could this function be simplified?"
- [ ] "Generate a test for this logic."
- [ ] "Rewrite this using a different algorithm."

Be curious! Ask follow-ups. Ask *why*. Modify prompts.
Try *Ask*, *Explain*, *Generate*, and *Edit* modes to see how each behaves.

- [ ] Switch between models (e.g. `GPT-5 mini`, `Claude Sonnet 4.6`, `Gemini 3 Flash`) and compare reasoning quality.

[Use Copilot Chat to understand code](https://docs.github.com/en/copilot/github-copilot-chat/understanding-your-code-with-github-copilot-chat)
</details>

---

<details>
<summary><b>4. Generate a <code>copilot_instructions.md</code> file</b></summary>

Copilot can generate **project setup and context notes** automatically — this file helps Copilot understand your project and coding style better.

### Why we're doing this
The `copilot_instructions.md` file acts as a **knowledge source** for Copilot.
It summarizes:
- How the project is structured
- How to build and run it
- Key dependencies, conventions, and folders

When this file exists, Copilot can use it to **reason more effectively** about your codebase — for example, it can:
- Give more accurate answers when you ask questions about the project.
- Provide better suggestions for refactoring, debugging, and tests.
- Maintain consistent terminology and architecture decisions in its output.

Think of it as giving Copilot a "project briefing document".

### Steps
> Make sure you're on your `copilot-hackathon` branch before generating the file.

- [ ] Open the **Command Palette** (`Ctrl/Cmd + Shift + P`)
- [ ] Search for **"Copilot: Generate Project Instructions"**
- [ ] Follow the prompts — Copilot will create `.github/copilot-instructions.md`

Once it's created, open the file and read what Copilot generated.
You can edit and expand this file — Copilot will use any updates in future conversations.

### Verify the file is loaded as context
- [ ] Open a **new Copilot Chat** session and ask any question about your project, e.g. "What is this project?"
- [ ] Once Copilot responds, **expand the references list** at the top of the reply (the "Used X references" or similar disclosure)
- [ ] Confirm that `.github/copilot-instructions.md` is listed there — this confirms the file is automatically included as context for every response going forward.

**Documentation:**
[Generate project instructions with Copilot](https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions)
</details>

---

**Next up:** [Part 2 – Custom Copilot Skills](part2-custom-skills.md) *(continues at step 5)*
