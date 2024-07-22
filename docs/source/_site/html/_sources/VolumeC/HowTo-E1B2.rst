Enterprise 1 Build 2 (E1B2) - EIG Run - Zscaler ZPA Central Authority (CA) as PE Product Guides
================================================================================================

.. include:: /_publication_note.rst

This section of the practice guide contains detailed instructions for installing, configuring, and integrating all of the products used to implement E1B2. For additional details on E1B2's logical and physical architectures, please refer to :ref:`architecture and builds`.

Zscaler
-------

Zscaler provides secure user access to public-facing sites and on- or off-premises private applications via the Zscaler Zero Trust Exchange, a cloud-delivered security service edge technology. The Zscaler Internet Access (ZIA) manages user access to the internet. Zscaler Private Access (ZPA) manages user access to applications within an enterprise. Zscaler integrates with Okta for authentication and authorization of users.

To begin, contact Zscaler to create an instance of ZIA and ZPA. To do this, Zscaler will need the FQDN of the enterprise using ZIA and ZPA. Admin user information will need to be provided to Zscaler to create admin accounts. Refer to documents for `ZIA <https://help.zscaler.com/zia>`__ and `ZPA <https://help.zscaler.com/zpa>`__.

Zscaler ZPA Configuration and Integration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Once admin access is available, log in to ZPA to perform the following:

1. Create additional `admin accounts <https://help.zscaler.com/zpa/about-administrators>`__ as needed.

2. Create a `Zscaler App Connector Group <https://help.zscaler.com/zpa/about-connector-groups>`__ and `Zscaler App Connector <https://help.zscaler.com/zpa/configuring-connectors>`__ in the ZPA portal. Note: App Connector Groups are recommended by Zscaler for availability and scaling. Note: This build has two App Connector Groups, one for on-prem applications and one for cloud applications in AWS.

3. Once the App Connector is configured in the ZPA portal, install the actual Zscaler App connector. Refer to the Zscaler Application Connector section below. Note: This build has two App Connectors, one for on-prem applications and one for cloud applications in AWS.

4. `Create integration with Okta <https://help.zscaler.com/zpa/configuring-idp-single-sign>`__. All users accessing resources within the enterprise will use two-factor authentication when logging into the Zscaler Client Connector. Note: Step 1 of configuration is completed in the Okta cloud. Refer to :ref:`Okta Identity Cloud<okta-e1b2>`. Step 2 of configuration is completed on the ZPA admin portal.

5. Deploy Zscaler Client Connectors (ZCCs) for various endpoints, including configuring ZCC policies to control the settings and behavior of ZCC. Refer to the Zscaler Client Connector section below.

6. Set up `ZPA Application configuration <https://help.zscaler.com/zpa/about-applications>`__ for access to resources. In this step, applications are defined and applied to segments so that the proper App Connector can perform PEP functions.

7. Configure `Access Policies <https://help.zscaler.com/zpa/about-policies>`__ to control user access to various applications. For our policies, we defined specific App Segments, configured specific IDP authentication parameters, and configured client posture checks.

8. Configure a `log receiver <https://help.zscaler.com/zpa/configuring-log-receiver>`__ for the IBM QRadar SIEM tool to receive logs for ZPA.

Zscaler ZIA Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~

Once admin access is available, log in to ZIA to perform the following:

1. Create additional `admin accounts <https://help.zscaler.com/zia/configuring-role-based-administration>`__ as needed.

2.  Set up `IdP integration <https://help.zscaler.com/zia/configuring-saml>`__ with Okta.

3.  `Create policies <https://help.zscaler.com/zia/documentation-knowledgebase/policies>`__ to manage user access to various resources on the internet. For this build, we used many of the defaults built into ZIA. We created policies to allow certain users access to a resource on the internet and to block certain users based on their role and time of day.

4. `Integrate ZIA Nanolog Streaming Service with IBM QRadar SIEM tool <https://help.zscaler.com/zia/zia-ibm-qradar-deployment-guide>`__ to receive ZIA logs.

Zscaler Client Connector
~~~~~~~~~~~~~~~~~~~~~~~~

