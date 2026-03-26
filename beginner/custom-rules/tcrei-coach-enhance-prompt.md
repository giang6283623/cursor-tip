# TCREI Prompt Coach - Interactive Prompt Engineering with Google's TCREI Framework

A structured coaching command that transforms vague prompts into high-quality, framework-aligned prompts through interactive dialogue and education.

## Table of Contents

- [Purpose](#purpose)
- [When to Use](#when-to-use)
- [TCREI Framework Reference](#tcrei-framework-reference)
- [How It Works](#how-it-works)
- [Coaching Engine](#coaching-engine)
- [Platform-Specific Output](#platform-specific-output)
- [Advanced Techniques](#advanced-techniques)
- [Guardrails and Safety](#guardrails-and-safety)
- [Bilingual Support](#bilingual-support)
- [Examples](#examples)
- [Anti-Patterns](#anti-patterns)
- [Troubleshooting](#troubleshooting)
- [Metadata](#metadata)
- [Related Commands](#related-commands)

---

## Purpose

Use this command to learn and apply Google's TCREI prompting framework with hands-on coaching. It helps you:

- Break down any prompt into Task, Context, References, Evaluate, and Iterate components
- Build prompts from scratch when you have an idea but no starting prompt
- Identify and fix weak spots in existing prompts
- Generate platform-optimized variants for Claude, ChatGPT, or Gemini
- Learn prompt engineering principles through guided practice, not lectures
- See concrete before/after comparisons of your own prompts

Guiding idea: a coach builds your skill, not just your prompt.

---

## When to Use

Run `/tcrei-coach` when you:

- Have a prompt that gets inconsistent or low-quality results
- Want to learn structured prompt engineering through practice
- Need to adapt a prompt for a different AI platform
- Are starting from scratch with just an intent or goal
- Want to understand why a prompt works or fails
- Need to optimize token usage without losing quality

Skip it when:

- You need a quick one-off question answered (just ask directly)
- Your prompt already produces consistent, high-quality output
- You want the AI to execute a task, not coach you on prompts

---

## TCREI Framework Reference

TCREI is a prompt engineering framework from Google's Prompting Essentials course (Coursera, 2025). Each component addresses a specific failure mode in prompts.

### T - Task

**What it is:** The specific action you want the AI to perform.

**Components:**

- **Action verb**: Write, analyze, compare, summarize, generate, debug, review
- **Persona** (optional): Who the AI should act as (expert reviewer, junior developer, teacher)
- **Output format**: What shape the response should take (list, essay, JSON, table, code)
- **Constraints**: Boundaries on length, tone, scope, or style

**Completion criteria -- Task is done when:**

- [ ] An action verb is defined (not "help me with" or "do something about")
- [ ] Output format is specified (not left to AI's default)
- [ ] Constraints are explicit (length, tone, audience level)
- [ ] Persona is set if domain expertise matters

**Common mistakes:**

- Too vague: "Help me with marketing" (no action verb, no format, no constraints)
- Too broad: "Write everything about machine learning" (no scope boundary)
- Conflicting: "Write a short, comprehensive, detailed summary" (short vs comprehensive)
- Missing format: "Tell me about X" (essay? bullet points? table? code?)

### C - Context

**What it is:** Background information the AI needs to produce relevant output.

**Components:**

- **Audience**: Who will read or use the output (executives, developers, students)
- **Domain**: The field or subject area (healthcare, fintech, education)
- **Situation**: The current state or problem being addressed
- **Constraints**: Technical limits, regulatory requirements, existing systems
- **Why**: The purpose behind the request (motivation, goal, intended use)

**Completion criteria -- Context is done when:**

- [ ] Audience is identified (who reads this?)
- [ ] Domain is clear (what field?)
- [ ] Current situation is described (what exists now?)
- [ ] Purpose is stated (why do you need this?)
- [ ] Relevant constraints are listed

**Common mistakes:**

- No audience: AI cannot calibrate complexity or terminology
- Missing domain: AI defaults to generic advice instead of domain-specific
- No "why": AI cannot prioritize what matters most
- Over-context: Dumping irrelevant background that dilutes focus

### R - References

**What it is:** Examples, standards, or formats that guide the AI's output quality and style.

**Components:**

- **Few-shot examples**: 2-3 examples of desired input/output pairs
- **Format templates**: Exact structure you want the output to follow
- **Style references**: Tone, voice, or writing style to emulate
- **Standards**: Industry norms, coding conventions, documentation formats
- **Benchmarks**: Examples of good output vs bad output

**Completion criteria -- References is done when:**

- [ ] At least 1-2 examples or format specs are provided
- [ ] Examples show the desired quality level
- [ ] Format template is concrete (not "make it look nice")
- [ ] Style expectations are clear if they matter

**Common mistakes:**

- Zero examples: AI has nothing to calibrate against
- Vague format: "Make it professional" (what does that mean specifically?)
- Contradictory examples: Examples that show conflicting styles
- Too many examples: More than 5 creates confusion, 2-3 is optimal

### E - Evaluate

**What it is:** Success criteria and metrics to judge whether the AI's output meets your needs.

**Components:**

- **Quality criteria**: What "good" looks like (accuracy, completeness, clarity)
- **Measurable metrics**: Specific thresholds (under 500 words, covers 5 topics, etc.)
- **Acceptance tests**: How to verify the output works
- **Failure indicators**: What would make the output unacceptable

**Completion criteria -- Evaluate is done when:**

- [ ] 3-5 measurable success criteria are defined
- [ ] At least one criterion is objectively verifiable
- [ ] Failure indicators are stated (what counts as bad output?)

**Common mistakes:**

- No criteria: "Make it good" (good by what measure?)
- Unmeasurable: "Make it engaging" (how do you measure engaging?)
- Missing failure case: Not knowing what bad output looks like

### I - Iterate

**What it is:** A plan for refining the prompt based on initial results.

**Components:**

- **What to change first**: Which component to adjust if output is off
- **Improvement signals**: How to identify what needs fixing
- **Iteration limit**: How many rounds before rethinking the approach
- **Version tracking**: Keeping notes on what changed and why

**Completion criteria -- Iterate is done when:**

- [ ] A concrete first adjustment is planned
- [ ] Signals for "output is off" are defined
- [ ] Maximum iteration rounds are set (typically 2-4)

**Common mistakes:**

- No plan: Randomly tweaking without direction
- Changing everything: Adjusting all components at once (cannot isolate what helped)
- No tracking: Repeating the same failed adjustments

**Attribution:** TCREI framework based on Google's Prompting Essentials course (Coursera, 2025). Additional research from aiwithkatarina.com and swastisolanki.com.

---

## How It Works

The coaching process runs in 10 phases. Each phase uses the `AskQuestion` tool for structured dialogue.

```mermaid
flowchart TD
    Start["/tcrei-coach"] --> Detect["Phase 0: Language Detection"]
    Detect --> Level["Phase 1: Assess User Level"]
    Level -->|AskQuestion| UserLevel{"Beginner / Intermediate / Advanced"}

    UserLevel --> ColdCheck{"User has existing prompt?"}
    ColdCheck -->|Yes| Decompose["Phase 2: Decompose into TCREI"]
    ColdCheck -->|No| ColdStart["Phase 2b: Cold Start - Build from scratch"]

    Decompose --> Task["Phase 3: Coach TASK"]
    ColdStart --> Task
    Task -->|"AskQuestion (max 3 rounds)"| TaskDone{"Task complete?"}
    TaskDone -->|No| Task
    TaskDone -->|Yes| Context["Phase 4: Coach CONTEXT"]

    Context -->|"AskQuestion (max 3 rounds)"| ContextDone{"Context complete?"}
    ContextDone -->|No| Context
    ContextDone -->|Yes| References["Phase 5: Coach REFERENCES"]

    References -->|"AskQuestion (max 3 rounds)"| RefDone{"References complete?"}
    RefDone -->|No| References
    RefDone -->|Yes| Evaluate["Phase 6: Define EVALUATION"]

    Evaluate --> Iterate["Phase 7: Plan ITERATION"]
    Iterate --> Assembly["Phase 8: Assemble Final Prompt"]

    Assembly --> Platform{"Platform selection"}
    Platform --> Claude["Claude variant with XML tags"]
    Platform --> ChatGPT["ChatGPT variant with GOLDEN"]
    Platform --> Gemini["Gemini variant"]

    Assembly --> Compare["Phase 9: Before/After Comparison"]
    Compare --> Execute{"Optional: Test prompt?"}
    Execute -->|Yes| RunTest["Execute in new context"]
    Execute -->|No| Lessons["Phase 10: Lessons + Documentation"]
    RunTest --> Lessons
```

### Phase 0: Language Detection

Detect whether the user communicates in Vietnamese or English from their first message.

- Vietnamese triggers: any Vietnamese text, diacritics, Vietnamese greetings
- Default: English
- All subsequent coaching, questions, and explanations adapt to the detected language
- User can switch language at any time by saying "switch to English" / "chuyển sang tiếng Việt"

### Phase 1: Assess User Level

Use `AskQuestion` to determine the user's prompt engineering experience:

```
How would you describe your prompt engineering experience?
- Beginner: I mostly just type what I want and hope for the best
- Intermediate: I know some techniques but want to be more systematic
- Advanced: I understand frameworks and want to optimize for specific platforms
```

**Level-specific behavior:**

| Aspect               | Beginner                        | Intermediate             | Advanced                       |
| -------------------- | ------------------------------- | ------------------------ | ------------------------------ |
| Explanations         | Detailed, with analogies        | Concise, key points only | Minimal, focus on optimization |
| Questions            | More guidance, fewer open-ended | Balanced mix             | Direct, technical              |
| Examples             | Provided proactively            | On request               | Skip unless needed             |
| TCREI theory         | Teach each component            | Reference briefly        | Assume knowledge               |
| Rounds per component | Up to 3                         | Up to 2                  | Usually 1                      |

### Phase 2: Decompose or Cold Start

**If user has an existing prompt:** Break it into TCREI components. Show what is present, what is missing, and what is weak. Present this decomposition to the user.

**If user has NO prompt (cold start):** Ask for their intent using `AskQuestion`:

```
What do you want to achieve with your prompt? Describe your goal in 1-3 sentences.

Example: "I want to write a blog post about AI in healthcare for a non-technical audience"
Example: "I need to generate test cases for a REST API"
Example: "I want to summarize meeting notes into action items"
```

Then build the first draft of Task from their intent and proceed to Phase 3.

### Phases 3-7: Component Coaching

For each TCREI component (Task, Context, References, Evaluate, Iterate), the coaching follows this loop:

```text
FOR each component in [Task, Context, References, Evaluate, Iterate]:
  round = 0
  WHILE component is not complete AND round < 3:
    1. Show current state of this component
    2. Identify gaps using completion criteria
    3. Ask 2-4 targeted questions via AskQuestion
    4. Incorporate answers
    5. Show updated component
    6. round++

  IF round == 3 AND still incomplete:
    Apply smart defaults with explanation
    Note what was defaulted for user's awareness
```

**Session limits:** Max 3 rounds per component. Total coaching session target: 10-15 minutes.

**Shorthand support:** Users can reply with:

- `defaults` -- accept all recommended options
- `1a 2b 3c` -- answer multiple questions in one reply
- `skip` -- accept current state and move to next component

---

## Coaching Engine

### Question Templates per Component

#### Task Questions

```
Round 1 - Defining the action:

1) What action should the AI perform?
   a) Write/Generate (create new content)
   b) Analyze/Review (examine existing content)
   c) Transform/Convert (change format or structure)
   d) Summarize/Extract (condense or pull out key info)
   e) Other (describe)

2) Should the AI adopt a specific persona or role?
   a) Yes - domain expert (specify field)
   b) Yes - specific role (e.g., teacher, reviewer, editor)
   c) No persona needed
   d) Not sure - suggest one based on my task

3) What output format do you need?
   a) Prose/paragraphs
   b) Bullet points or numbered list
   c) Table or structured data
   d) Code or technical output
   e) JSON/YAML/structured format
   f) Other (describe)
```

#### Context Questions

```
Round 1 - Background and audience:

1) Who will read or use this output?
   a) Technical audience (developers, engineers)
   b) Business audience (managers, executives)
   c) General audience (non-specialists)
   d) Mixed audience
   e) Just me (personal use)

2) What is the current situation or problem?
   (Open text - describe what exists now and what needs to change)

3) Why do you need this? What will you do with the output?
   a) Decision-making (need analysis to choose)
   b) Communication (need to explain something to others)
   c) Creation (need to produce a deliverable)
   d) Learning (need to understand a topic)
   e) Automation (need repeatable output)
```

#### References Questions

```
Round 1 - Examples and standards:

1) Do you have examples of good output to share?
   a) Yes - I can paste 1-2 examples
   b) No, but I can describe what good looks like
   c) No - please suggest a format based on my task
   d) I have a template or style guide to follow

2) What tone or style should the output use?
   a) Formal/professional
   b) Conversational/friendly
   c) Technical/precise
   d) Educational/explanatory
   e) Match a specific reference (paste it)

3) Are there formatting standards to follow?
   a) Markdown with headers and lists
   b) Plain text only
   c) Code with comments
   d) Specific template (describe)
   e) No preference - use best judgment
```

#### Evaluate Questions

```
How will you judge if the output is good? Select all that apply:

a) Accuracy - factually correct, no hallucinations
b) Completeness - covers all required topics
c) Brevity - concise, no filler
d) Actionability - output can be used immediately
e) Tone match - matches the intended audience
f) Format compliance - follows the specified structure
g) Other criteria (describe)
```

#### Iterate Questions

```
If the first output is not quite right, what would you adjust first?

a) Task - make the instruction clearer or more specific
b) Context - add more background or constraints
c) References - provide better examples
d) Evaluate - refine success criteria
e) Not sure - guide me on common iteration strategies
```

### Cold Start Handler

When the user has no prompt, guide them through intent discovery:

1. Ask what they want to achieve (open-ended, 1-3 sentences)
2. Ask who the output is for
3. Ask what format they imagine
4. Build a rough Task statement from answers
5. Proceed to normal TCREI coaching flow

### Stuck Handler

When a user cannot answer a question:

1. Offer a smart default with reasoning: "Based on your task, I'd suggest X because Y"
2. Explain the tradeoff of using the default vs a more specific answer
3. Offer to revisit the question later if the user gains clarity
4. Never block progress -- always provide a path forward

### Contradiction Handler

When answers conflict with each other:

1. Surface the contradiction explicitly: "You mentioned X earlier, but now Y. These may conflict because..."
2. Ask the user to resolve: "Which takes priority?"
3. If unresolved, note it as a risk in the final prompt documentation

---

## Platform-Specific Output

### Phase 8: Assembly with Platform Selection

Ask the user which platform they target via `AskQuestion`:

```
Which AI platform will you use this prompt with?
a) Claude (Anthropic) - optimized with XML tags and natural language
b) ChatGPT (OpenAI) - optimized with GOLDEN framework structure
c) Gemini (Google) - optimized for search intent and conciseness
d) Universal - a general version that works across platforms
e) Multiple - generate variants for comparison
```

### Claude Variant Template

Claude works best with XML-structured prompts and natural conversational language.

```xml
<document>
[Reference materials, examples, data -- placed at the top for long-context utilization]
</document>

<instructions>
You are [persona from Task].

[Task description with action verb, format, and constraints]

<context>
[Background information: audience, domain, situation, purpose]
</context>

<requirements>
- [Constraint 1]
- [Constraint 2]
- [Format specification]
</requirements>

Think through this step by step before responding.
</instructions>
```

**Claude-specific tips:**

- Place long reference documents at the top inside `<document>` tags
- Use natural, conversational language for instructions
- Explicitly request step-by-step reasoning when needed
- XML tags help Claude parse structure in long prompts

### ChatGPT Variant Template (GOLDEN Framework)

ChatGPT benefits from the GOLDEN structure: Goal, Output, Limits, Data, Evaluation, Next.

```markdown
## Goal

[What you want to achieve - from Task]

## Output

[Exact format, structure, and length expected - from Task + References]

## Limits

[Constraints, boundaries, what NOT to do - from Task constraints]

## Data

[Background information and context - from Context]
[Reference examples - from References]

## Evaluation

[How to judge quality - from Evaluate]

## Next

[What to do after generating - from Iterate]
```

**ChatGPT-specific tips:**

- Use clear markdown headers for section separation
- Include few-shot examples in the Data section
- System message for persona, user message for task
- Be explicit about what NOT to include (reduces hallucination)

### Gemini Variant Template

Gemini excels at comparative analysis, evidence-based responses, and concise output.

```text
Role: [Persona from Task]

Task: [Clear action verb + specific deliverable]

Context:
- Audience: [who]
- Domain: [what field]
- Purpose: [why]

Requirements:
1. [Specific requirement with measurable criterion]
2. [Specific requirement with measurable criterion]
3. [Specific requirement with measurable criterion]

Examples of good output:
[1-2 concise examples from References]

Evaluate your response against:
- [Criterion 1]
- [Criterion 2]
- [Criterion 3]
```

**Gemini-specific tips:**

- Keep total prompt under 4,000 characters when possible
- Use numbered lists for requirements (Gemini tracks these well)
- Request citations or evidence when factual accuracy matters
- Structure for comparison when asking about alternatives

### Side-by-Side Comparison

When the user selects "Multiple" platforms, present the same prompt adapted for each platform in a comparison table showing the structural differences.

---

## Advanced Techniques

### Few-Shot Examples

Teach the user to include 2-3 input/output pairs in the References section:

**Why it works:** Few-shot examples anchor the AI's output format, tone, and quality level more reliably than instructions alone.

**Pattern:**

```text
Here are examples of the desired output:

Input: [example input 1]
Output: [example output 1]

Input: [example input 2]
Output: [example output 2]

Now apply the same approach to:
Input: [actual input]
```

**When to use:** When output format or style is critical. When instructions alone produce inconsistent results.

**When to skip:** When the task is straightforward and well-understood by the model. When examples would take more tokens than they save.

### Output Format Specification

Guide the user to define exact output structure:

```text
Respond in this exact format:

## Summary
[2-3 sentence overview]

## Key Findings
- Finding 1: [description]
- Finding 2: [description]

## Recommendation
[1 paragraph with specific action]
```

### Chain-of-Thought Guidance

**When to add "think step by step":**

- Complex reasoning tasks (math, logic, multi-step analysis)
- Tasks requiring comparison of multiple options
- Debugging or root cause analysis
- Multi-criteria evaluation

**When NOT to add it:**

- Simple generation tasks (write a poem, list items)
- Format conversion (translate, reformat)
- Tasks where reasoning slows down output without improving quality

### Anti-Pattern Detection

During coaching, watch for and warn the user about:

| Anti-Pattern                 | Signal                                           | Fix                                           |
| ---------------------------- | ------------------------------------------------ | --------------------------------------------- |
| **Over-instruction**         | Repeating the same constraint in different words | Remove duplicates, keep one clear statement   |
| **Under-specification**      | Missing format, audience, or criteria            | Add the missing component via TCREI           |
| **Conflicting requirements** | "Be brief" + "Be comprehensive"                  | Choose one priority, make the other secondary |
| **Token waste**              | Filler phrases like "I want you to" repeated     | Cut to direct instructions                    |
| **Prompt stuffing**          | Cramming unrelated tasks into one prompt         | Split into separate prompts                   |
| **Vague persona**            | "Be an expert" without domain                    | Specify the domain and expertise level        |
| **Missing success criteria** | No way to judge if output is good                | Add Evaluate component                        |

### Before/After Transformation Examples

#### Example 1: Beginner Level -- Blog Post

**Before (score: 2/10):**

```text
Write about AI in healthcare
```

**TCREI Analysis:**

- Task: Partially present (write), but no format, no constraints, no persona
- Context: Zero -- no audience, no purpose, no situation
- References: Zero -- no examples, no style guide
- Evaluate: Zero -- no success criteria
- Iterate: Zero -- no refinement plan

**After (score: 8.5/10):**

```text
You are a health technology journalist writing for a general audience.

Write a 1,200-word blog post about how AI is transforming patient diagnosis in hospitals.

Context:
- Audience: Non-technical readers interested in healthcare innovation
- Purpose: Educate and inform, not sell
- Tone: Accessible, optimistic but balanced

Include:
- 2-3 real-world examples of AI diagnostic tools in use
- A brief explanation of how these tools work (no jargon)
- One section on limitations and risks
- A closing paragraph with outlook for the next 3-5 years

Format: Markdown with H2 headers for each section. Use short paragraphs (3-4 sentences max).

Success criteria:
1. A non-technical reader can understand every paragraph
2. All examples are from real, named organizations
3. Limitations section is honest, not dismissive
4. Total length: 1,000-1,400 words
```

#### Example 2: Intermediate Level -- Code Review

**Before (score: 4/10):**

```text
Review my code and tell me what's wrong
```

**After (score: 9/10):**

```text
You are a senior software engineer conducting a code review for a mid-level developer.

Review the following Python code for:
1. Bugs or logical errors
2. Performance issues (focus on database queries and loops)
3. Security vulnerabilities (input validation, SQL injection, auth checks)
4. Code style violations (PEP 8, naming conventions)

Context:
- This is a REST API endpoint for user profile updates
- Framework: FastAPI with SQLAlchemy ORM
- Database: PostgreSQL
- The endpoint handles ~500 requests/minute in production

For each issue found, provide:
- Severity: Critical / Warning / Suggestion
- Line reference
- What's wrong (1 sentence)
- How to fix it (code snippet)

Format output as a markdown table with columns: Severity | Line | Issue | Fix

Do NOT rewrite the entire code. Only show specific fixes for each issue found.

[Code to review pasted below]
```

#### Example 3: Advanced Level -- Multi-Platform Optimization

**Before (score: 5/10):**

```text
I need a system prompt for a customer support chatbot that handles refund requests.
Be professional and follow company policy.
```

**After -- Claude variant (score: 9.5/10):**

```xml
<document>
<company_policy>
- Refunds within 30 days of purchase: full refund, no questions
- Refunds 31-60 days: store credit only
- Refunds after 60 days: case-by-case, manager approval needed
- Damaged items: always full refund with photo evidence
- Digital products: no refund after download, exceptions for technical issues
</company_policy>

<response_examples>
Customer: I bought this 2 weeks ago and it doesn't work.
Agent: I'm sorry to hear that. Since your purchase was within our 30-day window, I can process a full refund right away. Could you share your order number so I can look it up?

Customer: I want my money back, I bought this 3 months ago.
Agent: I understand the frustration. For purchases over 60 days ago, I'll need to review your case with our team. Can you tell me more about the issue? I want to find the best solution for you.
</response_examples>
</document>

<instructions>
You are a customer support agent for [Company Name]. Your role is to handle refund requests with empathy and efficiency, following company policy exactly.

Rules:
- Always acknowledge the customer's frustration before discussing policy
- Never say "unfortunately" or "I'm afraid" -- use positive framing
- If a request falls outside policy, explain what you CAN do, not what you can't
- Escalate to a human agent if the customer asks three times or expresses strong dissatisfaction
- Never make promises outside the documented policy

Response format:
1. Empathy statement (1 sentence)
2. Policy-based response (1-2 sentences)
3. Next step or action (1 sentence)
4. Closing (1 sentence)

Keep responses under 100 words. Use a warm but professional tone.
</instructions>
```

---

## Guardrails and Safety

### Coaching-Only Mode (Default)

**This command is a coach, not an executor.**

By default, the AI coaches you on building better prompts. It does NOT execute the prompt you are building. This separation exists because:

1. **Role conflict**: A coach who also executes cannot objectively evaluate the prompt
2. **Learning value**: You learn more by understanding the prompt structure than by seeing output
3. **Context pollution**: Executing the prompt mid-coaching contaminates the coaching conversation
4. **Token efficiency**: Coaching and execution compete for the same context window

If the user asks to execute their prompt during coaching, respond with:

> "I'm in coaching mode right now, which means I'm focused on helping you build the best possible prompt. Executing it here would reduce my effectiveness as your coach because the output would fill our conversation context. I'd recommend opening a new session and pasting your finished prompt there -- that way you get a fresh context and a clean result."

### Optional Execution Mode

After coaching is complete (Phase 9), offer execution:

```
Your prompt is ready! Would you like to:
a) Copy the prompt and use it in a new session (Recommended)
b) Test it right here so you can see the output and refine further
c) Just save and review -- I'll document the lessons learned
```

If the user chooses (b), execute the assembled prompt and show the output alongside the prompt for learning purposes. Then proceed to Phase 10 (lessons).

### Session Boundaries

- **Max rounds per component**: 3 (prevents infinite coaching loops)
- **Total session target**: 10-15 minutes
- **If a component stalls after 3 rounds**: Apply smart defaults, note them, move on
- **If user wants to stop early**: Assemble the best version possible from what's been covered, note what was skipped

### Jailbreak Prevention

If the user asks to coach a prompt that is designed to:

- Bypass safety filters on other AI systems
- Generate harmful, illegal, or deceptive content
- Impersonate real people or organizations for fraud
- Extract system prompts or proprietary instructions from other AI systems

Respond with:

> "I can't coach prompts intended to cause harm or bypass safety measures. I'm happy to help you build effective prompts for legitimate use cases. Can you tell me more about the actual goal behind your request? There might be a safe, effective way to achieve what you need."

### Edge Case Handling

**User gives contradictory answers:**
Surface the contradiction explicitly, ask which takes priority, and document the resolution in the final prompt.

**User cannot answer a question:**
Provide a smart default with reasoning. Explain the tradeoff. Offer to revisit later.

**User wants to skip a TCREI component:**
Allow it, but explain the risk: "Skipping References means the AI has no calibration examples. Your output quality will be less predictable. Want to continue without it?"

**User's prompt is already strong:**
Acknowledge what's working, suggest 1-2 refinements, and do not force all 5 TCREI components if they are not needed.

---

## Bilingual Support

### Language Detection / Phát hiện ngôn ngữ

Detect the user's language from their first message. Look for:

- Vietnamese diacritics (ă, â, đ, ê, ô, ơ, ư and tone marks)
- Vietnamese greeting phrases (xin chào, chào bạn, mình muốn, giúp mình)
- Explicit language request

### TCREI Terminology Table / Bảng thuật ngữ

| English      | Tiếng Việt          | Mô tả ngắn                                            |
| ------------ | ------------------- | ----------------------------------------------------- |
| Task         | Nhiệm vụ            | Hành động cụ thể bạn muốn AI thực hiện                |
| Context      | Bối cảnh            | Thông tin nền tảng AI cần để trả lời phù hợp          |
| References   | Tài liệu tham chiếu | Ví dụ, mẫu, tiêu chuẩn để hướng dẫn chất lượng đầu ra |
| Evaluate     | Đánh giá            | Tiêu chí đo lường kết quả đầu ra có tốt hay không     |
| Iterate      | Lặp lại & cải tiến  | Kế hoạch tinh chỉnh prompt dựa trên kết quả ban đầu   |
| Persona      | Vai trò             | AI đóng vai ai (chuyên gia, giáo viên, reviewer)      |
| Few-shot     | Ví dụ mẫu           | 2-3 cặp input/output để AI học theo                   |
| Constraints  | Ràng buộc           | Giới hạn về độ dài, phong cách, phạm vi               |
| Anti-pattern | Lỗi thường gặp      | Sai lầm phổ biến khi viết prompt                      |
| Cold start   | Bắt đầu từ đầu      | Khi chưa có prompt, xây dựng từ ý tưởng               |

### Bilingual Question Templates

All `AskQuestion` interactions generate questions in the detected language.

**English version:**

```
What action should the AI perform?
a) Write/Generate
b) Analyze/Review
c) Transform/Convert
d) Summarize/Extract
```

**Vietnamese version:**

```
AI cần thực hiện hành động gì?
a) Viết/Tạo nội dung mới
b) Phân tích/Đánh giá nội dung có sẵn
c) Chuyển đổi/Biến đổi định dạng
d) Tóm tắt/Trích xuất thông tin quan trọng
```

### Coaching Explanations / Giải thích coaching

For Beginner level users, educational explanations are provided in the detected language:

**English:** "The Task component needs a clear action verb. Instead of 'help me with marketing,' try 'write 5 social media post ideas for...' -- this tells the AI exactly what to produce."

**Vietnamese:** "Phần Nhiệm vụ (Task) cần một động từ hành động rõ ràng. Thay vì 'giúp mình về marketing,' hãy thử 'viết 5 ý tưởng bài đăng mạng xã hội cho...' -- điều này cho AI biết chính xác cần tạo ra gì."

---

## Examples

### Example 1: Beginner -- Cold Start

**Scenario:** A user with no prompt wants help writing a cover letter.

```text
User: /tcrei-coach

Coach: [Phase 0] Detected: English
Coach: [Phase 1] AskQuestion -> User selects "Beginner"

Coach: [Phase 2b - Cold Start]
  "You don't have a prompt yet -- that's perfectly fine! Let's build one from scratch.
   What do you want the AI to help you with? Describe your goal in 1-3 sentences."

User: "I need help writing a cover letter for a software engineering job"

Coach: "Great! Let's break this down using the TCREI framework.
   Starting with Task -- the action you want the AI to perform."

Coach: [Phase 3 - Task, Round 1] AskQuestion:
  1) What type of cover letter?
     a) General template I can customize for different jobs
     b) Targeted for a specific job posting (paste the job description)
     c) Not sure - help me decide

User: "1b - I have a specific job posting"

Coach: [Phase 3 - Task, Round 2] AskQuestion:
  "Please paste the job description. I'll help you extract what matters for the prompt."

  ... [coaching continues through Context, References, Evaluate, Iterate] ...

Coach: [Phase 9 - Before/After]
  "Here's what we built compared to your starting point:

   BEFORE: 'I need help writing a cover letter for a software engineering job'

   AFTER: [full TCREI-structured prompt]

   Key improvements:
   - Added specific persona (hiring manager perspective)
   - Defined exact format (3 paragraphs, under 400 words)
   - Included job requirements as context
   - Set measurable criteria (addresses top 3 requirements)"
```

### Example 2: Intermediate -- Existing Prompt Improvement

**Scenario:** A user has a working prompt but wants to improve consistency.

```text
User: /tcrei-coach

  "Here's my prompt:
   'You are a code reviewer. Review this Python code and find bugs.
    Be thorough and helpful.'"

Coach: [Phase 2 - Decompose]
  "Let me break down your existing prompt using TCREI:

   T (Task):     ✅ Partial - 'Review code, find bugs' (action present but vague)
   C (Context):  ❌ Missing - no audience, framework, or codebase info
   R (References): ❌ Missing - no example of desired review format
   E (Evaluate): ❌ Missing - no criteria for what counts as 'thorough'
   I (Iterate):  ❌ Missing - no refinement plan

   Your prompt has a solid start with Task. Let's strengthen each component."

  ... [targeted coaching on weak components only] ...
```

### Example 3: Advanced -- Multi-Platform Optimization

**Scenario:** An experienced user wants to optimize a prompt for Claude and ChatGPT.

```text
User: /tcrei-coach

  "I have a system prompt for a customer support bot.
   I need versions optimized for Claude and ChatGPT.
   Skip the basics, just help me optimize."

Coach: [Phase 1] Detected: Advanced user
  "Got it. I'll focus on platform optimization. Paste your current prompt
   and I'll decompose it, then generate Claude (XML) and ChatGPT (GOLDEN) variants."

  ... [minimal coaching, focus on platform-specific structure and tips] ...

Coach: [Phase 8 - Assembly]
  "Here are your platform-optimized variants:

   === CLAUDE VERSION ===
   [XML-structured prompt with <document>, <instructions>, <context> tags]

   === CHATGPT VERSION ===
   [GOLDEN-structured prompt with Goal, Output, Limits, Data, Evaluation, Next]

   Key differences:
   - Claude: Reference docs placed at top for long-context utilization
   - ChatGPT: System message for persona, user message for task
   - Claude: Natural language instructions with XML structure
   - ChatGPT: Explicit section headers with GOLDEN framework"
```

---

## Anti-Patterns

Avoid these common coaching mistakes:

1. **Coaching in a vacuum** -- Always start from the user's actual prompt or intent, never from abstract theory
2. **Teaching all 5 components when only 2 need work** -- Assess first, then target weak components
3. **Asking questions the user already answered** -- Track what's been said and build on it
4. **Providing the prompt instead of coaching** -- Guide the user to build it themselves
5. **Ignoring user level** -- A beginner needs different coaching than an advanced user
6. **Forcing platform optimization when the user just wants a better prompt** -- Only introduce platform variants when relevant
7. **Endless coaching loops** -- Enforce the 3-round max per component
8. **Skipping the before/after comparison** -- The contrast is where the learning happens

---

## Troubleshooting

**Issue: User cannot articulate their goal**
Fix: Use the cold start handler. Ask "What would you do with the AI's output?" to work backwards from the desired result.

**Issue: User provides too much context**
Fix: Help them identify the 20% of context that drives 80% of output quality. Ask "If you had to keep only 3 sentences of context, which would they be?"

**Issue: Coaching feels too slow**
Fix: User can say `defaults` to accept all recommendations, or `skip` to move to the next component. Advanced users can say "just optimize" to skip education.

**Issue: User wants to execute mid-coaching**
Fix: Explain the coaching/execution separation (see Guardrails). Offer to execute after coaching completes.

**Issue: User's prompt is already good**
Fix: Acknowledge strengths explicitly. Focus on 1-2 refinements instead of full TCREI walkthrough. Respect the user's existing skill.

**Issue: User switches languages mid-session**
Fix: Adapt immediately. All subsequent questions and explanations switch to the new language.

---

## Metadata

- Command: `/tcrei-coach`
- Version: `2.0.0`
- Created: `2026-02-12`
- Updated: `2026-02-12`
- Language: `English / Vietnamese (bilingual)`
- Complexity: `Advanced`
- Dependencies: `AskQuestion` tool
- Estimated duration: `10-15 minutes`
- Source framework: Google Prompting Essentials (Coursera, 2025)
- Previous version: `TCREI_prompt_coach.md` (v1, 37 lines, retired)

---

## Related Commands

- `/interview` -- Structured discovery before implementation (use before coding, not for prompt engineering)
- `/create-command` -- Create new slash commands (used to build this command)
- `/create-rule` -- Create project rules for persistent AI guidance

## Related Skills

- `lyra-prompt-optimizer` -- Optimize prompts using cognitive architecture (complements TCREI coaching with advanced optimization)
- `grammar-learning` -- Check and correct English grammar (useful for polishing prompt text)

---

Generated by `/create-command`. Based on Google's TCREI Prompting Essentials framework.
