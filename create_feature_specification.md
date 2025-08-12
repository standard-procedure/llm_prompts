# Create a Feature Specification

## Goal

To produce a description of a feature in [Gherkin](https://cucumber.io/docs/gherkin/reference) format with a number of scenarios - a "happy" path, an "error" path, plus any variations required.  

We want to ship the feature as quickly as possible (so that we can get feedback from actual users).  Therefore remember the principle of "YAGNI" (You Are not Going to Need It) and defer any parts of the work that are not essential.  However, be certain to consider all security and data-protection aspects of the feature and its implementation.  

## Process

- Receive Initial Prompt: The user provides a brief description or request for a new feature or functionality.
- Understand the Project: Read the project glossary and other documentation in order to understand the system.
- Ask Clarifying Questions: Ask clarifying questions in order to ensure that the essential scenarios are fully understood. The goal is to understand the "what" and "why" of the feature, not necessarily the "how".  
- Generate Feature Specification: Generate a Feature Specification based upon those answers.
- Save Feature Specification: Save the feature specification in `docs/features` or in Linear, as appropriate.  

## Example Clarifying Questions

Adapt your questions based on the prompt and plan the questions you need to ask in advance.  Ask questions one at a time until you have sufficient information to proceed.  

Here are some areas to explore:

- *Goal* "What problem does this solve?", "Why does the client need this?"
- *Roles* "Which users will be using this?", "Is this an administrator-only function?"
- *Functionality* "Can you describe the feature step-by-step?", "What actions will the user take to do this?"
- *Existing features* "Is this an update to an existing feature?", "Which other parts of the system does this affect?"
- *Variations* "Are there options or configurations that affect how this feature works?", "Does this work the same way for everyone or can different clients set things up differently?"
- *Urgency* "What happens if we cannot deliver this feature in time?", "When is the client expecting this and why is that date important to them?"
- *Acceptance* "How will we know that the feature has been successfully implemented?", "What counts as success?"
- *Boundaries* "Is there anything that this feature should _not_ do?", "What is the minimum we can do to meet the requirement?"
- *Outputs* "What will the user expect to see?", "Are there any reports, data exports or other documents that must be generated as part of this work?"
- *Security* "How sensitive is the data involved?", "How do we ensure that this feature remains secure?"

## Scenarios

Once you have an understanding of the feature, split the feature into Scenarios.  Remember YAGNI - only specify the stories which are essential to ship immediately.

The most important scenario is the "happy path", where the feature completes successfully.  Consider error handling and the "blank slate" (when the feature is used for the first time).  There may be other scenarios (such as configuration options) but remember YAGNI.  Our goal is to ship early and get feedback.  

An individual scenario may cross multiple user roles, so that should be reflected in how the scenario is written.  

Example: 

```gherkin
Scenario: Inviting multiple people to a group

Given Mark is a manager
And there is a user group called "Engineers"
When Mark logs in
And he navigates to the "Engineers" group
And he invites 3 people to the group
Then an invitation email should be sent to each recipient

When Rebecca clicks the link in the invitation email
Then she should be asked to register
When she has registered
Then she should see that she is a member of the "Engineers" group
And Mark should receive a notification that Rebecca has now joined
```

## Feature Specification Structure

The generated document should be in [Gherkin](https://cucumber.io/docs/gherkin/reference) format: 

- Title
- User story
- Scenario
  - Given 
  - When 
  - Then 
- Scenario
  - Given 
  - When 
  - Then 
- Open questions

### Title

```
Feature: Manager invites people to a group
```

### User story

(These should be added as comments to the document)
```
# As a manager
# I want to invite people to a group
# So we can share information with those people
```

### Scenarios 

```
  Scenario: inviting multiple people
  
    Given Mark is a manager
    And there is a group called "Engineers"
    When Mark logs in
    And navigates to the "Engineers" group
    And invites some people
    Then the people should receive an invitation email
```
- Given steps set things up into a known state.  
- When steps denote actions taken by a user or by the system.  
- Then steps test for the results of those actions.  

## Output

- Format 
  Gherkin `.feature`
- Location
	If available: `docs/feature` folder 
  If available: create an issue in the correct Team and Project using the Linear MCP server	
- Filename
  `[feature-name].feature`

## Final instructions

- Do NOT start implementing the specification
- Make sure to ask the user clarifying questions
- Aim to deliver the smallest specification possible so we can ship early and receive feedback
