# Claude Code Tips & Best Practices 

Welcome to the companion repository for my **Claude Code Essentials Series** on YouTube! This repo contains examples, configurations, and best practices for using Claude Code.  You can find all my videos at: https://www.youtube.com/@SeanMatthewAI

## 📺 Tutorial Series

This repository corresponds to my Claude Code essentials series on YouTube. Each video focuses on specific techniques to improve your development workflow and get the most out of Claude Code.

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

## 📁 Repository Contents

- Sample CLAUDE.md file
- `agents/` - Custom subagent examples (coming in future episodes)
- `commands/` - Custom slash command implementations (coming in future episodes)

## 🔗 Resources

- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)
- [Awesome Claude Code Examples](https://github.com/hesreallyhim/awesome-claude-code)
- [Docker Containerization Guide](https://docs.anthropic.com/en/docs/claude-code/devcontainer)

## 🤝 Contributing

Have a great Claude Code tip or best practice? I'd love to feature it in a future video! Submit a PR with:
- Clear explanation of the technique
- Working example
- When/why to use it

## 📝 License

MIT License - Feel free to use these examples and configurations in your own projects!

---

*This repository is updated weekly with new content from the tutorial series. Star ⭐ and watch 👀 to stay updated!*