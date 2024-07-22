Enterprise 4 Build 4 (E4B4) - SDP, Microsegmentation, and EIG - VMware Workspace ONE Access, VMware Unified Access Gateway, and VMware NSX-T as PEs Product Guides
===================================================================================================================================================================

.. include:: /_publication_note.rst

This section of the practice guide contains detailed instructions for installing, configuring, and integrating all the products used to implement E4B4. For additional details on E4B4's logical and physical architectures, please refer to :ref:`architecture and builds`. Note that after this build was completed, VMware was acquired by Broadcom.

VMware Workspace ONE Access
---------------------------

Workspace ONE Access can serve as an IdP and integrate with a large range of enterprise identity components. For this build, Workspace ONE Access was integrated with an on-premises Active Directory to serve as an IdP.

Setup
~~~~~

Each cloud-based instance of Workspace ONE Access must be provisioned by VMware. After this has been completed, VMware provides access and setup instructions.

Integration with Microsoft AD
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To integrate with AD, an on-premises agent was installed on a Microsoft Windows Server 2019 system and connected to Workspace ONE Access. After this, Workspace ONE Access was configured to pull user, group, and attribute information.

1. The step-by-step guide to adding the on-prem connector can be triggered in the Workspace ONE Access console by navigating to **Integrations -> Connectors** and clicking **New**.

2. After the on-prem agent is installed and connected to Workspace ONE Access, follow the `official VMware documentation <https://docs.vmware.com/en/VMware-Workspace-ONE-Access/services/ws1_access_directory/GUID-9DB02A30-DE2E-4FDE-9AD6-32CCAD5FFA0B.html>`__ to add a new LDAP Directory and point Workspace ONE Access to your AD installation.

Once these two steps are completed, AD users, groups, and attributes are available for use within Workspace ONE.

Set Up Built-In IDP
~~~~~~~~~~~~~~~~~~~

Integration with AD was completed using the built-in IDP option. When users attempt to authenticate to resources, they will be redirected to Workspace ONE Access for user and device authentication.

1. In the Workspace ONE Access console, navigate to **Integrations -> Identity Providers** and click **Add -> Built-in IDP**. Choose your AD directory created in the previous section.

2. Fill out details in the form pertaining to your installation.

3. Under **Users**, select the directory that you created in your previous integration with RadiantOne.

4. Under **Authentication Methods**, select Mobile SSO for both Android and iOS.

5. Choose **All Ranges** as the Network option.

6. Click **Save** in the bottom right corner.

VMware Unified Access Gateway (UAG)
------------------------------------

VMware Unified Access Gateway (UAG) helps enable secure remote access for users of virtual desktops, internal sites, applications, and file repositories.

UAG Setup
~~~~~~~~~

1. Open firewall rules depending on the services to be utilized. For this build, inbound TCP port 443 was opened to the destination IP of the UAG appliance. Port lists can be obtained here: `UAG port list <https://docs.vmware.com/en/Unified-Access-Gateway/2203/uag-deploy-config/GUID-F197EB60-3A0C-41DF-8E3E-C99CCBA6A06E.html>`__

2. Deploy the UAG appliance using the OVF Template Wizard from VMware. Follow instructions found in the deployment document here: `UAG Deployment Guide. <https://docs.vmware.com/en/Unified-Access-Gateway/2203/uag-deploy-config/GUID-537BD936-73B4-4902-A15D-5723295BA29E.html>`__ For this build, the following optional configuration variables were set:

   a. Size: Large

   b. Enable SSH

   c. Allow SSH root login using password

UAG Configuration
~~~~~~~~~~~~~~~~~

1. Access the UAG console using the IP address specified in the previous section. Log in with the admin account. On the Welcome Screen, choose **Configure Manually**.

2. If desired, change the system setting defaults by following this guide: `UAG System Configuration. <https://docs.vmware.com/en/Unified-Access-Gateway/2203/uag-deploy-config/GUID-F71E6283-E24B-49F5-8AC6-D28915CD41AD.html>`__

3. Enable **Edge Service Settings** at the top of the admin page. Click the gear next to **Tunnel Settings** and set the following information:

   a. API Server URL: the API URL of your tenant. VMware can provide this information.

   b. API Server username

   c. API Server password

   d. Organization Group ID (found in the UEM console)

   e. Tunnel Server Hostname: FQDN of your UAG appliance

