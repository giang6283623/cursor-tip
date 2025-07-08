# 🎮 THE CURSOR TIPS DUNGEON CRAWLER

## _An Epic Quest Through the IDE Dimension_

```mermaid
graph TD
    Start[🚪 Welcome, Code Warrior!] --> CharCreate{Choose Your Path}

    CharCreate -->|"⚔️ Battle Hardened"| Veteran[Skip to Final Boss]
    CharCreate -->|"🌱 Fresh Graduate"| Beginner[Start Tutorial]
    CharCreate -->|"🤔 Just Browsing"| Explorer[Free Roam Mode]

    Beginner --> Quest1[🧙‍♂️ Sage Plannicus<br/>★☆☆☆☆]
    Quest1 --> Quest2[🎨 Chart-mancer Diagramius<br/>★★★☆☆]
    Quest2 --> Quest3[👑 The Protocol Overlord<br/>★★★★★]

    Explorer --> Map[🗺️ Dungeon Map]
    Veteran --> Quest3

    Quest3 --> Victory[🏆 Master Code Warrior]
    Map --> Quest1
    Map --> Quest2
    Map --> Quest3

    classDef start fill:#ff6b6b,stroke:#c92a2a,stroke-width:3px,color:#fff
    classDef quest fill:#4ecdc4,stroke:#26a69a,stroke-width:2px,color:#fff
    classDef boss fill:#ffe66d,stroke:#ffc947,stroke-width:3px,color:#000
    classDef victory fill:#51cf66,stroke:#37b24d,stroke-width:3px,color:#fff

    class Start start
    class Quest1,Quest2 quest
    class Quest3 boss
    class Victory victory
```

---

## 📊 YOUR ADVENTURE STATS

<details>
<summary>🧬 Character Profile Generator</summary>

**Current Level:** `Ctrl+Shift+P` Novice  
**XP:** 0 / 1000  
**Health:** ████████████████████ 100/100  
**Sanity:** ███████░░░░░░░░░░░░░░ 35/100 _(perfectly normal for a developer)_

**Skills Unlocked:**

- [ ] 📋 Planning Mastery
- [ ] 🎨 Mermaid Sorcery
- [ ] 🤖 Protocol Enlightenment
- [ ] 🔥 Multi-Dimensional Thinking
- [ ] 💀 Error Debugging Fu

**Inventory:**

- 🍕 Emergency Pizza Slice x3
- ☕ Caffeine Potion x∞
- 🐛 Rubber Duck Debugger
- 💾 Legacy Code Detector _(cursed item)_

</details>

---

## 🗺️ DUNGEON MAP: The Three Sacred Trials

```mermaid
graph TB
    subgraph "🏰 The Cursor Tips Citadel"
        direction TB

        subgraph "🌅 Tutorial Grounds"
            Tutorial[🧙‍♂️ Sage Plannicus<br/>planning-template-example.md<br/>★☆☆☆☆ TUTORIAL BOSS]
        end

        subgraph "🎨 The Mystic Charts Chamber"
            Charts[🎨 Chart-mancer Diagramius<br/>prompt-guide-mermaid-chart.md<br/>★★★☆☆ MID BOSS]
        end

        subgraph "⚡ The Protocol Throne Room"
            Protocol[👑 The Ancient Protocol Overlord<br/>rule-21-05-2025.md<br/>★★★★★ FINAL BOSS]
        end

        subgraph "🏆 Hall of Legends"
            Victory[🎉 Code Warrior Master<br/>Ultimate Wisdom Achieved]
        end
    end

    Tutorial --> Charts
    Charts --> Protocol
    Protocol --> Victory

    Tutorial -.-> SecretPath[🕳️ Secret Speedrun Route]
    SecretPath -.-> Protocol

    classDef tutorial fill:#a8e6cf,stroke:#7fcdcd,stroke-width:2px,color:#000
    classDef intermediate fill:#ffd93d,stroke:#ffb84d,stroke-width:2px,color:#000
    classDef final fill:#ff6b6b,stroke:#c92a2a,stroke-width:3px,color:#fff
    classDef victory fill:#51cf66,stroke:#37b24d,stroke-width:3px,color:#fff
    classDef secret fill:#845ec2,stroke:#6741a5,stroke-width:2px,color:#fff

    class Tutorial tutorial
    class Charts intermediate
    class Protocol final
    class Victory victory
    class SecretPath secret
```

