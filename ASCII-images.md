## Architecture Diagram (ASCII)

```
┌─────────────────────────────────────┐
│              USER                   │
│    • Goals                         │
│    • Constraints                   │
│    • Feedback                      │
└──────────────┬──────────────────────┘
               │
┌──────────────▼──────────────────────┐
│          .claude.md                 │
│    • Global Rules                  │
│    • Safety Guidelines             │
│    • Thinking Patterns             │
└──────────────┬──────────────────────┘
               │
┌──────────────▼──────────────────────┐
│        CLAUDE ENGINE                │
│    ┌──────────────────────────┐    │
│    │      Coordinator         │    │
│    │  • Task Planning        │    │
│    │  • Skill Selection      │    │
│    │  • Validation           │    │
│    └──────────┬───────────────┘    │
│               │                    │
│    ┌──────────▼───────────────┐    │
│    │      Memory & State      │    │
│    │  • Context Tracking      │    │
│    │  • Progress Monitoring   │    │
│    │  • Checkpoints           │    │
│    └──────────────────────────┘    │
└──────────────┬──────────────────────┘
               │
    ┌──────────┴──────────┐
    ▼                     ▼
┌─────────┐         ┌─────────┐
│ skill/  │         │ Tools   │
│         │         │         │
│ • Python│         │ • File  │
│ • C     │         │ • Shell │
│ • Java  │         │ • Web   │
└─────────┘         └─────────┘
```





## Multi-Agent Orchestration Diagram (ASCII)

```
                    ┌─────────────────┐
                    │    START        │
                    │  User Request   │
                    └────────┬────────┘
                             │
                    ┌────────▼────────┐
                    │   COORDINATOR   │
                    │                 │
                    │ 1. Parse request│
                    │ 2. Plan steps   │
                    │ 3. Assign agents│
                    └────────┬────────┘
                             │
         ┌───────────────────┼───────────────────┐
         │                   │                   │
    ┌────▼─────┐       ┌────▼─────┐       ┌────▼─────┐
    │ Python   │       │    C     │       │  Java    │
    │ Expert   │       │  Expert  │       │  Expert  │
    │          │       │          │       │          │
    │• Security│       │• Memory  │       │• Spring  │
    │• Data    │       │• Perf    │       │• Threads │
    │• ML      │       │• Safety  │       │• Microsvc│
    └────┬─────┘       └────┬─────┘       └────┬─────┘
         │                  │                  │
         └──────────────────┼──────────────────┘
                            │
                    ┌───────▼───────┐
                    │   MERGE &     │
                    │   VALIDATE    │
                    │               │
                    │ 1. Combine    │
                    │ 2. Check      │
                    │ 3. Resolve    │
                    └───────┬───────┘
                            │
                    ┌───────▼───────┐
                    │    FINAL      │
                    │    OUTPUT     │
                    │               │
                    │• Report       │
                    │• Documentation│
                    │• Next steps   │
                    └───────────────┘
```
