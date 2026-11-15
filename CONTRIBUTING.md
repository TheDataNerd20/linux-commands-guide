# Contributing to Linux Commands Guide

We welcome contributions from the community! Whether you're a data engineer with real-world experience or someone passionate about Linux, your input is valuable.

## How to Contribute

### 1. Fork & Clone
```bash
git clone https://github.com/YOUR_USERNAME/linux-commands-guide.git
cd linux-commands-guide
```

### 2. Create a Feature Branch
```bash
git checkout -b feature/your-feature-name
```

### 3. Make Your Changes

Possible contributions:
- Add more real-world examples from your data engineering work
- Improve explanations of existing commands
- Add new command categories or commands
- Fix typos or clarify confusing sections
- Add performance tips or optimization tricks
- Share troubleshooting scenarios

### 4. Follow Guidelines

**For new commands:**
- Include basic syntax
- Add real-world data engineering examples
- Explain common use cases
- Include warnings if dangerous

**Example format:**
```markdown
### mycommand
```bash
mycommand -option value   # Description
```

**Real-world example:**
```bash
# Your example here
```

Common pitfalls:
- Common mistake explanation
```

### 5. Commit & Push
```bash
git add .
git commit -m "Add: new Linux commands for data pipeline optimization"
git push origin feature/your-feature-name
```

### 6. Submit a Pull Request
- Open PR on GitHub
- Describe what you added and why
- Reference any issues if applicable

## Guidelines

### Content Guidelines
- ✅ Real-world data engineering use cases
- ✅ Practical examples that work
- ✅ Clear, concise explanations
- ✅ Performance considerations
- ❌ Theoretical knowledge without practical application
- ❌ Commands not relevant to data engineering

### Writing Style
- Use clear, simple language
- Include comments in code examples
- Explain the "why" not just the "what"
- Keep examples under 5 lines when possible

### Testing
- Test all commands before submitting
- Include expected output if relevant
- Mention any dependencies

## Reporting Issues

Found an error or have a suggestion?
1. Check existing issues first
2. Create a new issue with:
   - Clear title
   - Detailed description
   - Your environment (OS, Linux version)
   - Suggested fix if possible

## Code of Conduct

- Be respectful and inclusive
- Provide constructive feedback
- Help others learn
- No spam or promotional content

## Questions?

Feel free to:
- Open an issue with your question
- Comment on relevant PRs
- Start a discussion

---

Thank you for making this guide better! 🚀