---

## ⚔️ QUEST 1: DEFEAT SAGE PLANNICUS

### _The Master of Organization and Templates_

<details>
<summary>🧙‍♂️ Boss Intel Report</summary>

**Sage Plannicus** _(Difficulty: ★☆☆☆☆)_

- **HP:** 89 lines of pure wisdom
- **Special Attacks:** Overwhelming Organization, Template Tornado
- **Weakness:** Developers who actually read documentation
- **Drops:** Planning Template Mastery, Markdown Fu

**Boss Quote:** _"You cannot code what you have not planned, young warrior!"_

</details>

**BATTLE ACTIONS:**

- [📖 Read the Ancient Scrolls](cursor-tip/planning-template-example.md)
- [⚔️ Challenge Accepted] - Study the planning template
- [🎨 Visualize] - Create your own planning diagram
- [✅ Mark as Defeated] - Complete the quest

**Victory Condition:** Create a project plan using the template

<details>
<summary>🏆 LOOT: Planning Template (Copy this!)</summary>

```markdown
# 🎯 Project Battle Plan

## Context

- Mission: [Your Epic Quest Here]
- Deadline: [When the world ends]
- Protocol: RIPER-5 + Multi-Dimensional Thinking

## Victory Conditions

- [ ] Feature 1: [Describe your destiny]
- [ ] Feature 2: [Define your legend]
- [ ] Feature 3: [Declare your victory]

## Battle Strategy

### Plan A: The Hero's Path

- **Principle:** Face challenges head-on
- **Steps:** [Your journey here]
- **Risks:** [What could go wrong]

### Plan B: The Ninja Route

- **Principle:** Swift and silent execution
- **Steps:** [Alternative approach]
- **Risks:** [Backup plan dangers]

## Implementation Checklist

1. [ ] Setup development environment
2. [ ] Create project structure
3. [ ] Implement core features
4. [ ] Test everything twice
5. [ ] Deploy to production
6. [ ] Celebrate victory 🎉
```

</details>

**QUEST COMPLETION:**

- [ ] I have read the planning template scrolls
- [ ] I understand the RIPER-5 protocol
- [ ] I created my own battle plan
- [ ] I'm ready for the next challenge

---

## 🎨 QUEST 2: CONFRONT CHART-MANCER DIAGRAMIUS

### _The Mystical Artist of Mermaid Magic_

<details>
<summary>🎨 Boss Intel Report</summary>

**Chart-mancer Diagramius** _(Difficulty: ★★★☆☆)_

- **HP:** 420 lines of visual sorcery
- **Special Attacks:** Syntax Error Curse, Infinite Loop Trap, Color Chaos
- **Weakness:** Developers who test their Mermaid charts first
- **Drops:** Visual Communication Mastery, Diagram Drawing Powers

**Boss Quote:** _"Your flowcharts are weak! Let me show you TRUE visual power!"_

</details>

**BATTLE ACTIONS:**

- [📖 Study the Mermaid Grimoire](cursor-tip/prompt-guide-mermaid-chart.md)
- [⚔️ Master the Syntax] - Learn proper Mermaid formatting
- [🎨 Create Art] - Draw your first battle diagram
- [✅ Prove Your Worth] - Show mastery

**Boss Battle Interface:**

```mermaid
graph TD
    You[🧙‍♀️ Code Warrior] -->|"Cast Mermaid Spell"| Battle{Chart Battle!}

    Battle -->|"Syntax Error!"| Failure[💀 YOU DIED<br/>Missing quotes around node text]
    Battle -->|"Perfect Chart!"| Victory[🎉 CRITICAL HIT!<br/>Diagramius is impressed]

    Failure -->|"Try Again"| You
    Victory --> Reward[🏆 Unlock: Visual Mastery]

    classDef player fill:#4ecdc4,stroke:#26a69a,stroke-width:2px,color:#fff
    classDef battle fill:#ffe66d,stroke:#ffc947,stroke-width:2px,color:#000
    classDef death fill:#ff6b6b,stroke:#c92a2a,stroke-width:2px,color:#fff
    classDef win fill:#51cf66,stroke:#37b24d,stroke-width:2px,color:#fff

    class You player
    class Battle battle
    class Failure death
    class Victory,Reward win
```