Configure Workspace One Integration with UAG Tunnel
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. From the Workspace One UEM Console, configure the UAG Tunnel Connection using the `UEM Tunnel Configuration Guide <https://docs.vmware.com/en/VMware-Workspace-ONE-UEM/services/VMware_Tunnel/GUID-471260BA-4DDC-4BFE-B8C3-FA2DDC2116A1.html>`__ as a reference. For this build, the following configuration options were set:

   a. Deployment Type: Basic

   b. Hostname: hostname of the UAG appliance

   c. Port: 443

   d. Server Authentication: Airwatch

   e. Client Authentication: Airwatch

   f. Networking: disabled

   g. Logging: disabled

   h. No Custom Settings

2. From the Workspace One UEM Tunnel Configuration page, set up **Device Traffic Rule Sets** using the `Assign Traffic Rules Guide <https://docs.vmware.com/en/VMware-Workspace-ONE-UEM/services/VMware_Tunnel/GUID-007E716F-59FE-4148-B7AA-5F2584E91282.html>`__ as a reference. For this build, these settings were configured:

   a. Tunnel Mode: Per Application

   b. Rule 1: Chrome on Android

      i. Click on **Add Rule**. Under the Application dropdown, choose **Google Chrome**. Under the Action dropdown, select **TUNNEL**. For the Destination field, enter your Workspace Air Tenant URL.

   c. Rule 2: Other Web Browsers

      i. Click on **Add Rule**. Under the Application dropdown, choose **Safari - MacOS**, **Chrome - iOS**, **Chrome - Android**, **Chrome - WinRT**, and **Chrome - MacOS**. Under the Action dropdown, select **TUNNEL**. For the Destination field, list any URL resources that require traffic to be tunneled.

   d. Rule 3: **All Other Apps** set to BYPASS

   e. **Save** and **Publish** the rules once complete.

VMware NSX-T
------------

VMware NSX provides an agile software-defined infrastructure to build cloud-native application environments. NSX focuses on providing networking, security, automation, and operational simplicity for emerging application frameworks and architectures that have heterogeneous endpoint environments and technology stacks.

Setup and Installation
~~~~~~~~~~~~~~~~~~~~~~

NSX-T requires an existing vSphere cluster to operate with an existing vCenter server already installed. The high-level steps for installation are as follows:

1. Deploy the NSX Manager VM.

2.  Configure a vSphere Distributed Switch (VDS).

3. Create an uplink profile and configure host transport nodes.

4. Deploy two NSX Edge VMs to form an edge cluster.

5. Create and configure one tier-0 gateway for north-south traffic.

6. Create and configure a tier-1 gateway to route traffic from tenant VMs.

7. Create and configure a segment (logical switch) for tenant VMs.

8. Deploy a test VM to test north-south and east-west connectivity.

Step-by-step instructions can be found in the `NSX-T Quick Start Guide here <https://docs.vmware.com/en/VMware-NSX/4.1/quick_start/GUID-78489E7A-1F6F-4317-BD8B-DDF59FEF9860.html>`__.

Enable and Configure Identity Firewall in NSX-T
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Once NSX-T is configured, enable and configure Identity Firewall in NSX-T to provide ZTA features, including identity-specific network rules. The high-level procedure is as follows:

1. Enable NSX File Introspection driver and NSX Network Introspection driver (VMware Tools full installation adds these by default), or event log scraping. See `Identity Firewall Event Log Sources <https://docs.vmware.com/en/VMware-NSX/4.1/administration/GUID-508ED66D-FF4E-49A1-A3A7-C3150C387556.html#GUID-508ED66D-FF4E-49A1-A3A7-C3150C387556>`__. After configuring event log servers in the Active Directory, you need to turn on the Event Log Sources or Aria Operations for Logs.

2. `Enable Identity Firewall on DFW and GFW <https://docs.vmware.com/en/VMware-NSX/4.1/administration/GUID-0475A987-C612-483D-8CCF-01BE6DEE6952.html#GUID-0475A987-C612-483D-8CCF-01BE6DEE6952>`__. Identity Firewall must be activated for IDFW firewall rules to take effect.

3. Configure AD (required) and event log scraping (optional): `Configuring Active Directory and Event Log Scraping <https://docs.vmware.com/en/VMware-NSX/4.1/administration/GUID-8B60D22B-3119-48F6-AEAE-AE27A9372189.html#GUID-8B60D22B-3119-48F6-AEAE-AE27A9372189>`__. Active Directory is used in creating user-based Identity Firewall rules.

4. Configure AD sync operations: `Synchronize Active Directory <https://docs.vmware.com/en/VMware-NSX/4.1/administration/GUID-A1E49EF5-6B19-4D75-8696-F8B3EAE433F3.html#GUID-A1E49EF5-6B19-4D75-8696-F8B3EAE433F3>`__. Active Directory objects can be used to create security groups based on user identity, and identity-based firewall rules.

