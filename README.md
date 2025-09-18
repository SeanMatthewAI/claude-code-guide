# Coding Agent Tips & Best Practices 

Welcome to the companion repository for my **AI Coding Fundamentals Series** on YouTube! This repo contains examples, configurations, and best practices for using Claude Code (and other AI coding agents).  You can find all my videos at: https://www.youtube.com/@SeanMatthewAI

## 📺 Tutorial Series

This repository corresponds to my coding agent fundamentals series on YouTube. Each video focuses on specific techniques to improve your development workflow and get the most out of Claude Code and other AI coding agents.

### Episode 1: Foundation Essentials
- **CLAUDE.md Optimization**: How to create effective project memory
- **Permission Management**: Give Claude Code the ability to work faster without input

*More episodes coming weekly! Subscribe to stay updated.*

## 🎯 Quick Start Tips

### 1. Optimize Your CLAUDE.md Files

The `CLAUDE.md` file is your project's memory system and one of the most critical factors for consistent, high-quality output from Claude Code.  See the sample CLAUDE.md file in this repo for an example of useful structure and content for this file.

#### Key Principles:

**Keep it Short**
- Don't overload with details - contents are appended to your prompt
- Focus on essential information only
- Preserve your finite context window

**Keep it Organized**
- Structure your content logically
- Use clear headings and sections
- Make it scannable for both you and Claude

**Use Multiple CLAUDE.md Files**
- Create a master file at the project root
- Add specific CLAUDE.md files in subdirectories
- Tailor rules and context to each area of your project

#### Example Structure for Multiple Claude.md Files:
```
~/projects/
├── CLAUDE.md                # (Global project context)
├── backend/
│   └── CLAUDE.md            # (Backend-specific rules)
├── frontend/
│   └── CLAUDE.md            # (Frontend-specific context)
├── docs/
│   └── CLAUDE.md            # (Documentation guidelines)
└── shared/
    └── CLAUDE.md            # (Shared utilities context)
```

### 2. Manage Permissions Effectively

Claude Code allows you to control what commands and actions it can take automatically. Even with `Shift + Tab` (Autoaccept) enabled, you'll still get prompted for many basic operations without proper permission setup.

#### Recommended Permission Configuration

These are the permissions I typciall use. Feel free to add or change as needed in your `.claude/settings.local.json`:

```json
{
  "permissions": {
    "allow": [
      "Read(**)",
      "Edit(**)",
      "MultiEdit(**)",
      "Write(**)",
      "Grep(**)",
      "Bash(npm install:*)",
      "Bash(npx tailwindcss init:*)",
      "Glob(**)",
      "LS(**)",
      "WebSearch(**)",
      "Bash(git add:*)",
      "Bash(git mv:*)",
      "Bash(git stash:*)",
      "Bash(git diff:*)",
      "Bash(git commit:*)",
      "Bash(ls:*)",
      "Bash(tree:*)",
      "Bash(pwd:*)",
      "Bash(which:*)",
      "mcp__ide__getDiagnostics",
      "mcp__playwright__browser_navigate",
      "mcp__playwright__browser_console_messages",
      "mcp__playwright__browser_evaluate",
      "mcp__playwright__browser_close",
      "mcp__playwright__browser_take_screenshot",
      "mcp__playwright__browser_click"
    ],
    "deny": [],
    "ask": []
  }
}
```

#### Permission Best Practices:

✅ **DO Allow:**
- Basic file operations (Read, Edit, Write, List)
- Safe package management commands
- Git operations
- Development tool commands

❌ **DON'T Allow:**
- All bash commands globally
- `rm` (remove) commands
- System-level operations

#### YOLO Mode (Advanced)

For experienced users who want maximum automation:

```bash
claude --dangerously-skip-permissions
```

