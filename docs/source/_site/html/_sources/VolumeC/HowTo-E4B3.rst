Enterprise 4 Build 3 (E4B3) - EIG Run - IBM Security Verify as PE Product Guides
===================================================================================

.. include:: /_publication_note.rst

This section of the practice guide contains detailed instructions for installing, configuring, and integrating all the products used to implement E4B3. For additional details on E4B3's logical and physical architectures, please refer to :ref:`architecture and builds`.

IBM Security Verify
-------------------

IBM Security Verify is a cloud-based SaaS that operates as the Policy Engine and ICAM for Enterprise 4 and provides a variety of services including SSO, multifactor and passwordless authentication, adaptive access, identity lifecycle management, and identity analytics.

Setup
~~~~~

IBM provisioned a new instance of IBM Security Verify for this build.

Integration with Active Directory
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To integrate with Active Directory, an IBM Security Verify Bridge agent was installed on an on-premises server running Microsoft Windows Server 2019. To replicate this process, follow the instructions in the `official IBM documentation <https://www.ibm.com/docs/en/security-verify?topic=bridge-installation>`__. Completing this integration will add AD as an available identity source in IBM Security Verify.

Configuration
~~~~~~~~~~~~~

For this build, configuration focused on several areas. First, the integration with applications/resources needed to be configured. With the AD integration completed, users, groups, and attributes can now be managed, and authentication methods can be set up. Finally, access policies can be defined and implemented.

1. Add/configure connected applications.

   a. Begin the application configuration using the `official IBM documentation <https://www.ibm.com/docs/en/security-verify?topic=applications-managing-your>`__.

   b. In this build, SAML was configured to allow for user authentication. Follow the `official IBM documentation <https://www.ibm.com/docs/en/security-verify?topic=sign-configuring-saml-single-in-identity-provider>`__ for instructions on this step.

2. Users, groups, and attributes were managed using the `official IBM documentation <https://www.ibm.com/docs/en/security-verify?topic=managing-directories>`__. This allowed the configured policies to make decisions using user and group attributes.

3. Create security policies. There are a variety of pre-built policies available that can be utilized in different scenarios. For example, one of the pre-built policies will deny access to any device that is not in compliance with MaaS360 policy. Custom policies can also be built based on a range of criteria, including user and group attributes. Additional information on creating/editing policies can be found in the `official IBM documentation <https://www.ibm.com/docs/en/security-verify?topic=security-managing-access-policies>`__.

IBM Security Trusteer
---------------------

IBM Security Trusteer is a cloud-based SaaS that integrates with IBM Security Verify and uses cloud-based intelligence, AI, and machine learning (ML) to holistically identify new and existing users while improving the overall user experience by reducing the friction created with traditional forms of MFA. Within a ZTA, Trusteer acts as a risk engine that improves the efficacy of policy decisions enforced by various identity and access management solutions.

Integration with IBM Security Verify
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To act as a risk engine in this build, IBM provisioned a new Trusteer instance and linked it with IBM Security Verify. This action must be completed by an IBM representative.

IBM Security MaaS360
--------------------

IBM Security MaaS360 cloud-based SaaS provides endpoint management capabilities for both user workstations and user mobile devices through agents installed on each endpoint, supporting both BYOD and corporate-owned device usage.

Setup
~~~~~

IBM provisioned a new cloud-based instance of IBM Security MaaS360 for this build.

Configuration
~~~~~~~~~~~~~

The majority of MaaS360 configuration for this build was completed by building policies to apply to user or device groups.

1. Configure user and device groups. Group configuration instructions can be found in the `official IBM documentation <https://www.ibm.com/docs/en/maas360?topic=guide-groups>`__.

2. Build and apply policies to groups. Instructions for building these policies can be found in the `official IBM documentation <https://www.ibm.com/docs/en/maas360?topic=guide-security>`__.

3. Once these groups have been built and policies have been applied, policy enforcement can begin.

IBM Security QRadar XDR
-----------------------

For installation, configuration, and integration instructions, refer to :ref:`IBM Security QRadar XDR<ibm-qradar>`.

Integration with IBM Security MaaS360
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

QRadar was integrated with MaaS360 using the `official IBM documentation <https://www.ibm.com/docs/en/dsm?topic=maas360-security>`__.

Integration with IBM Security Verify
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

QRadar was integrated with Verify using the `official IBM documentation <https://www.ibm.com/docs/en/dsm?topic=security-verify-formerly-known-as-cloud-identity>`__.

IBM Security Guardium
---------------------

IBM Security Guardium is a data security platform that protects sensitive and regulated data across with compliance enforcement, sensitive data discovery, data encryption, and risk reduction. This build utilized two Security Guardium products: Guardium Data Protection and Guardium Data Encryption.

IBM Security Guardium Data Protection
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Guardium Data Protection is a unified data security solution that provides data discovery and classification, data activity monitoring and analytics, real-time response to threats, and automated compliance auditing and reporting. For this build, a single Guardium Data Protection appliance was deployed in VMware to serve as a data collector.

