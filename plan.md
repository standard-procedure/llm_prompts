# Generating a Task List for a Feature Specification

## Goal

To guide an AI assistant in creating a detailed, step-by-step task list based upon a part of a Feature Specification Document (stored in Linear as an Issue with ID $ARGUMENTS). The task list should guide a developer through implementation.

## Output

The tasks generated will be created and stored as a hierarchy of sub-issues within the original Feature Specification's Linear Issue.  

## Process

1.  **Receive Feature Specification Reference:** The user points the AI to a specific Linear Issue (identified as $ARGUMENTS) containing the Feature Specification.
2.  **Analyze Feature Specification:** The AI reads and analyzes the functional requirements, user stories, and other sections of the Feature Specification.
3.  **Understand the Project Documentation:** The AI should read the project style guide and glossary to ensure the code structures and names it suggests fit with the overall pattern of the project.  
4.  **Phase 1: Generate an Outline:** Use the process detailed in [generate_plan.md](generate_plan_.md) to design and record the plan for completion.  
5.  **Phase 2: Generate Detailed Tasks:** For each step within the plan, use the process detailed in [generate_tasks.md](generate_tasks.md) to design and record the detailed tasks that will work towards implementing the feature.  

## Output Format

*   **Format:** Markdown (`.txt`)
*   **Location:** Available for the user to download; create a folder called `doc/tasks/[feature-name]` and place a copy in there
*   **Filename:** `[feature-name].txt`

If available, update the original Feature Specification in Linear, adding comments for each part of the Design Outline and Sub-Issues for each Detailed Task.

The generated issues _must_ follow this structure:

In the filesystem:

- docs
  - tasks
    - [feature-name]
      - specification.txt
        - step 1 
          - summary.txt
          - task 1.txt
          - task 2.txt 
          - task 3.txt 
        - step 2 
          - summary.txt
          - task 1.txt 
          - task 2.txt 
          - task 3.txt
          
In Linear (if available): 

- Feature Specification - Issue ID $ARGUMENTS
  (This is the original Feature Specification that we are referencing to create these tasks)
  Comments:
		- Step 1
			Description
			Acceptance Criteria 
			Relevant Files
		- Step 2
			Description
			Acceptance Criteria 
			Relevant Files
  Sub-Issues
		- Step 1 - Task 1
			Description - which outline does this relate to? 
			Notes - to aid the developer whilst they are completing the task
		- Step 1 - Task 2
			Description - which outline does this relate to? 
			Notes - to aid the developer whilst they are completing the task
		- Step 1 - Task 3
			Description - which outline does this relate to? 
			Notes - to aid the developer whilst they are completing the task
		- Step 2 - Task 1
			Description - which outline does this relate to? 
			Notes - to aid the developer whilst they are completing the task
		- Step 2 - Task 2
			Description - which outline does this relate to? 
			Notes - to aid the developer whilst they are completing the task
		- Step 2 - Task 3
			Description - which outline does this relate to? 
			Notes - to aid the developer whilst they are completing the task

Because the original Feature Specification is broken down into a two-level hierarchy of issues, this ensures that all related work is easily tracked.
    
## Target Audience

Assume the primary reader of the task list is a **junior developer** who will implement the feature.

## Final instructions

1. Do NOT start implementing a fix to the report
2. Make sure to ask the user clarifying questions
3. Use these answers to improve the plan

