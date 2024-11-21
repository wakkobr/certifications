# IBM Cloud for Financial Services Course Notes

## Module 1: An Introduction to IBM Cloud for Financial Services

### Keywords
Ecosystem, mission-critical, regulations, continuous monitoring, moving data

### Key Elements
- Secure Transactions
- Monitoring
- Data Protection
- Innovation Lab

### Benefits of IBM Cloud for Financial Services
- Addresses compliance needs
- Facilitates speed and innovation
- Safeguards data
- Operates with agility everywhere

### Target Clients – Needs and Challenges
- Banking
- Insurance

### Five Key Dimensions
- Resiliency
- Security
- Compliance
- Performance
- Cost

## Module 2: Components, Risk, and Compliance

### Keywords
Define, Implement, Assess, Controls, EPX, KYOK, Confidential, NIST, GDPR, SCC, Sarbanes-Oaxley Act, Mitigate

### Define-Implement-Assess Model
- Define: controls, requirements
- Implement: automate
- Assess: monitor

### IBM Cloud for Financial Services Framework
- Originates from NIST 800-53

### DEFINE (WHAT):

#### Controls
- Simplify Risk Management
- Keep Controls Current
- Make simpler to Provide Compliance
- Real-time Monitoring

#### Core Focus Areas
- Active Monitoring and Response
- Focused Risk Management and Compliance
- Advanced Data Protection
- Operational Excellence
- Unified Infrastructure Security and Resilience
- Enhanced Authentication and Access Management
- Automated Application and Workload Protection

### IMPLEMENT (HOW):

#### Architecture Attributes (v1)
- Isolation
- Access Restriction
- Encryption
- Audit Logs and Compliance
- High Availability / Disaster Recover
- Management VPC
- Workload VPC

#### Architecture Capabilities (v1)
- Management VPC: enable application provider to monitor, operate, maintain the environment
- Workload VPC: provides compute, storage, and network services to support hosted applications

#### Architecture Comparison (v1)
- Virtual Server for VPC:  lift and shift for workloads running on virtual servers
- VMWare: VMware virtualized workloads
- Red Hat Openshift on IBM Cloud VPC: used to build new cloud-native applications, containers

#### Enterprise Platform Experience (EPX)
- Significantly reduced time to consumption (Deployable Architectures)
- Ensured "secure by default" environments for critical workloads (Catalog)
- Continuous assessments against compliance goals (SCC + DevOps)
- Alignment of cloud to their business (Projects)

#### IBM Cloud Hyper Protect Services / IBM Cloud Data Shield
- Confidential Computing
- Keep Your Own Key (KYOK)
- Confidential Containers
- Confidential Databases

#### IBM Cloud for Financial Services Validation (v1)
- Over 200 security controls

### ASSESS (WHO):

#### IBM Cloud Security and Compliance Center (SCC)
- Daily, automatic compliance checks into development lifecycle
- Analyzes client’s Cloud Security Posture (CSPM)
- Enforces users least privilege (CIEM)

#### Regulatory Authorities
- NIST (The National Institute of Standards and Technology)
- NYDFS (The New York Department of Financial Services)
- OSFI (The Office of the Superintendent of Financial Institutions)
- DORA (The Digital Operational Resilience Act) EU
- EBA (The European Banking Authority) EU

#### Financial Services Rules, Regulations, and Acts
- GDPR (General Data Protection Regulation) EU
- CCPA (California Consumer Privacy Act)
- Sarbanes-Oxley Act (2002): corporate and criminal fraud
- Dodd Frank and Gramm-Leach-Bliley Act: Financial Stability Oversight Counsel and the Consumer Financial Protection Bureau 
- AICPA/SOC (The American Institute of CPAs / System and Organizational Controls)

#### Data Classification from International Organization for Standardization (ISO)
- Company Confidential Data -> Client Confidential Data -> Proprietary/Internal Use -> Unrestricted/Public Use
 
#### Categories of Risk
- Business Impact
- Regulatory

