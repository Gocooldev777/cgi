<a name="module-01"></a>
## Module 01 – DevOps & DevSecOps Fundamentals

### 1.1 DevOps Culture, Principles and Collaboration Model

#### The DevOps Revolution

DevOps emerged from the need to bridge the gap between development teams (focused on delivering new features) and operations teams (focused on system stability). This cultural transformation emphasizes collaboration, automation, and shared responsibility.

**Core DevOps Principles:**

1. **Continuous Collaboration** - Shared responsibility between Dev and Ops
2. **Automation Everywhere** - Eliminate manual toil and create consistency
3. **Fast Feedback Loops** - Speed of feedback impacts quality and productivity
4. **Small, Frequent Releases** - Reduce risk with incremental changes
5. **Observability and Learning** - Monitor, measure, and improve continuously

#### What is DevSecOps?

DevSecOps = Development + Security + Operations

**Key Insight**: Security is not a gate, it's a guardrail.

**Shift-Left Security Visualization:**
```
Traditional:
Plan → Code → Build → Test → [SECURITY REVIEW] → Deploy
                                    (2 weeks)

DevSecOps:
Plan → Code → Build → Test → Deploy
  ↓     ↓      ↓       ↓       ↓
Threat Secret SAST   DAST  Runtime
Model  Scan   SCA    Scan   Monitor
```

---

### 1.2 SDLC vs Agile vs DevOps vs DevSecOps

**Evolution of Software Development:**

1. **Waterfall SDLC** - Sequential phases, long cycles, late feedback
2. **Agile** - Iterative development, 2-week sprints, customer collaboration
3. **DevOps** - Continuous delivery, automation, collaboration culture
4. **DevSecOps** - Security integrated throughout, automated security testing

**DORA Metrics:**

| Metric | Elite | High | Medium | Low |
|--------|-------|------|--------|-----|
| Deployment Frequency | Multiple per day | Weekly to monthly | Monthly to 6 months | < every 6 months |
| Lead Time for Changes | < 1 hour | 1 day to 1 week | 1-6 months | > 6 months |
| MTTR | < 1 hour | < 1 day | 1 day to 1 week | > 1 week |
| Change Failure Rate | 0-15% | 16-30% | 16-30% | 16-30% |

---

### 1.3 Shared Ownership – Dev, Ops and Security

In DevSecOps, security is everyone's responsibility.

**Developer Responsibilities:**
- Write secure code
- Security unit tests
- Dependency management
- Use security tools in IDE

**Operations Responsibilities:**
- Infrastructure hardening
- IAM and access control
- Network security
- Monitoring and logging

**Security Team Responsibilities:**
- Define security policies
- Threat modeling
- Provide security tooling
- Security metrics and dashboards

---

### 1.4 CIA Triad in DevOps Context

**Confidentiality** - Ensuring information is accessible only to authorized parties
- Encryption at rest and in transit
- Access control (RBAC)
- Secret management

**Integrity** - Ensuring data and systems haven't been tampered with
- Code signing
- Image signing
- Checksum validation
- Audit logging

**Availability** - Ensuring systems and data are accessible when needed
- High availability architecture
- Auto-scaling
- Circuit breakers
- Disaster recovery

---

<a name="module-02"></a>
## Module 02 – Core DevSecOps Principles & Terminologies

### 2.1 Shift-Left Security

**Definition**: Moving security testing and validation earlier in the SDLC.

**Implementation:**
- IDE security plugins
- Pre-commit hooks
- Pull request security checks
- Automated security in CI/CD

**Cost Impact:**
- Finding bugs in requirements: 1x cost
- Finding bugs in development: 5x cost
- Finding bugs in testing: 10x cost
- Finding bugs in production: 100x cost

---

### 2.2 Security as Code

**Definition**: Managing security policies, configurations, and controls through code.

**Examples:**
- Open Policy Agent (OPA) for Kubernetes policies
- Terraform Sentinel for infrastructure policies
- Cloud Custodian for compliance automation

**Benefits:**
- Version controlled
- Peer reviewed
- Testable
- Repeatable
- Auditable

---

### 2.3 Defense in Depth

**Layered Security Approach:**

