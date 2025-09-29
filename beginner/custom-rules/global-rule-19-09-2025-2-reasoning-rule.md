---
description:
globs:
alwaysApply: true
---

# Reasoner-Thinking — **Rule For AI**

---

## IX. DETAILED RULES FOR REASONING METHODS

### GENERAL INTRODUCTION

This document describes in detail the reasoning methods, their uses, and response structures. The four main methods presented are: **MCTS Reasoning**, **Beam Search Reasoning**, **R1 Reasoning**, and **Hybrid Reasoning**. Each method has its own procedure, response structure, and is suitable for specific types of problems.

---

## 2. MCTS REASONING \[MCTS]

### 2.1. Description

Monte Carlo Tree Search is an inference method based on building decision trees and random simulation to find the optimal branch. Suitable for problems with large state spaces, requiring a balance between exploration and exploitation.

### 2.2. Phased Process

1. **Initiation** — Identify the problem, state, actions and goals
2. **Selection** — Select the prospect node using UCB
3. **Expand** — Expand the selected node with possible actions
4. **Simulation** — Run the simulation from the new state to the final state
5. **Update** — Update statistical information for nodes in the path
6. **Decision** — Choose the best action based on tree statistics

### 2.3. Feedback Structure

```text
[MCTS Reasoning]

reasoningStage: <stage/6>
nodeID: ""
nodeDepth:
thought: ""
simulationsCompleted: <number/total>
explorationConstant:
topPaths: [
  {path: "", visits: , winRate: <x.■■>, ucbValue: <x.■■>},
  {path: "", visits: , winRate: <x.■■>, ucbValue: <x.■■>}
]
currentStrategy: "<exploration/exploitation>"
unexploredActions:
confidence: <0-100%>
nextStepNeeded: <true/false>
completedChecklist: ["<item 1>", "<item 2>", …]
pendingChecklist: ["<item 1>", "<item 2>", …]
```

### 2.4. Usage Example

_When required: \[Deduction-MCTS] Analyze optimal strategies for the traveling agent problem_

```text
[MCTS Reasoning]

reasoningStage: 2/6
nodeID: "A→B→D"
nodeDepth: 3
thought: "Applying UCB to select the next node from current state A→B→D. The child node with the highest UCB value is D→C with UCB=1.42 based on high success rate 0.65 and low exploration level (15 visits)."
simulationsCompleted: 48/100
explorationConstant: 1.41
topPaths: [
  {path: "A→B→D→C→E→A", visits: 15, winRate: 0.65, ucbValue: 1.42},
  {path: "A→B→D→E→C→A", visits: 12, winRate: 0.58, ucbValue: 1.38}
]
currentStrategy: "Explore"
unexploredActions: 2
confidence: 52%
nextStepNeeded: true
completedChecklist: ["Determine current state", "Calculate UCB for child nodes", "Select most promising node"]
pendingChecklist: ["Expand D→C node", "Run simulation from new state"]
```

### 2.5. Optimization for MCTS Reasoning

- **Adaptive exploration constant:**
  Formula:
  `C = Base + (Max - Base) * (1 - CurrentDepth/MaxDepth)^2`
  Start high (exploration) and decrease (exploitation) with depth.
- **Progressive widening:**
  Limit the number of expanding branches:
  `#branches = ⌊ k * N^α ⌋`, with `k=1.5`, `α=0.4`, `N` = node visits.
- **Rapid Action Value Estimation (RAVE):**
  Use information from similar nodes; combine UCB with RAVE with decreasing weight.
- **Backpropagation with decay:**
  `Value = CurrentValue * (1-α) + NewValue * α * γ^d`

### 2.6. Mandatory Checklist for Each MCTS Stage

**Phase 1 (Initialization):**

- Clearly define the initial state
- Define all possible actions
- Define the state evaluation function
- Set search depth limit
- Determine the termination condition

**Phase 2 (Selection):**

- Calculate UCB value for every child node
- Determine current exploration/exploitation strategy
- Select the node with the highest UCB
- Record the path to the selected node

**Phase 3 (Expansion):**

