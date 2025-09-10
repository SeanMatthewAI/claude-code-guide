---
description: Scan documentation directory and create structured map with summaries
allowed-tools: Bash(find:*), Bash(ls:*), Bash(grep:*), Bash(head:*), Bash(wc:*)
---

# Documentation Structure Mapper

Create a comprehensive documentation map for the specified directory path: `$ARGUMENTS`

## Pre-scan Analysis
!`find "$ARGUMENTS" -type f \( -name "*.md" -o -name "*.txt" -o -name "*.rst" -o -name "*.adoc" \) | head -20`

## Directory Structure Overview
!`find "$ARGUMENTS" -type d | sort`

## Documentation Files Inventory
!`find "$ARGUMENTS" -type f \( -name "*.md" -o -name "*.txt" -o -name "*.rst" -o -name "*.adoc" \) -exec wc -l {} + | sort -nr`

## Your Task

1. **Analyze the documentation structure** from the directory: `$ARGUMENTS`
2. **Scan each documentation file** and extract:
   - Main headings (# ## ###)
   - Section summaries (first 2-3 sentences of each major section)
   - Code examples or API references
   - Cross-references between documents

3. **Create a new Markdown file** named `docs-map-[library-name].md` in the current directory with:
   - **Navigation Index**: Hierarchical structure of all documents
   - **Quick Reference**: Key concepts, APIs, and examples
   - **Section Summaries**: Brief descriptions of each major section
   - **Direct Links**: Relative file paths to specific sections
   - **Keywords Index**: Searchable terms and their locations

4. **File Structure Template**:
```markdown
# Documentation Map: [Library Name]
*Generated: [timestamp]*

## Quick Navigation
- [Getting Started](#getting-started)
- [API Reference](#api-reference) 
- [Examples](#examples)

## Document Structure
### [Document Name](path/to/doc.md)
**Summary**: Brief description of document purpose
**Key Sections**:
- [Section Name](path/to/doc.md#section-anchor) - Description
- [Another Section](path/to/doc.md#another-anchor) - Description

## Keywords Index
- **keyword1**: Found in [doc1.md](path), [doc2.md](path)
- **keyword2**: Found in [doc3.md](path)
```

5. **Add rule to CLAUDE.md**: Append this rule to the project's CLAUDE.md file:
```markdown
### 📚 Documentation Reference
- **For [library-name] queries**: Always consult `docs-map-[library-name].md` before searching external sources
- **Priority order**: Local docs map → Official documentation → Community resources
```

6. **Output Summary**: Provide a brief report of:
   - Total documents processed
   - Key sections identified
   - Map file location
   - CLAUDE.md update status