Enterprise 1 Build 4 (E1B4) - SDP - Appgate SDP Controller as PE Product Guides
===================================================================================

.. include:: /_publication_note.rst

This section of the practice guide contains detailed instructions for installing, configuring, and integrating all the products used to implement E1B4. For additional details on E1B4's logical and physical architectures, please refer to :ref:`architecture and builds`.

Appgate
-------

The Appgate SDP solution has been designed with the intent to provide all the critical elements of zero trust. The Appgate SDP has a controller that offers PA and PE functionality, and gateways that offer PEP functionality. By providing highly performant, scalable, secure, integrated, and cloaked zero trust access, Appgate SDP is able to ensure that the correct device and user (under the appropriate conditions at that moment in time) are connected.

Appgate Installation and Configuration 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Appgate components for deployment are the controller and gateway. Prior to installation, admins should understand the `pre-installation considerations <https://sdphelp.appgate.com/adminguide/v6.1/pre-installationchecklist.html>`__ to deploy Appgate. These considerations include browser compatibility, network setup, identity providers, and DNS.

For this build, an Appgate controller and gateway are deployed on-prem as well as in the AWS IaaS cloud. Both the controller and gateway are deployed on the same server on-prem and in AWS.

For the on-prem installation, we used the instructions in the `Appgate SDP Installation from ISO into VMware <https://sdphelp.appgate.com/adminguide/v6.1/resources/Installation_Guide-VSphere.pdf>`__ guide.

For the Appgate install in AWS, we used the `Appgate SDP for AWS Deployment Guide <https://appgate-marketplace-public.s3.amazonaws.com/Appgate-SDP-for-AWS-StepByStep-Guide.pdf>`__.

After installation, the initial configuration is completed via `CLI (command-line interface) on the controller <https://sdphelp.appgate.com/adminguide/v6.1/controller-cz-setup.html>`__. Note: Gather various information about the network and IP addresses that are needed to configure the controller. Once the configuration is completed, an administrator can gain access to the GUI via ``https://controller-ip-address:8443`` on a browser.

Gateway configuration: As mentioned earlier, the gateway is deployed on the same server as the controller. Once logged into the controller, `deploy the gateway <https://sdphelp.appgate.com/adminguide/v6.1/adding-gateway-functionality.html>`__.

For this build, policies were created to allow users to access various resources on-premises and in the AWS IaaS environment for Enterprise 1. We leveraged the following tags, conditions, entitlements, and policies to allow employees access to all resources and contractors to certain resources.

-  Tags were used to differentiate which users were allowed access. Tags were created for employees, contractors, and mobile devices. Tags can be created when configuring a policy.

-  `Conditions <https://sdphelp.appgate.com/adminguide/v6.1/conditions.html>`__ were created for employees and contractors.

    -  Check endpoints and resources for compliance

    -  Appgate delegates to Ivanti to validate compliance for mobile devices

    -  Do a 10-minute reauthentication for high-value resources

    -  Validate user attributes pulled from Radiant Logic

-  An `entitlement <https://sdphelp.appgate.com/adminguide/v6.1/entitlements.html>`__ was created for four resources and applied with the appropriate tags. Resource1 and Resource2 were on-premises. Resource3 and Resource4 were in AWS. The employee tag was applied to all four resources. The contractor tag was applied to Resource2 and Resource4. Contractors did not have access to Resource1 and Resource3.

-  `Policies <https://sdphelp.appgate.com/adminguide/v6.1/policies.html>`__ were created for employees and contractors.

    -  The employee policy leveraged an identity provider for authentication, and validated that the user was an employee based on information retrieved from Radiant Logic. The employee tag was applied to this policy. Therefore, any entitlements and conditions applied with the same tag were applied to this policy.

    -  The same logic was applied to the contractor policy.

Appgate Clients
~~~~~~~~~~~~~~~

Appgate has clients for end users logging to desktop, laptop, and mobile devices for different OSes including Windows, Linux, macOS, iOS, and Android. `Installing clients <https://sdphelp.appgate.com/adminguide/v6.1/installing-clients.html>`__ require downloads for all clients' software, which are available `here <https://www.appgate.com/support/software-defined-perimeter-support/client>`__.

Headless clients were also installed to protect resources. From the same download page above, the Windows client is the same for both workstations/laptops and servers. For Linux clients, use the “Ubuntu Headless Client v6.x.x” instead of the full client. Instructions for installing `Windows <https://sdphelp.appgate.com/adminguide/v6.1/windows-headless.html>`__ and `Linux <https://sdphelp.appgate.com/adminguide/v6.1/linux-headless.html>`__ both use the command line.

Appgate Integrations
~~~~~~~~~~~~~~~~~~~~

For this build, Appgate integrates with Okta, Radiant Logic, Ivanti, and IBM.

For integration with Okta, which is used for authentication and authorization of the user to log in to the Appgate client, follow the `SAML configuration <https://sdphelp.appgate.com/adminguide/v6.1/identity-providers-configure.html>`__ instructions to create an identity provider in Appgate. Note: Certain information will be provided by Okta, so the integration configuration within Okta should be completed prior to this configuration.