Appliance Installation and Configuration
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Create a new virtual machine using `IBM's recommended requirements <https://www.ibm.com/support/pages/node/6599135>`__.

2.  Boot from the IBM-provided Guardium Data Protection ISO using the `IBM Guardium installation guide. <https://www.ibm.com/docs/en/guardium/11.5?topic=system-step-3-install-guardium-image>`__

3.  Choose **standard installation** at the boot prompt. Once the install completes, on first boot the appliance will ask the user to choose Collector or Aggregator mode. Choose **Collector**.

4.  After the installer finishes, log into the appliance console using the default credentials.

5.  Complete the initial setup and configuration for the appliance using the `IBM Guardium setup guide <https://www.ibm.com/docs/en/guardium/11.5?topic=system-step-4-set-up-initial-basic-configuration>`__. Reboot the appliance when configuration changes are complete.

6.  Log into the appliance command line and add a QRadar instance as a remote logger with the `command <https://www.ibm.com/docs/en/guardium/11.5>`__.

7. Log into the Guardium Data Protection web console at https://<ip address>:8443

8. Confirm remote log forwarders are configured by clicking on **Tools** \| **Tools and Views** \| **Remote Loggers**. Each daemon should have a green checkmark.

IBM Security Guardium Data Encryption
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Guardium Data Encryption is a data encryption suite that can safeguard files and databases, provide in-application encryption, manage encryption keys, and enforce access policies for data.

Appliance Installation & Configuration
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The Guardium Data Encryption platform for this build requires a local appliance installation on the Enterprise 4 VMware farm.

1. Obtain the latest .ova image from IBM for the IBM Security CipherTrust Manager software.

2. `Follow the install guide <https://thalesdocs.com/ctp/cm/2.7/get_started/deployment/virtual-deployment/cloud-init-deploy/index.html>`__ to deploy the IBM Security CipherTrust Manager on a new virtual machine with the cloud-init configuration enabled to set the static IP address.

3. On boot, access the assigned IP address of the CipherTrust Manager with a web browser and enter a user's public SSH key for administrator access. The CipherTrust Manager is not functional until this key is entered.

4. Change the default administrator password.

5. Under **Admin Settings** \| **Licensing**, enter a license key or click on **Start CipherTrust Evaluation** to license the appliance.

S-TAP Installation and Configuration
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Install the appropriate S-TAP agent on any client machines that require monitoring. For this build the Windows S-TAP agent was deployed on the Microsoft SQL Server Express 2019 using `IBM's install guide <https://www.ibm.com/docs/en/guardium/11.5?topic=wuiiwiuust-windows-installing-s-tap-agent-by-using-interactive-installer>`__. The S-TAP agent appliance IP address used during setup is from the IBM Guardium Data Protection Collector configured in the previous section.

2. Confirm S-TAP control from the IBM Guardium Data Protection Collector web console by accessing the `S-TAP control menu <https://www.ibm.com/docs/en/guardium/11.5?topic=wcst-windows-configuring-s-tap-in-s-tap-control-page>`__ and verifying the client machine appears with a green checkmark.

Client Machine Setup and Configuration
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The client machine for this build is a Windows 2019 Server running Microsoft SQL Server Express 2019.

1. From the Guardium Data Encryption web console, create a registration token for the client machine `following the steps in the CipherTrust Manager Administration Guide <https://thalesdocs.com/ctp/cm/2.11/admin/cm_admin/client-management/index.html>`__.

2. Copy and save the registration token created in step 1.

3. From the Guardium Data Encryption web console, manually create a new client entry for the client machine following the steps in `the CipherTrust Data Encryption Guide <https://thalesdocs.com/ctp/cm/2.11/admin/cte_ag/clients/index.html>`__. For this build, password registration was used to register the client with a user-generated password.

4. Install the CipherTrust Transparent Encryption client software on the client machine. Choose **Register CipherTrust Transparent Encryption Now** at the end of the installation. These parameters were used for this build:

    a. Components: File System

    b. Host name of key manager: IP/DNS of the Guardium Data Encryption Appliance

    c. Enable **hardware association** and **LDT feature**.

    d. On the host screen, paste the ASCII token from Step 2 into the **Registration Token** field. Leave the remaining fields blank.

    e. Click **Next** and then **Finish** once the client is registered. Restart the client machine.

GuardPoint Configuration
^^^^^^^^^^^^^^^^^^^^^^^^

A GuardPoint specifies the list of folders that contain paths to be protected. Access to files and encryption of files under the GuardPoint are controlled by security policies. More information on Guardpoints can be found in the `Guardium Data Encryption GuardPoint Guide <https://thalesdocs.com/ctp/cm/2.11/admin/cte_ag/guardpoints/index.html>`__.

1. Create two user sets, one for full and one for limited/no access using the `CipherTrust Transparent Encryption Guide <https://thalesdocs.com/ctp/cm/2.11/admin/cte_ag/cte-policies/policy-elements/index.html#creating-user-sets>`__. For this build, the Admins User Set will have no access to a protected directory while the AppUsers User Set will have full access.