```
Layer 7: User Education & Awareness
Layer 6: Application Security (WAF, Input Validation)
Layer 5: Data Security (Encryption, DLP)
Layer 4: Host Security (Antivirus, HIDS)
Layer 3: Network Security (Firewall, IDS/IPS)
Layer 2: Perimeter Security (Edge Firewall, VPN)
Layer 1: Physical Security (Access Control)
```

---

### 2.4 Least Privilege & Zero Trust

**Least Privilege**: Grant only minimum permissions necessary

**Zero Trust**: Never trust, always verify
- Verify every request
- Assume breach
- Micro-segmentation
- Continuous authentication

---


### Lab 1: Setting Up a Secure CI/CD Pipeline

**Objective**: Build a CI/CD pipeline with integrated security checks

**Components:**
1. Secret scanning (Gitleaks)
2. SAST (Bandit, Semgrep)
3. Dependency scanning (Safety, npm audit)
4. Container scanning (Trivy)
5. IaC scanning (Checkov)

### Lab 2: Implementing Security as Code with OPA

**Objective**: Use OPA to enforce Kubernetes security policies

**Policies to Implement:**
- Require specific labels
- Block root containers
- Enforce resource limits
- Restrict image registries

### Lab 3: Secret Management with HashiCorp Vault

**Objective**: Set up Vault and integrate with applications

**Tasks:**
- Install and configure Vault
- Store and retrieve secrets
- Create access policies
- Integrate with Kubernetes

---



<a name="module-03"></a>
## Module 03 – Common Attacks on DevOps and Cloud Environments

### 3.1 Supply Chain Attacks

**Definition**: Attacks targeting less-secure elements in the supply chain

**Attack Vectors:**
- Compromised dependencies
- Malicious container images
- Compromised build tools
- Backdoored libraries

**Real-World Examples:**
- SolarWinds (2020) - Build system compromise
- Event-Stream NPM (2018) - Malicious dependency

**Defense Strategies:**
1. Software Bill of Materials (SBOM)
2. Dependency verification with hashes
3. Binary authorization
4. Image signing with Cosign
5. Secure build pipelines

---

### 3.2 Container Escape Attacks

**Common Techniques:**
- Privileged containers
- hostPath mounts
- Docker socket mounting
- Kernel exploits

**Defense Strategies:**
1. Pod Security Standards
2. Run as non-root
3. Read-only root filesystem
4. Drop all capabilities
5. Runtime security monitoring (Falco)

---

### 3.3 Credential Theft and Secrets Exposure

**Common Scenarios:**
- Hardcoded secrets in code
- Secrets in Git history
- Cloud metadata service attacks (SSRF)
- Environment variable exposure

**Defense Strategies:**
1. Secret scanning in Git
2. Secrets management systems (Vault, AWS Secrets Manager)
3. Workload identity
4. Rotate secrets regularly
5. Never log secrets

---

### 3.4 API Attacks

**Common Vulnerabilities:**
- Broken Object Level Authorization (BOLA)
- Excessive data exposure
- Missing rate limiting
- Lack of input validation

**OWASP API Security Top 10:**
1. Broken Object Level Authorization
2. Broken Authentication
3. Broken Object Property Level Authorization
4. Unrestricted Resource Consumption
5. Broken Function Level Authorization
6. Unrestricted Access to Sensitive Business Flows
7. Server Side Request Forgery
8. Security Misconfiguration
9. Improper Inventory Management
10. Unsafe Consumption of APIs

---

<a name="module-04"></a>
## Module 04 – Network and Platform Security for DevOps

### 4.1 Network Segmentation

**Purpose**: Isolate workloads to limit blast radius

**Implementation:**
- VPCs with multiple subnets (public, private, database)
- Security groups with least privilege
- Network ACLs
- Private endpoints for cloud services

**Multi-Tier Architecture:**
```
Internet
    ↓
[Load Balancer] - Public Subnet
    ↓
[Application Servers] - Private Subnet
    ↓
[Database] - Database Subnet (no internet)
```

---

### 4.2 Firewall and Security Groups

**Best Practices:**
- Default deny all traffic
- Allow only necessary ports
- Use security group references instead of CIDR blocks
- Regular audit and cleanup
- Tag all security groups

