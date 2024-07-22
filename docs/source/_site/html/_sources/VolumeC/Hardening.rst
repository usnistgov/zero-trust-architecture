Hardening Information
=======================

.. include:: /_publication_note.rst

This section documents how to secure the zero trust technology environments in this project's builds. The first part provides steps to secure infrastructure baseline components such as operating systems, switches, access points, firewalls, and enterprise services and resources that are applicable to all builds. The second part provides steps recommended by collaborators to secure the configuration baselines for their technologies used in each build. Links to applicable hardening documentation are provided when available. Otherwise, the recommended hardening steps are described.

Infrastructure Hardening Applicable to All Builds 
--------------------------------------------------

This section describes the hardening of infrastructure devices that are applicable to all builds.

Security Technical Implementation Guides (STIGs) are security configuration standards from the Defense Information Systems Agency (DISA). They contain technical guidance on how to harden information systems. STIGs can be downloaded from https://public.cyber.mil/stigs and viewed using the STIG Viewing Tools, which can be downloaded from https://public.cyber.mil/stigs/srg-stig-tools/.

DISA provides instructions for implementing and validating security requirements. Group Policy Objects (GPOs) can be used to assist with implementing STIG settings. The GPO package can be downloaded from https://public.cyber.mil/stigs/gpo/ and deployed in the enterprise environment. The GPO reports enable reviewing GPO configuration from a browser. They can be found in the Reports folder in the downloaded GPO package under the desired OS and/or application.

If deploying in an IaaS environment, templates already implementing a hardened baseline may be available. For example, AWS provides Amazon Machine Images (AMI) for a variety of hardening standards, such as CIS Benchmarks.

Windows Hardening 
~~~~~~~~~~~~~~~~~~

1. Download STIGs for your applicable OS

2.  Copy and unzip the STIG file to the endpoint to be hardened.

3.  Run the SCAP Compliance Checker (SCC) tool:

    a. Open the SCC tool and click Select **Local Scan** under **Scan Type**.

    b. Check appropriate OS and/or application versions boxes in the **Content** area.

    c. Under **Stream Details** -> **Profile**, select **Mac1_Public** for non-sensitive environments.

    d. Go back to the **Scan** section on the left and click **Start Scan**.

4.  Once the scan is complete, click **Results** -> **Open Results Directory** and select the most recent Results directory.

5.  Open the HTML summary file and click on the **Non-Compliance** tab.

6.  Scroll down to the **Results** section and click on the any of the links with remediation information.

7.  Follow the instructions to perform the remediation.

8.  In Windows domain environments, create a GPO and group policies as shown in the remediation information.

9.  Go to the **Group Policy Management** tool on your Domain Controller (via **Server Manager**), and attach/link the GPO to any of the OUs in your environment.

10.  Make sure to move any computers you want to harden to the OU with the GPO attached.

11. Go to each of the computers/endpoints and run ``gpupdate /force``.

12. Verify that the Group Policy Object was applied by running and viewing the output of ``gpresult /r``.

Optionally, you can run the SCC tool after applying the GPO to verify that there are no CAT 1 issues to be fixed.

These hardening standards have been applied to the AD domain and all domain-connected Windows computers in each Enterprise, including systems that host services provided by collaborators.

Linux Hardening
~~~~~~~~~~~~~~~

Use a compliance checking tool like SCC or OpenSCAP to scan the system against the applicable DISA STIG or CIS Benchmark. The following instructions use OpenSCAP to remediate system policies that are out of compliance with the selected profile.

1. Install the OpenSCAP tool (oscap) and SCAP Security Guide.

   a. OpenSCAP can be installed using the instructions at https://www.open-scap.org/tools/openscap-base/

   b. The latest official SCAP Security Guide profiles can be downloaded from https://github.com/ComplianceAsCode/content/releases.

2. View possible profiles by running oscap info /path/to/profile/<Name_of_Profile>.xml.

3. To run an initial oscap scan and compare the current system against a specific profile, run the command ``oscap xccdf eval --profile xccdf_org.ssgproject.content_profile_stig --results results.xml /path/to/profile/<Name_of_Profile>.xml``

4. Remediate non-compliant policies by running ``oscap xccdf remediate --results remediation-results.xml results.xml``.

