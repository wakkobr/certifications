# IBM Cloud SAP Course Notes
Learning Plan: [https://cloud-prep.product-acquisition.dal.app.cirrus.ibm.com/training/cloud/cloud-prep/certifications/ibm-cloud-sap]

## Section 1 – Overview

**Keywords:** SAP basics, IBM Cloud, SAP workloads, sizing, SAP HANA, NetWeaver, IaaS, SAPS, Quick Sizer

- SAP Basics: SAP terminology; business vs technical applications; SAP HANA, NetWeaver, S4HANA, BW4HANA, Business One; IBM–SAP 50-year partnership; SAP Notes; IBM Cloud for SAP benefits (agility, scalability, security, AI/analytics integration).
- SAP Workloads on IBM Cloud: SAP components (ABAP/Java, NetWeaver, S4HANA, BW4HANA); SAP-certified IaaS options (Intel bare metal, VPC virtual servers, Power VS, VMware SDDC); supported OS and DB platforms; RISE with SAP and BREAKTHROUGH with IBM.
- Sizing SAP Workloads: SAPS benchmarks; SAP SD benchmark; SAP Quick Sizer; logical design and 99.99 uptime; sizing based on throughput, users, HA/DR, integrated systems; CPU/memory/storage/network considerations.

***

## Section 2 – Architecture

**Keywords:** SAP architecture, IBM Cloud Classic, VPC, Power VS, OLTP, OLAP, scale up, scale out, SAP certification, BYOL, OS support

- Introduction to SAP Architecture: SAP-certified IaaS environments (Classic, VPC, Power VS); bare metal, classic VS, VMware, VPC VS; Power enterprise components; migration steps (size, define landscape, connect, install, license); OLTP vs OLAP; scaling up vs scaling out.
- SAP Certified: Meaning of SAP-certified hardware; SAP Portal and SAP Notes; BYOL for SAP and OS; SAP HANA and NetWeaver only on certified servers; SAP-certified IBM Cloud solutions (Bare Metal, VPC VS, Power VS, VMware Solutions Dedicated); supported OS for HANA and NetWeaver (RHEL, SLES, Windows, AIX).

***

## Section 3 – Compute and Storage

### 3.1 Compute Considerations

**Keywords:** compute profiles, bare metal, VPC VS, Power VS, VMware Dedicated, SAPS, Optane, sizing principles

- Compute Profiles: vCPU/RAM/bandwidth combinations; SAP-certified platforms: Bare Metal Classic, VPC Intel VS, Power VS, VMware Dedicated.
- Bare Metal: Single-tenant; large HANA servers; cheaper storage; backbone replication; Intel Optane Persistent Memory; not recommended for NetWeaver app servers.
- VMware Dedicated: Single-tenant; ~10% capacity overhead; VCS (automated SDDC) vs VSS (manual vSphere); consolidate multiple SAP components; VMware HA for S4HANA.
- Virtual Server for VPC: Cost-effective for small systems; shut down at night/weekends to reduce cost; good for NetWeaver servers.
- Power Systems Virtual Servers: Best for big enterprise workloads; balanced/memory/ultra-high-memory profiles; high SAPS; scale CPU/RAM up to 8x without LPAR restart; HANA only on E980 with Linux.


### 3.2 Storage Considerations

**Keywords:** block storage, file storage, object storage, IOPS, throughput, RTO, storage tiers, custom IOPS, RAID10

- Storage Overview: Units (MB, GB, TB); IOPS as main performance metric; throughput MB/s; RTO depends on IOPS and HANA DB size.
- Provisioning: Storage tiers (0.25/2/4/10 IOPS/GB) vs custom IOPS; examples of 2 TB with 5 or 10 IOPS/GB; custom IOPS higher cost, higher performance for small volumes.
- Platform Storage Options:
    - Bare Metal: Network block/file; 4 or 10 IOPS/GB.
    - VMware: Local SSD in RAID10 for HANA; 10 IOPS/GB network storage for HANA; ≥4 IOPS/GB for NetWeaver.
    - VPC VS: Block Storage Tier 1 (10 IOPS/GB) for HANA; Tier 3 (3 IOPS/GB) default.
    - Power VS: Tier 1 block storage with fiber attach for HANA.


### 3.2 Data Migration

**Keywords:** lift-and-shift, migration, homogeneous, heterogeneous, SWPM, HSR, DMO, backup/restore, HCX, rsync, image conversion

- Migration Approaches:
    - Lift-and-shift (infrastructure change only).
    - Migration with version/config change (application, DB, OS).
- Homogeneous vs Heterogeneous:
    - Homogeneous: same OS/DB; methods include VSI backup/restore, DB backup/restore, fresh build + copy, replication tools.
    - Heterogeneous: different OS/DB; SAP export/import, standard DMO, two-step migration, colocation options.
- Infrastructure-Specific Methods: Rackware RMM for Bare Metal; VMware HCX and lift-and-shift SDDC; Classic to VPC via rsync or image conversion (VMDK/VHD); Power VS via SWPM, HSR, DMO, native backup/restore, Rapid Move, COS; no block-level tools for SAP.


### 3.2 Backup Strategies

**Keywords:** snapshots, VPC, Power VS backups, Backint, HANA Cockpit, HANA Studio, Veeam, Spectrum Protect, COS

- Power VS Backups: Capture/export AIX/IBMi VSIs to COS; images stored as block volumes.
- HANA Backup Methods: Backint interface for online backups with certified tools; offline file-level backups of DB and logs; tools: HANA Cockpit, HANA Studio.
- Snapshots for VPC: Block snapshots via IBM Cloud Backup for VPC; scheduled (daily/weekly/monthly); max 10 TB; data encrypted in transit and at rest in COS; snapshots independent from source volume; incremental after first full.
- Veeam \& Spectrum Protect: Veeam Backup \& Replication on Bare Metal or Classic VS; Backint-based HANA backups; Endurance block storage repository; incremental backups of changed blocks. Spectrum Protect with Backint; BUFFSIZE parameter controls buffer size.

***

## Section 4 – Network and Security

### 4.1 Network Considerations

**Keywords:** VLAN, subnet, Direct Link, Transit Gateway, VPC routing, VPN, latency, throughput

- Networking Basics: Components, topology, performance, latency, ports; segregation with VLANs/subnets; importance for SAP traffic flows.
- Bare Metal \& VMware: Direct Link between Classic and Power VS; PCI/VLAN NICs on Bare Metal; Transit Gateways for frequent data transfer and hybrid workloads.
- Virtual Servers (VPC): VPC routing tables for local VPC-to-VPC flows; VPN gateway, Internet gateways; BYOIP process starts with creating a VPC.
- Power VS: Connectivity with IBM Cloud Infrastructure via Direct Link; considerations for hybrid network design.


### 4.2 Security Considerations

**Keywords:** network isolation, firewalls, ACLs, security groups, HANA zones, BYOIP, encryption, KMS, Hyper Protect Crypto, Endurance encryption, edge clusters

- Security Concerns: Network isolation for SAP systems; best practices in VPC, Classic, VMware; limiting access to HANA; IPs for security; firewall rules and ports between HANA and NetWeaver; ACLs and security groups for subnet protection.
- Security at the Edge: Edge computing; edge clusters (Kubernetes-based, scalable); benefits (scalability, faster insight, secure communication, availability); VMware Edge Services Cluster option; IBM Security Services for SAP (consulting, best practices, risk mitigation).
- Data Encryption Options:
    - IBM-managed encryption: default for IBM Block Storage; IBM Cloud Endurance native encryption for full NFS volume.
    - Client-managed encryption: requires Key Management Service; BYOK/KYOK.
    - Hyper Protect Crypto Service: strong assurance no one can access client SAP data.
    - VMware encryption options.

***

## Section 5 – Architecture Patterns

**Keywords:** high availability, disaster recovery, system tiering, NetWeaver, SPOF, WSFC, SAP HANA HSR, latency, compliance, STAR registry, automation, Schematics, Terraform, Ansible, bastion, SAP kits

### 5.1.1 High Availability

- System Tiering: Two-tier, three-tier, multi-tier designs; HA and DR separation; NetWeaver AS variants (ABAP, Java, Dual Stack).
- NetWeaver HA: SPOFs (DBMS, central services); failover clustering (e.g. WSFC) to protect SPOFs; shared storage via NFS and mount points; VMware vMotion to reduce planned downtime.
- HANA HA/DR: OS add-ons (RHEL, SLES) for HA; HANA System Replication (synchronous vs asynchronous; delta shipping vs log replay); standby DB and storage; latency KPIs (RTT); S4HANA scale-out up to 4 nodes; BW4HANA scale-out for analytics.


### 5.1.2 Regulatory Requirements

- Compliance Programs: Global, government, industry, regional; examples: GDPR, EBA, FFIEC, FISC, GxP, HIPAA, HYTRUST.
- STAR Registry: Options IBM Cloud Infrastructure and IBM Cloud Platform; mapping of SAP deployments to appropriate compliance programs.
- Program Types: Regional vs industry programs for SAP on IBM Cloud; cross-over for government deployments requiring both global and regional compliance.


### 5.1.3 Automation

- Automation Tools: IBM Cloud Schematics; Terraform; Ansible; Red Hat OpenShift and ROKS; Operators, Helm; VPC VSIs and Power VS resources.
- Bastion Server: Jump server for remote installation; used for SAP VPC automated solutions; runs Terraform `remote-exec` and Ansible playbooks.
- SAP Kits \& Terraform: SAP kits as grouped products; GitHub Terraform/Ansible repositories per SAP solution; steps: adjust variables (`terraform.tfvars`, `input.auto.tfvars`), plan, verify, apply; do not modify resources via Dashboard.
