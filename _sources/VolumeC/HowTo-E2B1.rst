Enterprise 2 Build 1 (E2B1) - EIG Crawl - Ping Identity Ping Federate as PE Product Guides
==============================================================================================

.. include:: /_publication_note.rst

This section of the practice guide contains detailed instructions for installing, configuring, and integrating all of the products used to implement E2B1. For additional details on E2B1's logical and physical architectures, please refer to :ref:`architecture and builds`.

Ping Identity PingOne
---------------------



Ping Identity PingOne is a SaaS solution that provides ICAM capabilities to an enterprise. The following sections describe the setup of PingOne and its PingFederate service, and various integrations to other products. Ping Identity integrates with Radiant Logic for identity information, and with Cisco Duo to delegate the second authentication factor for users accessing resources.

Configuration: PingOne and PingFederate
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _ping-one-config:

1. PingOne setup: From your web browser, type pingone.com and click the “Try Ping” at the top right of the screen. Follow the instructions to sign up.

2. Once the PingOne environment is set up and functioning, scroll down the screen and click on the PingFederate service. A new browser tab will open. Most of the configuration will be performed on PingFederate for this build.

3. Create an `IDP adaptor <https://docs.pingidentity.com/bundle/pingfederate-111/page/rgr1564002998046.html>`__. This configuration should include some required values like mail and group membership (these will be mapped in steps below to the policy contract) and this adaptor is used as the first authentication factor and will be applied in the policy in the next step.

4. `Create a policy <https://docs.pingidentity.com/bundle/pingfederate-110/page/qmq1564002987890.html>`__ contract as a list to map values to the connection(s). The policy contract will use a policy to fulfill the mappings from sources (such as LDAP or Third-Party Identity Provider using a Federated Hub).

5. Create an authentication policy that will be used to dictate application authentication. For our policies, we are using user ID and password for the first authentication factor (step 3 above) and Duo as the second authentication factor (Integration with Cisco Duo section).

6. `Create a policy contract <https://docs.pingidentity.com/bundle/pingfederate-110/page/aat1564002989773.html>`__ to connect that uses the above policy.

7. Configure `SAML application <https://docs.pingidentity.com/r/en-us/pingfederate-110/help_idpconnectionconfigtasklet_idpbrowserssostate>`__ integrations. Note that all applications are different. For our resources (applications), certain SAML formats and attributes are used. Follow the linked documentation above to configure the specific setup of your own application.

8. For this build, we developed policies that allow employees to access all resources (resource 1 and resource 2) and contractors to access resource 2 only. In order to do that, we leveraged the “memberof” attribute from Radiant Logic to identify employees and contractors. Once this information is identified, refer to:

   a. `Authentication Policies <https://docs.pingidentity.com/bundle/pingfederate-111/page/jul1564002986701.html>`__ to define the attribute mappings using this information

   b. `SAML applications <https://docs.pingidentity.com/r/en-us/pingfederate-110/help_idpconnectionconfigtasklet_idpbrowserssostate>`__ to configure issuance criteria to information retrieved from Radiant Logic

Integration with Radiant Logic
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _ping-one-integration:

1. For this build we installed a `PingOne Gateway <https://docs.pingidentity.com/bundle/pingone/page/djk1630007404580.html>`__, which is “on-premise software that allows PingOne to communicate with other systems like LDAP servers,” to communicate with RadiantOne. The PingOne Gateway was installed on a Windows Server on the same subnet as the RadiantOne server. We used the PingOne Gateway due to restrictions of multiple firewalls and NAT rules within our lab environments (some are not under our control) from allowing PingOne from the Internet to reach RadiantOne in Enterprise 2. In many environments, the LDAP gateway is not needed if NAT is not used, and opening the proper TCP/UDP ports on the enterprise firewalls will allow communication between PingOne and the on-prem resource. Note: Prerequisites and instructions for installing the gateway are available under **Connections/Gateway** in the PingOne console.

2. Once the Gateway is configured, click the **Add** button within the Connections/Gateway screen. Follow instructions on the screen to complete the integration with Radiant Logic. Note: A service account and other information from Radiant Logic is needed for the setup. Ensure this service account is created within Radiant Logic prior to configuring the PingOne Gateway.

3. From PingFederate, go to **Data Stores** and create a **New Data Store** for Radiant Logic. Select **LDAP** for your **LDAP Type** and fill in the variables to complete the configuration.

Integration with Cisco Duo
~~~~~~~~~~~~~~~~~~~~~~~~~~

Make sure that configuration from Cisco Duo is completed before performing the integration.

For `IDP application integration <https://docs.pingidentity.com/bundle/pingfederate-111/page/rgr1564002998046.html>`__, from the **Authentication** tab, select **IDP Adaptors**, and click **Create New Instance** to create the integration with Cisco Duo to use Duo MFA as the second authentication factor. Specific API configuration information that was created from Cisco Duo is needed here to complete the setup.