5. Remediation can be completed during the initial oscap scan by running ``oscap xccdf eval --remediate --profile xccdf_org.ssgproject.content_profile_stig --results-arf results.xml /path/to/profile/<Name_of_Profile>.xml``.

These hardening standards have been applied to Linux-based computers in each enterprise, including systems that host services provided by collaborators.

Cisco Switch Hardening (Catalyst 9300 and Cisco 3850)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Hardening recommendations for Cisco routers and switches are described at the following link:

-  https://public.cyber.mil/stigs/downloads/

Cisco Wireless Access Point Controller Hardening
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Hardening recommendations for Cisco Wireless Access Point Controller is described at the following link:

-  https://public.cyber.mil/stigs/downloads/

Mobile Device Hardening
~~~~~~~~~~~~~~~~~~~~~~~

Microsoft's recommendations for mobile device hardening can be found at the following links:

-  iOS - `iOS/iPadOS security configuration framework - Microsoft Intune \| Microsoft Learn <https://learn.microsoft.com/en-us/mem/intune/enrollment/ios-ipados-configuration-framework>`__

-  Android - `Android Enterprise security configuration framework - Microsoft Intune \| Microsoft Learn <https://learn.microsoft.com/en-us/mem/intune/enrollment/android-configuration-framework>`__

Note that STIGs for iOS and Android devices are available at the following links:

-  iOS - https://public.cyber.mil/announcement/disa-releases-the-apple-ios-ipados-16-security-technical-implementation-guide/

-  Android - https://public.cyber.mil/announcement/disa-has-released-the-google-android-12-security-technical-implementation-guide-stig/

Pushing these STIGs to a mobile device requires creating policies to address each of the individual items listed in the STIG. These policies may be created manually, but endpoint management solutions sometimes provide pre-created policies that allow customers to easily apply the STIGs as baselines. If such pre-created policies are not available and users want to apply baseline STIGs for the mobile device and MDM in question, they will need to create the hardening profile baseline policies manually.

Palo Alto Networks Firewall Hardening (PAN 5250 NGFW)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Device hardening guidelines for Palo Alto Networks (PAN) Next Generation Firewalls and Panorama management devices, which are detailed in the PANW Common Criteria Evaluated Configuration Guides (CCECGs), can be found at the following links. Note that this documentation also includes guidance for enabling FIPS mode, but FIPS was not enabled for this project's deployment:

-  CCECG for `Palo Alto Networks PA-220, PA-400, PA-800, PA-3200, PA-3400, PA-5200, PA-5400, PA-5450, PA-7000, and VM Series Next-Generation Firewall with PAN-OS 10.2 <https://www.niap-ccevs.org/Product/Maint.cfm?AMID=1545&PID=11284>`__ - https://www.niap-ccevs.org/MMO/ProductAM/st_vid11284-agd.pdf

-  CCECG for Palo Alto Networks M-200, M-300, M-600, and M-700 Hardware, and Virtual Appliances all running Panorama 10.2 - https://www.niap-ccevs.org/MMO/ProductAM/st_vid11285-agd.pdf

Enterprise Services and Resources Hardening
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This section describes the steps taken to harden various enterprise services and resources used in the project. For all services below, the OS's are hardened according to the :ref:`Windows Hardening` section or :ref:`Linux Hardening` section. No applicable DISA STIGs or CIS Benchmarks exist for these services.:

-  Certificate Authority (CA)

   -  The Root CA is kept offline unless needed. Microsoft hardening recommendations are applied.

   -  Microsoft's recommendations for CA hardening can be found here: `Securing PKI: Technical Controls for Securing PKI \| Microsoft Learn <https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn786426(v=ws.11)>`__

-  Dynamic Host Configuration Protocol (DHCP)

   -  In addition to the OS hardening referenced in the :ref:`Windows Hardening` section, Microsoft provides more recommendations at the following link: https://techcommunity.microsoft.com/t5/core-infrastructure-and-security/building-the-totally-network-isolated-root-certification/ba-p/1189470

-  Domain Name System (DNS)

   -  Microsoft provides DNS hardening recommendations in its Secure DNS Deployment Guide, which is at the following link: `<https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee649266(v=ws.10)>`__

-  Remote Authentication Dial-In User Service (RADIUS)

   -  Microsoft Network Policy Server (NPS) best practices are followed. They can be found at: https://learn.microsoft.com/en-us/windows-server/networking/technologies/nps/nps-best-practices.