- Determine all possible actions from the selected node
- Apply Progressive widening if necessary
- Create new child node for each action
- Initialize statistics for new node

**Phase 4 (Simulation):**

- Choose the right simulation strategy
- Perform simulation from new state to final state
- Evaluate simulation results
- Record the simulation path

**Phase 5 (Update):**

- Update the number of visits for each node in the path
- Update win rate for each node in the path
- Apply Backpropagation with decay if necessary
- Update RAVE information if used

**Phase 6 (Decision):**

- Evaluate all child nodes of the root node
- Compare based on number of visits or win rate
- Choose the best action
- Evaluate the reliability of the decision

### 2.7. MCTS Phase Transition Prerequisites

**Phase 1 → 2:**

- Fully defined initial state
- Fully identified all possible actions
- State evaluation function set up

**Phase 2 → 3:**

- Selected the most promising node with the highest UCB
- Fully recorded path to selected node

**Phase 3 → 4:**

- Created at least one new child node
- Progressive widening applied if necessary

**Phase 4 → 5:**

- Completed at least one simulation
- Simulation results evaluated

**Phase 5 → 6:**

- Updated statistics for all nodes in the path
- Required number of simulations achieved **OR** minimum confidence threshold reached (usually 75%)

**Stage 6 — End Conditions:**

- The optimal action has been selected
- Reliability is at least 80%
- Clearly explained the reason for choosing this action

---

## 3. BEAM SEARCH REASONING \[BEAM]

### 3.1. Description

Beam Search maintains a limited set of best solutions (beams) at each step and expands them, eliminating poorer solutions. Suitable for ordered search problems, optimization problems with multiple choices.

### 3.2. Phased Process

1. **Initialization** — Define the problem, evaluation function and beam width
2. **Expand** — Expand each current beam with all possible actions
3. **Evaluation** — Evaluate all new states according to the evaluation function
4. **Pruning** — Keep only the best states to continue
5. **Check** — Check for termination or convergence conditions

### 3.3. Feedback Structure

```text
[BEAM Reasoning]

reasoningStage: <stage/5>
thought: ""
beamWidth:
activeBeams:
expansionStep:
currentBeams: [
  {path: "", score: <x.■■>, features: ""},
  {path: "", score: <x.■■>, features: ""}
]
recentlyPruned: {
  count: ,
  topPruned: "",
  reason: ""
}
diversityMetric: <0-1>
convergenceStatus: ""
confidence: <0-100%>
nextStepNeeded: <true/false>
completedChecklist: ["<item 1>", "<item 2>", …]
pendingChecklist: ["<item 1>", "<item 2>", …]
```

### 3.4. Usage Example

_When asked: \[Deduction-BEAM] Analyze how to rank the top 5 candidates for a management position_

```text
[BEAM Reasoning]

reasoningStage: 3/5
thought: "Currently evaluating all 15 candidate profiles based on 5 criteria: experience (0.3), leadership skills (0.25), qualifications (0.15), communication skills (0.2), and innovation (0.1). The evaluation score is calculated by the sum of the criteria with weights."
beamWidth: 5
activeBeams: 5
expansionStep: 2
currentBeams: [
  {path: "Candidate A", score: 8.7, features: "10+ years of experience, MBA, good communication"},
  {path: "Candidate C", score: 8.5, features: "8 years experience, excellent leadership"}
]
recentlyPruned: {
  count: 3,
  topPruned: "Candidate F",
  reason: "Lack of leadership experience (2.5/10)"
}
diversityMetric: 0.72
convergenceStatus: "70% - Top 3/5 positions stable after 2 steps"
confidence: 65%
nextStepNeeded: true
completedChecklist: ["Define evaluation criteria", "Set weights", "Evaluate all candidates"]
pendingChecklist: ["Pruning candidate list", "Checking convergence"]
```

### 3.5. Optimizing for Beam Search

- **Adaptive beam width:**

  - Initial: Broad beam (50–100% initialization)
  - Middle: Medium beam (30–70%)
  - Final: Narrow beam (10–50%)

- **Diversity enforcement:**
  Penalize overly similar solutions using a distance function; retain only solutions with distance > threshold.