Note: For this build, we are using Duo, although Ping Identity has its own MFA.

Radiant Logic RadiantOne
------------------------

Installation and Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Refer to :ref:`Radiant Logic RadiantOne Installation and Configuration<radiant-install>`.

Integration
~~~~~~~~~~~

Refer to :ref:`Radiant Logic RadiantOne Integration<radiant-integration>` for integration with SailPoint.

For integration with Ping Identity, a service account was created in RadiantOne. This service account, along with various credential information is used by PingFederate to communicate with RadiantOne to authenticate users. The communication between RadiantOne and PingFederate is through the Ping Gateway, which was installed on the same subnet as RadiantOne.

SailPoint IdentityIQ
--------------------

Installation and Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Refer to :ref:`SailPoint IdentityIQ Installation and Configuration<sailpoint-install>`.

Integration with Radiant Logic
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Refer to :ref:`SailPoint IdentityIQ Integration with Radiant Logic<sailpoint-integration-radiant>`.

Integration with AD
~~~~~~~~~~~~~~~~~~~

Refer to :ref:`SailPoint IdentityIQ Integration with AD<sailpoint-integration-ad>`.

Integration with Ping Identity
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

There is no integration with Ping Identity. For this build, SailPoint provides AD user information and Duo pulls from AD.

Cisco Duo
---------

Cisco Duo is a SaaS solution that implements and enforces security policies and processes, using strong authentication to reduce the risk of data breaches due to compromised credentials and access from unauthorized devices. For this build, we use Cisco Duo as the second authentication factor for resources.

Configuration
~~~~~~~~~~~~~

.. _cisco-duo-config:

Sign up with Cisco Duo to create a Duo instance. Once you have admin access, create policies and integration with AD and Ping Identity.

`Create a policy <https://duo.com/docs/policy#global-policy>`__ to enable MFA for users. Navigate to **Policy** and click **Edit Global Policy**. In the Global Policy, there are many sub-policies that can be applied. For this build, we enabled the following:

-  New User policy: prompt any user without the Duo app to enroll

-  Authentication policy: require two-factor

-  Authentication methods: Duo Mobile app (Duo Push)

-  Device Health application: enable macOS and Windows (note: these are the only operating systems that are capable of device health monitoring when installed with Cisco Duo.)

-  Custom Policies: create a policy to monitor device health if the authentication request comes from PingFederate. Self-enrollment is enabled so users will be prompted to install a Duo client on the end device for health monitoring. For this build, users will not be given access to a resource if their macOS or Windows firewall is turned off. There are other health checks available.

Integration
~~~~~~~~~~~

.. _cisco-duo-integration:

For integration with PingFederate, navigate to **Applications** and `click Protect an application <https://duo.com/docs/pingfederate>`__. Follow the instructions to complete the configuration. Note the three pieces of information provided: Client ID, Client secret, and API hostname. This information will be used to configure the integration within PingFederate to communicate with Duo.

For integration with `Microsoft Active Directory <https://duo.com/docs/directorysync>`__, navigate to **Users** and click on **Directory Sync**. Follow the instructions to configure the AD integration. A `Duo Authentication Proxy <https://duo.com/docs/authproxy-overview>`__ is needed for this build since the Enterprise 2 AD is not visible to the Internet.

Palo Alto Networks Next Generation Firewall
-------------------------------------------

.. _palo-alto-ngfw:

In this build, a dedicated Palo Alto Networks Next Generation Firewall (NGFW) virtualized system was deployed as a security and access control device. The Palo Alto Networks virtualized systems (vsys) are separate, logical firewall instances within a single physical Palo Alto Networks firewall. Each vsys is an independent, separately managed firewall with its traffic kept separate from the traffic of other virtual systems. The firewall provides `zone-based network filtering <https://docs.paloaltonetworks.com/pan-os/10-1/pan-os-admin/getting-started/segment-your-network-using-interfaces-and-zones>`__ for both inbound and outbound traffic, including remote access VPNs using the GlobalProtect clients.

Prior to the deployment of the vsys, the `initial configuration <https://docs.paloaltonetworks.com/pan-os/10-1/pan-os-admin/getting-started/integrate-the-firewall-into-your-management-network/perform-initial-configuration>`__ of the physical firewall was performed. `Creating a vsys <https://docs.paloaltonetworks.com/pan-os/10-1/pan-os-admin/virtual-systems/configure-virtual-systems>`__ requires the following:

-  A superuser administrative role

-  A configured interface

-  A Virtual Systems license

Once the vsys has been deployed, we `created a security policy <https://docs.paloaltonetworks.com/pan-os/10-1/pan-os-admin/getting-started/set-up-a-basic-security-policy>`__ for filtering the inbound and outbound traffic.

For GlobalProtect VPN access installation instructions, visit: https://docs.paloaltonetworks.com/globalprotect/10-1/globalprotect-admin/globalprotect-quick-configs/remote-access-vpn-authentication-profile

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
