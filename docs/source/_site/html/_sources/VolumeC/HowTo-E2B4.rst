Enterprise 2 Build 4 (E2B4) - SDP and SASE - Symantec Cloud Secure Web Gateway, Symantec ZTNA, and Symantec Cloud Access Security Broker as PEs Product Guides
================================================================================================================================================================

.. include:: /_publication_note.rst

This section of the practice guide contains detailed instructions for installing, configuring, and integrating all of the products used to implement E2B4. For additional details on E2B4's logical and physical architectures, please refer to :ref:`architecture and builds`.

Symantec ZTNA
-------------

Symantec ZTNA is a cloud-based service that allows this build to control network access within the enterprise and to control access to enterprise applications and resources.

Installation and Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This build's instance of the Symantec Cloud SWG was provisioned and deployed with the help of the Symantec team. The initial configuration process is detailed in the `official documentation <https://techdocs.broadcom.com/us/en/symantec-security-software/web-and-network-security/secure-access-cloud/1-0/sac-workflow.html>`__. Symantec ZTNA was also integrated with many of the other build components, for which details can be found later in this section. Following that, policies were configured in accordance with the `official Symantec ZTNA policy guidance <https://techdocs.broadcom.com/us/en/symantec-security-software/web-and-network-security/secure-access-cloud/1-0/sac-policies.html>`__.

Integration with Okta Identity Cloud
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Integration with Okta Identity Cloud was accomplished using `Symantec by Broadcom's official documentation <https://techdocs.broadcom.com/us/en/symantec-security-software/web-and-network-security/secure-access-cloud/1-0/Integrate-Identity-Providers/Integrate-Okta-IdP.html>`__.

Integration with Symantec DLP 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Integration with Symantec DLP was accomplished using `Symantec by Broadcom's official documentation <https://techdocs.broadcom.com/us/en/symantec-security-software/web-and-network-security/secure-access-cloud/1-0/sac-policies/Integrate-Symantec-DLP/sac-int-with-dlp.html>`__.

Integration with Symantec Endpoint Security
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Integration with Symantec Endpoint Security was accomplished using `Symantec by Broadcom's official documentation <https://techdocs.broadcom.com/us/en/symantec-security-software/web-and-network-security/secure-access-cloud/1-0/sac-policies/Device-Compliance/device-comp-requirements.html>`__.

Integration with Symantec Cloud Secure Web Gateway (Cloud SWG)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Integration with the Symantec Cloud SWG was accomplished using guidance provided in the Symantec ZTNA web interface. Integrating these components depends on linking them together via subscription ID.

Symantec ZTNA Connector
~~~~~~~~~~~~~~~~~~~~~~~

The Symantec ZTNA Connector provides a secure connection between the cloud-based Symantec ZTNA service and applications and resources that are being protected. The protected applications and resources can be hosted on-prem or in the cloud and can be private or public-facing. Deployment instructions can be found in the Symantec ZTNA web interface.

Symantec Cloud Secure Web Gateway (Cloud SWG)
---------------------------------------------

The Symantec Cloud SWG is a cloud-based service that can apply policy to user traffic. User endpoints with the Symantec Endpoint Security agent are configured to pass network traffic through the Cloud SWG, allowing policy to be applied and enforced.

Installation and Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This build's instance of the Symantec Cloud SWG was provisioned and deployed with the help of the Symantec by Broadcom team. Once deployment was complete, policies were configured in accordance with the `official Cloud SWG Policy guidance <https://techdocs.broadcom.com/us/en/symantec-security-software/web-and-network-security/cloud-swg/help/policy-matrix.html>`__.

Integrations
~~~~~~~~~~~~

The Symantec Cloud SWG was also integrated with the Symantec Cloud Security Access Broker (CASB) and the Symantec DLP Cloud Detection Service to better enable policy enforcement in those areas. These integrations were accomplished using the `official integration documentation for the Symantec CASB <https://techdocs.broadcom.com/us/en/symantec-security-software/web-and-network-security/cloud-swg/help/about_webapps_co/about-casb.html>`__ and the `official integration documentation for Symantec DLP <https://techdocs.broadcom.com/us/en/symantec-security-software/web-and-network-security/cloud-swg/help/symdlp_co/symdlp_int.html>`__. The Cloud SWG was also integrated with Symantec Endpoint Security to allow endpoint traffic to flow through the Cloud SWG, using the `official integration documentation <https://techdocs.broadcom.com/us/en/symantec-security-software/endpoint-security-and-management/endpoint-security/sescloud/Protection/Secure-Connection/configuring-symantec-web-security-service-integrat-v131901403-d4152e1396.html>`__.