-  Server Message Block (SMB)/Secure File Transfer Protocol (SFTP)

   -  Microsoft recommends accessing the following link for information on SMB security enhancements: https://learn.microsoft.com/en-us/windows-server/storage/file-server/smb-security

-  Windows Server Update Services (WSUS)

   -  In addition to performing the standard Windows Hardening referenced above, Microsoft recommends following their recommended WSUS best practices, which can be found at the following link: https://learn.microsoft.com/en-us/troubleshoot/mem/configmgr/update-management/windows-server-update-services-best-practices

-  GitLab Enterprise

   -  GitLab Enterprise is hardened according to the guidance provided by GitLab at the following link: https://docs.gitlab.com/ee/security/.

Hardening Information Provided by Collaborating Vendors Applied to the Builds
-----------------------------------------------------------------------------

This section describes the custom device hardening steps that our collaborators recommend be performed for their products used in the builds. For details regarding which of these products are in each build, please refer to the :ref:`Build Architecture Details`.

Appgate
~~~~~~~

Appgate SDP Controller and Gateway Hardening
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The `Appgate Admin Guide <https://sdphelp.appgate.com/adminguide/system-security.html>`__ provides Appgate SDP Appliance hardening steps and is updated with every version of Appgate. Critical items to configure include:

-  `Restrict access to Controller's port 8443 <https://sdphelp.appgate.com/adminguide/system-security.html?anchor=admin-port>`__.

-  `Enable UDP-TCP Single Packet Authorization (SPA <https://sdphelp.appgate.com/adminguide/global-settings.html#spa>`__).

-  `Disable SSH to appliances <https://sdphelp.appgate.com/adminguide/system-security.html?anchor=port22>`__.

-  `Enable MFA for admin access <https://sdphelp.appgate.com/adminguide/mfa-for-admins.html>`__.

-  Use SAML/OIDC with MFA for admin UI authentication.

-  Configure granular policies to grant access based on device type, device security, user role, etc.

-  Configure granular entitlements using FQDN or IP and specific protocol and port numbers.

-  Forward logs to an enterprise SIEM so they can be aggregated with the enterprise logs, monitored, and generate alerts.

Appgate SDP Client Hardening
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The `Appgate Admin Guide <https://sdphelp.appgate.com/adminguide/v6.2/system-security.html?anchor=client-security>`__ provides Appgate SDP Client hardening steps and is updated with every version of Appgate. Critical items to configure include:

-  Install and configure the Appgate Client using enterprise device management tools, see `this link <https://sdphelp.appgate.com/adminguide/v6.2/system-security.html?anchor=client-security>`__ for more details.

-  Use SAML/OIDC with MFA, or certificate-based authentication (including smartcard/PIV/CAC) for client authentication.

-  Configure ring fencing to block incoming traffic to client devices.

-  Enable Tamper Proofing to prevent local admins from multi-homing their devices.

-  Use certificate authentication for headless and always-on clients.

Broadcom (VMware) 
~~~~~~~~~~~~~~~~~

VMware disables unnecessary ports, protocols, and services as part of baseline hardening standards. It follows industry best practices in applying secure configurations to managed servers.

For Workspace ONE UEM, Workspace ONE Assist, and VMware RemoteHelp servers that use Windows operating systems, server configurations can be hardened using GPO policies (such as account policies, user rights, security options, event log settings, app restrictions). Workspace ONE UEM, Workspace ONE Access, and Workspace ONE Intelligence Linux-based servers use Amazon Linux 2 images for system hardening. The Amazon Linux 2 images include default security configurations, such as limited remote access using SSH key pairs, remote root login disablement, reduced non-critical package installation, and automatic security related updates. This hardening information can be found at https://techzone.vmware.com/resource/workspace-one-cloud-services-security#system-hardening.

An overview of the security controls implemented within Workspace ONE commercial cloud services and their alignment with the NIST SP 800-171 standards can be found at the following link: https://techzone.vmware.com/resource/workspace-one-cloud-services-alignment-nist-sp-800-171#introduction.

Note that after the VMware products were implemented at NCCoE, VMware was acquired by Broadcom.

Cisco Systems 
~~~~~~~~~~~~~~