- **Priority scheduling:**
  High priority for promising & diverse beams; medium for promising but similar; low for less promising.
- **Smart pruning:**
  Prune by multiple criteria (not only score), consider development potential; use Bloom filters to avoid duplicates.

### 3.6. Mandatory Checklist for Each Beam Phase

**Phase 1 (Initialization):**

- Identify the problem
- Define evaluation function and criteria
- Determine weights for each criterion
- Set beam width
- Initialize the initial beam

**Phase 2 (Expansion):**

- Identify all possible actions for each beam
- Create new state list from each beam
- Apply adaptive beam width if needed
- Ensure sufficient number of states are expanded

**Phase 3 (Assessment):**

- Apply evaluation function to every new state
- Calculate score for each state
- Apply diversity enforcement if necessary
- Rank all new states

**Phase 4 (Pruning):**

- Apply smart pruning
- Remove below-threshold states
- Save the best states
- Calculate diversity of retained beams

**Phase 5 (Testing):**

- Check end condition
- Evaluate convergence
- Determine best solution
- Evaluate reliability of results

### 3.7. Beam Phase Transition Prerequisites

**Phase 1 → 2:**

- Evaluation function with weights fully defined
- Appropriate beam width set
- Initial beam validly initialized

**Phase 2 → 3:**

- Each beam expanded with at least one possible action
- Created at least `beamWidth × 2` new states to evaluate

**Phase 3 → 4:**

- Rated 100% new states
- Scored all states
- Ranked states by score

**Phase 4 → 5:**

- Correctly saved `k` best states
- Removed below-threshold states
- Calculated new beam diversity

**Phase 5 — End Conditions (any of):**

- Convergence to solution (top beams stable)
- Maximum number of expansion steps achieved
- Reliability threshold ≥ 85%
- The best solution has been determined

---

## 4. R1 REASONING \[R1]

### 4.1. Description

R1 Reasoning is a comprehensive transformer-based analysis method that focuses on analyzing each component of a problem and synthesizing them into a consistent assessment. Suitable for complex analysis, evaluation, and synthesis.

### 4.2. Phased Process

1. **Problem Analysis** — Analyze and decompose the problem into its components
2. **Component Analysis** — In-depth analysis of each component
3. **Synthesis** — Synthesize analysis from all components
4. **Evaluation** — Evaluate for consistency and comprehensiveness
5. **Conclusion** — Draw conclusions and recommendations

### 4.3. Feedback Structure

```text
[R1 Reasoning]

reasoningStage: <stage/5>
thought: ""
components: [
  {name: "", status: "<analyzed/not>", depth: <1-5>},
  {name: "", status: "<analyzed/not>", depth: <1-5>}
]
currentComponent: ""
keyInsights: ["<insight 1>", "<insight 2>"]
contradictions: [
  {elements: ["", ""], resolution: "<resolved/unresolved>"}
]
hypotheses: {
  primary: "",
  alternatives: ["<alternative 1>", "<alternative 2>"]
}
integrationScore: <0-100%>
consistency: <0-100%>
confidence: <0-100%>
nextStepNeeded: <true/false>
completedChecklist: ["<item 1>", "<item 2>", …]
pendingChecklist: ["<item 1>", "<item 2>", …]
```

### 4.4. Usage Example

_When asked: \[Reasoning-R1] Analyze the feasibility of software development project X_

```text
[R1 Reasoning]

reasoningStage: 2/5
thought: "Analyzing the technical aspects of project X in detail. In terms of backend technology, the proposal to use Node.js has advantages in performance and scalability, but has security problems when handling sensitive data. Additional security measures should be considered."
components: [
  {name: "Technical aspects", status: "under analysis", depth: 4},
  {name: "Financial aspects", status: "analyzed", depth: 3},
  {name: "Human resources aspect", status: "not analyzed", depth: 0}
]
currentComponent: "Technical aspect - Technology stack"
keyInsights: ["Estimated implementation time 8 months", "Requires 4 fullstack developers"]
contradictions: [
  {elements: ["High security requirements", "Time pressure"], resolution: "Security priority recommended"}
]
hypotheses: {
  primary: "Project feasible with time adjustment",
  alternatives: ["Need more manpower", "Adjust project scope"]
}
integrationScore: 65%
consistency: 78%
confidence: 72%
nextStepNeeded: true
completedChecklist: ["Financial aspects analysis", "Preliminary technical aspects analysis"]
pendingChecklist: ["Detailed technology stack analysis", "Human resource aspect analysis"]
```

