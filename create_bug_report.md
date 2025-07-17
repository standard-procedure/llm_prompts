# Generating a Bug Report

## Goal

To create a detailed Bug Report in Markdown format, based on an initial user prompt. The Bug Report should be clear, actionable, and suitable for a junior developer to understand and implement the feature.

## Process

1.  **Receive Initial Prompt:** The user provides a brief description or request for a new feature or functionality.
2.  **Ask Clarifying Questions:** Before writing the Bug Report, the AI *must* ask clarifying questions to gather sufficient detail.
3.  **Generate Bug Report:** Based on the initial prompt and the user's answers to the clarifying questions, generate a Bug Report using the structure outlined below.
4.  **Save Bug Report:** Generate the Bug Report as a Markdown document (with .txt extension).  Allow the user to view and download the bug report, add it to `docs/tasks` and, if available, post this document to Linear so that it is available for the relevant Team to work on. 

## Clarifying Questions (Examples)

The AI should adapt its questions based on the prompt, but here are some common areas to explore:

*   **What Happened vs Expectations:** "What did the user see when the bug occurred?", "What did the user expect to happen?", "In the user's words, how did the system fail to achieve what they were trying to do"
*   **User and Account Details:** "Which user was doing this?", "Which Account were they in?"
*   **Configuration Settings:** "Which configuration settings apply to that account?", "Which preferences had the user set?"
*   **Security and Data Loss:** "Could this lead to a data breach?", "Has this caused any data loss?"
*   **Urgency:** "What timescale are they expecting for a resolution?"
*   **Importance:** "Is this issue preventing them from getting their work done?", "Do we, as the software provider, look bad because of this?"
*   **Acceptance Criteria:** "How will we know when this bug is successfully fixed?", "What is the user expecting?"
*   **Related Items:** "Is there anything in this area that it would be good to fix at the same time?"
*   **Scope/Boundaries:** "Although they may be related, are there any other aspects of this bug that we *should not* look at fixing at this time?"
*   **Mitigations and Workarounds:** "Are there any quick fixes that will keep the users happy while we work on the underlying problem?"

Prepare a list of clarifying questions, then ask them one at a time, allowing a conversation to flow.  Remember that the person filing the report will not be aware of technical terms.  If clarification is required, ask for more details, referring to the project glossary if available.  

## Bug Report Structure

The generated document should include the following sections:

1.  **Introduction/Overview:** Briefly describe the bug report
5.  **Urgency:** When is a resolution required?
6.  **Importance:** How much reputational damage could not fixing this cause to us? How important is this to the customer?  
2.  **What Happened:** List the specific things that happened to cause the report to be filed
3.  **User Expectations:** Detail what the user _expected_ to happen.  
4.  **Security Implications:** Are there any security or data loss implications in this report?
7.  **Detailed Report:** Information about the user in question, the account configuration and other factors that may have played a role in the issue.  
8.  **Success Metrics:** What will keep the customer happy?  What do we need to do to prevent this happening again?  
9.  **Open Questions:** List any remaining questions or areas needing further clarification.

## Target Audience

Assume the primary reader of the Bug Report is a **junior developer**. Therefore, requirements should be explicit, unambiguous, and avoid jargon where possible. Provide enough detail for them to understand the bug's causes and what a successful resolution would look like.  

## Output

*   **Format:** Markdown (`.txt`)
*   **Location:** Available for the user to download; place a copy in the project's `doc/tasks` folder if accessible
*   **Filename:** `[bug-report-title].txt`

If possible, also create a new issue in Linear within the relevant Team and Project.

## Final instructions

1. Do NOT start implementing a fix to the report
2. Make sure to ask the user clarifying questions
3. Treat security and data protection as our highest priority