Note that in addition to the Cisco hardening recommendations provided in this section, information regarding hardening of Cisco switches and wireless access point controllers used in the network infrastructure of all builds are provided in the :ref:`Cisco Switch Hardening (Catalyst 9300 and Cisco 3850)` and :ref:`Cisco Wireless Access Point Controller Hardening` sections.

Cisco provides hardening recommendations for ISE and SNA at the links below:

-  ISE - https://ncp.nist.gov/checklist/994 and/or `https://dl.dod.cyber.mil/wp-content/uploads/stigs/zip/U_Cisco_ISE_Y23M06_STIG.zip <https://gcc02.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdl.dod.cyber.mil%2Fwp-content%2Fuploads%2Fstigs%2Fzip%2FU_Cisco_ISE_Y23M06_STIG.zip&data=05%7C01%7Cparisa.grayeli%40nist.gov%7Cf8daec6b3e374ad0590d08db9a82ce90%7C2ab5d82fd8fa4797a93e054655c61dec%7C1%7C0%7C638273658845872886%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C3000%7C%7C%7C&sdata=iumMWw%2FnfrdYgc%2BEPB7X5rsdNuZvtHJ%2BJ2aj%2BXG%2BwGo%3D&reserved=0>`__

-  SNA - `https://www.niap-ccevs.org/product/Compliant.cfm?PID=11313 <https://gcc02.safelinks.protection.outlook.com/?url=https%3A%2F%2Fwww.niap-ccevs.org%2Fproduct%2FCompliant.cfm%3FPID%3D11313&data=05%7C01%7Cparisa.grayeli%40nist.gov%7Cf8daec6b3e374ad0590d08db9a82ce90%7C2ab5d82fd8fa4797a93e054655c61dec%7C1%7C0%7C638273658845872886%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C3000%7C%7C%7C&sdata=lLtfYo9NrD1Bs4hKYbBMQF9fXt5wm3E5%2FmcimWF2YAs%3D&reserved=0>`__

DigiCert 
~~~~~~~~~

The DigiCert services used in this project are cloud-based, and hardening is managed by DigiCert. At this time, DigiCert does not have specific hardening recommendations for users regarding its CertCentral TLS Manager. DigiCert-managed solutions run on a secure infrastructure that complies with strict security processes and standards. Specific hardening actions are listed below:

-  Server Hardening

   -  Network Time Protocol (NTP) configuration

   -  Host-based intrusion detection system installation and configuration

   -  AV/EDR installation and configuration

   -  Event monitoring system installation and configuration

   -  Logging configuration

   -  Hosts.allow and hosts.deny configuration

   -  Warning banner configuration

   -  Permissions configuration

   -  Applying OS patches and hotfixes

   -  Disabling of standard and/or unneeded network services

   -  Disabling of standard and/or unneeded OS services

   -  Least privilege for user and administrative roles (through role-based access control)

   -  Password policy compliance

   -  Account lockout policy

   -  Enabling MFA for accounts

   -  Encryption at rest

-  Network Hardening

   -  Blocking unnecessary networks

   -  Disabling unneeded network services

   -  Applying patches and hotfixes

   -  Changing or removing default passwords

   -  Logging configuration

   -  NTP configuration

   -  Least privilege for user and administrative roles (RBAC)

   -  Password policy compliance

   -  Account lockout policy

   -  Enabling MFA for accounts

-  Application Hardening

   -  Disabling unneeded services or components

   -  Applying patches and hotfixes

   -  Least privilege for user and administrative roles (RBAC)

   -  Changing or removing default passwords

   -  Account lockout policy

   -  Enabling MFA for accounts

   -  Logging configuration

-  Database Hardening

   -  Applying patches and hotfixes

   -  Changing or removing default passwords

   -  Logging configuration

   -  NTP configuration

   -  Least privilege for user and administrative roles (RBAC)

   -  Password policy compliance

   -  Account lockout policy

   -  Enabling MFA for accounts

   -  Encryption as appropriate (per data classification policy)

   -  Encryption at rest

F5
~~

F5's hardening recommendations for its systems can be found at the following link: https://my.f5.com/manage/s/article/K53108777. For information on hardening NGINX, please see https://docs.nginx.com/nginx/admin-guide/security-controls/.

Google
~~~~~~

A link to the STIG for Android mobile devices is provided in the :ref:`Mobile Device Hardening` section.

Ivanti 
~~~~~~~