#### Forms of Risk (v1)
- Cyber security
- Compliance
- Reputational
- Operational
- Transactional
- Credit
- Technology

#### Risk Management Process
- Identify -> Analyze and Assess -> Review Controls -> Mitigate 
 
#### De-risking Third and Fourth-Party Risks -> Improved agility and innovation
- Lack of visibility
- Lack of control
- Lack of understanding

## Module 3: Customer Workload Environment

### Keywords
Core computing, mission-critical, regulatory issues, transform business, zero-trust, virtualized workloads, containers, controls, ecosystem, portable, confidential, SLZ, continuous compliance, automation

### Application Migration and Modernization
- Achieves Continuous Compliance
- Accelerate Innovation
- Operate with Agility
- Safeguard Data

### Migration Process (v1)
- Assess -> Plan -> Migrate -> Validate

### Workload Considerations (v1)
- Security, compliance and regulations
- Data latency
- Complexity of hybrid and multicloud
- Talent

### Lift and Shift
- Modernize without changing
- As-is
- Alternatives (v1): PaaS or SaaS migration

### The IBM Well-Architected Framework
- Hybrid and Portable
- Resiliency
- Efficient Operations
- Security and Compliance
- Performance
- Financial Operations and Sustainability

### Design Principles for the Well-Architected Framework
- Automate Operations
- Respect Data Gravity
- Best Platform for the Workload

### IBM Cloud Tools to Support the Architecture
 - Secure Landing Zone (SLZ)
 - OnePipeline
 - IBM Cloud Security and Compliance Center (SCC)

#### Secure Landing Zone (SLZ): 
 - Management and Workload VPCs connected by a transit gateway
 - Virtual Private Cloud (VPC):  Flow log collector created
 - Virtual Server Instance (VSI)
 - Red Hat® OpenShift®  

#### OnePipeline (Tekton)
 - Continuous Integration (CI): Develop applications (software development process)
 - Continuous Deployment (CD): Toolchain, DevSecOps
 - Continuous Compliance (CC): Security, compliance
 
## Module 4: Technical Solution Design

### Keywords
Satellite, key management, FIPS level 4, OpenShift, block storage

### Reference Architectures
- IBM Cloud VPC
- IBM Cloud Satellite
- IBM Cloud for VMware Regulated Workloads

### IBM Cloud Virtual Private Cloud (VPC)
- Logical Isolation: Subnets, scalability, security
- Quick instance provisioning with high performance: virtual server instances
- Multi-architecture images: different operating systems
- Storage capabilities: block storage
- External connectivity
- Security: security groups (virtual firewalls), ACLs
- High Availability: region (VPC is deployed), which contain zones (logically isolated data centers), multiple zones
- Classic access: IBM Cloud Classic, Direct Link

### IBM Cloud VPC Options
- IBM Cloud Virtual Servers for VPC: virtual servers, 3 zones in one MZR
- Red Hat® OpenShift® on IBM Cloud: containers, 1 zone

### IBM Cloud Satellite
- Flexible infrastructure options
- Growing catalog of services and software
- Consistent operations experience
- Security across locations

### Architecture Building Blocks: Hub and Spoke Pattern
- Workload VPC: keeps data isolated, Virtual Private Endpoint
- Management VPC: network segment is shared, bastion server
- Edge/transit VPC: all communication pass, internal to external, On-premises data center or Point of Presence (POP)

### Financial Services Cloud Hyper Protect Crypto Services (HPCS)
- Key management & encryption
- Unified key orchestrator
- KYOK
- FIPS 140-2 level 4

## Module 5: Implementation Considerations

### Keywords
DevSecOps, continuous integration, code risk analyzer, IAM, nesting account groups, OpenPages, KYOK, TLS, industry informed framework, risk-averse

### IBM Cloud Enterprise Account Management
- Centralized account management
- Consolidated subscription billing
- Top-down usage reporting
- Enterprise-managed IAM

### IBM Cloud Enterprise Hierarchy
 Enterprise account -> Account groups -> Accounts -> Nested account groups
 
