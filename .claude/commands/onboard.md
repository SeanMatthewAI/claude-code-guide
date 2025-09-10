---
description: Onboard Claude Code by analyzing recent session and current tasks
allowed-tools: Bash(ls:*), Bash(head:*), Bash(tail:*), Bash(cat:*), Bash(find:*)
---

# Session Onboarding & Context Loading

Resume development work by analyzing the most recent session and current task status.

## Recent Session Analysis
**Most recent session file**:
!`ls -t sessions/*.md 2>/dev/null | head -1`

**Session content**:
!`ls -t sessions/*.md 2>/dev/null | head -1 | xargs cat`

## Current Task Status
**TASKS.md overview**:
!`head -50 TASKS.md`

## Project Context Files
**PLANNING.md summary**:
!`head -30 PLANNING.md`

**CLAUDE.md key rules**:
!`grep -A 2 "###" CLAUDE.md | head -20`

## Your Onboarding Task

Based on the session analysis and current tasks, provide me with:

### 1. **Session Context Summary**
- **Last session focus**: What was the main area of work?
- **Key decisions made**: What architectural or implementation choices were established?
- **Current development state**: Where did we leave off?
- **Files modified**: What code was changed in the last session?

### 2. **Immediate Next Steps**
From the "Next Session Context" and "Priority Actions" in the recent session:
- **Primary objective**: What should we work on first?
- **Required files**: Which files need attention?
- **Dependencies**: What needs to be completed before other work?
- **Testing needs**: What testing is pending?

### 3. **Task Status Assessment**
Review TASKS.md and identify:
- **Active tasks**: What's currently in progress?
- **Blocked items**: What's waiting on dependencies?
- **Quick wins**: What can be completed easily?
- **Priority conflicts**: Any tasks that need reordering?

### 4. **Development Environment Check**
Verify readiness:
- **Required tools**: Are all necessary packages/tools available?
- **Configuration**: Are environment variables and configs set?
- **Database state**: Any pending migrations or data issues?
- **Build status**: Does the project currently build/run successfully?

### 5. **Recommended Action Plan**
Provide a clear, prioritized list:
1. **Immediate action**: What should we start with right now?
2. **Follow-up tasks**: What comes next in logical order?
3. **Potential blockers**: What might slow us down?
4. **Success criteria**: How will we know this work is complete?

### 6. **Context Questions**
If any context is unclear, ask:
- Missing information about project state
- Unclear requirements or specifications
- Technical decisions that need clarification
- Resource or dependency questions

**Goal**: Get me fully up to speed and ready to continue productive development work immediately, with clear understanding of where we are and what needs to happen next.

## Additional Context Loading
**Recent file changes** (if git available):
!`git log --oneline -10 2>/dev/null || echo "Git not available"`

**Project structure reminder**:
!`find . -maxdepth 2 -type f -name "*.md" -o -name "*.json" -o -name "package.json" | sort`