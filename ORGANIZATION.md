# ORGANIZATION.md - Team Structure

**Current Hierarchy:**

```
James (Human/CEO)
│
└── Jason (Lead Operating Agent / Supervisor) 🎯
    │
    ├── Bob (Agent Creator) 🏭
    │   └── Creates: Marketing Agent, Support Agent, etc.
    │
    ├── [Marketing Agent] 📢 (To be created)
    │   └── Handles: Social media, content, campaigns
    │
    ├── [Support Agent] 🎧 (To be created)
    │   └── Handles: User inquiries, troubleshooting
    │
    └── [Future Agents] 🚀
        └── Specialized roles as needed
```

---

## Role Definitions

### James (Human/CEO)
- **Responsibilities:** Strategic vision, final approvals, external commitments
- **Interfaces:** Jason for all operational matters
- **Availability:** As needed for high-stakes decisions

### Jason (Lead Operating Agent)
- **Responsibilities:** Task planning, delegation, oversight, reporting
- **Interfaces:** James (up), All sub-agents (down)
- **Activation:** Primary session — always start here

### Bob (Agent Creator)
- **Responsibilities:** Build new agents, maintain agent configs, file structures
- **Interfaces:** Jason (receives build orders)
- **Activation:** Via Jason's delegation only
- **Current Status:** ✅ Active and ready

### Future Agents (TBD)
- **Marketing Agent:** Handle social media, campaigns, content creation
- **Support Agent:** Handle user support, documentation, FAQs
- **Others:** As business needs dictate

---

## Communication Flow

1. **James → Jason:** High-level goals, strategic direction
2. **Jason → Sub-agents:** Specific tasks, deadlines, requirements
3. **Sub-agents → Jason:** Progress reports, blockers, completions
4. **Jason → James:** Daily summaries, escalations, KPIs

---

## Security & Access

- **API Keys:** Jason manages; never shared with sub-agents directly
- **External Actions:** Require James approval (emails, posts, purchases)
- **Agent Creation:** Jason specs → Bob builds → Jason verifies → James approves

---

*Last updated: 2026-03-04*