For `integration configuration with Radiant Logic <https://sdphelp.appgate.com/adminguide/v6.1/identity-providers-configure.html>`__, the purpose is to identify users and additional attributes to verify compliance of a user. One attribute being leveraged is the groups attribute so Appgate can identify whether the user is an employee or contractor. We also leveraged several attributes such as BreakGlassScore, ClearanceValue, RiskLevel, and BehavorialRiskScore. A `User Claim Script <https://sdphelp.appgate.com/adminguide/v6.1/user-claims.html>`__ was leveraged to pull these attributes from Radiant Logic. If the user does not meet certain scores for these attributes, the user is denied entitlements to resources.

For integration with Ivanti, Appgate is trusting Ivanti's claim of whether a device is complaint or not. To perform this integration, a `User Claim Script <https://sdphelp.appgate.com/adminguide/v6.1/user-claims.html?anchor=user-claim-script>`__ was created. Note: Knowledge of JavaScript is required for this configuration.

To manage Appgate logs for large deployments, Appgate recommends using a `LogForwarder <https://sdphelp.appgate.com/adminguide/v6.1/audit-logs-intro.html>`__ to send logs to your log server or SIEM. For integration with IBM QRadar, we `configured the LogForwarder <https://sdphelp.appgate.com/adminguide/v6.1/audit-logs-intro.html>`__ to send logs to IBM QRadar.

Okta Identity Cloud
-------------------

For this build, the integration between Okta and Ivanti was disabled in Okta Identity Cloud. Users logging into a resource are authenticated via Okta with a password for the first factor and Okta Verify for the second factor. Users logging into Appgate SDP also use Okta for authentication. Use the link for `integration with Appgate <https://help.okta.com/en-us/Content/Topics/Apps/Apps_App_Integration_Wizard_SAML.htm>`__ to configure Okta. Note: Information such as Single Sign-on URL, Issuer, and other data created here are needed for the Appgate integration configuration.

No changes were made from Build 1 to the :ref:`Okta Verify App<okta-verify-app>` and :ref:`Okta Access Gateway<okta-access-gateway>`. Refer to those sections for configuration details.

Radiant Logic RadiantOne
------------------------

Additional attributes were added to the RadiantOne solution. These attributes allow other zero trust tools to create more granular policies for access. Within the Directory Namespace, we created namespaces for Clearance, Data Governance, Risk, and Training. Information pertaining to these categories was imported via flat files for the purpose of this build. For configuration instructions, refer to RadiantOne v7.4.4 Namespace Configuration Guide. We also updated RadiantOne's configuration with a `Global Database View <https://developer.radiantlogic.com/v7.4/global-identity-viewer-guide/01-introduction/>`__ of users combining these attributes with the AD directory and HR database. We leveraged the `Global Identity Builder <https://developer.radiantlogic.com/v7.4/global-identity-builder-guide/introduction/>`__ to perform this.

For integration with Appgate, a user ID was created in Radiant Logic as a service account for Appgate to be able to retrieve attributes. To create this, follow the instructions from :ref:`Radiant Logic RadiantOne Integration<radiant-integration>`.

SailPoint IdentityIQ
--------------------

No changes were made from Build 1. Refer to :ref:`SailPoint IdentityIQ Installation and Configuration<sailpoint-install>`.

Ivanti Neurons for UEM
----------------------

No significant changes were made from Build 1. Ivanti Neurons for UEM was configured to deploy the Appgate Client to managed devices. For information, configuration, and integration instructions, refer to :ref:`Ivanti Neurons for UEM<ivanti-neurons>`.

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

.. _aws-iaas:

Amazon Web Services is a cloud computing platform provided by Amazon that includes a mixture of IaaS, PaaS, and SaaS offerings. This section describes the setup of AWS IaaS resources to serve as a public/private cloud host.

For details on the logical architecture of the AWS environment, please refer to :ref:`IaaS - Amazon Web Services (AWS)`.

Appgate Controller Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Ensure the on-prem controller can reach the AWS segment on which the new controller will be installed. This controller will need to communicate with the on-prem controller. To install the controller in AWS, follow the prerequisites outlined in the `AWS Step by Step guide <https://appgate-marketplace-public.s3.amazonaws.com/Appgate-SDP-for-AWS-StepByStep-Guide.pdf>`__ and the steps to provision AWS resource for a new appliance (up to Step 1 of the guide). Once these steps are completed, log in to the on-prem Appgate controller user interface (UI) and follow the `Configuring a new appliance <https://sdphelp.appgate.com/adminguide/new-appliance.html>`__ instructions to deploy the AWS controller.

Zimperium Mobile Threat Defense (MTD)
-------------------------------------

For installation, configuration, and integration instructions, refer to :ref:`Zimperium Mobile Threat Defense<zimperium-mtd>`.
