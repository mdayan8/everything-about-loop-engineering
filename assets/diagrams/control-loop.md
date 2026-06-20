# Control Loop Diagram

```mermaid
flowchart LR
    A[Observe State] --> B{Desired State Reached?}
    B -- No --> C[Take Action]
    C --> A
    B -- Yes --> D[Wait / Stop]
    D --> A
```