**Example Security Group Rules:**
```
Web Tier:
  Inbound: 443 from 0.0.0.0/0
  Outbound: 8080 to App Tier SG

App Tier:
  Inbound: 8080 from Web Tier SG
  Outbound: 5432 to DB Tier SG

DB Tier:
  Inbound: 5432 from App Tier SG
  Outbound: None (deny all)
```

---

### 4.3 Service Mesh Security

**Service Mesh Benefits:**
- Mutual TLS between all services
- Traffic encryption
- Access policies
- Request authentication
- Observability

**Istio Security Features:**
- Automatic mTLS
- Authorization policies
- JWT authentication
- Certificate management

---

### 4.4 Infrastructure Hardening

**Server Hardening Checklist:**
- Disable unnecessary services
- Configure firewall (ufw, iptables)
- Secure SSH (disable root login, key-based auth)
- Enable automatic security updates
- Configure audit logging
- Install and configure fail2ban
- Set up intrusion detection (AIDE, Tripwire)

**Container Hardening:**
- Use minimal base images
- Run as non-root user
- Read-only root filesystem
- Drop all capabilities
- No privileged mode
- Resource limits

---



### Lab 4: Network Security Configuration

**Objective**: Configure secure network architecture in cloud

**Tasks:**
1. Create VPC with multiple subnets
2. Configure security groups with least privilege
3. Set up NAT gateway for private subnets
4. Configure VPC flow logs
5. Test network isolation

### Lab 5: Container Security Scanning

**Objective**: Scan containers for vulnerabilities

**Tools:**
- Trivy for vulnerability scanning
- Dockle for best practice checks
- Grype for comprehensive scanning

**Tasks:**
1. Build Docker image
2. Scan with multiple tools
3. Fix identified vulnerabilities
4. Integrate into CI/CD pipeline

### Lab 6: Runtime Security with Falco

**Objective**: Detect suspicious container behavior

**Tasks:**
1. Install Falco on Kubernetes
2. Configure custom rules
3. Generate test alerts
4. Integrate with SIEM/alerting

---


<a name="module-05"></a>
## Module 05 – Secure Protocols, Secrets and Encryption

### 5.1 TLS/SSL Best Practices

**TLS Configuration:**
- Use TLS 1.3 (or minimum TLS 1.2)
- Strong cipher suites only
- Perfect Forward Secrecy (PFS)
- HSTS headers
- Certificate pinning for critical services

**Example Nginx Configuration:**
```nginx
server {
    listen 443 ssl http2;
    
    ssl_protocols TLSv1.3 TLSv1.2;
    ssl_ciphers 'TLS_AES_128_GCM_SHA256:TLS_AES_256_GCM_SHA384';
    ssl_prefer_server_ciphers on;
    
    add_header Strict-Transport-Security "max-age=31536000; includeSubDomains" always;
}
```

---

### 5.2 Encryption at Rest and in Transit

**At Rest:**
- Database encryption (TDE)
- Disk/volume encryption (LUKS, BitLocker)
- Object storage encryption (S3 SSE)
- Application-level encryption for sensitive fields

**In Transit:**
- TLS for all network communications
- VPN for site-to-site connections
- mTLS for service-to-service communication
- SSH for remote access

---

### 5.3 Secrets Management

**Secrets Management Solutions:**
- HashiCorp Vault
- AWS Secrets Manager
- Azure Key Vault
- Google Secret Manager
- Kubernetes Secrets (with encryption at rest)

**Best Practices:**
- Never commit secrets to Git
- Rotate secrets regularly
- Use short-lived credentials when possible
- Audit secret access
- Encrypt secrets at rest
- Use workload identity instead of long-lived credentials

---

### 5.4 Key Management

**Key Management Service (KMS) Usage:**
- Envelope encryption for data
- Automatic key rotation
- Audit logging of key usage
- Separate keys per environment
- Principle of least privilege for key access

**Key Hierarchy:**
```
Master Key (HSM-backed)
    ↓
Data Encryption Keys (DEKs)
    ↓
Encrypted Data
```

---

<a name="module-06"></a>
## Module 06 – Cloud Security for DevOps

### 6.1 Cloud Identity and Access Management

**IAM Best Practices:**
- Use IAM roles instead of access keys
- Implement least privilege
- Enable MFA for all users
- Regular access reviews
- Use service accounts for automation
- Implement just-in-time access

