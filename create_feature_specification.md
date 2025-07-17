# Generating a Feature Specification

## Goal

To produce a detailed Feature Specification in Markdown format, based on an initial user prompt. The Feature Specification should be clear, actionable and suitable for a junior developer to use.  

We want to ship the feature as quickly as possible, so that we can get feedback from actual users.  Therefore remember the principle of "YAGNI" (You Are not Going to Need It) and attempt to defer any parts of the work that are not essential.  However, be certain to consider all security and data-protection aspects of the feature and its implementation.  

## Process

1.  **Receive Initial Prompt:** The user provides a brief description or request for a new feature or functionality.
2.  **Ask Clarifying Questions:** Before writing the Feature Specification, the AI *must* ask clarifying questions to gather sufficient detail, including who has requested this feature and which team will be responsible. The goal is to understand the "what" and "why" of the feature, not necessarily the "how".  
3.  **Generate Feature Specification:** Based on the initial prompt and the user's answers to the clarifying questions, generate a Feature Specification using the structure outlined below.
4.  **Save Feature Specification:** Generate the Feature Specification as a Markdown document (with .txt extension).  If available, post this document to Linear so that it is available for the relevant team to work on.

## Example Clarifying Questions

Adapt your questions based on the prompt - here are some common areas to explore:

*   **Problem/Goal:** "What problem does this feature solve for the user?" or "What is the main goal we want to achieve with this feature?"
*   **Target User:** "Who is the primary user of this feature?"
*   **Core Functionality:** "Can you describe the key steps or actions a user would perform to achieve this?"
*   **User Stories:** "Which types of user are involved in this?", "Could you fill in the blanks ... As a [type of user], I want to [perform an action] so that [beneficial outcomes]"
*   **Scenarios:** "Are there any alternatives (different configuration options, feature flags) that will affect how this works?"
*   **Acceptance Criteria:** "How will we know when this feature is successfully implemented? What are the key success criteria?"
*   **Existing Functionality:** "Is this an enhancement to an existing feature?", "Which other aspects of the product will this affect?"
*   **Scope/Boundaries:** "Are there any specific things this feature *should not* do (non-goals)?"
*   **Data Requirements:** "What kind of data does this feature need to display or manipulate?"
*   **Design/UI:** "Are there any existing design mockups or UI guidelines to follow?" or "What is the user expecting to see at the end of the process?"
*   **Edge Cases:** "Are there any potential gotchas or error conditions we should consider?"
*   **YAGNI:** "Which parts of this feature are essential?" or "What is the absolute minimum we can ship?"

Plan the questions that you need to ask in advance, then ask them one at a time, allowing a conversation to flow.  This helps the user provide you with the relevant information - especially as they may not fully understand all the technical terms that are being used.

## User Stories

Once you have an understanding of the feature, split the feature into Scenarios.  Remember YAGNI - only specify the stories which are essential to ship immediately.

The most important scenario is the "happy path", where the feature completes successfully.  Consider error handling and the "blank slate" (when the feature is used for the first time).  There may be other scenarios (such as configuration options) but remember YAGNI.  Our goal is to ship early and get feedback.  

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

- **Introduction/Overview:** Briefly describe the feature and the problem it solves. 
- **Goals:** List the specific, measurable objectives for this feature.
- **Scenarios:** Detail the various scenarios that this feature may follow.  Number these scenarios and place them in order of importance.  
- **Non-Goals (Out of Scope):** Clearly state what this feature will *not* include to manage scope.
- **Technical Considerations (Optional):** Mention any known technical constraints, dependencies, or suggestions (e.g., "Should integrate with the existing Auth module").
- **Success Metrics:** How will the success of this feature be measured? (e.g., "Increase user engagement by 10%", "Reduce support tickets related to X").
- **Open Questions:** List any remaining questions or areas needing further clarification.

## Target Audience

Assume the primary reader of the Feature Specification is a **junior developer**. Therefore, requirements should be explicit, unambiguous, and avoid jargon where possible. Provide enough detail for them to understand the feature's purpose and core logic.

## Output

*   **Format:** Markdown (`.txt`)
*   **Location:** Available for the user to download; create a folder called `doc/tasks/[feature-name]` and place a copy in there
*   **Filename:** `[feature-name].txt`

If available, post this document at Linear as a new issue, assigned to the relevant Team and Project.  

## Final instructions

1. Do NOT start implementing the specification
2. Make sure to ask the user clarifying questions
3. Aim to deliver the smallest specification possible so we can ship early and receive feedback
