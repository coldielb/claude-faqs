# Claude Code FAQ

## Getting Started & Best Practices

### I'm new to Claude Code. What are the best workflows for building projects?

**[temp answer]** Start with small, focused tasks to understand Claude Code's capabilities. Use the project feature to maintain context across sessions. Break larger projects into manageable chunks and use the todo list feature to track progress. Claude Code works best when given clear, specific instructions rather than vague requests.

### Should I start with small, iterative tasks or give Claude the full project scope at once?

**[temp answer]** Start with small, iterative tasks. This allows you to:
- Verify Claude understands your requirements correctly
- Catch issues early before they compound
- Maintain better control over the project direction
- Learn how Claude Code works best with your coding style

Once comfortable, you can gradually increase task complexity.

### What is the best IDE setup for Claude Code (e.g., VS Code vs. Cursor)?

**[temp answer]** Claude Code works as a standalone CLI tool that integrates with any development environment. Popular setups include:
- **VS Code**: Use alongside Claude Code for file editing and project management
- **Terminal/Command Line**: Direct interaction with Claude Code CLI
- **Any editor**: Claude Code can read and modify files created in any text editor (just not all support "live" editing)

The choice depends on your personal preference and existing workflow.

### How can I make Claude less agreeable and more of a critical coding partner?

**[temp answer]** To get more critical feedback from Claude:
- Ask explicitly for code reviews and critiques
- Request alternative approaches or potential issues
- Ask "What could go wrong with this approach?"
- Request performance, security, or maintainability concerns
- Use prompts addendums like "Challenge my assumptions" or "What am I missing?"

### How do I prevent Claude from over-engineering my code?

**[temp answer]** To keep Claude's code simple and focused:
- Specify "keep it simple" or "minimal implementation" in your requests
- Ask for "the simplest solution that works"
- Ask Claude for a Minimum Viable Product (MVP) first and build from there
- Avoid asking for optimizations or advanced features until the basic version is complete
- Set constraints like "use only standard library" or "maximum 50 lines"
- Request explanations for complex patterns Claude suggests
- Explicitly state when you prefer simple over optimal solutions

### I'm not a developer. How can I use Claude to build simple apps or for creative projects?

**[temp answer]** Non-developers can use Claude Code for:
- **Simple scripts**: Automation tasks, file processing
- **Web pages**: Basic HTML/CSS/JavaScript sites
- **Creative tools**: Text processing, data manipulation
- **Learning**: Understanding code through explanation and modification

Start with very small projects and ask Claude to explain everything it creates.

## Context, Memory, and Limits

### How can I make Claude remember our past conversations (persistent memory)?

**[temp answer]** Claude Code doesn't have persistent memory between sessions by default, but you can:
- Use the `#<what you want claude to know across sessions>` feature to append important context about your codebase to the `CLAUDE.md` file
- Save important information to files that Claude can read (typically within the same directory)
- Create documentation files that capture important decisions and context

### What is "context rot" and how can I prevent Claude from losing context in long chats/sessions?

**[temp answer]** Context rot occurs when very long conversations and/or sessions cause Claude to lose track of earlier information. To prevent it:
- Start fresh conversations for new topics (e.g. new features or larger changes, unrelated tasks for the same codebase)
- Summarize important points periodically (you can use `/compact` or create your own summary files for Claude to read)
- Break complex tasks into focused sessions
- Reference specific files rather than relying on conversation memory (e.g. tagging a file with `@/path/to/filename`)

### What is "auto-compaction" and how does it affect my conversation?

**[temp answer]** Auto-compaction is a feature that summarizes or compresses older parts of long conversations to maintain performance during longer sessions. Effects include:
- Earlier conversation details may become less accessible (e.g. specific remarks, instructions, etc.)
- Context from early in the conversation may be summarized
- Performance remains consistent in very long chats (note: there typically is consistent performance across coding tasks, but degradation of conversation context may occur)
- Important information should be saved to files rather than relying on chat memory

### Why am I hitting my usage limit so quickly on the Pro/Max plan?

**[temp answer]** Usage limits can be reached quickly due to:
- Large codebases: Processing many files uses significant tokens (remember: input tokens + output tokens count against your limit)
- Long conversations: Extended back-and-forth discussions (e.g. debugging sessions, reviewing code, planning, errors all count against your limit)
- Complex requests: Detailed analysis or code generation (e.g. longer initial prompts, more comments, explanations, etc.)
- Parallel operations: Multiple sub-agents running simultaneously or multiple `claude` instances running simultaneously

Monitor your usage in account settings and consider breaking large tasks into smaller sessions (see above for tips/tricks).

### How do I check my remaining usage or when my limit resets?

**[temp answer]** Unfortunately, Claude Code does not currently provide a built-in way to check usage or limits for Pro/Max users. To monitor your usage for API users you can:
- Check your account dashboard on https://console.anthropic.com/ for API usage details
- Track your usage manually based on your known limits and typical usage patterns
- Contact support for specific questions about your plan and usage
- Contact sales if you need a custom plan or higher limits

### Is the Pro or Max plan worth it? What are the real differences?

