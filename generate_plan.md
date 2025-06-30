# Suggest a high-level plan for implementing a Feature Specification

## Goal

To guide an AI assistant in creating a high level task list based upon an existing Feature Specification Document (stored in Linear as an Issue with ID $ARGUMENTS). The task list should provide a discussion point for building a detailed task list in future.  

## Output

The tasks generated will be created and stored as comments within the original Feature Specification's Linear Issue.  

## Process

1.  **Receive Feature Specification Reference:** The user points the AI to a specific Linear Issue (identified as $ARGUMENTS) containing the Feature Specification or a feature that is specified within the `docs/features` folder.
2.  **Analyze Feature Specification:** The AI reads and analyzes the functional requirements, scenarios, and other sections of the Feature Specification.
3.  **Understand the Project Documentation:** The AI should read the project style guide and glossary to ensure the code structures and names it suggests fit with the overall pattern of the project.  
4.  **Phase 1: Suggest a plan:** Based on the Feature Specification analysis, decide on a plan to implement this feature.  It's likely that the plan will break down into a number of steps, each representing one or more scenarios from the specification.  Suggest an order that these steps should be implemented in.  Do not start deciding on the individual tasks within each step yet.  Present this plan to the user.  
5.  **Respond to Feedback:** If the user has feedback on the plan, take that into account and rewrite the plan.  Present the revised plan to the user and respond to feedback again, until the user is happy.  
6.  **Phase 2: Generate Outline Tasks:** Once the user confirms, repeat the following steps for each step within the plan: 
    2. **Outline Relevant Files and Acceptance Criteria:** Based on the Feature Specification, identify the models, controllers, tests and specs that will be necessary.  The models and controllers will implement the feature while the specs will prove that we have met the acceptance criteria for the Feature Specification.  The spec and test files should be at the appropriate levels of abstraction - a small number of full-stack (slow) tests to verify the integration of the most important user paths, with many (smaller and faster) low-level tests for the individual units that make up the feature.  
    3.  **Generate the Plan Output:** Write the plan to the `docs/tasks/[feature-name]` folder as a series of individual, numbered, markdown files.  These should contain the scenario, relevant files and acceptance criteria for that step.  Then, if available, add each step as a comment to the Feature Specification Issue $ARGUMENTS.
8.  **Generate a Summary:** Present a summary of the outlines.  

## Output Format

Each step file should contain the scenarios, relevant files and acceptance criteria.  

See [plan.md](plan.md) for details of where each step should be placed, both in the filesystem and in Linear.  

## Interaction Model

The process explicitly requires the AI to request feedback after generating the tasks. This ensures the high-level plan aligns with user expectations.

## Target Audience

Assume the primary reader of the task list is a **junior developer** who will implement the feature.

## Final instructions

1. Do NOT start implementing a fix to the step
2. Make sure to ask the user clarifying questions
3. Use these answers to improve the plan

