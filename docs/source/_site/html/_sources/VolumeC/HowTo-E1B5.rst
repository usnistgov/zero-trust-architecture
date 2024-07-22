Enterprise 1 Build 5 (E1B5) - SASE and Microsegmentation - PAN NGFW and PAN Prisma Access as PEs Product Guides
=================================================================================================================

.. include:: /_publication_note.rst

This section of the practice guide contains detailed instructions for installing, configuring, and integrating all the products used to implement E1B5. For additional details on E1B5's logical and physical architectures, please refer to :ref:`architecture and builds`,

Palo Alto Networks (PAN) Panorama
---------------------------------

Panorama is used to manage PAN NGFWs whether they are in the enterprise, a branch office, or the cloud. Configuration is updated on the Panorama user interface and pushed to the NGFWs. For this build, we deployed a virtual Panorama instance to manage the NGFWs for Enterprise 1. Once deployed, all NGFW configurations were modified and updated by the Panorama. Follow the `Panorama Administrator's Guide <https://docs.paloaltonetworks.com/panorama/10-2/panorama-admin>`__ to perform the following:

-  Deployment planning

-  Virtual appliance installation and setup

-  Adding firewalls as managed device

PAN Next Generation Firewall (NGFW)
-----------------------------------

The PAN NGFWs in Enterprise 1 are the PE and PEPs. The NGFW that is on-premises manages the access of on-prem users to the on-prem resources. It also acts as a PEP to branch office and remote users attempting to access on-prem resources. The branch NGFW acts as the PE and PEP for branch users. Initial authentication, authorization, and compliance checks of users and endpoints are performed by the branch NGFW. Policies are also applied on the branch NGFW for access to resources that are either on-premises or in the cloud. The on-premises or cloud NGFW will perform policy checks again to validate that the branch user has permission to access the resource that it is protecting. There are no users within the AWS cloud. A virtual NGFW is deployed to protect cloud resources.

For all the NGFW configurations, please use the `Next-Generation Firewall Administrator's Guide <https://docs.paloaltonetworks.com/pan-os/10-2/pan-os-admin/getting-started>`__ unless a link is provided below.

For the on-premises and branch office NGFW, we used a physical 5250 NGFW appliances. `Basic device <https://docs.paloaltonetworks.com/pan-os/10-1/pan-os-admin/getting-started/integrate-the-firewall-into-your-management-network/perform-initial-configuration>`__, `network <https://docs.paloaltonetworks.com/pan-os/10-1/pan-os-admin/getting-started/segment-your-network-using-interfaces-and-zones>`__, and `policy setup <https://docs.paloaltonetworks.com/pan-os/10-1/pan-os-admin/getting-started/set-up-a-basic-security-policy>`__ was completed prior to this build. The following specific configurations are performed during this build:

-  `Policies for access to on-premises resources <https://docs.paloaltonetworks.com/pan-os/10-1/pan-os-admin/getting-started/set-up-a-basic-security-policy>`__: Each policy may leverage the configuration below such as Host Information Profile (HIP) and URL filtering to properly protect the resources.

    -  The most specific and granular policies should be at the top of the list

    -  Policies can overlap. Perform tests to validate new policies do not overlap with current policies.

-  Authentication using Integration with PAN `Cloud Identity Engine (CIE) <https://docs.paloaltonetworks.com/cloud-identity/cloud-identity-engine-getting-started/authenticate-users-with-the-cloud-identity-engine/configure-the-cloud-identity-engine-in-an-authentication-profile>`__

-  `HIP configuration <https://docs.paloaltonetworks.com/globalprotect/10-1/globalprotect-admin/globalprotect-quick-configs/globalprotect-for-internal-hip-checking-and-user-based-access>`__ for compliance checks

-  `User groups retrieved from Okta <https://docs.paloaltonetworks.com/cloud-identity/cloud-identity-engine-getting-started/choose-directory-type/configure-a-cloud-based-directory/set-up-okta-directory-in-the-cloud-identity-engine>`__ to be leveraged for policy configuration based on user type (e.g., employee or contractor)

