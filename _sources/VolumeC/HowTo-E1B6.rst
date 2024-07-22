Enterprise 1 Build 6 (E1B6) - SDP and Microsegmentation - Ivanti Neurons for Zero Trust Access as PEs Product Guides
====================================================================================================================

.. include:: /_publication_note.rst

This section of the practice guide contains detailed instructions for installing, configuring, and integrating all the products used to implement E1B6. For additional details on E1B6's logical and physical architectures, please refer to :ref:`architecture and builds`.

Ivanti Neurons for Zero Trust Access (nZTA)
-------------------------------------------

Ivanti Neurons for Zero Trust Access (nZTA) is a cloud-based SaaS application. The nZTA consists of a controller, gateway(s), and secure access clients. The nZTA controller is the policy decision point of the solution. The nZTA gateway is the policy enforcement point. Once the nZTA SaaS solution instance is created and enabled by an Ivanti representative, the controller will be active and available to be configured. Use `this link <https://help.ivanti.com/ps/help/en_US/nSA/22.x/nsa-zta/ag/pzta_oview.htm#Deployin>`__ for an overview of deployment and usage of nZTA.

Note: Once the administrator logs into the controller for the first time, the onboarding wizard will show up. The wizard can be leveraged to configure the authentication policies, gateways, and applications policies. The administrator can also skip the onboarding process and manually configure each task. For this build, the onboarding wizard was not used.

To configure authentication policies, this build leveraged local authentication for administrators and SAML authentication using Okta as the IdP. For local authentication policies, use the `Workflow: Creating a Local Authentication Policy <https://help.ivanti.com/ps/help/en_US/nSA/22.x/nsa-zta/ag/tadmin_user_auth.htm?Highlight=authentication%20policy#Workflow>`__ section of the Ivanti Neurons for Zero Trust Access Tenant Admin Guide. For SAML authentication policies, follow the instructions in :ref:`Okta Identity Cloud<okta-e1b6>`.

To create nZTA gateways, follow :ref:`Ivanti nZTA Gateway`.

For this build, policies were created to allow users to access various resources on-premises and in the AWS IaaS environment for Enterprise 1. To create the policies, the following items need to be configured:

-  Manage Applications - Create definitions of applications to which your end users require access and multiple applications that can leverage the same secure access policy. Follow the `Working with Applications and Application Groups <https://help.ivanti.com/ps/help/en_US/nSA/22.x/nsa-zta/ag/tadmin_app_grp.htm#top>`__ section of the Admin guide for configuration details.

-  Manage Devices - Define how endpoints access cloud and on-premises applications. Follow the `Creating Device Policies and Device Policy Rules <https://help.ivanti.com/ps/help/en_US/nSA/22.x/nsa-zta/ag/tadmin_dev_p.htm#top>`__ section of the Admin guide for configuration details.

-  Manage Users - User rules and user groups can be created to apply to authentication policies. Follow the `Creating User Rules and User Groups <https://help.ivanti.com/ps/help/en_US/nSA/22.x/nsa-zta/ag/tadmin_user_auth.htm#Creating>`__ section of the Admin guide for configuration details.

Once user, device, and application configuration are completed, access policies can be created to allow endpoints access to resources. Follow the `Creating/Editing Secure Access Policies <https://help.ivanti.com/ps/help/en_US/nSA/22.x/nsa-zta/ag/tadmin_sec_acc_p.htm#top>`__ section of the Admin guide for configuration details.

Note: In this build, we have policies that allow users to access resources on-prem and in the cloud. Users are grouped into several categories such as employees, contractors, and administrators. Resources are assigned to the users based on the groups they are assigned to. For example, administrators have access to a resource that no other groups have access to.

Ivanti nZTA Gateway
--------------------

For this build, an Ivanti nZTA gateway is deployed on-premises as well as in the IaaS cloud. To deploy the Ivanti nZTA gateway in both locations, leverage the `Working with Gateways <https://help.ivanti.com/ps/help/en_US/nSA/22.x/nsa-zta/ag/tadmin_cr_gway.htm#top>`__ document. In our build, our on-premises gateway was built in VMware vSphere and our cloud gateway was built in AWS. Specific documentation for deployment can be found under the “\ `Workflow: Creating a Gateway in VMware vSphere <https://help.ivanti.com/ps/help/en_US/nSA/22.x/nsa-zta/ag/tadmin_cr_gway.htm#Workflow>`__\ ” and “\ `Workflow: Creating a Gateway in Amazon Web Services <https://help.ivanti.com/ps/help/en_US/nSA/22.x/nsa-zta/ag/tadmin_cr_gway.htm#Workflow2>`__\ ” section of the Working with Gateways document.

Note: For this build, we used manual settings (selected in a check box when creating the gateway on the nZTA controller) and added the IP and DNS addresses.

Okta Identity Cloud
-------------------

.. _okta-e1b6:

For integration with Okta, refer to the `SAML Authentication section <https://help.ivanti.com/ps/help/en_US/nSA/22.x/nsa-zta/ag/pzta_oview.htm#SAML>`__ of the Ivanti Neurons for Zero Trust Access Tenant Admin Guide. This will allow a user to login to the Secure Access Client using Okta as the identity provider.

No additional changes were made to Build 1. Refer to :ref:`Okta Identity Cloud<okta-identity-cloud>`.

Radiant Logic RadiantOne
------------------------

No changes were made from Build 1. Refer to :ref:`Radiant Logic RadiantOne<radiant-one>`.

SailPoint IdentityIQ
--------------------

No changes were made from Build 1. Refer to :ref:`SailPoint IdentityIQ Installation and Configuration<sailpoint-install>`.

Ivanti Secure Access Client
---------------------------

To use the Ivanti Secure Access Client, end user devices must be enrolled. Use this `link <https://help.ivanti.com/ps/help/en_US/nSA/22.x/nsa-zta/ag/tadmin_enrol_client.htm#top>`__ to enroll various operating systems. Windows, macOS, and Linux devices were enrolled in this build.

Once the client is installed and user device is enrolled, use the `Using Ivanti Secure Access Client with nZTA section of the admin guide <https://help.ivanti.com/ps/help/en_US/nSA/22.x/nsa-zta/ag/tadmin_client.htm#top>`__ for connection configuration.

Note: Once enrolled and logged in, the Ivanti Secure Access Client will display the resources that the endpoint has access to.

IBM Security QRadar XDR
-----------------------

To integrate with IBM QRadar, follow the “Using Enterprise Integration to Export Your Logs for External Analysis” section of the `Ivanti Neurons for Zero Trust Access Tenant Admin Guide <https://help.ivanti.com/ps/help/en_US/nSA/22.x/nsa-zta/ag/tadmin_entint.htm?Highlight=syslog>`__.

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

For details on the logical architecture of the AWS environment, please refer to :ref:`iaas - amazon web services (aws)`.
