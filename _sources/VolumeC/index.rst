Build Implementation Instructions
=====================================================

.. include:: /_publication_note.rst

.. toctree::
   :maxdepth: 1
   :titlesonly:
   :glob:
   :hidden:
   
   HowTo-E1B1.rst
   HowTo-E2B1.rst
   HowTo-E3B1.rst
   HowTo-E1B2.rst
   HowTo-E3B2.rst
   HowTo-E1B3.rst
   HowTo-E2B3.rst
   HowTo-E3B3.rst
   HowTo-E4B3.rst
   HowTo-E1B4.rst
   HowTo-E2B4.rst
   HowTo-E3B4.rst
   HowTo-E4B4.rst
   HowTo-E1B5.rst
   HowTo-E2B5.rst
   HowTo-E3B5.rst
   HowTo-E1B6.rst
   Hardening.rst

The following section of this guide shows information technology (IT) professionals and security engineers how we implemented numerous example zero trust architecture (ZTA) solutions. We cover all of the products employed in this reference design.

*Note: This is not comprehensive documentation. There are many possible service and security configurations for these products that are out of scope for these demonstrations.*

Build Overview
--------------

This NIST Cybersecurity Practice Guide addresses the challenge of using standards-based protocols and available technologies to build a ZTA. In our lab at the NCCoE and using our collaborators' cloud infrastructure, we plan to implement and demonstrate a variety of builds that serve as example ZTA solutions, each of which is designed to dynamically and securely manage access to resources across a set of use cases that a medium or large enterprise might typically deploy. Our plan is to implement these builds in a series of phases, starting with a baseline enterprise architecture that represents the typical legacy components that an enterprise might start with when deciding to begin adding zero trust capabilities.

We began with builds for enhanced identity governance (EIG) that were restricted to a limited set of capabilities. We call these *EIG crawl phase builds*. The central capabilities of these builds are identity, credential, and access management (ICAM) and endpoint protection. In particular, these EIG crawl phase builds do not include separate, centralized policy engine (PE) or policy administration (PA) components. Instead, these initial EIG crawl phase builds rely upon the PE and PA capabilities provided by their ICAM components. We did not perform an EIG walk phase. After completing the EIG crawl phase builds, we enhanced these implementations by adding specialized PE and PA components, device discovery, and cloud-based resources in the EIG run phase. Next, we began the software-defined perimeter (SDP), microsegmentation, and secure access service edge (SASE) phase of the project. As its name suggests, this phase involved integrating ZTA components that support one or more of the SDP, microsegmentation, and SASE deployment models. It also integrated additional supporting components and features to provide an increasingly rich set of ZTA functionalities.

This practice guide provides instructions for reproducing the builds that we have implemented so far, as listed in Table 1:

**Table 1 - Implemented ZTA Builds and their Policy Engines and Architecture Types**

