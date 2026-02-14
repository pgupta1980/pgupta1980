# 👋 Hi, I'm pgupta1980

> Building with AI-assisted development using Claude Code

## 🚀 About Me

I leverage AI-powered development workflows to build software more efficiently. I'm particularly passionate about using Claude Code to enhance productivity, code quality, and collaborative development.

---

## 🛠️ Claude Code: Tips, Tricks & Best Practices

### 🎯 Quick Start

Claude Code is Anthropic's official CLI tool that brings Claude's AI capabilities directly into your development workflow.

```bash
# Install Claude Code
npm install -g @anthropic-ai/claude-code

# Start a session
claude-code
```

---

## 💡 Essential Tips & Tricks

### 1. **Leverage the `.claude/` Directory**

Organize your AI-assisted workflow with project-specific configurations:

```
.claude/
├── commands/          # Custom slash commands
├── agents/            # Specialized sub-agents
├── skills/            # On-demand domain skills
├── scratchpad.md      # Persistent context between sessions
└── settings.json      # Project-specific settings
```

### 2. **Master Slash Commands**

Create custom commands for repetitive tasks:

```markdown
<!-- .claude/commands/review-pr.md -->
Review the current PR with focus on:
- Type safety and error handling
- Test coverage
- Security vulnerabilities
- Performance implications
```

Then use: `/review-pr`

### 3. **Use Specialized Agents**

Launch focused agents for specific tasks:

- **Explore Agent**: Deep codebase exploration
- **Plan Agent**: Design implementation strategies
- **Code Reviewer**: Thorough code reviews
- **Domain Modeler**: Design domain models first

```markdown
Task: Launch an Explore agent to find all authentication-related code
```

### 4. **Maintain Context with Scratchpad**

Use `.claude/scratchpad.md` for persistent context across sessions:

```markdown
## Current Focus
Working on user authentication - using JWT tokens

## Open Questions
- Should we use refresh tokens?
- Rate limiting strategy?

## Decisions Made
- Using bcrypt for password hashing
- Session timeout: 24 hours
```

---

## 🎨 Best Practices

### **Project Setup**

1. **Create a `CLAUDE.md` file** in your repository root with:
   - Project overview and tech stack
   - Architecture decisions
   - Development conventions
   - How to run/test/deploy
   - Custom commands and agents available

2. **Use `.claudeignore`** to exclude unnecessary files:
   ```
   node_modules/
   .git/
   dist/
   *.log
   .env
   ```

3. **Configure project-specific settings** in `.claude/settings.json`:
   ```json
   {
     "mcp": {
       "servers": {
         "filesystem": {
           "type": "stdio",
           "command": "npx",
           "args": ["-y", "@modelcontextprotocol/server-filesystem", "src/"]
         }
       }
     }
   }
   ```

### **Development Workflow**

#### ✅ DO:
- Use dedicated tools (Read, Edit, Write) instead of bash commands
- Launch parallel agents for independent exploration tasks
- Update scratchpad before ending sessions (`/handoff`)
- Create focused, single-responsibility commands
- Write clear, specific prompts with context
- Review AI-generated code before committing

#### ❌ DON'T:
- Use bash for file operations when dedicated tools exist
- Let context window fill up without handoff
- Commit without reviewing diffs
- Create overly generic commands
- Skip testing AI-generated code
- Assume the AI knows your entire codebase

### **Code Quality Workflow**

```markdown
1. Plan first: Use /plan-feature or Plan agent
2. Implement: Let Claude write the code
3. Review: Use /review-diff or code-reviewer agent
4. Test: Create tests or use /quick-test
5. Commit: Review and commit with descriptive message
6. Document: Use /document-session for significant work
```

---

## 🎓 Advanced Techniques

### **Parallel Agent Execution**

Launch multiple agents simultaneously for faster exploration:

```markdown
Please launch 3 Explore agents in parallel:
1. Find all database schemas and models
2. Find all API endpoints and routes
3. Find all authentication and authorization code
```

### **Custom Skills with On-Demand Loading**

Create domain-specific skills that load only when needed:

```yaml
# .claude/skills/database-migration.yaml
name: database-migration
description: Guide for creating and running database migrations
prompt: |
  # Database Migration Guide

  1. Create migration: `alembic revision -m "description"`
  2. Write upgrade() and downgrade() functions
  3. Test migration: `alembic upgrade head`
  4. Test rollback: `alembic downgrade -1`
```

### **MCP Server Integration**

Extend Claude's capabilities with Model Context Protocol servers:

```json
{
  "mcp": {
    "servers": {
      "postgres": {
        "type": "stdio",
        "command": "uvx",
        "args": ["mcp-server-postgres", "postgresql://localhost/mydb"]
      },
      "github": {
        "type": "stdio",
        "command": "npx",
        "args": ["-y", "@modelcontextprotocol/server-github"]
      }
    }
  }
}
```

---

## 📚 Command Cheatsheet

| Command | Description |
|---------|-------------|
| `/help` | Show available commands |
| `/handoff` | Save context before ending session |
| `/commit` | Create a git commit with AI-generated message |
| `/review-diff` | Review changes against main branch |
| `/clear` | Clear conversation history |
| `/undo` | Undo last action |
| `/settings` | Open settings |

---

## 🔥 Pro Tips

1. **Work Backwards**: When planning features, start from the end goal and work backwards to current state

2. **Domain-Driven Design**: Model your domain first, then build services, then adapters

3. **Test-Driven Development**: Write tests alongside or before implementation

4. **Keep It Simple**: Avoid over-engineering; make only the changes requested

5. **Incremental Commits**: Commit often with focused, atomic changes

6. **Read Before Edit**: Always read a file before modifying it

7. **Context Management**: When context reaches ~60%, do a handoff and start fresh

8. **Verify AI Output**: Always review and test AI-generated code before shipping

9. **Use Type Hints**: Strongly typed code helps Claude understand and generate better code

10. **Clear Prompts**: Be specific about what you want - vague prompts get vague results

---

## 🌟 Example Workflows

### Feature Development

```markdown
1. "/plan-feature user authentication with JWT"
2. Review plan, ask questions, approve
3. Claude implements the feature
4. "/quick-test" to run relevant tests
5. "/review-diff" to review changes
6. Fix any issues found
7. "/commit" to create a commit
8. "/document-session" to log the work
```

### Bug Investigation

```markdown
1. "Launch an Explore agent to find all error handling related to user login"
2. Review agent findings
3. "Read the specific files" that seem relevant
4. "Fix the bug in auth.py where exceptions aren't caught"
5. "Add a test case that reproduces the bug"
6. "/quick-test" to verify the fix
7. "/commit" with descriptive message
```

### Code Review

```markdown
1. "Launch a code-reviewer agent for the current PR"
2. Review findings with severity ratings
3. Address critical and high-severity issues
4. Discuss medium-severity items
5. Document decisions in scratchpad
6. "/commit" fixes
```

---

## 📖 Resources

- [Claude Code Documentation](https://docs.anthropic.com/claude-code)
- [Claude API Documentation](https://docs.anthropic.com/)
- [Model Context Protocol](https://modelcontextprotocol.io/)
- [Claude Code GitHub](https://github.com/anthropics/claude-code)

---

## 📫 Connect With Me

- GitHub: [@pgupta1980](https://github.com/pgupta1980)

---

<div align="center">

### 💻 "Code smarter, not harder"

Built with ❤️ using Claude Code

</div>
