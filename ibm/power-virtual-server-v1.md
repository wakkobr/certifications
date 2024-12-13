# IBM Power Cloud Virtual Server Course Notes
Learning Plan: https://yourlearning.ibm.com/activity/PLAN-A7B2BFED5813?focuslmsId=ITS-DL70544G

## Module 1: Power Virtual Server Overview

### Keywords
CapEx, OpEx, HADR, AIX, IBM i, MMA, IaaS, In-Core, Quantum Safe

### Key Elements
- CapEx to OpEx
- HA/DR (High Availability / Disaster Recover)
- AI in-core (MMA - Matrix Math Accelerator)
- Supported: AIX, IBM i, Linux (RHEL, SUSE)
  
### Operational Value (Oracle, SAP, IBM i)  
- Expand SAP clients to Power Virtual Server  
- Efficiently Scale Data-Intensive Workloads  
- Create a Backup/Restore Solution

### Supported Databases
- IBM DB2
- Oracle
- Postgre SQL
- MongoDB
- IBM Datastage
- IBM Cognos

### IaaS Options
- IBM Power: Business continuity and agility; end-to-end security
- Power Private Cloud with Dynamic Capacity: pay-as-you-go, cloud on premises with monitoring
- Power Virtual Server with IBM Cloud: VMaaS, consistent archtecture, cloud services, OpenShift

### Powe4 Virtual Server Use Cases
- Data Center Strategy Optimization
- Business Continuity Planning
- Modernize
- Improve Operational Cost

## Module 2: Power Virtual Server Architecture and Technology

### Keywords
RISC Processor, PowerVC, shared Storage Pool

### Key Elements
- Cores (8 cores, IBM i only 4 cores)
- RISC: Wide, high speed data pathways and multi-threading (vs x86)
- Power Virtualization Stack: PowerVC
- Virtualization without Limits: PowerVM, Power Hypervisor (PHYP), isolated VMs
- PowerVM: interface between VMs and physical hardware
- Virtual I/O Server (VIOS): many VMs, reduce costs, share storage pools
- PowerSC (Security and Compliance): role-based access, logs, automation, monitoring
- Matrix Math Accelerator (MMA): AI 'in-place', directly in the processor, accelerate inferencing

### Operating Systems
- Linux: RHEL, SUSE
- AIX: database systems, Oracle workloads
- IBM i: enhanced security - object based, business resiience, object-base addressing, virtualization, RTO Zero with DB2 Mirror
- SAP HANA: lower TCO - few cores to run workloads, consolidate servers, smaller footprint; RHEL and SLES

### Value Proposition of Shared Processor Pools (SPP)
- Oracle Licensing Optimization: reduce licenses by limiting uncapped partitions/processors; can add licenses as needed 
- Reserve Capacity: capped price for later, saving OS licensing and memory costs

### Servers
- Scale Out: S922 and S1022 (4 cores limit on IBM i)
- Enterprise: E980 and E1080

## Module 3: Use Cases and Solutions for Power Virtual Server

### Keywords
Modernize, BCP, Scale up/down, spin up/down, footprint, IBM Cloud Object Storage

### Key Elements

### Four Key Use Cases
- Data Center Strategy Optimization
- Business Continuity Planning
- Modernize
- Improve Operational Cost

#### Data Center Strategy Optimization
- SAP HANA on Power: superior core performance, BYOL
- Oracle on Power: CPU sharing (SPP), can escalate
- Red Hat on Power: OpenShift, modernize, automate, secure, reduce cost by reduce server, use existing hardware
- IBM i: mission critical on cloud - reliability, security, performance; scalability and agility, no impact on workloads

#### Modernize
- Helping Clients Extend the Usefulness of Existing Infrastructure
- Mission-critical workloads: extend on-premises to cloud, connect to IBM Cloud (API)
- Software and hardware EoL/EoS: test new things, scale/spin up/down
- Develop, upgrade and test software: pay-as-you-use
- Deploying containers: containers or VMs, automation tools, muiticloud management

#### Common Business Continuity Planning Use Cases
- High Availability: shared resources
- Disaster Recovery
- Backup: many options (Compass - AIX, Linux; Cloud Object Storage; FalconStor; Veeam - AIX)

## Module 4: Business Continuity Planning for Power Virtual Server

### Keywords
HADR, FlashCopy, GLVM, Geographic mirroring, Snapshot, Compass, PowerHA, GRS, Image Captures, ROHA

### Key Elements
- Backup Strategies and Methods
- Disaster Recovery: Recovery point objectives (RPOs) and recovery time objectives (RTOs) metrics
- High Availability
- IBM PowerHA: DR/HA solution for AIX and IBM i
- Geographic logical volume manager (GLVM): AIX DR solution over TCP/IP
- Geographic mirroring: IBM i DR solution, synchronous or asynchronous system replication
- Storage Replication: Global Replication Service (GRS) is IBM Cloud service, asynchronous

### Resiliency Features
- Images: FlashCopy, create master image template, 10 Tb max
- Snapshots: backup LPAR, point-in-time, full copy of the volume or data, can only be used on the LPAR it was taken
- Volume Clones: replica of the volume

### Backup Methods
- AIX Backup Strategies: COS, IBM Storage Protect, Veeam, Compass by Cobalt Iron
- FalconStor StorSafe VTL: IBM i, virtual tape library (VTL), > 2 Tb, on-premises and cloud

