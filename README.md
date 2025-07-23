# AI Rules: A Cognitive Architecture for Autonomous Software Development

This repository contains the operational blueprint for an advanced AI agent designed for autonomous software development within the Cursor IDE. It defines the agent's core reasoning, planning, learning, and memory systems, acting as a "constitution" that governs its behavior.

The core of this system is defined in the [`cursor-rules.txt`](./cursor-rules.txt) file.

## Core Concepts

The AI's architecture is built upon several key systems:

| System                             | Description                                                                                                                             |
| ---------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| **Ω\* (Omega): Core Reasoning**    | The AI's "brain." It uses multiple thinking modes (logical, analogical, exploratory) to break down problems and form hypotheses.        |
| **D\*: Contradiction Resolution**  | Manages conflicting information, prioritizing user intent above all else.                                                               |
| **P\*: Planning System**           | The project manager. It enforces a **"plan-first"** workflow for all complex tasks.                                                     |
| **M\*: Memory Bank**               | The AI's persistent memory. It reads all context files at the start of a session to understand the project's vision and status.         |
| **C\*: Coding Standards**          | The rulebook for writing clean, modular, and maintainable code, following best practices like KISS and DRY.                             |
| **Λ\* (Lambda): Rule Learning**    | Allows the AI to learn from recurring patterns and autonomously generate new rules to improve its efficiency over time.                 |
| **T\*: Task Management**           | Integrates with Cursor's native TODOs to break down plans into atomic, trackable tasks.                                                 |
| **TDD\*: Test-Driven Development** | Enforces a "test-first" approach, ensuring that all new features are built on a foundation of clear specifications and are verifiable.  |
| **Ψ\* (Psi): Cognitive Trace**     | A "black box" recorder that logs the AI's entire thought process for transparency and debugging.                                        |
| **Σ_hooks: Event Hooks**           | The nervous system that connects all components, automating workflows by triggering actions based on events (e.g., `on_session_start`). |

---

## How It Works: A Practical Example

Here’s a simplified step-by-step demonstration of how the AI would handle a request to **"add a new user profile page"**:

### 1. Context Loading (on_session_start)

- The session starts, and the `on_session_start` hook fires.
- **Memory (M\*)** reads all project files (`projectBrief.md`, `techContext.md`, etc.) to load the complete project context.

### 2. Planning (P\*)

- The user provides the task.
- The **Planning System (P\*)** activates its `always_plan_first` rule.
- The **Reasoning Engine (Ω\*)** analyzes the task, consults its memory for existing patterns, and asks clarifying questions to fully define the requirements.

### 3. Task Creation (T\*)

- Once the user approves the plan, the `on_plan_created` hook fires.
- The **Task Management System (T\*)** automatically creates a list of sub-tasks in Cursor's TODO panel, such as:
  - `[ ] Write test specification for the profile page.`
  - `[ ] Create the React component.`
  - `[ ] Fetch user data from the API.`
  - `[ ] Style the component.`

### 4. Test-Driven Development (TDD\*)

- The AI begins with the first task: creating a failing test for the new component.
- It then writes the necessary code to make the test pass, adhering to the **Coding Standards (C\*)**.

### 5. Completion and Learning (M\* & Λ\*)

- As each task is completed, the `on_todo_completed` hook fires.
- The **Task System (T\*)** marks the TODO as done.
- The **Memory System (M\*)** logs the progress.
- The **Cognitive Trace (Ψ\*)** records the entire process. If any new, reusable patterns are identified, the **Rule Learning System (Λ\*)** may propose a new rule for future use.

This cycle continues until all tasks are complete, ensuring a structured, transparent, and high-quality development process.