Symantec Cloud Access Security Broker (CASB)
--------------------------------------------

The Symantec Cloud Access Security Broker (CASB) (also known as CloudSOC) integrates with the Symantec Cloud SWG, Symantec DLP, and Symantec ZTNA to control access to cloud-based applications and resources.

Installation and Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This build's instance of the Symantec CASB was provisioned and deployed with the help of the Symantec team. Further configuration was accomplished using the `official Symantec documentation <https://techdocs.broadcom.com/us/en/symantec-security-software/information-security/symantec-cloudsoc/cloud.html>`__.

Integration with SpanVA
~~~~~~~~~~~~~~~~~~~~~~~

SpanVA is an on-prem component of the Symantec CASB that was deployed and integrated with this build's AD instance. This allowed the CASB to correlate user identities and events. Deployment and integration was accomplished using the `official SpanVA documentation <https://techdocs.broadcom.com/us/en/symantec-security-software/information-security/symantec-cloudsoc/cloud/spanva-home.html>`__.

Symantec Endpoint Security
--------------------------

Symantec Endpoint Security provides a wide range of endpoint protection capabilities. It functions with a cloud-based management console on the backend and applies policies to endpoints through a software agent deployed to the device.

Installation and Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This build's instance of Symantec Endpoint Security was provisioned and deployed with the help of the Symantec by Broadcom team. Once deployed, policies were configured using `Symantec's official documentation <https://techdocs.broadcom.com/us/en/symantec-security-software/endpoint-security-and-management/endpoint-security/sescloud/Policies-and-Policy-Groups.html>`__, and software agents were deployed to endpoints throughout the enterprise.

Symantec Endpoint Security Agent
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

A software agent was deployed onto Windows, macOS, Linux, iOS, and Android endpoints within the build. This software agent provided a range of endpoint protection capabilities, including device health and posture management, and tunneling the endpoint's network traffic to the Symantec Cloud SWG.

Symantec DLP Cloud Detection Service
------------------------------------

The Symantec DLP Cloud Detection Service provided data loss prevention capabilities for this build. This deployment is primarily a cloud-based service that integrates with Symantec ZTNA, Symantec Cloud SWG, and Symantec Endpoint Security. An on-prem Symantec DLP Management Server was deployed in the build's on-prem environment for granular policy configuration.

Installation and Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This build's instance of the Symantec DLP Cloud Detection Service was provisioned and deployed with the help of the Symantec by Broadcom team. Next, the Symantec DLP Management Server was deployed in the enterprise on-prem environment, using `Symantec's official documentation <https://techdocs.broadcom.com/us/en/symantec-security-software/information-security/data-loss-prevention/16-0/Install-DLP.html>`__. Once deployed, policies were configured through the Symantec DLP Management Server, using `Symantec's official documentation <https://techdocs.broadcom.com/us/en/symantec-security-software/information-security/data-loss-prevention/16-0/about-data-loss-prevention-policies-v27576413-d327e9.html>`__.

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

.. _google-cloud:

The Google Cloud Platform is a cloud computing platform provided that includes a mixture of IaaS, PaaS, and SaaS offerings. This build utilized Google Cloud IaaS resources to serve as a public/private cloud host. This section describes the Google Cloud components that were utilized in this build.

1. A Virtual Private Cloud (VPC) network was created within the Google Cloud console, and subnets were configured. Step-by-step instructions can be found in `Google's official documentation <https://cloud.google.com/vpc/docs/create-modify-vpc-networks>`__.

2. VPC firewall rules were configured to secure the environment. Step-by-step instructions can be found in `Google's official documentation <https://cloud.google.com/firewall/docs/firewalls>`__.

3. VMs to host resources were created using `Google's official documentation <https://cloud.google.com/compute/docs/instances/create-start-instance>`__. For this build, Google Cloud hosted MSV Agents, a Symantec ZTNA Connector, and GitLab servers that served as applications/resources for demonstrations.

4. A Google Cloud VPN was configured to connect components of the on-prem environment. This was set up using `Google's official documentation <https://cloud.google.com/network-connectivity/docs/vpn/concepts/overview>`__.

For details on the logical architecture of the Google Cloud environment, please refer to :ref:`IaaS - Google`.

DigiCert CertCentral
---------------------

For installation, configuration, and integration instructions, refer to :ref:`DigiCert CertCentral<digicert-certcentral>`.