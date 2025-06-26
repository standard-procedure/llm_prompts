# Generating a detailed Task List for a portion of a Feature Specification

## Goal

To guide an AI assistant in creating a detailed, step-by-step task list based upon one aspect of a design for an existing Feature Specification Document. The Feature Specification will already have been broken down in to one or more "outlines", detailing the implementation of one aspect of the functionality. The sub-tasks will be stored in Linear as Issues with the Feature Specification being the Parent Issue with ID $ARGUMENTSThe task list should guide a developer through implementation.

## Output

The tasks generated will be created and stored as sub-issues of Issue ID $ARGUMENTS.  

## Process

1.  **Receive Feature Specification Reference and the relevant High Level Outline:** The user points the AI to a specific Linear Issue (identified as $ARGUMENTS) containing the feature specification, plus describes the outline .
2.  **Analyse Feature Specification:** The AI reads and analyzes the functional requirements, user stories, and other sections of the Feature Specification - which are stored in Linear as the Parent Issue of $ARGUMENTS.  This is in order to understand the greater context of this particular task.  
3.  **Analyse the task:**  Next read Issue ID $ARGUMENTS, which is the task that we are working on right now.  This may also be stored in a sub-folder of `docs/tasks` as a Markdown document.  
4.  **Understand the Project Documentation:** The AI should read the project style guide and glossary to ensure the code structures and names it suggests fit with the overall pattern of the project.  
6.  **Decide on the Sub-Tasks:** Break the task down into smaller, actionable sub-tasks, necessary to complete the parent task. Ensure sub-tasks logically follow from the parent task and cover the implementation details implied by the high level task.
7.  **Generate Task Output:** For each sub-task, create a new Issue in Linear as a sub-issue of $ARGUMENTS and populate it with the implementation notes.  
8.  **Optionally assign the tasks:** Ask the user if they have a preferred team member to complete these tasks.  They may respond with no, in which case, keep the tasks as unassigned.  If they respond with a single team member, assign all the newly created tasks to that team member.  If they respond with multiple team members, ask which sub-tasks should be assigned to which team member, then assign the issues accordingly.  
9.  **Optionally schedule the tasks:** Ask the user if they would like to schedule the issues, either in the current cycle or the next one - and if so, update the issues accordingly.  Only schedule the detailed tasks, do not schedule Issue $ARGUMENTS or its parent Feature Specification.  
8.  **Generate a Summary:** Present a summary of the task list with the Issue identifiers from Linear.  

## Output Format

The generated issues _must_ follow this structure:

- Feature Specification - Issue ID $ARGUMENTS
  The original Feature Specification that defines the requirement
  - Comment describing High Level Outline 1
  - Comment describing High Level Outline 2
  - Sub-Issues:
		- Detailed Task 1
			Summary - which part of the parent task is this task about
			Notes - to aid the developer whilst they are completing the task
		- Detailed Task 2
			Summary
			Notes
		- Detailed Task 3
			Summary
			Notes

Because the original Feature Specification contains the original specification, plus the outline implementations, adding the detailed tasks as sub-issues ensures that all related work is easily tracked within Linear.  
    
## Interaction Model

The process explicitly requires interaction with the user to ensure that the created Issues are assigned and scheduled correctly.  

## Target Audience

Assume the primary reader of the task list is a **junior developer** who will implement the feature.
