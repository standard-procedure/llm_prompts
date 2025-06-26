# Suggest a high level task list for a Feature Specification

## Goal

To guide an AI assistant in creating a high level task list based upon an existing Feature Specification Document (stored in Linear as an Issue with ID $ARGUMENTS). The task list should provide a discussion point for building a detailed task list in future.  

## Output

The tasks generated will be created and stored as a hierarchy of sub-issues within the original Feature Specification's Linear Issue.  

## Process

1.  **Receive Feature Specification Reference:** The user points the AI to a specific Linear Issue (identified as $ARGUMENTS) containing the Feature Specification.
2.  **Analyze Feature Specification:** The AI reads and analyzes the functional requirements, user stories, and other sections of the Feature Specification.
3.  **Understand the Project Documentation:** The AI should read the project style guide and glossary to ensure the code structures and names it suggests fit with the overall pattern of the project.  
4.  **Phase 1: Suggest Tasks:** Based on the Feature Specification analysis, decide on the main, high-level tasks required to implement the feature. These are likely to represent different user journeys through the feature.  Use your judgement on how many high-level tasks to use (it's likely to be about 5). Present these tasks to the user in the specified format (without sub-tasks). Feel free to create a folder within `docs/tasks` that holds individual markdown files for each parent task, to help keep track of the work that will be needed.  When done, inform the user: "This is my outline for the tasks that will be needed, based on the Feature Specification."
5.  **Respond to Feedback:** If the user has feedback on any of the tasks, rewrite and update the tasks, taking that feedback in to account.  Update the markdown files containing the task contents.  Continue in this way until the user has confirmed they are happy with all the tasks.  
6.  **Phase 2: Generate Outline Tasks:** Once the user confirms, repeat the following steps for each high-level task in turn: 
    2. **Outline Relevant Files and Acceptance Criteria:** Based on the tasks and Feature Specification, identify the models, controllers, tests and specs that will be necessary.  The models and controllers will implement the feature while the specs will prove that we have met the acceptance criteria for the Feature Specification.  The spec and test files should be at the appropriate levels of abstraction - a small number of full-stack (slow) tests to verify the integration of the most important user paths, with many (smaller and faster) low-level tests for the individual units that make up the feature.  
    3.  **Generate Task Output:** Create a new Markdown document and populate it with the task details, along with the design outline, relevant files and acceptance criteria.  Create a folder in `doc/tasks` named after the feature specification and place the generated outlines as Markdown documents in there (if available). Then, add each outline as a comment to the Feature Specification Issue $ARGUMENTS.
8.  **Generate a Summary:** Present a summary of the outlines.  

## Output Format

The generated outlines _must_ follow this structure:

- Feature Specification - Issue ID $ARGUMENTS
  The original Feature Specification that defines the requirement
  - Comment describing High Level Outline 1
    Design outline
    Acceptance Criteria - including outline RSpec System Specs using Capybara
    Relevant Files - models, controllers, specifications and other files
  - Comment describing High Level Outline 2
    Design Outline 
    Acceptance Criteria 
    Relevant Files

## Interaction Model

The process explicitly requires the AI to request feedback after generating the tasks. This ensures the high-level plan aligns with user expectations.

## Target Audience

Assume the primary reader of the task list is a **junior developer** who will implement the feature.
