# Create a Bug Report

## Goal

To create a detailed Bug Report in Markdown format, based on an initial user prompt. The Bug Report should be clear and actionable, plus it should be clear how important and urgent this issue is.  

## Process

- Receive Initial Prompt: The user provides a brief description of the issue.
- Understand the Project: Read the project glossary and other documentation in order to understand the system.
- Ask Clarifying Questions: Ask clarifying questions to ensure the background and implications of the report are fully understood.  
- Generate Bug Report: Based on the answers provided by the user generate a Bug Report.
- Save Bug Report: Save the bug report in `docs/bugs` or in Linear, as appropriate.   

## Example Clarifying Questions

Adapt your questions based on the prompt and plan the questions you need to ask in advance.  Ask questions one at a time until you have sufficient information to proceed.  

Here are some areas to explore:

- What happened: 
	"What steps did the user perform when this happened?", "In the user's words, how did the system fail to achieve what they were trying to do?"
- User details:
  "Which user was doing this and when did it happen?", "Which account was the user in?"
- Configuration: 
  "Which preferences are set for that user?", "How is the account configured?"
- Security and Data Loss: 
  "Could this lead to a data breach?", "Does this reveal data that should be kept secret?"
- Urgency: 
  "How quickly does this need to be resolved?", "When does the user expect a fix?"
- Importance: 
  "Is this stopping people from working?", "Does this make us, the software provider, look bad?"
- Acceptance: 
  "How do we know that this has been successfully fixed?", "What is the user expecting us to do?"
- Mitigations and Workarounds: 
  "Are there any quick fixes that will keep the users happy while we work on the underlying problem?"

## Bug Report Structure

The generated document should include the following sections:

- Description
- Urgency
- Importance
- Steps to reproduce 
- Acceptance criteria 
- Detailed report (if required)

## Target Audience

Assume the primary reader of the Bug Report is a junior developer. Therefore, requirements should be explicit, unambiguous, and avoid jargon where possible. Provide enough detail for them to understand the bug's causes and what a successful resolution would look like.  

## Output

- Format 
  MArkdown `.md`
- Location
	If available: `docs/bugs` folder 
  If available: create an issue in the correct Team and Project using the Linear MCP server	
- Filename
  - `[bug-report-title].md`

## Final instructions

- Do NOT start implementing a fix to the report
- Make sure to ask the user clarifying questions
- Treat security and data protection as our highest priority