Ivanti's nZTA hardening information can be found in this portion of the Ivanti nZTA Admin Guide: https://help.ivanti.com/ps/help/en_US/nSA/22.x/nsa-zta/ag/tadmin_cr_gway.htm#Configur

Ivanti recommends implementing the relevant mobile device OS STIGs via the Ivanti Neurons for UEM (IN UEM) Platform for managed devices. The STIG controls are implemented through configurations and policies in the IN UEM Console.

1. Log in to the IN UEM Console.

2. Navigate to **Configurations** -> **Add New** -> select relevant OS -> select relevant configuration based on the STIG control implementation - > **Save Configuration** and apply to appropriate User/Device group.

3. Navigate to **Policies** -> **Add New** -> select relevant policy (Custom) -> create device policy -> **Save Policy** and apply to appropriate User/Device group.

The relevant mobile OSes STIGs Ivanti supports are: Apple iOS, Google Android, Samsung/Honeywell/Motorola/Zebra. The STIG Mobility Library can be found at the following link: https://public.cyber.mil/stigs/downloads/?_dl_facet_stigs=mobility

Ivanti publishes a STIG for Ivanti Sentry (formerly MobileIron Sentry). The Ivanti Sentry STIG specifies the hardening recommendations and step-by-step configurations for Ivanti Sentry configured for Tunnel or Access ZSO. The Ivanti Sentry STIG can be found at the following link: https://ncp.nist.gov/checklist/1010/download/7785

Lookout
~~~~~~~

The Lookout SSE hardening information can be found at the following link: https://www.lookout.com/form/sse-admin-guide

Mandiant MSV
~~~~~~~~~~~~

The Mandiant Security Validation (MSV) platform has been hardened using the STIG for each core component. MSV is currently available in two flavors: General Availability (GA) and STIG. The STIG release is by request only, specifically created to support the strict deployment requirements of the Department of Defense. To make these improvements more widely available, Mandiant Engineering is merging the STIG and GA releases to create a single STIG-based version. Its increased security and hardening measures will not impact functionality and performance.

Microsoft 
~~~~~~~~~~

Note that in addition to the Microsoft hardening recommendations provided in this section, information regarding hardening of the Windows OS and various enterprise services used in the network infrastructure of all builds is provided in the :ref:`Windows Hardening` and :ref:`Enterprise Services and Resources Hardening` sections.

All admin consoles for Azure AD (note that the product name "Azure AD" was later changed to "Entra ID"), Azure AD Conditional Access, Azure AD Identity Governance, Azure AD MFA, Azure AD Identity Protection, Azure AD Application Proxy, Defender for Apps, Defender for Cloud, Intune, Defender for Endpoint, Defender for Identity, Entra Permissions Management, Purview DLP, Purview Information Protection, Purview Information Protection Scanner Intune VPN Tunnel, Azure Arc, Azure Automanage, Intune Privilege Access Workstations (PAW), Azure Virtual Desktop Windows 365, Sentinel, and Azure-IaaS are cloud-based and hosted by Microsoft.

Best practices for securing Microsoft Entra can be found at the following link: `Best practices to secure with Microsoft Entra ID - Microsoft Entra | Microsoft Learn <https://learn.microsoft.com/en-us/entra/architecture/secure-best-practices>`__ 

Best practices for securing Microsoft Entra privileged roles can be found at the following link: `Best practices for Microsoft Entra roles - Microsoft Entra ID | Microsoft Learn <https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/best-practices>`__

Best practices for securing break glass accounts for Microsoft Entra can be found at the following link: `Manage emergency access admin accounts - Microsoft Entra ID | Microsoft Learn <https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/security-emergency-access>`__

Security best practices for Azure IaaS can be found at the following link: https://learn.microsoft.com/en-us/azure/security/fundamentals/iaas

The Windows hardening guide for Intune and Defender for Endpoint can be found at the following link: https://techcommunity.microsoft.com/t5/security-compliance-and-identity/hardening-windows-clients-with-microsoft-intune-and-defender-for/ba-p/3807378

The Microsoft user application hardening guide can be found at the following link: https://learn.microsoft.com/en-us/compliance/essential-eight/e8-app-harden

The Microsoft Privilege Access Workstation hardening guide can be found at the following link: https://learn.microsoft.com/en-us/security/privileged-access-workstations/privileged-access-deployment

The Azure Virtual Desktop hardening guide can be found at the following link: https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/azure-virtual-desktop-security-baseline

