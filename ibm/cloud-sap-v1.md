# IBM Cloud SAP Course Notes
Learning Plan: [https://cloud-prep.product-acquisition.dal.app.cirrus.ibm.com/training/cloud/cloud-prep/certifications/ibm-cloud-sap]

## Section 1 – Overview (SAP Basics)

### Keywords ###
SAP basics, IBM–SAP partnership, SAP Notes, SAP workloads, IaaS, SAP S/4HANA, SAP BW/4HANA, SAP Business One, SAPS, Quick Sizer, sizing

### Key concepts ###
- IBM and SAP have a 50+ year partnership; IBM Cloud for SAP provides SAP‑certified infrastructure for public and hybrid deployments, requiring client SAP licenses (S‑user ID) and an IBM Cloud account.
- SAP workloads include ABAP/Java on SAP NetWeaver and ABAP on SAP S/4HANA, running business apps like S/4HANA (ERP), BW/4HANA (EDW), and Business One on certified IBM Cloud options.
- Benefits of SAP on IBM Cloud include enterprise-ready IaaS, flexible scale, multiple security-centric options, AI/analytics integration, and higher resiliency possibilities.
- SAP Notes (accessed with S‑user ID) provide up-to-date implementation and operations guidance for SAP environments.
- SAPS is the standard benchmark for transactional throughput; SAP Quick Sizer translates business requirements into CPU, memory, and storage needs, considering throughput, users, HA/DR, and integrated apps.

## Section 2 – Architecture

### Keywords ###
SAP architecture, Classic, VPC, Power VS, OLTP, OLAP, scale up, scale out, SAP certification, BYOL, OS support, SAP-certified, SAP HANA, SAP NetWeaver, BYOL, Virtual Server for VPC, Bare Metal, VMware Dedicated, Power VS, OS support

### Key concepts ###
- SAP on IBM Cloud runs on three main certified compute environments: IBM Cloud Classic (bare metal, VMware), IBM Cloud VPC (Virtual Servers for VPC), and IBM Power Systems Virtual Servers.
- OLTP focuses on fast, small, balanced read/write transactions; OLAP targets long-running, read‑intensive analytical queries, influencing platform and sizing choices.
- Scaling up adds resources to a server; scaling out distributes workloads across multiple servers, critical for performance, HA, and large HANA/BW systems.

### SAP Certified Infrastructure \& Licensing
- Only SAP‑certified server models are supported for SAP HANA and SAP NetWeaver; clients use the SAP Portal and SAP Notes to verify certified models and recommendations.
- SAP HANA licenses are BYOL only; OS licensing differs by platform (VPC VSIs and Power VS via IBM Cloud, VMware via BYOL, Classic bare metal via BYOL or IBM Cloud).
- Certified compute options: Bare Metal Servers, Virtual Servers for VPC, IBM Power Virtual Servers, and VMware Solutions Dedicated (VSS/VCS), with specific HANA/NetWeaver OS lists (RHEL/SLES/Windows/AIX).

## Section 3 – Compute and Storage

###Keywords###
Compute profiles, Bare Metal, Virtual Server for VPC, VMware Dedicated, Power VS, SAPS, HANA memory limits, block/file/object storage, IOPS, RTO, storage tiers, migration, backup, Veeam, Spectrum Protect, lift-and-shift, homogeneous migration, heterogeneous migration, SWPM, HSR, DMO, Rackware RMM, HCX, rsync, image conversion, COS, snapshots, VPC backup, COS, Power VS VSI backup, HANA Backint, HANA Cockpit, HANA Studio, Veeam, Spectrum Protect

### Compute Considerations
- A compute profile defines vCPU, RAM, and bandwidth; SAP‑certified options include Classic Bare Metal, Virtual Servers for VPC, Power VS, and VMware Solutions Dedicated.
- Bare Metal is single-tenant with fixed RAM/CPU “appliance” profiles, suited to large HANA nodes (with optional Intel Optane); Power VS (E980/S922) supports ultra‑high memory and dynamic scaling up to 8× without LPAR restart.
- Virtual Server for VPC is cost‑effective for smaller systems and NetWeaver, allowing workloads to be shut down off‑hours; VMware Dedicated runs multiple SAP components per bare metal with ~10% capacity overhead from hypervisor.
- S/4HANA and BW/4HANA maximum scale‑up/scale‑out memory differs per platform; Power VS provides the highest SAPS benchmark in the comparison table.

### Storage Overview
- Main storage types are block, file, and object; key metrics are capacity (MB/GB/TB), IOPS, and throughput (MB/s, GB/s), which directly affect SAP HANA RTO.
- RTO for SAP HANA is driven by storage IOPS/throughput and HANA database size; mandatory HANA storage layouts must be followed on certified hardware.
- Block/file storage IOPS can use storage tiers (e.g., 0.25, 2, 4, 10 IOPS/GB) or custom IOPS; higher-cost custom IOPS support high performance on smaller volumes.
- Classic Bare Metal and VMware use local SSD (RAID10) plus network storage at 4 or 10 IOPS/GB; VPC supports Tier 1 (10 IOPS/GB, mission‑critical/HANA) and Tier 3 (3 IOPS/GB) block storage; Power VS uses Tier 1 with fibre‑attached storage for HANA.

### Data Migration
- Lift‑and‑shift moves workloads “as‑is” at infrastructure level; migration changes application, database, or OS configuration or version.
- Homogeneous migration keeps OS/database types; uses VSI or DB backup/restore, fresh build \& copy, DB replication or CPD tools.
- Heterogeneous migration changes OS and/or DB; uses SAP export/import, standard DMO, two‑step migration, or colocation options.
- Classic Bare Metal migration can use Rackware RMM; VMware NSX‑V to NSX‑T migration can use HCX or lift‑and‑shift vCenter; Classic‑to‑VPC uses rsync or image conversion (VMDK/VHD to VPC image, with Windows env vars).
- Power VS migrations use SWPM, HSR, DMO, DB native backup/restore, IBM Rapid Move, and other SAP‑approved tools; SAP forbids block‑level storage migration tools for SAP DBs.

### Backup Strategies
- VPC block storage snapshots capture point‑in‑time volume copies, stored encrypted in COS; they can be scheduled (daily/weekly/monthly) and are independent of source volumes (max 10 TB per snapshot).
- Power VS AIX/IBM i VSIs can be captured and exported to COS; SAP HANA backups use Backint‑based online backups or offline file‑level backups of DB and logs.
- HANA Cockpit (web admin/monitoring) and HANA Studio (Eclipse‑based legacy tool) manage backup and recovery operations.
- Veeam Backup \& Replication with the HANA plug‑in performs Backint‑based backups to IBM Cloud repositories on Bare Metal or Classic VSI with Endurance block storage.
- IBM Spectrum Protect for SAP HANA integrates via Backint, using BUFFSIZE to tune transfer buffers and supporting full/incremental backups and redo log protection.

## Section 4 – Network and Security

### Keywords ###
topology, latency, Direct Link, VPN, Transit Gateway, VLANs, VPC networking, security groups, ACLs, bastion host, HANA zones, firewalls, Web Dispatcher, SAProuter, edge clusters, IBM Security Services, encryption, BYOK, KYOK, edge computing, edge cluster, NSX‑T, VSI edge cluster, IBM Security Services for SAP, data‑at‑rest encryption, IBM‑managed, client‑managed, Hyper Protect Crypto Services, Key Protect, BYOK, KYOK, VMware encryption

### Networking Basics
- Key design aspects: topology, small traditional SAP traffic volumes, 10 Gbps recommended between app servers and HANA, and RTT‑based latency testing for HA/DR scenarios.
- Classic connectivity: SSL VPN, IPsec VPN, and Direct Link for enterprise low‑latency links.
- VPC connectivity: floating IPs and public gateways for internet access, VPC IPsec VPN, and Direct Link 2.0 (Connect/Dedicated) for hybrid connectivity.
- Power VS uses private VLANs plus Direct Link/IPsec/DMZ firewalls for communication with Classic, VPC, and on‑premises.
- VLANs and subnets segregate traffic in Classic; VMware NSX VXLAN overlays support multiple subnet types (primary/portable/static/global).
- VPC uses zones and subnets (CIDR‑based) with routing tables, security groups (allow‑only), ACLs, and public/private load balancers.

### Security Concerns
- Data breaches can arise from client or cloud provider configurations; SAP IaaS deployments require isolated, secure private networks.
- VPC isolation is enforced via hypervisors, VNIs, VRFs, and MPLS; security groups and ACLs control inbound/outbound traffic per instance or subnet.
- A bastion host (jump server) restricts SSH/ICMP access to internal resources from the public internet.
- SAP HANA network security uses separate client, internal, and storage zones; only required channels reach HANA, with recommended 10 Gbps throughput between app servers and HANA.

### Security Tools
- Firewalls enforce port‑level access (e.g., Web Dispatcher HTTPS port) and protect zones; ports identify target services.
- BYOIP/CIDR allows custom subnets; creating the VPC is the first step before BYOIP.
- SAProuter and SAP Web Dispatcher act as application‑layer gateways, typically in public subnets; they filter SAP traffic and front HTTPS access into SAP systems.
- IBM Cloud Internet Services adds additional protection for domains/URLs and traffic patterns.

### Security at the Edge
- Edge computing brings applications closer to data sources via devices, edge servers, and edge clouds that must meet security and compliance requirements.
- Edge clusters are Kubernetes‑based, scalable (tens–thousands of clusters, thousands–millions of devices) with benefits like secure communication, high availability, and faster insights.
- VMware NSX‑T edge clusters host network edge/firewall components; when ordering VMware Solutions Dedicated, the Edge Services Cluster option enables this.
- IBM Security Services for SAP offers automated monitoring and protection, near real‑time preventative/detective/corrective controls, and consulting/best practices for secure SAP workloads.

### Data Encryption Options
- IBM‑managed encryption is default for block/file storage and COS objects; Endurance native encryption uses IBM‑managed keys to encrypt full NFS volumes.
- Client‑managed encryption lets customers bring/generate keys via a KMS; provisioning a KMS is required before creating client‑encrypted VPC volumes.
- Hyper Protect Crypto Services provides hardware‑backed key control and KYOK assurance that no one else can access SAP data; access uses private service endpoints.
- VMware environments let clients manage their own encryption stack (e.g., LUKS, file‑level, or third‑party) on top of IBM Cloud storage.

## Section 5 – Architecture Patterns

### Keywords ###
HA, DR, two‑tier, three‑tier, multi‑tier, SAP NetWeaver HA, SAP HANA HA/DR, regulatory requirements, automation, Terraform, Schematics, Ansible

### High Availability
- SAP system tiering: two‑tier (app+DB on one host), three‑tier (separate app and DB), and multi‑tier where HA/DR further separates components with redundancy.
- SAP NetWeaver AS can be ABAP, Java, or Dual Stack and requires HA patterns that differ by Classic vs Power infrastructure.
- HANA/S/4HANA/BW/4HANA HA/DR designs combine HANA System Replication, clustered failover, multiple availability zones/regions, and correctly sized standby systems.

### Automation
- IBM provides Terraform + Ansible automation to build SAP landscapes on VPC, with a bastion server as a prerequisite and per‑solution folders in the IBM GitHub repository.
- Typical Terraform workflow: set input parameters (or terraform.tfvars), run `terraform plan`, validate resources, then `terraform apply`; renames are done by editing `input.auto.tfvars` and re‑planning/applying (not via UI).

## Section 6 – Business Opportunities

### Keywords ###
data center exit, lift‑and‑shift, fresh implementation, mergers/acquisitions, carve‑out, ECC to S/4HANA, Brownfield, Greenfield, Bluefield, IBM Rapid Move, CAPEX to OPEX, hardware refresh

### Key concepts ###
- Key business drivers for SAP on IBM Cloud include data center exit, hardware refresh, fresh SAP implementation, and complex M\&A/spinoff scenarios.
- Lift‑and‑shift data center exits move privately hosted SAP workloads quickly to modern hardware, shifting from CAPEX to OPEX and enabling capacity expansion.
- S/4HANA migrations: Brownfield (full ECC conversion), Greenfield (new implementation), Bluefield (selective migration), and IBM Rapid Move (hybrid “pick‑and‑choose” acceleration).
- Bluefield/Rapid Move approaches are recommended for ECC→S/4HANA on IBM Cloud, especially for selective carve‑outs in demergers or acquisitions.
