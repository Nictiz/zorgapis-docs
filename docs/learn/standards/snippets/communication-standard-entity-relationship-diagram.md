``` mermaid
erDiagram
  COMMUNICATION-STANDARD ||--o{ VERSION : contains
  COMMUNICATION-STANDARD }o..|| ORGANIZATION : references
```

!!! info

    - Exactly one `COMMUNICATION-STANDARD` *contains* zero or more `VERSION`
    - Zero or more `COMMUNICATION-STANDARD` *references* exactly one `ORGANIZATION`