### Financial Services Validation
- IBM Cloud for Financial Services Validated
- Advantage to Bank
- Advantage to ISV
- OpenPages is used to collect evidence

### Requirements for Financial Services Validation
- Approved architecture
- System of account and access management: zero-trust environment
- Non-prod treated as Prod
- Isolate and separate functions
- Protect the boundaries of the application
- Execute all operator actions through a Bastion host
- Capture audit events
- Follow secure development processes
- Encrypt consumer data always: KYOK, TLS
- Design for high availability
- BCP and DR
- Monitor for security and compliance

### Toolchains
- DevOps tools are integrated into toolchains
- Integration of capabilities

### Continuous Integration & Benefits
- New code integrated at least 1/day
- Automated testing
- Progress for improved feedback
- Early error detection and metrics
- Improved team collaboration
- Fewer parallel changes 
- Fewer errors during system testing
- Constantly updated systems against which to test
- Controls, Checkpoint, Speed (v1)

### DevOps Lifecycle (v1)
- Planning -> Development -> Integration -> Deployment -> Operations -> Learning -> (back to start)

### Code Risk Analyzer (CRA) (v1)
- Quickly assess and remediate security and legal risks
- CRA is provided as a set of Tekton tasks
- Can be easily incorporated into delivery pipelines
- Snyk (IBM partner)

## Module 6: Compliance, SLOs, and SLAs

### Keywords
CDR, CIEM, CWP, CSPM, Cloud Support Tiers, SLA, SLO, automation, controls, workload protection, cyberstrong

### Five Dimensions
- Security
- Compliance
- Performance
- Cost
- Risk

### Overview of IBM Security Compliance Center (SCC)
- Controls
- Policies
- Automation and integration
- Workload protection
- Remediation and response

### SCC's Key Capabilities
- Continuous Compliance and Risk Posture
- Cloud Detection and Response (CDR)
- Cloud Infrastructure Entitlement Management (CIEM)
- Cloud Workload Protection (CWP)
- Automation and Integration
- Cloud Security Posture Management (CSPM)
- Data Protection and Encryption
- Support for 3rd/4th Party Risk Management

### Importance for Financial Services Industry
- Manage security and compliance while managing risk and compliance requirements
- Monitor compliance and create audit reports
- High volume simulations
- Saves times and cost through automation and controls

### SLA Availability Tiers
- Default (Standard): single instance, single data center
- Hardened Configuration: 2 instances (redundancy)
- Regional HA (High Availability): 3 sets on 3 zones
- Multi-Regional HA: 2 or more regions

### IBM Cloud Support Tiers
- Basic: basic protection
- Advanced: prioritized ticket handling (Production Workloads)
- Premium: high value client engagement (Business Critical/Complex Workloads)
   
   
  
## Glossary

### A
- **aaS**: as a Service
- **ACLs**: Access Control Lists
- **API**: Application Programming Interface

### C
- **CDR**: Cloud Detection and Response
- **CIEM**: Cloud Infrastructure Entitlement Management
- **CSP**: Cloud Service Provider
- **CSPM**: Cloud Security Posture Management
- **CWP**: Cloud Workload Protection

### F
- **FI**: Financial Institutions

### H
- **HA**: High Availability
- **HPCS**: Hyper Protect Crypto Services

### I
- **IAM**: Identity Access Management
- **ISV**: Independent Software Vendors

### K
- **KYOK**: Keep Your Own Key

### M
- **MZR**: Multizone Region

### P
- **POP**: Point of Presence

### S
- **SaaS**: Software as a Service
- **SCC**: Security and Compliance Center
- **SI**: Systems Integrator
- **SLAs**: Service Level Agreements
- **SLOs**: Service Level Objectives
- **SLZ**: Secure Landing Zone
- **SOC**: System and Organizational Controls

### T
- **TAM**: Technical Account Manager
- **TLS**: Transport Layer Security

### V
- **VPC**: Virtual Private Cloud
- **VPE**: Virtual Private Endpoint
- **VSI**: Virtual Server Instance
