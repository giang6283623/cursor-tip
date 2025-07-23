# BoltBot Discord Integration Guide

_Your AI Programming Companion for Token-Efficient Development_

## Overview

BoltBot ⚡ is a powerful Discord AI assistant designed specifically for programming tasks and development workflows. With over **3,055 servers** and **580,697 users**, BoltBot has established itself as a trusted companion for developers worldwide.

### Key Features

- **Verified Discord App** - Official and secure integration
- **Programming-Focused AI** - Specialized in code explanations and debugging
- **Philosophical Approach** - Unique teaching style with insightful metaphors
- **Token-Efficient** - Perfect for simple tasks to save Cursor tokens
- **Multi-Language Support** - Includes Vietnamese programming explanations

## Installation Guide

### Step 1: Add BoltBot to Your Discord Server

1. **Click the Installation Link:**

   ```
   https://discord.com/oauth2/authorize?client_id=1250114494081007697
   ```

2. **Select Your Server:**

   - Choose the Discord server where you want to add BoltBot
   - Ensure you have "Manage Server" permissions

3. **Configure Permissions:**

   - **Required Permissions:**
     - Send Messages
     - Read Message History
     - Use Slash Commands
     - Embed Links
   - **Recommended Permissions:**
     - Attach Files (for code sharing)
     - Add Reactions (for interactive responses)

4. **Complete Installation:**
   - Click "Authorize" to add BoltBot to your server
   - BoltBot will appear in your server's member list

## How to Use BoltBot

### Method 1: Prefix Command

Start your message with `bb ` followed by your question:

```
bb explain React hooks with examples
bb debug this JavaScript error: Cannot read property 'map' of undefined
bb review my Python function for best practices
```

### Method 2: Tag the Bot

Mention @BoltBot in your message:

```
@BoltBot help me understand async/await in JavaScript
@BoltBot what's wrong with this CSS flexbox layout?
```

## Optimized Roleplay Prompts for Programming

### 🔥 Master Roleplay Setup (Comprehensive Senior Developer)

Use this detailed prompt to establish a persistent senior developer role that BoltBot will maintain across multiple questions:

```
bb Act as senior software engineer with 10+ years experience in JavaScript, Python, Java, C#, Go, Rust, and TypeScript. You have expertise in:
- Full-stack development (React, Vue, Angular, Node.js, Django, Spring Boot)
- Database design (SQL, NoSQL, Redis, PostgreSQL, MongoDB)
- Cloud platforms (AWS, Azure, GCP, Docker, Kubernetes)
- System architecture and microservices
- Performance optimization and security best practices
- Code review and mentoring junior developers

Your communication style:
- Provide practical, production-ready solutions
- Explain trade-offs and alternative approaches
- Include performance considerations
- Mention potential pitfalls and how to avoid them
- Give examples from real-world scenarios

When answering:
1. Start with the direct solution
2. Explain the reasoning behind your choice
3. Mention 1-2 alternatives if relevant
4. Include best practices or warnings

Reply "OK, I'm your senior dev mentor" if you understand and are ready to help with technical questions.
```

### 💡 Important: Context Persistence

**BoltBot remembers your roleplay setup!** Once you establish a role (like the senior developer above), the bot will maintain that persona for all subsequent questions until you explicitly change it. To switch roles, simply send a new roleplay prompt starting with "bb Act as [new role]..."

### 1. Code Mentor (Beginner-Friendly)

```
bb Act as coding mentor: Explain [topic] step-by-step with real examples. Include common mistakes beginners make.
```

**Example:**

```
bb Act as coding mentor: Explain Python list comprehensions step-by-step with real examples. Include common mistakes beginners make.
```

### 2. Code Reviewer (Quality Focus)

```
bb Act as code reviewer: Analyze this code for bugs, performance issues, and best practices:
[paste your code]
```

**Example:**

```
bb Act as code reviewer: Analyze this code for bugs, performance issues, and best practices:
def calculate_total(items):
    total = 0
    for item in items:
        total += item.price * item.quantity
    return total
```

