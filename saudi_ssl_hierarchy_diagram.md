# Saudi National SSL Certificate Policy

## Figure 1 – Scope and Domain of Saudi National SSL
*Based on Section 1.1.3, Page 12 of Saudi National SSL Certificate Policy v1.4*

```mermaid
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
```

## Scope and Domain Components

### **Organizational Structure**
- **SDAIA**: Saudi Data and Artificial Intelligence Authority - Owner and operator
- **NIC**: National Information Center - Entity under SDAIA that operates the public Saudi National SSL

### **Certificate Authority Hierarchy**

#### **Saudi National SSL Root CA**
- **Type**: Self-signed Root Certificate Authority (Trust Anchor)
- **Key Specification**: RSA 4096 bits
- **Signature Algorithm**: SHA-512 with RSA
- **Validity Period**: 240 months (20 years) or valid not beyond 2043, whichever is earlier
- **Function**: Issues certificates only to approved subordinate CAs
- **Status**: Offline Root CA for enhanced security

#### **Saudi National SSL CA (Issuing CA)**
- **Type**: Subordinate Certificate Authority
- **Key Specification**: RSA 3072 bits  
- **Signature Algorithm**: SHA-256 with RSA
- **Validity Period**: 120 months (10 years) or valid not beyond 2033, whichever is earlier
- **Function**: Issues Organization Validation SSL certificates to end entities

#### **End Entity SSL Certificates**
- **Type**: Organization Validation (OV) SSL Certificates
- **Key Specification**: RSA 3072 bits minimum
- **Signature Algorithm**: SHA-256 with RSA
- **Validity Period**: 12 months maximum
- **Policy OID**: 2.23.140.1.2.2 (CA/Browser Forum OV)

### **Eligible Certificate Recipients (Scope)**
As defined in Section 1.1.3, the Saudi National SSL issues certificates to:
- **Registered Organizations in KSA**: Any legally registered organization within the Kingdom of Saudi Arabia
- **Government Entities in KSA**: All government entities, departments, and agencies within Saudi Arabia

### **PKI Operations and Governance**

#### **Certificate Policy Framework**
```
Saudi National SSL Certificate Policy (CP)
└── OID: 2.16.682.1.101.5000.1.6.1.1
    ├── Saudi National SSL Root CA CPS
    │   └── OID: 2.16.682.1.101.5000.1.6.1.2
    └── Saudi National SSL CA CPS
        └── OID: 2.16.682.1.101.5000.1.6.1.3
```

#### **PKI Infrastructure Services**
- **Certificate Repository**: http://ssl.gov.sa/repository
- **Root CA Certificate**: http://ssl.gov.sa/repository/certs/snsslrootca.crt  
- **Issuing CA Certificate**: http://ssl.gov.sa/repository/certs/snsslca.crt
- **CRL Distribution Points**:
  - Root CA CRL: http://crl.ssl.gov.sa/snsslrootca.crl
  - Issuing CA CRL: http://crl.ssl.gov.sa/snsslca.crl
- **OCSP Responder**: http://ocsp.ssl.gov.sa

### **Compliance and Standards**
- **CA/Browser Forum Baseline Requirements**: Full compliance with publicly-trusted certificate requirements
- **WebTrust Auditing**: WebTrust for Certification Authorities and SSL Baseline with Network Security
- **FIPS 140-2 Level 3**: Cryptographic modules for key generation and storage
- **Multi-Person Control**: 3 of 5 shareholders required for CA operations with 2 of 3 trusted personnel for HSM control