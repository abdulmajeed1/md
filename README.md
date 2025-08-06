# Saudi National SSL Certificate Policy

## Figure 1 – Scope and domain of Saudi National SSL

```mermaid
graph TD
    subgraph PKI["<b>Saudi National SSL PKI</b>"]
        A[Saudi National SSL Root CA] --> B["Saudi National SSL CA
        (Issuing CA)"]
        B --> C[End Entity Certificates]
        B --> D[End Entity Certificates]
    end
    
    classDef rootca fill:#e1f5fe,stroke:#0277bd,stroke-width:2px
    classDef issuingca fill:#f3e5f5,stroke:#7b1fa2,stroke-width:2px  
    classDef endentity fill:#e8f5e8,stroke:#2e7d32,stroke-width:2px
    
    class A rootca
    class B issuingca
    class C,D endentity
    
    %%{wrap}%%
