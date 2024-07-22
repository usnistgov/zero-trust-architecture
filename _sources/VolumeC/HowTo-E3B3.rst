Enterprise 3 Build 3 (E3B3) - SDP and Microsegmentation - Microsoft Azure AD Conditional Access (later renamed Entra Conditional Access), Microsoft Intune, Microsoft Sentinel, Forescout eyeControl, and Forescout eyeExtend as PEs Product Guides
========================================================================================================================================================================================================================================================

.. include:: /_publication_note.rst

This section of the practice guide contains detailed instructions for installing, configuring, and integrating all the products used to implement E3B3. For additional details on E3B3's logical and physical architectures, please refer to :ref:`architecture and builds`. Build 3 was built on top of Build 2 and all the components in Build 2 were used in this build. For E3B2's configuration, please refer to :ref:`Enterprise 3 Build 2<enterprise 3 build 2 (e3b2) - eig run - microsoft azure ad conditional access (later renamed Entra Conditional Access), microsoft intune, forescout eyecontrol, and forescout eyeextend as pes product guides>`. Below are the additional components added to Build 3.

Microsoft Defender for Identity
-------------------------------

.. _microsoft-defender-identity:

Microsoft Defender for Identity is a cloud-based solution that detects identity-based threats in hybrid environments. Using signals collected from AD, it will discover compromised identities and alert on suspicious user actions. To deploy Defender for Identity, use the following steps:

1. Review the `prerequisites <https://learn.microsoft.com/en-us/defender-for-identity/prerequisites>`__ before deploying Defender for Identity.

2. `Configure the necessary Windows event logs <https://learn.microsoft.com/en-us/defender-for-identity/configure-windows-event-collection>`__ to enable appropriate detections.

3. `Create a directory service account <https://learn.microsoft.com/en-us/defender-for-identity/directory-service-accounts>`__ that will be used by Defender for Identity in the domain.

4. `Download <https://learn.microsoft.com/en-us/defender-for-identity/download-sensor>`__ and install the `Defender for Identity sensor <https://learn.microsoft.com/en-us/defender-for-identity/install-sensor>`__.

5. `Configure sensor settings <https://learn.microsoft.com/en-us/defender-for-identity/configure-sensor-settings>`__ and `validate installation <https://learn.microsoft.com/en-us/defender-for-identity/configure-sensor-settings#validate-installations>`__.

Microsoft Defender for Office
-----------------------------

Microsoft Defender for Office 365 provides protection from malware, phishing, spam, unsafe links and attachments, and other related threats. To configure Defender for Office 365, use the following steps:

1. `Configure the Standard Preset Security Policy for Defender for Office 365 <https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/step-by-step-guides/ensuring-you-always-have-the-optimal-security-controls-with-preset-security-policies?view=o365-worldwide>`__.

2. `Configure anti-phishing policies <https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/anti-phishing-policies-mdo-configure?source=recommendations&view=o365-worldwide>`__.

3. `Configure anti-malware policies <https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/anti-malware-policies-configure?source=recommendations&view=o365-worldwide>`__.

4. `Configure safe attachment protections in Microsoft 365 <https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/safe-attachments-policies-configure?source=recommendations&view=o365-worldwide>`__.

5. `Set up safe links protections <https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/safe-links-policies-configure?source=recommendations&view=o365-worldwide>`__.

Microsoft Purview Information Protection
-----------------------------------------

.. _microsoft-purview:

Purview Information Protection discovers, labels, classifies, and protects data in the cloud and on-premises. It aims to provide data governance and protection throughout the enterprise.

`Discover your sensitive data <https://learn.microsoft.com/en-us/microsoft-365/compliance/sit-create-edm-sit-unified-ux-workflow?view=o365-worldwide>`__ using the `examples shown here <https://learn.microsoft.com/en-us/microsoft-365/compliance/sit-common-scenarios?source=recommendations&view=o365-worldwide>`__. To discover sensitive data on-premises, you will need to deploy the Information Protection Scanner.

Information Protection Scanner
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Information Protection Scanner is used to discover sensitive data in an on-premises environment.

Use the information here to `install and configure the Information Protection Scanner <https://learn.microsoft.com/en-us/microsoft-365/compliance/deploy-scanner-configure-install?view=o365-worldwide&tabs=azure-portal-only>`__.

Purview DLP
~~~~~~~~~~~

Purview Data Loss Prevention (DLP) reduces the risk of unauthorized information disclosure and reduces the likelihood that sensitive data will be shared inappropriately. Data loss prevention policies specify the category of data to protect and the type of restrictions that are applicable.

Use the information here to `create and deploy DLP policies <https://learn.microsoft.com/en-us/microsoft-365/compliance/dlp-create-deploy-policy?view=o365-worldwide>`__.

Microsoft Entra Permissions Management
---------------------------------------

Entra Permissions Management provides visibility and control of an identity's permissions in Amazon Web Services (AWS), Microsoft Azure, and Google Cloud Platform (GCP). It identifies a user's permissions across all three cloud platforms, determines which permissions are not required based on usage, and can be configured to reduce the permissions to only those being used.