**AWS IAM Policy Example:**
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": ["s3:GetObject", "s3:PutObject"],
      "Resource": "arn:aws:s3:::my-bucket/${aws:username}/*"
    }
  ]
}
```

---

### 6.2 Cloud Security Posture Management (CSPM)

**What is CSPM:**
- Continuous monitoring of cloud configurations
- Automated detection of misconfigurations
- Compliance checking
- Remediation recommendations

**Common Misconfigurations:**
- Public S3 buckets
- Overly permissive security groups
- Missing encryption
- Disabled logging
- No MFA on root account
- Unused access keys

**CSPM Tools:**
- AWS Security Hub
- Azure Security Center
- Google Security Command Center
- Prisma Cloud
- Wiz
- Orca Security

---

### 6.3 Cloud Workload Protection

**Container Security:**
- Image scanning before deployment
- Runtime protection
- Network segmentation
- Secrets management
- Compliance policies

**Serverless Security:**
- Function-level permissions
- API Gateway security
- Input validation
- Dependency scanning
- Cold start security

---

### 6.4 Cloud Compliance and Governance

**Compliance Frameworks:**
- SOC 2
- ISO 27001
- PCI-DSS
- HIPAA
- GDPR

**Compliance as Code:**
- Automated compliance checks
- Policy-as-code enforcement
- Continuous compliance monitoring
- Automated evidence collection
- Audit-ready documentation

**Tools:**
- AWS Config Rules
- Azure Policy
- Google Cloud Asset Inventory
- Cloud Custodian
- Chef InSpec

---



### Lab 7: TLS Configuration and Certificate Management

**Objective**: Configure secure TLS and automate certificate management

**Tasks:**
1. Generate SSL certificates with Let's Encrypt
2. Configure Nginx with TLS 1.3
3. Implement HSTS
4. Test with SSL Labs
5. Automate certificate renewal

### Lab 8: Implementing Encryption

**Objective**: Encrypt data at rest and in transit

**Tasks:**
1. Enable database encryption (RDS)
2. Encrypt S3 buckets
3. Implement application-level encryption
4. Use KMS for key management
5. Set up envelope encryption

### Lab 9: Cloud Security Audit

**Objective**: Audit cloud environment for security issues

**Tasks:**
1. Run AWS Security Hub assessment
2. Use Scout Suite for multi-cloud audit
3. Identify misconfigurations
4. Prioritize findings
5. Create remediation plan

### Lab 10: Compliance Automation

**Objective**: Implement automated compliance checking

**Tasks:**
1. Define compliance policies in code
2. Set up Cloud Custodian
3. Configure automated remediation
4. Generate compliance reports
5. Set up continuous monitoring

---

## Additional Resources

### Security Tools Cheat Sheet

**SAST (Static Application Security Testing):**
- Semgrep
- SonarQube
- Bandit (Python)
- Brakeman (Ruby)
- ESLint (JavaScript)

**DAST (Dynamic Application Security Testing):**
- OWASP ZAP
- Burp Suite
- Nikto
- Nuclei

**SCA (Software Composition Analysis):**
- Snyk
- Dependency-Check
- Safety (Python)
- npm audit (Node.js)

**Container Security:**
- Trivy
- Grype
- Clair
- Anchore

**Secrets Scanning:**
- Gitleaks
- TruffleHog
- detect-secrets

**Infrastructure as Code Security:**
- Checkov
- tfsec
- Terrascan
- KICS

**Runtime Security:**
- Falco
- Sysdig
- Aqua Security

---

## DevSecOps Maturity Model

### Level 1: Initial
- Manual security reviews
- Security testing before production only
- Limited automation
- Reactive security approach

### Level 2: Managed
- Some automated security scanning
- Security integrated in CI/CD
- Basic security training
- Security metrics tracked

### Level 3: Defined
- Comprehensive automated security testing
- Security throughout SDLC
- Security champions program
- Proactive vulnerability management

### Level 4: Quantitatively Managed
- Security metrics drive decisions
- Predictive security analytics
- Continuous improvement culture
- Advanced automation

### Level 5: Optimizing
- Proactive threat hunting
- AI/ML-powered security
- Industry-leading practices
- Security innovation

---

## Security Metrics to Track

### Key Performance Indicators (KPIs):

1. **Mean Time to Detect (MTTD)**
   - Average time from vulnerability introduction to detection

2. **Mean Time to Remediate (MTTR)**
   - Average time from detection to fix deployment

3. **Vulnerability Density**
   - Number of vulnerabilities per 1000 lines of code

4. **Security Debt**
   - Count of open vulnerabilities by severity

5. **Shift-Left Effectiveness**
   - Percentage of vulnerabilities found before production

6. **Security Test Coverage**
   - Percentage of code covered by security tests

7. **Compliance Score**
   - Percentage of resources compliant with policies

8. **Secret Exposure Rate**
   - Number of secrets found in code repositories

---

## Best Practices Summary

### Code Security:
✅ Use parameterized queries (prevent SQL injection)
✅ Sanitize all user input
✅ Implement proper authentication and authorization
✅ Use security linters in IDE
✅ Write security unit tests
✅ Keep dependencies updated

### Infrastructure Security:
✅ Principle of least privilege
✅ Network segmentation
✅ Encrypt data at rest and in transit
✅ Enable audit logging
✅ Regular security patching
✅ Infrastructure as Code for consistency

### Container Security:
✅ Use minimal base images
✅ Run as non-root
✅ Read-only root filesystem
✅ Scan images before deployment
✅ Sign and verify images
✅ Runtime security monitoring

### Cloud Security:
✅ Enable MFA for all accounts
✅ Use IAM roles, not access keys
✅ Enable CloudTrail/audit logging
✅ Encrypt all data stores
✅ Regular security assessments
✅ Implement CSPM

### CI/CD Security:
✅ Secret scanning in pipeline
✅ SAST and SCA in every build
✅ Container scanning before push
✅ IaC security scanning
✅ DAST on staging environments
✅ Signed artifacts only in production

---

## Incident Response

### Incident Response Plan:

1. **Preparation**
   - Define roles and responsibilities
   - Create runbooks
   - Set up communication channels
   - Establish escalation paths

2. **Detection**
   - Automated monitoring and alerting
   - Log aggregation and analysis
   - Threat intelligence integration

3. **Analysis**
   - Determine scope and impact
   - Identify root cause
   - Assess business impact

4. **Containment**
   - Isolate affected systems
   - Prevent lateral movement
   - Preserve evidence

5. **Eradication**
   - Remove threat
   - Patch vulnerabilities
   - Update security controls

6. **Recovery**
   - Restore from clean backups
   - Validate system integrity
   - Monitor for reinfection

7. **Post-Incident**
   - Blameless post-mortem
   - Document lessons learned
   - Update procedures
   - Implement preventive measures

---

## Conclusion

DevSecOps is a journey, not a destination. Key takeaways:

1. **Culture First**: Security is everyone's responsibility
2. **Shift Left**: Find and fix issues early
3. **Automate Everything**: Security at the speed of DevOps
4. **Continuous Improvement**: Always be learning and adapting
5. **Measure Progress**: Use metrics to drive improvement

### Next Steps:
- Assess current security maturity
- Identify quick wins
- Build security champions network
- Implement automated security testing
- Foster collaboration between teams
- Continuously measure and improve

---

## Glossary

**BOLA** - Broken Object Level Authorization  
**CSPM** - Cloud Security Posture Management  
**DAST** - Dynamic Application Security Testing  
**DORA** - DevOps Research and Assessment  
**IAM** - Identity and Access Management  
**IaC** - Infrastructure as Code  
**KMS** - Key Management Service  
**MTTR** - Mean Time to Remediate  
**MTTD** - Mean Time to Detect  
**OPA** - Open Policy Agent  
**RBAC** - Role-Based Access Control  
**SAST** - Static Application Security Testing  
**SBOM** - Software Bill of Materials  
**SCA** - Software Composition Analysis  
**SDLC** - Software Development Lifecycle  
**SIEM** - Security Information and Event Management  
**SRE** - Site Reliability Engineering  
**SSRF** - Server-Side Request Forgery  
**TLS** - Transport Layer Security  
**WAF** - Web Application Firewall  
**XSS** - Cross-Site Scripting

---
