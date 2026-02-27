# Part 1 – Setup & Exploring Copilot Chat

> **Navigation:** Part 1 | [Part 2 – Custom Skills](part2-custom-skills.md) | [Part 3 – Custom Agents](part3-custom-agents.md) | [Part 4 – Issues, Coding Agent & Review](part4-issues-and-review.md)

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
- [Getting started with GitHub Copilot](https://docs.github.com/en/copilot/get-started/quickstart)
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

[Use Copilot Chat to understand code](https://docs.github.com/en/copilot/how-tos/chat-with-copilot/chat-in-ide)
</details>

---

<details>
<summary><b>4. Generate a <code>copilot-instructions.md</code> file</b></summary>

Copilot can analyse your codebase and generate a **project instructions file** automatically. This file tells Copilot how your project is structured, how to build and run it, and what conventions to follow — so every future chat response is more accurate and consistent.

### Why we're doing this
The `.github/copilot-instructions.md` file acts as a **persistent project briefing** for Copilot.
It summarizes:
- How the project is structured and what it does
- How to build, test, and run it
- Key dependencies, conventions, and architecture decisions

When this file exists, Copilot automatically includes it as context in every request — you don't need to repeat yourself each session.

### Steps
> Make sure you're on your `copilot-hackathon` branch before generating the file.

- [ ] Open **Copilot Chat** in VS Code (Agent mode)
- [ ] Type `/init` and press Enter
- [ ] Copilot will analyse your workspace and create `.github/copilot-instructions.md`

Once it's created, open the file and read what Copilot generated.
You can edit and expand it freely — any updates will be picked up automatically in future conversations.

### Verify the file is loaded as context
- [ ] Open a **new Copilot Chat** session and ask a question about your project, e.g. "What is this project?"
- [ ] Once Copilot responds, **expand the references list** at the top of the reply
- [ ] Confirm that `.github/copilot-instructions.md` is listed — this means it's automatically included as context for every response going forward.

**Documentation:**
[Customize AI in VS Code – Set up your project for AI](https://code.visualstudio.com/docs/copilot/customization/overview#_set-up-your-project-for-ai)
</details>

---

**Next up:** [Part 2 – Custom Copilot Skills](part2-custom-skills.md) *(continues at step 5)*
