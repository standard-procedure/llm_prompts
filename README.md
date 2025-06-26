# Claude Commands

A collection of prompts that can be used by an LLM to assist with project management during a software project.

They currently are designed to read and write Issues to and from [Linear](https://linear.app) but will fall back to generating markdown files if Linear is not available.

## Process

### Bug Reports 

- Ask the LLM to create a bug report
- The LLM asks you some questions
- The LLM generates a bug report in a (relatively) standardised format
  - If the LLM has access to your code it will include possible causes and potential fixes for the developers to explore
- The LLM posts the bug report to Linear if it can

### Feature Specifications

- Ask the LLM to create a feature specification
- The LLM asks you some questions
- The LLM generates a feature specification in a (relatively) standardised format
  - If it has access it will add this as a new Issue to Linear
- Ask the LLM to generate some outlines tasks for this feature
- The LLM will ask you more questions
  - If the LLM has access to your codebase it may do some analysis of its own
- The LLM will outline some high-level tasks that could be used to implement the feature 
- Ask the LLM to generate detailed tasks for this feature
- The LLM will look at the Feature Specification and Outline Tasks and generate a detailed task list
  - If it has access it will add these as Sub-Issues of the Feature Issue in Linear

### Code Review

- Ask the LLM to perform a Code Review for a Feature or Bug Report
- The LLM will attempt to read the original Feature Specification or Bug Report
- The LLM will ensure it is on the correct branch and then diff that with the `develop` branch
- The LLM will run the linter and tests to make sure nothing is obviously broken
- The LLM will compare the diff to your style guide to see if it matches the existing code and your basic criteria (authorisation checks etc) have been met
- The LLM will use the diff to ascertain if the code changes reach their goal
- At any point, the LLM may attempt to fix things itself - you may need to intervene to prevent this
- The LLM will make a recommendation about merging this PR or sending it back to the developer in question

Of course, this is not a complete Code Review.  

The LLM cannot know if the code _really_ achieves its goal and it does not attempt to examine the user interface.  So you still have work to do - run the code manually, check the interface changes, verify the functionality.  

But lots of the boring grunt work should be done for you.  

## Setting up your project

These prompts rely on the LLM being able to understand your project.  To help it along (and reduce the token usage and hence the cost), ensure you have the following: 

- A README that explains the purpose of the project
- A Glossary (in `docs/glossary.md`) that explains the terms and names used (for example, your models)
- A Style Guide (in `docs/style-guide.md`) that explains any coding styles and formats you use

Some of the prompts will attempt to generate text files in `docs/tasks`.  This is to help each stage understand what the previous stage did without having to analyse the entire project again.  

## Claude Code

(Requires an API account at the time of writing)

- `git clone` this repository into `~/.claude/commands`
- Claude Code should automatically read these prompts and make them available
- Use Claude Code's `/init` command to generate a `Claude.MD` file, noting the technical details of your project. Edit this to include the stuff you think is important
- Use Claude Code's `/mcp` command to link your Linear account to Claude Code

If using a devcontainer then add the following to your `.devcontainer/devcontainer.json`

```json
  "features": {
    "ghcr.io/anthropics/devcontainer-features/claude-code:1.0": {}
  },
  "mounts": [
    "source=${localEnv:HOME}/.claude,target=/home/vscode/.claude,type=bind,consistency=cached"
  ],
```

These prompts are now available as slash commands within Claude Code - for example `/create_bug_report`.

## Claude App

(Requires a Pro account at the time of writing)

- Connect your Github account to Claude
- Connect your Linear account to Claude
- Create a project and add a Project Description describing the project and Claude's role (project administrator or similar)
- Add this repository to the "Project Knowledge" section
- Add your repository to the "Project Knowledge" section. It may be useful to limit the folders selected, reducing the context and therefore lowering the amount of analysis the LLM needs to do (and thus reducing your bill)

Tell Claude "I need to create a bug report in this project". (Hopefully) it will associate your request with the "create_bug_report" prompt and follow the instructions within.

## ChatGPT

(Requires a Plus or Teams account at the time of writing)

- At the moment, ChatGPT projects cannot use connectors (MCP) - so ChatGPT cannot read this repository or your code directly
- Clone this repository
- Create a project and add a Project Description describing the project and ChatGPT's role (project administrator or similar)
- Upload the prompts from this repository to the project

Tell ChatGPT "I need to create a bug report in this project". (Hopefully) it will associate your request with the "create_bug_report" prompt and follow the instructions within.

Because the ChatGPT project cannot access this repository, you will need to manually replace the prompts as and when new versions are released.  