-  `Dynamic User Group configuration to quarantine users <https://docs.paloaltonetworks.com/pan-os/10-1/pan-os-admin/policy/use-auto-tagging-to-automate-security-actions>`__ based on policy violations

-  `Advanced URL Filtering <https://docs.paloaltonetworks.com/advanced-url-filtering/administration/url-filtering-basics/how-url-filtering-works>`__ to allow or deny access to websites

-  Global Protect Internal Gateway configuration to receive HIP information (see :ref:`PAN Global Protect`)

-  `Syslog configuration <https://www.ibm.com/docs/en/qsip/7.5?topic=networks-palo-alto-pa-series>`__ to send logs to QRadar

-  Service connection configuration between on-premises NGFW and Prisma Access to allow remote users access to on-premises resources. Follow instructions in the `Next-Generation Firewall Administrator's Guide <https://docs.paloaltonetworks.com/pan-os/10-2/pan-os-admin/getting-started>`__ to Configure IPsec VPN Tunnels (Site-to-Site) for this service connection.

-  Remote connection configuration between branch office and Prisma Access to allow users access to on-premises resources via Prisma Access. Follow instructions in the `Next-Generation Firewall Administrator's Guide <https://docs.paloaltonetworks.com/pan-os/10-2/pan-os-admin/getting-started>`__ to Configure IPsec VPN Tunnels (Site-to-Site) for this remote connection.

To install the NGFW in AWS, use the `VM-Series NGFW on AWS Guide <https://docs.paloaltonetworks.com/vm-series/10-2/vm-series-deployment/set-up-the-vm-series-firewall-on-aws>`__. The following configurations were performed on the NGFW in AWS:

-  Installation and initial setup

-  Policies for access to AWS resources. Use the `Next-Generation Firewall Administrator's Guide <https://docs.paloaltonetworks.com/pan-os/10-2/pan-os-admin/getting-started>`__

-  `Syslog configuration <https://www.ibm.com/docs/en/qsip/7.5?topic=networks-palo-alto-pa-series>`__ to send logs to QRadar

-  Service connection configuration between NGFW in AWS and Prisma Access. Follow instructions in the `Next-Generation Firewall Administrator's Guide <https://docs.paloaltonetworks.com/pan-os/10-2/pan-os-admin/getting-started>`__ to Configure IPsec VPN Tunnels (Site-to-Site) for this service connection.

PAN Strata Cloud Manager 
-------------------------

PAN Strata Cloud Manager uses AI and other data analytics to improve security posture and prevent network disruptions. Using the Strata Cloud Manager, administrators can access and configure all of Palo Alto Networks's cloud-based solutions such as Prisma Access, Prisma SD-WAN, Cloud Identity Engine, and Cloud Delivered Security Services. For this build, a tenant was created, and the four solutions listed above were activated. The Palo Alto Networks representative activated a Strata Cloud Manager tenant and added NCCoE engineers as administrators. Once that process was completed, administrators were able to login to the Strata Cloud Manager and configure the four solutions.

PAN Prisma SASE (Prisma Access & Prisma SD-WAN)
-----------------------------------------------

The PAN Prisma SASE cloud solution secures mobile users' access to applications whether the users are remote or on-premises. Applications are also protected whether they are on-premises, in the datacenter, or in the cloud. Prisma SASE components used in this build includes Prisma Access and Prisma SD-WAN. Please see :ref:`PAN Prisma Access` for Prisma Access configuration.

PAN Prisma SD-WAN is a cloud-based service that implements app-defined, autonomous SD-WAN to secure and connect branch offices, data centers and large campus with the ability to use any WAN solution.

For this build, we configured a branch office with SD-WAN for demonstration purposes. Use the `Prisma SD-WAN Administrator's Guide <https://docs.paloaltonetworks.com/prisma/prisma-sd-wan/prisma-sd-wan-admin>`__ to configure the following:

-  SD-WAN sites and devices

-  Administrator authentication and authorization