`Zscaler Client Connectors (ZCCs) <https://help.zscaler.com/client-connector/step-step-configuration-guide-zscaler-client-connector>`__ are available for Windows, macOS, Linux, iOS, and Android endpoints. Deployment of ZCC includes configuring ZCC policies to control the settings and behavior of ZCC. For all these endpoints, a device manager can be leveraged to push the ZCC. For this build, we tested the use of Ivanti to push ZCC to Windows, iOS, and Android endpoints. For other devices we manually installed ZCC. Once ZCC is installed, users are prompted to log in, which allows the user and device to be managed by ZPA and ZIA, depending on the type of resource the user is accessing.

Zscaler Application Connector
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The Zscaler Application Connector is installed and configured on the same subnet where the resource will be protected. For this build, we use the documentation for `Linux OS <https://help.zscaler.com/zpa/connector-deployment-guide-centos-oracle-and-redhat>`__ to install the App Connector. Zscaler supports other `operating systems <https://help.zscaler.com/zpa/about-connectors>`__. Repeat steps 1 and 2 in the configuration section if an application residing in a different subnet segment needs to be protected. If that application is in the same subnet, then only one App Connector is needed to protect both applications.

Okta Identity Cloud
-------------------

.. _okta-e1b2:

For this build, the integration between Okta and Ivanti was disabled in Okta Identity Cloud. Users logging into a resource are authenticated via Okta with a password for the first factor and Okta Verify for the second factor. Use the link for `integration with Zscaler <https://help.zscaler.com/zpa/configuration-guide-okta>`__ to configure Okta.

No changes were made from Build 1 to the :ref:`Okta Verify App<okta-verify-app>` and :ref:`Okta Access Gateway<okta-access-gateway>`. Refer to those sections for configuration details.

Radiant Logic RadiantOne
------------------------

No changes were made from Build 1. Refer to :ref:`Radiant Logic RadiantOne<radiant-one>`.

SailPoint IdentityIQ
--------------------

No changes were made from Build 1. Refer to :ref:`SailPoint IdentityIQ<sailpoint>`.

Ivanti Neurons for UEM
----------------------

No significant changes were made from Build 1. Ivanti Neurons for UEM was configured to deploy the Zscaler Client Connector to managed devices. For information, configuration, and integration instructions, refer to :ref:`Ivanti Neurons for UEM<ivanti-neurons>`.

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
---------

Amazon Web Services is a cloud computing platform provided by Amazon that includes a mixture of IaaS, platform as a service (PaaS), and SaaS offerings. The following section describes the setup of AWS IaaS resources to serve as a public/private cloud host.

For details on the logical architecture of the AWS environment, please refer to :ref:`IaaS - Amazon Web Services (AWS)`.

Configuration
~~~~~~~~~~~~~

The purpose of this subsection is to outline how to set up a cloud infrastructure to provide a platform to host public and private resources which integrate with products from E1B2. AWS CloudFormation templates were used during the build of the AWS IaaS environment but are considered outside of the scope of this document. `More information about CloudFormation may be found here <https://aws.amazon.com/cloudformation/>`__.

1. `Create and activate an AWS account <https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/>`__. Use the root account to create administrative accounts with rights to create necessary resources for the project.

2. Create a Production and Management Virtual Private Cloud (VPC). Configure ingress and egress Security Group rules for each VPC.

3. Create Transit gateways to attach on-prem networks to the AWS environment. Create Internet gateways for access to the internet.

4. Within the Prod VPC, configure redundant public subnets in different Availability Zones for fault tolerance. Configure redundant private subnets for Web, Application, and Database tiers.

5. Set up resources for testing in the Prod VPC. For demonstration purposes, a private WordPress and GitLab server pair and a public WordPress server were built. Configure auto scaling and Elastic Load Balancing for servers/services set up on the Web, Application, and Database tiers.

6. Within the Mgmt VPC, configure redundant public subnets in different Availability Zones for fault tolerance. Configure private subnets for Satellite, Domain Controller, and Security Management Tiers.

7. Set up AWS Session Manager access for remote admins.

8. For shared AWS services, configure VPC endpoints with ICAM policies to control access.