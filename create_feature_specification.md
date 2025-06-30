# Generating a Feature Specification

## Goal

To guide an AI assistant in creating a detailed Feature Specification in Markdown format, based on an initial user prompt. The Feature Specification should be clear, actionable, and suitable for a junior developer to understand and implement the feature.

## Process

1.  **Receive Initial Prompt:** The user provides a brief description or request for a new feature or functionality.
2.  **Ask Clarifying Questions:** Before writing the Feature Specification, the AI *must* ask clarifying questions to gather sufficient detail, including who has requested this feature and which team will be responsible. The goal is to understand the "what" and "why" of the feature, not necessarily the "how" (which the developer will figure out).  
3.  **Generate Feature Specification:** Based on the initial prompt and the user's answers to the clarifying questions, generate a Feature Specification using the structure outlined below.
4.  **Save Feature Specification:** Generate the Feature Specification as a Markdown document (with .txt extension).  If available, post this document to Linear so that it is available for the relevant Team to work on, otherwise allow the user to view and download the Feature Specification. 

## Clarifying Questions (Examples)

The AI should adapt its questions based on the prompt, but here are some common areas to explore:

*   **Problem/Goal:** "What problem does this feature solve for the user?" or "What is the main goal we want to achieve with this feature?"
*   **Target User:** "Who is the primary user of this feature?"
*   **Core Functionality:** "Can you describe the key actions a user should be able to perform with this feature?"
*   **User Stories:** "Could you provide a few user stories? (e.g., As a [type of user], I want to [perform an action] so that [benefit].)"
*   **Scenarios:** "Are there any alternatives - for example, if different configuration options are selected - that will affect the path that the user takes?"
*   **Acceptance Criteria:** "How will we know when this feature is successfully implemented? What are the key success criteria?"
*   **Existing Functionality:** "Does this count as an enhancement to an existing feature?", "Which other aspects of the product will this affect?"
*   **Scope/Boundaries:** "Are there any specific things this feature *should not* do (non-goals)?"
*   **Data Requirements:** "What kind of data does this feature need to display or manipulate?"
*   **Design/UI:** "Are there any existing design mockups or UI guidelines to follow?" or "Can you describe the desired look and feel?"
*   **Edge Cases:** "Are there any potential edge cases or error conditions we should consider?"
*   **Team:** If Linear is available, the list of teams available to work on this Feature Specification can be taken from there.  If not, ask the user which team this Feature Specification is for (example teams are Collabor8Online, Policy Manager, Site Manager).

When asking questions, remember that the person requesting the feature may not be aware of the technical terms used within the system - if clarification is required, refer to the project glossary, or ask for more details.   

Do not present the user with multiple questions in one go.  Where possible, ask one question at a time, allowing the conversation to flow.  This will put the user at ease and make it easier to get the relevant information.  Stop asking questions when either of you feels they have provided enough information.  

## User Stories

Once you have an understanding of the feature, split the feature into Scenarios.  The most important scenario is the "happy path", where the feature completes successfully.  But there may be other important scenarios (such as selecting different options or if the account has certain features switched on or off), plus we will also need to consider error handling and what could go wrong.  

An individual scenario may cross multiple user roles, so that should be reflected in how the scenario is written.  

For example: 
- Manager invites a user a group
  - Manager sends the invitation 
- User receives the invitation
  - User opens the invitation page and enters their details
  - User completes the registration process 
  - User is now added to the group
- Manager receives a notification that the user has registered

## Feature Specification Structure

The generated document should include the following sections:

1.  **Introduction/Overview:** Briefly describe the feature and the problem it solves. State the goal.
2.  **Goals:** List the specific, measurable objectives for this feature.
3.  **Scenarios:** Detail the various scenarios that this feature may follow.  Number these scenarios and place them in order of importance.  
4.  **Functional Requirements:** List the specific functionalities the feature must have. Use clear, concise language (e.g., "The system must allow users to upload a profile picture."). Number these requirements.
5.  **Non-Goals (Out of Scope):** Clearly state what this feature will *not* include to manage scope.
6.  **Design Considerations (Optional):** Links to mockups, describe UI/UX requirements, or mention relevant components/styles if applicable.
7.  **Technical Considerations (Optional):** Mention any known technical constraints, dependencies, or suggestions (e.g., "Should integrate with the existing Auth module").
8.  **Success Metrics:** How will the success of this feature be measured? (e.g., "Increase user engagement by 10%", "Reduce support tickets related to X").
9.  **Open Questions:** List any remaining questions or areas needing further clarification.

## Target Audience

Assume the primary reader of the Feature Specification is a **junior developer**. Therefore, requirements should be explicit, unambiguous, and avoid jargon where possible. Provide enough detail for them to understand the feature's purpose and core logic.

## Output

*   **Format:** Markdown (`.txt`)
*   **Location:** Available for the user to download; create a folder called `doc/tasks/[feature-name]` and place a copy in there
*   **Filename:** `[feature-name].txt`

If available, post this document at Linear as a new issue, assigned to the relevant Team and Project.  

## Final instructions

1. Do NOT start implementing the specification
2. Make sure to ask the user clarifying questions, taking in to account their level of technical knowledge
3. Take the user's answers to the clarifying questions and improve the specification
