# Generating a detailed Task List for a portion of a Feature Specification

## Goal

To guide an AI assistant in creating a detailed, step-by-step task list based upon one aspect of a design for an existing Feature Specification Document. The Feature Specification will already have been broken down in to one or more "steps", detailing the implementation of one aspect of the functionality. The task list should guide a developer through implementation.

## Output

The tasks generated will be created and stored as Markdown files within the `doc/tasks/[feature-name]/step [number]` folder of the project, plus, if available, as sub-issues of the feature specification in Linear.  

## Process

- **Receive Feature Specification Reference and the relevant step:** The user points the AI to a specific step within the plan for a Feature Specification
- **Analyse Feature Specification:** The AI reads and analyzes the scenarios and acceptance criteria for this step, referring to the wider specification if more context is required.  
- **Understand the Project Documentation:** The AI should read the project style guide and glossary to ensure the code structures and names it suggests fit with the overall pattern of the project.  
- **Decide on the Sub-Tasks:** Break the step down into smaller, actionable sub-tasks, as necessary to complete the step. Ensure sub-tasks logically follow from one another and cover the requirements of the scenarios in this step.
- **Generate Task Output:** For each sub-task, create a text file recording the implementation notes.  If available, also create a sub-issue in Linear.  
8.  **Optionally assign the tasks in Linear:** Ask the user if they have a preferred team member to complete these tasks.  They may respond with no, in which case, keep the tasks as unassigned.  If they respond with a single team member, assign all the newly created tasks to that team member.  If they respond with multiple team members, ask which sub-tasks should be assigned to which team member, then assign the issues accordingly.  
9.  **Optionally schedule the tasks in Linear:** Ask the user if they would like to schedule the issues, either in the current cycle or the next one - and if so, update the issues accordingly.  Only schedule the detailed tasks, do not schedule Issue $ARGUMENTS or its parent Feature Specification.  
8.  **Generate a Summary:** Present a summary of the task list.  

## Sub Tasks

When deciding on sub-tasks:
- Include detailed descriptions of any database migrations including fields, data types, foreign keys and indices.
- Provide outlines of ruby models without writing the actual code - list the associations, enums, validations and normalisations required plus important methods
- Provide full model specs
- Provide the routes required but do not write the controllers
- Provide full request specs, ensuring authentication and authorisation are fully tested

## Output Format

Each task file should contain notes to assist the developer complete the task.  

See [plan.md](plan.md) for details of where each step should be placed, both in the filesystem and in Linear.  

## Interaction Model

The process explicitly requires interaction with the user to ensure that the created Issues are assigned and scheduled correctly.  

## Target Audience

Assume the primary reader of the task list is a **junior developer** who will implement the feature.

## Final instructions

1. Do NOT start implementing a fix to the step
