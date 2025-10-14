# Global Rules & Prompts

This directory contains global prompt rules designed to enhance AI-assisted development workflows. Each prompt serves a specific purpose and can be used individually or in combination.

## Available Prompts

### 1. `global-rule-19-09-2025-1.md` - Core Development Standards

**Purpose:** Establishes fundamental coding standards, best practices, and communication protocols.

**Key Features:**

- Code quality and best practices enforcement
- Project organization and file management
- Security and validation practices
- Testing and documentation standards
- Communication and response protocols

**Usage:** Can be used standalone or combined with other prompts.

---

### 2. `global-rule-19-09-2025-2-reasoning-rule.md` - Advanced Reasoning Methods

**Purpose:** Provides structured reasoning frameworks for complex problem-solving.

**Key Features:**

- **MCTS Reasoning** - Monte Carlo Tree Search for decision trees
- **Beam Search Reasoning** - Parallel solution exploration
- **R1 Reasoning** - Comprehensive component analysis
- **Hybrid Reasoning** - Multi-method combination

**Activation Tags:**

- `[Inference-MCTS]` - For decision-tree-based problems
- `[Inference-BEAM]` - For solution comparison
- `[Inference-R1]` - For comprehensive analysis
- `[Inference-HYBRID]` - For complex multi-dimensional problems

**Usage:** Best used together with `global-rule-19-09-2025-1.md` for complex tasks.

---

### 3. `global-rule-12-10-2025-inspired-by-BIDARA-Chat-Bot-NASA.md` - STAR Systems Thinking

**Purpose:** Inspired by NASA's BIDARA chatbot (biomimicry simulation), this prompt helps you apply (and learn) systems thinking approaches to everything.

**Key Features:**

- Systems thinking fundamentals
- Complex problem-solving strategies
- Cognitive and metacognitive skill development
- Multi-component interaction analysis
- Emergent behavior debugging

**Activation:** Use `[STAR-Thinking]` tag

**Usage:** Can only be used together with `global-rule-19-09-2025-1.md` (not compatible with the reasoning-rule prompt).

---

## Compatibility Matrix

| Prompt                                                       | Can be used with                   | Notes                       |
| ------------------------------------------------------------ | ---------------------------------- | --------------------------- |
| `global-rule-19-09-2025-1.md`                                | All prompts                        | Core foundation prompt      |
| `global-rule-19-09-2025-2-reasoning-rule.md`                 | `global-rule-19-09-2025-1.md`      | For complex reasoning tasks |
| `global-rule-12-10-2025-inspired-by-BIDARA-Chat-Bot-NASA.md` | `global-rule-19-09-2025-1.md` only | For systems thinking        |

**Valid Combinations:**

- ✅ `global-rule-19-09-2025-1.md` + `global-rule-19-09-2025-2-reasoning-rule.md`
- ✅ `global-rule-19-09-2025-1.md` + `global-rule-12-10-2025-inspired-by-BIDARA-Chat-Bot-NASA.md`
- ❌ All three together (not recommended)

---

## Usage Experience

### Pros (based on real-world application)

- **Improved Accuracy:** Significantly increases precision in addressing requirements
- **Complex Problem Handling:** Better equipped to solve intricate, multi-faceted challenges
- **Structured Thinking:** Reasoning modes provide systematic approaches to difficult tasks
- **Learning Opportunity:** Helps developers learn better thinking patterns

### Cons (token consumption)

- **High Token Usage:** When set to "always" mode, responses consume significant tokens
- **Slower Responses:** More processing time for simple tasks
- **Overkill for Simple Tasks:** Not necessary for straightforward, small tasks

---

## When to Use What

**Use `global-rule-19-09-2025-1.md` when:**

- Starting any new project
- Need consistent coding standards
- Working on production code

**Add `global-rule-19-09-2025-2-reasoning-rule.md` when:**

- Facing complex architectural decisions
- Analyzing multiple solution approaches
- Need systematic problem decomposition
- Working on optimization problems

**Add `global-rule-12-10-2025-inspired-by-BIDARA-Chat-Bot-NASA.md` when:**

- Dealing with complex system interactions
- Need to understand emergent behaviors
- Analyzing system-wide impacts
- Want to learn systems thinking approaches
- Debugging multi-component issues

---

## Best Practices

1. **Start Simple:** Use only `global-rule-19-09-2025-1.md` for routine tasks
2. **Scale Up:** Add reasoning or systems thinking prompts only when complexity demands it
3. **Use Tags:** Leverage activation tags for selective feature usage
4. **Monitor Tokens:** Be mindful of token consumption on simple tasks
5. **Learn Patterns:** Use these prompts as learning tools, not just automation

---

## Further Reading

See `guide.md` for detailed setup instructions and examples.
