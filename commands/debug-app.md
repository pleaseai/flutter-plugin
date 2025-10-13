---
description: Do a deep dive to debug a complex issue in a Dart or Flutter app or package.
---

We're going to debug a Dart or Flutter application. Your goal is to help the user debug an issue in their Dart or Flutter application. Follow these steps methodically.

## Problem Specification

Begin by prompting the user for a detailed description of the problem. Ask them to include:

- The symptoms of the bug.
- The expected behavior of the application.
- Specific, step-by-step instructions to reproduce the issue, if available.
- Any available error messages, stack traces, or logs.

After the user provides the initial description, ask clarifying questions until you have a clear and unambiguous understanding of the problem.

## Information Gathering

Next, collect additional information required for debugging. Ask the user one question at a time. Your questions should gather the following details:

- Ask the user to select a target device. Use the `list_devices` tool to present them with a list of available devices to run the app on.
- The root directory of the project and the main entry point file (e.g., `lib/main.dart`).
- Any debugging steps the user has already attempted, and their outcomes.
- Whether they want to fix the bug on a new branch or the current one. Suggest a branch name.

## Dependency and Environment Checks

Before diving into the code, let's verify the project's dependencies and environment.

- [ ] Run `flutter doctor` to get the Flutter and Dart SDK versions and check for any issues reported.
- [ ] Use the `pub` tool with the `outdated` command to look for outdated packages or dependency conflicts in `pubspec.yaml` and `pubspec.lock`.
  - Run the command `pub` tool with `upgrade` to upgrade to latest versions.
  - If that isn't sufficient, sometimes upgrading the package version to a new major version can help. The `pub` tool can't do this, so run the command `dart pub upgrade --major-versions` to do this.

## Initial Triage

Before developing a full debugging plan, perform initial checks to establish a baseline of the project's health.

- [ ] Use the `analyze_files` tool to check for static analysis issues.
- [ ] Use the `run_tests` tool to check for any failing tests.

If any issues are discovered, explain their potential impact and recommend a plan to resolve them first. If the user chooses to proceed, acknowledge their choice and continue with the primary debugging task.

## Debugging Plan

Based on the information gathered, formulate a detailed, step-by-step debugging plan. The plan must be presented to the user for their approval before you begin execution.

The debugging strategy should be chosen to yield the best results and may involve a combination of the following techniques. Tailor your plan to the specific type of bug.

- **Initial Hypothesis:** Start by stating a clear hypothesis about the cause of the bug. This will guide the debugging process.

- **Reproduction & Observation:**
  - Use the `launch_app` tool to start the application and reproduce the issue.
  - For complex UI interactions, use the `flutter_driver` tool to automate the steps.
  - While the app is running, use `get_runtime_errors` to monitor for exceptions.

- **Logging and Tracing:**
  - Add strategic logging statements to the code to trace execution flow. Prefer `debugPrint()` over `print()` for cleaner, non-interfering output.
  - Use `hot_reload` to apply logging changes quickly while preserving the app's state. If the state needs to be reset, explain that a Hot Restart is needed, and you will need to stop and restart the app.

- **Flutter DevTools & UI Inspection:**
  - **For UI and layout bugs:** Use the `get_widget_tree` tool to inspect the widget hierarchy and properties.
  - **Indicating widgets:** Allow the user to indicate a widget to check using the `set_widget_selection_mode` and `get_selected_widget` tools to allow them to click on a widget to select it.

- **Advanced Debugging Dumps:**

  Propose using Flutter's `debugDump*()` functions for deep inspection when necessary. These can be called from code (e.g., inside a button's `onPressed` handler) in a debug build and will write copious output to the logs. Be careful where you put these: they can produce too much output to process if placed in build functions, etc. Some strategies to reduce that are: trigger them from an event like a button click, or have a bool that prevents them from running more than once, etc.

  If you want to look at the widget tree only, the get_widget_tree tool returns much less verbose output.

  - `debugDumpApp()`: To get a complete picture of the widget tree.
  - `debugDumpRenderTree()`: For complex layout issues, to inspect the render tree's constraints and sizes.
  - `debugDumpLayerTree()`: For painting and compositing problems.
  - `debugDumpSemanticsTree()`: For accessibility-related issues.
  - `debugDumpFocusTree()`: For debugging keyboard input and focus management.

- **Assertions:**
  - Propose adding `assert()` statements to the code to verify assumptions and invariants. This can help catch logical errors early during development.

- **Test-Driven Debugging:**
  - For complex logic bugs, propose writing a new unit or widget test that specifically reproduces the bug in isolation. This allows for faster, more focused iteration on a fix.

Write the plan to DEBUGGING_PLAN.md in the package root.

Do not proceed until the user has explicitly approved the plan.

## Execution and Iteration

Execute the approved plan one step at a time. This is an iterative process:

- After each step, report your findings to the user.
- If the results from a step provide new insights, propose modifications to the debugging plan and update the plan document.
- When a potential fix is implemented, verify it by attempting to reproduce the original bug and by running all tests to check for regressions.
- When a fix is found, if a test doesn't already cover that case, propose adding a test to prevent regression.

## Finalization

Once the bug is confirmed to be fixed and the application is stable:

- [ ] Remove any temporary debugging code (e.g., logging statements that aren't generally useful).
- [ ] Run `dart_fix`, `dart_format`, `analyze_files`, and `run_tests` to ensure the codebase is clean and healthy.
- [ ] Prepare a descriptive commit message for the fix, following the "Conventional Commits" specification. The message should include a subject, an optional body explaining the "why" behind the change, and a footer (e.g., `Fixes: #123`) if the user provides an issue number or link. Present the message to the user for approval before committing the changes.
  - Do not include the DEBUGGING_PLAN.md file in the commit. When done, ask the user if they would like to remove it.