### 3. Debugging Expert (Problem Solver)

```
bb Act as debugging expert: This error occurred: "[error message]". Explain why it happens and give 3 solutions.
```

**Example:**

```
bb Act as debugging expert: This error occurred: "TypeError: 'NoneType' object is not iterable". Explain why it happens and give 3 solutions.
```

### 4. Quick Senior Developer (Single Questions)

```
bb Act as senior dev: Compare [concept A] vs [concept B] with pros/cons and when to use each.
```

**Example:**

```
bb Act as senior dev: Compare Redux vs Context API with pros/cons and when to use each.
```

### 🎯 How to Use Persistent Roleplay

1. **Set up once** with the Master Roleplay Setup above
2. **Ask multiple questions** without repeating the roleplay
3. **Switch roles** only when you need a different perspective
4. **Reset if needed** by saying "bb forget previous role, act as [new role]"

**Example workflow:**

```
// First message - Setup
bb [Master Senior Developer Prompt from above]

// Bot responds: "OK, I'm your senior dev mentor"

// Then ask questions directly:
bb How would you architect a real-time chat application?
bb What's the best way to handle user authentication?
bb Review this database schema for an e-commerce app
```

### 5. Architecture Advisor (Design Patterns)

```
bb Act as architecture advisor: Suggest the best design pattern for [scenario]. Explain implementation briefly.
```

**Example:**

```
bb Act as architecture advisor: Suggest the best design pattern for user authentication system. Explain implementation briefly.
```

### 6. Performance Expert (Optimization)

```
bb Act as performance expert: Identify bottlenecks in this code and suggest optimizations:
[paste code]
```

### 7. Learning Path Guide (Structured Learning)

```
bb Act as learning guide: Create 5-step roadmap to master [technology] for [experience level].
```

**Example:**

```
bb Act as learning guide: Create 5-step roadmap to master React for intermediate developers.
```

### 8. Quick Explainer (Concept Clarification)

```
bb Act as tech explainer: Explain [concept] in 3 bullet points with one practical example.
```

**Example:**

```
bb Act as tech explainer: Explain closures in JavaScript in 3 bullet points with one practical example.
```

## Token-Saving Strategy for Cursor Usage

### 🟢 Use BoltBot For (Save Cursor Tokens)

| Task Type              | BoltBot Usage                        | Example Prompts                                      |
| ---------------------- | ------------------------------------ | ---------------------------------------------------- |
| **Quick Concepts**     | Basic explanations, syntax questions | `bb explain arrow functions vs regular functions`    |
| **Code Reviews**       | Small snippets (< 50 lines)          | `bb review this React component for issues`          |
| **Simple Debugging**   | Single errors, common mistakes       | `bb why am I getting "undefined is not a function"?` |
| **Best Practices**     | Quick guidelines, conventions        | `bb what are Python naming conventions?`             |
| **Examples**           | Code snippets, mini-implementations  | `bb show me how to use map() in JavaScript`          |
| **Comparisons**        | Technology/method differences        | `bb Docker vs VM in simple terms`                    |
| **Learning Questions** | "How does X work?" queries           | `bb how does Git branching work?`                    |

### 🔴 Use Cursor For (Complex Tasks)

| Task Type               | Why Cursor is Better                             |
| ----------------------- | ------------------------------------------------ |
| **Full Features**       | Need complete implementation with multiple files |
| **Architecture Design** | Requires deep analysis and long-form planning    |
| **Complex Debugging**   | Multi-component issues needing full context      |
| **Large Refactoring**   | Codebase-wide changes and optimizations          |
| **Documentation**       | Extensive API docs, technical specifications     |
| **Project Setup**       | Full configuration, deployment, CI/CD            |

### Optimal Workflow

1. **Start with BoltBot**: Get quick understanding and direction
2. **Clarify with BoltBot**: Ask follow-up questions for concepts
3. **Plan with Cursor**: Use for complex implementation planning
4. **Implement with Cursor**: Build features with full context
5. **Debug with BoltBot**: Quick fixes and error explanations