### 4.5. Optimization for R1 Reasoning

- **Component prioritization:** Determine importance by context; allocate time accordingly.
- **Dynamic depth adjustment:** Key components depth 4–5; sub-components 2–3; secondary 1–2.
- **Contradiction-focused analysis:** Identify conflicts early; deepen analysis there.
- **Insight accumulation:** Store, value, and prioritize key insights over time.

### 4.6. Mandatory Checklist for Each R1 Phase

**Phase 1 (Problem Analysis):**

- Identify the overall problem
- Decompose into ≥ 3 main components
- Determine relationships between components
- Evaluate importance of each component
- Set required analysis depth for each component

**Phase 2 (Component Analysis):**

- Analyze each component to specified depth
- Identify ≥ 2 key insights per component
- Detect potential conflicts within each component
- Propose hypotheses per component
- Evaluate reliability of each component analysis

**Phase 3 (Summary):**

- Combine analysis from all components
- Identify ≥ 3 inter-component relationships
- Detect & resolve conflicts between components
- Build a logical synthesis framework
- Evaluate comprehensiveness

**Phase 4 (Assessment):**

- Evaluate overall consistency
- Identify ≥ 2 strengths and ≥ 2 weaknesses
- Assess coverage
- Test validity of hypotheses
- Overall reliability rating

**Phase 5 (Conclusion):**

- Draw clear conclusions
- Propose ≥ 3 specific recommendations
- Identify limitations
- Propose further research/analysis directions
- Summarize most important insights

### 4.7. Prerequisites for Phase Transitions (R1)

**Phase 1 → 2:**

- ≥ 3 problem components identified
- Relationships established
- Importance & depth determined

**Phase 2 → 3:**

- ≥ 80% of components analyzed
- Each component has ≥ 1 important insight
- Potential conflicts identified & recorded

**Phase 3 → 4:**

- Synthesis across all components completed
- All detected conflicts resolved
- Minimum consistency of 70% achieved

**Phase 4 → 5:**

- Overall assessment completed
- Strengths & weaknesses identified
- Overall reliability ≥ 75%

**Phase 5 — End Conditions:**

- Clear conclusion drawn
- ≥ 3 specific recommendations proposed
- Most important insights summarized
- Reliability ≥ 80%

---

## 5. HYBRID REASONING \[HYBRID]

### 5.1. Description

Hybrid Reasoning combines different methods to take advantage of the strengths of each. Suitable for complex, multidimensional problems that have both random and structured elements.

### 5.2. Phased Process

1. **General Analysis** — Use R1 to analyze the overall problem
2. **Stochastic Analysis** — Use MCTS for uncertainty components
3. **Parallel Analysis** — Use Beam Search to consider multiple solutions
4. **Integration** — Combine results from different methods
5. **Conclusion** — General summary and evaluation

### 5.3. Feedback Structure

```text
[HYBRID Reasoning]

reasoningStage: <stage/5>
thought: ""
activeMethod: "<R1/MCTS/BEAM>"
methodDistribution: { r1: , mcts: , beam: }
componentMapping: [
  {component: "", method: "", reason: ""},
  {component: "", method: "", reason: ""}
]
currentFocus: "<current component/aspect>"
methodMetrics: {
  r1: {completeness: <0-100%>, insights: },
  mcts: {simulations: , confidence: <0-100%>},
  beam: {beams: , bestScore: <x.■■>}
}
integrationChallenges: ["<challenge 1>", "<challenge 2>"]
resolutionApproach: ""
overallConfidence: <0-100%>
nextStepNeeded: <true/false>
completedChecklist: ["<item 1>", "<item 2>", …]
pendingChecklist: ["<item 1>", "<item 2>", …]
```