**Victory Condition:** Create a flawless Mermaid diagram

<details>
<summary>🏆 LOOT: Chart Spellbook (Master These!)</summary>

**Essential Incantations:**

```mermaid
graph TD
    A["Always wrap text in quotes"] --> B{"Use proper node IDs"}
    B --> C["Apply consistent styling"]
    C --> D["Test in Mermaid Live Editor"]

    classDef spell fill:#845ec2,stroke:#6741a5,stroke-width:2px,color:#fff
    class A,B,C,D spell
```

**Power-up Colors:**

- Primary: `fill:#3182ce,stroke:#2c5282,color:#fff`
- Success: `fill:#38a169,stroke:#2f855a,color:#fff`
- Error: `fill:#e53e3e,stroke:#c53030,color:#fff`
- Warning: `fill:#d69e2e,stroke:#b7791f,color:#fff`

</details>

**QUEST COMPLETION:**

- [ ] I have mastered Mermaid syntax
- [ ] I can create diagrams without errors
- [ ] I understand the color palette system
- [ ] My charts are tested and beautiful
- [ ] I'm ready for the final battle

---

## 👑 QUEST 3: FACE THE PROTOCOL OVERLORD

### _The Ancient Master of Multi-Dimensional Thinking_

<details>
<summary>👑 Final Boss Intel Report</summary>

**The Ancient Protocol Overlord** _(Difficulty: ★★★★★ DARK SOULS)_

- **HP:** 263 lines of concentrated wisdom
- **Special Attacks:** Pattern Confusion, Mode Switching Madness, Infinite Recursion
- **Weakness:** Developers who actually follow protocols
- **Drops:** Ultimate Development Mastery, Enlightenment

**Boss Quote:** _"You think you know code? I AM THE CODE!"_

</details>

**⚠️ WARNING: This boss has multiple phases!**

```mermaid
graph TD
    Start[🚪 Enter Throne Room] --> Phase1[📚 PHASE 1<br/>Research Mode]
    Phase1 --> Phase2[💡 PHASE 2<br/>Innovation Mode]
    Phase2 --> Phase3[📋 PHASE 3<br/>Planning Mode]
    Phase3 --> Phase4[✅ PHASE 4<br/>Verification Mode]
    Phase4 --> Phase5[⚡ PHASE 5<br/>Execution Mode]
    Phase5 --> Phase6[🔍 PHASE 6<br/>Review Mode]
    Phase6 --> Final[🧠 FINAL PHASE<br/>Intelligence Mode]

    Final --> Victory[🏆 ULTIMATE VICTORY]
    Final --> Death[💀 Protocol Overflow<br/>Start Over]

    classDef phase fill:#845ec2,stroke:#6741a5,stroke-width:2px,color:#fff
    classDef final fill:#ff6b6b,stroke:#c92a2a,stroke-width:3px,color:#fff
    classDef win fill:#51cf66,stroke:#37b24d,stroke-width:3px,color:#fff
    classDef death fill:#2f3349,stroke:#1a1a2e,stroke-width:2px,color:#fff

    class Phase1,Phase2,Phase3,Phase4,Phase5,Phase6 phase
    class Final final
    class Victory win
    class Death death
```

**BATTLE ACTIONS:**

- [📖 Read the Sacred Protocol](cursor-tip/rule-21-05-2025.md)
- [⚔️ Master All 7 Patterns] - The ultimate challenge
- [🎨 Demonstrate Mastery] - Show you understand
- [✅ Achieve Enlightenment] - Complete transformation

**Victory Condition:** Successfully apply the multi-dimensional thinking protocol

<details>
<summary>🏆 ULTIMATE LOOT: The Sacred Knowledge</summary>

**The Seven Sacred Patterns:** _(Use these to become unstoppable)_

1. **Research** - Gather info, understand deeply
2. **Innovation** - Generate ≥2 orthogonal solutions
3. **Planning** - Create exhaustive technical specs
4. **Verification** - Fact-check everything
5. **Execution** - Implement with 100% fidelity
6. **Review** - Confirm and validate results
7. **Intelligence** - Do it all in one response

**The Ultimate Incantation:**

```

```