## Quick Reference: Common Prompts

### Debugging

```
bb Act as debugging expert: Error "[paste error]" - explain cause and fix
bb why does this code return undefined?
bb common reasons for infinite loops in [language]
```

### Code Review

```
bb Act as code reviewer: rate this function 1-10 and explain improvements:
bb security issues in this authentication code?
bb optimize this algorithm for better performance
```

### Learning

```
bb Act as coding mentor: roadmap to learn [framework] in 30 days
bb explain [concept] like I'm 5 years old
bb differences between [tech A] and [tech B] with examples
```

### Best Practices

```
bb Act as senior dev: folder structure for [type] project
bb naming conventions for [language]
bb when should I use [design pattern]?
```

## Advanced Usage Tips

### 1. Chain Questions for Deeper Learning

```
bb Act as coding mentor: explain MVC pattern with example
// After response, follow up:
bb show me how to implement MVC in Express.js
```

### 2. Context Building

```
bb Act as code reviewer: I'm building a React e-commerce app. Review this product component:
[paste code]
```

### 3. Specific Scenarios

```
bb Act as debugging expert: In Next.js, getting hydration mismatch - common causes?
bb Act as performance expert: React app slow on mobile - top 3 optimization tips?
```

### 4. Language-Specific Prompts

```
bb Act as Python expert: Pythonic way to [task]
bb Act as JS expert: modern ES6+ approach for [problem]
bb Act as CSS expert: responsive design for [layout issue]
```

## Troubleshooting

### Common Issues

1. **Bot Not Responding**

   - Verify BoltBot is online (green status)
   - Check if you used correct prefix `bb ` or mentioned @BoltBot
   - Ensure bot has message permissions in the channel

2. **Limited Response Quality**

   - Be more specific with roleplay prompts
   - Include relevant code snippets
   - Provide context about your project/skill level

3. **Permission Errors**
   - Verify "Send Messages" and "Read Message History" permissions
   - Check channel-specific permissions for the bot

## Token Efficiency Metrics

### Estimated Token Savings

- **Simple Questions**: Save 200-500 Cursor tokens per query
- **Code Reviews**: Save 300-800 tokens for small snippets
- **Debugging Help**: Save 400-1000 tokens for common errors
- **Learning Sessions**: Save 500-1500 tokens for concept explanations

### ROI Calculator

- **Daily BoltBot Usage**: 10-15 quick questions
- **Cursor Token Savings**: ~5,000-10,000 tokens/day
- **Monthly Savings**: ~150,000-300,000 tokens
- **Cost Equivalent**: Significant reduction in API costs

## Best Practices Summary

1. **Start Simple**: Use BoltBot for initial exploration and understanding
2. **Be Specific**: Include language, framework, and context in prompts
3. **Use Roleplay**: "Act as..." prompts give more focused responses
4. **Follow Up**: Build conversations for deeper learning
5. **Know When to Switch**: Move to Cursor for complex implementations
6. **Document Learnings**: Save useful BoltBot responses for reference

## Conclusion

BoltBot ⚡ is your first line of defense against unnecessary token consumption. By using the optimized prompts and strategies in this guide, you can:

- **Reduce Cursor token usage by 60-80%** for simple tasks
- **Get instant help** without waiting for complex AI processing
- **Learn more effectively** through focused, roleplay-driven conversations
- **Maintain high code quality** with quick reviews and debugging

**Remember**: BoltBot handles the quick wins, Cursor tackles the complex challenges. Together, they create an unbeatable development workflow!

---

_For more information, visit [boltbot.app](https://boltbot.app) or join BoltBot's official Discord server._

### Quick Start Checklist

- [ ] Add BoltBot to your Discord server
- [ ] Test with `bb help` command
- [ ] Try 3 different roleplay prompts
- [ ] Identify your most common programming questions
- [ ] Create custom prompt templates for your workflow
- [ ] Set up token usage tracking
- [ ] Share with your development team