5. Create a group with AD group members: `Add a Group <https://docs.vmware.com/en/VMware-NSX/4.1/administration/GUID-9DFF6EE2-2E00-4097-A412-B72472596E4D.html#GUID-9DFF6EE2-2E00-4097-A412-B72472596E4D>`__. Groups include different objects that are added both statically and dynamically and can be used as the source and destination of a firewall rule.

6. Assign group with AD group members to a distributed firewall rule or gateway firewall rule. If creating a DFW rule using guest introspection, make sure that the **Applied to** field applies to the destination group: `Add a Distributed Firewall <https://docs.vmware.com/en/VMware-NSX/4.1/administration/GUID-41CC06DF-1CD4-4233-B43E-492A9A3AD5F6.html#GUID-41CC06DF-1CD4-4233-B43E-492A9A3AD5F6>`__. The distributed firewall monitors all the East-West traffic on your virtual machines. The **Source** field should be an AD-based group.

The full `Identity Firewall Workflow Guide can be found here <https://docs.vmware.com/en/VMware-NSX/4.1/administration/GUID-F15C4916-CEBF-47A0-A6A8-64428190B08D.html>`__.

Configure Segment Firewall for URL Blocking
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For this build we configured a Tier-1 Segment Firewall to block a subset of users from access specific URLs with the following rule and profile:

**Segment Firewall Rule Settings:**

-  Source: Active Directory Group “Test NSX Users”

-  Destination: Any

-  Services: HTTP, HTTPS

-  Applied To: T1

-  Action: Allow

-  Profile: URL Category

**“URL Category” Profile Settings:**

-  L7 Profile

-  Name: URL Category

-  Attribute Values: “Alcohol and Tobacco” and “Auctions”

-  Action: Reject with Response

-  Logging: Yes

-  Enabled: Yes

Configure Distributed Firewall Rule for VM to VM Blocking
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For this build we configured a Distributed Firewall rule to block VM to VM traffic with our vSphere cluster with the following rule configuration:

-  Sources: NSX Group “UseCaseGSubjectsGroup” (Virtual Machine Group)

-  Destinations: NSX Group “UseCaseGResourcesGroup” (Virtual Machine Group)

-  Services: Any

-  Applied To: DFW

-  Action: Reject

-  Enable: On

VMware Workspace ONE UEM
------------------------

Workspace ONE UEM provides endpoint management capabilities for this build and allows certificates to be provisioned for user authentication.

Setup
~~~~~

The cloud-based Workspace ONE UEM instance must be provisioned by VMware. After this has been completed, follow the `official Workspace ONE UEM documentation <https://docs.vmware.com/en/VMware-Workspace-ONE-UEM/services/rn/WorkspaceONEUEMDocumentation.html>`__ to deploy agents to each of your managed endpoints. Instructions for deploying profiles and compliance requirements to devices can also be found in the link above.

Integration with Active Directory
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Workspace ONE UEM integrates with your existing directory service - such as Active Directory, Lotus Domino, and Novell e-Directory - to provide directory-based account access. This type of account access lets users authenticate with Workspace ONE UEM apps and enroll devices using their existing directory service credentials. The Workspace One UEM `Directory Services Guide can be found here <https://docs.vmware.com/en/VMware-Workspace-ONE-UEM/services/Directory_Service_Integration/GUID-AWT-DIRECTORYSERVICESOVERVIEW.html>`__.

Application Deployment
~~~~~~~~~~~~~~~~~~~~~~

Internal (private) applications or public (App Store) applications can be deployed via UEM to provide services to endpoints. Google Chrome and VMWare's UAG Tunnel Application were both deployed as a public application via UEM to Android and iOS devices. All public applications follow the same deployment steps provided in the `Deploy Public Applications Guide <https://docs.vmware.com/en/VMware-Workspace-ONE-UEM/services/Application_Management/GUID-DeployPublicApps.html>`__ of the Workspace One UEM User Manual.

For macOS and Windows, the VMWare UAG Tunnel and Carbon Black Enterprise EDR agent were deployed as internal applications. All internal applications follow the same deployment steps provided in the `Deploy Internal Applications Guide <https://docs.vmware.com/en/VMware-Workspace-ONE-UEM/services/Application_Management/GUID-DeployInternalApplications.html>`__ of the Workspace One UEM User Guide.

VMware Workspace ONE MTD
------------------------

Workspace ONE MTD provides endpoint security and protection for iOS, Android, and Chrome OS, securing devices against app, device, OS, and network-based threats. Integrating MTD with Workspace ONE UEM empowers your organization to adopt secure mobility without compromising productivity.

