# Goal-Condition Primitive

```mermaid
flowchart LR
    A[Agent Acts] --> B[Verifier Checks Condition]
    B -- Condition Met --> C[Loop Stops]
    B -- Condition Not Met --> A
```