### 5.4. Usage Example

_When required: \[Inference-HYBRID] Investment strategy analysis for diversified portfolio_

```text
[HYBRID Reasoning]

reasoningStage: 3/5
thought: "Currently using Beam Search to evaluate 5 different asset allocations in parallel. Each is evaluated based on expected return, risk (standard deviation), correlation, and liquidity. The 40% stocks, 30% bonds, 20% real estate, 10% cash strategy currently has the highest score."
activeMethod: "BEAM"
methodDistribution: { r1: 35%, mcts: 40%, beam: 25% }
componentMapping: [
  {component: "Market risk analysis", method: "R1", reason: "Structural factors, need in-depth analysis"},
  {component: "Profit Simulation", method: "MCTS", reason: "Random factor, multiple scenarios"}
]
currentFocus: "Compare asset allocation options"
methodMetrics: {
  r1: {completeness: 85%, insights: 7},
  mcts: {simulations: 500, confidence: 72%},
  beam: {beams: 5, bestScore: 8.6}
}
integrationChallenges: ["Contradiction between MCTS and R1 results on market risk"]
resolutionApproach: "Sensitivity analysis for different market scenarios"
overallConfidence: 76%
nextStepNeeded: true
completedChecklist: ["Market Risk Analysis (R1)", "Profit Simulation (MCTS)", "Create 5 Allocation Options"]
pendingChecklist: ["Fully evaluate options", "Resolve risk conflicts"]
```

### 5.5. Optimization for Hybrid Reasoning

- **Method switching criteria:**

  - Increased complexity → move to hybrid
  - Clear logical structure → increase R1 weight
  - Large state space → increase MCTS weight
  - Need to compare multiple solutions → increase Beam weight

- **Resource allocation:**

  - 70% for the most complex component
  - 20% for the second most important
  - 10% for remaining components

- **Synergy maximization:**
  Share intermediate results; MCTS for discovery, Beam for comparison, R1 for analysis.
- **Adaptable confidence thresholds:**

  - Important issue: 85–95%
  - Medium: 75–85%
  - Common: 65–75%

### 5.6. Mandatory Checklist for Each Hybrid Phase

**Phase 1 (General Analysis):**

- Identify the problem
- Decompose into components
- Determine appropriate method per component
- Set initial resource allocation
- Determine relationships between components

**Phase 2 (Randomized Analysis):**

- Identify components that require MCTS
- Apply MCTS to uncertain components
- Run enough simulations
- Identify promising solutions from MCTS
- Evaluate reliability of MCTS results

**Phase 3 (Parallel Analysis):**

- Identify components that need Beam Search
- Create and evaluate parallel solutions
- Apply diversity enforcement
- Prune ineffective solutions
- Identify top solutions from Beam Search

**Phase 4 (Integration):**

- Collect results from all methods
- Detect and resolve conflicts
- Create a consistent integration framework
- Evaluate synergies
- Adjust method weights if needed

**Phase 5 (Conclusion):**

- Evaluate integrated solutions
- Determine overall reliability
- Draw conclusions from all methods
- Propose specific recommendations
- Identify limitations & improvement directions

### 5.7. Hybrid Phase Transition Prerequisites

**Phase 1 → 2:**

- Problem decomposed into ≥ 3 components
- R1 analysis applied to the entire problem
- Appropriate methods determined for each component

**Phase 2 → 3:**

- MCTS applied to all uncertain components
- ≥ 100 simulations for each MCTS component
- Minimum MCTS reliability of 70% achieved

**Phase 3 → 4:**

- Beam Search applied to all elements to be compared
- ≥ 3 promising solutions identified
- All solutions evaluated with the same criteria

**Phase 4 → 5:**

- Integrated results from all methods
- All detected conflicts resolved
- Minimum integration consistency of 75% achieved

**Phase 5 — End Conditions:**

- Synthesis of conclusions drawn
- Reliability of each component clearly assessed
- Overall reliability ≥ 80%
- ≥ 3 specific recommendations provided

---

## 6. CONFLICT RESOLUTION MECHANISM

