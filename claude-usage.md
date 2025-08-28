# Claude's Capabilities & Usage

## Claude Code

### How do sub-agents work?

[temp answer] Sub-agents are like specialized assistants that Claude Code can call on for specific tasks. When you ask Claude Code to do something, it can automatically delegate the work to a sub-agent that's an expert in that area such as having a code reviewer check your changes or a debugger investigate errors. Each sub-agent works in its own separate space with its own separate context, which keeps your main conversation clean and focused. You can either let Claude Code decide when to use them, or explicitly ask for one by name (like "Use the test-runner sub-agent for x"). They're configured as simple markdown files that define what the agent does, what tools it can use, and how it should approach problems.
To get started in Claude Code use `/agents` to configure, create, or remove agents Claude has access to.