Setup
~~~~~

The cloud-based Workspace ONE MTD instance must be provisioned by VMware. After this has been completed, log into your Workspace One MTD console to continue configuration.

Workspace One UEM Integration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Follow the `Workspace ONE MTD and UEM Configuration Guide <https://docs.vmware.com/en/VMware-Workspace-ONE/services/WS1-MTD/GUID-MTD-IntegrateWithWS1UEM.html>`__ to create an Organizational Unit in MTD and integrate UEM with Workspace One MTD.

Configure Device Enrollment
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Once UEM integration is complete, configure an enrollment group in UEM to automatically enroll devices from UEM into MTD by following the `Monitor Enrollment and Activation Guide here <https://docs.vmware.com/en/VMware-Workspace-ONE/services/WS1-MTD/GUID-MTD-Monitor-Enrollment-Activation.html>`__.

Configure and Enforce Compliance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Device Compliance and Threat Classification is configured once enrollment is complete. Devices can be placed into Low/Medium/High Risk groups depending on rule sets. Additionally, AllowList and DenyList URL sets may be configured to allow or block specific URLs on devices. `The Compliance and Threat Classification Configuration Guide can be found here. <https://docs.vmware.com/en/VMware-Workspace-ONE/services/WS1-MTD/GUID-MTD-Configure-Enforce-Compliance.html>`__

VMware Carbon Black Enterprise EDR
----------------------------------

VMware Carbon Black Enterprise EDR Standard is a next-generation antivirus (NGAV) and behavioral endpoint detection and response (EDR) solution that protects against the full spectrum of modern cyber-attacks. 

Setup
~~~~~

The cloud-based VMWare Carbon Black Enterprise EDR instance must be provisioned by VMware. After this has been completed, log into your Carbon Black Cloud console to continue configuration.

Carbon Black Cloud Sensor Installation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Carbon Black Endpoints require Cloud sensors for protection. Each Windows, Linux, macOS, or VDI endpoint will need a Cloud sensor installed to provide protection. Sensor installation instructions are provided in the `VMWare Carbon Black Cloud Sensor Installation Guide <https://docs.vmware.com/en/VMware-Carbon-Black-Cloud/services/cbc-sensor-installation-guide/GUID-76272E42-E534-47AD-8654-B2F3B5682806.html>`__.

Carbon Black Cloud Policies
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Once endpoints are configured, policies must be set to control endpoint behavior. Overall policy configuration is addressed in the `Managing Policies section of the VMWare Carbon Black Cloud User Guide. <https://docs.vmware.com/en/VMware-Carbon-Black-Cloud/services/carbon-black-cloud-user-guide/GUID-814C8950-5560-49D6-8E74-466ECE460D4F.html>`__

For this build, a “Deny Operation” rule was set in the “Blocking and Isolation” policy section for the process “/usr/local/bin/nmap”.

VMware Carbon Black Cloud 
--------------------------

VMware Carbon Black Cloud provides the visibility and control that DevOps and security teams need to secure Kubernetes clusters and the applications deployed on them. It delivers instant visibility into all workloads with the ability to enforce compliance, security, and governance from a single dashboard.

Setup
~~~~~

The cloud-based VMWare Carbon Black Cloud instance must be provisioned by VMware. After this has been completed, log into your Carbon Black Cloud console to continue configuration.

Add Existing Cluster to Carbon Black and Install Kubernetes Sensor on Cluster to Enable Carbon Black Cloud 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To complete the following steps, an existing Kubernetes cluster is required, along with terminal access to the cluster. `Step-by-step instructions are provided in the Kubernetes Sensor Installation Guide <https://docs.vmware.com/en/VMware-Carbon-Black-Cloud/services/cbc-sensor-installation-guide/GUID-9AF20C3A-BA0D-44AE-89B7-446F4D0028B3.html>`__.

Set Kubernetes Policies 
~~~~~~~~~~~~~~~~~~~~~~~~

Runtime and hardening policies can be set according to best practices in the `Carbon Black for Containers User's Guide <https://docs.vmware.com/en/VMware-Carbon-Black-Cloud/services/carbon-black-cloud-container-user-guide.pdf>`__. For this build, default rules and policies were used and were not changed.

VMware vSphere, vCenter, and vSAN
---------------------------------

Installation and configuration of vSphere, vCenter, and vSAN is outside the scope of this document. General information can be found here: https://docs.vmware.com/en/VMware-vSphere/index.html

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

DigiCert ONE
------------

For installation, configuration, and integration instructions, refer to :ref:`DigiCert ONE<digicert-one>`.