**[temp answer]** Plan differences typically include:
- **Usage limits**: Higher message/token limits on paid plans
- **Priority access**: Faster response times during peak usage
- **Advanced features**: Early access to new Claude Code features
- **Model access**: Access to newer or more capable Claude models (note: as of 08/28/2025 Pro users do not have access to Claude 4/4.1 Opus via Claude Code; Opus models are available via the web app)

Consider upgrading if you hit free tier limits regularly or need consistent access during peak times.

### Is there a cheaper plan, or a mid-tier option between Pro and Max?

**[temp answer]** Plan availability and pricing may vary. Check the current pricing page for:
- Available subscription tiers
- Regional pricing differences
- Student or educational discounts
- Usage-based vs subscription options

Currently, there are no mid-tier options between Pro and Max.

## Claude Code: Advanced Features (Agents & MCPs)

### How do I effectively use Sub-agents and MCPs with Claude Code?

**[temp answer]** Sub-agents and MCPs (Model Context Protocols) allow specialized functionality:
- **Sub-agents**: Use for specific tasks like code review, documentation, or testing
- **MCPs**: Connect external tools and services to Claude Code
- **Best practices**: Choose the right agent for each task, monitor their progress, provide clear instructions

### What are the most popular or useful community-built MCPs?

**[temp answer]** Popular community MCPs include:
- Database connectors for various databases
- API integrations for common services
- Development tools (linters, formatters, testing frameworks)
- File system utilities and search tools
- Cloud service integrations

Check the Claude Code documentation and community repositories for current options.

### How can I see what a sub-agent is doing and improve its visibility?

**[temp answer]** To monitor sub-agent activity:
- Check the task/todo list for sub-agent progress
- Request progress updates from sub-agents during long-running tasks

### How can I get sub-agents to run in parallel instead of one by one?

**[temp answer]** Parallel sub-agent execution:
- Specify parallel execution in your request to the Delegator agent (e.g., "Run these tasks in parallel" or "Use sub-agent x and y simultaneously")
- Break independent tasks into separate sub-agent calls
- Some sub-agents may run in parallel automatically depending on the task

### How do I connect my own custom MCP server to Claude?

**[temp answer]**


## Troubleshooting, Bugs, and Performance Issues

### Why has Claude's personality changed? It feels colder/more robotic.

**[temp answer]** Perceived personality changes may be due to:
- Model updates or improvements
- Different conversation context
- Changes in how you're interacting with Claude
- Temporary technical issues

Try starting a fresh conversation or adjusting your communication style.

### Why does Claude say "You're absolutely right!" all the time, and how can I stop it?

**[temp answer]** To reduce overly agreeable responses:
- Ask Claude to be more critical or challenging
- Request honest feedback and different perspectives
- Use prompts that encourage disagreement when appropriate
- Specify that you want authentic responses, not just agreement

### How do I stop Claude from "lying" or falsely claiming a task is complete?

**[temp answer]** To ensure accurate completion reporting:
- Ask Claude to verify its work before marking tasks complete
- Request specific evidence of completion
- Use the todo list to track actual progress
- Ask for screenshots or file outputs as proof
- Break large tasks into verifiable smaller steps

### Why are the token counter and TODO list missing in Claude Code?

**[temp answer]** If UI elements are missing:
- Refresh the application or restart Claude Code
- Check for updates to Claude Code as they may have removed previously available UI features
- Contact support if features remain missing (despite other users having them)

### Why is my voice chat cutting off mid-sentence?

**[temp answer]** Voice chat issues may be caused by:
- Network connectivity problems
- Microphone or audio settings
- Browser permissions for microphone access
- Background noise interference
- Usage limits or technical maintenance

Check audio settings and network connection.

### Why are my chat messages appearing in the wrong order?

**[temp answer]** Message ordering issues can result from:
- Network latency or connection problems
- Browser or app synchronization issues
- Rapid message sending overwhelming the system
- Technical maintenance or server issues

Try refreshing the application or slowing down message frequency.

### My Claude is running slowly or lagging when I type. How can I fix it?

**[temp answer]** Performance issues may be due to:
- Large conversation history
- Complex ongoing operations
- Network connectivity problems
- High system resource usage
- Browser performance issues

Try starting a new conversation or closing other applications.

### Why does Claude execute dangerous commands (rm -rf) without permission?

**[temp answer]** This should not happen as Claude Code has safety measures. If it does:
- Report this immediately as a safety issue
- Review what commands you've authorized
- Check your project permissions and settings
- Consider this a critical bug that needs reporting
- Be more explicit about command restrictions in future requests

### Why is my request being blocked for a "Usage Policy violation" for harmless topics?

**[temp answer]** Policy violations can be triggered by:
- Misinterpreted intent by safety systems
- Keywords that seem problematic out of context
- Complex requests that appear suspicious
- Overly sensitive filtering during high-traffic periods

Try rephrasing your request more clearly or contact support for review.

## Still Need Help?

If your Claude Code question isn't answered here:
- **Check the official Claude Code documentation**
- **Join the Claude Code community Discord**
- **Search GitHub issues** for similar problems
- **Contact support** for account-specific issues