1. `Enable Entra Permissions Management <https://learn.microsoft.com/en-us/azure/active-directory/cloud-infrastructure-entitlement-management/onboard-enable-tenant>`__.

2.  `Onboard an AWS Account <https://learn.microsoft.com/en-us/azure/active-directory/cloud-infrastructure-entitlement-management/onboard-aws>`__.

3. `Onboard an Azure Subscription <https://learn.microsoft.com/en-us/azure/active-directory/cloud-infrastructure-entitlement-management/onboard-azure>`__.

4. `Onboard a GCP Project <https://learn.microsoft.com/en-us/azure/active-directory/cloud-infrastructure-entitlement-management/onboard-gcp>`__.

5. `Add an AWS Account, Azure Subscription, and GCP Project after onboarding is complete <https://learn.microsoft.com/en-us/azure/active-directory/cloud-infrastructure-entitlement-management/onboard-add-account-after-onboarding>`__.

6. To view inactive users or users with overprovisioned permissions, click `here <https://learn.microsoft.com/en-us/azure/active-directory/cloud-infrastructure-entitlement-management/ui-dashboard>`__.

7. To revoke unused permissions, click `here <https://learn.microsoft.com/en-us/azure/active-directory/cloud-infrastructure-entitlement-management/how-to-revoke-task-readonly-status>`__.

Microsoft Azure Virtual Desktop
----------------------------------

Azure Virtual Desktop is a desktop and application virtualization service that delivers the full Windows experience over HTTPS to a connecting client. Use the following steps to set up Azure Virtual Desktop:

1. `Understand prerequisites <https://learn.microsoft.com/en-us/azure/virtual-desktop/prerequisites?tabs=portal>`__ prior to deployment.

2. `Create and connect to an Azure Virtual Desktop <https://learn.microsoft.com/en-us/azure/virtual-desktop/tutorial-create-connect-personal-desktop?tabs=windows-client>`__.

Microsoft Intune VPN Tunnel
----------------------------

The Intune VPN Tunnel is a VPN solution that provides access to internal network resources from iOS/iPad and Android devices using modern authentication and conditional access. Use the following steps to set up the Intune VPN Tunnel:

1. `Understand the prerequisites <https://learn.microsoft.com/en-us/mem/intune/protect/microsoft-tunnel-prerequisites>`__ prior to deployment.

2. `Install and configure Intune VPN Tunnel <https://learn.microsoft.com/en-us/mem/intune/protect/microsoft-tunnel-configure>`__.

Microsoft Azure Arc
---------------------

Azure Arc is an Azure cloud platform that provides governance and management of on-premises servers, containers, and other related infrastructure components using Azure policies and management tools. It essentially extends governance to resources existing in on-premises environments. Use the following steps to set up Azure Arc:

1. `Understand network requirements <https://learn.microsoft.com/en-us/azure/azure-arc/network-requirements-consolidated?tabs=azure-cloud>`__.

2. `Understand Azure Arc-enabled servers <https://learn.microsoft.com/en-us/azure/azure-arc/servers/overview>`__.

3. `Onboard a Windows server <https://azurearcjumpstart.io/azure_arc_jumpstart/azure_arc_servers/general/onboard_server_win/>`__.

4. `Onboard a Linux server <https://azurearcjumpstart.io/azure_arc_jumpstart/azure_arc_servers/general/onboard_server_linux/>`__.

Microsoft Azure Automanage
---------------------------

Azure Automanage automatically configures onboarded servers with Azure best practices, monitors those servers, and remediates them when any configuration drift occurs. With Automanage, you must create a configuration profile for the server.

`Enable Azure Automanage for VMs in Azure portal <https://learn.microsoft.com/en-us/azure/automanage/quick-create-virtual-machines-portal>`__.

Microsoft Sentinel Playbooks
----------------------------

Playbooks in SOAR systems enable automated responses to address detected threats in an environment. In this build, a Sentinel playbook was created to revoke or terminate sessions of users when the risk evaluated for that session was deemed high. You can create playbooks with the information found at the `create a playbook <https://learn.microsoft.com/en-us/azure/sentinel/tutorial-respond-threats-playbook?tabs=LAC%2Cincidents>`__ link.

Microsoft Privileged Access Workstation
---------------------------------------

A privileged access workstation is a hardened workstation that includes security controls that lock down local administrative access and tools to only what is required for performing sensitive tasks. Use the information at `configure a privileged access workstation <https://learn.microsoft.com/en-us/security/privileged-access-workstations/privileged-access-deployment>`__ to do so.

Microsoft Azure Application Gateway
---------------------------------------

Azure Application Gateway is a layer seven load balancer and can be configured to provide Web Application Firewall functionality. Use the instructions at `Create and Configure an Application Gateway <https://learn.microsoft.com/en-us/azure/application-gateway/quick-create-portal>`__ to setup and configure an Azure Application Gateway. To configure the Web Application Firewall functionality, use the information at `Enable Web Application Firewall Feature <https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-application-gateway-waf#5-enable-the-waf-in-the-application-gateway-and-set-it-to-prevention-mode>`__ on an Azure Application Gateway.