+-------+----------------------------------------------------------------------------------+------------------------------------+
| Build | Policy Engines                                                                   | ZTA Architecture Instantiated      |
+=======+==================================================================================+====================================+
| E1B1  | Okta Identity Cloud                                                              | EIG Crawl                          |
|       |                                                                                  |                                    |
|       | Ivanti Access ZSO                                                                |                                    |
+-------+----------------------------------------------------------------------------------+------------------------------------+
| E2B1  | Ping Identity Ping Federate                                                      | EIG Crawl                          |
+-------+----------------------------------------------------------------------------------+------------------------------------+
| E3B1  | Azure AD (Conditional Access, later renamed Entra Conditional Access)            | EIG Crawl                          |
+-------+----------------------------------------------------------------------------------+------------------------------------+
| E1B2  | Zscaler ZPA Central Authority (CA)                                               | EIG Run                            |
+-------+----------------------------------------------------------------------------------+------------------------------------+
| E3B2  | Microsoft Azure AD (Conditional Access, later renamed Entra Conditional Access)  | EIG Run                            |
|       |                                                                                  |                                    |
|       | Microsoft Intune                                                                 |                                    |
|       |                                                                                  |                                    |
|       | Forescout eyeControl                                                             |                                    |
|       |                                                                                  |                                    |
|       | Forescout eyeExtend                                                              |                                    |
+-------+----------------------------------------------------------------------------------+------------------------------------+
| E1B3  | Zscaler ZPA Central Authority (CA)                                               | SDP                                |
+-------+----------------------------------------------------------------------------------+------------------------------------+
| E2B3  | Ping Identity PingFederate                                                       | Microsegmentation                  |
|       |                                                                                  |                                    |
|       | Cisco ISE                                                                        |                                    |
|       |                                                                                  |                                    |
|       | Cisco Secure Workload                                                            |                                    |
+-------+----------------------------------------------------------------------------------+------------------------------------+
| E3B3  | Microsoft Azure AD (Conditional Access, later renamed Entra Conditional Access)  | SDP and Microsegmentation          |
|       |                                                                                  |                                    |
|       | Microsoft Intune                                                                 |                                    |
|       |                                                                                  |                                    |
|       | Microsoft Sentinel                                                               |                                    |
|       |                                                                                  |                                    |
|       | Forescout eyeControl                                                             |                                    |
|       |                                                                                  |                                    |
|       | Forescout eyeExtend                                                              |                                    |
+-------+----------------------------------------------------------------------------------+------------------------------------+
| E4B3  | IBM Security Verify                                                              | EIG Run                            |
+-------+----------------------------------------------------------------------------------+------------------------------------+
| E1B4  | Appgate SDP Controller                                                           | SDP                                |
+-------+----------------------------------------------------------------------------------+------------------------------------+
| E2B4  | Symantec Cloud Secure Web Gateway (Cloud SWG)                                    | SDP and SASE                       |
|       |                                                                                  |                                    |
|       | Symantec ZTNA                                                                    |                                    |
|       |                                                                                  |                                    |
|       | Symantec Cloud Access Security Broker (CASB)                                     |                                    |
+-------+----------------------------------------------------------------------------------+------------------------------------+
| E3B4  | F5 BIG-IP                                                                        | SDP                                |
|       |                                                                                  |                                    |
|       | F5 NGINX Plus                                                                    |                                    |
|       |                                                                                  |                                    |
|       | Forescout eyeControl                                                             |                                    |
|       |                                                                                  |                                    |
|       | Forescout eyeExtend                                                              |                                    |
+-------+----------------------------------------------------------------------------------+------------------------------------+
| E4B4  | VMware Workspace ONE Access                                                      | SDP, Microsegmentation, and EIG    |
|       |                                                                                  |                                    |
|       | VMware Unified Access Gateway (UAG)                                              |                                    |
|       |                                                                                  |                                    |
|       | VMware NSX-T                                                                     |                                    |
+-------+----------------------------------------------------------------------------------+------------------------------------+
| E1B5  | PAN NGFW                                                                         | SASE and Microsegmentation         |
|       |                                                                                  |                                    |
|       | PAN Prisma Access                                                                |                                    |
+-------+----------------------------------------------------------------------------------+------------------------------------+
| E2B5  | Lookout SSE                                                                      | SDP and SASE                       |
|       |                                                                                  |                                    |
|       | Okta Identity Clouds                                                             |                                    |
+-------+----------------------------------------------------------------------------------+------------------------------------+
| E3B5  | Microsoft Entra Conditional Access (formerly called Azure AD Conditional Access) | SDP and SASE                       |
|       |                                                                                  |                                    |
|       | Microsoft Security Service Edge                                                  |                                    |
+-------+----------------------------------------------------------------------------------+------------------------------------+
| E1B6  | Ivanti Neurons for Zero Trust Access                                             | SDP and Microsegmentation          |
+-------+----------------------------------------------------------------------------------+------------------------------------+

The NCCoE worked with members of the ZTA community of interest to develop a diverse but non-comprehensive set of use cases and scenarios to demonstrate the capabilities of the builds. The use cases are summarized in :ref:`Functional Demonstrations`.

EIG Crawl Phase Build Features
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

A general ZTA reference design is depicted in :ref:`Figure 1 - General ZTA Reference Architecture<ArchitectureFigure1>`. It consists of ZTA core components: a policy decision point (PDP), which includes both a PE and a PA, and one or more policy enforcement points (PEPs); and ZTA functional components for ICAM, security analytics, data security, and endpoint security. The EIG crawl phase builds differ from this reference design insofar as they do not include separate, dedicated PDP components. Their ICAM component serves as their PDP, and they include very limited data security and security analytics functionality. These limitations were intentionally placed on the initial builds in an attempt to demonstrate the ZTA functionality that an enterprise that currently has ICAM and endpoint protection solutions deployed will be able to support without having to add additional ZTA-specific capabilities.

Each EIG crawl phase build is instantiated in a unique way, depending on the equipment used and the capabilities supported. Briefly, the three builds are as follows:

-  E1B1 uses products from IBM, Ivanti, Mandiant, Okta, Radiant Logic, SailPoint, Tenable, and Zimperium. Certificates from DigiCert are also used.

-  E2B1 uses products from Cisco Systems, IBM, Mandiant, Palo Alto Networks, Ping Identity, Radiant Logic, SailPoint, and Tenable. Certificates from DigiCert are also used.

-  E3B1 uses products from F5, Forescout, Lookout, Mandiant, Microsoft, Palo Alto Networks, PC Matic, and Tenable. Certificates from DigiCert are also used.

EIG Run Phase Build Features
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The EIG run phase, as its name suggests, builds upon the EIG crawl phase architecture. The EIG run phase no longer imposes the requirement that the PE and PA components must be provided by the ICAM products used in the build. It also adds capabilities to the EIG crawl phase. In addition to protecting access to resources that are located on-premises, the run phase also protects access to some resources that are hosted in the cloud. The EIG run phase includes a device discovery capability, which is performed as part of the baseline. In addition to monitoring and alerting when new devices are detected, enforcement can be enabled to deny access to devices that are not compliant. The run phase also includes the capability to establish a tunnel between the requesting endpoint and the resource being accessed over which access to the resource can be brokered.

Each EIG run phase build is instantiated in a unique way, depending on the equipment used and the capabilities supported. Briefly, the three builds are as follows:

-  E1B2 uses products from Amazon Web Services, IBM, Ivanti, Mandiant, Okta, Radiant Logic, SailPoint, Tenable, and Zscaler. Certificates from DigiCert are also used.

-  E3B2 uses products from F5, Forescout, Mandiant, Microsoft, Palo Alto Networks, PC Matic, and Tenable. Certificates from DigiCert are also used.

-  E4B3 uses products from IBM, Mandiant, Palo Alto Networks, Tenable, and VMware. Certificates from DigiCert are also used.

SDP, Microsegmentation, and SASE Phase Build Features
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The SDP, microsegmentation, and SASE phase builds are based on the general ZTA reference design that is depicted in :ref:`Figure 1 - General ZTA Reference Architecture<ArchitectureFigure1>`. It consists of ZTA core components: a PDP, which includes both a PE and a PA; one or more PEPs; and ZTA functional components for ICAM, security analytics, data security, and endpoint security. The builds implemented in the SDP, microsegmentation, and SASE phase of the project each deploy elements of one or more of the SDP, microsegmentation, or SASE deployments.

Each SDP, microsegmentation, and SASE phase build is instantiated in a unique way, depending on the equipment used and the capabilities supported. Briefly, the eleven builds are as follows:

-  E1B3 uses all of the same products and technologies as E1B2, so there is no separate section for E1B3 in this document.

-  E2B3 uses products from Cisco Systems, IBM, Mandiant, Palo Alto Networks, Ping Identity, Radiant Logic, SailPoint, Tenable, and VMware. Certificates from DigiCert are also used.

-  E3B3 uses products from F5, Forescout, Mandiant, Microsoft, Palo Alto Networks, PC Matic, and Tenable. Certificates from DigiCert are also used.

-  E1B4 uses products from Amazon Web Services, Appgate, IBM, Ivanti, Mandiant, Okta, Radiant Logic, SailPoint, Tenable, and Zimperium. Certificates from DigiCert are also used.

-  E2B4 uses products from Google Cloud, IBM, Mandiant, Okta, Radiant Logic, SailPoint, Symantec by Broadcom, Tenable, and VMware. Certificates from DigiCert are also used.

-  E3B4 uses products from F5, Forescout, Mandiant, Microsoft, Palo Alto Networks, and Tenable. Certificates from DigiCert are also used.

-  E4B4 uses products from IBM, Mandiant, Tenable, and VMware. Certificates from DigiCert are also used.

-  E1B5 uses products from Amazon Web Services, IBM, Mandiant, Okta, Palo Alto Networks, Radiant Logic, SailPoint, and Tenable. Certificates from DigiCert are also used.

-  E2B5 uses products from Google Cloud, IBM, Lookout, Mandiant, Okta, Radiant Logic, SailPoint, Tenable, and VMware. Certificates from DigiCert are also used.

-  E3B5 uses products from Mandiant, Microsoft, and Tenable. Certificates from DigiCert are also used.

-  E1B6 uses products from Amazon Web Services, IBM, Ivanti, Mandiant, Okta, Radiant Logic, SailPoint, and Tenable. Certificates from DigiCert are also used.

