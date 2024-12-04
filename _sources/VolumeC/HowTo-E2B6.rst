Enterprise 2 Build 6 (E2B6) - SASE - Google Chrome Enterprise Premium (CEP) - Access Context Manager as PE
===========================================================================================================

.. include:: /_publication_note.rst

This section of the practice guide contains detailed instructions for installing, configuring, and integrating all the products used to implement E2B6. For additional details on E2B6's logical and physical architectures, please refer to :ref:`architecture and builds`.

Google Chrome Enterprise Premium (CEP)
--------------------------------------

Google's CEP is a zero trust platform that is secure and reliable, providing continuous and real-time end-to-end protection. CEP's PE and PDP (Access Context Manager) are managed by Google's cloud platform. Use Google's `Access Context Manager Documentation <https://cloud.google.com/access-context-manager/docs/how-to>`__ for setup and configuration of policies. CEP leverages Chrome browser for endpoint protection and compliance and leverages the Identity Aware Proxy (IAP) to act as the PEP. Use the `CEP How-to Guides <https://cloud.google.com/beyondcorp-enterprise/docs/how-to>`__ to configure access to resources.

Note: BeyondCorp and Chrome Enterprise has merged and it is called Chrome Enterprise Premium (CEP) now.

Google CEP Chrome Browser
-------------------------

Google's CEP Chrome browser is the endpoint security solution implemented in this build. The CEP Chrome browser provides endpoint and user information to Okta and CEP for endpoint verification and compliance checks based on policies set by CEP Access Context Manager. To setup and configure CEP to manage the Chrome browser, follow the `Chrome Browser Cloud Management <https://support.google.com/chrome/a/answer/9116814?hl=en&sjid=16280189471034552740-NA&visit_id=638572547336200246-964934049&ref_topic=9301744&rd=1>`__ documentation. Steps include:

-  Sign up for Chrome Browser Cloud Management

-  Enroll cloud-managed Chrome browsers

-  Enable Chrome browser reporting

-  Set policies for enrolled browsers including data protection

Google Application Connector
-----------------------------

Google's identity aware proxy (IAP) is the application connector that is used to protect both cloud and on-prem resources. For this build, we have resources on-prem and in the cloud. To begin setup, please start with the `Identity-Aware Proxy overview <https://cloud.google.com/iap/docs/concepts-overview>`__ document. For specific configuration for cloud resources, follow the instructions in the `Enabling IAP for Compute Engine <https://cloud.google.com/iap/docs/enabling-compute-howto>`__ document. 

The On-Premises connection setup, review the information in the `Overview of IAP for on-premises apps <https://cloud.google.com/iap/docs/cloud-iap-for-on-prem-apps-overview>`__ document prior to installation. Follow the instructions to configure the on-prem IAP in the `Enabling IAP for on-premises apps <https://cloud.google.com/iap/docs/enabling-on-prem-howto>`__ document.

Google Cloud
-------------

For installation, configuration, and integration instructions, refer to :ref:`Google Cloud<google-cloud>`.

Google Workspace
----------------

For installation, configuration, and integration instructions, refer to :ref:`Google Workspace<google-workspace>`.

Refer to Google's `Okta user provisioning and single sign-on <https://cloud.google.com/architecture/identity/okta-provisioning-and-single-sign-on>`__ documentation for integration with Okta.

Okta Identity Cloud
-------------------

The Okta Identity Cloud was implemented in the same manner as Enterprise 1. No significant changes were made. Refer to :ref:`Okta Identity Cloud<okta-identity-cloud>`.

Specific configuration for Okta's integration with Google can be found in Okta's `Google Workspace integration <https://help.okta.com/en-us/content/topics/provisioning/google/google-provisioning.htm>`__ documentation.

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
----------------------

For installation, configuration, and integration instructions, refer to :ref:`VMware Workspace ONE<vmware-workspace-one>`.

Note that after the VMware End User Computing division products were implemented at NCCoE, VMware was acquired by Broadcom, then the VMware End User Computing Division was divested and reformed under a new entity, Omnissa LLC. 

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
