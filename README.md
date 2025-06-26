# Claude Commands

A collection of prompts that can be used by an LLM to assist with project management during a software project.

They currently are designed to read and write Issues to and from [Linear](https://linear.app) but will fall back to generating markdown files if Linear is not available.

## Claude Code

(Requires an API account at the time of writing)

- `git clone` this repository into `~/.claude/commands`
- Claude Code should automatically read these prompts and make them available as `/command` - for example `/create_bug_report`
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