The Windows 365 hardening guide can be found at the following link: https://learn.microsoft.com/en-us/windows-365/enterprise/security-guidelines

Okta 
~~~~~

Okta Identity Cloud is being hosted on a cloud platform which has options of FedRAMP High, FedRAMP Moderate, and DoD Impact Level 4 (IL4). For the hardening details, please refer to `https://www.okta.com/resources/whitepaper/okta-security-technical-white-paper/ <https://gcc02.safelinks.protection.outlook.com/?url=https%3A%2F%2Fwww.okta.com%2Fresources%2Fwhitepaper%2Fokta-security-technical-white-paper%2F&data=05%7C01%7Cparisa.grayeli%40nist.gov%7Cc91010cbdef74f55ffc608db89fffd33%7C2ab5d82fd8fa4797a93e054655c61dec%7C1%7C0%7C638255504786105445%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C3000%7C%7C%7C&sdata=mrNnI6qWKMRi0pvF6XuU4ajRReNIwSUJ2%2BNwDg61SOo%3D&reserved=0>`__

Palo Alto Networks (PAN)
~~~~~~~~~~~~~~~~~~~~~~~~

Links to device hardening guidelines for Palo Alto Networks (PANW) Next Generation Firewalls and Panorama management devices are provided in the :ref:`Palo Alto Networks Firewall Hardening (PAN 5250 NGFW)` section.

Strata Cloud Manager is used by organizations to manage their NGFWs and SASE environments from a single interface. Strata Cloud Manager has best practice security checks built into it to allow organizations to assess their Panorama, NGFW, and Panorama-managed Prisma Access security configurations against best practices and remediate any failed checks. To use Strata Cloud Manager to perform best practice checks, see this link: https://docs.paloaltonetworks.com/cloud-management/administration/overview/built-in-best-practices

To configure a security policy that is shared across NGFWs and Prisma Access, see this link: https://docs.paloaltonetworks.com/cloud-management/administration/manage-configuration-ngfw-and-prisma-access

Ping Identity 
~~~~~~~~~~~~~~

The OS is hardened according to the appropriate OS Hardening section above. A product-specific security hardening guide is available at: https://support.pingidentity.com/s/article/PingFederate-Security-Hardening-Guide

Symantec by Broadcom
~~~~~~~~~~~~~~~~~~~~~

The majority of services provided by Symantec by Broadcom for this project are hosted in the cloud, and hardening is managed by Symantec by Broadcom. Symantec by Broadcom is `in process for FedRAMP authorization <https://marketplace.fedramp.gov/products/FR2232465502>`__. Two on-prem instances of Symantec by Broadcom offerings were deployed: the Symantec DLP Management Server and SpanVA.

Symantec DLP Management Server Hardening
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Guidelines for hardening aspects of Symantec DLP capabilities are as follows:

-  Firewall ports: https://techdocs.broadcom.com/us/en/symantec-security-software/information-security/data-loss-prevention/16-0-1/Install-DLP/post-installation-tasks-v15632229-d279e10401/about-post-installation-security-configuration-v15632391-d279e10427/corporate-firewall-configuration-v15632745-d279e11210.html

-  Services: https://techdocs.broadcom.com/us/en/symantec-security-software/information-security/data-loss-prevention/16-0-1/Install-DLP/post-installation-tasks-v15632229-d279e10401/about-post-installation-security-configuration-v15632391-d279e10427/windows-security-lockdown-guidelines-v15632398-d279e11241.html

-  Service account configuration: https://techdocs.broadcom.com/us/en/symantec-security-software/information-security/data-loss-prevention/16-0-1/Install-DLP/post-installation-tasks-v15632229-d279e10401/about-post-installation-security-configuration-v15632391-d279e10427/windows-administrative-security-settings-v15632498-d279e11405.html

SpanVA
^^^^^^

SpanVA hardening guidelines are located in Symantec's official documentation: https://techdocs.broadcom.com/us/en/symantec-security-software/information-security/symantec-cloudsoc/cloud/audit-home/spanva-audit/spanva-security.html

The SpanVA appliance comes hardened out of the box; only necessary firewall ports are open and all externally facing services, including SSH, are turned off.

Tenable 
~~~~~~~~~