⚠️ **Warning**: If using YOLO mode, it is recommended that you containerize your Claude Code environment with Docker for safety. See [Anthropic's containerization guide](https://docs.anthropic.com/en/docs/claude-code/devcontainer).

### 3. Plan Correctly

The PRD/Plan/Tasks Framework helps you turn your idea into an app more effectively by giving the AI coding agent a project plan and system to excute the plan. This framework separates your project's core requirements, architecture, and tasks into distinct files to manage context efficiently and give you a better output.

#### The Process:

**Step 1: Create a PRD**
Start by creating a Product Requirements Document (PRD) with your preferred AI chat interface (Claude, ChatGPT, Gemini, Grok, etc.). Brainstorm thoroughly about what you want to build, and draft a 1-2 paragraph prompt describing what you want.  Ask the AI interface to generate a detailed PRD.

**Step 2: Generate Core Files**
From your PRD, ask AI to generate three essential files:
- **CLAUDE.md**: Distilled important details from the PRD
- **PLANNING.md**: Vision, architecture, technology stack, and required tools
- **TASKS.md**: Bullet-point tasks divided into milestones

Use these prompts:
- **Prompt to create CLAUDE.md**: "Using the PRD and the attached example CLAUDE.md file, generate a CLAUDE.md file for this project."  Use an example CLAUDE.md from this repo to give guidance about how to structure the file.
- **Prompt to create PLANNING.md**: "Create a PLANNING.md file that includes vision, architecture, technology stack, and required tools list for this app."
- **Prompt to create TASKS.md**: "Create a TASKS.md file with bullet points tasks divided into milestones for building this app."

**Step 3: Configure CLAUDE.md**
Add this language to your CLAUDE.md to ensure proper file usage:
```markdown
- **Always read** PLANNING.md at the start of a new conversation to understand the app's architecture, goals, tech stack, and constraints.
- **Check** TASKS.md before starting work. If the task isn't listed, add it with a brief description and today's date.
- **Mark completed tasks in** TASKS.md immediately after fully completing them.
- **Add any new tasks** to TASKS.md.
```

**Step 4: Initiate Development**
Start with this prompt:
```
Please read PLANNING.md, CLAUDE.md, and TASKS.md to understand the project. Then complete the first task on TASKS.md
```
Then interate through each task, clearing context often.

#### Best Practices:

**For Large Projects:**
- Create nested CLAUDE.md, PLANNING.md, and TASKS.md files in subdirectories (backend/, frontend/, etc.)

```
~/.claude/CLAUDE.md        # (Global personal default settings)
└── projects/
    ├── CLAUDE.md          # (Project-wide instructions)
    ├── backend/
    │   ├── CLAUDE.md      # (Backend-specific context)
    │   ├── PLANNING.md    # (Backend planning tasks)
    │   └── TASKS.md       # (Backend actionable tasks)
    ├── frontend/
    │   ├── CLAUDE.md      # (Frontend-specific context)
    │   ├── PLANNING.md    # (Frontend planning tasks)
    │   └── TASKS.md       # (Frontend actionable tasks)
    ├── docs/
    │   ├── CLAUDE.md      # (Docs/internals guidelines)
    │   ├── PLANNING.md    # (Docs planning tasks)
    │   └── TASKS.md       # (Docs actionable tasks)
    └── shared/
        ├── CLAUDE.md      # (Shared utils/templates context)
        ├── PLANNING.md    # (Shared planning tasks)
        └── TASKS.md       # (Shared actionable tasks)
```

- Consider migrating tasks to Linear using the Linear MCP for better task management:
  - Install Linear MCP in Claude Code with this command: `claude mcp add --transport sse linear-server https://mcp.linear.app/sse`
  - Prompt to use: "Use the Linear MCP server to migrate all tasks (completed, in progress, and future tasks) from TASKS.md and any useful context from PLANNING.md and CLAUDE.md"

**For Existing Codebases:**
Use a high-context coding agent and model (e.g., Gemini CLI) to analyze your codebase:
```
Analyze this codebase to understand project structure, architecture, technology stack, and required tools. Please see [existing documentation] and generate a detailed PRD for this project. Also create a project status .md that details all work completed to-date and any new or future milestones/sprints left to complete.
```

**Important:** Keep these files distinct - they serve related but different purposes. Avoid overlap between CLAUDE, PLANNING, and TASKS files.

## 📁 Repository Contents

- Sample CLAUDE.md, PLANNING.md, TASKS.md, and PRD.md files
- `agents/` - Custom subagent examples (coming in future episodes)
- `commands/` - Custom slash command implementations (coming in future episodes)

## 🔗 Resources

- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)
- [Awesome Claude Code Examples](https://github.com/hesreallyhim/awesome-claude-code)
- [Docker Containerization Guide](https://docs.anthropic.com/en/docs/claude-code/devcontainer)

## 🤝 Contributing

Have a great Claude Code tip or best practice?  Have a question about how to use these tips in other coding agents (e.g., Gemini CLI, GPT 5 Codex, etc.)? I'd love to feature it in a future video! Submit a PR with:
- Clear explanation of the technique
- Working example
- When/why to use it

## 📝 License

MIT License - Feel free to use these examples and configurations in your own projects!

---

*This repository is updated weekly with new content from the tutorial series. Star ⭐ and watch 👀 to stay updated!*