2. Create a new Standard Policy using the `CipherTrust Transparent Encryption Guide <https://thalesdocs.com/ctp/cm/2.11/admin/cte_ag/cte-policies/create-policies/index.html>`__. Name it “File Access Policy” and create Security rules for file access based on a User Set.

3. Follow the `CipherTrust Transparent Encryption Guide <https://thalesdocs.com/ctp/cm/2.11/admin/cte_ag/cte-policies/create-policies/index.html>`__ using Step 2 to create a new Key Rule and a new encryption key.

4. Once the policy is created, check the order of the Key Rules from the Policies Menu on the web console. If they are out of order, reorder them according to Step 2.

5. Create “encrypted” and “unencrypted” folders on the client machine to test access policies.

6. From the web console, create an AutoDirectory GuardPoint using the `CipherTrust Transparent Encryption Guide <https://thalesdocs.com/ctp/cm/2.11/admin/cte_ag/guardpoints/create-guardpoints/std-gps/index.html>`__. Use the Policy created in Step 2 and point the GuardPoint to the “encrypted” folder created in Step 5.

7. Confirm access is restricted by logging into the client machine with a user from each UserSet.

IBM Cloud Pak for Security (CP4S)
---------------------------------

The IBM Cloud Pak for Security (CP4S) platform enables the integration of existing security tools and provides understanding and management of threats in the environment.

Installation
~~~~~~~~~~~~

Refer to :ref:`IBM Cloud Pak for Security<ibm-cp4s>` for installation instructions.

CP4S and QRadar Integration
~~~~~~~~~~~~~~~~~~~~~~~~~~~

For this build, QRadar was integrated into CP4S as a data source for events from other resources.

1. Install the `QRadar SOAR app plugin <https://www.ibm.com/docs/en/qradar-common?topic=i-installing-app>`__ on the QRadar instance.

2. Configure the QRadar SOAR app plugin to connect to the CP4S instance using an API key. Follow the instructions in the `IBM QRadar SOAR app plugin Configuration Guide <https://www.ibm.com/docs/en/qradar-common?topic=configuration-configuring-app>`__.

3. An IBM Edge Application Gateway must be installed first to connect CP4S to QRadar. Install the Edge Gateway appliance in your virtual environment `following the IBM installation guide <https://www.ibm.com/docs/en/cloud-paks/cp-security/saas?topic=gateway-installing-virtual-application>`__.

4. `Pair the IBM Cloud Pak for Security account with the Edge Gateway <https://www.ibm.com/docs/en/cloud-paks/cp-security/saas?topic=installation-pairing-cloud-pak-security-account-edge-gateway>`__ appliance.

5. `Finish creating the Edge Gateway <https://www.ibm.com/docs/en/cloud-paks/cp-security/saas?topic=i-creating-edge-gateway>`__ with the pairing information from Step 4.

6. Follow the `IBM guide to add QRadar as a data source <https://www.ibm.com/docs/en/cloud-paks/cp-security/saas?topic=udic-security-qradar>`__ to CP4S.

CP4S Playbooks
~~~~~~~~~~~~~~

A CP4S Playbook is a set of rules, conditions, business logic, workflows, and tasks used to respond to a case/incident. For this build, IBM provided a test playbook to disable accounts in IBM Security Verify when multiple failed logins were detected in QRadar. Playbook design suggestions and instructions can be found in the `IBM Cloud Pak for Security SOAR Guide <https://www.ibm.com/docs/en/cloud-paks/cp-security/saas?topic=started-playbook-designer>`__.

IBM Cloud
---------

IBM Cloud provides compute, networking, and storage services that enable the creation of an enterprise IT infrastructure by subscribers.

1. Start with setting up the IPsec tunnel between IBM Cloud and the on-prem data center as shown `here <https://cloud.ibm.com/catalog/infrastructure/ipsec-vpn>`__.

2. Build the components in the IBM Cloud using the `architecture <https://www.ibm.com/cloud/architecture/architectures/virtual-private-cloud/reference-architecture>`__ and `configuration guide <https://cloud.ibm.com/docs>`__.

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

.. _digicert-one:

This build utilized DigiCert ONE, a cloud-based enterprise PKI manager. This service was instantiated by DigiCert and set up using `the official DigiCert ONE documentation <https://docs.digicert.com/en/digicert-one.html>`__.

Palo Alto Networks Next Generation Firewall
-------------------------------------------

For installation, configuration, and integration instructions, refer to :ref:`Palo Alto Networks Next Generation Firewall<palo-alto-ngfw>`.

VMware
------

The VMware environment was used for on-premises virtualized infrastructure hosting enterprise resources and consisted of three vSAN clusters. The VMware vSAN installation and configuration guide `can be found here <https://docs.vmware.com/en/VMware-vSphere/8.0/vsan-planning/GUID-3332D48C-E8F2-4462-BC30-60C9532C624C.html>`__.
