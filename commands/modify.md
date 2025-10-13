---
description: Perform a modification of your Flutter or Dart project.
---

We're going to modify some Dart or Flutter project code.

## Problem specification

First, prompt the user for a description of what the purpose and details of the modification will be.

Once the user has specified the description and purpose of the modification, outline the information that you will be collecting before creating the design and implementation plan, and present the list to the user, along with your first question.

## Collecting Information

Next, collect remaining information from the user, one question at a time.

The information you need to collect includes, but might not be limited to:

- If there are ambiguous elements to the modification, ask the user questions to clarify. When the goal is clear, or the user says to, then move on.
- Whether to do the work on the current git branch, or a new feature branch.
  - Suggest a branch name, making sure it is a valid git branch name.

## Initialize workspace

First, make sure there are no uncommitted changes on the current branch. If there are, notify the user and ask what they would like to do about them before proceeding.

If the user wants the work done on a new branch, create the branch now.

## Modification design document

Develop a **DETAILED** Markdown-formatted design document that follows all of the guidance you have about Dart and Flutter design patterns, rules, best practices, and core principles. Save the design document in MODIFICATION_DESIGN.md in the top directory of the workspace. Feel free to use your available tools to research any aspects of the modification that are unclear.

The design doc should (at least) include:

- An overview
- A detailed analysis of the goal or problem
- Alternatives considered
- A detailed design for the modification
- Any diagrams needed to explain the modification or the design, in Mermaid format.
  - Be sure to put quotes around labels that include special characters (e.g. parenthesis).
- A summary of the design
- References to research URLs used to arrive at the design.

Be sure to **actually fetch and read** the research URLs **before** writing the design document. Do actual web research on the topics that are important to the design.

You must ask the user to review this design document and they must approve it before you continue on to create the implementation plan. They must review and approve it first because if they ask for any changes, it may affect the implementation plan.

## Implementation plan

After getting explicit approval from the user for the MODIFICATION_DESIGN.md document, develop a **DETAILED** Markdown-formatted phased implementation plan of checkboxed tasks that need to be performed in order to finish the modification. Save the implementation plan in MODIFICATION_IMPLEMENTATION.md in the top of the repo.

The implementation plan should include a section for a "Journal" which will be updated after each phase and contain a log of the actions taken, things learned, surprises, and deviations from the plan. It should be in chronological order.

The plan should include instructions similar to: "After completing a task, if you added any TODOs to the code or didn't fully implement anything, make sure to add new tasks so that you can come back and complete them later." to prevent leaving tasks unfinished.

In the first phase of the implementation plan, include:
- [ ] Run all tests to ensure the project is in a good state before starting modifications.

The implementation plan should specify after each phase that you should:

- [ ] Create/modify unit tests for testing the code added or modified in this phase, if relevant.
- [ ] Run the dart_fix tool to clean up the code.
- [ ] Run the analyze_files tool one more time and fix any issues.
- [ ] Run any tests to make sure they all pass.
- [ ] Run dart_format to make sure that the formatting is correct.
- [ ] Re-read the MODIFICATION_IMPLEMENTATION.md file to see what, if anything, has changed in the implementation plan, and if it has changed, take care of anything the changes imply.
- [ ] Update the MODIFICATION_IMPLEMENTATION.md file with the current state, including any learnings, surprises, or deviations in the Journal section. Check off any checkboxes of items that have been completed.
- [ ] Use `git diff` to verify the changes that have been made, and create a suitable commit message for any changes, following any guidelines you have about commit messages. Be sure to properly escape dollar signs and backticks, and present the change message to the user for approval.
- [ ] Wait for approval. Don't commit the changes or move on to the next phase of implementation until the user approves the commit.
- [ ] After commiting the change, if an app is running, use the hot_reload tool to reload it.

In the last phase of the plan, include steps to:

- [ ] Update any README.md file for the package with relevant information from the modification (if any).
- [ ] Update any GEMINI.md file in the project directory so that it still correctly describes the app, its purpose, and implementation details and the layout of the files.
- [ ] Ask the user to inspect the package (and running app, if any) and say if they are satisfied with it, or if any modifications are needed.

You must ask the user to review this implementation plan and they must approve it before starting implementation. They must review and approve it before you begin because if they ask for any changes, the changes may affect the implementation.

## Implementation

After getting explicit approval from the user for the MODIFICATION_IMPLEMENTATION.md document, begin implementing the plan.
