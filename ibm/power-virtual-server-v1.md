# IBM Power Cloud Virtual Server Course Notes

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


### Key Elements
- Backup Strategies and Methods
- Disaster Recovery
- High Availability
- IBM PowerHA: DR/HA solution for AIX and IBM i
- Geographic logical volume manager (GLVM): AIX DR solution
- Geographic mirroring: IBM i DR solution

### Resiliency Features
- Images: FlashCopy, create master image template, 10 Tb max
- Snapshots: backup LPAR, point-in-time, full copy of the volume or data, can only be used on the LPAR it was taken
- Volume Clones: replica of the volume

### Backup Methods
- AIX Backup Strategies: COS, IBM Storage Protect, Veeam, Compass by Cobalt Iron
- FalconStor StorSafe VTL: virtual tape library (VTL), > 2 Tb, on-premises and cloud
