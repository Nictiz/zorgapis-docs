# Adding a trust framework

## Entity relationship diagram

``` mermaid
erDiagram
  TRUST-FRAMEWORK ||--o{ VERSION : contains
  TRUST-FRAMEWORK }o..|| ORGANIZATION : references
```

!!! info

    - Exactly one `TRUST-FRAMEWORK` *contains* zero or more `VERSION`
    - Zero or more `TRUST-FRAMEWORK` *references* exactly one `ORGANIZATION`

## Add trust framework

## Add trust framework version

## Set trust framework main version