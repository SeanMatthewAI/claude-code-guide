---
description: Generate coding session summary with decisions, issues, and next steps
allowed-tools: Bash(mkdir:*), Bash(date:*), Bash(ls:*), Bash(wc:*)
---

# Session Summary Generator

Create a comprehensive session documentation file for focus area: **$ARGUMENTS**

## Session Context
- **Current timestamp**: !`date "+%Y-%m-%d %H:%M:%S"`
- **Sessions directory check**: !`ls -la sessions/ 2>/dev/null || echo "Sessions directory will be created"`
- **Existing sessions**: !`ls -1 sessions/*.md 2>/dev/null | wc -l || echo "0"` previous session files

## Your Task

1. **Create sessions directory** if it doesn't exist:
   !`mkdir -p sessions`

2. **Generate filename** using current date and session focus:
   - Format: `sessions/session-YYYY-MM-DD-HHMM-[focus-area].md`
   - Replace spaces in focus area with hyphens
   - Use lowercase for consistency

3. **Create session summary file** with this exact structure:

```markdown
# Coding Session Summary

### Session Date & Duration
- **Session date**: [Current date from timestamp above]
- **Session focus**: $ARGUMENTS
- **Duration**: [Estimate based on conversation length and work completed]

### Key Decisions Made
Document any:
- [ ] Architectural choices and rationale
- [ ] Library selections and why they were chosen
- [ ] Implementation patterns established
- [ ] Technology stack decisions
- [ ] Design pattern adoptions
- [ ] File structure or organization decisions

**Details**:
[Analyze our conversation and document specific decisions made]

### Issues Encountered
Include:
- [ ] Problems faced during development
- [ ] Error messages encountered
- [ ] Debugging approaches used
- [ ] Solutions implemented or attempted
- [ ] Workarounds applied
- [ ] Research conducted

**Details**:
[Document specific issues from our session]

### Deviations from Plan
Note any:
- [ ] Changes from PLANNING.md specifications
- [ ] Modifications to TASKS.md priorities
- [ ] Scope adjustments and reasoning
- [ ] Approach changes and why
- [ ] Feature modifications or pivots

**Details**:
[Document any plan changes or scope adjustments]

### Code Changes Made
Track modifications:
- [ ] New files created
- [ ] Existing files modified
- [ ] Dependencies added/updated
- [ ] Configuration changes
- [ ] Database schema updates

**File List**:
[List specific files that were created or modified]

### Next Session Context
Provide context for future sessions:
- [ ] Current state of development
- [ ] Immediate next steps
- [ ] Work in progress that needs completion
- [ ] Testing that needs to be done
- [ ] Blockers or dependencies identified
- [ ] Documentation that needs updating

**Priority Actions**:
1. [Most urgent next step]
2. [Secondary priority]
3. [Lower priority items]

### Session Artifacts
Links to relevant items:
- **Planning**: [PLANNING.md](../PLANNING.md)
- **Tasks**: [TASKS.md](../TASKS.md)
- **Previous Session**: [Link to previous session file if exists]

---
*Generated on [timestamp] using Claude Code*
```

4. **Analyze our current conversation** and fill in the template with:
   - Specific decisions we made together
   - Problems we solved or encountered
   - Code we wrote or modified
   - Next steps we identified

5. **Update TASKS.md** if any new tasks were discovered during this session

6. **Provide summary** of:
   - Session file created at: `sessions/session-[date]-[focus].md`
   - Key highlights from this session
   - Recommended next steps
   - Files that need attention