-  Routing, security, and availability policies

-  Log incidents and provide alerts

PAN Prisma Access
-----------------

PAN Prisma Access is a component of the Prisma SASE SaaS solution to provide access and security to remote users as well as secure communications to enterprise and remote networks. Remote users login to Global Protect Gateway within Prisma Access to gain access to various resources from the enterprise and the cloud. For Prisma Access configurations, please use the `Prisma Access Administration Guide <https://docs.paloaltonetworks.com/prisma-access>`__.

For Prisma Access, the following specific configurations are performed:

-  Policies for access to on-premises and cloud resources: Each policy may leverage the configuration below, such as HIP and URL filtering, to properly protect the resources.

    -  The most specific and granular policies should be at the top of the list.

    -  Policies can overlap easily. Perform tests to validate that new policies do not overlap with current policies.

-  Authentication using integration with `PAN CIE <https://docs.paloaltonetworks.com/cloud-management/administration/manage-configuration-ngfw-and-prisma-access/identity-services/cloud-identity-engine>`__

-  HIP configuration for compliance checks

-  `User groups retrieved from Okta <https://docs.paloaltonetworks.com/cloud-identity/cloud-identity-engine-getting-started/choose-directory-type/configure-a-cloud-based-directory/set-up-okta-directory-in-the-cloud-identity-engine>`__ to be leveraged for policy configuration based on user type (e.g., employee or contractor)

-  Dynamic User Group configuration to quarantine users based on policy violations

-  Advanced URL Filtering to allow or deny access to websites

-  Global Protect Gateway configuration to allow users access and to receive HIP information (see :ref:`PAN Global Protect`)

-  `Log forwarding configuration <https://docs.paloaltonetworks.com/cortex/cortex-data-lake/cortex-data-lake-getting-started/get-started-with-log-forwarding-app/forward-logs-from-logging-service-to-syslog-server>`__ to send logs to QRadar

-  Service connection configuration between on-premises NGFW and Prisma Access to allow remote users access to on-premises resources

-  Remote connection configuration between branch office and Prisma Access to allow users access to on-premises resources via Prisma Access

PAN Cloud Delivered Security Services (CDSS)
--------------------------------------------

PAN Cloud Delivered Security Services (CDSS) are a set of security services that are natively integrated into zero trust solutions such as Prisma SASE and NGFWs. The CDSS services leveraged for this build are:

-  Advanced Threat Protection: Cloud-based, inline, machine learning-based detection and enforcement service for protection against known and unknown malware.

-  Advanced URL Filtering: Real-time, inline, web security engine performing analysis run on actual user-generated traffic, rather than relying strictly on URL database lookups.

-  DNS Security: DNS security service providing predictive analytics to disrupt attacks that use DNS for command and control or data theft.

-  Enterprise DLP: Data security service covering discovery, monitoring, and protection of all sensitive data across every network, cloud, and user.

-  Advanced WildFire: Cloud-based sandboxing and malware analysis solution enabling detection of and protection against highly evasive malware.

The CDSS services are configured within the PE. For example, on-premises NGFW were used to configure CDSS services for on-prem users, Prisma Access for remote users, and branch NGFW for branch users. Please see :ref:`PAN Next Generation Firewall (NGFW)` and :ref:`PAN Prisma Access` for specific configurations.

PAN Cloud Identity Engine (CIE)
-------------------------------

PAN Cloud Identity Engine (CIE) is a centralized solution that provides user identification and authentication to on-premises, hybrid, and cloud resources. For this build, PAN CIE integrates with Okta to provide IDP functions to users accessing Enterprise 1 resources. All the PEPs in Enterprise 1 leverage PAN CIE for authentication. When CIE receives the authentication requests, it sends the requests to the IDP Okta.

Use the `Cloud Identity Engine Document <https://docs.paloaltonetworks.com/cloud-identity/cloud-identity-engine-getting-started/authenticate-users-with-the-cloud-identity-engine/configure-an-identity-provider-in-the-cloud-identity-engine/configure-okta-as-an-idp-in-the-cloud-identity-engine>`__ to configure CIE to allow Enterprise 1 users to authenticate using Okta as the IDP.

