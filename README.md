graph TD
    subgraph "Saudi National SSL PKI Domain"
        subgraph "SDAIA - Saudi Data and Artificial Intelligence Authority"
            subgraph "NIC - National Information Center"
                A[Saudi National SSL Root CA<br/>Self-signed Trust Anchor<br/>RSA 4096 | SHA-512<br/>20 years validity]
                
                A --> B[Saudi National SSL CA<br/>Issuing CA<br/>RSA 3072 | SHA-256<br/>10 years validity]
                
                B --> C[Organization Validation<br/>SSL Certificates<br/>RSA 3072 | SHA-256<br/>12 months validity]
            end
        end
        
        subgraph "Certificate Recipients - Kingdom of Saudi Arabia"
            C --> D[Registered Organizations<br/>in KSA]
            C --> E[Government Entities<br/>in KSA]
        end
        
        subgraph "PKI Services & Repository"
            F[Certificate Repository<br/>http://ssl.gov.sa/repository]
            G[CRL Distribution<br/>http://crl.ssl.gov.sa/]
            H[OCSP Responder<br/>http://ocsp.ssl.gov.sa]
        end
        
        B -.-> F
        B -.-> G  
        B -.-> H
    end
    
    classDef rootCA fill:#ff6b6b,stroke:#333,stroke-width:3px,color:#fff
    classDef issuingCA fill:#4ecdc4,stroke:#333,stroke-width:2px,color:#fff
    classDef endEntity fill:#45b7d1,stroke:#333,stroke-width:2px,color:#fff
    classDef subscriber fill:#f9ca24,stroke:#333,stroke-width:1px
    classDef services fill:#6c5ce7,stroke:#333,stroke-width:1px,color:#fff
    
    class A rootCA
    class B issuingCA
    class C endEntity
    class D,E subscriber
    class F,G,H services
