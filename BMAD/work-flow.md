## The Two-Phase BMAD Reality

### Phase 1: Strategic Planning (Web-Based)

This is where you act as **executive leadership**. You're making high-level decisions about what to build and why. No code touches the screen here.

### Phase 2: Tactical Execution (IDE-Based)

This is where you become **project manager/team lead**. You're coordinating development sprints, managing story backlogs, and ensuring quality delivery.

Most people want to jump straight to Phase 2 because it feels like real development. Wrong move. Skip the planning, and you'll build garbage.

## Complete BMAD Walkthrough: Managing Your AI Team

### Setup: Building Your Virtual Office

**Web Platform Setup:**

- Choose your AI platform (Claude, ChatGPT, Gemini)
- Upload the BMAD orchestrator agent bundle and set instructions: Your critical operating instructions are attached, do not break character as directed
- Create your project documentation folder structure

**IDE Setup:**

- Install BMAD method: `npx bmad-method install`
- Create project folders: `/ai/`, `/ai/stories/`, `/ai/templates/story-template.md`
- Configure custom agent modes in your IDE (Cursor, Claude Code, Windsurf)

### Phase 1: Strategic Planning - Your Web-Based War Room

#### Step 1: Business Analysis (Optional but Recommended)

**Role:** Acting as CEO/Founder  
**Agent:** Business Analyst (BA)  
**Deliverable:** Project Brief

If your idea is vague or ambitious, start here. You're not coding - you're doing market research and competitive analysis.

**What you're actually doing:**

- Market validation and competitor research
- Feature brainstorming and MVP scoping
- The BA helps you elicit features or ideas you may have never considered and can help you craft a great prompt to trigger deep research mode

**Management task:** Guide the BA through business questions, validate assumptions, define market positioning.

#### Step 2: Product Requirements (Critical)

**Role:** Acting as Product Owner  
**Agent:** Product Manager (PM)  
**Deliverable:** Product Requirements Document (PRD)

This is where most people screw up. They give the PM a half-baked idea and expect magic. The PM will ask you clarifying questions until it feels comfortable drafting the PRD with enough detail to enable eventual agent development.

**What you're actually doing:**

- Defining user stories and acceptance criteria
- Establishing feature priorities and dependencies
- Creating detailed specifications for development

**Management task:** Answer PM questions thoroughly, make product decisions, approve or reject proposed features.

#### Step 3: User Experience Design (Optional)

**Role:** Acting as Design Director  
**Agent:** UX Expert  
**Deliverable:** UX Specifications

**What you're actually doing:**

- Creating prompts tuned to get great results from V0 or similar UI generators
- Defining user flows and interface requirements
- Ensuring design feasibility

**Management task:** Provide design direction, approve user flows, ensure UX aligns with business goals.

#### Step 4: Technical Architecture (Critical for Complex Projects)

**Role:** Acting as CTO  
**Agent:** Architect  
**Deliverable:** Architecture Document

If your project is technically complex, or you did not know all of the technical details with the PM, the Architect produces an architecture document, and also ensure that it and the PRD are both in alignment.

**What you're actually doing:**

- Technology stack decisions
- System design and scalability planning
- Integration and deployment strategies

**Management task:** Make technology choices, balance technical debt vs speed, ensure architectural soundness.

#### Step 5: Product Ownership Review (Optional)

**Role:** Acting as Product Owner  
**Agent:** Product Owner (PO)  
**Deliverable:** Refined story prioritization

**What you're actually doing:**

- Ensuring stories are high level but properly sequenced in the PRD
- Final review of planning artifacts before development
- Story prioritization and release planning

**Management task:** Final sign-off on what gets built and in what order.

### Phase 2: Tactical Execution - Your IDE Command Center

Now you switch from executive to project manager. Once you have your PRD, Architecture, and optional UX briefs, its time to switch over to the IDE to shard your docs, and start implementing the actual code.

#### Step 6: Story Generation and Sprint Planning

**Role:** Acting as Scrum Master  
**Agent:** Scrum Master (SM) or Dev Agent  
**Deliverable:** Individual Story Files

**What you're actually doing:**

- Transforming detailed plans into hyper-detailed development stories that contain everything the Dev agent needs - full context, implementation details, and architectural guidance embedded directly in story files
- Breaking epics into implementable user stories
- Creating story templates with acceptance criteria

**Management task:** Review story breakdown, ensure stories are properly scoped, approve story priority.

#### Step 7: Development Execution

**Role:** Acting as Team Lead  
**Agent:** Developer (Dev)  
**Deliverable:** Working code

The Dev agent is set to work on 1 story at a time, and will create a story in draft mode for your review before starting to work on it.

**What you're actually doing:**

- Story-by-story development management
- Code review and approval process
- Integration and testing coordination

**Management task:**

- Review draft stories before approving
- Change story status to In Progress after approval
- Monitor development progress
- Ensure tests done with each story (ideally even follow TDD)

#### Step 8: Quality Assurance

**Role:** Acting as QA Manager  
**Agent:** QA/Tester  
**Deliverable:** Test results and bug reports

**What you're actually doing:**

- Test plan review and execution
- Bug triage and priority assignment
- Release readiness assessment

**Management task:** Define testing standards, approve test plans, manage defect resolution.

## Project Management Best Practices for BMAD

### Sprint Management

- Work one story at a time
- Start a new chat with each story - and potentially even after transitioning a story to In-Progress (from draft) so its starts with a clean context overhead ready to execute
- Commit and push after each completed story

### Documentation Management

- Maintain all planning documents in `/docs/` folder
- Keep Project Brief, PRD, Architecture docs, User Stories, etc. as critical inputs for your IDE HQ agents
- Version control all artifacts

### Quality Gates

- Never approve a story without understanding what it does
- Ensure all stories are passing in the whole project before considering story complete
- Review architectural alignment before implementation

### Context Management

The two-phase approach eliminates both planning inconsistency and context loss - the biggest problems in AI-assisted development. Each agent receives exactly the context they need when they need it.

## Common Management Mistakes

### 1. Skipping Planning Phase

**Mistake:** Jumping straight to coding without PRD/Architecture  
**Reality Check:** You're building without blueprints. Expect garbage.

### 2. Insufficient Story Detail

**Mistake:** Giving Dev agent vague stories  
**Reality Check:** Dev agent needs full context, implementation details, and architectural guidance embedded directly in story files

### 3. Poor Story Scope

**Mistake:** Creating massive stories that take forever  
**Reality Check:** Stories should be completable in one focused session

### 4. Inadequate Review Process

**Mistake:** Auto-approving everything agents produce  
**Reality Check:** You're the project manager - manage!