For CIE, the following specific configuration are performed:

-  Activate and set up CIE basic configuration

-  Configure a Cloud-Based Directory (Okta)

-  Authenticate users with CIE

-  Configure PE/PEPs to use CIE for authentication (refer to :ref:`PAN Next Generation Firewall (NGFW)` and :ref:`PAN Prisma Access`)

PAN Global Protect
------------------

The Global Protect (GP) Gateway resides within the PAN NGFW or Prisma Access to allow users access into the network and resources. Global Protect Configuration is needed on the NGFW or Prisma Access so it can connect endpoints and gather endpoint HIP information as well. This information can be used to identify endpoint compliance and make policy decisions about the user and endpoint. Use the `Global Protect Administration Guide <https://docs.paloaltonetworks.com/globalprotect>`__ to configure the NGFW GP Internal Gateway and to set up the endpoints. Use the `Prisma Access Administration Guide <https://docs.paloaltonetworks.com/prisma-access>`__ to configure the Global Protect Gateway within Prisma Access.

The following configurations were performed:

-  Configure Global Protect Internal Gateway for both the on-premises NGFW and branch NGFW.

-  Configure Global Protect Gateway on Prisma Access.

-  Install and set up the Global Protect client on endpoints. Windows, macOS, Linux, iOS, and Android operating systems are all supported.

Okta Identity Cloud
-------------------

For installation, configuration, and integration instructions, refer to :ref:`Okta Identity Cloud<okta-identity-cloud>`.

Configuration specific to this build requires PAN's Cloud Identity Engine to set up Okta Identity Cloud as the IDP. To configure Okta as IDP, use the `Cloud Identity Engine Documentation <https://docs.paloaltonetworks.com/cloud-identity/cloud-identity-engine-getting-started/authenticate-users-with-the-cloud-identity-engine/configure-an-identity-provider-in-the-cloud-identity-engine/configure-okta-as-an-idp-in-the-cloud-identity-engine>`__.

Okta Verify App
---------------

For installation, configuration, and integration instructions, refer to :ref:`Okta Verify App<okta-verify-app>`

Radiant Logic RadiantOne
------------------------

For installation, configuration, and integration instructions, refer to :ref:`Radiant Logic RadiantOne<radiant-one>`.

SailPoint IdentityIQ
--------------------

For installation, configuration, and integration instructions, refer to :ref:`SailPoint IdentityIQ Installation and Configuration<sailpoint-install>`.

IBM Security QRadar XDR
-----------------------

For installation, configuration, and integration instructions, refer to :ref:`IBM Security QRadar XDR<ibm-qradar>`.

Tenable.io
----------

For installation, configuration, and integration instructions, refer to :ref:`Tenable.io<tenable-io>`.

Tenable.ad
----------

For installation, configuration, and integration instructions, refer to :ref:`Tenable.ad<tenable-ad>`.

Tenable NNM
-----------

For installation, configuration, and integration instructions, refer to :ref:`Tenable NNM<tenable-nnm>`.

Mandiant Security Validation (MSV)
-----------------------------------

For installation, configuration, and integration instructions, refer to :ref:`Mandiant Security Validation (MSV)<mandiant-msv>`.

DigiCert CertCentral
---------------------

For installation, configuration, and integration instructions, refer to :ref:`DigiCert CertCentral<digicert-certcentral>`.

AWS IaaS
--------

For installation, configuration, and integration instructions, refer to :ref:`AWS IaaS<aws-iaas>`.

For this build, we created a virtual firewall to protect the resources in AWS. We leveraged VM-Series NGFW on AWS Guide Version 10.2 `to install and configure the firewall. <https://docs.paloaltonetworks.com/vm-series/10-2/vm-series-deployment/set-up-the-vm-series-firewall-on-aws>`__ Please see :ref:`PAN Next Generation Firewall (NGFW)` for details.
