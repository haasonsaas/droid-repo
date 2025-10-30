# Factory Droids Collection

This repository provides a set of reusable **Factory.ai** custom droids that you can drop into your project to delegate specialized tasks.  Each droid is defined in the `.factory/droids` directory as a Markdown file with YAML front‑matter.

## Setup

1. **Enable custom droids** – In the Factory CLI, run `/settings` and toggle **Custom Droids** under the experimental section.  Restart the CLI afterward.
2. **Install the droids** – Copy the `.factory/droids` directory from this repository into the root of your project (e.g. `<repo>/.factory/droids/`).  Alternatively, place the files in your personal directory `~/.factory/droids/` if you want them available globally.
3. **Reload** – Run `/droids` in the CLI to see the list of available droids and verify that they loaded correctly.

## Available droids

### `oracle`

A senior engineering advisor that plans, reviews and provides expert guidance on complex tasks.  Use it for architecture reviews, complex implementation planning, debugging across files, and answering tough technical questions.  It has read‑only access to your code and can search the web, but it will not perform simple file operations or code modifications.

**Invocation example:**

```text
Run the subagent `oracle` to review our authentication system and propose improvements.
```

### `code‑reviewer`

Performs in‑depth reviews of diffs.  Summarizes the intent of the change, flags correctness risks, missing tests, and migration fallout, and calls out follow‑up actions.

**Invocation example:**

```text
Use the subagent `code-reviewer` on the staged diff.
```

### `security‑sweeper`

Scans recently edited files for insecure patterns and suggests mitigations.  It identifies injections, insecure transport, privilege escalation and secrets exposure, and links to relevant CWE entries when possible.

**Invocation example:**

```text
Run `security-sweeper` to audit the changed files in this patch for security issues.
```

### `architecture‑planner`

Helps you design new features or refactorings.  When given a goal, it proposes a high‑level architecture (modules, APIs, data flows), identifies risks and dependencies, and outlines implementation steps.

**Invocation example:**

```text
Ask the subagent `architecture-planner` to propose a high-level design for adding real-time collaboration to our app.
```

## Creating your own droids

To define your own droid, create a new Markdown file in `.factory/droids/` with YAML front‑matter specifying at least `name`, and optionally `description`, `model` and `tools`.  After the front‑matter, write a clear system prompt describing how the subagent should behave.  See the files in this repository for reference.