The on-premises architecture for Tenable Identity Exposure (formerly known as Tenable.ad) uses the Microsoft Windows Server platform and is spread across three dedicated servers for optimal performance and security. Tenable recommends using Windows Server 2022 with the latest patches applied. The three servers that make up the Tenable Identity Exposure Platform are Storage Manager (SQL Server), Security Engine Node, and the Directory Listener. Each of these servers can be configured with additional hardened settings to ensure that the platform is deployed in the most secure manner. These and other additional hardened settings are described in the subsections below.

TLS Server
^^^^^^^^^^

Tenable recommends customers use `TLS with Peer Verification <https://docs.tenable.com/identity-exposure/Installation/Content/03_Install/install_TLS_with_peer.htm>`__ when installing Tenable Identity Exposure in a production environment. This makes the platform more resistant to man-in-the-middle attacks.

Storage Manager (SQL)
^^^^^^^^^^^^^^^^^^^^^

Tenable recommends that after installation completes, the customer should create a new account in SQL for database access and disable the default service account (SA). In addition, it is recommended to change the port for SQL to something other than the default SQL port. These changes will reduce the likelihood of a threat actor accessing the SQL data. Please reference the *How to change Tenable.AD SQL Service account Password Knowledge Article* here: https://community.tenable.com/s/article/How-to-change-the-Tenable-ad-SQL-service-account-password?language=en_US#:~:text=Connect%20to%20Storage%20Manager.%20Assign%20the%20new%20account,the%20Security%20Engine%20Node.%20Restart%20the%20alsid_eridanis%20service.

Security Engine Node
^^^^^^^^^^^^^^^^^^^^

Tenable recommends that customers change the default username and password for RabbitMQ administration. Please refer to *Changing the default RabbitMQ password* `Knowledge Article <https://community.tenable.com/s/article/Tenable-ad-Changing-the-default-RabbitMQ-password>`__ here: https://community.tenable.com/s/article/Tenable-ad-Changing-the-default-RabbitMQ-password?language=en_US

Tenable recommends that customers use a `custom certificate <https://docs.tenable.com/identity-exposure/Installation/Content/06_Manage/https-for-tenablead-web-application.htm>`__ to enforce HTTPS for portal access in Internet Information Services (IIS).

Directory Listener 
^^^^^^^^^^^^^^^^^^^

Tenable recommends that customers install a client certificate on the directory listener to enable LDAPS between the directory listener and the domain controller.

Forest
^^^^^^

Tenable recommends that customers `secure the service account and enforce Kerberos authentication <https://docs.tenable.com/identity-exposure/3_x/Content/Admin/07a-Forests/AddForests.htm>`__. This configuration will allow the customer to add the account to the protected users group for additional security protection.

Domain
^^^^^^^

Tenable recommends that customers configure `LDAPS <https://docs.tenable.com/identity-exposure/3_x/Content/Admin/08a-Domains/Domains.htm>`__ for the domain configuration to ensure all communications are secure. In addition, Tenable recommends using the FQDN for the hostname of the Primary Domain Controller emulator (PDCe) instead of the IP address. This is a requirement to enforce Kerberos authentication.

Authentication
^^^^^^^^^^^^^^^

Tenable recommends that customers use `SAML <https://docs.tenable.com/identity-exposure/3_x/Content/Admin/02a-Authentication/SAMLAuthentication.htm>`__ with enforcement of MFA for all users who need to connect to the portal.

TLS for Alerting
^^^^^^^^^^^^^^^^^

Tenable recommends that customers configure TLS for SMTP and syslog using the application services module `Trusted Certificate Authorities <https://docs.tenable.com/identity-exposure/3_x/Content/Admin/02a-Authentication/LDAPAuthentication.htm?Highlight=TRUSTED%20CERTIFICATE%20AUTHORITIES#To>`__.

Zscaler 
~~~~~~~~~

Hardening recommendations for on-premises components such as Zscaler Client Connector can be found at the following link: https://help.zscaler.com/zcspm/about-quick-wins-os-hardening

Zscaler only deploys its public cloud nodes within accredited and hardened data centers that meet Zscaler's standards for physical security. Zscaler has achieved FedRAMP High and Impact Level 5 accreditation for Zscaler's Federal Customers.

In addition, Zscaler holds globally recognized certifications that cover locations where data is stored: SSAE 16/SOC 2 Type II, ISO 27001, ISO 27018, and others.
