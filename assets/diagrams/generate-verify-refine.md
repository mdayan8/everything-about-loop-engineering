# Generate-Verify-Refine Loop

```mermaid
flowchart LR
    A[Generate] --> B[Verify Against Real Feedback]
    B -- Pass --> C[Deliver]
    B -- Fail --> D[Refine]
    D --> A
```