Physical Architecture Overview
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The laboratory environment in which the builds have been implemented is depicted and described in detail in the :ref:`ZTA Laboratory Physical Architecture<ArchitecturePhysical>` section. The laboratory architecture drawing from that section is reproduced here in the :download:`full architecture diagram </VolumeB/images/Architecture-PhysicalFullDetail.png>`. As shown, this laboratory environment includes four separate enterprise environments, each hosting its own distinct implementation of a ZTA architecture. The enterprises may interoperate as needed by a given use case, and the baseline enterprise environments have the flexibility to support enhancements. The laboratory environment also includes a management virtual local area network (VLAN) on which the following components are installed: Ansible, Terraform, MSV Director, and MSV Protected Theater. These management components support infrastructure as code (IaC) automation and orchestration.

The following builds are supported within the physical architecture depicted in the full architecture diagram and documented in the remainder of this guide:

-  E1B1 components consist of DigiCert CertCentral, IBM Cloud Pak for Security (CP4S), IBM Security QRadar XDR, Ivanti Access Zero Sign-On (ZSO), Ivanti Neurons for Unified Endpoint Management (UEM), Ivanti Sentry, Ivanti Tunnel, Mandiant Security Validation (MSV), Okta Identity Cloud, Okta Verify App, Radiant Logic RadiantOne Intelligent Identity Data Platform, SailPoint IdentityIQ, Tenable.ad, Tenable.io, and Zimperium Mobile Threat Defense (MTD).

-  E2B1 components consist of Cisco Duo, DigiCert CertCentral, IBM Security QRadar XDR, Mandiant MSV, Palo Alto Networks Next Generation Firewall (NGFW), PingFederate, which is a service in the Ping Identity Software as a Service (SaaS) offering of PingOne, Radiant Logic RadiantOne Intelligent Identity Data Platform, SailPoint IdentityIQ, Tenable.ad, Tenable.io, and Tenable Nessus Network Monitor (NNM).

-  E3B1 components consist of DigiCert CertCentral, F5 BIG-IP, Forescout eyeSight, Lookout Mobile Endpoint Security (MES), Mandiant MSV, Microsoft Azure Active Directory (AD), Microsoft Defender for Endpoint, Microsoft Endpoint Manager, Microsoft Sentinel, Palo Alto Networks NGFW, PC Matic Pro, Tenable.ad, and Tenable.io.

-  E1B2 and E1B3 components consist of Amazon Web Services (AWS) Infrastructure as a Service (IaaS), DigiCert CertCentral, IBM CP4S, IBM Security QRadar XDR, Mandiant MSV, Okta Identity Cloud, Okta Verify App, Radiant Logic RadiantOne Intelligent Identity Data Platform, SailPoint IdentityIQ, Tenable.ad, Tenable.io, Tenable NNM, Zscaler Admin Portal, Zscaler Application Connector, Zscaler Central Authority, Zscaler Client Connector (ZCC), Zscaler Internet Access (ZIA) Public Service Edges, and Zscaler Private Access (ZPA) Public Service Edges.

-  E3B2 components consist of DigiCert CertCentral, F5 BIG-IP, Forescout eyeControl, Forescout eyeExtend, Forescout eyeSegment, Forescout eyeSight, Mandiant MSV, Microsoft AD, Microsoft Azure AD, Microsoft Azure AD (Conditional Access), Microsoft Azure AD Identity Protection, Microsoft Azure (IaaS), Microsoft Defender for Cloud, Microsoft Defender for Cloud Apps, Microsoft Defender for Endpoint, Microsoft Intune, Microsoft Office 365 (SaaS), Microsoft Sentinel, Palo Alto Networks NGFW, PC Matic Pro, Tenable.ad, Tenable.io, and Tenable NNM.

-  E2B3 components consist of Cisco Duo, Cisco Identity Services Engine (ISE), Cisco network devices, Cisco Secure Endpoint (CSE), Cisco Secure Network Analytics (SNA), Cisco Secure Workload, DigiCert CertCentral, IBM Security QRadar XDR, Mandiant MSV, Palo Alto Networks NGFW, Ping Identity PingOne, Radiant Logic RadiantOne Intelligent Identity Data Platform, SailPoint IdentityIQ, Tenable.ad, Tenable.io, Tenable NNM, VMware Workspace ONE UEM and Access.