### IBM PowerHA
- Disaster and HA solution forAIX and IBM i
- Integrate with GLVM and Geographic mirroring
- Supports resource optimization high availability (ROHA): automatically adjust CPUs and memory resources
- Standard & Enterprise (uses Geographic mirroring) editions

## Module 5: Migration Strategies for Power Virtual Server

### Keywords
Open Virtualization Appliance (OVA), FalconStor Storsage VTL, BRMS, Aspera (FASP)

### Key Elements
- OVA Images: needs access to PowerVC
- PowerVC: virtualization management and cloud deployment tool
- OVA image captured -> transported IBM COS -> imported Power Virtual Server -> new instance created

### Migration Transfer Tools
- TCP/IP: FTP, SFTP or SCP (Secure Copy Protocol)
- Aspera-based Transfers to COS: FASP (Fast And Secure Protocol)

### Migration Challenges and Considerations
- Downtime Requirements
- Workload
- High Availability
- Network Options
- Replication or Mirroring Options
- Familiarity and Comfort with Tools and Processes

### Storage Options
- IBM COS: Max 10 Tb
- Seagate Lyve: transfers from on-premises to COS, then restores to Power Virtual Server
- FalconStor Storsafe VTL

### AIX
- System Backup (mksysb and savevg) OR Application Backup
- FTP/SFTP/SCP, IBM COS, Aspera OR Seagate Lyve
- Restore rootvg (mksysb) OR Restore volume group (restvg)
- Replication Strategy: Host/OS (PowerHA with GLVM), Application (Oracle Data Guard, Oracle GoldenGate, DB2 HADR), 3rd Party (Double-Take, MIMIX)

### Optimal OVA Image Size for Data Transfer
- IBM COS: Less than 2 Tb
- Direct Transfer: over 2 Tb
- FalconStor StoreSafe VTL: over 2 Tb

### IBM i
- Geographic mirroring: migrate from onpremises to Power Virtual Server in IBM Cloud
- Replication Strategy: Host/OS (PowerHA with geographic mirroring), Application, 3rd Party (Maxava, MIMIX, Rocket iCluster, RobotHA)
- BRMS: used to manage backup and recovery operations, automated backup and recovery management

## Module 6: Power Virtual Server Options

### Keywords
IOPS, GDPR, SOC, Storage Pools, VLAN, VIOS, HPCS, Key Protect

### Key Elements
- Input/output operation per second (IOPS)
- Observability and Monitoring Options: can monitor platform metrics with IBM Cloud Monitoring dashboards
- Storage Pools (SP): affinity (same SP), anti-affinity (diff SP), auto-select
- Flexible IOPS: more IOPS, higher the cost
- Platform Metrics
- Activity Tracker
- IBM Cloud Monitoring Limitations: 5 minutes, IPv6, memory display at 100%

### Storage Options
- Tier 0: up to 25 IOPS/Gb; ideal for high performance DBs (SAP HANA, Oracle) or workloads that benefit from higher storage performance
- Tier 1: up to 10 IOPS/Gb; ideal for prod workloads with defined performance characteristics
- Tier 3: up to 3 IOPS/Gb; ideal for non-production workloads
- Fixed 5000 IOPS:  ideal where the highest performance is required for meeting specific workloads KPIs

### Security for Power Virtual Server
- IBM manages infrastructure (hypervisor and below)
- Client manages OS
- VLAN isolation: each client environment and subnet is deployed in a separate VLAN (Network Segregation/Segmentation

### Integrating Power Virtual Server with IBM Cloud Key Management Services
- IBM Cloud Hyper Protect Crypto Services (HPCS): dedicated key management service and hardware security module (HSM) in IBM Cloud
- IBM Key Protect: multi-tenant encryption solution, allows data to be secured and encrypted stored in IBM Cloud

### Power Virtual Server Regulatory Compliance
- GDPR
- SOC (System Organization Controls)
- Payment Card Industry (PCI) data security standards

## Module 7: Networking Options for Power Virtual Server

### Keywords
Virtual Router Appliance (VRA), IPSec VPN, Transit Gateway, Direct Link

### Key Elements
- Workspace, Subnet & Gateway Appliances
- Transit Gateway
- Generic Routing Encapsulation (GRE): encapsulate data packets; traverse networks
- Power Edge Router (PER): high performance router, improved UX, less complexity and cost
- PER is replacing IBM Cloud Connections and Direct Link
- PER connetion and transit gateway integrate IBM Power Virtual Server and IBM Cloud
- Direct Link: connect on-premise/other cloud to IBM Cloud; highest speed

### Power Virtual Server Networking Basics
- Workspace: container for all instances; administrative unit
- Subnets: will use for communication, creates a VLAN
- Gateway Appliances: provide clients control over network traffic; increased security; policies and rules

### Transit Gateway
- Allows clients to interconnect various parts of IBM Cloud
- Can also connect external resources in other clouds/on-premises via Direct Link

### Connectivity Patterns
- Limited Default Public Access over the Internet: temp access, no prod
- On-Premises to Power Virtual Server using Direct Link and Transit Gateway: with or without Client-Managed Gateway
- Site-to-Site Network Connection with IBM Cloud VPN Service
- Site-to-Site Network Connection on Client-Managed Gateway in Classic
- Site-to-Site Network Connection on Client-Managed Gateway (VPC and Bring Your Own License - BYOL)
