This document is a comprehensive and highly structured operational blueprint for an advanced AI agent, likely designed for software development within an environment called "Cursor." It defines the agent's core principles, systems, workflows, and learning mechanisms.

In simple terms, this is the "mind" and "nervous system" of an AI programmer. It's not a simple prompt but a detailed constitution that dictates how the agent thinks, plans, codes, learns, and remembers.

### Meaning of Each Component

Here is a breakdown of what each section means in plain English:

**Core Reasoning Engine (Ω\*)**

- **What it is:** The central "brain" of the AI.
- **Its Goal:** To achieve the best possible understanding and reasoning that aligns with the user's intent.
- **How it Works:** It uses multiple modes of thinking (logic, analogy, exploration), breaks down problems into smaller pieces, forms hypotheses, and evaluates them based on confidence and evidence. It has built-in safeguards to prevent common engineering mistakes like over-complicating things or creating solutions before the problem is fully understood.

**Contradiction Resolution (D\*)**

- **What it is:** The AI's system for handling conflicting information or instructions.
- **Its Goal:** To resolve contradictions logically.
- **Its Priority:** When faced with a conflict, it prioritizes **1. The user's intent**, 2. Keeping the system consistent, and 3. Optimizing the solution.

**Planning System (P\*)**

- **What it is:** The project manager component.
- **Its Goal:** To ensure every action is part of a clear and efficient plan.
- **Its Core Rule:** **Always plan first.** The workflow is to think, analyze the existing code, ask clarifying questions, draft a plan, and _then_ execute it using the "Cursor" to-do list feature.

**Memory Bank (M\*)**

- **What it is:** The AI's long-term memory, stored in a specific folder (`.cursor/memory/`).
- **Its Goal:** To maintain a deep, persistent understanding of the project.
- **Its Core Rule:** It **must read all memory files at the start of a session.** This gives it immediate context on the project's vision, architecture, and progress. It automatically updates its memory when major changes happen.

**Coding Standards (C\*)**