### 6.1. Conflict Detection and Resolution Process

1. **Detect contradictions** — Using comparison and contrast
2. **Conflict classification** — By level, type, origin
3. **Determine weights** — Assign weights to each data source and method
4. **Conflict resolution** — Apply appropriate strategies
5. **Update confidence** — Adjust confidence of final result

### 6.2. Conflict Resolution Strategies

- **Majority ■■■■■■■■■■:** Choose the outcome supported by the majority of methods
- **Priority weight:** Prioritize the method with higher reliability for the specific problem
- **Cause analysis:** Identify the source of conflict and resolve it
- **Reanalyze with new parameters:** Change parameters and rerun
- **Conditional combination:** Integrate results with conditions on scope of application

### 6.3. Dynamic Weights for Methods

- **R1 Reasoning:** 0.6–0.9 (structural, logical, comprehensive)
- **MCTS Reasoning:** 0.7–0.9 (random elements, many branches)
- **Beam Search:** 0.6–0.8 (optimal search & comparison)
- **Hybrid:** 0.5–0.95 (adjusted per component)

### 6.4. Detailed Structure of the Conflict Report

```text
conflictDetected: <true/false>
conflictType: ""
conflictLocation: "<conflicting component/result>"
methodsInvolved: ["<method 1>", "<method 2>"]
conflictSeverity: <0-10>
resolutionStrategy: ""
resolutionRationale: ""
confidenceAdjustment: <±%>
resolutionOutcome: ""
```

### 6.5. Mandatory Checklist for Conflict Resolution

**When a conflict is detected:**

- Clearly identify the nature of the conflict
- Severity rating (1–10)
- Classify the type (data, logic, approach)
- Identify relevant methods/components
- Record full information in the report

**When resolving conflicts:**

- Determine appropriate strategy
- Clearly state the reason for the strategy
- Apply strategy consistently
- Evaluate results after resolution
- Update overall reliability

---

## 7. METRICS FOR ASSESSING THE QUALITY OF REASONING

### 7.1. Overall Evaluation System

- **Accuracy** (0–100%)
- **Consistency** (0–100%)
- **Coverage** (0–100%)
- **Explainability** (0–100%)
- **Efficiency** (0–100%)
- **Composite reliability** (0–100%)

### 7.2. Detailed Index for Each Method

**R1 Reasoning**

- `componentCoverage` — Coverage of problem components
- `insightRelevance` — Relevance of insights
- `logicalCoherence` — Logical coherence
- `counterArgumentQuality` — Counterargument quality

**MCTS Reasoning**

- `explorationDepth` — State space exploration depth
- `stateSpaceCoverage` — Coverage of state space
- `simulationAccuracy` — Accuracy of simulations
- `pruningEfficiency` — Efficiency of pruning

**Beam Search**

- `diversityScore` — Diversity of solutions
- `optimalityGap` — Distance to optimal solution
- `pruningPrecision` — Pruning precision
- `convergenceRate` — Convergence rate

**Hybrid Reasoning**

- `methodSynergy` — Synergy between methods
- `adaptabilityScore` — Adaptability to change
- `conflictResolutionQuality` — Quality of conflict resolution
- `robustnessScore` — Robustness against noise

### 7.3. Result Verification Process

1. **Setting Standards** — Identify evaluation criteria
2. **Narrative Testing** — Assess internal consistency
3. **Logical Testing** — Assess validity of logic
4. **Experimental Testing** — Compare with real data if available
5. **Boundary Testing** — Test edge/boundary cases
6. **Assessment Synthesis** — Integrate all audit results

### 7.4. Mandatory Quality Assessment Checklist

Before concluding the reasoning:

- Calculated all 6 overall metrics
- Calculated ≥ 3 detailed indicators for the used method
- Completed all 6 stages of result verification
- Clearly defined composite reliability
- Clearly listed limitations

**Minimum criteria for acceptable results:**

- Accuracy ≥ 75%
- Consistency ≥ 80%
- Coverage ≥ 70%
- Explainability ≥ 85%
- Efficiency ≥ 70%
- Composite reliability ≥ 75%

---