-  E3B3 components consist of DigiCert CertCentral, F5 BIG-IP, Forescout eyeControl, Forescout eyeExtend, Forescout eyeSight, Forescout eyeSegment, Mandiant MSV, Microsoft AD, Microsoft Azure AD, Microsoft Azure AD (Conditional Access), Microsoft Azure AD Identity Governance, Microsoft Intune, Microsoft Sentinel, Microsoft Azure App Proxy, Microsoft Defender for Endpoint, Microsoft Azure AD Identity Protection, Microsoft Defender for Identity, Microsoft Defender for Office, Microsoft Entra Permissions Management, Microsoft Defender for Cloud Apps, Microsoft Purview  - Data Loss Prevention (DLP), Microsoft Purview Information Protection, Microsoft Purview Information Protection Scanner, Microsoft Intune VPN Tunnel, Microsoft Azure Arc, Microsoft Azure Automanage, Microsoft Intune Privilege Access Workstation, Microsoft Azure Virtual Desktop Windows 365, Microsoft Defender for Cloud, Microsoft Azure (IaaS), Microsoft Office 365 (SaaS), Palo Alto Networks NGFW, PC Matic Pro, Tenable.io, Tenable.ad, and Tenable NNM.

-  E4B3 components consist of DigiCert ONE, IBM CP4S, IBM QRadar XDR, IBM Security Guardium Data Encryption, IBM Security MaaS360 (for both laptops and mobile devices), IBM Security Verify, Mandiant MSV, Palo Alto Networks GlobalProtect VPN, Tenable.ad, Tenable.io, Tenable NNM, and VMware infrastructure.

-  E1B4 components consist of Appgate SDP Controller, Appgate SDP Gateway, Appgate SDP client, Appgate Portal, AWS IaaS and SaaS, DigiCert CertCentral, IBM CP4S, IBM Security QRadar XDR, Ivanti Neurons for UEM Platform, Mandiant MSV, Okta Identity Cloud, Okta Verify App, Radiant Logic RadiantOne Intelligent Identity Data Platform, SailPoint IdentityIQ, Tenable.ad, Tenable.io, Tenable NNM, and Zimperium MTD.

-  E2B4 components consist of Symantec Cloud Secure Web Gateway (Cloud SWG), Symantec Zero Trust Network Access (ZTNA), Symantec Cloud Access Security Broker (CASB), Symantec Endpoint Security Agent, VMware Workspace ONE UEM, Symantec DLP Cloud Detection Service, Symantec ZTNA Connector, Okta Identity Cloud, Okta Verify App, Radiant Logic RadiantOne Intelligent Identity Data Platform, SailPoint IdentityIQ, IBM Security QRadar XDR, Tenable.io, Tenable.ad, Tenable NNM, Mandiant MSV, Google Cloud, and DigiCert CertCentral.

-  E3B4 components consist of F5 BIG-IP, F5 NGINX Plus, F5 Access App, Microsoft AD, Microsoft Azure AD, Microsoft Azure AD Identity Governance, Microsoft Intune, Microsoft Sentinel, Tenable.io, Tenable.ad, Tenable NNM, Mandiant MSV, Forescout eyeControl, Forescout eyeExtend, Forescout eyeSight, Forescout eyeSegment, Microsoft Azure (IaaS), and DigiCert CertCentral.

-  E4B4 components consist of VMware Workspace ONE Access, VMware Unified Access Gateway (UAG), VMware NSX-T, VMware Workspace ONE UEM, VMware Workspace ONE MTD, VMware Carbon Black Enterprise EDR, VMware Carbon Black Cloud, VMware vSphere, VMware vCenter, VMware vSAN, IBM Security QRadar XDR, Mandiant MSV, Tenable.io, Tenable.ad, Tenable NNM, and DigiCert ONE.

-  E1B5 components consist of PAN Panorama, PAN Next Generation Firewall (NGFW), PAN Prisma Access, PAN Prisma SASE (Prisma Access & Prisma SD-WAN), PAN Cloud Delivered Security Services (CDSS), PAN Cloud Identity Engine, PAN Global Protect, PAN Strata Cloud Manager, Okta Identity Cloud, Radiant Logic RadiantOne Intelligent Identity Data Platform, SailPoint IdentityIQ, Okta Verify App, IBM Security QRadar XDR, Tenable.io, Tenable.ad, Tenable NNM, Mandiant MSV, DigiCert CertCentral, and AWS IaaS.

For a detailed description of the architecture of each build, see :ref:`Build Architecture Details`. The remainder of this guide describes how to implement the EIG crawl, EIG run, and SDP, microsegmentation, and SASE phase builds.