- **What it is:** The AI's rulebook for writing high-quality code.
- **Its Goal:** To produce clean, maintainable, and reliable code.
- **Its Principles:** Includes standard best practices like KISS (Keep It Simple, Stupid), DRY (Don't Repeat Yourself), and writing modular code. It makes changes only when it is certain about them.

**Technology Stack (Θ\*)**

- **What it is:** The list of approved technologies for the project.
- **Its Goal:** To ensure the AI uses the correct technical stack (e.g., Node.js, React, SQL) and avoids unapproved ones.

**Rule Learning System (Λ\*)**

- **What it is:** The AI's ability to learn and create its own rules.
- **Its Goal:** To adapt and become more efficient over time.
- **How it Works:** If it notices a recurring pattern or solution more than a few times, it can automatically draft a new rule for itself to follow in the future. These rules are stored in a `.cursor/rules/` folder.

**Task Management (T\*)**

- **What it is:** The AI's to-do list manager, which is integrated directly with Cursor's native "todo" feature.
- **Its Goal:** To break down complex plans into small, trackable steps and manage their execution.
- **How it Works:** It automatically populates the to-do list when a plan is approved and updates the status as it completes each item.

**Test-Driven Development (TDD\*)**

- **What it is:** A system that enforces a "test-first" approach to development.
- **Its Goal:** To ensure new code is reliable and well-tested.
- **Its Core Rule:** For new features, it must first write a test that specifies what the code should do. The test will fail initially, and the AI's job is to write the code that makes it pass.

**Pattern Abstraction (Φ\*)**

- **What it is:** A higher-level thinking process for identifying recurring design concepts.
- **Its Goal:** To recognize and capture architectural patterns and conventions, which helps maintain consistency.

**Diagnostics & Refinement (Ξ\*)**

- **What it is:** The AI's self-maintenance and debugging system.
- **Its Goal:** To log errors, find their root causes, and clean up the codebase (e.g., remove dead code).
- **How it Works:** If an error occurs too often, this system will ask the Rule Learning System (`Λ*`) to create a new rule to prevent it.

**Cognitive Trace (Ψ\*)**

- **What it is:** The AI's "black box" flight recorder.
- **Its Goal:** To log its entire thought process for a given task.
- **How it Works:** It records the reasoning chain, errors encountered, rules applied, and actions taken. This is invaluable for understanding why the AI made a particular decision.

**Event Hooks (Σ_hooks) & CRITICAL RULES**

- **What they are:** The "nervous system" that connects all the other components.
- **Their Goal:** To automate the AI's workflow by triggering specific actions in response to events (e.g., `on_session_start` or `on_error_detected`). The Critical Rules are non-negotiable and enforce the most important principles, like "Always plan first."

---

### Step-by-Step Demonstration of a Complete Task

Here’s how the AI would handle a request to "add a new user profile page" based on this blueprint.

**Step 1: Session Start & Context Loading**

- The user starts a session with the AI.
- **`on_session_start` hook fires.**
- The AI's **Memory (`M*`)** system immediately reads all files in the `.cursor/memory/` folder: `projectBrief.md`, `techContext.md`, `systemPatterns.md`, etc.
- It now has full project context: it knows the tech stack, architectural rules, and business goals.

**Step 2: Task Analysis and Planning**

- The user gives the task: "Add a new user profile page."
- The **Planning System's (`P*`)** critical rule `always_plan_first` is activated.
- The **Reasoning Engine (`Ω*`)** breaks down the task. It consults **Memory (`M*`)** for existing UI components and the **Tech Stack (`Θ*`)** to confirm it should use React. It checks the **Rule Learning System (`Λ*`)** for any specific rules about creating new pages.
- The AI determines it needs more information and asks clarifying questions, like: "1. What specific user details should be displayed? 2. Should there be an 'edit' button? 3. What is the URL endpoint for user data? 4. Does this page need specific access permissions?"

**Step 3: Plan Approval and Task Decomposition**

- The user answers the questions.
- The AI creates a detailed plan and presents it.
- Once the user approves the plan, the **`on_plan_created` hook fires.**
- The **Task Management system (`T*`)** automatically populates the Cursor to-do list with atomic sub-tasks:
  - `[ ] CRITICAL: Create test specification for the profile page component (TDD.spec_first).`
  - `[ ] HIGH: Create a new React component file: ProfilePage.js.`
  - `[ ] HIGH: Fetch user data from the API.`
  - `[ ] MEDIUM: Render user data in the component.`
  - `[ ] LOW: Add basic styling according to systemPatterns.md.`

**Step 4: Execution via Test-Driven Development**

- The AI starts with the first to-do item.
- The **TDD System (`TDD*`)** takes over. It creates a test file (`ProfilePage.test.js`) that defines what the component should do (e.g., "it should display the user's name when given user data").
- It runs the test, which fails (because the component doesn't exist yet).
- The AI now proceeds to the next to-do item: creating `ProfilePage.js`. It writes just enough code to make the test pass, strictly following the **Coding Standards (`C*`)**.
- As it saves the file, the **`on_file_modified` hook** might trigger the **Rule System (`Λ*`)** to check for compliance with linting or architectural rules.

**Step 5: Completion, Memory Update, and Learning**

- Once a to-do is finished and its test passes, the **`on_todo_completed` hook fires.**
- The **Task System (`T*`)** marks the item as done in Cursor.
- The **Memory System (`M*`)** updates `progress.md` to log the completed work.
- The **Cognitive Trace (`Ψ*`)** logs the entire cycle: the reasoning, the code, and the test result.
- During this process, if the AI notices a new, reusable way of fetching data, the **Pattern Abstraction (`Φ*`)** system will note it. If it happens often, the **Rule Learning (`Λ*`)** system may suggest creating a new rule for it.

**Step 6: Task Completion and Final Report**

- The AI repeats Step 4 and 5 for all items in the to-do list.
- Once all tasks are marked complete in Cursor, the AI reports back to the user that the profile page is finished, live, and fully tested. It might also mention any new patterns it observed or potential improvements for the future, based on its **Diagnostics (`Ξ*`)** and **Cognitive Trace (`Ψ*`)** logs.
