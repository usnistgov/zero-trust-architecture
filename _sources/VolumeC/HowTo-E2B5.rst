Enterprise 2 Build 5 (E2B5) - SDP and SASE - Lookout SSE and Okta Identity Cloud as PEs Product Guides
======================================================================================================

.. include:: /_publication_note.rst

This section of the practice guide contains detailed instructions for installing, configuring, and integrating all of the products used to implement E2B5. For additional details on E2B5's logical and physical architectures, please refer to :ref:`architecture and builds`.

Lookout Security Service Edge (SSE) - Includes Secure Private Access, Secure Cloud Access, and Secure Internet Access
---------------------------------------------------------------------------------------------------------------------

The Lookout Security Service Edge converges cloud-centric security capabilities to facilitate secure access to the web, cloud services (SaaS), and private applications. While different components within SSE perform different functions, SSE unifies the management of these components into a single interface, allowing policies to be applied seamlessly across the organization. This service was initially provisioned by the Lookout team, with setup, installation, and integration occurring afterwards. Additional details on the implementation of the Lookout SSE Platform and components can be found in the Lookout Cloud Security Platform Administrator Guide, which is available at the `Lookout website <https://www.lookout.com/form/sse-admin-guide>`__.

Lookout Secure Private Access
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Secure Private Access provides secure remote access to an organization's applications, data, and services based on defined access control policies. Secure Private Access enforces granular, adaptive, and context-aware policies for providing secure and seamless access to private applications hosted across clouds and corporate data centers, from any remote location and from any device. That context can be a combination of user identity, user or service location, time of the day, type of service, and security posture of the device.

In this build, Secure Private Access provides access to the on-prem and IaaS applications running within Enterprise 2.

Lookout Secure Cloud Access
~~~~~~~~~~~~~~~~~~~~~~~~~~~

As part of the Lookout Cloud Security Platform, Secure Cloud Access provides policy controls to support cloud-based applications. In this build, Secure Cloud Access manages user access to the SaaS-based Google Workspace component of Enterprise 2.

Lookout Secure Internet Access
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Secure Internet Access keeps users safe from cyberthreats and prevents unauthorized traffic from entering and spreading through internal networks. As a cloud-based solution, Secure Internet Access monitors user web traffic and enforces policies that define conditions for access to specific websites or types of sites. It plays an important role in protecting employee and user work environments from infections coming from malicious web traffic, internet-borne malware, and other cyberthreats.

Policy Configuration
~~~~~~~~~~~~~~~~~~~~

This section details the process of creating an access control policy to control user access to a resource, internet destination, or cloud resource. Because Lookout SSE's dashboard unifies policies pertaining to Private Access, Cloud Access, and Internet Access, the policy creation process for each of these components follows similar steps. Detailed instructions on creating policies can be found in the Lookout Cloud Security Platform Administrator Guide, which is available at the `Lookout website <https://www.lookout.com/form/sse-admin-guide>`__.

Integration with Okta Identity Cloud
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Instructions to configure the Lookout SSE integration with Okta can be found in the Lookout Administrator Guide under the **Enable Enterprise Authentication** section, which is available at the `Lookout website <https://www.lookout.com/form/sse-admin-guide>`__.

Integration with Google Workspace
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Instructions to configure the Lookout SSE integration with Google Workspace can be found in the Lookout Administrator Guide under the **Onboarding Google Workspace Suite and Applications** section, which is available at the `Lookout website <https://www.lookout.com/form/sse-admin-guide>`__.

Lookout Secure Private Access Connector
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The Lookout Secure Private Access Connector integrates with the cloud-based Secure Private Access Gateway to provide connectivity to on-prem and IaaS applications within Enterprise 2. For this build, the Connector was placed on a VM instance within Google Cloud. Setup details can also be found in the Lookout Administrator Guide under the **Deployment - Secure Private Access** section, which is available at the `Lookout website <https://www.lookout.com/form/sse-admin-guide>`__.

Lookout Client
--------------

The Lookout Client is available for Windows and macOS platforms, and it must be running for users to gain access to resources through Lookout SSE. The installation instructions can also be found in the Lookout Administrator Guide under the **Managing Traffic Steering in Windows and MacOS Clients** section, which is available at the `Lookout website <https://www.lookout.com/form/sse-admin-guide>`__.

Lookout MES
-----------

Refer to :ref:`Lookout MES<lookout-mes>`.

Okta Identity Cloud
-------------------

The Okta Identity Cloud was implemented in the same manner as Enterprise 1. No significant changes were made. Refer to :ref:`Okta Identity Cloud<okta-identity-cloud>`.

Okta Verify App
---------------

The Okta Verify App was implemented in the same manner as Enterprise 1. No significant changes were made. Refer to :ref:`Okta Verify App<okta-verify-app>`.

Radiant Logic RadiantOne
------------------------

Installation and Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Refer to :ref:`Radiant Logic RadiantOne Installation and Configuration<radiant-install>`.

Integrations
~~~~~~~~~~~~

Refer to :ref:`Radiant Logic RadiantOne Integration<radiant-integration>` for integration of Radiant Logic with SailPoint.

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

VMware Workspace ONE
--------------------

For installation, configuration, and integration instructions, refer to :ref:`VMware Workspace ONE<vmware-workspace-one>`.

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

Google Cloud
-------------

For installation, configuration, and integration instructions, refer to :ref:`Google Cloud<google-cloud>`.

Google Workspace
----------------

Google Workspace is a cloud-based SaaS offering that provides a range of SaaS applications to users. For this build, Google Workspace provided SaaS resources that were accessible to users via Lookout SSE.

Instructions for initial setup and configuration can be found in Google's `Quick Start Guide <https://support.google.com/a/answer/9212645?sjid=10765815004953819990-NA>`__.

DigiCert CertCentral
---------------------

For installation, configuration, and integration instructions, refer to :ref:`DigiCert CertCentral<digicert-certcentral>`.