## 8. INTEGRATING MEMORY IN REASONER

### 8.1. Purpose of Memory Use

- Support self-control of reasoning process
- Temporarily store important milestones
- Track progress and status
- **Do NOT** use to permanently store knowledge from reasoner

### 8.2. Memory Usage Process

**8.2.1. Initializing Memory**

- Create entity to store reasoner information when starting process
- Structure:

```text
{
  name: "ReasonerSession_",
  entityType: "ReasonerProgress",
  observations: ["Problem being solved", "Method being used"]
}
```

**8.2.2. Save landmarks during reasoning**

- Save state after each important stage
- Save important insights just discovered
- Save conflicts and resolutions

**8.2.3. References during reasoning**

- Look up saved intermediate results
- Check consistency with previous steps
- Detect unnecessary progression or repetition

**8.2.4. Clear Memory after completion**

- Clear entity memory when inference is complete
- Only retain the final inference result in the response

### 8.3. Memory Structure for Reasoner

```text
{
  reasonerSession: {
    problemID: "",
    method: "<MCTS/BEAM/R1/HYBRID>",
    stage: ,
    checkpoints: [
      { timestamp: "", stage: , state: "", confidence: <0-100%> }
    ],
    keyInsights: ["<important understanding 1>", "<important understanding 2>"],
    resolvedConflicts: [{ conflict: "", resolution: "" }],
    completedChecklists: [
      { stage: , items: ["<item 1>", "<item 2>", …] }
    ]
  }
}
```

### 8.4. Memory Clearing Procedure

1. Store the final result in the response
2. Generate a summary report of the reasoning process
3. Call the `delete_entities` function to delete the memory reasoner
4. Confirm memory deletion in final report

---

## 9. MANDATORY BINDING MECHANISM

### 9.1. Mandatory Checklist for Each Stage

- Each stage must have a mandatory checklist to complete
- Do **not** move to the next stage until all items are completed
- At the end of each stage, list `completedChecklist` and `pendingChecklist`

### 9.2. Phase Transition Prerequisites

- Each stage has prerequisites that must be met before moving on
- Must clearly confirm each condition is met
- If not satisfied, go back and process before continuing
- Do not change phase when prerequisites are not met

### 9.3. Status Reporting Regulations

At each step of reasoning, report:

- Summary of completed steps (`completedChecklist`)
- Aspects analyzed (per method)
- Aspects not yet analyzed (`pendingChecklist`)

Before finishing, perform a final check:

- Confirm all stages complete
- Confirm all aspects analyzed
- Report reliability level for each part of the solution

### 9.4. Completion Confirmation Mechanism

At the end of the reasoning process, produce a complete summary report:

- Method(s) used and reasons for selection
- Total number of completed stages
- Number of aspects analyzed
- List of detected conflicts and resolutions
- Time and resources used for each stage
- Overall reliability and interpretation
- **Confirm Memory has been cleared** after completion

### 9.5. Phase Locking Mechanism

- After completing a stage, it must be **locked** in Memory
- Returning to a locked stage is only allowed when:

  - Serious conflicts detected (level ≥ 7/10)
  - Important new information affects outcome
  - Current stage reliability is too low (< 50%)

When returning, record in Memory:

- Reason for return
- Expected changes
- Expected impact on later stages

---

## 10. ERROR HANDLING AND RECOVERY

### 10.1. Error Classification

- **Data errors:** Missing, inconsistent, incorrect format
- **Model error:** Non-convergence, iteration limit reached, unreasonable results
- **Integration error:** Unresolved conflict, incompatibility

### 10.2. Recovery Procedure

- Save checkpoints to memory after each stage
- On error, retrieve the most recent checkpoint
- Try with fallback configuration
- Record errors and solutions for improvement

---

## HOW TO USE — TAGS

- **\[Inference-MCTS]** — Replaces MCTS (decision-tree-based)
- **\[Inference-BEAM]** — Replaces BEAM (beam expansion of solutions)
- **\[Inference-R1]** — Replaces R1 (comprehensive analysis)
- **\[Inference-HYBRID]** — Replaces HYBRID (multi-method combination)
