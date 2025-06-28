# Generating a Task List from a Feature Specification

## Goal

To guide an AI assistant in creating a detailed, step-by-step task list based upon an existing Feature Specification Document (stored in Linear as an Issue with ID $ARGUMENTS). The task list should guide a developer through implementation.

## Output

The tasks generated will be created and stored as a hierarchy of sub-issues within the original Feature Specification's Linear Issue.  

## Process

1.  **Receive Feature Specification Reference:** The user points the AI to a specific Linear Issue (identified as $ARGUMENTS) containing the Feature Specification.
2.  **Analyze Feature Specification:** The AI reads and analyzes the functional requirements, user stories, and other sections of the Feature Specification.
3.  **Understand the Project Documentation:** The AI should read the project style guide and glossary to ensure the code structures and names it suggests fit with the overall pattern of the project.  
4.  **Phase 1: Generate Parent Tasks:** Use the process detailed in [generate_outline_tasks.md](generate_outline_tasks.md) to design and record the high-level task breakdown.  
5.  **Phase 2: Generate Detailed Tasks:** For each high-level task, use the process detailed in [generate_detailed_tasks.md](generate_details_tasks.md) to design and record the detailed tasks that will work towards implementing the feature.  

## Output Format

The generated issues _must_ follow this structure:

- Feature Specification - Issue ID $ARGUMENTS
  The original Feature Specification that defines the requirement
  - High Level Task 1
    Design outline
    Acceptance Criteria - including outline RSpec System Specs using Capybara
    Relevant Files - models, controllers, specifications and other files
      - Sub Task 1
        Summary - which part of the parent task is this task about
        Notes - to aid the developer whilst they are completing the task
      - Sub Task 2
        Summary
        Notes
  - High Level Task 2
    Design Outline 
    Acceptance Criteria 
    Relevant Files
      - Sub Task 3 
      - Sub Task 4 

Because the original Feature Specification is broken down into two tiers of issues, this ensures that all related work is easily tracked within Linear.  
    
## Target Audience

Assume the primary reader of the task list is a **junior developer** who will implement the feature.
